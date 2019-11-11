---
title: Skapa en enhets profil för macOS kernel Extensions med Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till eller skapa en macOS-enhets profil och konfigurera sedan kernel-tillägg så att användare åsidosätter, Lägg till Team-ID och ett paket-och grupp-ID i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e69f1b11833da0906aaf831f8bb82b04241e442f
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755182"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Lägga till macOS kernel-tillägg i Intune

På macOS-enheter kan du lägga till funktioner på kernel-nivå. Dessa funktioner kommer åt delar av operativ systemet som normala program inte har åtkomst till. Din organisation kan ha särskilda behov eller krav som inte är tillgängliga i en app, en enhets funktion och så vidare. 

Om du vill lägga till kernel-tillägg som alltid får läsas in på dina enheter lägger du till "kernel-tillägg" (KEXT) i Microsoft Intune och distribuerar sedan tilläggen till dina enheter.

Till exempel har du ett antivirus program som söker igenom enheten efter skadligt innehåll. Du kan lägga till det här Antivirus programmets kernel-tillägg som ett tillåtet kernel-tillägg i Intune. Tilldela sedan "tillägget till dina macOS-enheter.

Med den här funktionen kan administratörer tillåta att användare åsidosätter kernel-tillägg, lägger till Team identifierare och lägger till vissa kernel-tillägg i Intune.

Den här funktionen gäller för:

- macOS 10.13.2 och senare

Om du vill använda den här funktionen måste enheterna vara:

- Registreras i Intune med Apples Programmet för enhetsregistrering (DEP). [Registrera MacOS-enheter automatiskt](../enrollment/device-enrollment-program-enroll-macos.md) med mer information.

  ELLER

- Registreras i Intune med "User-godkänd registrering" (Apples). [Förbered för ändringar i kernel-tillägg i MacOS med hög Sierra](https://support.apple.com/en-us/HT208019) (öppnar Apples webbplats) har mer information.

Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till macOS-enheter i din organisation.

Den här artikeln visar hur du skapar en enhets konfigurations profil med hjälp av kernel-tillägg i Intune.

> [!TIP]
> Mer information om kernel-tillägg finns i [Översikt över kernel-tillägg](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (öppnar Apples webbplats).

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- Osignerade gamla kernel-tillägg kan läggas till.
- Se till att ange rätt team identifierare och paket-ID för kernel-tillägget. Intune validerar inte de värden du anger. Om du anger fel information fungerar inte tillägget på enheten.

> [!NOTE]
> Apple har publicerat information om signering och notarization för all program vara. I macOS 10.14.5 och senare behöver kernel-tillägg som distribueras via Intune inte uppfylla Apples notarization-princip.
>
> Information om den här notarization-principen och eventuella uppdateringar och ändringar finns i följande resurser:
>
> - [Notarizing din app före distributionen](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (öppnar Apples webbplats) 
> - [Förbered för ändringar i kernel-tillägg i MacOS med hög Sierra](https://support.apple.com/en-us/HT208019) (öppnar Apples webbplats)

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [administrations centret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **enheter** > **konfigurations profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **macOS**
    - **Profil typ**: Välj **tillägg**.
    - **Inställningar**: Ange vilka inställningar som du vill konfigurera. En lista med alla inställningar och vad de gör finns i:

        - [macOS](kernel-extensions-settings-macos.md)

4. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i listan. Kom ihåg att [tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).
