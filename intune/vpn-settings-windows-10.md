---
title: Konfigurera Windows 10 VPN-inställningarna i Microsoft Intune – Azure | Microsoft Docs
description: Läs om tillgängliga VPN-inställningar i Microsoft Intune, vad de används till och vad de gör, inklusive trafikregler, villkorlig åtkomst samt DNS- och proxyinställningar för Windows 10-enheter och Windows Holographic for Business-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.reviewer: tycast
ms.custom: intune-azure
ms.openlocfilehash: 0b064c6f0eaa67157c5c50ddad3a8fd863295b8b
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312858"
---
# <a name="windows-10-vpn-settings-in-intune"></a>Windows 10 VPN-inställningar i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan konfigurera VPN-anslutningar med Intune. I artikeln beskrivs inställningar, trafikregler, villkorlig åtkomst samt DNS- och proxyinställningar.

Dessa inställningar gäller för:

- Enheter som kör Windows 10
- Enheter som kör Windows Holographic for Business

Beroende på vilka inställningar du väljer, kanske inte alla värden är konfigurerbara.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **Servrar**: Lägg till en eller flera VPN-servrar som enheterna ska ansluta till. När du lägger till en server, anger du följande information:
  - **Beskrivning**: Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**
  - **IP-adress eller fullständigt domännamn**: Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till, exempelvis **192.168.1.1** eller **vpn.contoso.com**
  - **Standardserver**: Gör servern till den standardserver som enheterna använder för att upprätta anslutningen. Ange endast en server som standard.
  - **Importera**: Bläddra till en kommateckenavgränsad fil som innehåller en lista med servrar i formatet: beskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa servrar till listan **Servrar**.
  - **Exportera**: Exporterar listan med servrar till en kommateckenavgränsad fil (csv)

- **Registrera IP-adresser med internt DNS**: Välj **Aktivera** för att konfigurera Windows 10 VPN-profilen så att den dynamiskt registrerar IP-adresser som har tilldelats till VPN-gränssnittet med internt DNS, eller välj **Inaktivera** om du inte vill registrera IP-adresserna dynamiskt.

- **Anslutningstyp**: Välj VPN-anslutningstypen från leverantörslistan nedan:

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWALL Mobile Connect**
  - **Check Point Capsule VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **Automatiskt**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  När du väljer en VPN-anslutningstyp, kan du också efterfrågas om följande inställningar:  
    - **Alltid på**: Aktivera för att automatiskt ansluta till VPN-anslutningen när följande inträffar: 
      - Användarna loggar in på sina enheter
      - Nätverket på enheten ändras
      - Skärmen på enheten sätts på efter att ha varit avstängd 

    - **Autentiseringsmetod**: Välj hur du vill att användarna autentiseras mot VPN-servern. Med hjälp av **certifikat** får du utökade funktioner, t.ex. zero-touch-upplevelse, VPN på begäran och VPN per app.
    - **Spara autentiseringsuppgifter för varje inloggning**: välja att cachelagra autentiseringsuppgifterna.
    - **Anpassad XML**: Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.
    - **EAP XML**: Ange EAP XML-kommandon som konfigurerar VPN-anslutningen

#### <a name="pulse-secure-example"></a>Pulse Secure-exempel

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

#### <a name="f5-edge-client-example"></a>F5 Edge Client-exempel

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

#### <a name="sonicwall-mobile-connect-example"></a>SonicWall Mobile Connect-exempel
**Inloggningsgrupp eller domän**: Den här egenskapen kan inte anges i VPN-profilen. I stället parsar Mobile Connect värdet när användarnamn och domän har angetts i formatet `username@domain` eller `DOMAIN\username`.

Exempel:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

#### <a name="checkpoint-mobile-vpn-example"></a>Kontrollpunkt för mobilt VPN-exempel

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

#### <a name="writing-custom-xml"></a>Skriva anpassad XML
Mer information om hur du skriver anpassade XML-kommandon finns i varje tillverkares VPN-dokumentation.

Läs mer om att skapa anpassade EAP XML-filer i informationen om [EAP-konfiguration](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration).

## <a name="apps-and-traffic-rules"></a>Regler för appar och trafik

- **Associera PIA eller appar med denna VPN**: Aktivera den här inställningen om du endast vill att vissa appar ska använda VPN-anslutningen. Alternativen är:

  - **Associera en PIA med den här anslutningen**: Ange en **PIA-domän för den här anslutningen**
  - **Associera appar med den här anslutningen**: Du kan **Begränsa VPN-anslutning för dessa appar** och sedan lägga till **Associerade appar**. De appar som du anger använder automatiskt VPN-anslutningen. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.
  >[!IMPORTANT]
  >Vi rekommenderar att du skyddar alla applistor som skapas för VPN:er per app. Om en obehörig användare ändrar listan och du importerar den till applistan med VPN:er per app, finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor på är att använda en åtkomstkontrollista (ACL).

- **Nätverkstrafikregler för den här VPN-anslutningen**: Välj vilka protokoll, vilka lokala portar och fjärrportar, samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.

## <a name="conditional-access"></a>Villkorlig åtkomst

- **Villkorlig åtkomst för den här VPN-anslutningen**: Aktiverar enhetskompatibilitetsflöde från klienten. När det är aktiverat försöker VPN-klienten kommunicera med Azure Active Directory (AD) för att få ett certifikat för autentisering. VPN-klienten måste vara inställd på användning av certifikatautentisering och VPN-servern måste lita på den server som returneras av Azure Active Directory.

- **Enkel inloggning (SSO) med alternativt certifikat**: Använd ett annat certifikat än VPN-autentiseringscertifikatet vid Kerberos-autentisering för att uppnå enhetskompatibilitet. Ange certifikatet med följande inställningar:

  - **Namn**: Namn för förbättrad nyckelanvändning (EKU)
  - **Objektidentifierare**: Objektidentifierare vid förbättrad nyckelanvändning
  - **Utfärdarhash**: Tumavtryck för SSO-certifikat

## <a name="dns-settings"></a>DNS-inställningar

**Domän och servrar för den här VPN-anslutningen**: Lägg till domänen och DNS-servern som VPN-anslutningen ska använda. Du kan välja vilka DNS-servrar som ska användas av VPN-anslutningen när anslutningen har upprättats. För varje server anger du:
- **Domän**
- **DNS-server**
- **Proxy**

## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange den **URL för proxyserver**, exempelvis `http://proxy.contoso.com`, som innehåller konfigurationsfilen.
- **Adress**: Ange proxyserverns adress såsom en IP-adress eller `vpn.contoso.com`
- **Portnummer**: Ange TCP-portnumret som används av proxyservern
- **Kringgå proxy för lokala adresser**: Om du inte vill använda en proxyserver för lokala adresser, välj då Aktivera. Den här inställningen gäller om VPN-servern kräver en proxyserver för anslutningen.

## <a name="split-tunneling"></a>Delade tunnlar

- **Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.
- **Routning för delade tunnlar för den här VPN-anslutningen**: Lägg till valfria vägar för tredje parts VPN-leverantörer. Ange ett målprefix och en prefixstorlek för varje anslutning.
