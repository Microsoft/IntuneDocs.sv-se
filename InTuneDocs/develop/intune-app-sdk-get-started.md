---
title: "Kom igång med Microsoft Intune App SDK | Microsoft Docs"
description: 
keywords: 
author: mtillman
manager: angrobe
ms.author: oydang
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1
ms.reviewer: oydang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6adfb7375f9747f64e7037164f48918789bd7ee0
ms.openlocfilehash: 7372cdd1c1001d621ba8374284e814951f55ef93


---

# <a name="get-started-with-the-microsoft-intune-app-sdk"></a>Kom igång med Microsoft Intune App SDK

Den här Kom igång-guiden hjälper dig att snabbt aktivera din mobilapp för mobil programhantering (MAM) med Microsoft Intune. Det kan vara bra att först förstå fördelarna med Intune App SDK:n som räknas upp i [Intune App SDK-översikt](intune-app-sdk.md).

Den här guiden går igenom de viktigaste stegen när du ska aktivera MAM i din app med Microsoft Intune. Intune App SDK:n stöder liknande scenarier mellan plattformar och är avsedd att ge IT-administratörer en enhetlig upplevelse på sina olika plattformar. På grund av plattformsbegränsningar förekommer dock smärre skillnader vad gäller stöd av vissa funktioner.

## <a name="register-your-store-app-with-microsoft"></a>Registrera din Store-app med Microsoft

**Om din app är en intern företagsapp som inte ska publiceras i en offentlig appbutik**:

