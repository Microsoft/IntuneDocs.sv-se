---
title: "Intune VPN-inställningar för Windows 10-enheter"
titleSuffix: Intune on Azure
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Windows 10-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 495e4ed6-b2ef-47cc-a110-13fa9b5f85a6
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6f112983a33c1af24d288f19140114084575f36d
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-windows-10-devices-in-microsoft-intune"></a>VPN-inställningar för Windows 10-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.


## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


- **Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ska ansluta till.
    - **Lägg till** – Öppnar bladet **Lägg till rad** där du kan ange följande information:
        - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
        - **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
        - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
    - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
    - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

**Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
- **Pulse Secure**
- **F5 Edge Client**
- **Dell SonicWALL Mobile Connect**
- **Check Point Capsule VPN**
- **Automatiskt**
- **IKEv2**
- **L2TP**
- **PPTP**

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

Läs VPN-dokumentationen för varje tillverkare för mer information om hur du skriver anpassade XML-kommandon.

**Delade tunnlar** - **Aktivera** eller **Inaktivera** detta alternativ för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.
- **Routning för delade tunnlar för den här VPN-anslutningen** – Lägg till valfria vägar för tredje parts VPN-leverantörer. Ange ett målprefix och en prefixstorlek för varje väg.

## <a name="apps-and-traffic-rules"></a>Regler för appar och trafik

**Begränsa VPN-anslutning till de här apparna** – Aktivera endast det här alternativet om du vill att de appar du anger ska använda VPN-anslutningen.
**Tillhörande appar** – Ange en lista med appar som ska använda VPN-anslutningen automatiskt. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.

>[!IMPORTANT]
>Vi rekommenderar att du skyddar alla listor över appar som du sammanställer för användning i konfigurationen av per app-VPN. Om en obehörig användare ändrar listan och du importerar den till per app-VPN-applistan finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor är att använda en åtkomstkontrollista (ACL, Access Control List).

**Nätverkstrafikregler för den här VPN-anslutningen** – Välj vilka protokoll, vilka lokala portar och fjärrporta,r samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.


## <a name="conditional-access"></a>Villkorlig åtkomst

**Villkorlig åtkomst för den här VPN-anslutningen** -
**Enkel inloggning med alternativt certifikat** -
**Förbättrad nyckelanvändning** -
**Utfärdar-hash** -

## <a name="dns-settings"></a>DNS-inställningar

**DNS-namn och servrar för den här VPN-anslutningen** – Välj vilka DNS-servrar som ska användas av VPN-anslutningen när anslutningen har upprättats.
För varje server anger du:
- **DNS-namn**
- **DNS-server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
    - **Adress** – Ange proxyns serveradress (som en IP-adress).
    - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
