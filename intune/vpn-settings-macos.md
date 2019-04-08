---
title: VPN-inställningar i Microsoft Intune för macOS-enheter
titleSuffix: ''
description: Läs mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på macOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f752ec33ca7a69d698ffe2c06c726f3881cc35ce
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798452"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-macos"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda till att konfigurera VPN-anslutningar på enheter som kör macOS.

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
    - **Anpassat VPN**
- **Delade tunnlar** - **Aktivera** eller **Inaktivera** det här alternativet för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** kan du konfigurera inställningarna ytterligare:

- **VPN-ID** Detta är en identifierare för VPN-appen som du använder och den tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för de anpassade VPN-attributen** Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.


## <a name="proxy-settings"></a>Proxyinställningar

- **Skript för automatisk konfigurering** – Använd en fil för att konfigurera proxyservern. Ange den **URL för proxyserver** som innehåller konfigurationsfilen. Ange till exempel `http://proxy.contoso.com`.
- **Adress** – Ange proxyns serveradress (som en IP-adress).
- **Portnummer** – Ange det portnummer som är kopplat till proxyservern.
