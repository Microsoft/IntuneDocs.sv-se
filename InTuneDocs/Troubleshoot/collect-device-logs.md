---
title: Samla in enhetsloggar| Microsoft Intune
description: "Lär dig hur du samlar in loggar från dina hanterade enheter."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>Enhetsloggar

Som en del av ditt arbete med felsökning kanske du vill samla in loggar från användarenheter. Anvisningar om att samla in dessa loggar finns här. Vanligtvis kan du behöva åtkomst till enheten eller en begäran från användaren om att personen samlar in loggarna och skickar dem till dig.

### <a name="android-log-location"></a>Plats för Android-loggar
Android-loggar finns i *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. Användaren kan även skicka loggfiler via e-post, enligt beskrivningen i [Skicka loggar med Android-diagnostikdata till IT-administratören via e-post](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android).

### <a name="ios-logs"></a>iOS-loggar

Användaren kan skicka registreringsfelen till dig enligt beskrivningen i [Skicka iOS-registreringsfel till IT-administratören](/intune/enduser/send-errors-to-your-it-admin-ios)

### <a name="mac-os-x-devices"></a>Mac OS X-enheter

1. Öppna appen **Konsol**.
2. Välj **system.log** under **FILER** .
3. I menyfältet högst upp väljer du **Arkiv** > **Spara en kopia som…** och spara filen.

### <a name="windows-phone"></a>Windows Phone

I den **Företagsportalen för Windows Phone** måste användaren välja **...** för att komma åt menyn, och sedan välja **Skicka loggar**. Det här alternativet är tillgängligt både före och efter inloggning till portalen.

### <a name="windows"></a>Windows

Loggarna för Windows-företagsportalen finns i *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Oct16_HO3-->


