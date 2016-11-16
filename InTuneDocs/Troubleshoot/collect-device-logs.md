---
title: Samla in enhetsloggar| Microsoft Intune
description: "Lär dig hur du samlar in loggar från dina hanterade enheter."
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013


---

# <a name="device-logs"></a>Enhetsloggar

Som en del av ditt arbete med felsökning kanske du vill samla in loggar från användarenheter. Anvisningar om att samla in dessa loggar finns här. Vanligtvis kan du behöva åtkomst till enheten eller en begäran från användaren om att personen samlar in loggarna och skickar dem till dig.

### <a name="android-logs"></a>Android-loggar
Android-loggar finns i *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. 

Ibland visas filerna inte, särskilt på nyare Android-enheter. Om detta händer, be dina slutanvändare att öppna företagsportalappen för Android och gå till **Inställningar**, välja **Kopiera loggar**, och sedan starta om enheten. 

Mer information om hur dina användare kan skicka dataloggar till dig finns i följande artiklar:

- [Use Verbose Logging to help your IT admin fix device issues](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) (Använd utförlig loggning för att hjälpa din IT-administratör att åtgärda problem med enheter) – Beskriver hur användare aktiverar utförlig loggning som gör att alla dataloggar skickas till dig automatiskt. Utförlig loggning är aktiverat som standard.

- [Send Android diagnostic data logs to your IT admin using email](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) (Skicka loggar med diagnostikdata för Android till din IT-administratör med e-post) 

- [Skicka loggar med diagnostikdata till din IT-administratör via USB-kabel](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS-loggar

Användare kan skicka registreringsfelen till dig enligt beskrivningen i [Skicka iOS-registreringsfel till IT-administratören](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Mac OS X-loggar

1. Öppna appen **Konsol**.
2. Välj **system.log** under **FILER** .
3. I menyfältet högst upp väljer du **Arkiv** > **Spara en kopia som…** och spara filen.

### <a name="windows-phone"></a>Windows Phone

I Windows Phone-företagsportalappen väljer användarna **...** för att komma åt menyn, och sedan välja **Skicka loggar**. Det här alternativet är tillgängligt både före och efter inloggning till företagsportalappen.

### <a name="windows"></a>Windows

Loggarna för Windows-företagsportalen finns i *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Nov16_HO2-->


