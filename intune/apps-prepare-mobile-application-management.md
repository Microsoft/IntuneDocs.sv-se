---
title: Förbered branschspecifika appar för appskyddsprinciper
titlesuffix: Microsoft Intune
description: Använd programhanteringsverktyget och App SDK för att göra så att dina verksamhetsspecifika appar kan använda appskyddsprinciper i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 29e22121-8268-48b5-a671-f940a6be1d24
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d61ba21ba465037fbf2ef4e1c7423f6649fc810f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="prepare-line-of-business-apps-for-app-protection-policies"></a>Förbered branschspecifika appar för appskyddsprinciper

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Du kan använda appskyddsprinciper i dina appar med hjälp av Intunes apphanteringsverktyg eller Intune App SDK. Det här avsnittet innehåller information om dessa metoder och när du ska använda dem.

## <a name="intune-app-wrapping-tool"></a>Intunes apphanteringsverktyg
Apphanteringsverktyget används främst för interna affärsappar. Verktyget är ett kommandoradsprogram som skapar en omslutning runt en app, som sedan gör att appen kan hanteras av en Intune-appskyddsprincip.

Du behöver inte källkoden för att använda verktyget, men du behöver autentiseringsuppgifter för signering. Mer information om autentiseringsuppgifter för signering finns i [Intune-bloggen](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/). Dokumentation om appomslutningsverktyget finns i [Appomslutningsverktyget för Android](app-wrapper-prepare-android.md) respektive [Appomslutningsverktyget för iOS](app-wrapper-prepare-ios.md).

Apphanteringsverktyget stöder **inte** appar i Apple App Store eller Google Play Store. Det stöder inte heller vissa funktioner som kräver utvecklarintegration (se följande tabell med funktionsjämförelser).


Mer information om programhanteringsverktyget för appskyddsprinciper på enheter som inte har registrerats i Intune finns i [Skydda branschspecifika appar och data på enheter som inte har registrerats i Microsoft Intune](/intune-classic/deploy-use/protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune).

### <a name="reasons-to-use-the-app-wrapping-tool"></a>Skäl för att använda programhanteringsverktyget
* Din app har inte några inbyggda dataskyddsfunktioner
* Din app är enkel
* Din app distribueras internt
* Du har inte tillgång till appens källkod
* Du har inte utvecklat appen
* Din app har minimala användarautentiseringsfunktioner


### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Apphanteringsverktyg** | **Xamarin** |**Cordova** |
|------|----|----|
|**iOS** |Ja|Ja|
|**Android**| I förhandsversion |Ja|

## <a name="intune-app-sdk"></a>Intune App SDK
App SDK är främst utformat för kunder som har appar i Apple App Store eller Google Play Store och som vill kunna hantera appar med Intune. Alla appar kan dock dra nytta av integrera SDK, även branschspecifika appar.

Mer information om SDK:n finns i [Översikt](app-sdk.md). Om du vill börja använda SDK:n läser du [Komma igång med Microsoft Intune App SDK](app-sdk-get-started.md).

### <a name="reasons-to-use-the-sdk"></a>Skäl för att använda SDK
* Din app har inte några inbyggda dataskyddsfunktioner
* Din app är komplex och innehåller många funktioner
* Din app har distribuerats via en offentlig appbutik som Google Play eller Apple App Store
* Du är en apputvecklare och har de tekniska förutsättningarna att kunna använda SDK:n
* Din app har andra SDK-integrationer
* Din app uppdateras ofta

### <a name="supported-app-development-platforms"></a>Utvecklingsplattformar för program som stöds

|**Intune App SDK** |**Xamarin** |**Cordova**
|------|----|----|
|**iOS**|Ja – Använd [Xamarin-bindningar för Intune App SDK](app-sdk-xamarin.md).|Ja – Använd [Cordova-plugin-programmet för Intune App SDK](app-sdk-cordova.md).|
|**Android**| Ja – Använd [Xamarin-bindningar för Intune App SDK](app-sdk-xamarin.md).|Ja – Använd [Cordova-plugin-programmet för Intune App SDK](app-sdk-cordova.md).|

## <a name="feature-comparison"></a>Jämförelse av funktioner
Den här tabellen visar de inställningar som du kan använda för App SDK och apphanteringsverktyget.

> [!NOTE]
> Apphanteringsverktyget kan användas med den fristående versionen av Intune eller Intune med Configuration Manager.

|                                                         Funktion                                                          | App SDK | Apphanteringsverktyg |
|--------------------------------------------------------------------------------------------------------------------------|---------|-------------------|
|                              Begränsa webbinnehåll till att bara visas i en företagshanterad webbläsare                              |    X    |         X         |
|                                        Förhindra Android-, iTunes- och iCloud-säkerhetskopieringar                                        |    X    |         X         |
|                                         Tillåt att appen överför information till andra appar                                         |    X    |         X         |
|                                        Tillåt att appen hämtar data från andra appar                                         |    X    |         X         |
|                                      Begränsa klipp ut, kopiera och klistra in med andra appar                                       |    X    |         X         |
|                                              Kräv enkel PIN-kod för åtkomst                                               |    X    |         X         |
|                                         Ersätt appens inbyggda PIN-kod med PIN-koden för Intune                                         |    X    |                   |
|                                     Ange antal försök innan PIN-koden återställs                                      |    X    |         X         |
|                                             Tillåt fingeravtryck istället för PIN                                             |    X    |         X         |
|                                         Kräv företagets autentiseringsuppgifter för åtkomst                                         |    X    |         X         |
|                             Hindra hanterade appar från att köras på jailbrokade eller rotade enheter                              |    X    |         X         |
|                                                     Kryptera appdata                                                     |    X    |         X         |
|                           Kontrollera åtkomstbehörigheterna på nytt efter angivet antal minuter                            |    X    |         X         |
|                                             Ange offlinerespitperiod                                             |    X    |         X         |
|                                           Blockera skärmdump (endast Android)                                            |    X    |         X         |
|                                        Stöd för MAM utan enhetsregistrering                                         |    X    |         X         |
|                                                        Fullständig rensning av enheten                                                         |    X    |         X         |
| Selektiv rensning <br></br><strong>Obs!</strong> När hanteringsprofilen tas bort i iOS tas även appen bort. |    X    |                   |
|                                                    Förhindra ”Spara som”                                                     |    X    |                   |
|                                            Konfiguration av målprogram                                            |    X    |                   |
|                                                Stöd för flera identiteter                                                |    X    |                   |
|                                                    Anpassningsbar stil                                                    |    X    |                   |

## <a name="next-steps"></a>Nästa steg

Mer information om appskyddsprinciper i Intune finns i följande avsnitt:

  -  [Apphanteringsverktyg för Android](app-wrapper-prepare-android.md)</br>
  - [Apphanteringsverktyg för iOS](app-wrapper-prepare-ios.md)</br>
  - [Aktivera hantering av mobilprogram i appar med SDK](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
