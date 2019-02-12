---
title: Konfigurera VPN-inställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: När du skapar en VPN-konfigurationsprofil för Android- och Android for Work-enheter anger du anslutningsnamnet, IP-adressen eller FQDN för VPN-servern, väljer hur användare autentiserar med VPN-servern och väljer sedan anslutningstyperna Citrix, SonicWall, Check Point Capsule, Pulse Secure samt Microsoft Edge.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f37d19beddd96fdad63c61d83b0012869a7f9cd3
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843722"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Konfigurera VPN-inställningar för enheter som kör Android i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda till att konfigurera VPN-anslutningar på enheter som kör Android.

Du kan konfigurera VPN-inställningar för följande plattformar:

- [Android](#android-vpn-settings)
- [Android enterprise](#android-enterprise-vpn-settings)

Beroende på vilka inställningar du väljer kan bara vissa av följande värden konfigureras.

## <a name="android-vpn-settings"></a>VPN-inställningar för Android

- **Anslutningens namn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga VPN-anslutningar.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.

  - **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. Alternativen är:

    - **Certifikat**: Välj en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) visar stegen för att skapa en certifikatprofil.
    - **Användarnamn och lösenord**: Vid inloggning till VPN-servern uppmanas slutanvändarna att ange ett användarnamn och lösenord.

- **Anslutningstyp**: Välj VPN-anslutningstyp. Alternativen är:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **Fingeravtryck** (endast Check Point Capsule VPN): Ange en sträng, till exempel **Contoso fingeravtryckskod**, för att verifiera att VPN-servern är betrodd. Ett fingeravtryck kan skickas till klienten så att den vet att den ska lita på alla servrar som har samma fingeravtryck vid anslutningen. Om enheten inte har fingeravtrycket uppmanar den användaren att lita på VPN-servern medan fingeravtrycket visas. Användaren verifierar fingeravtrycket manuellt och väljer betrodd för att ansluta.
- **Ange nyckel och värdepar för Citrix VPN-attributen** (endast Citrix): Ange nyckel och värdepar som tillhandahålls av Citrix. Dessa värden konfigurerar egenskaperna för VPN-anslutningen.

## <a name="android-enterprise-vpn-settings"></a>VPN-inställningar för Android Enterprise

- **Anslutningens namn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga VPN-anslutningar.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.

  - **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. Alternativen är:
  
    - **Certifikat**: Välj en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) visar stegen för att skapa en certifikatprofil.
    - **Användarnamn och lösenord**: Vid inloggning till VPN-servern uppmanas slutanvändarna att ange ett användarnamn och lösenord.

- **Anslutningstyp**: Välj VPN-anslutningstyp. Alternativen är:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="next-steps"></a>Nästa steg
[VPN-profiler i Intune](vpn-settings-configure.md)
