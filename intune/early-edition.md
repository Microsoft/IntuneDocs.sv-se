---
title: "Tidig utgåva"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7d54cb060dc44d29c95203138396f771abbb2325
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Den tidiga utgåvan för Microsoft Intune – Februari 2018

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på sidan med [nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker <!-- 1471783 -->

På Registreringsöversiktssidan, kommer du att kunna se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen, kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Förhindra slutanvändare från att lägga till eller ta bort konton i arbetsprofilen <!-- 1728700 -->    
När du distribuerar Gmail-appen till en Android for Work-profil så kan du förhindra användare från att lägga till eller ta bort konton i arbetsprofilen genom att använda inställningen **Lägg till och ta bort konton** i profilen för enhetsbegränsningar i Android for Work.

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 -->

Intune stöder registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Stöd för hälsostatus och hotstatusrapporter i Windows Defender<!--854704 -->

Det är viktigt att förstå Windows Defenders hälsa och status för att hantera Windows-datorer.  Intune lägger till nya rapporter och åtgärder till Windows Defender-agentens status och hälsa. Med en statussammanfattningsrapport i arbetsbelastningen för enhetsefterlevnad kan du se enheter som behöver något av följande:

- signaturuppdatering
- starta om
- manuella åtgärder
- fullständig genomsökning
- övriga agenttillstånd som kräver åtgärder

I vissa fall går det att vidta fjärreparationsåtgärder som utlösning av en signaturuppdatering.  Rapporten visar även hur många datorer som rapporteras som **Rengör**.

En detaljerad rapport för varje statuskategori visar de enskilda datorer som behöver åtgärdas eller vilka som rapporteras som **Rengör**.

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>Protokollundantag för program<!--1035509 eeready-->

Du kan skapa undantag till principen för MAM-dataöverföring i Intune (Mobile Application Management) för att öppna vissa ohanterade program. Sådana program måste vara betrodda av IT-avdelningen. Utöver de undantag du skapar är dataöverföringen ändå begränsad till program som hanteras av Intune när din dataöverföringsprincip är inställd på **endast hanterade appar**. Du kan skapa begränsningarna med protokoll (iOS) eller paket (Android).

Du kan exempelvis lägga till Webex-paketet som ett undantag till MAM-dataöverföringsprincipen. På så vis kan Webex-länkar i ett hanterat e-postmeddelande i Outlook öppnas direkt i Webex-programmet. Dataöverföringen är fortfarande begränsad i andra ohanterade program.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Anpassa teman för företagsportalen med hexkoder <!--1049561 eeready-->

Du kan anpassa temafärgen i företagsportalens appar med hexkoder. När du anger en hexkod kan Intune bestämma vilken textkod som ger den högsta kontrastnivån mellan textfärgen och bakgrundsfärgen per [WCAG 2.0-standarder](http://www.w3.org/TR/WCAG20). Du kan förhandsgranska både textfärgen och företagets logotyp mot färgen i **Mobilappar** > **Företagsportal**. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för skydd av slutpunkter<!--1102252 --> 

Nya inställningar för [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] läggs till i **Enhetskonfiguration** > **Profiler** > **Endpoint protection**. Följande inställningar läggs till: 

- Säkerhetsnivå för plattform: ange om säkerhetsnivå för plattform är aktiverat vid nästa omstart. Virtualiseringsbaserad säkerhet kräver Säker start. Virtualiseringsbaserad säkerhet kan också aktiveras med DMA-skydd (direkt minnesåtkomst). DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade.
- Virtualiseringsbaserad säkerhet: ange om virtualiseringsbaserad säkerhet är aktiverat vid nästa omstart. 
- Windows Defender Credential Guard: slå på Credential Guard med virtualiseringsbaserad säkerhet för att skydda autentiseringsuppgifter vid nästa omstart när både säkerhetsnivå för plattform med säker start och virtualiseringsbaserad säkerhet är aktiverat. Bland de tillgängliga alternativen finns **Inaktiverad**, **Aktiverat med UEFI-lås**, **Aktiverat utan lås** och **Inte konfigurerad**. 
  - Alternativet ”Inaktiverad” stänger av Credential Guard via fjärranslutning om det tidigare har slagits på med alternativet ”Aktiverat utan lås”.

  - Alternativet ”Aktiverat med UEFI-lås” ser till att Credential Guard inte kan inaktiveras med registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du har använt den här inställningen måste du ställa in gruppolicy på ”Inaktiverad” och ta bort säkerhetsfunktionerna från varje dator med en fysiskt närvarande användare för att rensa konfigurationen som finns kvar i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - Med alternativet ”Aktiverat utan lås” kan Credential Guard inaktiveras via fjärranslutning med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

  - Alternativet ”Inte konfigurerad” låter principinställningen vara odefinierad. Grupprincip skriver inte inställningar för principen till registret, så den har ingen påverkan på datorer eller användare. Om det finns en aktuell inställning i registret ändras den inte.

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>Synkronisera och distribuera glest paketerad Windows Store för företagsappar <!--1222672 -->
Offline-appar som du köpt från Windows Store för företag kommer att synkroniseras med Intune-portalen. Du kommer sedan att kunna distribuera apparna till enhetsgrupper eller användargrupper. Offline-appar installeras av Intune och inte av butiken.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Återställa lösenord för Android O-enheter <!-- 1238299 -->
Du kan återställa lösenorden för registrerade Android O-enheter. När du skickar en förfrågan om att ”återställa lösenord” till en Android O-enhet ställer den in ett nytt lösenord för upplåsning av enheten eller en hanterad profilutmaning till den aktuella användaren. Lösenordet eller utmaningen skickas baserat på om enheten har en profilägare eller enhetsägare, och träder i kraft omedelbart.

### <a name="local-device-security-option-settings----1251887---"></a>Inställningar för säkerhetsalternativ för lokal enhet <!-- 1251887 -->
Du kan aktivera säkerhetsinställningarna på Windows 10-enheter med de nya inställningarna för säkerhetsalternativ för den lokala enheten. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

Fr utbildningsprofiler finns nya inställningar under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**. 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nya inställningar för enhetsbegränsningar <!--1308926 -->

Två nya sekretessinställningar blir tillgängliga för enheter:

- **Publicera användaraktiviteter**: Ställ in den här på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen.

- **Endast lokala aktiviteter**: Ställ in det här alternativet på **Blockera** för att förhindra delad användning och upptäckt av nyligen använda resurser i aktivitetsväxlingen baserat på lokala aktiviteter.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Stöd för macOS-företagsportal för registreringar som använder Enhetsregistreringshanteraren <!-- 1352411 -->

Användarna kan använda Enhetsregistreringshanteraren när de registrerar sig med macOS-företagsportalen.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nya inställningar för Microsoft Edge-webbläsaren <!--1469166 -->

Två nya inställningar blir tillgängliga för enheter med Microsoft Edge-webbläsaren: **Sökväg till favoritfiler** och **Ändringar i Favoriter**. 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (PIA)-krypterad data i Windows-sökresultat <!-- 1469193 -->

En ny inställning i principen för Windows Information Protection (PIA) gör att du kan kontrollera om PIA-krypterade data ingår i Windows-sökresultaten.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1473977 -->
Intune erbjuder möjligheten att installera LOB-appar i macOS. LOB-appar är appar där du tillhandahåller installationsfilen och använder Intune för att installera appen på enheten. Som en del av stödet för LOB-appar i macOS måste du använda Microsoft Intunes programhanteringsverktyg för macOS för att bearbeta LOB-appar i macOS i förväg.

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Konfigurera resurskontoinställningar för Surface Hubs <!-- 1475674 -->

Du kan fjärrkonfigurera resurskontoinställningar för Surface Hubs.

Resurskontot används av en Surface Hub för att autentisera med Skype/Exchange så att den kan ansluta till ett möte. Du kan skapa ett unikt resurskonto så att Surface Hub visas i mötet som konferensrummet. Resurskontot kan till exempel visas som **konferensrum B41/6233**.

> [!NOTE]
> - Om du låter fält vara tomma åsidosätter du tidigare konfigurerade attribut på enheten.
>
> - Egenskaper för resurskonto kan ändras dynamiskt på Surface Hub. Exempelvis om lösenordsrotation är på. Det är alltså möjligt att värdena i Azure-konsolen tar lite tid på sig att återspegla enhetens verklighet. 
>
>   För att förstå vad som för närvarande konfigureras på Surface Hub kan resurskontoinformationen inkluderas i maskinvaruinventeringen (som redan har en intervall på 7 dagar) eller som skrivskyddade egenskaper. För att förbättra noggrannheten när en fjärråtgärd har vidtagits kan du genast hämta parametrarnas tillstånd när du har kört åtgärden för att uppdatera kontot/parametrarna på Surface Hub.

### <a name="ios-app-provisioning-configuration----1581650---"></a>Etableringskonfiguration för iOS-app <!-- 1581650 -->
Du kan tilldela iOS-apparetableringsprofiler för att förhindra att dina appar upphör genom att inkludera eller exkludera säkerhetsgrupper.

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Nya inställningar för Windows Defender Exploit Guard-princip <!-- 631893 -->

Sex nya inställningar för **minskning av attackytan** och utökade funktioner för **Reglerad mappåtkomst: Mappskydd** blir tillgängliga. Inställningarna finns här: Device configuration\Profiles\
Create profile\Endpoint protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Minska attackytan

|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Avancerat skydd för utpressningstrojan|Aktiverad, granskad, inte konfigurerad|Använd aggressivt skydd mot utpressningstrojan.|
|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem|Aktiverad, granskad, inte konfigurerad|Flagga stöld av inloggningsuppgifter från Windows Local Security Authority Subsystem (lsass.exe).|
|Skapa process från PSExec- och WMI-kommandon|Blockera, Granska, Inte konfigurerat|Blockera skapande av processer från PSExec- och WMI-kommandon.|
|Obetrodda och osignerade processer som körs via USB|Blockera, Granska, Inte konfigurerat|Blockera obetrodda och osignerade processer som körs via USB.|
|Körbara filer som inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista|Blockera, Granska, Inte konfigurerat|Blockera körbara filer från att köras om de inte uppfyller ett villkor för användningsmönster, ålder eller betrodd lista.|

#### <a name="controlled-folder-access"></a>Reglerad mappåtkomst

|Inställningsnamn  |Inställningsalternativ  |Description  |
|---------|---------|---------|
|Mappskydd (redan implementerat)|Inte konfigurerad, Aktivera, Endast granskning (redan implementerat)<br><br> **Nytt**<br>Blockera diskändring, Granska diskändring|
Skydda filer och mappar från obehöriga ändringar av oönskade appar.<br><br>**Aktivera**: Förhindra att obetrodda appar ändrar eller tar bort filer i skyddade mappar och skriver till disksektorer.<br><br>
**Blockera endast diskändring**:<br>Blockera obetrodda appar från att skriva till disksektorer. Obetrodda appar kan fortfarande ändra eller ta bort filer i skyddade mappar.|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nya Windows Defender Application Guard-inställningar <!-- 1631890 -->

- **Aktivera grafikacceleration**

Administratörer kan aktivera en virtuell grafikprocessor för Windows Defender Application Guard. Med den här inställningen kan processorn avlasta grafikåtergivning till vGPU. Detta kan förbättra prestanda när du arbetar med grafikintensiva webbplatser eller tittar på videor inuti behållaren.

- **SaveFilestoHost**

Administratörer kan aktivera att filer ska kunna skickas från Microsoft Edge som körs i behållaren så att de kan vara värdar för filsystem. Om du slår på det här kan användare ladda ned filer från Microsoft Edge i behållaren för att vara värd för filsystemet.

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>Visa registreringsbegränsningar per användare <!-- 1634444 -->
På felsökningsbladet kan du se vilka registreringsbegränsningar som gäller för varje användare.

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Konfigurera en MSI-mobilapp med automatisk uppdatering<!-- 1740840 -->
Du kan konfigurera en känd MSI-mobilapp med automatisk uppdatering för att ignorera versionskontrollen. Den här funktionen är användbar för att undvika konkurrenstillstånd. Det kan exempelvis ske när appen uppdateras automatiskt av apputvecklaren och även uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket kan skapa en konflikt.

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Tillägg till efterlevnadsprinciper för inställningar för systemsäkerhet för Windows 10 och senare <!--1704133 -->

Tillägg till efterlevnadsprinciper för Windows 10 blir tillgängliga, däribland krav på brandvägg och Windows Defender Antivirus.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inklusive och exklusive apptilldelning baserat på grupperna för Android Enterprise <!-- 1813081 -->
Under apptilldelning och när du har valt tilldelningstyp stöder Android Enterprise (tidigare Android for Work) funktioner för undantag.


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Relaterade uppsättningar applicenser som stöds i Intune <!-- 1864117 -->
Intune i Azure-portalen stöder relaterade uppsättningar med applicenser som ett enskilt appobjekt i användargränssnittet. Dessutom konsolideras alla offlinelicensierade appar från Microsoft Store för företag till en enda appinmatning och eventuella distributionsuppgifter från de enskilda paketen migreras över till den enda inmatningen. Om du vill se relaterade uppsättningar applicenser i Azure-portalen väljer du **Applicenser** på bladet **Mobilappar**.

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nya alternativ för användarautentisering för Apple-massregistrering <!-- 747625 -->
Intune ger dig möjlighet att autentisera enheter med hjälp av företagsportalappen för följande registreringsmetoder:

- Apples DEP (Device Enrollment Program)
- Apple School Manager
- Registrera Apple Configurator

När du använder alternativet Företagsportalen, kan Azure Active Directory-multifaktorautentisering tillämpas utan att blockera dessa registreringsmetoder.

När du använder alternativet Företagsportalen, hoppar Intune över användarautentisering i iOS-installationsassistenten för registrering av användartillhörighet. Detta innebär att enheten först registreras som en användarlös enhet och därför inte tar emot konfigurationer eller principer från användargrupper. Den tar bara emot konfigurationer och principer för enhetsgrupper. Intune kommer dock automatiskt att installera företagsportalappen på enheten. Den första användaren som startar och loggar in på företagsportalappen kommer att associeras med enheten i Intune. Användaren får då konfigurationer och principer för sina användargrupper. Användarassociationen kan inte ändras utan omregistrering.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune-stöd för flera Apple DEP/Apple School Manager-konton<!-- 747685 -->
Intune stöder registrering av enheter från upp till 100 olika Apple-program för enhetsregistrering (DEP) eller Apple School Manager-konton. Varje token som har överförts kan hanteras separat för registreringsprofiler och- enheter. En annan profil kan tilldelas automatiskt per DEP/School Manager-token som har överförts. Om flera School Manager-token har överförs, kan bara en åt gången delas med Microsoft School-datasynkronisering.

Efter migreringen fungerar inte beta-Graph API:er och publicerade skript för att hantera Apple DEP eller ASM över Graph längre. Nya beta-Graph API:er är under utveckling och kommer att släppas efter migreringen.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>Välj enhetskategorier med hjälp av inställningarna för åtkomst till arbete eller skola <!-- 1058963 -->
Om du har aktiverat [mappning av enhetsgrupp](https://docs.microsoft.com/intune/device-group-mapping), uppmanas Windows 10-användare att välja en enhetskategori efter registreringen via knappen **Anslut** i **Inställningar** > **Konton** > **Åtkomst till arbete eller skola** eller under välkomstprogrammet.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Ange mål för efterlevnadsprinciper för enheter i enhetsgrupperna <!--1307012 -->

Du kommer att kunna ange mål för efterlevnadsprinciper för användare i användargrupperna. Du kommer att kunna ange mål för efterlevnadsprinciper för enheter i användargrupperna.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows Information Protection (PIA)-krypterad data i Windows-sökresultat <!-- 1469193 -->

En ny inställning i principen för Windows Information Protection (PIA) gör att du kan kontrollera om PIA-krypterade data ingår i Windows-sökresultaten.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Fjärrutskrift via ett säkert nätverk <!-- 1709994  -->
PrinterOn:s trådlösa mobila lösningar gör att användare via fjärranslutning kan skriva ut var och när som helst via ett säkert nätverk. PrinterOn kan integreras med Intune APP SDK för både iOS och Android. Du kommer att kunna ange mål för appskyddsprinciper för den här appen via bladet Intune **Appskyddsprinciper** i administrationskonsolen. Användarna kommer att kunna ladda ner appen PrinterOn for Microsoft via Play Store eller iTunes för att använda i sina Intune-ekosystem.



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>Microsoft Graph API för Intune – allmän tillgänglighet <!-- 1833289 -->
Intune API:er i Microsoft Graph ger programmatisk åtkomst till data och metoder för att automatisera administrativa åtgärder för Intune-tjänsten.  Med **Allmän tillgänglighet** kommer dessa API:er, kunder, partner och utvecklare att kunna utnyttja API:erna för att integrera med interna eller externa lösningar som gäller för eller som kräver stöd för Intune eller andra Microsoft-tjänster som är tillgängliga via Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Appskyddsprinciper  <!-- 679615 -->
Intunes appskyddsprinciper ger dig möjligheten att skapa globala standardprinciper för att snabbt aktivera skydd för alla användare i hela klientorganisationen.

### <a name="new-ios-device-action------1244701---"></a>Ny iOS-enhetsåtgärd   <!-- 1244701 -->
Du kan stänga av iOS 10.3-övervakade enheter. Den här åtgärden stänger av enheten omedelbart utan varning till slutanvändaren. Åtgärden **stäng ner (endast övervakat)** finns i enhetsegenskaperna när du väljer en enhet i arbetsbelastningen **enhet**.

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune erbjuder åtgärden flytta kontot <!-- 1573558, 1579830 -->
**Flytta kontot** migrerar en klient från en Azure-skalenhet (ASU) till en annan. **Flytta kontot** kan användas för både kundinitierade scenarier, när du anropar Intunes supportteam som begär det och det kan vara ett Microsoft-drivet scenario där Microsoft behöver göra justeringar i tjänsten i serverdelen. Vid **flytta kontot**, går klienten in i skrivskyddat läge (ROM). Tjänståtgärder som registrering, byta namn på enheter, uppdatering av efterlevnadsstatus misslyckas under ROM-perioden.

Ändringen löser problemet som uppstår när en app har tilldelats till flera grupper med olika avsikter.

Om du vill att din app ska vara tillgänglig i portalen för informationsanställda och företagsportalen innan lanseringen av versionen i november så har du två alternativ:

1. Ta bort tilldelningen **Ej tillämpligt** för din grupp.
2. Skapa en ny grupp som inte innehåller medlemmar med avsikten **Nödvändig och Tillgänglig** och tilldela gruppen som **Ej tillämpligt**.

Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

> [!Note]
> Efter utgivningen kommer du inte längre att kunna visa eller ändra apptilldelningar för hantering av mobilenheter (MDM) i den klassiska Intune-konsolen. Du kan dock använda Azure-konsolen eller Intune Graph API för att utföra dina apptilldelningar.

### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurera PIN-kod för en iOS-app <!-- 1586774 -->
Du kommer snart att kunna kräva en PIN-kod för iOS-appar. Du kan konfigurera kravet på PIN-kod och förfallodatum i dagar via Azure Portal. När kravet är gäller måste en användare konfigurera och använda en ny PIN-kod innan de får åtkomst till en iOS-app. Endast iOS-appar som har appskydd aktiverat med Intune App SDK har stöd för den här funktionen.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866-->

Vi kommer att släppa en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen medför en komplett visuell uppfräschning, vilket omfattar ett modernare utseende med bättre användbarhet och tillgänglighet. Alla befintliga funktioner i företagsportalen för iOS kommer att finnas kvar.

Vi har en förhandsversion av den uppdaterade appen Företagsportal för iOS som är tillgänglig via Apple TestFlight-programmet, som du kan använda och lämna feedback på. Registrera dig på https://aka.ms/intune_ios_cp_testflight för att få åtkomst till TestFlight. 

![marknadsföringsbilder för den nya ios-appen Företagsportal](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Appskydd i Intune och Citrix MDX-utvecklingsverktyg <!-- 709185 -->
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Det gör det möjligt att hantera appar med Intunes appskyddsprincip samtidigt som du använder Citrix mVPN-teknik.

Du kan hitta ett kodcentrallager som innehåller Intune Apphanteringsverktyg och Intune App SDK för iOS och Android, som integreras med Citrix MDX mVPN-teknik.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Omdirigera macOS-användare till den nya företagsportalappen <!--1380728-->   
När en slutanvändare loggar in på företagsportalens webbplats för att registrera sin macOS-enhet dirigeras de för att ladda ned den nya företagsportalappen för macOS och på så sätt slutföra processen. Det inträffar för macOS-enheter som använder OS X El Capitan 10.11 eller senare. 

<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Intune Managed Browser har stöd för iOS och Android <!-- 1374196 -->
Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare. Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändare med Android-enheter ett vänligt felmeddelande med en åtgärd: ”You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)



## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.



### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


