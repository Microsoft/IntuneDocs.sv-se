---
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Nyheter i Microsoft Intune -- Oktober 2016
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## Nyheter

### Villkorlig åtkomst för hantering av mobila program
Du kommer att kunna begränsa åtkomsten till Exchange Online så att åtkomst endast kan ges genom appar som stöder Intunes hanteringsprinciper för mobilprogram, som till exempel Outlook. [Den här nya funktionen](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) passar perfekt ihop med Intune MAM-principer (mobile app management) eftersom du kan blockera åtkomst till inbyggda e-postklienter eller andra appar som inte har konfigurerats med Intune MAM-principerna. Detta garanterar att dina användare har åtkomst till din organisations data med appar som kan skyddas med Intune MAM. Du kan komma igång med hantering av mobilappar i Intune via Azure Portal. Leta efter det nya avsnittet om villkorlig åtkomst i bladet ”Inställningar”.

### Villkorlig åtkomst för Windows-datorer
Nu kan du skapa principer för villkorlig åtkomst via Intune-administratörskonsolen om du vill blockera Windows-datorer från att få åtkomst till [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) och [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune). Du kan även skapa principer för villkorlig åtkomst för att blockera åtkomst till stationära och universella Office-program.

### Stöd för Android for Work
Intune är nu en del av Android for Work-programmet. Vi kommer att börja integrera stöd för Android for Work-funktioner i Intune med början den här månaden.
[Läs Microsofts tillkännagivande om Intune-stöd för Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Följande avsnitt för Intune är nya eller uppdaterade med information om Android for Work:

För IT-proffs:
- [Konfigurera Android for Work](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Begränsa åtkomsten för e-post till Exchange Online och nya Exchange Online Dedicated med Microsoft Intune](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Begränsa e-poståtkomsten till Exchange On-premises och äldre Exchange Online Dedicated med Microsoft Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Inställningar för policy för efterlevnad för Android for Work](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [Så här distribuerar du Android for Work-appar](/intune/deploy-use/android-for-work-apps)
- [Konfigurera Android for Work-appar med konfigurationsprinciper för mobilappar](/intune/deploy-use/afw-app-configuration-policy)
- [Principinställningar för Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

För slutanvändare:
- [Vad händer när du skapar en arbetsprofil](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Skapa en arbetsprofil och registrera din enhet i Intune](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Lookout-integration för att skydda iOS-enheter
Från och med oktober integrerar Microsoft med Lookouts lösning för skydd mot mobilhot för att skydda mobila Android-enheter genom att exempelvis identifiera skadlig kod och riskfyllda appar på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla iOS-enheter uppmanas att registrera sig och måste installera Lookout for Work-appen på sina enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Lär dig hur du [konfigurerar och distribuerar Lookout for work-appar](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Intunes programhanteringsverktyg för Android
Du kan konfigurera dina appar att använda Intune MAM-principer för hantering av mobilprogram med hjälp av Intunes programhanteringsverktyg. Nu finns stöd för Intune MAM-principer utan krav på enhetsregistrering.

### Hantera utskrifter från appar som hanteras med hjälp av MAM-principer
Nu kan du förhindra utskrift av företagsdata från appar som har MAM-principer. Den här inställningen är tillgänglig på [Azure-portalen](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) och stöds på både [iOS](/Intune/deploy-use/ios-mam-policy-settings)- och [Android](/Intune/deploy-use/android-mam-policy-settings)-enheter.
<!--TFS 1014328-->

## Meddelanden

### Android Samsung KNOX-kompatibilitet med Intune
Vissa modeller av Samsung Galaxy Ace-telefonen kan inte hanteras av Intune som Samsung KNOX-enheter. När du registrerar dessa enheter med Intune hanteras de i stället som Android-standardenheter.

Följande modellnummer påverkas:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Du och dina slutanvändare behöver inte vidta någon ytterligare åtgärd. Mer information finns på webbplatsen för [Samsung KNOX](https://www.samsungknox.com).

### Företagsportalappen för Windows 8 är föråldrad; stödet för Windows Phone 8- och Windows RT-plattformar upphör snart
Från och med oktober 2016 upphör Microsoft Intunes stöd för Windows 8-företagsportalen. Microsoft Intunes stöd för Windows Phone 8- och Windows RT-plattformarna upphör också snart. Det betyder att du inte kommer att kunna registrera eller uppdatera Windows Phone 8- eller Windows RT-enheter.

Men du kan fortsätta att hantera Windows Phone 8-, Windows RT- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.

Från och med november 2016 upphör stödet för Windows Phone 8-företagsportalappen.
<!--TFS 1255391-->

## Kommande nyheter

### Nya Microsoft Intune-företagsportalen för Windows 10-enheter
Microsoft lanserar en ny Microsoft Intune-företagsportal för Windows 10-enheter. Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store. Mer information finns på [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

### Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Tidigare versioner av Intune](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


