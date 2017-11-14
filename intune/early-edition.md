---
title: "Tidig utgåva"
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f7cc595655950ef1bf2586e939b6f02e270e7afc
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---november-2017"></a>The Early Edition för Microsoft Intune – November 2017

Den **tidiga utgåvan** innehåller en lista med funktioner i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte denna information med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
>Följande ändringar är under utveckling för Intune. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal


### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Tilldela Office 365-mobilappar till iOS och Android-enheter med den inbyggda apptypen <!-- 1332318 -->
Den **inbyggda** apptypen gör det enklare att skapa och tilldela Office 365-appar till iOS- och Android-enheter som du hanterar. De här apparna inkluderar 365-appar som Word, Excel, PowerPoint och OneDrive. Du kan tilldela specifika appar till apptypen och redigera konfigurationen för appinformationen.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Stöd för enkel inloggning (SSO) på iOS <!-- 1333645 -->  
Du kommer att kunna använda enkel inloggning för iOS-användare. iOS-appar som är kodade för att leta efter användares autentiseringsuppgifter i nyttolasten för enkel inloggning fungerar med den här uppdateringen av nyttolastkonfigurationen. Du kan även använda UPN och Intune-enhets-ID för att konfigurera huvudnamn och sfär.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API för appinventering för iOS 11 för mobil hotidentifiering <!-- 1391759 -->
Intune samlar in information om appinventering från både personliga och företagsägda enheter och gör den tillgänglig för leverantörer av mobil hotidentifiering (MTD) att hämta, till exempel Lookout for Work. Du kommer att kunna samla in appinventering från användare av enheter med iOS 11+.

**Appinventering**  
Inventeringar från både företagsägda iOS 11+ och personligt ägda enheter skickas till MTD-leverantören. Data i appinventeringen omfattar:

 - App-ID
 - Appversion
 - Kort appversion
 - Appnamn
 - Storlek på appsamling
 - Dynamisk appstorlek
 - Om appen har verifierats eller inte
 - Om appen är hanterad eller inte

### <a name="audit-updates----1412961---"></a>Granska uppdateringar <!-- 1412961 -->  
Intune-granskning tillhandahåller en post med förändringsåtgärder relaterade till Intune.  Alla åtgärder för att skapa, uppdatera och ta bort, samt fjärruppgifter, sparas och lagras i ett år.  Azure Portal visar granskningsdata i varje arbetsbelastning för de senaste 30 dagarna. Det går även att filtrera bland dessa data.  En motsvarande Graph API gör det möjligt att hämta granskningsdata som lagrats under det senaste året. 

Granskning hittas under gruppen **ÖVERVAKA**. Det finns ett menyalternativ för **Granskningsloggar** för varje arbetsbelastning.   

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Textprotokollet som tillåts från hanterade appar <!-- 1414050  -->
Appar som hanteras av Intune App SDK kommer att kunna skicka SMS-meddelanden.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Starta om en iOS-enhet via en fjärranslutning (endast övervakade) <!-- 1424595 -->
Du kommer att kunna få en övervakad iOS 10.3 +-enhet att starta om med en enhetsåtgärd. Mer information om hur du använder åtgärden för omstart av enhet finns i [Starta om enheter med Intune med en fjärråtgärd](device-restart.md).

> [!Note]  
> Det här kommandot kräver en övervakad enhet och behörighet till **Enhetslås**. Enheten startas om direkt. iOS-enheter låsta med lösenord kommer inte återansluta till ett Wi-Fi-nätverk efter omstarten. Efter omstart kanske de inte kan kommunicera med servern.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Fjärrlåsa hanterade macOS-enheter med Intune <!-- 1437691 -->
Du kommer att kunna låsa en förlorad macOS-enhet och ange en PIN-kod för återställning på 6 siffror. När enheten är låst visar bladet **Enhetsöversikt** PIN-koden tills en annan enhetsåtgärd skickas.

