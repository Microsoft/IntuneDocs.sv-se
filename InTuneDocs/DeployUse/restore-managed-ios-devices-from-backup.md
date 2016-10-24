---
title: "Återställa Intune-hanterade iOS-enheter från en säkerhetskopia | Microsoft Intune"
description: "Ge vägledning till slutanvändare om hur de kan registrera sina enheter igen efter att enheterna blivit återställda från säkerhetskopior."
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a19e5612-8805-4bd7-a86a-b734bde293ae
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 612b0954a81de1ee8d4a1e96c7440239437dec14
ms.openlocfilehash: 5fc4423f8fd0c5829be5fe6c96949e126991e430


---

# Återställa Intune-hanterade iOS-enheter från en säkerhetskopia

I vissa fall kan du eller användarna komma att behöva återställa en iOS-enhet från en säkerhetskopia, till exempel när en användare får en ny enhet. Det här avsnittet beskriver ytterligare steg som du kan behöva utföra för att konfigurera Intune-hantering efter att enheten återställts.

## Återställa säkerhetskopior på samma enhet

Om säkerhetskopian återställs på samma enhet så kommer även registreringstillståndet att återställas på den enheten. Det finns inget behov av ytterligare åtgärder.

## Återställa säkerhetskopior på olika enheter

Om säkerhetskopian återställs på en annan enhet så kommer registreringstillståndet inte att återställas automatiskt på den nya enheten. Användare måste följa standardstegen för registrering i företagsportalappen på programversion 2.1.22 eller senare för att [enroll their iOS device into Intune](/Intune/EndUser/enroll-your-device-in-intune-ios) (registrera sin iOS-enhet i Intune).

> [!NOTE]
> Om slutanvändarna hanteras med principer för villkorlig åtkomst kommer de inte kunna komma åt företagets e-post förrän efter att de omregistrerat sig.

> [!TIP]
> Ett exempelmeddelande till dina användare kan se ut så här: Registrera er på den nya enheten och se till att företagsportalappen är version 2.1.22 eller senare. Öppna företagsportalappen, tryck på menyn i det övre högra hörnet och tryck sedan på Om för att kontrollera vilken version som du kör. Om du har en tidigare version stänger du företagsportalappen och öppnar App Store. Tryck på knappen Uppdateringar i det nedre högra hörnet och sedan på knappen Uppdatera bredvid objektet Företagsportalen i listan. När uppdateringen är färdig startar du företagsportalsappen och [enroll your iOS device into Intune](/Intune/EndUser/enroll-your-device-in-intune-ios) (registrerar iOS-enheten i Intune).



<!--HONumber=Oct16_HO2-->


