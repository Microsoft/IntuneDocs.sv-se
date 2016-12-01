---
title: "Den tidiga utgåvan | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f287a0ad082fa20a2e84abbf8f5585117aae6f57
ms.openlocfilehash: e604b8809bd444d9069d449a6c691a8444296623


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>Den tidiga utgåvan för Microsoft Intune – December

Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Offentlig förhandsversion av nya Intune adminstratörsupplevelse på Azure

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills din klient har migrerats, registrerar du dig för ett nytt utvärderingskonto på Intune eller tar en titt på den nya dokumentationen.

Om du har frågor om tidslinjen för migrering av din klientorganisation, kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Hantering av telekomkostnad i förhandsversionen av Azure-portalen<!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Multifaktorautentisering på alla plattformar <!--747590-->
Du kan nu använda multifaktorautentisering (MFA) på en grupp av användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet från Azure-hanteringsportalen genom att konfigurera MFA på registreringsprogrammet för Microsoft Intune i Azure Active Directory.

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>Villkorlig åtkomst för MAM med SharePoint Online <!--VSO 679339-->
Du kan blockera appar som inte stöds av principer för hantering av mobilappar (MAM) i Intune från att komma åt SharePoint Online.  Du kan komma igång med hantering av mobilappar i Intune i Azure Portal. Leta efter avsnittet __Villkorlig åtkomst__ i bladet __Inställningar__ som innehåller alternativet för SharePoint Online. Den här funktionen skickas separat från resten av versionen av tjänsten.

## <a name="notices"></a>Meddelanden

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multifaktorautentisering då registreringen flyttar till Azure-portalen <!--VSO 750545-->
Administratörer gick tidigare till Intune-konsolen eller konsolen Konfigurationshanteraren (tidigare än versionen 1610) för att ange MFA för Intune-registreringar. Med den här uppdaterade funktionen kommer du nu att logga in på [Microsoft Azure-portalen](https://manage.windowsazure.com) med dina Intune-autentiseringsuppgifter och konfigurera MFA-inställningar via Azure AD. Mer information om detta finns [här](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Företagsportalappen för Android är nu tillgänglig i Kina <!--VSO 658093-->
Vi publicerar företagsportalappen för Android för hämtning i Kina. På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska appmarknadsplatser. Företagsportalappen för Android blir tillgänglig för hämtning på 360, Tencent, Xiaomi, Wandoujia och Huawei. 

Företagsportalappen för Android använder Google Play-tjänster för att kommunicera med Microsoft Intune-tjänsten. Eftersom Google Play-tjänster ännu inte är tillgängliga i Kina, kan utförandet av någon av följande aktiviteter ta upp till 8 timmar att slutföra. 

|Administrationskonsolen för Intune| Intune-företagsportalsapp för Android |Intune-företagsportalens webbplats|   
|---|---|---|
|Fullständig rensning| Ta bort en fjärransluten enhet| Ta bort enhet (lokal och fjärransluten)|
|Selektiv rensning| Återställ enhet| Återställ enhet|
|Nya eller uppdaterade appdistributioner| Installera tillgängliga branschspecifika appar| Återställning av enhetens lösenord|
|Fjärrlåsning|||
|Återställning av lösenord|||

## <a name="deprecations"></a>Föråldringar

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Borttagning av principer för Exchange Online mobila inkorg <!--770687-->
Från och med december kommer administratörer inte längre att kunna visa eller konfigurera principer för mobila postlådor för Exchange Online (EAS) i Intune-konsolen. Den här ändringen kommer att lanseras till alla klienter i Intune under december och januari. Alla befintliga principer kommer att förbli såsom konfigurerade. Använd Exchange Management Shell för att konfigurera nya principer. Ta reda på mer [här](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Apparna Intune AV Player, Image Viewer och PDF Viewer stöds inte längre på Android <!--747553-->
Från mitten av december 2016 och framåt kommer användarna inte längre att kunna använda apparna Intune AV Player, Image Viewer och PDF Viewer. De här apparna har ersatts med appen Azure Information Protection. Lär dig mer om appen Azure Information Protection [här](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Nov16_HO4-->


