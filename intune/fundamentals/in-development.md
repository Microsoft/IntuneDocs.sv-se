---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182924"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Under utveckling för Microsoft Intune – november 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Förutom informationen på den här sidan:

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion går in i produktion, oavsett om det är en för hands version eller är allmänt tillgänglig, kommer funktions beskrivningen att flyttas från den här sidan till [vad som är nytt](whats-new.md).
- Den här sidan och sidan [Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [Microsoft 365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!NOTE]
> Den här sidan visar våra aktuella förväntningar om Intune-funktioner i en framtida version. Datum och enskilda funktioner kan ändras. Den här sidan beskriver inte alla funktioner som utvecklas.

**RSS-feed**: Få reda på när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>S/MIME-stöd för Microsoft Outlook Mobile <!-- 2669398  -->
Intune har stöd för att leverera S/MIME-signering och krypterings certifikat som kan användas med Outlook Mobile på iOS och Android. Relaterad information finns i [e-postinställningar för iOS-enheter](~/configuration/email-settings-ios.md) och [e-postinställningar för Android-enheter](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Stöd för anpassade inställningar för macOS-program <!-- 4736278  -->
Intune stöder anpassade inställningar, så att du kan lägga till vissa nycklar och värden i en befintlig egenskaps lista för inställningar (. plist) för att konfigurera macOS-appar och enheten. Alla appar har inte stöd för hanterade inställningar, och i vissa fall kan endast vissa inställningar hanteras. Inställningarna distribueras endast via enhets kanalen. Du bör bara ladda upp filer för egenskaps listor eller XML-filer som är riktade mot enhets kanal inställningar.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Tilldelnings typ värde i Windows Företagsportal <!-- 5459950  -->
Sidan **installerade appar** i Windows företagsportal-appen kommer att uppdateras. Kolumnen **tilldelnings typ** på sidan **installerade appar** har uppdaterats så att den kallas "krävs av din organisation". Möjliga värden är **Ja** eller **Nej** för att ange nödvändiga eller tillgängliga appar. Den här ändringen görs som svar på viss förvirring i slutanvändaren. Mer information om Windows företagsportal finns i [Så här konfigurerar du appen för Microsoft Intune-företagsportal](~/apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Köra Win32-appar på Windows 10 S-mode-enheter <!-- 3747604  --> 
Du kan installera och köra Win32-appar på enheter som hanteras i Windows 10 S-läge. Skapa en eller flera kompletterande principer för S-läge med hjälp av PowerShell-verktygen för Windows Defender-WDAC (program kontroll). Använd Device Guard-signing Portal för att signera tilläggs principerna. Sedan laddar du upp och distribuerar principerna via Intune. 

I Intune hittar du den här funktionen genom att välja **klient program**  > **Windows 10 S kompletterande principer**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Ange appens tillgänglighet baserat på datum och tid <!-- 3510685  -->
Som administratör kan du konfigurera start tiden och tids gränsen för en obligatorisk app. Vid start tiden laddar Intune Management-tillägget ned appens innehåll och cachelagrar det. Appen kommer att installeras vid tids gränsen. För tillgängliga appar kommer start tiden att diktera när appen visas i Företagsportal. 

Ange appens tillgänglighet baserat på datum och tid:

1. I Intune väljer du **Klientappar** > **Appar**. 
1. Välj en app i listan eller Lägg till en ny genom att välja **Lägg till**. 
1. Från bladet app väljer du **tilldelningar** > **Lägg till grupp**. 
1. Ange **tilldelnings typen** till **obligatorisk** och välj sedan **inkluderade grupper**. 
1. Ställ in **gör den här appen obligatorisk för alla användare** till **Ja**. 
1. Välj **Redigera** för att ändra **slutanvändarens upplevelse** alternativ. 
1. På bladet **slut användar upplevelse** anger du den **tillgängliga tiden för program vara** efter behov. 

Du hittar mer information i [Lägg till appar i Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Kräv att Win32-appar startas om <!-- 3136567  -->
Du kan behöva en Win32-app för att starta om efter en lyckad installation. Du kan välja hur lång tid (Grace-perioden) som ska starta innan omstarten.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Visa meddelanden för Företagsportal-appen i Windows <!-- 1808082  -->
Vi uppdaterar Företagsportal-appen på Windows-enheter för att visa popup-meddelanden till användare, även när programmet stängs. Uppdateringen visar endast meddelanden för tillgängliga appar när installations statusen är slutförd eller inte fungerar. Företagsportal appen visar inte meddelanden för nödvändiga program.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Visa installations status meddelanden för appen Företagsportal <!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.
- Appen har installerats men kräver en omstart.
- Appen håller på att installeras men kräver en omstart för att fortsätta.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Konfigurera program meddelande innehåll för organisations konton <!-- 2576686 -->
Med Intune-appen på Android-och iOS-enheter kan du styra appens meddelande innehåll för organisations konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Använda PKCS-certifikat med Wi-Fi-profiler på enheter med Windows 10 och senare <!-- 3246388  -->
För närvarande kan du autentisera Windows Wi-Fi-profiler med SCEP-certifikat (**enhets konfiguration** > **profiler** > **Skapa profil** > **Windows 10 och senare** för Platform > **Wi-Fi** för profil typ > **Enterprise** > **EAP-typ**). Du kommer att kunna använda PKCS-certifikat med dina Windows Wi-Fi-profiler. Med den här funktionen kan användarna autentisera Wi-Fi-profiler med hjälp av nya eller befintliga PKCS-certifikat profiler i din klient organisation. 

Mer information om Wi-Fi-profiler finns i [lägga till Wi-Fi-inställningar för enheter med Windows 10 och senare i Intune](../configuration/wi-fi-settings-windows.md).

Gäller för:
- Windows 10 och senare

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Nya ExchangeActiveSync-inställningar när du skapar en profil för e-postenhets konfiguration på iOS-enheter <!-- 4892824  --> 
På iOS/iPad-enheter kan du konfigurera e-postanslutning i en enhets konfigurations profil (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS/iPad** för Platform > **e-post** för profil typ). 

Det kommer att finnas nya ExchangeActiveSync-inställningar tillgängliga, inklusive:
- Välj vilka tjänster som ska synkroniseras (eller blockera synkronisering), till exempel e-post, kalender och kontakter.
- Tillåt (eller blockera) användare att ändra synkroniseringsinställningarna för dessa tjänster på sina enheter. 

Om du vill se de aktuella inställningarna går du till [Inställningar för e-postprofil för iOS-enheter i Intune](../configuration/email-settings-ios.md).

Gäller för:
- iOS 13.0 och senare
- iPadOS 13.0 och senare

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Hindra användare från att lägga till personliga Google-konton till Android Enterprise-enhetens ägare och dedikerade enheter <!-- 5353228  -->
Du kan förhindra att användare skapar personliga Google-konton på Android Enterprise-enhetens ägare och dedikerade enheter (**enhets konfiguration** > **profiler** > **Skapa profil** > **Android Enterprise** för plattforms > **enhets ägaren bara > enhets begränsningar** för profil typ > **användare och konton inställningar**).

Om du vill se de aktuella inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-enhetsägare
- Dedikerade Android Enterprise-enheter

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>Loggning på Server sidan för Siri-kommandon tas bort i profilen iOS-enhets begränsningar <!-- 5468501  -->
På iOS-enheter kan du skapa en profil för enhets begränsningar som konfigurerar loggning på Server sidan för Siri-kommandon (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS/iPad** för plattform > **Enhets begränsningar** för profil typ > **inbyggda appar**). Inställningen på **Server sidans loggning för Siri-kommandon** kommer att tas bort.

Den här inställningen tas bort från Intunes administratörs konsol. Den här inställningen har ingen påverkan på enheten trots att befintliga principer som har den här inställningen konfigurerad kommer att fortsätta att visa inställningen. Om du vill ta bort inställningen från befintliga principer går du till principen, gör en mindre redigering, sparar den och principen kommer att uppdateras.

Om du vill se de inställningar som du kan konfigurera går du till [Inställningar för iOS- och IPadOS-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-ios.md).

Gäller för:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Enhetshantering

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Redigera enhets namn värde för autopilot-enheter<!-- 2640074  -->
Du kan redigera enhets namn svärdet för Azure AD-anslutna autopilot-enheter. Det gör du genom att gå till **Intune** > **enhets registrering** > **Windows-registrering** > **Windows autopilot** > **enheter** > Välj enhet > ändra värdet för **enhets namn** i den högra rutan > **Spara**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Redigera gruppens märkes värde för autopilot-enheter<!-- 4816775 -->
Du kan redigera **grupp märkes** värdet för autopilot-enheter:

1. Välj **Intune**  > **enhets registrering**  > **Windows-registrering**  > **Windows autopilot** - > **enheter**.
1. Välj enhet.
1. Ändra värdet för **grupp tag gen** i rutan till höger.
1. Välj **Spara**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Mål användar grupper för macOS för att kräva JAMF-hantering <!-- 4061739 -->
Du kan rikta in dig på specifika grupper av användare så att de kräver att deras macOS-enheter hanteras av JAMF. Den här anpassningen gör att du kan använda JAMF-kompatibilitet för en delmängd av macOS-enheter medan andra enheter fortsätter att hanteras av Intune. Med mål kan du också gradvis migrera användarnas enheter från ett MDM-system (Mobile Device Management) till en annan.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune-appar

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Förbättrad användning av macOS-registrering i Företagsportal <!-- 5074349  -->
Företagsportal för macOS-registreringen kommer att ha en enklare registrerings process som kommer att justeras mer nära med Företagsportal för registrerings upplevelsen för iOS. Enhets användare ser:  

* Ett slimmat användar gränssnitt.  
* En förbättrad registrerings check lista.  
* Tydligare instruktioner för hur du registrerar sina enheter.  
* Förbättrade fel söknings alternativ.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Förbättrad check lista design i Företagsportal app för Android<!-- 5550857  -->
Check lista för installationen i Företagsportal-appen för Android kommer att uppdateras med en lätt design och nya ikoner. Ändringarna justeras med de senaste uppdateringarna som gjorts i Företagsportal-appen för iOS.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Övervakning och fel sökning

### <a name="updated-support-experience-------5012398------"></a>Uppdaterad supportupplevelse   <!--  5012398    -->
Som en del av fortsatta förbättringar kommer vi att uppdatera support upplevelsen i konsolen för Intune.  Vi förbättrar sökningen och feedbacken i konsolen för vanliga problem och vi effektiviserar arbets flödet för att kontakta supporten.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Duplicera anpassade eller inbyggda roller <!-- 1081938 -->
Du kommer att kunna kopiera inbyggda och anpassade roller. Det gör du genom att gå till **Intune** > **roller** > **alla roller** > Välj en roll i listan > **dubblett**. Se till att ange ett nytt namn som är unikt.

<!-- ***********************************************-->

## <a name="security"></a>Säkerhet

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker-nyckel rotation     <!-- 2564951      -->
Du kan använda Intune för att rotera återställnings nycklar för BitLocker för hanterade enheter som kör Windows version 1909 eller senare. 

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).
