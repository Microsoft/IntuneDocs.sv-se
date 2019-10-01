---
title: Använd VPN-inställningar för Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att skapa VPN-anslutningar på Android-enheter i Microsoft Intune. Ange anslutnings namn, IP-adress eller FQDN för VPN-servern, Välj hur användare autentiseras och välj Citrix, SonicWall, Check Point kapsel och Pulse Secure Connection types.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36806769e3b4c2c726038c23edf22cb006819d8c
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2019
ms.locfileid: "71302800"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>Inställningar för Android-enhet för att konfigurera VPN i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln beskriver de olika inställningar för VPN-anslutningar som du kan styra på Android-enheter. Som en del av din lösning för hantering av mobila enheter (MDM) använder du de här inställningarna för att skapa en VPN-anslutning, väljer hur VPN-autentiseringen ska autentiseras, väljer en VPN-server typ med mera.

Som Intune-administratör kan du skapa och tilldela VPN-inställningar till dina Android-enheter. 

Mer information om VPN-profiler i Intune finns i [VPN-profiler](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en profil för enhetskonfiguration](vpn-settings-configure.md#create-a-device-profile) och välj **Android**.

## <a name="base-vpn"></a>Bas-VPN

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga VPN-anslutningar. Ange till exempel `Contoso VPN`.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.

  - **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. Alternativen är:

    - **Certifikat**:Välj en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) visar stegen för att skapa en certifikatprofil.
    - **Användarnamn och lösenord**: Vid inloggning till VPN-servern uppmanas slutanvändarna att ange ett användarnamn och lösenord.

- **Anslutningstyp**: Välj VPN-anslutningstyp. Alternativen är:

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **Fingeravtryck** (endast Check Point Capsule VPN): Ange en sträng, till exempel **Contoso fingeravtryckskod**, för att verifiera att VPN-servern är betrodd. Ett finger avtryck skickas till klienten så att klienten kan lita på alla servrar som har samma finger avtryck. Om enheten inte har fingeravtrycket uppmanar den användaren att lita på VPN-servern medan fingeravtrycket visas. Användaren verifierar fingeravtrycket manuellt och väljer betrodd för att ansluta.
- **Ange nyckel-värdepar för Citrix VPN-attributen** (endast Citrix): Ange nyckel- och värdepar som tillhandahålls av Citrix. Dessa värden konfigurerar egenskaperna för VPN-anslutningen. 

  Du kan också **Importera** en fil med kommaavgränsade värden (. csv) med nycklar och värdepar. Se till att granska **mina data har rubriker** och **nyckel** egenskaper.

  När du har lagt till dina nyckel-och värdepar använder du **Exportera** för att säkerhetskopiera dina data till en. csv-fil.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa VPN-profiler för [Android Enterprise](vpn-settings-android-enterprise.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 och senare](vpn-settings-windows-10.md), [Windows 8,1](vpn-settings-windows-8-1.md)och [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) -enheter.
