---
title: "VPN-inställningar i Microsoft Intune för enheter som kör iOS"
titlesuffix: 
description: "Läs mer om de Intune-inställningar du kan använda för att konfigurera VPN-anslutningar på enheter som kör iOS."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70721d1d2f360527af0e269a93d6243b6a42431b
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör iOS.

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Under **Autentiseringscertifikat** väljer du den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Cisco (IPSec)**
    - **Citrix**
    - **Anpassat VPN**
- **Delade tunnlar** - **Aktivera** eller **Inaktivera** det här alternativet för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.


## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** som anslutningstyp, kan du konfigurera inställningarna ytterligare:

- **VPN-ID** Detta är en identifierare för VPN-appen som du använder och den tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för de anpassade VPN-attributen** Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.

## <a name="apps-per-app-vpn-settings"></a>Inställningar för appar (per app-VPN)

- **Per app-VPN** – Aktivera det här alternativet om du vill att webbadresser ska aktivera VPN-anslutningen när de besöks i Safari-webbläsaren. Om du vill konfigurera detta måste du ha valt **Certifikat** som autentiseringsmetod i de grundläggande VPN-inställningarna.
- **Webbadresser som aktiverar VPN-anslutningen när webbläsaren Safari används** – Klicka på Lägg till för att lägga till en eller flera webbadresser. VPN-anslutningen aktiveras när de här webbadresserna besöks.

- **Regler på begäran** – Här kan du konfigurera villkorliga regler som styr när VPN-anslutningen ska initieras. Du kan till exempel skapa ett villkor där VPN-anslutningen endast används när en enhet inte är ansluten till något av dina trådlösa företagsnätverk. Du kan också skapa ett villkor där VPN-anslutningen inte initieras om enheten inte får åtkomst till en DNS-sökdomän som du har angett.

    - **SSID:n eller DNS-sökdomäner** – Välj om det här villkoret ska använda det trådlösa nätverkets **SSID:n** eller **DNS-sökdomäner**. Välj Lägg till för att konfigurera en eller flera SSID:er eller sökdomäner.
    - **URL-strängavsökning** – Om du vill kan du ange en URL som regeln använder som ett test. Om den enhet där profilen har installerats får tillgång till den här webbadressen utan omdirigering, startas VPN-anslutningen och enheten ansluter till målwebbadressen. Användaren ser inte URL-strängens avsökningsplats. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att webbadressen testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till målwebbadressen via VPN.
    - **Domänåtgärd** – Välj något av följande:
        - Anslut vid behov – 
        - Anslut aldrig – 
    - **Åtgärd** – Välj något av följande:
        - Anslut – 
        - Utvärdera anslutning – 
        - Ignorera – 
        - Koppla från – 


## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Adress** – Ange proxyns serveradress (som en IP-adress).
- **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
