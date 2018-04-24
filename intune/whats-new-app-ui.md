---
title: Uppdateringar i användargränssnittet för Intunes slutanvändarappar
titlesuffix: Microsoft Intune
description: Ta reda på vad som har ändrats i användargränssnittet för appar som används på slutanvändarenheter med Microsoft Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8da396e41844c854cd18a9384fe97ac0bee59355
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/06/2018
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Uppdateringar i användargränssnittet för Intunes slutanvändarappar
Läs mer om de senaste uppdateringarna i användargränssnittet för appar som dina slutanvändare ser i den här versionen av Microsoft Intune. Att förstå dessa uppdateringar underlättar din användarkommunikation och eventuell uppdaterad anpassad dokumentation som du har skapat för att stödja distributionen. Det underlättar också felsökningen av eventuella problem som användarna har om de kontaktar supportavdelningen för att få hjälp med att använda företagsportalen.

<!---End-user messaging for accounts 1573558, 1712; changes to be made for other platforms for 1801 Users of the Company Portal website, will be blocked from taking actions that require write access to your tenant. They will see appropriate error messaging explaining that their account is under maintenance. Similar changes are coming to the Company Portal apps for Android, iOS, macOS, and Windows soon. ![Error message that occurs during account move](./media/account-move-rom-iwp-user-1712.png)--->

## <a name="week-of-april-2-2018"></a>Veckan 2 april 2018

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866 -->
Vi har släppt en större uppdatering av användarupplevelsen i företagsportalappen för iOS. Uppdateringen är en fullständig visuell omarbetning som ger appen en modernare design. Vi har bevarat appens funktionalitet men förbättrat användarvänligheten och tillgängligheten.  

Andra nyheter:
- Stöd för iPhone X.
- Snabbare appstart och inläsning som sparar tid för användarna.
- Fler förloppsindikatorer som ger användarna den senaste statusinformationen.
- Metoden att ladda upp loggar har förbättrats, vilket gör det enklare för användarna att rapportera om något går fel.  

|Före|Efter|
|---|---|
|![01](/intune/media/cp_iosRedesign_before_1803_01.png)|![01](/intune/media/cp_iosRedesign_after_1803_01.png)|
|*Kombineras med föregående steg*|![02](/intune/media/cp_iosRedesign_after_1803_02.png)|
|![03](/intune/media/cp_iosRedesign_before_1803_02.png)|![03](/intune/media/cp_iosRedesign_after_1803_03.png)|

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Språkförbättringar i företagsportalappen för Windows <!---1683758--->
Vi har förbättrat språket i företagsportalen för att Windows 10 ska vara mer användarvänligt och specifikt för ditt företag.

|Före|Efter|
|---|---|
|![01](./media/windows_enroll_before_1803.png)|![01](./media/windows_enroll_after_1803.png)|
|![02](./media/windows_view_policy_issues_before_1803.png)|![02](./media/windows_view_policy_issues_after_1803.png)

## <a name="week-of-march-12-2018"></a>Vecka 12 i mars 2018

#### <a name="company-portal-for-android-visual-updates---976944---"></a>Visuella uppdateringar i företagsportalen för Android <!--976944 -->

