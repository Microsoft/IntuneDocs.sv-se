---
title: "Den tidiga utgåvan | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5c4b0f15456a9f24c95954d669a17c63f96a459
ms.openlocfilehash: 273016d4fe114bbe60e9cebc06e89584c8f91f0b


---

# Kommande nyheter i Microsoft Intune – oktober
Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka då och då för nytillkommet innehåll.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

### Hantera utskrifter från appar som hanteras med hjälp av MAM-principer
Nu kan du förhindra utskrift av företagsdata från appar som har MAM-principer. Den här inställningen är tillgänglig på [Azure-portalen](..deployuse/create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) och stöds på både [iOS](..deployuse/ios-mam-policy-settings)- och [Android](..deployuse/android-mam-policy-settings)-enheter.
<!--TFS 1014328-->

### Nya Microsoft Intune-företagsportalen för Windows 10-enheter
Microsoft lanserar en ny Microsoft Intune-företagsportal för Windows 10-enheter. Den här appen, som använder det nya Windows 10 Universal-formatet, ger en uppdaterad användarupplevelse i appen och identiska miljöer på alla Windows 10-enheter, både på datorer och mobila enheter, med samma funktioner som användarna redan använder.

Med den nya appen kan användarna dessutom dra nytta av ytterligare plattformsfunktioner som enkel inloggning (SSO) och certifikatbaserad autentisering på Windows 10-enheter. Appen kommer att vara tillgänglig som en uppgradering till de befintliga installationerna av Windows 8.1-företagsportalen och Windows Phone 8.1-företagsportalen från Windows Store.
<!--TFS 1016502-->

### Stöd för Android for Work

Intune är nu en del av [Android for Work-programmet](https://enterprise.google.com/android/partners/). Vi kommer att börja integrera stöd för Android for Work-funktioner i Intune med början den här månaden.

[Läs Microsofts tillkännagivande om Intune-stöd för Android for Work](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

<!---This month, some newly provisioned Intune tenants will start seeing the Android for Work features. We will announce later when existing tenants will begin to see this feature.--->
<!--TFS 1043303-->

### Android Samsung KNOX-kompatibilitet med Intune

Vissa modeller av Samsung Galaxy Ace-telefonen kan inte hanteras av Intune som Samsung KNOX-enheter. När du registrerar dessa enheter med Intune hanteras de i stället som Android-standardenheter.
Följande modellnummer påverkas:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Du och dina slutanvändare behöver inte vidta någon ytterligare åtgärd.
Mer information finns på webbplatsen för [Samsung KNOX](https://www.samsungknox.com).

<!--TFS 1173566 iX blurb provided by Barry; requires PM signoff

### Multi-factor authentication for Android and iOS enrollment

In addition to Windows 8.1 and later, administrators can now enable multi-factor authentication for Android and iOS devices in the Microsoft Intune Enrollment application. -->    

### Företagsportalappen för Windows 8 är föråldrad; stödet för Windows Phone 8- och Windows RT-plattformar upphör snart
Från och med oktober 2016 upphör Microsoft Intunes stöd för Windows 8-företagsportalen. Microsoft Intunes stöd för Windows Phone 8- och Windows RT-plattformarna upphör också snart. Det betyder att du inte kommer att kunna registrera eller uppdatera Windows Phone 8- eller Windows RT-enheter.

Men du kan fortsätta att hantera Windows Phone 8-, Windows RT- och Windows 8-enheter som redan har registrerats. Uppdatera enheter med Windows Phone 8 och Windows 8 till Windows Phone 8.1 respektive Windows 8.1 och använd motsvarande företagsportalappar för Windows 8.1 och Windows Phone 8.1. På så sätt kan du fortsätta att distribuera appar till dessa enheter utan avbrott.

Från och med november 2016 upphör stödet för Windows Phone 8-företagsportalappen.
<!--TFS 1255391-->

### Villkorlig åtkomst för hantering av mobila program
Nu kan du skapa en princip för villkorlig åtkomst för att blockera ohanterade mobila program så att de inte kan komma åt [Exchange Online](..deployuse/restrict-access-to-exchange-online-with-microsoft-intune.md) och [SharePoint Online](..deployuse/restrict-access-to-sharepoint-online-with-microsoft-intune.md). Du kan blockera de inbyggda e-postklienterna och appar som inte är MAM-aktiverade med Intune App SDK.  Du kan göra det genom att skapa en princip för villkorlig åtkomst och ange vilka program som ska ha åtkomst till Exchange Online och SharePoint Online via Azure-portalen.
<!--TFS 1317673-->

<!--TFS 1318014; awaiting approval in notes as to whether to proceed

### "Default" policy is deprecated

To minimize unintentionally assigned profiles, Intune is removing support for the "default" Corporate Device Enrollment profile for Apple Device Enrollment Program (DEP) device serial numbers in the new Azure console. Serial numbers synchronized from an Apple DEP account will initially have no Corporate Device Enrollment profile assigned.  A profile must be assigned manually after synchronization. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

<!--TFS 1318023; awaiting approval in notes as to whether to proceed

### Deprecation of row-by-row iOS Details review for iOS device CSV uploads

In order to streamline uploading IMEI numbers for Corporate devices and Apple serial numbers for Configurator enrollment, Intune is removing the row by row review of hardware identifiers already found in the system. This review allows the IT Pro to accept associated Details from the CSV to overwrite the existing details for a hardware identifier already in the system. The review will be replaced by a single option to automatically overwrite Details for all hardware identifiers or ignore new details for existing identifiers. This change will apply to the new console only. Until the existing Admin console is retired, no change will take place.
-->

### Lookout-integration för att skydda iOS-enheter
Från och med oktober integrerar Microsoft med Lookouts lösning för skydd mot mobilhot för att skydda mobila Android-enheter genom att exempelvis identifiera skadlig kod och riskfyllda appar på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla iOS-enheter uppmanas att registrera sig och måste installera Lookout for Work-appen på sina enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst.
<!--TFS 1319493-->

### Intune App SDK och apphanteringsverktyget för Android
Du kan konfigurera dina appar att använda Intune MAM-principer för hantering av mobilprogram, antingen med hjälp av Intunes apphanteringsverktyg eller med Intune App SDK. Exempel på nya uppdateringar för apphanteringsverktyget och SDK är:

* Stöd för Android N
* Stöd för Intune MAM-principer utan enhetsregistrering
* Stöd för Xamarin-baserade Android-appar

Du kan testa stödet för MAM utan enhetsregistrering och Xamarin i den offentliga förhandsversionen av apphanteringsverktyget för Android här: [https://github.com/msintuneappsdk/intune-app-wrapper-android-preview](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview)
<!--TFS 1319511; please create new TFS entry for WN text associated with this TFS item-->

<!--TFS 1319613; no iX review on PM text blurb

### Private preview customers using MAM Conditional Access will have their policies reset

Due to changes in the policy structure for Conditional Access for Mobile App Management, any existing policies that were set by customers through the private preview will be removed. Customers will need to set new policies once the change is made. The timing will coincide with the October service update.
-->

### Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Oct16_HO1-->


