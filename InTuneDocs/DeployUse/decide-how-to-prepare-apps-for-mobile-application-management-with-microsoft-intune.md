---
title: "Förbereda appar för hantering av mobilprogram | Microsoft Intune"
description: "Informationen i det här avsnittet hjälper dig att avgöra när du ska använda apphanteringsverktyget och App SDK för att förbereda dina verksamhetsspecifika appar för användning av hanteringsprinciper för mobilappar."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 70f9fb5580b114fe1ba14a1bd05de58467d5cd00
ms.openlocfilehash: b5dd5bec0910a8ce3a940b5ed288907aba0f7ee4


---

# Förbereda appar för hantering av mobilprogram med Microsoft Intune
Du kan använda principer för hantering av mobilprogram (MAM) i dina appar med hjälp av Intunes apphanteringsverktyg eller Intune App SDK. Det här avsnittet innehåller information om dessa metoder och när du ska använda dem.

## Intunes apphanteringsverktyg
Apphanteringsverktyget används främst för interna affärsappar. Verktyget är ett kommandoradsprogram som skapar en wrapper runt appen, som gör att appen kan hanteras av en princip för hanteringar av mobilprogram. Du behöver inte källkoden för att använda verktyget, men du behöver autentiseringsuppgifter för signering.  Mer information om autentiseringsuppgifter för signering finns i [Intune-bloggen](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Dokumentation om appomslutningsverktyget finns i [Appomslutningsverktyget för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) respektive [Appomslutningsverktyget för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Apphanteringsverktyget stöder inte appar i App Store eller Play Store eller funktioner som kräver integrering av utvecklingstid (se jämförelsetabellen för funktioner nedan).

Du bör använda apphanteringsverktyget i stället för SDK, om appen har redan skrivits eller om källkoden är inte tillgänglig.

**Programhanteringsverktyget för MAM på enheter som inte har registrerats i Intune stöds för närvarande i förhandsversionen. För mer information, se artikeln [Skydda verksamhetsspecifika appar på enheter som inte har registrerats i Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md)**.

### Plattformar som stöds

|**Apphanteringsverktyg** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja|Ja|
|**Android**| Nej |Ja|
## Intune App SDK
App SDK är utformat främst för kunder som har appar i App Store eller Play Store och vill kunna hantera appar med Intune. Alla appar kan dock dra nytta av integrera SDK, även interna affärsappar.

Mer information om SDK:n finns i [Översikt](/intune/develop/intune-app-sdk). Om du vill börja använda SDK:n läser du [Komma igång med Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started).

### Plattformar som stöds
|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Ja – Använd Xamarin-komponenten för Intune App SDK|Ja – Använd Cordova-insticksprogrammet för Intune App SDK|
|**Android**| Ja – Använd Xamarin-komponenten för Intune App SDK|Ja – Använd Cordova-insticksprogrammet för Intune App SDK|

## Jämförelse av funktioner
Den här tabellen visar de inställningar som du kan använda för App SDK och apphanteringsverktyget.

> [!NOTE]
> Apphanteringsverktyget kan användas med den fristående versionen av Intune eller Intune med Configuration Manager.

|Funktion|App SDK|Apphanteringsverktyg|
|-----------|---------------------|-----------|
|Begränsa webbinnehåll till att bara visas i en företagshanterad webbläsare|X|X|
|Förhindra Android-, iTunes- och iCloud-säkerhetskopieringar|X|X|
|Tillåt att appen överför information till andra appar|X|X|
|Tillåt att appen hämtar data från andra appar|X|X|
|Begränsa klipp ut, kopiera och klistra in med andra appar|X|X|
|Kräv enkel PIN-kod för åtkomst|X|X|
|Ersätt appens inbyggda PIN-kod med PIN-koden för Intune|X||
|Ange antal försök innan PIN-koden återställs|X|X|
|Kräv fingeravtryck i stället för PIN-kod (endast iOS)<br></br>**Obs!** Endast tillgängligt i MAM-miljöer.|X||
|Kräv företagets autentiseringsuppgifter för åtkomst|X|X|
|Hindra hanterade appar från att köras på jailbrokade eller rotade enheter|X|X|
|Kryptera appdata|X|X|
|Kontrollera åtkomstbehörigheterna på nytt efter angivet antal minuter|X|X|
|Ange offlinerespitperiod|X|X|
|Blockera skärmdump (endast Android)|X|X|
|Fullständig rensning av enheten|X|X|
|Selektiv rensning <br></br>**Obs!** När hanteringsprofilen tas bort i iOS tas även appen bort.|X||
|Förhindra ”Spara som” |X||
|Stöd för flera identiteter|X||
### Se även

[Apphanteringsverktyg för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Apphanteringsverktyg för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Sep16_HO2-->