Mer information finns i [Fjärrlåsa hanterade enheter med Intune](device-remote-lock.md).

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings------1455974-----"></a>Inställningar för rapporteringsfrekvens för Windows Defender Avancerat skydd <!--- 1455974  --->
Tjänsten Windows Defender Avancerat skydd (WDATP) låter administratörer hantera rapporteringsfrekvensen för hanterade enheter. Med det nya alternativet **Skicka frekvensvärde för telemetrirapportering** samlar WDATP in data och utvärderar risker oftare. Standardvärdet för rapporteringsfrekvensen optimerar hastighet och prestanda. Att öka frekvensen för rapportering kan vara användbart för högriskenheter. Den här inställningen finns i profilen **Windows Defender ATP** i **Enhetskonfigurationer**.

### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Konfliktlösning för tilldelning har ändrats för iOS Store-appar<!-- 1480316 -->
Slutanvändare kan uppleva att tillgängligheten för iOS Store-appar har ändrats. En app som har tilldelats till två grupper med en konflikt mellan **Nödvändig och Tillgänglig** och **Ej tillämpligt** ger för närvarande prioritet till **Nödvändig och Tillgänglig**. I och med ändringen ger en app med den här konflikten prioritet till **Ej tillämpligt** istället.

Ändringen löser problemet som uppstår när en app har tilldelats till flera grupper med olika avsikter.

Om du vill att din app ska vara tillgänglig i portalen för informationsanställda och företagsportalen innan lanseringen av versionen i november så har du två alternativ:

1. Ta bort tilldelningen **Ej tillämpligt** för din grupp.
2. Skapa en ny grupp som inte innehåller medlemmar med avsikten **Nödvändig och Tillgänglig** och tilldela gruppen som **Ej tillämpligt**.

Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

> [!Note]
> Efter utgivningen kommer du inte längre att kunna visa eller ändra apptilldelningar för hantering av mobilenheter (MDM) i den klassiska Intune-konsolen. Du kan dock använda Azure-konsolen eller Intune Graph API för att utföra dina apptilldelningar.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Hantera Android for Work-enheter oberoende av Android-enheter <!-- 1490731 -->
Intune stöder registrering av hantering för Android for Work-enheter oberoende av Android-plattformen. De här inställningarna hanteras under **Enhetsregistrering** > **Registreringsbegränsningar** > **Begränsningar för enhetstyper**. (De fanns tidigare **Enhetsregistrering** > **Android for Work-registrering** > **Registreringsinställningar för Android for Work**.)

Som standard är dina Android for Work-enhetsinställningar samma som dina inställningar för Android-enheter. Men när du har ändrat dina Android for Work-inställningar kommer det här inte längre att vara fallet.
 
Om du blockerar registrering av personligt ägda Android for Work-enheter så kan endast företagsägda Android-enheter att registrera Android for Work.

Tänk på följande när du konfigurerar nya inställningar:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Om du aldrig tidigare har publicerat Android for Work-registrering
Den nya Android for Work-plattformen blockeras av standardbegränsningarna för enhetstyper. När du har publicerat funktionen kan du tillåta enheter att registreras med Android for Work. För att göra detta ändrar du på standardvärdena eller skapar en ny begränsning för enhetstyp för att ersätta begränsningen för enhetstyp som är standard.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Om du har publicerat Android for Work-registrering
Om du har publicerat tidigare så beror din situation på de inställningar du väljer:

| Inställningar | Statusen för Android for Work under begränsningar för enhetstyper | Anteckningar |
| --- | --- | --- |
| **Hantera alla enheter som Android** | Blockerad | Alla Android-enheter måste registreras utan Android for Work. |
| **Hantera enheter som stöds som Android for Work** | Tillåts | Alla Android-enheter som har stöd för Android for Work måste registreras med Android for Work. |
| **Hantera endast enheter som stöds i de här grupperna som Android for Work för användare** | Blockerad | En separat princip för begränsningar för enhetstyper skapades för att åsidosätta standardinställningen. Den här principen definierar de grupper som du tidigare valde för att tillåta Android for Work-registrering. Användare i de valda grupperna fortsätter att kunna registrera sina Android for Work-enheter. Alla andra användare är begränsade från att registrera med Android for Work. |

