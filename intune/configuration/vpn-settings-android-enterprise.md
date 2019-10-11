---
title: Använd VPN-inställningar för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Se alla inställningar för att skapa VPN-anslutningar på Android Enterprise-enheter i Microsoft Intune. Ange anslutnings namn, IP-adress eller FQDN för VPN-servern, Välj hur användare autentiseras och välj Citrix, SonicWall, Check Point kapsel och Pulse Secure Connection types.
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
ms.openlocfilehash: 642e054f7ba400fcc8b38b83ba19731c8e0998da
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734173"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Inställningar för Android Enterprise-enhet för att konfigurera VPN i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln beskriver de olika inställningar för VPN-anslutningar som du kan styra på Android Enterprise-enheter. Som en del av din lösning för hantering av mobila enheter (MDM) använder du de här inställningarna för att skapa en VPN-anslutning, väljer hur VPN-autentiseringen ska autentiseras, väljer en VPN-server typ med mera.

Som Intune-administratör kan du skapa och tilldela VPN-inställningar till dina Android Enterprise-enheter. 

Mer information om VPN-profiler i Intune finns i [VPN-profiler](vpn-settings-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en profil för enhetskonfiguration](vpn-settings-configure.md#create-a-device-profile) och välj **Android Enterprise**.

## <a name="device-owner-only"></a>Endast enhetens ägare

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga VPN-anslutningar. Ange till exempel `Contoso VPN`.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.

  - **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. Alternativen är:
  
    - **Certifikat**:Välj en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](../protect/certificates-configure.md) visar stegen för att skapa en certifikatprofil.
    - **Användarnamn och lösenord**: Vid inloggning till VPN-servern uppmanas slutanvändarna att ange ett användarnamn och lösenord.

- **Anslutningstyp**: Välj VPN-anslutningstyp. Alternativen är:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>Endast arbetsprofil

- **Anslutningsnamn**: Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten efter tillgängliga VPN-anslutningar. Ange till exempel `Contoso VPN`.
- **IP-adress eller fullständigt domännamn**: Ange IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**.

  - **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. Alternativen är:
  
    - **Certifikat**:Välj en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](../protect/certificates-configure.md) visar stegen för att skapa en certifikatprofil.
    - **Användarnamn och lösenord**: Vid inloggning till VPN-servern uppmanas slutanvändarna att ange ett användarnamn och lösenord.

- **Anslutningstyp**: Välj VPN-anslutningstyp. Alternativen är:

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa VPN-profiler för [Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), [MacOS](vpn-settings-macos.md), [Windows 10 och senare](vpn-settings-windows-10.md), [Windows 8,1](vpn-settings-windows-8-1.md)och [Windows Phone 8,1](vpn-settings-windows-phone-8-1.md) -enheter.