Du *behöver inte* att registrera din app. För interna affärsspecifika appar, distribuerar IT-administratören appen internt. Intune identifierar att appen har skapats med SDK:n och tillåter att IT-administratören tillämpar MAM-principinställningar på den. Du kan hoppa till avsnittet [Aktivera din iOS- eller Android-mobilapp för MAM med SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Om din app kommer att publiceras på en offentlig appbutik som Apple App Store eller Google Play**:

*Måste* du först registrera din app med Microsoft Intune och samtycka med villkoren för registrering. Därefter kan IT-administratörer tillämpa Intunes MAM-principinställningar för den upplysta appen, som listas som en Intune-appartner. Intune administratörer kommer inte att ha möjlighet att tillämpa MAM-principen på din apps djuplänk förrän registreringen har slutförts och bekräftats av Microsoft Intune-teamet. Microsoft kommer även att lägga till din app till sin [Microsoft Intune-partnersida](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps). Där kommer appikonen att visas för att visa att den stöder Microsoft Intunes MAM-princip.

Fyll i [Microsoft Intune-appartner frågeformuläret](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR6oOVGFZ3pxJmwSN1N_eXwJUQUc5Mkw2UVU0VzI5WkhQOEYyMENWNDBWRS4u) för att påbörja registreringsprocessen.

Vi använder e-postadresserna som står i frågeformulärets svar för att kontakta dig och fortsätta registreringsprocessen. Vi använder även din e-postadress från registreringen för att kontakta dig om vi har frågor.

> [!NOTE]
> All information som samlas in i formuläret ovan och via e-postkommunikation med Microsoft Intune-teamet följer [Microsofts sekretesspolicy](https://www.microsoft.com/en-us/privacystatement/default.aspx).

**Hur ser registreringsprocessen ut?**:

1. När du har skickat frågeformuläret kontaktar Microsoft dig på den e-postadress som du uppgav vid registreringen, antingen för att bekräfta att registreringen mottagits eller för att be om ytterligare information som krävs för att slutföra registreringen.
2. När vi har fått all nödvändig information från dig skickar vi avtalet för Microsoft Intune-appartner till dig för underskrift. Det här avtalet beskriver villkoren som ditt företag måste godkänna för att bli en Microsoft Intune-appartner.
3. Du meddelas när din app har registrerats med Microsoft Intune-tjänsten och när appen publiceras på webbplatsen för [Microsoft Intune-partner](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps).
4. Slutligen läggs djuplänken för din app till i nästa månatliga Intune Service-uppdatering. Om registreringsinformationen exempelvis slutfördes i juli, stöds appens djuplänk i mitten av augusti.

Om din apps djuplänk ändras i framtiden, måste du omregistrera din app. Informera oss också om du uppdaterar din app med en ny version av Intune App SDK.



## <a name="download-the-sdk-files"></a>Hämta SDK-filerna

Intune App SDK:er för interna iOS- och Android-appar finns på ett Microsoft GitHub-konto. De här offentliga lagringsplatserna innehåller SDK-filer för iOS och Android:

* [Intune App SDK för iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios)
* [Intune App SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)

Om din app är en Xamarin- eller Cordova-app använder du de här utvecklingsverktygen:

* [Intune App SDK Xamarin-komponenten](https://github.com/msintuneappsdk/intune-app-sdk-xamarin)
* [Intune App SDK Cordova-insticksprogrammet](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam)

Det är en bra idé att registrera dig för ett GitHub-konto som du kan använda för att förgrena och använda pull i våra lagringsplatser. GitHub låter utvecklare kommunicera med vårt produktteam, öppna frågor och få snabba svar, se versionsanmärkningar och ge feedback till Microsoft. Kontakta msintuneappsdk@microsoft.com för frågor om GitHub-kontot och lagringsplatser.





## <a name="enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk"></a>Aktivera din iOS- eller Android-mobilapp för MAM med SDK

Om du vill integrera Intune App SDK med en intern iOS-app behöver du följande:

* **[Utvecklarguide för Intune App SDK för iOS](intune-app-sdk-ios.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din iOS-mobilapp med Intune App SDK.


Om du vill integrera Intune App SDK med en intern Android-app behöver du följande:

* **[Utvecklarhandbok för Intune App SDK för Android](intune-app-sdk-android.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din Android-mobilapp med Intune App SDK.

Om du vill skapa Cordova-appar med plugin-programmet Intune App SDK Cordova behöver du följande:

* **[Guide för plugin-programmet Intune App SDK Cordova](intune-app-sdk-cordova.md)**: Det här dokumentet hjälper dig att skapa iOS- och Android-appar med Cordova för hantering av mobilprogram i Intune.

Om du vill skapa Xamarin-appar med Intune App SDK Xamarin-komponenten behöver du följande:

* **[Guide för Intune App SDK Xamarin-komponenten](intune-app-sdk-xamarin.md)**: Det här dokumentet hjälper dig att skapa iOS- och Android-appar med Cordova för hantering av mobilprogram i Intune.




## <a name="configure-telemetry-for-your-app"></a>Konfigurera telemetri för din app

Microsoft Intune samlar in data för användningsstatistik för din app.

* **Intune App SDK för iOS**: SDK loggar SDK-telemetridata om användningshändelser som standard. Dessa data skickas till Microsoft Intune.

    * Om du väljer att inte skicka SDK-telemetridata till Microsoft Intune från din app måste du inaktivera telemetriöverföring genom att tilldela egenskapen `MAMTelemetryDisabled` värdet ”YES” i IntuneMAMSettings-ordlistan.

* **Intune App SDK för Android**: Telemetridata loggas inte via SDK.

## <a name="test-your-mam-enabled-app-with-microsoft-intune"></a>Testa din MAM-aktiverade app med Microsoft Intune

När du har slutfört de nödvändiga stegen för att integrera din iOS- eller Android-app med Intune App SDK så måste du se till att alla apphanteringsprinciper är aktiverade och fungerar för användaren och IT-administratören. Du behöver följande för att testa din integrerade app:

<!--TODO-->

* **Testa din MAM-aktiverade app med Microsoft Intune**: Det här dokumentet beskriver steg för steg hur du testar dina MAM-aktiverade iOS- eller Android-appar med Microsoft Intune. Du hittar det här dokumentet i GitHub-lagringsplatserna för SDK:erna.

* **Microsoft Intune-konto**: Du behöver ett Microsoft Intune-konto för att kunna testa dina MAM-aktiverade appar med Microsoft Intune.
    * Om du är en ISV som aktiverar dina iOS eller Android store-appar för Intune MAM, får du en kampanjkod när du har slutfört registreringen med Microsoft Intune, enligt beskrivningen i registreringssteget. Kampanjkoden låter dig registrera dig för en utvärderingsversion av Microsoft Intune med ett års utökad användning.
    * Om du utvecklar en affärsspecifik app som inte ska publiceras i butiken, förväntas du ha åtkomst till Microsoft Intune genom din organisation. Du kan också registrera dig för en månads kostnadsfri utvärdering av [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).



<!--HONumber=Dec16_HO2-->


