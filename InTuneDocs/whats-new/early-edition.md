---
title: "Tidig utgåva | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>Den tidiga utgåvan för Microsoft Intune – Februari 2017

Den **tidiga utgåvan** innehåller en lista över funktioner som är planerade för kommande versioner av Microsoft Intune. Den här informationen omfattas av vårt sekretessavtal och tillhandahålls på ett ytterst begränsat sätt. Informationen kan komma att ändras. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta din Intune- eller PM-representant om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

> [!Note]
> Följande ändringar är under utveckling för Intune. Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
I början av februari kommer företagsportalwebbplatsen att anpassas med andra Microsoft-produkter och -tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny" ![Liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar. Du kan hitta före och efter-bilder som är tillgängliga på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!--713927-->
Från och med mars innehåller företagsportalen för Windows 10 en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar anpassade för användarens version av Windows 10 som hjälper användaren att utföra AAD-registrering (krävs för identifiering för funktioner för villkorlig åtkomst) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden bli tillgänglig från företagsportalens startsida och är frivillig. Användarna kan fortsätta att använda appen även om de inte slutför registreringen men appen kan då ha begränsad funktionalitet.

###

## <a name="notices"></a>Meddelanden

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>Gruppmigrering kräver inte några uppdateringar för grupper eller principer för iOS-enheter<!--898837-->
För varje Intune-enhetsgrupp som tilldelas i förväg av en profil för registrering av företagsenhet skapas en motsvarande dynamisk enhetsgrupp i AAD. Det görs baserat på namnet på profilen för registrering av företagsenhet under migreringen till Azure Active Directory-enhetsgrupper. Detta säkerställer att när enheter registreras kommer de automatiskt att grupperas och ta emot samma principer och appar som den ursprungliga Intune-gruppen.

När en klient startar migreringsprocessen för att gruppera och ange mål skapar Intune automatiskt en dynamisk AAD-grupp som motsvarar en Intune-grupp som är mål för en profil för registrering av företagsenheter. Om Intune-administratören tar bort Intune-målgruppen tas inte motsvarande dynamiska AAD-grupp bort. Gruppens medlemmar och den dynamiska frågan kommer att tas bort, men själva gruppen finns kvar tills IT-administratören tar bort den via AAD-portalen.

Och om IT-administratören ändrar vilken grupp Intune riktas mot av en profil för registrering av företagsenheter skapar Intune en ny dynamisk grupp som avspeglar den nya profiltilldelningen. Den nya dynamiska gruppen som har skapats för den gamla tilldelningen tas inte bort.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Ny MDM-serveradress för Windows-enheter <!--893007-->
Windows och Windows Phone-användare som försöker registrera en enhet misslyckas om de anger __manage.microsoft.com__ som MDM-serveradressen (om de uppmanas till det). MDM-serveradressen ändras från __manage.microsoft.com__ till __enrollment.manage.microsoft.com__. Meddela användarna att de ska använda adressen __enrollment.manage.microsoft.com__ som MDM-serveradress om de tillfrågas om den under registreringen av en Windows- eller och Windows Phone-enhet. Uppdateringen kräver att ett CNAME i DNS som omdirigerar __EnterpriseEnrollment.contoso.com__ till __manage.microsoft.com__ ersätts med ett CNAME i DNS som omdirigerar __EnterpriseEnrollment.contoso.com__ till __EnterpriseEnrollment-s.manage.microsoft.com__. Mer information om den här ändringen finns på [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.
* __Gränssnitt__: Knapparna Aktuella appar och Alla appar har uppdaterats på fliken. Sökknappen är nu flytande.
* __Navigering__: Alla appar visar en flikvy över Aktuella, Alla och Kategorier för att underlätta navigeringen.
* __Tjänst__: Flikarna Mina enheter och Kontakta IT har förbättrad läsbarhet.

Du kan hitta före och efter-bilder på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Koppla flera hanteringsverktyg till Windows Store för företag<!--926135-->
Om du använder fler än ett hanteringsverktyg för att distribuera Windows Store för affärsappar kunde du tidigare bara koppla ett av dem till Windows Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Offentlig förhandsversion av den nya Intune-adminstratörsupplevelsen på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Om du har frågor om tidslinjen för migrering av din klientorganisation, kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="february-2017"></a>Februari 2017

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Möjlighet att begränsa registrering av mobila enheter <!--747600, 795782-->
Intune lägger till nya registreringsbegränsningar som avgör vilka plattformar som mobila enheter ska kunna registrera. Intune skiljer mellan mobilplattformar som iOS, macOS, Android, Windows och Windows Mobile.

* Begränsningen av registrering av mobila enheter begränsar inte registreringen av datorklienter.  
* För iOS och Android finns det ytterligare ett alternativ för att blockera registrering av personligt ägda enheter.

Intune markerar alla nya enheter som personliga såvida inte IT-administratören vidtar åtgärder för att markera dem som företagsägda, vilket beskrivs i [den här artikeln](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

#### <a name="view-all-actions-on-managed-devices---677150--"></a>Visa alla åtgärder på hanterade enheter <!--677150-->
En ny rapport om __enhetsåtgärder__ visar vem som har utfört fjärråtgärder som fabriksåterställning på enheter, och dessutom visas status för åtgärden.

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>Icke-hanterade enheter kan komma åt tilldelade appar <!--664691-->
Som en del av designändringarna på företagsportalens webbplats ska iOS- och Android-användare kunna installera appar som har tilldelats dem som "tillgänglig utan registrering" på sina icke-hanterade enheter. Med sina Intune-autentiseringsuppgifter kan användare logga in på företagsportalens webbplats och se en lista över appar som tilldelats dem. App-paket för apparna som är "tillgängliga utan registrering" görs tillgängliga för hämtning via företagsportalens webbplats. Appar som kräver registrering för installation påverkas inte av den här ändringen, eftersom användarna uppmanas att registrera sina enheter om de vill installera apparna.

#### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.
Läs [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Lägga till en app i Intune).

#### <a name="display-device-categories---814654--"></a>Visa enhetskategorier <!--814654-->
Du kan nu visa enhetskategorin som en kolumn i listan över enheter. Du kan också redigera kategorin från avsnittet med egenskaper på bladet Enhetsegenskaper.

### <a name="january-2017"></a>Januari 2017

#### <a name="custom-app-categories---748805--"></a>Anpassade appkategorier <!--748805-->
Du kan nu skapa, redigera och tilldela kategorier för appar som du lägger till i Intune. Kategorier kan för närvarande kan bara anges på engelska.

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>Tilldela branschspecifika appar oavsett om enheterna har registrerats eller inte <!--748803-->
Du kan nu tilldela branschspecifika appar och appar från butiken till användare, oavsett om deras enheter är registrerade i Intune eller inte. Om användarens enhet inte har registrerats i Intune måste användaren gå till webbplatsen för företagsportalen för att installera den, i stället för företagsportalappen.

### <a name="december-2016"></a>December 2016

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Hantering av telekomkostnad i förhandsversionen av Azure-portalen<!--747605-->
Vi börjar nu att förhandsgranska integrering med tredje parters hantering av telekomkostnad (TEM) i Azure-portalen. Du kan använda Intune för att tvinga gränser för nationell och central dataanvändning. Vi börjar de här integreringarna med [Saaswedo](http://www.saaswedo.com). Om du vill aktivera den här funktionen i utvärderingsversionen av klienten kan du [kontakta Microsoft support](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new-in-microsoft-intune.md).

