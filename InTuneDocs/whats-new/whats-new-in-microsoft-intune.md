---
title: "Vad är nytt | Microsoft Docs"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 053cf0a1b5d06496397b36cbd1a7ebdce420fed3
ms.openlocfilehash: 5158d58c32066ea720335a878fef87451542c195


---
# <a name="whats-new-in-microsoft-intune---january-2017"></a>Nyheter i Microsoft Intune – Januari 2017
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

<!--### Actions for non-compliance <!--730266
_Actions for non-compliance_ is a new feature of compliance policies that lets you take action on devices that are out of compliance. You can specify single or multiple actions and specify the time period at which those actions must occur. For example, you can notify users of non-compliant devices immediately after the devices become non-compliant through email, or you can block non-compliant devices from accessing corporate resources after a 3-day grace period via Conditional Access.-->

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Rapporter i konsolen för MAM utan registrering <!--677961-->
Nya rapporter för appskydd har lagts till för både registrerade enheter och enheter som inte har registrerats. Lär dig mer om hur du kan [övervaka hanteringsprinciper för mobilappar med Intune här](https://docs.microsoft.com/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

<!--### Conditional access for MAM with SharePoint Online <!--679339
You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint Online.  You can get started using Intune mobile app management in the Azure portal. Look for the __Conditional Access__ section in the __Settings__ blade which will include the option for SharePoint Online. This feature will ship separately from the rest of the service release. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Stöd för Android 7.1.1 <!--694397-->
Intune har nu fullständigt stöd för och hantering av Android 7.1.1.

### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Lös problemet med att iOS-enheterna är inaktiva eller att administratörskonsolen inte kan kommunicera med dem <!--unknown-->
När användarnas enheter förlorar kontakt med Intune kan du ge dem nya felsökningssteg för att hjälpa dem att återfå åtkomst till företagets resurser. Se [Enheterna är inaktiva eller så kan administratörskonsolen inte kommunicera med dem](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

## <a name="notices"></a>Meddelanden

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardvärde för hantering av Windows Desktop-enheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten.

Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

<!--### Company Portal for iOS links open inside the app <!--665954
Links inside of the Company Portal app for iOS, including those to documentation and apps, will open directly in the Company Portal app using an in-app view of Safari. This update will ship separately from the service update in January.-->

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning för hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny" ![Hamburgarmenyn på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar. Du kan hitta före- och efterbilder på [sidan med information om nyheter i Intune-appens användargränssnitt](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui#January_2017).

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Ny dokumentationen för appskyddsprinciper<!--583398-->
Vi har uppdaterat dokumentationen för administratörer och apputvecklare som vill aktivera appskyddsprinciper (kallas MAM-principer) i sina iOS- och Android-appar med Intune programhanteringsverktyg eller Intune App SDK.

Följande artiklar har uppdaterats:

* [Förbereda appar för hantering av mobilprogram med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Kom igång med Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Utvecklarhandbok för Intune App SDK för iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Följande artiklar har nya tillägg i dokumentbiblioteket:

* [Intune App SDK Cordova-insticksprogrammet](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Intune App SDK Xamarin-komponenten](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

<!--### Progress bar when launching the Company Portal on iOS <!--665978
The Company Portal for iOS is introducing a progress bar on the launch screen to provide the user with information about the loading processes that occur. There will be a phased rollout of the progress bar to replace the spinner. This means that some of your users will see the new progress bar while others will continue to see the spinner.-->

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Förloppsindikator när företagsportalappen startas i iOS <!--665978-->
Företagsportalen för iOS lanserar en förloppsindikator på startskärmen som ger användaren information om de inläsningsprocesser som sker. Det kommer att ske ett stegvist införande av förloppsindikatorn som ersätter rotationsrutan. Det innebär att vissa av användarna ser den nya förloppsindikatorn medan andra kommer att fortsätta se rotationsrutan.

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Vad är nytt i den offentliga förhandsversion av Intunes adminstratörsupplevelse på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Om du har frågor om tidslinjen för migrering av din klientorganisation, kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Du kan se vad som är nytt i Intunes förhandsversion i Azure [här](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Vad är nytt i förhandsversionen av Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Nyheter i företagsportalens gränssnitt](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Nyhetsarkiv](whats-new-archive.md)



<!--HONumber=Feb17_HO1-->


