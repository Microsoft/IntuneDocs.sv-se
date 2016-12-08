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
ms.sourcegitcommit: 0c05b4e16f7b0a87215a0cd20f7d559cd8497296
ms.openlocfilehash: 0f175b1eb2d80a68c8b7864d21f5a9e585de458b


---

# <a name="device-logs"></a>Enhetsloggar

Som en del av ditt arbete med felsökning vill du kanske samla in loggar från användarenheter. Anvisningar om att samla in dessa loggar finns här. I normala fall behöver du åtkomst till enheten för att få tillgång till dessa loggar, eller så kan du skicka en begäran till användaren om att samla in loggarna och skicka dem till dig.

### <a name="android-logs"></a>Android-loggar
Android-loggar finns i *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Ibland visas filerna inte, särskilt på nyare Android-enheter. Om detta händer så låt dina användare öppna företagsportalsappen för Android. De bör då välja **Inställningar**>**Kopiera loggar** och starta om enheten.

Mer information om hur dina användare kan skicka dataloggar till dig finns i följande artiklar:

- [Hjälp din IT-administratör med att åtgärda enhetsproblem genom att använda utförlig loggning](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android): Beskriver hur användarna kan aktivera utförlig loggning, varvid alla deras dataloggar skickas till dig automatiskt. Utförlig loggning är aktiverat som standard.

- [Send Android diagnostic data logs to your IT admin using email](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) (Skicka loggar med diagnostikdata för Android till din IT-administratör med e-post)

- [Skicka loggar med diagnostikdata till din IT-administratör via USB-kabel](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>iOS-loggar

Användare kan skicka registreringsfelen till dig enligt beskrivningen i [Skicka iOS-registreringsfel till IT-administratören](/intune/enduser/send-errors-to-your-it-admin-ios).

### <a name="mac-os-x-logs"></a>Mac OS X-loggar

1. Öppna appen **Konsol**.
2. Välj **system.log** under **FILES**.
3. Välj **Arkiv** > **Spara en kopia som…** i menyfältet högst upp. Spara sedan filen.

### <a name="windows-phone"></a>Windows Phone

I Windows Phone-företagsportalsappen öppnar användarna menyn genom att klicka på de tre punkterna (**…**) och väljer sedan **Skicka loggar**. Det här alternativet är tillgängligt både före och efter inloggning till företagsportalappen.

### <a name="windows"></a>Windows

Loggarna för Windows-företagsportalen finns i *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Nov16_HO5-->


