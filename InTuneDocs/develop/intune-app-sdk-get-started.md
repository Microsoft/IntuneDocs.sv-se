---
# required metadata

title: Komma igång med Microsoft Intune App SDK | Microsoft Intune
description:
keywords:
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 38ebd3f5-cfcc-4204-8a75-6e2f162cd7c1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Komma igång med Microsoft Intune App SDK

Den här Kom igång-guiden hjälper dig att snabbt aktivera din mobilapp för hantering av mobilprogram med Microsoft Intune. Det kan vara bra att först förstå fördelarna med Intune App SDK som räknas upp i [översikten över Intune App SDK](intune-app-sdk.md).

Den här guiden går igenom de viktigaste stegen när du ska aktivera hantering av mobilappar i en app med Microsoft Intune. Intune App SDK stöder liknande scenarier mellan plattformar och är avsett att ge IT-administratörer en enhetlig miljö på olika plattformar. På grund av plattformsbegränsningar förekommer det dock mindre skillnader vad gäller stödet av vissa funktioner.

# Komma igång

## Registrera dig för Microsoft Connect

Intune App SDK är tillgängligt via Microsoft Connect och kräver registrering. Det gör du genom att registrera dig för ett [Microsoft-konto](https://connect.microsoft.com/ConfigurationManagervnext/InvitationUse.aspx?ProgramID=8967&InvitationID=8967-YJYJ-8G6X) med företagets e-postadress.

Registreringen har väntande status tills Intune-teamet har granskat din begäran. Svarstiden är normalt 2–3 arbetsdagar. När registreringen har godkänts får du ett e-postmeddelande med en nedladdningslänk för Intune App SDK för din eller dina plattformar samt relaterade handböcker. Du kan också komma åt dessa guider på webbplatsen MSDN.

## Registrera din Store-app med Microsoft Intune

**Om din aktiverade app är en intern företagsapp som inte ska publiceras i Apple Store eller Google App Store**: Du behöver inte registrera appen. IT-administratören läser in sådana interna appar direkt i Microsoft Intune-konsolen för distribution. Intune känner av att appen har byggts med SDK och IT-administratören kan välja att tillämpa MAM-principen på den. Du kan hoppa till avsnittet [Aktivera din iOS- eller Android-mobilapp för MAM med SDK](#enable-your-ios-or-android-mobile-app-for-mam-with-the-sdk).

**Om du är en oberoende programvaruleverantör (ISV) och utvecklar en app som ska göras tillgänglig för kunder via Apple  eller Google App Store**: Du måste först registrera din app med Microsoft Intune och acceptera registreringsvillkoren. Du kan uppge appens djuplänk vid detta tillfälle. Därefter kan en IT-administratör tillämpa Intune MAM-principen på appen. MAM-principen kan inte tillämpas på appens djuplänk i administrationskonsolen förrän registreringen har slutförts och bekräftats av Microsoft Intune-teamet. Microsoft har också en Microsoft Intune-partnerwebbplats där appen registreras så att kunder vet att den stöder Microsoft Intunes MAM-princip.

Börja registreringen genom att **läsa och underteckna** [partneravtalet för Microsoft Intune](https://connect.microsoft.com/ConfigurationManagervnext/Survey/Survey.aspx?SurveyID=17806). Det här avtalet beskriver villkoren som ditt företag måste acceptera för att bli en Microsoft Intune-appartner. Du måste logga in innan du kan visa det här dokumentet. Du hittar avtalet på Microsoft Connect-webbplatsen för Intune App SDK under fliken för undersökningar eller här. Vi ber dig även att uppge namnet på appen, företagets namn, samt Google Stores eller iTunes Stores djuplänk till din app.

![Microsoft Connect](../media/microsoft-connect.png)

Vi använder e-postadressen som du angav när du registrerade dig för att bekräfta och slutföra registreringen. Vi använder även samma e-postadress för att kontakta dig om vi har frågor.

**Hur ser registreringsprocessen ut?**När du har skickat formuläret kontaktar Microsoft dig på den e-postadress som du uppgav vid registreringen, antingen för att bekräfta att registreringen mottagits eller för att be om ytterligare information som krävs för att slutföra registreringen. Du blir också kontaktad när din app har registrerats med Microsoft Intune och när appen publiceras på Microsoft Intunes partnerwebbplats. När vi har bekräftat att vi tagit emot din information tas din apps djuplänk med i nästa månads Intune-tjänstuppdatering. Om registreringsinformationen exempelvis är komplett i juli, stöds appens djuplänk i mitten av augusti. Om appens djuplänk ändras i framtiden måste du registrera om appen. Meddela oss också om du uppdaterar appen med en ny version av Intune App SDK.

**Obs!**All information som samlas in i formuläret ovan och via e-postkommunikation med Intune-teamet följer [Microsofts sekretesspolicy](https://www.microsoft.com/en-us/privacystatement/default.aspx).

## Aktivera din iOS- eller Android-mobilapp för MAM med SDK

Du behöver följande för att aktivera din iOS-mobilapp:

1. **[Utvecklarhandbok för Intune App SDK för iOS](intune-app-sdk-ios.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din iOS-mobilapp med Intune App SDK. Du  hittar det här dokumentet i dokumentationsmappen som hämtas som en del av Intune App SDK-paketet.
2. **Intune App SDK för iOS**: Som en del av Intune App SDK-paketet som du hämtar från Microsoft Intune hittar du den signerade mappen ”Intune App SDK for iOS”. Den här mappen innehåller allt innehåll för Intune App SDK för iOS.

Du behöver följande för att aktivera din Android-mobilapp med Intune App SDK:

1. **[Utvecklarhandbok för Intune App SDK för Android](intune-app-sdk-android.md)**: Det här dokumentet beskriver steg för steg hur du aktiverar din Android-mobilapp med Intune App SDK. Du  hittar det här dokumentet i dokumentationsmappen som hämtas som en del av Intune App SDK-paketet.
2. **Intune App SDK för Android**: Som en del av Intune App SDK-paketet som du hämtar från Microsoft Intune hittar du den signerade mappen ”Intune App SDK for Android”. Den här mappen innehåller allt innehåll för Intune App SDK för Android.

## Inaktivera telemetri för din app

**Intune App SDK för iOS**: SDK loggar SDK-telemetridata om användningshändelser som standard. Dessa data skickas till Microsoft Intune.

Om du väljer att inte skicka SDK-telemetridata till Microsoft Intune från ditt program **måste du inaktivera** SDK-telemetriöverföring genom att tilldela egenskapen `MAMTelemetryDisabled` värdet ”YES” i `IntuneMAMSettings`.

**Intune App SDK för Android**: SDK-telemetridata loggas inte via SDK.

## Testa din MAM-aktiverade app med Microsoft Intune

När du har slutfört nödvändiga steg för att integrera Intune App SDK med iOS eller Android Intune App SDK måste du se till att alla apphanteringsprinciper är aktiverade och fungerar för slutanvändaren och IT-administratören. Du behöver följande för att testa integreringen:

1. **Testa din MAM-aktiverade app med Microsoft Intune**: Det här dokumentet beskriver steg för steg hur du testar dina MAM-aktiverade iOS- eller Android-appar med Microsoft Intune. Du  hittar det här dokumentet i dokumentationsmappen som hämtas som en del av Intune App SDK-paketet.
2. **Microsoft Intune-konto**: Du behöver ett Microsoft Intune-konto för att kunna testa dina MAM-aktiverade appar med Microsoft Intune. Om du är en oberoende programvaruleverantör (ISV) som aktiverar iOS- eller Android-appar för MAM får du en kampanjkod när du har slutfört registreringen med Microsoft Intune (se beskrivningen i registreringsavsnittet). Med kampanjkoden kan du registrera dig för en utvärderingsversion av Microsoft Intune med ett års utökad användning. Om du utvecklar en affärsapp som inte ska publiceras i butiken måste du ha åtkomst till Microsoft Intune via din organisation. Du kan också registrera dig för en kostnadsfri 1-månads utvärderingsversion med [Microsoft Intune](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0).



<!--HONumber=May16_HO2-->


