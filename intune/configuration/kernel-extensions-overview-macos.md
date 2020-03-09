---
title: Skapa enhetsprofil för macOS-kerneltillägg med Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till eller skapa en macOS-enhetsprofil och konfigurera sedan kerneltillägg för att tillåta användaråsidosättning samt lägg till teamidentifierare och ett paket och teamidentifierare i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/25/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8a516ce9dda525d5c7a48fcbc2c799471489d0d
ms.sourcegitcommit: ff254acb94df88afc3e3e7b878084052adf40745
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77600240"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Lägg till macOS kernel-tillägg i Intune

> [!NOTE]
> macOS kernel-tillägg håller på att ersättas med systemtillägg. Mer information finns i [Supporttips: Användning av systemtillägg i stället för kernel-tillägg för macOS Catalina 10.15 i Intune](https://techcommunity.microsoft.com/t5/intune-customer-success/support-tip-using-system-extensions-instead-of-kernel-extensions/ba-p/1191413).

På macOS-enheter kan du lägga till funktioner på kernelnivå. Dessa funktioner kommer åt delar av operativsystemet som vanliga program inte har åtkomst till. Din organisation kan ha särskilda behov eller krav som inte är tillgängliga i en app, en enhetsfunktion och så vidare. 

Om du vill lägga till kerneltillägg som alltid får läsas in på dina enheter lägger du till "kernel extensions" (KEXT) i Microsoft Intune och distribuerar sedan tilläggen till dina enheter.

Till exempel har du ett antivirusprogram som söker igenom enheten efter skadligt innehåll. Du kan lägga till det här antivirusprogrammets kerneltillägg som ett tillåtet kerneltillägg i Intune. Sedan "assign" (tilldelar) du tillägget till dina macOS-enheter.

Med den här funktionen kan administratörer tillåta att användare åsidosätter kerneltillägg, lägger till teamidentifierare och lägger till specifika kerneltillägg i Intune.

Den här funktionen gäller för:

- macOS 10.13.2 och senare

För användning av den här funktionen måste enheterna vara:

- Registrerade i Intune med hjälp av Apple-programmet för enhetsregistrering (DEP). Mer information finns i [Registrera macOS-enheter automatiskt](../enrollment/device-enrollment-program-enroll-macos.md).

  ELLER

- Registrerade i Intune med "user approved enrollment" (användargodkänd registrering, term från Apple). Mer information finns i [Förbered för ändringar av kerneltillägg i macOS High Sierra](https://support.apple.com/en-us/HT208019) (öppnar Apple-webbplatsen).

Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till macOS-enheter i din organisation.

Den här artikeln beskriver hur du skapar en enhetskonfigurationsprofil med hjälp av kerneltillägg i Intune.

> [!TIP]
> Mer information om kerneltillägg finns i [översikten av kerneltillägg](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (öppnar Apple-webbplatsen).

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- Osignerade äldre kerneltillägg kan läggas till.
- Se till att ange rätt teamidentifierare och paket-ID för kerneltillägget. Intune validerar inte de värden som du anger. Om du anger fel information fungerar inte tillägget på enheten. En teamidentifierare består av exakt 10 alfanumeriska tecken. 

> [!NOTE]
> Apple har publicerat information om signering och notarisering för all programvara. I macOS 10.14.5 och senare behöver kerneltillägg som distribueras via Intune inte uppfylla Apples notariseringsprincip.
>
> Information om den här notariseringsprincipen och eventuella uppdateringar eller ändringar finns i följande resurser:
>
> - [Notarisera din app före distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (öppnar Apple-webbplatsen) 
> - [Förbered för ändringar av kerneltillägg i macOS High Sierra](https://support.apple.com/en-us/HT208019) (öppnar Apple-webbplatsen)

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **macOS**
    - **Profiltyp**: Välj **Tillägg**.
    - **Inställningar**: Ange vilka inställningar som du vill konfigurera. En lista med alla inställningar och vad de gör finns i:

        - [macOS](kernel-extensions-settings-macos.md)

4. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

Profilen skapas och visas i listan. Kom ihåg att [tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).