I samtliga fall bevaras din avsedda regler. Ingen åtgärd krävs från din sida för att underhålla den globala begränsningen eller per grupp-begränsningen för Android for Work i din miljö.

De här ändringarna börjar publiceras med novemberuppdateringen, men det kan ta tid innan de appliceras på ditt konto. Du får ett bekräftelsemeddelande i Office 365-portalen när ändringarna är applicerade på ditt konto.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Stöd för flera anslutningsprogram för registreringstjänster för nätverksenheter (NDES) <!-- 1528104 -->
Registreringstjänsten för nätverksenheter (NDES) gör det möjligt för mobilenheter som körs utan domänautentiseringsuppgifter att hämta certifikat baserade på SCEP-tillägg (Simple Certificate Enrollment Protocol). Med den här uppdateringen stöds flera NDES-anslutningsprogram.

### <a name="new-scep-profile-details-supported----1559808---"></a>Ny SCEP-profilinformation som stöds <!-- 1559808 -->
Administratörer kommer att kunna ange fler inställningar när de skapar en SCEP-profil på Windows, iOS, macOS och Android-plattformar.  Administratörer kan ange IMEI, serienummer eller eget namn inklusive e-post i ämnesnamnets format.

### <a name="configure-an-ios-app-pin----1586774---"></a>Konfigurera PIN-kod för en iOS-app <!-- 1586774 -->
Du kommer snart att kunna kräva en PIN-kod för iOS-appar. Du kan konfigurera kravet på PIN-kod och förfallodatum i dagar via Azure Portal. När kravet är gäller måste en användare konfigurera och använda en ny PIN-kod innan de får åtkomst till en iOS-app. Endast iOS-appar som har appskydd aktiverat med Intune App SDK har stöd för den här funktionen.

### <a name="retain-data-during-a-factory-reset-----1588489---"></a>Behåll data under en fabriksåterställning <!-- 1588489 -->
Vi lägger till stöd för en ny funktion för fabriksåterställning i Windows. Administratörer kan nu ange om enhetsregistrering och andra etablerade data ska finnas kvar på en enhet efter en fabriksåterställning utförts. 
 
Följande data behålls efter en fabriksåterställning:
- Användarkonton kopplade till enheten
- Enhetstillstånd (domänanslutning, AADJ)
- MDM-registrering
- Installerade OEM-appar (store och Win32-appar)
- Användarprofil
- Användardata utanför användarprofilen
- Automatisk inloggning för användare
 
Följande data bevaras inte:
- Användarfiler
- Användarinstallerade appar (store och Win32-appar)
- Enhetsinställningar som inte är standard 

### <a name="app-install-status-report-now-a-bar-chart----1249446---"></a>Statusrapporten för appinstallation är nu ett stapeldiagram <!-- 1249446 -->  
Rapporten **Status för appinstallation** är tillgänglig för varje app via listan **Appar** i arbetsbelastningen **Mobilappar** kommer snart att renderas som ett stapeldiagram.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Lägg till ”Hitta min iPhone” för personliga enheter <!--1427287-->
Du kommer att kunna se om iOS-enheter som har Aktiveringslås aktiverat. Den här funktionen kunde tidigare hittas i den klassiska Intune-portalen.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Grupptilldelade registreringsbegränsningar <!-- 747598 -->
Som Intune-administratör kommer du att kunna skapa anpassade registreringsbegränsningar för enhetstyp och enhetsgräns för användargrupper.
 
Du kan skapa upp till 25 instanser av varje begränsningstyp med Intune Azure Portal som du sedan kan tilldela till användargrupper. Grupptilldelade begränsningar åsidosätter standardbegränsningarna.
 
