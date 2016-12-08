---
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ef3b7e4eec5a520c93fb3f70c8e5b6ee7d2c3aa
ms.openlocfilehash: e0b0c7eb3ddc07f05fc0c2e4caa6726ed052c9d8


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Nyheter i Microsoft Intune – November 2016
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Nya Microsoft Intune-företagsportalen för Windows 10-enheter__ Microsoft har lanserat en ny [Microsoft Intune-företagsportalsapp för Windows 10-enheter](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store. Mer information finns på [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __En uppdatering av Intune och Android for Work__

> Även om du kan distribuera Android for Work-appar med åtgärden __Krävs__ kan du bara distribuera appar som __tillgängliga__ om Intune-grupper har migrerats till den nya Azure AD-gruppmiljön.

### <a name="intune-app-sdk-for-cordova-plugin-now-supports-mam-without-enrollment"></a>Nu stöder Intune App SDK för Cordova-plugin-programmet MAM utan registrering
Nu kan apputvecklare använda Intune App SDK för Cordova-plugin-programmet för att aktivera MAM-funktioner utan enhetsregistrering i deras Cordova-baserade appar för Android och iOS. Intune App SDK för Cordova-plugin-programmet finns [här](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

### <a name="intune-app-sdk-xamarin-component-now-supports-mam-without-enrollment"></a>Nu stöder Intune App SDK Xamarin-komponenten MAM utan registrering
Nu kan apputvecklare använda Intune App SDK Xamarin-komponenten för att aktivera MAM-funktioner utan enhetsregistrering i deras Xamarin-baserade appar för Android och iOS. Intune App SDK Xamarin-komponenten finns [här](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

## <a name="notices"></a>Meddelanden

### <a name="symantec-signing-certificate-no-longer-requires-signed-windows-phone-8-company-portal-for-upload"></a>Symantec-signeringscertifikat kräver inte längre en signerad Windows Phone 8-företagsportal för överföring
Överföring av Symantec-signeringscertifikatet kräver inte längre en signerad Windows Phone 8-företagsportalapp. Certifikatet kan överföras fristående.

## <a name="deprecations"></a>Föråldringar

### <a name="support-for-the-windows-phone-8-company-portal"></a>Stöd för Windows Phone 8-företagsportalen
Stöd för Windows Phone 8-Företagsportalen kommer upphöra. Stöd för Windows Phone 8- och WinRT-plattformarna upphörde oktober 2016. Stöd för Windows Phone 8-företagsportalen upphörde också det oktober 2016.


### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Tidigare versioner av Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO1-->


