---
title: "Förbereda appar för hantering av mobilprogram med Microsoft Intune | Microsoft Docs"
description: "Informationen i det här avsnittet hjälper dig att avgöra när du ska använda apphanteringsverktyget och App SDK för att förbereda dina verksamhetsspecifika appar för användning av hanteringsprinciper för mobilappar."
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 02/8/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b15f56f6e771faeb924668aa68140ab89a174b8d
ms.openlocfilehash: c9bba34d2252e6b9dff295724f9c935c558aa179


---

# <a name="prepare-line-of-business-apps-for-mam"></a>Förbereda affärsappar för MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan använda principer för hantering av mobilprogram (MAM) i dina appar med hjälp av Intunes apphanteringsverktyg eller Intune App SDK. Det här avsnittet innehåller information om dessa metoder och när du ska använda dem.

## <a name="intune-app-wrapping-tool"></a>Intunes apphanteringsverktyg
Apphanteringsverktyget används främst för interna affärsappar. Verktyget är ett kommandoradsprogram som skapar en omslutning runt en app, som sedan gör att appen kan hanteras av en Intune MAM-princip.

Du behöver inte källkoden för att använda verktyget, men du behöver autentiseringsuppgifter för signering.  Mer information om autentiseringsuppgifter för signering finns i [Intune-bloggen](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Dokumentation om appomslutningsverktyget finns i [Appomslutningsverktyget för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) respektive [Appomslutningsverktyget för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

Apphanteringsverktyget stöder **inte** appar i Apple App Store eller Google Play Store. Det stöder inte heller vissa funktioner som kräver utvecklarintegration (se följande tabell med funktionsjämförelser).


Mer information om programhanteringsverktyget för MAM på enheter som inte har registrerats i Intune finns i [Skydda branschspecifika appar och data på enheter som inte har registrerats i Microsoft Intune](protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune.md).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Skäl för att använda apphanteringsverktyget:
* Din app har inte några inbyggda dataskyddsfunktioner.
* Din app är enkel.
* Din app distribueras internt.
* Du har inte tillgång till appens källkod
* Du har inte utvecklat appen.
* Din app har minimala användarautentiseringsfunktioner.


### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Apphanteringsverktyg** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja|Ja|
|**Android**| Nej |Ja|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK är främst utformat för kunder som har appar i Apple App Store eller Google Play Store och som vill kunna hantera appar med Intune. Alla appar kan dock dra nytta av integrera SDK, även branschspecifika appar.

Mer information om SDK:n finns i [Översikt](/intune/develop/intune-app-sdk). Om du vill börja använda SDK:n läser du [Komma igång med Microsoft Intune App SDK](/intune/develop/intune-app-sdk-get-started).

### <a name="reasons-to-use-the-sdk"></a>Skäl för att använda SDK
* Din app har inte några inbyggda dataskyddsfunktioner.
* Din app är komplex och innehåller många funktioner.
* Din app har distribuerats via en offentlig appbutik som Google Play- eller Apple App Store.
* Du är en apputvecklare och har de tekniska förutsättningarna att kunna använda SDK:n.
* Din app har andra SDK-integrationer.
* Din app uppdateras ofta.

### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Ja – Använd [Xamarin-komponenten för Intune App SDK](/../develop/intune-app-sdk-xamarin).|Ja – Använd [Cordova-plugin-programmet för Intune App SDK](/../develop/intune-app-sdk-cordova).|
|**Android**| Ja – Använd [Xamarin-komponenten för Intune App SDK](/../develop/intune-app-sdk-xamarin).|Ja – Använd [Cordova-plugin-programmet för Intune App SDK](/../develop/intune-app-sdk-cordova).|

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
|Tillåt fingeravtryck istället för PIN |X|X|
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
|Anpassningsbar stil |X|||
### <a name="see-also"></a>Se även

[Apphanteringsverktyg för Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Apphanteringsverktyg för iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)</br>
[Aktivera hantering av mobilprogram i appar med SDK](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Feb17_HO2-->


