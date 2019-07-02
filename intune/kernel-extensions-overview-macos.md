---
title: Skapa macOS-enhetsprofil för kernel-tillägg med Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till eller skapa en macOS-enhetsprofil och konfigurera kernel-tillägg för att tillåta åsidosättning av användare, lägga till team-ID och ett paket och team-ID i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403912"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Lägg till kernel-tillägg för macOS i Intune

Du kan lägga till funktioner på macOS-enheter på kernel-nivå. De här funktionerna åtkomst till delar av Operativsystemet som inte kan komma åt vanliga program. Din organisation kan ha specifika behov eller krav som inte är tillgängliga i en app, en funktion för enheten och så vidare. 

Lägg till kernel-tillägg som tillåts alltid att läsa in på dina enheter genom att lägga till ”kernel-tillägg” (KEXT) i Microsoft Intune och sedan distribuera dessa tillägg till dina enheter.

Exempelvis kan ha du ett antivirusprogram som söker igenom din enhet efter skadlig kod. Du kan lägga till den här virusgenomsökning programmets kernel-tillägget som en utökning av tillåtna kernel i Intune. ”Tilldela sedan” tillägget till din macOS-enheter.

Med den här funktionen kan administratörer tillåta användare att åsidosätta kernel-tillägg, Lägg till team identifierare och lägga till specifika kernel-tillägg i Intune.

Den här funktionen gäller för:

- macOS 10.13.2 och senare

Om du vill använda den här funktionen måste måste enheterna vara:

- Har registrerats i Intune med Apples Device Enrollment Program (DEP). [Registrera macOS-enheter automatiskt](device-enrollment-program-enroll-macos.md) innehåller mer information.

  ELLER

- Har registrerats i Intune med ”användargodkänd registrering” (Apples villkor). [Förbereda för ändringar av kernel-tillägg i macOS High Sierra](https://support.apple.com/en-us/HT208019) (öppnas Apples webbplats) innehåller mer information.

Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till macOS-enheter i din organisation.

Den här artikeln visar hur du skapar en profil för enhetskonfiguration använder kernel-tillägg i Intune.

> [!TIP]
> Mer information om kernel-tillägg finns i [översikt över kernel-tillägget](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (öppnas Apples webbplats).

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- Osignerade äldre kernel-tillägg kan läggas till.
- Glöm inte att ange rätt team-ID och appsamlings-ID för kernel-tillägget. Intune verifierar inte de värden som du anger. Om du anger fel information fungerar inte tillägget på enheten.

> [!NOTE]
> Apple släppt information om signering och notarization för all programvara. I macOS 10.14.5 och nyare, kernel-tillägg som distribueras via Intune inte behöver uppfylla Apples notarization princip.
>
> Information om den här notarization-principen och eventuella uppdateringar eller ändringar finns i följande resurser:
>
>  - [Notarizing din app innan distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (öppnas Apples webbplats) 
>  - [Förbereda för ändringar av kernel-tillägg i macOS High Sierra](https://support.apple.com/en-us/HT208019) (öppnas Apples webbplats)

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **macOS**
    - **Profiltyp**: Välj **tillägg**.
    - **Inställningar**: Ange vilka inställningar som du vill konfigurera. En lista med alla inställningar och vad de gör finns i:

        - [macOS](kernel-extensions-settings-macos.md)

4. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i listan. Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
