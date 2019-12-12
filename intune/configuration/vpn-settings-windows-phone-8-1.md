---
title: VPN-inställningar i Microsoft Intune för Windows Phone 8.1-enheter
titleSuffix: ''
description: Läs mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Windows Phone 8.1.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69de660e65ed2a0f3b6c9c7e4ce774a6fcde2676
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506514"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör Windows Phone 8.1

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Windows Phone 8.1.


Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Använd alla inställningar endast för Windows Phone 8.1** – Detta är en inställning som du kan konfigurera i den klassiska Intune-portalen. Den här inställningen kan inte ändras i Azure-portalen. Om denna anges till **Konfigurerad** tillämpas inställningar endast på Windows Phone 8.1-enheter. Om inställningen anges till **Inte konfigurerad** gäller inställningarna även för Windows 10 Mobile-enheter.
- **Anslutningsnamn** – Ange ett namn på anslutningen. Användarna ser det här namnet när de bläddrar på enheten i listan med tillgängliga VPN-anslutningar.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
  - **Certifikat** – Under **Autentiseringscertifikat** väljer du den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](../protect/certificates-configure.md).
  - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Servrar** – Lägg till en eller flera VPN-servrar som enheterna ansluter till.
  - **Lägg till** – Öppnar bladet **Lägg till rad** där du kan ange följande information:
    - **Beskrivning** – Ange ett beskrivande namn för servern, som t.ex. **Contoso VPN-server**.
    - **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
    - **Standardserver** – Gör den här servern till den standardserver som enheterna använder för att upprätta anslutningen. Du ska endast ange en server som standard.
  - **Importera** – Bläddra till en fil som innehåller en kommateckenavgränsad lista med servrar i formatbeskrivning, IP-adress eller FQDN, samt standardserver. Välj **OK** för att importera dessa till listan **Servrar**.
  - **Exportera** – Exporterar listan med servrar till en kommateckenavgränsad fil (csv).

- **Kringgå VPN i företagets trådlösa nätverk** – Aktivera det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till företagets trådlösa nätverk.
- **Kringgå VPN i trådlöst hemnätverk** – Aktivera det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till ett trådlöst hemnätverk.

- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
  - **Check Point Capsule VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

- **Inloggningsgrupp eller domän** (endast SonicWall Mobile Connect) – Ange namnet på den inloggningsgrupp eller domän som du vill ansluta till.
- **Roll** (endast Pulse Secure) – Ange namnet på den användarroll som har åtkomst till anslutningen. En användarroll definierar personliga inställningar och alternativ, och aktiverar eller inaktiverar vissa åtkomstfunktioner.
- **Sfär** (endast Pulse Secure) – Ange namnet på den autentiseringssfär som du vill använda. En autentiseringssfär är en grupp av autentiseringsresurser som används av Pulse Secure-anslutningstypen.

- **Söklista för DNS-suffix** - **Lägg till** ett eller flera DNS-suffix. Varje DNS-suffix som du anger genomsöks vid anslutning till en webbplats med ett kort namn. Ange exempelvis DNS-suffixen **domain1.contoso.com** och **domain2.contoso.com** och gå till URL:en `http://mywebsite`, så söks URL:erna `http://mywebsite.domain1.contoso.com` och `http://mywebsite.domain2.contoso.com` igenom.

- **Anpassad XML** – Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen.

    **Exempel för Pulse Secure:**

```xml
    <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

**Exempel för CheckPoint Mobile VPN:**

```xml
    <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

**Exempel för SonicWall Mobile Connect:**

```xml
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

**Exempel för F5 Edge Client:**

```xml
    <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

Läs VPN-dokumentationen för varje tillverkare för mer information om hur du skriver anpassade XML-kommandon.

- **Delade tunnlar** - **Aktivera** eller **Inaktivera** det här alternativet för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.




## <a name="proxy-settings"></a>Proxyinställningar

- **Identifiera proxyinställningar automatiskt** – Om VPN-servern kräver en proxyserver för anslutningen, kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **Proxyserver-URL** (till exempel `http://proxy.contoso.com`) som innehåller konfigurationsfilen.
- **Använd proxyserver** – Aktivera det här alternativet om du vill ange inställningarna för proxyservern manuellt.
  - **Adress** – Ange proxyns serveradress (som en IP-adress).
  - **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
- **Kringgå proxy för lokala adresser** – Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
