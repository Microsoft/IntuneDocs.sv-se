---
title: Lägga till anpassade inställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Exportera iOS-inställningar från Apple Configurator eller Apples Profile Manager och importera sedan dessa inställningar till Microsoft Intune. De här inställningarna kan skapa, använda och kontrollera anpassade inställningar och funktioner på iOS-enheter. Den här anpassade profilen kan sedan tilldelas eller distribueras till iOS-enheter i din organisation för att skapa en baslinje eller standard.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4f9f3cabf0826380dfd97b9c0f772f9846912f0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530259"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Använda anpassade inställningar för iOS-enheter i Microsoft Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina iOS-enheter med hjälp av ”anpassade profiler”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

När du använder iOS-enheter kan du hämta anpassade inställningar till Intune på två sätt:

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

Du kan använda dessa verktyg för att exportera inställningar till en konfigurationsprofil. I Intune importerar du den här filen och tilldelar sedan profilen till dina iOS-användare och iOS-enheter. När de har tilldelats distribueras inställningarna och en baslinje eller standard skapas för iOS i din organisation.

Den här artikeln beskriver hur du skapar en anpassad profil för iOS-enheter. Den innehåller även viss vägledning om hur du använder Apple Configurator och Apple Profile Manager.

## <a name="before-you-begin"></a>Innan du börjar

- När du använder **Apple Configurator** för att skapa konfigurationsprofilen måste du kontrollera att de inställningar som du exporterar är kompatibla med iOS-versionen på de enheter som du använder. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

- Om du använder **Apple Profile Manager** måste du göra följande:

  - Aktivera [hantering av mobila enheter](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C) i Profile Manager.
  - Lägg till [iOS-enheter](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984) i Profile Manager.
  - När du har lagt till en enhet i Profile Manager går du till **Under biblioteket** > **Enheter** > välj din enhet > **Inställningar**. Ange allmänna inställningar för enheten.

    Hämta och spara den här filen. Du ska lägga till den här filen i Intune-profilen.

  - Kontrollera att de inställningar som du exporterar från Apple Profile Manager är kompatibla med iOS-versionen på de enheter som du använder. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `ios custom profile`.
    - **Beskrivning:** Ange en beskrivning för profilen.
    - **Plattform**: Välj **iOS**.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Anpassad konfiguration** anger du följande inställningar:

    - **Anpassat namn på konfigurationsprofil**: Ange ett namn för principen. Det här namnet visas på enheten och i Intune-statusen.
    - **Konfigurationsprofilfil**: Bläddra till konfigurationsprofilen som du skapade med Apple Configurator eller Apple Profile Manager. Filen som du importerade visas i området **Filinnehåll**.

5. Välj **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).

Se hur du [skapar profilen på macOS-enheter](custom-settings-macos.md). 
