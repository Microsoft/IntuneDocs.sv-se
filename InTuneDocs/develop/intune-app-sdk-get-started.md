---
title: "Komma igång med Microsoft Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed1008c786285821c608a8404805c6615c60507f
ms.openlocfilehash: c80868fdee79df62aae0aa64e378be5dcc9664ae


---

# Komma igång med Microsoft Intune App SDK

Den här Kom igång-guiden hjälper dig att snabbt aktivera din mobilapp för hantering av mobilprogram med Microsoft Intune. Det kan vara bra att först förstå fördelarna med Intune App SDK som räknas upp i [översikten över Intune App SDK](intune-app-sdk.md).

Den här guiden går igenom de viktigaste stegen när du ska aktivera hantering av mobilappar i en app med Microsoft Intune. Intune App SDK stöder liknande scenarier mellan plattformar och är avsett att ge IT-administratörer en enhetlig miljö på olika plattformar. På grund av plattformsbegränsningar förekommer det dock mindre skillnader vad gäller stödet av vissa funktioner.

# Komma igång

## Registrera din Store-app med Microsoft

**Om din app är en intern företagsapp som inte ska publiceras i en offentlig appbutik**:

Du **behöver inte** att registrera din app. För interna affärsappar distribuerar IT-administratören appen internt. Intune identifierar att appen har skapats med SDK och tillåter IT-administratören att tillämpa MAM-principinställningarna på den. Du kan hoppa till avsnittet [Aktivera din iOS- eller Android-mobilapp för MAM med SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Om din app kommer att publiceras på en offentlig appbutik som Apple App Store eller Google Play**: 

**Måste** du först registrera din app med Microsoft Intune och samtycka med villkoren för registrering. Efter registrering kan IT-administratörer använda Intune MAM-principinställningar för RMS-appen, som visas som en Intune-appartner. Intune administratörer kommer inte att ha möjlighet att tillämpa MAM-principen på din apps djuplänk förrän registreringen har slutförts och bekräftats av Microsoft Intune-teamet. Microsoft kommer även att lägga till appen till [Microsoft Intune-partnerplatsen](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps) där appens ikon kommer att visas så att kunder vet att den stöder Microsoft Intunes MAM-princip.

Du börjar registreringen genom att fylla i **[formuläret för Microsoft Intune-appartner](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u)**. 

Microsoft använder den eller de e-postadresser som du uppger i formuläret för att kontakta dig och fortsätta registreringsprocessen. Vi använder även samma e-postadress för att kontakta dig om vi har frågor.

> [!NOTE]
> All information som samlas in i formuläret ovan och via e-postkommunikation med Intune-teamet följer [Microsofts sekretesspolicy](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**Hur ser registreringsprocessen ut?**: 

1. När du har skickat frågeformuläret kontaktar Microsoft dig på den e-postadress som du uppgav vid registreringen, antingen för att bekräfta att registreringen mottagits eller för att be om ytterligare information som krävs för att slutföra registreringen. 
2. När vi har fått all nödvändig information från dig skickar vi avtalet för Microsoft Intune-appartner till dig för underskrift. Det här avtalet beskriver villkoren som ditt företag måste acceptera för att bli en Microsoft Intune-appartner. 
3. Du meddelas när din app har registrerats med Microsoft Intune-tjänsten och när appen publiceras på webbplatsen för [Microsoft Intune-partner](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). 
4. Djuplänken för din app läggs sedan till i nästa månatliga Intune Service-uppdatering. Om registreringsinformationen exempelvis är komplett i juli, stöds appens djuplänk i mitten av augusti. 

Om appens djuplänk ändras i framtiden måste du registrera om appen. Informera oss också om du uppdaterar din app med en ny version av Intune App SDK.



## Hämta SDK-filerna

Intune App SDK:er för interna iOS- och Android-appar finns på ett Microsoft GitHub-konto. De offentliga lagringsplatserna nedan innehåller SDK-filer för iOS och Android, respektive:

* [Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

**Om din app är en Xamarin- eller Cordova-app använder du utvecklingsverktygen nedan**:

* [Intune App SDK Xamarin-komponenten](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova-plugin-programmet](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Vi rekommenderar att du registrerar dig för ett GitHub-konto som du kan använda för att skapa förgreningar och använda pull i våra databaser. GitHub gör att utvecklare kan kommunicera med vårt produktteam, öppna frågor och få snabba svar, se versionsanmärkningar och lämna feedback till Microsoft. Kontakta msintuneappsdk@microsoft.com för frågor om GitHub-kontot och lagringsplatser.





## Aktivera din iOS- eller Android-mobilapp för MAM med SDK

Om du vill integrera Intune App SDK med en intern iOS-app behöver du följande: 

* **[Utvecklarhandbok för Intune App SDK för iOS](intune-app-sdk-ios.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din iOS-mobilapp med Intune App SDK. 


Om du vill integrera Intune App SDK med en intern Android-app behöver du följande:

* **[Utvecklarhandbok för Intune App SDK för Android](intune-app-sdk-android.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din Android-mobilapp med Intune App SDK. 

Dokumentationen för Intune App SDK Xamarin-komponenten och Intune App SDK Cordova-plugin-programmet finns i deras respektive GitHub-databaser. 


## Konfigurera telemetri för din app

Microsoft Intune samlar in data för användningsstatistik för din app.

* **Intune App SDK för iOS**: SDK loggar SDK-telemetridata om användningshändelser som standard. Dessa data skickas till Microsoft Intune.

    * Om du väljer att inte skicka SDK-telemetridata till Microsoft Intune från din app måste du inaktivera telemetriöverföring genom att tilldela egenskapen `MAMTelemetryDisabled` värdet ”YES” i IntuneMAMSettings-ordlistan.

* **Intune App SDK för Android**: Telemetridata loggas inte via SDK.

## Testa din MAM-aktiverade app med Microsoft Intune

När du har slutfört de nödvändiga stegen för att integrera din iOS- eller Android-app med Intune App SDK måste du se till att alla apphanteringsprinciper är aktiverade och fungerar för slutanvändaren och IT-administratören. Du behöver följande för att testa din integrerade app:

<!--TODO-->

* **Testa din MAM-aktiverade app med Microsoft Intune**: Det här dokumentet beskriver steg för steg hur du testar dina MAM-aktiverade iOS- eller Android-appar med Microsoft Intune. Du hittar det här dokumentet i GitHub-lagringsplatserna för SDK:erna.

* **Microsoft Intune-konto**: Du behöver ett Microsoft Intune-konto för att kunna testa dina MAM-aktiverade appar med Microsoft Intune. 
    * Om du är en oberoende programvaruleverantör (ISV) som aktiverar iOS- eller Android-appar för Intune MAM får du en kampanjkod när du har slutfört registreringen med Microsoft Intune (se beskrivningen i registreringsavsnittet). Med kampanjkoden kan du registrera dig för en utvärderingsversion av Microsoft Intune med ett års utökad användning. 
    * Om du utvecklar en affärsapp som inte ska publiceras i butiken måste du ha åtkomst till Microsoft Intune via din organisation. Du kan också registrera dig för en kostnadsfri 1-månads utvärderingsversion med [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).




<!--HONumber=Oct16_HO3-->