Alla instanser av en begränsningstyp lagras i ett strikt sorterad lista. Den här ordningen definierar prioritetsvärden för konfliktlösning. En användare som påverkas av mer än en begränsningsinstans begränsas endast av instansen med det högsta prioritetsvärdet. Du kan ändra prioriteten för en viss instans genom att dra den till en annan plats i listan. 
 
Den här funktionen kommer att lanseras med migreringen av Android for Work-inställningar från registreringsmenyn för Android for Work till menyn för registreringsbegränsningar. Den här migreringen kan ta flera dagar. Ditt konto kan uppgraderas för andra delar av novemberversionen innan grupptilldelning aktiveras för registreringsbegränsningar.

### <a name="windows-10-update-ring-assignments-are-displayed----1621837---"></a>Tilldelningar för Windows 10:s uppdateringstestgrupper visas <!-- 1621837 -->
Du kan se alla tilldelningar till Windows 10:s uppdateringstestgrupper för användaren som du visar när du **felsöker**.  



<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory-webbplatser kan kräva appen Intune Managed Browser och ha stöd för enkel inloggning för Managed Browser (allmänt tillgänglig förhandsversion) <!-- 710595 -->   
Med Azure Active Directory (Azure AD) kan du begränsa åtkomst till webbplatser på mobila enheter till appen Intune Managed Browser. I Managed Browser förblir webbplatsdata säkra och separata från slutanvändarens personliga data. Dessutom stöder Managed Browser funktioner för enkel inloggning för webbplatser som stöds av Azure AD. När du loggar in på Managed Browser eller använder Managed Browser på en enhet med en annan app som hanteras av Intune, tillåts Managed Browser att få åtkomst till företagswebbplatser som skyddas av Azure AD utan att användaren måste ange sina autentiseringsuppgifter. Den här funktionen gäller för webbplatser som Outlook Web Access (OWA) och SharePoint Online, samt andra företags webbplatser som resurser i intranätet som nås via Azure App Proxy.

### <a name="troubleshoot-enrollment-issues------746324----"></a>Felsöka problem med registreringen  <!--- 746324 --->  
Felsökningsarbetsytan visar problem med användarregistreringen. Information om problemet och förslagna lösningar kan hjälpa administratörer och medarbetare på supportavdelningen att felsöka problem. Vissa problem med registreringen inte fångas upp, och vissa fel kanske inte har några reparationsförslag.


