Vi har uppdaterat företagsportalappen för Android så att den följer Androids riktlinjer för [Materialdesign](https://material.io/).

|Före|Efter|
|---|---|
|![01](./media/android_about_before_1803.png)|![01](./media/androidCP_about_after_1803.png)|
|![02](./media/android_contact_it_before_1803.png)|![02](./media/android_contact_it_after_1803.png)|
|![03](./media/android_devices_before_1803.png)|![03](./media/androidCP_devicelist_after_1803.png)|
|![04](./media/android_device_details_before_1803.png)|![05](./media/androidCP_devicedetails_1_after1803.png)|
|![05](./media/android_device_details_update_settings_before_1803.png)|![05](./media/androidCP_devicedetails_red_box_2_after1803.png)|
|![06](./media/android_profile_before_1803.png)|![06](./media/android_profile_after_1803.png)|
|![07](./media/androidCP_Setup01_before_1803.png)|![07](./media/androidCP_Setup01_after_1803.png)|


## <a name="week-of-november-27-2017"></a>Veckan som börjar med 27 november 2017

### <a name="new-device-categories-step-in-guided-setup-for-the-company-portal-app-for-windows-10----1335292---"></a>Nytt steg för "Enhetskategorier" i den guidade konfigurationen för företagsportalappen för Windows 10 <!---1335292--->

Om du har aktiverat [Mappning av enhetsgrupp](device-group-mapping.md) får användarna nu vägledning i företagsportalappen för Windows 10 i hur de väljer en enhetskategori efter att de har registrerat sin enhet.

![Kategori för mappning av enhetsgrupp](./media/w10_cp_category_device_setup_after_1711.png)

## <a name="week-of-november-13-2017"></a>Veckan som börjar 13 november 2017

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen för iOS i version 2.9.0 <!---1417174--->

Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för iOS. Språket är mer användarvänligt och vi har kombinerat skärmar där det är möjligt. Vi har också gjort språket mer specifikt för ditt företag genom att använda företagsnamnet genomgående i installationstexten.

> [!NOTE]
> Vi använder företagets namn som du har angett i Azure Portal i **Microsoft Intune** > **mobilappar** > **företagsportalanpassning** > **företagsnamn**. Om du inte har angett det här värdet, använder vi det klientnamn som ställts in i **Azure Active Directory** > **egenskaper** > **namn**. Om du inte har angett något företagsnamn i företagsportalsanpassningen och inte vill att ditt klientnamn ska visas, rekommenderar vi att du anger företagets namn i företagsportalens anpassningsflik. Om du inte vill att den här strängen ska visas i rubriken till företagsportalen, kan du avmarkera kryssrutan visa företagets namn bredvid logotypen.

|Före|Efter|
|---|---|
|![01](./media/ios_cp_enroll_01_before_1711.png)|![01](./media/ios_cp_enroll_01_after_1711.png)|
|![02](./media/ios_cp_enroll_02_before_1711.png)|*Kombineras med föregående steg*|
|![03](./media/ios_cp_enroll_03_before_1711.png)|![03](./media/ios_cp_enroll_03_after_1711.png)|
|![04](./media/ios_cp_enroll_04_before_1711.png)|![04](./media/ios_cp_enroll_04_after_1711.png)|
|![05](./media/ios_cp_enroll_05_before_1711.png)|![05](./media/ios_cp_enroll_05_after_1711.png)|
|![06](./media/ios_cp_enroll_06_before_1711.png)|![06](./media/ios_cp_enroll_06_after_1711.png)|
|![07](./media/ios_cp_enroll_07_before_1711.png)|![07](./media/ios_cp_enroll_07_after_1711.png)|


## <a name="week-of-november-6-2017"></a>Veckan som börjar med 6 november 2017

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Uppdateringar i företagsportalappen för Windows 10 <!--1299474-->
Inställningssidan i företagsportalappen för Windows 10 har uppdaterats för att inställningar och avsedda användaråtgärder ska vara mer konsekventa över alla inställningar. Den har också uppdaterats så att den matchar layouten för andra Windows-appar.

|Före|Efter|
|---|---|
|![01](./media/w10-share-logs.png)|![02](./media/w10-share-logs-after-1711.png)|


### <a name="search-improvements-to-the-company-portal-apps-and-website---1418189--"></a>Sökförbättringar i företagsportalens appar och webbplats <!--1418189-->
Företagsportalapparna använder nu sökningar i appkategorier, namn och beskrivningar. Resultaten sorteras i fallande relevansordning. De här uppdateringarna är även tillgängliga på [företagsportalwebbplatsen](https://portal.manage.microsoft.com).

Vi finjusterar fortfarande spårningen av relevans, så meddela oss gärna hur det fungerar via länken "Feedback" längst ned på företagsportalwebbplatsen.

## <a name="week-of-october-16-2017"></a>Veckan som börjar med 16 oktober 2017

### <a name="search-improvements-to-the-company-portal-website---1331697--"></a>Sökförbättringar på företagsportalwebbplatsen <!--1331697-->
Vi förbättrar appsökfunktionerna och börjar med [företagsportalwebbplatsen](https://portal.manage.microsoft.com). Sökningar utförs nu även på appkategorier, utöver fälten Namn och Beskrivning. Resultaten sorteras i fallande relevansordning som standard. 

Även iOS-användare får denna ändring, eftersom företagsportalwebbplatsen också används som en del av företagsportalappen för iOS. Företagsportalapparna för Android och Windows får liknande uppdateringar under de kommande månaderna.

Vi finjusterar fortfarande spårningen av relevans, så meddela oss gärna hur det fungerar via länken "Feedback" längst ned på företagsportalwebbplatsen.


### <a name="ios-company-portal-displays-large-icons----1454593---"></a>iOS företagsportal visar stora ikoner <!-- 1454593 -->
I den här versionen åtgärdas ett känt problem med hur iOS företagsportal visar ikoner i appanelen. Om du överför appikoner på 120 × 120 bildpunkter eller större, visas de nu på [Företagsportalens webbplats](https://portal.manage.microsoft.com) och på appsidorna i Företagsportalen för iOS i full storlek i appanelen.


## <a name="week-of-october-2-2017"></a>Veckan då den 2 oktober 2017 infaller

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Förbättringar av arbetsflödet för enhetskonfiguration i företagsportalen <!--1490692-->
Vi har förbättrat arbetsflödet för enhetskonfiguration i företagsportalappen för Android. Språket är mer användarvänligt och specifikt för ditt företag, och vi har kombinerat skärmar där det är möjligt. 

|Före|Efter|
|---|---|
|![01](./media/android_cp_enroll_01_post_1709.png)|![01](./media/android_cp_enroll_01_1709_new.png)|
|![01a](./media/android_cp_enroll_01_before_1710.png)| *Kombineras med föregående steg* |
|![02](./media/android_cp_enroll_02_before_1710.png)|![02](./media/android_cp_enroll_02_after_1710.png)|
|![03](./media/android_cp_enroll_03_before_1710.png)|![03](./media/android_cp_enroll_03_after_1710.png)|

Ytterligare åtgärder har förbättrats på Android for Work-enheter.

|Före|Efter|
|---|---|
|![04](./media/android_work_cp_enroll_01_before_1710.png)|![04](./media/android_work_cp_enroll_01_after_1710.png)|
|![05](./media/android_work_cp_enroll_02_before_1710.png)| *Kombineras med föregående steg* |
|![06](./media/android_work_cp_enroll_03_before_1710.png)|![06](./media/android_work_cp_enroll_03_after_1710.png)|
|![07](./media/android_work_cp_enroll_04_before_1710.png)|![07](./media/android_work_cp_enroll_04_after_1710.png)|
|![08](./media/android_work_cp_enroll_05_before_1710.png)| *Kombineras med föregående steg* |


Vi har även uppdaterat e-postaktiveringsskärmen för villkorlig åtkomst.

|Före|Efter|
|---|---|
|![06](./media/android_conditional_access_email_before_1710.png)|![06](./media/android_conditional_access_email_after_1710.png)

## <a name="week-of-september-11-2017"></a>Veckan då den 11 september 2017 infaller

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Enklare formuleringar i företagsportalappen för Android <!---1396349--->  

Registreringen av företagsportalappen för Android har förenklats med ny text som gör det enklare för slutanvändarna att registrera sig. Om du har anpassad registreringsdokumentation bör du uppdatera den så att den återspeglar de nya skärmarna. Du hittar exempelbilder nedan:

|Före|Efter|
|---|---|
|![01](./media/android_cp_enroll_01_before_1709.png)|![01](./media/android_cp_enroll_01_post_1709.png)|
|![02](./media/android_cp_enroll_02_before_1709.png)|![02](./media/android_cp_enroll_02_post_1709.png)|
|![03](./media/android_cp_enroll_03_before_1709.png)|![03](./media/android_cp_enroll_03_post_1709.png)|
|![04](./media/android_cp_enroll_04_before_1709.png)|![04](./media/android_cp_enroll_04_post_1709.png)|
|![05](./media/android_cp_enroll_05_before_1709.png)|![05](./media/android_cp_enroll_05_post_1709.png)|


## <a name="august-2017"></a>Augusti 2017

### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>E-postprogrammet för iOS 11 stöder OAuth<!---1196951--->

Villkorlig åtkomst med Intune stöder säkrare autentisering på iOS-enheter med OAuth. Ett annat flöde på företagsportalappen för iOS kommer att användas för att möjliggöra säkrare autentisering. När användare försöker logga in på ett nytt Exchange-konto i e-postprogrammet visas en dialogruta om webbvyn. Vid registreringen i Intune visas en dialogruta som ger det inbyggda e-postprogrammet åtkomst till ett certifikat. De flesta användarna kommer inte att se e-postmeddelanden i karantän längre. För befintliga e-postkonton används även i fortsättningen det grundläggande protokollet för autentisering, så dessa användare kommer fortfarande att få e-postmeddelanden i karantän levererade till sig. Den här inloggningen för slutanvändare liknar den på Office-mobilappar.

![Välj kontotyp i det inbyggda e-postprogrammet.](./media/ios-11-ca-email-after-1708-01.png)

![När du har valt Exchange visar iOS-enheten en dialogruta som frågar efter e-postadressen och kontonamnet.](./media/ios-11-ca-email-after-1708-02.png)

![Ange e-postadress och kontonamn.](./media/ios-11-ca-email-after-1708-03.png)

![Skickas till den externa Microsoft-inloggningssidan.](./media/ios-11-ca-email-after-1708-04.png)

![Ange ett lösenord på Microsoft-sidan.](./media/ios-11-ca-email-after-1708-05.png)

![Microsoft uppmanar användaren att registrera enheten för hantering.](./media/ios-11-ca-email-after-1708-06.png)

![Användaren uppmanas att registrera från företagsportalens webbplats.](./media/ios-11-ca-email-after-1708-07.png)



### <a name="intune-mobile-application-management-mam-dialog-boxes-will-have-a-modern-interface----1199015---"></a>Dialogrutor för hantering av mobilprogram i Intune (MAM) kommer att få ett modernt gränssnitt <!-- 1199015 -->

Dialogrutor för hantering av mobilprogram i Intune (MAM) kommer att uppdaterats till ett modernt utseende. Dialogrutorna kommer att fungera på samma sätt som tidigare.

**Tidigare upplevelse**

![gammalt gränssnitt](./media/NewUI_Old_AttachFileHandler.jpg)

**Modern upplevelse**

![modernt gränssnitt](./media/NewUI_Modern_AttachFileHandler.jpg)


### <a name="updates-to-the-device-details-page-on-the-company-portal-app-for-windows-10----1287448---"></a>Uppdateringar av sidan Enhetsinformation i företagsportalappen för Windows 10 <!---1287448--->

Företagsportalappen för Windows 10 flyttar __Kategori__-taggen från under rubriken till en egenskap på sidan __Enhetsinformation__.

![Företagsportalappen för Windows-skärmen Enhetsinformation där nu fältet Kategorier visas som en egenskap istället för direkt under rubriken på skärmen.](./media/cp_win10_category_tag_move_after_1708.png)

## <a name="july-2017"></a>Juli 2017

### <a name="apps-details-pages-will-display-new-information-for-android-devices---1287476--"></a>Sidor med appinformation kommer att visa ny information för Android-enheter <!--1287476-->

Sidan med appinformation i företagsportalappen för Android visar nu de appkategorier som IT-administratören har definierat för den appen.

![Den nya appinformationssidan](./media/cp_android_appdetails_after_1708.png)

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->

Vi informerar om en förändring som kommer under de kommande månaderna som kommer att förbättra inloggningen för Intune-företagsappar för Android, iOS och Windows. Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.  

Nedan kan du se den tidigare inloggningen, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet.

__Föregående inloggning__

![Företagsportalens inloggningssida med en ikon som föreställer en person framför en grafisk bild av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_before_1704_001.png)

![Användarna anger sina autentiseringsuppgifter på den här sidan när de har tryckt på Logga in, vilken begär användarens e-post och lösenord, tillsammans med förslag på att lösa lösenordsfel.](./media/cp_ios_aad_signin_before_1704_002.png)

![När de har angett sina lösenord loggas de in på företagsportalappen, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_before_1704_003.png)

__Ny inloggning__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_after_1704_001.png)

![Användaren ombeds endast att ange sin e-postadress, i stället för sin e-post och lösenord på samma skärm.](./media/cp_ios_aad_signin_after_1704_002.png)

![Användaren uppmanas att ange lösenordet när e-postadressen har accepterats.](./media/cp_ios_aad_signin_after_1704_003.png)

![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Ny inloggning vid inloggning från en annan enhet__

![Företagsportalens inloggningssida med en ikon som föreställer en person framför en grafisk bild av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Tryck på länken __Logga in från en annan enhet__.

![Instruktioner visas för att gå till sidan aka.ms/devicelogin med ett unikt lösenord från din arbetsdator. Därefter använder du koden för att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Starta en webbläsare och gå till [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![En bild av användarens webbläsare på arbetsdatorn, i stället för företagsportalappen. Sidan ”Inloggning på enhet” visas och uppmanar användarna ange koden de fick i företagsportalsappen.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Ange koden som du såg i företagsportalsappen. När du väljer __Fortsätt__, kommer du att kunna autentisera med någon av metoderna som stöds av ditt företag, till exempel ett smartkort.

![Användaren har matat in sin unika kod i fältet och webbplatsen ”Inloggning på enhet” har begärt en bekräftelse på att Intunes företagsportal är rätt app för att få behörighet att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![En bekräftelsesida som anger att användaren har loggat in i företagsportalsappen på sin enhet visas nu, och den här sidan kan stängas.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

Företagsportalappen börjar logga in.

![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="june-2017"></a>Juni 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies"></a>Företagsportalappen för Android har nu ett nytt användargränssnitt för appskyddsprinciper
Baserat på feedback från våra kunder har vi ändrat företagsportalappen för Android så att den visar knappen **Åtkomst till företagsinnehåll**. Avsikten är att förhindra användare från att i onödan gå genom registreringsprocessen när de bara behöver åtkomst till appar som stöder appskyddsprinciper, en funktion i Intune för hantering av mobilappar.

Användaren kan då trycka på knappen **Åtkomst till företagsinnehåll** i stället för att börja registrera enheten.

![En bild av Android-företagsportalappen, som i stor text visar Åtkomst till företagsinnehåll i mitten i stället för att erbjuda registreringsalternativ som i standardfallet](./media/and_access_company_content_after_1706.png)

Användaren tas sedan till webbplatsen för företagsportalen för att auktorisera appen för användning på sin enhet. Användarens autentiseringsuppgifter verifieras på webbplatsen för företagsportalen.

![En bild på företagsportalens webbplats som bekräftar inloggningen.](./media/and_iwp_sign_in_auth_page_after_1706.png)

Enheten kan fortfarande registreras för fullständig hantering genom att användaren trycker på menyn **Åtgärd**.

![En bild av företagsportalappen för Android som visar menyn från det övre högra hörnet på skärmen med ett alternativ för att registrera enheten.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Förbättringar av appsynkronisering med Windows 10 Creators Update <!--676505-->

Företagsportalen för Windows 10 kommer automatiskt att initiera en synkronisering för appinstallationsbegäranden för enheter med Windows 10 Creators Update (1703). Detta minskar problemen där appen fastnar vid tillståndet ”Väntar på synkronisering” när installationer utförs. Dessutom kommer användare att kunna initiera en synkronisering från appen manuellt.

![En bild av företagsportalappen för Windows 10, där hämtningen av Microsoft Word är i ett väntande tillstånd från företagsportalens appbutik.](./media/w10_download_pending_after_1706.png)

![En bild av företagsportalappen för Windows 10 där den nya automatiska synkroniseringsstatusen visar ett statusmeddelande som anger att enheten synkroniseras och försöker ladda ned appen.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!---1058938--->
Företagsportalappen för Windows 10 kommer att innehålla en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar som hjälper användaren att utföra AAD-registrering (krävs för villkorliga åtkomstfunktioner) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden kommer att vara tillgänglig på företagsportalens startsida. Användarna kan fortsätta att använda appen även om de inte slutför registreringen, men de får begränsad funktionalitet.

Den här uppdateringen visas bara på enheter som kör Windows 10 Anniversary Update (version 1607) eller senare.

![En bild av startsidan i företagsportalappen i Windows 10 med ett statusmeddelande i mitten av enhetslistan som talar om för användaren att enheten han eller hon använder inte har konfigurerats för företagsanvändning ännu och att användaren ska välja meddelandet för att påbörja installationen.](./media/win10_guided_enroll_select_setup_after_1706.png)

![En bild av konfigurationssidan i företagsportalappen i Windows 10 med en varning till användaren om att han eller hon behöver lägga till ett företagskonto till den här enheten och sedan registrera enheten för hantering.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![En bild av sidan Lägg till ett företagskonto på den här enheten i företagsportalappen i Windows 10, där användaren uppmanas att gå till appen Inställningar och välja ”Anslut” för att slutföra registreringen. När användaren har gjort det visas ett meddelande om att användaren måste gå tillbaka till företagsportalappen och slutföra registreringen.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![En bild av skärmen enroll into management (registrera för hantering) i företagsportalappen i Windows 10 som visar ett statusmeddelande om slutförd åtgärd som informerar om att användarens enhet nu har registrerats och att användaren ska trycka på Nästa för att fortsätta.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![En bild av slutförandeskärmen i företagsportalappen i Windows 10, där användaren informeras om att allt är klart samt att enheten har registrerats och ett företagskonto har lagts till det på rätt sätt.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Ny menyåtgärd för att enkelt ta bort Företagsportalen <!--1164569-->
Baserat på användarfeedback har vi lagt till en ny menyåtgärd i företagsportalen för Android för att ta bort den från din enhet. Den här åtgärden tar bort enheten från Intune-hanteringen så att användaren kan ta bort appen från enheten.

![En bild av företagsportalappen för Android med åtgärdsmenyn öppnad i det övre högra hörnet. Det nya alternativet ”ta bort företagsportal” finns tillgängligt som det tredje alternativet under ”min profil” och ”inställningar” och ovanför ”användarvillkor”, ”hjälp och feedback” och ”om”.](./media/android_remove_cp_menu_action_after_1705.png)

![En bild av dialogrutan som visas när du har valt det nya alternativet ”ta bort företagsportalen” i åtgärdsmenyn. Dialogrutan informerar användaren att ”genom att ta bort företagsportalen kommer enheten inte längre att hanteras av IT-administratören och åtkomst till företagsdata, företagsappar och företagets e-post kan tas bort." Användaren ombes sedan att bekräfta att de vill ta bort företagsportalappen genom att välja ”Ja”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios---1230777--"></a>Förbättringar av appaneler i företagsportalappen för iOS <!--1230777-->
Vi har uppdaterat designen av appaneler på startsidan så att de återspeglar anpassningsfärgen som du angett för Företagsportalen.

**Före**

![En avbildning av företagsportalsappen för iOS från tidpunkten innan uppdateringen gjordes, och som visade förinställda utfyllningsbilder för ”alla appar”, ”aktuella appar” och ”kategorier."](./media/cp_ios_homepage_before_1705.png)

**Efter**

![En bild av företagsportalsappen för iOS efter uppdateringen, vilken nu visar möjligheten att välja de färger som är relevanta för din organisation.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Kontoväljaren finns nu tillgänglig för företagsportalappen för iOS
Om användarna har använt sina arbets- eller skolkonton för att logga in till andra Microsoft-appar på sina iOS-enheter, så kan det hända att de ser den nya kontoväljaren när de loggar in på företagsportalen för första gången.

![En bild av kontoväljaren som visar testanvändaren Robin Swanson som väljer mellan en av två e-postadresser. Det finns olika knappar under de respektive adresserna, med vilka användaren kan välja konto att logga in med.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>April 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nya ikoner för Managed Browser och företagsportalen <!--918433, 918431-->

Den hanterade webbläsaren får uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det överensstämmer med andra appar i Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

Företagsportalen har också fått uppdaterade ikoner för Android-, iOS- och Windows-versionerna av appen, för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis till plattformarna från april till slutet av maj.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggningen i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn går igenom nya statusmeddelanden, med början på "Ansluter...", sedan "Loggar in...", följt av "Kontrollerar säkerhetskrav..." innan användaren kommer åt appen.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width="200" height="366" align="center">
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width="200" height="366" align="center">
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign-in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width="200" height="366" align="center">
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Appens installationsstatus har förbättrats för Företagsportalappen för Windows 10 <!--676495-->
Företagsportalappen för Windows 10 innehåller nu en förloppsindikator för installation på appinformationssidan. Den stöds för moderna appar på enheter som kör Windows 10 Anniversary Update och senare.

__Före__ ![En avbildning av den tidigare versionen av inläsningsskärmen där status bara angavs som "Installerar".](./media/cp_win10_install_status_before_1704.png)

__Efter__ ![En avbildning av den uppdaterade versionen av inläsningsskärmen nu visar en förloppsindikator för installationen.](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>Februari 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622, announced 1702-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Enheter som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Gränssnitt__: Knapparna __Aktuella appar__ och __Alla appar__ har uppdaterats på fliken __Appar__. __Sökknappen__ är nu flytande.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Appar som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigering__: Alla appar visar en flikvy över __Aktuella__, __Alla__ och __Kategorier__ för att underlätta navigeringen. __Kontakta IT__ har effektiviserats för bättre läsbarhet.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width="200" height="366" align="center">
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Januari 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernisera företagsportalswebbplatsen <!--753980, announced 1701-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny", ![En liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar.

![Till vänster visas en bild av den aktuella versionen av webbplatsen för företagsportalen med dess tidigare version av Appar, Mina enheter och vyerna Aktuellt och Kategorier. Till höger visas en bild av den uppdaterade versionen av webbplatsen för företagsportalen med en uppdaterad appkarusell, lista över nyligen publicerade appar och uppdaterad kategorivy.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Kommer snart i användargränssnittet
Det här är våra planer för hur vi kan förbättra användarupplevelsen genom att uppdatera användargränssnittet.

> [!Note]
> Observera att bilderna nedan kan vara förhandsgranskningar och att den presenterade produkten kan skilja sig från presenterade versioner.

### <a name="ui-iwp"></a>Ny uppdatering av användarupplevelsen för företagsportalens webbplats <!--2000968-->

Vi presenterar en ny webbplats för företagsportalen i april, med uppdateringar av användargränssnittet, effektivare arbetsflöden och hjälpmedelsförbättringar. Detta inkluderar kundefterfrågade förbättringar som appdelning och förbättrad övergripande prestanda för att få en mer användarvänlig upplevelse.

Vi har lagt till några nya funktioner, baserat på feedback från kunder som du, som förbättrar befintliga funktioner och användbarhet:

-   Förbättringar i användargränssnittet på hela webbplatsen
-   Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger

Du behöver inte göra några förberedelser inför den här ändringen. Vi meddelar dig när den uppdaterade webbplatsen för företagsportalen blir tillgänglig för dig. Du kan dock behöva uppdatera slutanvändardokument med uppdaterade skärmbilder. Observera att du också kan behöva uppdatera dokumentationen för företagsportalappen för iOS, eftersom webbplatsen startar avsnittet **Appar** i iOS-appen.

|Uppdaterad|Föregånde|
|---|---|
|![Den uppdaterade enhetssidan visar enheten korrekt placerad ovanför enhetsinformationen, den dyker inte längre upp ovanför hela listan.](./media/iwp-device-after-1803.png)|![Den tidigare versionen av enhetssidan.](./media/iwp-device-before-1803.png)|
|![Den uppdaterade appinstallationssidan visar appen korrekt placerad ovanför en beskrivning och olika typer av installationsinformation, inklusive publiceringsdatum, version och typ av app.](./media/iwp-app-install-after-1803.png)|![Den tidigare versionen av appinstallationssidan.](./media/iwp-app-install-before-1803.png)|

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Gränssnittsuppdateringar på företagsportalswebbplatsen <!--1313244 part 2-->

__Uppdateringar av aktuella appar__ Vi har lagt till en särskild sida på webbplatsen där användarna kan bläddra bland appar som du har valt att presentera, och vi har gjort några gränssnittsförändringar på avsnittet Aktuella på startsidan.

![De färggranna ikonerna visar apparna. Det finns stora rutor med färg under varje app, där färgen hämtas från den huvudsakliga färgen i appens logotyp. Avsnittet ”Aktuella appar” visas längst upp i företagsportalappen.](./media/cp_win10_colorful_tiles_after_1708.png)



### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/cloud-platform/roadmap)
* [Nyheter i Intune](https://docs.microsoft.com/intune/whats-new)
