---
title: Lägga till VPN-inställningar för enheter i Microsoft Intune – Azure | Microsoft Docs
description: För Android-, Android Enterprise-, iOS-, macOS- och Windows-enheter använder du inbyggda inställningar för att skapa anslutningar för virtuella privata nätverk (VPN) i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59a1b5679b81a8de90e39d6ec13bbe87dac90947
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984174"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Skapa VPN-profiler för att ansluta till VPN-servrar i Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheter använder en VPN-anslutningsprofil för att initiera en anslutning till VPN-servern. **VPN-profiler** i Microsoft Intune tilldelar VPN-inställningar till användare och enheter i din organisation så att de enkelt och säkert kan ansluta till nätverket.

Exempel: Du vill konfigurera alla enheter som kör iOS med de inställningar som krävs för att ansluta till en filresurs i företagsnätverket. Du skapar en VPN-profil som innehåller de här inställningarna. Sedan tilldelar du den här profilen till alla användare som har iOS-enheter. Användarna ser VPN-anslutningen i listan med tillgängliga nätverk och kan enkelt ansluta.

> [!NOTE]
> Du kan använda [anpassade konfigurationsprinciper i Intune](custom-settings-configure.md) för att skapa VPN-profiler för följande plattformar:
>
> * Android 4 och senare
> * Registrerade enheter som kör Windows 8.1 och senare
> * Windows Phone 8.1 och senare
> * Registrerade enheter som kör Windows 10 desktop och senare
> * Windows 10 Mobil
> * Windows 10 Holographic for Business

## <a name="vpn-connection-types"></a>VPN-anslutningstyper

Du kan skapa VPN-profiler med följande anslutningstyper:

|Anslutningstyp|Plattform|
|-|-|
|Automatiskt|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Android Enterprise-arbetsprofiler<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Android Enterprise-arbetsprofiler<br/>- Ägare av Android Enterprise-enhet (helt hanterad)<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Android Enterprise-arbetsprofiler: Använd [konfigurationsprincip för app](../apps/app-configuration-policies-use-android.md)<br/>– Ägare av Android Enterprise-enhet (helt hanterad): Använd [konfigurationsprincip för app](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|Anpassat VPN|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Android Enterprise-arbetsprofiler<br/>- Ägare av Android Enterprise-enhet (helt hanterad)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Android Enterprise-arbetsprofiler: Använd [konfigurationsprincip för app](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Android Enterprise-arbetsprofiler<br/>- Ägare av Android Enterprise-enhet (helt hanterad)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Android Enterprise-arbetsprofiler<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Android Enterprise-arbetsprofiler: Använd [konfigurationsprincip för app](../apps/app-configuration-policies-use-android.md)<br/>- iOS|

> [!IMPORTANT]
> Innan du kan använda de VPN-profiler som har tilldelats till en enhet måste du installera lämplig VPN-app för profilen. Använd informationen i artikeln [Vad är apphantering i Microsoft Intune?](../apps/app-management.md) när du ska tilldela appar med hjälp av Intune.  

Läs om hur du skapar anpassade VPN-profiler med hjälp av URI-inställningarna i [Skapa en profil med anpassade inställningar](custom-settings-configure.md).

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett bra profilnamn är t.ex. **VPN-profil för hela företaget**.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform för dina enheter. Alternativen är:

      - **Android**
      - **Android Enterprise** > **endast enhetsägare**
      - **Android Enterprise** > **endast arbetsprofil**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 och senare**
      - **Windows 10 och senare**

    - **Profiltyp**: Välj **VPN**.

4. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Se följande artiklar om du vill se detaljerade inställningar på respektive plattform:

    - [Inställningar för Android](vpn-settings-android.md)
    - [Inställningar för Android Enterprise](vpn-settings-android-enterprise.md)
    - [Inställningar för iOS/iPadOS](vpn-settings-ios.md)
    - [Inställningar för macOS](vpn-settings-macos.md)
    - [Inställningar för Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 8.1](vpn-settings-windows-8-1.md)
    - [Windows 10 settings](vpn-settings-windows-10.md) (Inställningar för Windows 10) (inklusive Windows Holographic for Business)

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i profillistan. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).

## <a name="secure-your-vpn-profiles"></a>Skydda dina VPN-profiler

VPN-profiler kan använda ett antal olika anslutningstyper och protokoll från olika tillverkare. Dessa anslutningar skyddas vanligtvis med följande metoder.

### <a name="certificates"></a>Certifikat

När du skapar VPN-profilen väljer du en SCEP- eller PKCS-certifikatprofil som du tidigare har skapat i Intune. Profilen kallas för identitetscertifikat. Det används för att autentisera mot en betrodd certifikatprofil (eller ett *rotcertifikat*) som du har skapat för att användarens enhet ska få ansluta. Det betrodda certifikatet tilldelas datorn som autentiserar VPN-anslutningen, vanligtvis VPN-servern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Microsoft Intune](../protect/certificates-configure.md).

### <a name="user-name-and-password"></a>Användarnamn och lösenord

Användaren autentiseras mot VPN-servern genom att ange användarnamn och lösenord.

## <a name="next-steps"></a>Nästa steg

När profilen har skapats gör den ingenting ännu. Härnäst [tilldela profilen](device-profile-assign.md) till några enheter.

Du kan också skapa och använda VPN per app på [Android-](android-pulse-secure-per-app-vpn.md) och [iOS-](vpn-setting-configure-per-app.md)-enheter.
