---
title: Per-app-anpassad VPN-profil för Android
titleSuffix: Microsoft Intune
description: Du kan skapa en VPN-profil per app för Android-enheter som hanteras av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d035ebf5-85f4-4001-a249-75d24325061a
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62f418e396c5030a47ea0bcb31914cd4e1069c40
ms.sourcegitcommit: eb2e420b304c7da9d3be5ef49a676cba66766d2b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74319846"
---
# <a name="use-a-microsoft-intune-custom-profile-to-create-a-per-app-vpn-profile-for-android-devices"></a>Använd en anpassad Microsoft Intune-profil för att skapa en VPN-profil per app för Android-enheter

Du kan skapa en VPN-profil per app för enheter som kör Android 5.0 och senare som hanteras av Intune. Börja med att skapa en VPN-profil som använder antingen Pulse Secure- eller Citrix-anslutningstypen. Skapa sedan en princip för anpassad konfiguration som associerar VPN-profilen med specifika appar.

> [!NOTE]
> Om du vill använda VPN per app på Android Enterprise-enheter kan du också använda de här stegen. Men vi rekommenderar att du använder en [konfigurationsprincip för appar](../apps/app-configuration-policies-use-android.md) för VPN-klientprogramvaran.

När du har tilldelat principen till din Android-enhet eller till användargrupper måste användarna starta Pulse Secure- eller Citrix VPN-klienten. VPN-klienten tillåter då endast trafik från de angivna apparna att använda den öppna VPN-anslutningen.

> [!NOTE]
>
> Endast anslutningstyperna Pulse Secure och Citrix stöds för den här profilen.

## <a name="step-1-create-a-vpn-profile"></a>Steg 1: Skapa en VPN-profil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett exempel på ett bra profilnamn är **Android per-app VPN profile for entire company** (VPN-profil per Android-app för hela företaget).
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Android**.
    - **Profiltyp**: Välj **VPN**.

4. Välj **Inställningar** > **Konfigurera**. Konfigurera sedan VPN-profilen. Mer information finns i [Konfigurera VPN-inställningar](vpn-settings-configure.md) och [Intune VPN-inställningar för Android-enheter](vpn-settings-android.md).

Notera **anslutningens namn** , det vill säga det värde som du anger när du skapar VPN-profilen. Detta krävs i nästa steg. Till exempel **MyAppVpnProfile**.

## <a name="step-2-create-a-custom-configuration-policy"></a>Steg 2: Skapa en anpassad konfigurationsprincip

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn för den anpassade profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett exempel på ett bra profilnamn är **Custom OMA-URI Android VPN profile for entire company** (Anpassad OMA-URI VPN-profil för Android för hela företaget).
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Android**.
    - **Profiltyp**: Välj **Anpassad**.

4. Välj **Inställningar** > **Konfigurera**.
5. I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
    - **Namn**: Ange ett namn för inställningen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **OMA-URI**: Ange `./Vendor/MSFT/VPN/Profile/*Name*/PackageList`, där *Namn* är anslutningsnamnet som du antecknade i steg 1. I det här exemplet är strängen `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList`.
    - **Datatyp**: Ange **String**.
    - **Värde**: Ange en semikolonavgränsad lista med paket som ska associeras med profilen. Om du till exempel vill att Excel och webbläsaren Google Chrome ska använda VPN-anslutningen anger du `com.microsoft.office.excel;com.android.chrome`.

![Exempel på VPN-anpassad princip per app för Android](./media/android-pulse-secure-per-app-vpn/android_per_app_vpn_oma_uri.png)

### <a name="set-your-app-list-to-blacklist-or-whitelist-optional"></a>Ange applistan som svartlistad eller vitlistad (valfritt)

Du kan ange en lista över appar som *inte* kan använda VPN-anslutningen med hjälp av värdet **BLACKLIST** (svartlistat). Alla andra appar ansluter via VPN. Eller så kan du använda värdet **WHITELIST** (vitlistat) för att ange en lista över appar som *får* använda VPN-anslutningen. Appar som inte finns med i listan ansluter inte via VPN-anslutningen.

1. I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till**.
2. Ange ett namn på inställningen.
3. I **OMA-URI** anger du `./Vendor/MSFT/VPN/Profile/*Name*/Mode`, där *Namn* är det VPN-profilnamn som du antecknade i steg 1. I vårt exempel är strängen `./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode`.
4. I **Datatyp** anger du **String**.
5. Under **Värde** anger du **SVARTLISTAT** eller **VITLISTAT**.

## <a name="step-3-assign-both-policies"></a>Steg 3: Tilldela båda principerna

[Tilldela båda enhetsprofilerna](device-profile-assign.md) till nödvändiga användare eller enheter.
