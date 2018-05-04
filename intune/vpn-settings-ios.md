---
title: VPN-inställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa tillgängliga konfigurationsinställningar för virtuella privata nätverk (VPN), inklusive anslutningsinformation, autentiseringsmetoder och delade tunnlar i de grundläggande inställningarna. Visa även de anpassade VPN-inställningarna med identifieraren och nyckel-värdeparen. Det är även möjligt att visa VPN-inställningarna per app som inkluderar Safari-webbadresser och VPN-anslutningar på begäran med SSID- eller DNS-sökningsdomäner samt proxyinställningar för att inkludera ett konfigurationsskript, en IP- eller FQDN-adress och en TCP-port i Microsoft Intune på iOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 374c3937d04fd546c17d6f147609f448875dddba
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/18/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör iOS.

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar i en lista över tillgängliga VPN-anslutningar på enheten.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.
- **Autentiseringsmetod**: Välj hur enheter ska autentiseras mot VPN-servern från:
  - **Certifikat** – Under **Autentiseringscertifikat** väljer du en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) innehåller vägledning om certifikatprofiler.
  - **Användarnamn och lösenord**: Slutanvändare måste ange ett användarnamn och ett lösenord för att logga in på VPN-servern.
- **Anslutningstyp**: Välj VPN-anslutningstypen från leverantörslistan nedan:
  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **Cisco Legacy AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Cisco (IPSec)**
  - **Citrix**
  - **Anpassat VPN**

    > [!NOTE]
    > - **Cisco Legacy AnyConnect VPN**-profiler är för [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-appversion 4.0.5x och äldre versioner
    > - **Cisco AnyConnect VPN**-profiler är för [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-appversion 4.0.7x och nyare versioner

- **Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.

## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** som anslutningstyp kan du även konfigurera följande inställningar:

- **VPN-ID** En identifierare för VPN-appen som du använder och som tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för de anpassade VPN-attributen** Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.

## <a name="apps-per-app-vpn-settings"></a>Inställningar för appar (per app-VPN)

- **Per app-VPN**: Aktivera det här alternativet om du vill använda webbadresser som aktiverar VPN-anslutningen när de besöks i Safari-webbläsaren. Om du vill konfigurera en per app-VPN måste du välja **Certifikat** som autentiseringsmetod i de grundläggande VPN-inställningarna.
  - **Safari-webbadresser som utlöser denna VPN**: Välj det här alternativet för att lägga till en eller flera webbadresser. VPN-anslutningen aktiveras när de här webbadresserna besöks.

- **VPN på begäran**: Konfigurera villkorliga regler som styr när VPN-anslutningen ska initieras. Du kan till exempel skapa ett villkor där VPN-anslutningen endast används när en enhet inte är ansluten till ett trådlöst företagsnätverk. Du kan även skapa ett villkor där VPN-anslutningen inte initieras om enheten inte får åtkomst till en DNS-sökdomän som du har angett.

  - **SSID:n eller DNS-sökdomäner**: Välj om det här villkoret ska använda det trådlösa nätverkets **SSID:n** eller **DNS-sökdomäner**. Välj **Lägg till** för att konfigurera en eller flera SSID:er eller sökdomäner.
  - **URL-strängavsökning**: Valfritt. Ange en URL som regeln använder som ett test. Om den enhet där profilen har installerats får tillgång till den här webbadressen utan omdirigering startas VPN-anslutningen och enheten ansluter till målwebbadressen. Användaren ser inte URL-strängens avsökningsplats. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att webbadressen testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till målwebbadressen via VPN.
  - **Domänåtgärd**: Välj något av följande:
    - Anslut vid behov
    - Anslut aldrig
  - **Åtgärd**: Välj något av följande:
    - Ansluta
    - Utvärdera anslutning
    - Ignorera
    - Koppla från

## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Adress**: Ange IP-adressen för det fullt kvalificerade värdnamnet för proxyservern.
- **Portnummer**: Ange det portnummer som är associerat med proxyservern.

## <a name="next-step"></a>Nästa steg
[Skapa VPN-profiler i Intune](vpn-settings-configure.md)