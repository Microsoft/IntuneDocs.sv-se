---
title: "Intune VPN-inställningar för Windows 10-enheter"
titlesuffix: Azure portal
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Windows 10-enheter.”"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d126853051bb4a6c2f1ea6fbd54195ae06254b51
ms.sourcegitcommit: 2c7794848777e73d6a9502b4e1000f0b07ac96bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2018
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>VPN-inställningar för Windows 10-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

> [!NOTE]
> De här inställningarna appliceras även till enheter som kör Windows Holographic for Business.


## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


- **Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ansluter till.
    - **Lägg till** – Öppnar bladet **Lägg till rad** där du kan ange följande information:
        - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
        - **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
        - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
    - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
    - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

**Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
- **Automatiskt**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **Dell SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**


**Inloggningsgrupp eller domän** (endast Dell SonicWALL Mobile Connect) – Ange namnet på den inloggningsgrupp eller domän som du vill ansluta till.

**Anpassad XML**/**EAP XML** – Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.

**Exempel för Pulse Secure:**

```
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exempel för CheckPoint Mobile VPN:**

```
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exempel för Dell SonicWALL Mobile Connect:**

```
    <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exempel för F5 Edge Client:**

```
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Mer information om hur du skriver anpassade XML-kommandon finns i varje tillverkares VPN-dokumentation.

Läs mer om att skapa anpassade EAP XML-filer i informationen om [EAP-konfiguration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Delade tunnlar** - **Aktivera** eller **Inaktivera** detta alternativ för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.
- **Routning för delade tunnlar för den här VPN-anslutningen** – Lägg till valfria vägar för tredje parts VPN-leverantörer. Ange ett målprefix och en prefixstorlek för varje väg.

## <a name="apps-and-traffic-rules"></a>Regler för appar och trafik

**Begränsa VPN-anslutning till de här apparna** – Aktivera endast det här alternativet om du vill att de appar du anger ska använda VPN-anslutningen.
**Tillhörande appar** – Ange en lista med appar som använder VPN-anslutningen automatiskt. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.

>[!IMPORTANT]
>Vi rekommenderar att du skyddar alla listor över appar som du sammanställer för användning i konfigurationen av per app-VPN. Om en obehörig användare ändrar listan och du importerar den till per app-VPN-applistan finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor är att använda en åtkomstkontrollista (ACL, Access Control List).

**Nätverkstrafikregler för den här VPN-anslutningen** – Välj vilka protokoll, vilka lokala portar och fjärrportar, samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.


## <a name="conditional-access"></a>Villkorlig åtkomst

**Villkorlig åtkomst för den här VPN-anslutningen** – Aktiverar enhetskompatibilitetsflöde från klienten. När det är aktiverat försöker VPN-klienten kommunicera med Azure Active Directory för att få ett certifikat för autentisering. VPN-klienten måste vara inställd för användning av certifikatautentisering och VPN-servern måste lita på den server som returneras av Azure Active Directory.

**Enkel inloggning (SSO) med alternativt certifikat** – Använd ett annat certifikat än VPN-autentiseringscertifikatet för Kerberos-autentisering för enhetsefterlevnad. Ange certifikat med följande inställningar: 

- **Förbättrad nyckelanvändning** – Namn på förbättrad nyckelanvändning (EKU).
- **Objektidentifierare** – Objektidentifierare för förbättrad nyckelanvändning.
- **Utfärdarhash** – Tumavtryck för SSO-certifikat.

## <a name="dns-settings"></a>DNS-inställningar

**DNS-namn och servrar för den här VPN-anslutningen** – Välj vilka DNS-servrar som ska användas av VPN-anslutningen när anslutningen har upprättats.
För varje server anger du:
- **DNS-namn**
- **DNS-server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
    - **Adress** – Ange proxyns serveradress (som en IP-adress).
    - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
