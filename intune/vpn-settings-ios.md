---
title: "VPN-inställningar i Intune för iOS-enheter"
titleSuffix: Intune on Azure
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på iOS-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1447c123-ea33-4ea0-aab4-69577cdb8d00
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6cc079b05037cc18b7d27dd0d2674e87e1d54d0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="vpn-settings-for-ios-devices-in-microsoft-intune"></a>VPN-inställningar för iOS-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar


**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
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
- **Delade tunnlar** - **Aktivera** eller **Inaktivera** detta alternativ för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.


## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** som anslutningstyp, kan du konfigurera inställningarna ytterligare:

- **VPN-ID** Detta är en identifierare för VPN-appen som du använder och den tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för de anpassade VPN-attributen** Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.

## <a name="apps-per-app-vpn-settings"></a>Inställningar för appar (per app-VPN)

- **Per app-VPN** – Aktivera det här alternativet om du vill att webbadresser ska aktivera VPN-anslutningen när de besöks i Safari-webbläsaren. Om du vill konfigurera detta måste du ha valt **Certifikat** som autentiseringsmetod i de grundläggande VPN-inställningarna.
- **Ange webbadresser som ska aktivera VPN-anslutningen när webbläsaren Safari används** – Klicka på Lägg till för att lägga till en eller flera webbadresser. VPN-anslutningen kommer att aktiveras när dessa webbadresser besöks.

- **Regler på begäran** – Här kan du konfigurera villkorliga regler som styr när VPN-anslutningen ska initieras. Du kan till exempel skapa ett villkor där VPN-anslutningen endast används när en enhet inte är ansluten till något av dina trådlösa företagsnätverk. Du kan också skapa ett villkor där VPN-anslutningen inte initieras om enheten inte får åtkomst till en DNS-sökdomän som du har angett.

    - **SSID:er eller DNS-sökdomäner** – Välj om detta tillstånd ska använda det trådlösa nätverkets **SSID:er** eller **DNS-sökdomäner**. Välj Lägg till för att konfigurera en eller flera SSID:er eller sökdomäner.
    - **URL-strängavsökning** – Om du vill kan du ange en URL som regeln använder som ett test. Om den enhet där profilen har installerats får tillgång till denna URL utan omdirigering, initieras VPN-anslutningen och enheten ansluter till mål-URL:en. Användaren ser inte URL-strängavsökningsplatsen. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att URL:en testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till mål-URL:en via VPN.
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
