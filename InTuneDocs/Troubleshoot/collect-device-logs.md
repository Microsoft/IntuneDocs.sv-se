---
title: Samla in enhetsloggar| Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 06/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac5c66f57194a84580aa495a58e5281683aa1cca
ms.openlocfilehash: 4fc08fcea6cea897b9ddc3d0c00f2d83069f639d


---

# Enhetsloggar

Som en del av ditt arbete med felsökning kanske du vill samla in loggar från användarenheter. Anvisningar om att samla in dessa loggar finns här. Vanligtvis kan du behöva åtkomst till enheten eller en begäran från användaren om att personen samlar in loggarna och skickar dem till dig. 

### Plats för Android-loggar
Android-loggar finns i *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. Användaren kan även skicka loggfiler via e-post, enligt beskrivningen i [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### iOS-loggar

Användaren kan skicka registreringsfelen till dig enligt beskrivningen i [Skicka iOS-registreringsfel till IT-administratören](/intune/enduser/send-errors-to-your-it-admin-ios)

### Mac OS X-enheter

1. Öppna appen **Konsol**.
2. Välj **system.log** under **FILER** .
3. I menyfältet högst upp väljer du **Arkiv** > **Spara en kopia som…** och spara filen.

### Windows Phone

I den **Företagsportalen för Windows Phone** måste användaren välja **...** för att komma åt menyn, och sedan välja **Skicka loggar**. Det här alternativet är tillgängligt både före och efter inloggning till portalen.

### Windows

Loggarna för Windows-företagsportalen finns i *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Jun16_HO4-->