<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Stöd för uppgraderingsprincip i Windows 10-utgåvan <!-- 903672(archived), 1119689 -->  
Du kommer att kunna skapa en uppgraderingsprincip för Windows 10-utgåvan som uppgraderar Windows 10-enheter till Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education och Windows 10 Professional Education N. Mer information om Windows 10-uppgraderingar finns i [Så här konfigurerar du Windows 10-uppgraderingar](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Android for Work-stöd för Lookout <!-- 1087312 -->   
Intune-anslutningsprogrammet med Lookout stöder Android for Work-enheter när du använder Lookout for Work-appen. Du kan distribuera Lookout-appen innanför eller utanför behållaren.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Appskydd i Intune och Citrix MDX-utvecklingsverktyg <!-- 709185 -->
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Det gör det möjligt att hantera appar med Intunes appskyddsprincip samtidigt som du använder Citrix mVPN-teknik.

Du kan hitta ett kodcentrallager som innehåller Intune Apphanteringsverktyg och Intune App SDK för iOS och Android, som integreras med Citrix MDX mVPN-teknik.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram <!-- 676614 -->   
Du kan ha fler roller för klientåtkomstservrar (CAS) för lokala Exchange-anslutningsprogram. Om de viktigaste klientåtkomstservrarna misslyckas till exempel, så tar Exchange-anslutningsprogrammet emot en fråga för att gå över till andra klientåtkomstservrar. Den här funktionen ser till att tjänsten inte avbryts.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Hanteringspaket för Exchange-anslutningsprogram i System Center Operations Manager <!-- 885457 -->   
Med System Center Operations Manager-hanteringspaketet för Exchange-anslutningsprogrammet kommer du att kunna tolka Exchange-anslutningsloggarna. Det här hanteringspaketet ger dig flera olika sätt att övervaka Intune när du behöver felsöka problem.





## <a name="intune-apps"></a>Intune-appar

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Hjälper dina användare att hjälpa sig själva med företagsportalsappen för Android <!---1573324, 1573150, 1558616, 1564878--->
Företagsportalappen för Android lägger till anvisningar för slutanvändare för att hjälpa dem att förstå och, om möjligt, själva lösa nya problem. 

- Ett nytt meddelande visas som förklarar att en efterlevnadsprincip för kryptering har distribuerats, men att [enhetstillverkaren inte krypterar enheten](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android) enligt [Googles rekommenderade riktlinjer](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean).
- Slutanvändare dirigeras till (Azure Active Directory-portalen) [https://account.activedirectory.windowsazure.com/r/#/profile] för att ta bort en enhet om de har nått det högsta antalet enheter som de tillåts ha. 
- Slutanvändare rekommenderas åtgärder att vidta för att hjälpa dem att [åtgärda aktiveringsfel på Samsung KNOX-enheter](https://go.microsoft.com/fwlink/?linkid=859718) eller för att [inaktivera energisparläge](/intune-user-help/power-saving-mode-android). Om ingen av dessa lösningar löser problemet tillhandahåller vi en förklaring om hur du [submit logs to Microsoft](/intune-user-help/send-logs-to-microsoft-ios) (skickar loggar till Microsoft). 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>En ny funktion, ”Lös”, är tillgänglig för Android-enheter <!---1583480--->
Företagsportalappen för Android presenterar en ”Lös”-åtgärd på sidan _Uppdatera enhetsinställningar_. Det här alternativet tar slutanvändaren direkt till inställningen som gör att enheten är icke-kompatibel. Företagsportalappen för Android stöder för närvarande den här åtgärden för inställningarna [enhetens lösenkod](/intune-user-help/set-your-pin-or-password-android), [enhetskryptering](/intune-user-help/encrypt-your-device-android), [USB-felsökning](/intune-user-help/you-need-to-turn-off-usb-debugging-android), och [Okända källor](/intune-user-help/you-need-to-turn-off-unknown-sources-android). 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Omdirigera macOS-användare till vår nya företagsportalapp <!--1380728-->   
När en slutanvändare loggar in på företagsportalens webbplats för att registrera sin macOS-enhet dirigeras de för att ladda ned den nya företagsportalappen för macOS och på så sätt slutföra processen. Det inträffar för macOS-enheter som använder OS X El Capitan 10.11 eller senare. 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Program som är tillgängliga med eller utan registrering kan nu installeras utan att först uppmanas till registrering. <!-- 1334712 -->
Företagsprogram som har gjorts tillgängliga med eller utan registreringen i Androids företagsportalapp kan installeras utan någon uppmaning att registrera.


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Intune Managed Browser har stöd för iOS och Android <!-- 1374196 -->
Från och med oktober 2017 stöder Intune Managed Browser-appen på Android-appen endast enheter som körs på Android 4.4 och senare. Intune Managed Browser-appen på iOS har endast stöd för enheter som körs på iOS 9.0 eller senare. Tidigare versioner av Android och iOS kommer att kunna fortsätta att använda Managed Browser, men kommer inte att kunna installera nya versioner av appen och kanske inte använda alla funktioner. Vi rekommenderar att du uppdaterar de här enheterna till en version av operativsystemet som stöds.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Förbättrat felmeddelande när en användare når det högsta antalet enheter som tillåts för registrering <!-- 1270370 -->
I stället för ett allmänt felmeddelande ser slutanvändarna ett vänligt felmeddelande med en åtgärd: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin.” (Du har registrerat det högsta antalet enheter som IT-administratören tillåter. Ta bort en registrerad enhet eller be IT-administratören om hjälp.)




## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.




### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
