---
title: "Återställa Intune-hanterade iOS-enheter från en säkerhetskopia"
description: "Ge vägledning till slutanvändare om hur de kan registrera sina enheter igen efter att enheterna blivit återställda från säkerhetskopior."
keywords: restore, managed, iOS
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 7fc99a944000a8d5ecfc09ebc2e956e7c0f201c9
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="restore-intune-managed-ios-devices-from-backup"></a>Återställa Intune-hanterade iOS-enheter från en säkerhetskopia

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I vissa fall kan du eller användarna komma att behöva återställa en iOS-enhet från en säkerhetskopia, till exempel när en användare får en ny enhet. Det här avsnittet beskriver ytterligare steg som du kan behöva utföra för att konfigurera Intune-hantering efter att enheten återställts.

## <a name="restoring-backups-onto-the-same-device"></a>Återställa säkerhetskopior på samma enhet

Om säkerhetskopian återställs på samma enhet så kommer även registreringstillståndet att återställas på den enheten. Det finns inget behov av ytterligare åtgärder.

## <a name="restoring-backups-onto-different-devices"></a>Återställa säkerhetskopior på olika enheter

Om säkerhetskopian återställs på en annan enhet så kommer registreringstillståndet inte att återställas automatiskt på den nya enheten. Användare måste följa standardstegen för registrering i företagsportalappen på programversion 2.1.22 eller senare för att [enroll their iOS device into Intune](/intune-user-help/enroll-your-device-in-intune-ios) (registrera sin iOS-enhet i Intune).

> [!NOTE]
> Om slutanvändarna hanteras med principer för villkorlig åtkomst kommer de inte kunna komma åt företagets e-post förrän efter att de omregistrerat sig.

> [!TIP]
> Ett exempelmeddelande till dina användare kan se ut så här: Registrera er på den nya enheten och se till att företagsportalappen är version 2.1.22 eller senare. Öppna företagsportalappen, tryck på menyn i det övre högra hörnet och tryck sedan på Om för att kontrollera vilken version som du kör. Om du har en tidigare version stänger du företagsportalappen och öppnar App Store. Tryck på knappen Uppdateringar i det nedre högra hörnet och sedan på knappen Uppdatera bredvid objektet Företagsportalen i listan. När uppdateringen är färdig startar du företagsportalsappen och [enroll your iOS device into Intune](/intune-user-help/enroll-your-device-in-intune-ios) (registrerar iOS-enheten i Intune).

## <a name="resolving-known-issues-with-restores"></a>Åtgärda kända problem med återställningar

Användare kan uppleva visa problem om de har återställt sin enhet och startat företagsportalappen när de fortfarande har företagsportalappen med version 2.1.21 eller tidigare. Dessa problem kan åtgärdas genom att vidta lämpliga åtgärder för användarens situation.

### <a name="for-users-who-will-only-use-their-new-device"></a>För användare som endast kommer att använda sin nya enhet
Starta företagsportalsappen och avregistrera genom att välja den aktuella enhetspanelen och trycka på knappen __Ta bort__. När du har tagit bort följer du standardstegen för registrering för att [registrera en iOS-enhet i Intune](/intune-user-help/enroll-your-device-in-intune-ios).

### <a name="for-users-who-will-use-both-their-old-and-new-devices"></a>För användare som kommer att använda både sina gamla och nya enheter
Rensa cookies från Safari genom att trycka på __Inställningar__ > __Safari__ > __Rensa historik och webbplatsdata__. När rensningen är klar avinstallerar och installerar du om företagsportalappen och följer sedan standardregistreringsstegen för att [registrera en iOS-enhet i Intune](/intune-user-help/enroll-your-device-in-intune-ios).

