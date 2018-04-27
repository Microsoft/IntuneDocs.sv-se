---
title: Visa VPN-inställningarna i Microsoft Intune – Azure | Microsoft Docs
description: Läs om tillgängliga VPN-inställningar i Microsoft Intune, vad de används till och vad de gör, inklusive trafikregler, villkorlig åtkomst samt DNS- och proxyinställningar för Windows 10-enheter och Windows Holographic for Business-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/8/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 787501892d0955e3396bc8f37e5da8ba0d312c74
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="read-about-the-vpn-settings-in-intune"></a>Läs mer om VPN-inställningar i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan konfigurera VPN-anslutningar med Intune. I artikeln beskrivs inställningar, trafikregler, villkorlig åtkomst samt DNS- och proxyinställningar.

Dessa inställningar gäller för:

- Enheter som kör Windows 10
- Enheter som kör Windows Holographic for Business

Beroende på vilka inställningar du väljer, kanske inte alla värden är konfigurerbara.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar**: Lägg till en eller flera VPN-servrar som enheterna ska ansluta till.
  - **Lägg till**: Öppnar **Lägg till rad** där du anger följande information:
    - **Beskrivning**: Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**
    - **IP-adress eller fullständigt domännamn**: Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till, exempelvis **192.168.1.1** eller **vpn.contoso.com**
    - **Standardserver**: Gör servern till den standardserver som enheterna använder för att upprätta anslutningen. Ange endast en server som standard.
  - **Importera**: Bläddra till en kommateckenavgränsad fil som innehåller en lista med servrar i formatet: beskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa servrar till listan **Servrar**.
  - **Exportera**: Exporterar listan med servrar till en kommateckenavgränsad fil (csv)

**Anslutningstyp**: Välj VPN-anslutningstypen från leverantörslistan nedan:

- **Automatiskt**
- **Check Point Capsule VPN**
- **Citrix VPN**
- **SonicWALL Mobile Connect**
- **F5 Edge Client**
- **IKEv2**
- **L2TP**
- **PPTP**
- **Pulse Secure**

**Inloggningsgrupp eller domän** (endast SonicWALL Mobile Connect): Den här egenskapen kan inte anges i VPN-profilen. I stället parsar Mobile Connect värdet när användarnamn och domän har angetts i formatet `username@domain` eller `DOMAIN\username`.

**Anpassad XML**/**EAP XML**: Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.

**Exempel för Pulse Secure:**

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exempel för CheckPoint Mobile VPN:**

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exempel för SonicWALL Mobile Connect:**

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exempel för F5 Edge Client:**

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Mer information om hur du skriver anpassade XML-kommandon finns i varje tillverkares VPN-dokumentation.

Läs mer om att skapa anpassade EAP XML-filer i informationen om [EAP-konfiguration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

**Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.
- **Routning för delade tunnlar för den här VPN-anslutningen**: Lägg till valfria vägar för tredje parts VPN-leverantörer. Ange ett målprefix och en prefixstorlek för varje väg.

## <a name="apps-and-traffic-rules"></a>Regler för appar och trafik

**Begränsa VPN-anslutning till de här apparna**: Aktivera den här inställningen om du endast vill att vissa appar ska använda VPN-anslutningen.

**Tillhörande appar**: Ange en lista med appar som använder VPN-anslutningen automatiskt. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.

>[!IMPORTANT]
>Vi rekommenderar att du skyddar alla applistor som skapas för VPN:er per app. Om en obehörig användare ändrar listan och du importerar den till applistan med VPN:er per app, finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor på är att använda en åtkomstkontrollista (ACL).

**Nätverkstrafikregler för den här VPN-anslutningen**: Välj vilka protokoll, vilka lokala portar och fjärrportar, samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.

## <a name="conditional-access"></a>Villkorlig åtkomst

**Villkorlig åtkomst för den här VPN-anslutningen**: Aktiverar enhetskompatibilitetsflöde från klienten. När det är aktiverat försöker VPN-klienten kommunicera med Azure Active Directory för att få ett certifikat för autentisering. VPN-klienten måste vara inställd för användning av certifikatautentisering och VPN-servern måste lita på den server som returneras av Azure Active Directory.

**Enkel inloggning (SSO) med alternativt certifikat**: Använd ett annat certifikat än VPN-autentiseringscertifikatet vid Kerberos-autentisering för att uppnå enhetskompatibilitet. Ange certifikatet med följande inställningar:

- **Förbättrad nyckelanvändning**: Namn på förbättrad nyckelanvändning (EKU)
- **Objektidentifierare**: Objektidentifierare vid förbättrad nyckelanvändning
- **Utfärdarhash**: Tumavtryck för SSO-certifikat

## <a name="dns-settings"></a>DNS-inställningar

**DNS-namn och servrar för den här VPN-anslutningen**: Välj vilka DNS-servrar som ska användas av VPN-anslutningen när anslutningen har upprättats.
För varje server anger du:
- **DNS-namn**
- **DNS-server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt**: Om VPN-servern kräver en proxyserver för anslutningen, kan du välja om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna.
- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange den **URL för proxyserver**, exempelvis `http://proxy.contoso.com`, som innehåller konfigurationsfilen.
- **Använd proxyserver**: Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
  - **Adress**: Ange proxyserverns adress (som en IP-adress)
  - **Portnummer**: Ange det portnummer som är associerat med proxyservern
- **Kringgå proxy för lokala adresser**: Välj den här inställningen om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger.
