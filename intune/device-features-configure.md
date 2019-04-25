---
title: Skapa iOS- eller macOS-enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en iOS- eller macOS-enhetsprofil och konfigurera sedan inställningar för AirPrint, layout för startsidan, appmeddelanden, delad enhet, enkel inloggning och webbinnehållsfilter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ae03a4155fa2d170648548bb9a08b570f49c673
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509576"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Lägga till funktionsinställningar för iOS- eller macOS-enheter i Intune

Intune innehåller många funktioner och inställningar som hjälper administratörer styra iOS- och macOS-enheter. Administratörerna kan exempelvis:

- Ge användarna åtkomst till AirPrint-skrivare i nätverket
- Lägga till appar och mappar på startsidan, inklusive att lägga till nya sidor
- Välja om och hur appmeddelanden ska visas
- Konfigurera att låsskärmen visar ett meddelande eller en resurstagg, vilket är särskilt användbart för delade enheter
- Ge användarna en säker enkel inloggning för att kunna dela autentiseringsuppgifter mellan appar
- Filtrera webbplatser som innehåller språk som är olämpligt för barn, samt tillåta eller blockera vissa webbplatser

Dessa funktioner är tillgängliga i Intune och kan konfigureras av administratören. Intune använder ”konfigurationsprofiler” till att skapa och anpassa inställningarna efter din organisations behov. När du har lagt till dessa funktioner i en profil, kan du skicka eller distribuera profilen till iOS- och macOS-enheter i din organisation.

Den här artikeln beskriver hur du skapar en enhetskonfigurationsprofil. Artikeln innehåller även alla tillgängliga inställningar för [iOS](ios-device-features-settings.md)- och [macOS](macos-device-features-settings.md)-enheter.

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj din plattform:
        - **iOS**
        - **macOS**
    - **Profiltyp**: Välj **Enhetsfunktioner**.
    - **Inställningar**: Ange vilka inställningar som du vill konfigurera. En lista med alla inställningar och vad de gör finns i:

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. När du är klar väljer du **OK** och sedan **Skapa** för att spara dina ändringar.

Profilen skapas och visas i listan. Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

## <a name="next-steps"></a>Nästa steg

När profilen har skapats är den klar att tilldelas. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Visa alla enhetsfunktionsinställningar för [iOS](ios-device-features-settings.md)- och [macOS](macos-device-features-settings.md)-enheter.
