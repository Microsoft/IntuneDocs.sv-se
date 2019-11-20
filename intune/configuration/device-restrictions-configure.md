---
title: Begränsa enhetsfunktioner med principer i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till en enhetsprofil för att begränsa funktioner i Android-, macOS-, iOS-, iPadOS-, Windows Phone- och Windows 10-enheter i Microsoft Intune
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
ms.openlocfilehash: 704da2ee4f0f2e6dce222c89704c83a35368c02c
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059528"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Konfigurera inställningar för enhetsbegränsningar i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune innehåller principer för begränsning av enheter som hjälper administratörer att kontrollera Android-, iOS-, macOS-, och Windows-enheter. Med dessa begränsningar kan du kontrollera en mängd olika inställningar och funktioner för att skydda din organisations resurser. Administratörerna kan exempelvis:

- Tillåt eller blockera enhetens kamera
- Kontrollera åtkomst till Google Play, App Store, dokumentvisning och spel
- Blockera inbyggda appar eller skapa en lista över appar som tillåts eller blockeras
- Tillåt eller förhindra säkerhetskopiering av filer till moln- och lagringskonton
- Ange minsta längd på lösenord och blockera enkla lösenord

Dessa funktioner är tillgängliga i Intune och kan konfigureras av administratören. Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till enheter i din organisation.

Den här artikeln beskriver hur du skapar en enhetsbegränsningsprofil. Artikeln innehåller även alla tillgängliga inställningar för olika plattformar.

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på principen. Namnge dina principer så att du enkelt kan identifiera dem senare. Ett exempel på ett bra principnamn är **iOS: Blockera kameran på enheterna**.
    - **Beskrivning**: Ange en beskrivning av principen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform för dina enheter. Alternativen är:  

        - **Android**
        - **Android enterprise**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 och senare**
        - **Windows 10 och senare**

    - **Profiltyp**: Välj **Enhetsbegränsningar**.

        För att skapa en enhetsbegränsningsprofil för Windows 10 Team-enheter, som en Surface Hub, väljer du sedan **Enhetsbegränsningar (Windows 10 Team)** .

4. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Välj din plattform för detaljerade inställningar:

    - [Inställningar för Android](../device-restrictions-android.md)
    - [Inställningar för Android Enterprise](../device-restrictions-android-for-work.md)
    - [Inställningar för iOS/iPadOS](device-restrictions-ios.md)
    - [Inställningar för macOS](device-restrictions-macos.md)
    - [Inställningar för Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Inställningar för Windows 10](device-restrictions-windows-10.md)
    - [Inställningar för Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Inställningar för Windows Holographic for Business](device-restrictions-windows-holographic.md)

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i profillistan.

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
