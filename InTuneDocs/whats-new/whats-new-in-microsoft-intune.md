---
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Nyheter i Microsoft Intune – December 2016
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Offentlig förhandsversion av nya Intune adminstratörsupplevelse på Azure<!--736542-->
Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er. Innan den här portalen får allmän tillgång för alla klienter i Intune, är vi glada att kunna meddela att vi ska börja lansera en förhandsversion av den här nya administratörupplevelsen senare denna månad för att välja klienter.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Under tiden kan du ta reda på mer om vad vi har på lager för Microsoft Intune i Azure-portalen i vår [nya dokumentation](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Om du har frågor om tidslinjen för migrering av din klientorganisation, kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Hantering av telekomkostnad i förhandsversionen av Azure-portalen<!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Multifaktorautentisering på alla plattformar <!--747590-->
Du kan nu använda multifaktorautentisering (MFA) på en grupp av användare när de registrerar en iOS-, Android-, Windows 8.1+- eller Windows Phone 8.1+-enhet från Azure-hanteringsportalen genom att konfigurera MFA på registreringsprogrammet för Microsoft Intune i Azure Active Directory.

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
Du kan blockera appar som inte stöds av principer för hantering av mobilappar (MAM) i Intune från att komma åt SharePoint Online.  Du kan komma igång med hantering av mobilappar i Intune i Azure Portal. Leta efter avsnittet __Villkorlig åtkomst__ i bladet __Inställningar__ som innehåller alternativet för SharePoint Online. Den här funktionen skickas separat från resten av versionen av tjänsten. Lär dig mer om den här nya funktionen [här](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>Möjlighet att begränsa registrering av mobila enheter<!--747596-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.
* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.
* För iOS finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Meddelanden

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Multifaktorautentisering då registreringen flyttar till Azure-portalen <!--VSO 750545-->
Administratörer gick tidigare till Intune-konsolen eller konsolen Konfigurationshanteraren (tidigare än versionen oktober 2016) för att ange MFA för Intune-registreringar. Med den här uppdaterade funktionen kommer du nu att logga in på [Microsoft Azure-portalen](https://manage.windowsazure.com) med dina Intune-autentiseringsuppgifter och konfigurera MFA-inställningar via Azure AD. Mer information om detta finns [här](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>Företagsportalappen för Android är nu tillgänglig i Kina <!--VSO 658093-->
Vi publicerar företagsportalappen för Android för hämtning i Kina. På grund av avsaknad av Google Play-butik i Kina, måste Android-enheter hämta appar från kinesiska appmarknadsplatser. Företagsportalappen för Android blir tillgänglig för hämtning på följande platser:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

Företagsportalappen för Android använder Google Play-tjänster för att kommunicera med Microsoft Intune-tjänsten. Eftersom Google Play-tjänster ännu inte är tillgängliga i Kina, kan utförandet av någon av följande aktiviteter ta upp till 8 timmar att slutföra. 

|Administrationskonsolen för Intune| Intune-företagsportalsapp för Android |Intune-företagsportalens webbplats|   
|---|---|---|
|Fullständig rensning| Ta bort en fjärransluten enhet| Ta bort enhet (lokal och fjärransluten)|
|Selektiv rensning| Återställ enhet| Återställ enhet|
|Nya eller uppdaterade appdistributioner| Installera tillgängliga branschspecifika appar| Återställning av enhetens lösenord|
|Fjärrlåsning|||
|Återställning av lösenord|||

## <a name="deprecations"></a>Föråldringar

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>Firefox har inte längre stöd för Silverlight<!--VSO TBA-->
Mozilla tar bort sitt stöd för Silverlight i version 52 av [webbläsaren Firefox](https://www.mozilla.org/firefox), sker i mars 2017. Därför kommer du inte längre att kunna logga in på den befintliga Intune-konsolen med Firefox-versioner som är större än 51. Vi rekommenderar att du använder Internet Explorer 10 eller 11 för att komma åt administrationskonsolen, eller en [version av Firefox före version 52](https://ftp.mozilla.org/pub/firefox/releases/). Intunes övergång till Azure-portalen gör att den stöder ett antal [moderna webbläsare](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) utan att vara beroende av Silverlight.

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Borttagning av principer för Exchange Online mobila inkorg <!--770687-->
Från och med december kommer administratörer inte längre att kunna visa eller konfigurera principer för mobila postlådor för Exchange Online (EAS) i Intune-konsolen. Den här ändringen kommer att lanseras till alla klienter i Intune under december och januari. Alla befintliga principer kommer att förbli såsom konfigurerade. Använd Exchange Management Shell för att konfigurera nya principer. Ta reda på mer [här](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Apparna Intune AV Player, Image Viewer och PDF Viewer stöds inte längre på Android <!--747553-->
Från mitten av december 2016 och framåt kommer användarna inte längre att kunna använda apparna Intune AV Player, Image Viewer och PDF Viewer. De här apparna har ersatts med appen Azure Information Protection. Lär dig mer om appen Azure Information Protection [här](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Tidigare versioner av Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->


