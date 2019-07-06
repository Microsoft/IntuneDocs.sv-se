---
title: Ta bort din iOS-enhet från Intune | Microsoft Docs
description: Beskriver hur du tar bort en iOS-enhet från Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 210a11cbd6e2c3be85ed0b0f97c2bb4ab59d11e6
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546603"
---
# <a name="remove-your-ios-device-from-intune"></a>Ta bort din iOS-enhet från Intune

När du tar bort din iOS-enhet från Intune, har enheten inte längre åtkomst till företagets resurser och hanteras inte längre av Intune.


## <a name="removing-the-device-from-my-devices"></a>Ta bort enheten från Mina enheter

Gör enligt följande om du vill ta bort enheten från Intune, eller titta på denna video:


1. Tryck på **Enheter** i företagsportalappen. och välj den enhet som du vill avregistrera. Om du bara har en enhet kommer du direkt till skärmen Enhetsinformation när du trycker på **Enheter**.

2. Bredvid **Byt namn** trycker du på ellipserna > **Ta bort enhet** > **Ta bort**.  

    |![Skärmbild av företagsportalappens enhetsskärm som visar alternativ när användaren har klickat på Ta bort. Visar knapparna ”Ta bort enhet” och ”Fabriksåterställning” och ”Avbryt”.](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![Skärmbild av företagsportalappens enhetsskärm som visar alternativ när användaren har klickat på knappen Ta bort enhet. Visar en röd ”Ta bort”-knapp, en blå ”Mer information”-knapp och en ”Avbryt”-knapp.](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


  När du avregistrerar en enhet från Intune händer följande:

  - Enheten visas inte på företagsportalen längre.

  - Det går inte att installera appar från företagsportalen längre.

  - Inställningar som ändrades på enheten när du lade till den, exempelvis inaktivering av kameran eller att en viss längd på lösenorden krävdes, gäller inte längre.

  - Eventuellt har du inte åtkomst till vissa företagsresurser från din enhet längre, exempelvis fildelningar eller interna webbplatser.

  - Det går inte att använda företagsappar eller företagsdata på enheten längre.

  - Eventuellt går det inte längre att ansluta till företagets nätverk via Wi-Fi eller VPN.

  - Företagets e-profiler tas bort från enheten.

  - Enheter som bara är konfigurerade för e-post visas inte längre i företagsportalappen eller på webbplatsen.
  
  - Apparna avinstalleras. Data som hör till företagsappar tas bort.

## <a name="removing-data-collected-by-the-company-portal-app"></a>Ta bort data som samlas in av företagsportalappen

Det finns tre platser där företagsportalen lagrar lokala data på enheten.

- **Informationsloggar**: Standardappens aktivitetsdata som Microsoft samlar in, t.ex. hur länge appen var öppen eller om den kraschade, raderas automatiskt när du tar bort enheten från företagsportalen.

- **Apple-analys**: Standardappens aktivitetsdata om krascher som Apple samlar in. Den här informationen kan bara tas bort genom att återställa enheten till fabriksinställningarna. All personlig information raderas på enheten. Gör detta genom att öppna **Inställningar** > **Allmänt** > **Återställ** > **Radera allt innehåll och alla inställningar**.

- **Nyckelring**: Enheten lagrar dina lösenord och annan information som används för inloggning i nyckelringen. Microsoft-appar delar din inloggningsinformation i Microsoft-utvecklade appar som du har på enheten, till exempel Microsoft Outlook och Microsoft Authenticator. Precis som i Apple-analysen kan den här informationen bara tas bort genom att återställa enheten till fabriksinställningarna. All personlig information raderas på enheten. Gör detta genom att öppna **Inställningar** > **Allmänt** > **Återställ** > **Radera allt innehåll och alla inställningar**.


Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
