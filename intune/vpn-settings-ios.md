---
title: "VPN-inställningar i Intune för iOS-enheter"
titlesuffix: Azure portal
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på iOS-enheter.”"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d3db57b851c405758c9cccdc3e70c96ca9e76000
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>VPN-inställningar för iOS-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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
    - **Dell SonicWALL Mobile Connect**
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
    - **URL-strängavsökning** – Om du vill kan du ange en URL som regeln använder som ett test. Om den enhet där profilen har installerats får tillgång till den här webbadressen utan omdirigering, startas VPN-anslutningen och enheten ansluter till målwebbadressen. Användaren ser inte URL-strängavsökningsplatsen. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att webbadressen testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till målwebbadressen via VPN.
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