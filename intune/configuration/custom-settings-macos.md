---
title: Lägga till anpassade inställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Exportera macOS-inställningar från Apple Configurator eller Apples Profile Manager och importera sedan dessa inställningar till Microsoft Intune. De här inställningarna kan skapa, använda och kontrollera anpassade inställningar och funktioner på macOS-enheter. Den här anpassade profilen kan sedan tilldelas eller distribueras till macOS-enheter i din organisation för att skapa en baslinje eller standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 492c90bc1d032b32ebc3a4b8465163085674f245
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511454"
---
# <a name="use-custom-settings-for-macos-devices-in-microsoft-intune"></a>Använda anpassade inställningar för macOS-enheter i Microsoft Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina macOS-enheter med hjälp av en ”anpassad profil”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

När du använder macOS-enheter kan du hämta anpassade inställningar till Intune på två sätt:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Du kan använda dessa verktyg för att exportera inställningar till en konfigurationsprofil. I Intune importerar du den här filen och tilldelar sedan profilen till dina macOS-användare och macOS-enheter. Inställningarna distribueras så snarat de har tilldelats. De skapar också en baslinje eller standard för macOS i din organisation.

Den här artikeln innehåller riktlinjer om hur man använder Apple Configurator och Apple Profile Manager och beskriver de egenskaper som du kan konfigurera.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa profilen](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- När du använder **Apple Configurator** för att skapa konfigurationsprofilen måste du kontrollera att de inställningar som du exporterar är kompatibla med macOS-versionen på enheterna. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

- Om du använder **Apple Profile Manager** måste du göra följande:

  - Aktivera [hantering av mobila enheter](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) i Profile Manager.
  - Lägg till [macOS-enheter](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) i Profile Manager.
  - När du har lagt till en enhet i Profile Manager går du till **Under biblioteket** > **Enheter** > välj din enhet > **Inställningar**. Ange allmänna inställningar och säkerhets-, sekretess-, katalog- och certifikatinställningar för enheten.

    Hämta och spara den här filen. Du ska lägga till den här filen i Intune-profilen. 

  - Kontrollera att de inställningar som du exporterar från Apple Profile Manager är kompatibla med macOS-versionen på enheterna. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

## <a name="custom-configuration-profile-settings"></a>Anpassade inställningar för konfigurationsprofil

- **Anpassat namn på konfigurationsprofil**: Ange ett namn för principen. Det här namnet visas på enheten och i Intune-statusen.
- **Konfigurationsprofilsfil**: Bläddra till den konfigurationsprofil som du skapade med Apple Configurator eller Apple Profile Manager. Filen som du importerade visas i området **Filinnehåll**.

  Du kan också lägga till enhetstokens till dina `.mobileconfig`-filer. Enhetstoken används för att lägga till enhetsspecifik information. Ange till exempel `{{serialnumber}}` om du vill visa serienumret. På enheten visas texten på ungefär samma sätt som `123456789ABC`, som är unikt för varje enhet. När du anger variabler ska du använda klammerparenteser `{{ }}`. [Token för appkonfiguration](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) innehåller en lista över variabler som kan användas. Du kan också använda `deviceid` eller andra enhetsspecifika värden.

  > [!NOTE]
  > Variablerna är inte validerade i användargränssnittet och är skiftlägeskänsliga. Därför kan du se profiler sparade med felaktiga indata. Om du till exempel anger `{{DeviceID}}` istället för `{{deviceid}}` visas litteralsträngen istället för enhetens unika ID. Se till att du anger rätt information.

Välj **OK** > **Skapa** för att spara ändringarna. Profilen skapas och visas i profillistan.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).

Se hur du kan [skapa profilen på iOS/iPadOS-enheter](../custom-settings-ios.md).
