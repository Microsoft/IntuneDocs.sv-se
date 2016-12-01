---
title: "Förbereda appar för hantering av mobilprogram | Microsoft Intune"
description: "Informationen i det här avsnittet hjälper dig att avgöra när du ska använda apphanteringsverktyget och App SDK för att förbereda dina verksamhetsspecifika appar för användning av hanteringsprinciper för mobilappar."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: 376c9bce811ffd986242678929469f3e28bfad4c
ms.openlocfilehash: e145baf0f7366f331e8d1df994a8fa40ec693227


---

# <a name="decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune"></a>Förbereda appar för hantering av mobilprogram med Microsoft Intune
Du kan använda principer för hantering av mobilprogram (MAM) i dina appar med hjälp av Intunes apphanteringsverktyg eller Intune App SDK. Det här avsnittet innehåller information om dessa metoder och när du ska använda dem.

## <a name="intune-app-wrapping-tool"></a>Intunes apphanteringsverktyg
Apphanteringsverktyget används främst för interna affärsappar. Verktyget är ett kommandoradsprogram som skapar en omslutning runt en app, som sedan gör att appen kan hanteras av en Intune MAM-princip.

Du behöver inte källkoden för att använda verktyget, men du behöver autentiseringsuppgifter för signering.  Mer information om autentiseringsuppgifter för signering finns i [Intune-bloggen](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Dokumentation om appomslutningsverktyget finns i [Appomslutningsverktyget för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) respektive [Appomslutningsverktyget för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Apphanteringsverktyget stöder **inte** appar i Apple App Store eller Google Play Store. Det stöder inte heller vissa funktioner som kräver utvecklarintegration (se följande tabell med funktionsjämförelser).

Du bör använda apphanteringsverktyget i stället för SDK, om appen har redan skrivits eller om källkoden är inte tillgänglig.

Mer information om programhanteringsverktyget för MAM på enheter som inte har registrerats i Intune finns i [Skydda branschspecifika appar och data på enheter som inte har registrerats i Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Apphanteringsverktyg** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja|Ja|
|**Android**| Nej |Ja|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK är främst utformat för kunder som har appar i Apple App Store eller Google Play Store och som vill kunna hantera appar med Intune. Alla appar kan dock dra nytta av integrera SDK, även branschspecifika appar.

Mer information om SDK:n finns i [Översikt](/intune/develop/intune-app-sdk). Om du vill börja använda SDK:n läser du [Komma igång med Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started).

### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Ja – Använd Xamarin-komponenten för Intune App SDK.|Ja – Använd Cordova-plugin-programmet för Intune App SDK.|
|**Android**| Ja – Använd Xamarin-komponenten för Intune App SDK.|Ja – Använd Cordova-plugin-programmet för Intune App SDK.|

## <a name="feature-comparison"></a>Jämförelse av funktioner
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
|Stöd för MAM utan enhetsregistrering|X|X|
### <a name="see-also"></a>Se även

[Apphanteringsverktyg för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Apphanteringsverktyg för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Nov16_HO3-->


