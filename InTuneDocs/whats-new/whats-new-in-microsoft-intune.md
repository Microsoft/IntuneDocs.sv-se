---
title: "Vad är nytt | Microsoft Docs"
description: "Ta reda på vad som är nytt i den här månadens och i tidigare versioner av Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a9336e3d230de962d2623dd627e45c6e9262a822
ms.openlocfilehash: cfe4a0bb802956278387ac2a39d5316482e09332
ms.lasthandoff: 03/02/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Nyheter i Microsoft Intune – Februari 2017
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

> [!Note]
> Hybriddistributioner (Configuration Manager med Intune) kommer också att ha stöd för alla dessa funktioner. Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nya funktioner

### <a name="modernizing-the-company-portal-website---753980--"></a>Modernisera företagsportalswebbplatsen <!--753980-->
Företagsportalens webbplats kommer att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och -tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny" ![Liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar. Du kan hitta före och efter-bilder som är tillgängliga på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Ny guidad upplevelse för Windows 10-företagsportalen <!--713927-->
Från och med mars innehåller företagsportalen för Windows 10 en guidad Intune-genomgång för enheter som inte har identifierats eller registrerats. Den nya guiden innehåller stegvisa anvisningar anpassade för användarens version av Windows 10 som hjälper användaren att utföra AAD-registrering (krävs för identifiering för funktioner för villkorlig åtkomst) och MDM-registrering (krävs för enhetshanteringsfunktioner). Guiden bli tillgänglig från företagsportalens startsida och är frivillig. Användarna kan fortsätta att använda appen även om de inte slutför registreringen men appen kan då ha begränsad funktionalitet.

## <a name="notices"></a>Meddelanden

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>Gruppmigrering kräver inte några uppdateringar för grupper eller principer för iOS-enheter<!--898837-->
För varje Intune-enhetsgrupp som tilldelas i förväg av en profil för registrering av företagsenhet skapas en motsvarande dynamisk enhetsgrupp i AAD. Det görs baserat på namnet på profilen för registrering av företagsenhet under migreringen till Azure Active Directory-enhetsgrupper. Detta säkerställer att enheter automatiskt grupperas och tar emot samma principer och appar som den ursprungliga Intune-gruppen när de registreras.

När en klient startar migreringsprocessen för att gruppera och ange mål skapar Intune automatiskt en dynamisk AAD-grupp som motsvarar en Intune-grupp som är mål för en profil för registrering av företagsenheter. Om Intune-administratören tar bort Intune-målgruppen tas inte motsvarande dynamiska AAD-grupp bort. Gruppens medlemmar och den dynamiska frågan kommer att tas bort, men själva gruppen finns kvar tills IT-administratören tar bort den via AAD-portalen.

Och om IT-administratören ändrar vilken grupp Intune riktas mot av en profil för registrering av företagsenheter skapar Intune en ny dynamisk grupp som avspeglar den nya profiltilldelningen. Den nya dynamiska gruppen som har skapats för den gamla tilldelningen tas inte bort.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>Standardvärde för hantering av Windows Desktop-enheter via Windows-inställningar <!--663050-->
Standardbeteendet för att registrera Windows 10-datorer ändras. Nya registreringar följer det normala MDM-agentregistreringsflödet i stället för via datoragenten. Webbplatsen för företagsportalen ger Windows 10 Desktop-användare registreringsanvisningar som leder dem genom processen med att lägga till Windows 10 Desktop-datorer som mobila enheter. Detta påverkar inte datorer som är registrerade och företaget kan fortfarande hantera Windows 10-datorer med datoragenten [om så önskas](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Förbättra stöd i hantering av mobila appar för selektiv rensning <!--581242-->
Slutanvändare får ytterligare vägledning för hur de kan återfå åtkomsten till arbets- eller skoldata som tas bort automatiskt till följd av principen "Offlineintervall innan appdata rensas".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>Länkar till företagsportalen för iOS öppnas i appen <!--665954-->
Länkar i företagsportalappen för iOS, inklusive sådana som leder till dokumentation och appar, öppnas direkt i företagsportalappen med en Safari-vy i appen. Den här uppdateringen skickas separat från tjänstuppdateringen i januari.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Ny MDM-serveradress för Windows-enheter <!--893007-->
Windows och Windows Phone-användare som försöker registrera en enhet misslyckas om de anger __manage.microsoft.com__ som MDM-serveradressen (om de uppmanas till det). MDM-serveradressen ändras från __manage.microsoft.com__ till __enrollment.manage.microsoft.com__. Meddela användarna att de ska använda adressen __enrollment.manage.microsoft.com__ som MDM-serveradress om de tillfrågas om den under registreringen av en Windows- eller och Windows Phone-enhet. Inga ändringar krävs för din CNAME-installation. Mer information om den här ändringen finns på [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.
* __Gränssnitt__: Knapparna Aktuella appar och Alla appar har uppdaterats på fliken. Sökknappen är nu flytande.
* __Navigering__: Alla appar visar en flikvy över Aktuella, Alla och Kategorier för att underlätta navigeringen.
* __Tjänst__: Flikarna Mina enheter och Kontakta IT har förbättrad läsbarhet.

Du kan hitta före och efter-bilder på [sidan med UI-uppdateringar](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Koppla flera hanteringsverktyg till Windows Store för företag<!--926135-->
Om du använder fler än ett hanteringsverktyg för att distribuera Windows Store för affärsappar kunde du tidigare bara koppla ett av dem till Windows Store för företag. Du kan nu koppla flera hanteringsverktyg till butiken, exempelvis Intune och Configuration Manager. Mer information finns i [Hantera appar som du har köpt från Windows Store för företag med Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Vad är nytt i den offentliga förhandsversion av Intunes adminstratörsupplevelse på Azure <!--736542-->

Tidigt under 2017 kommer vi att migrera vår fullständiga administratörsupplevelse till Azure, vilket ger kraftfull och integrerad hantering av EMS-kärnarbetsflöden på en modern tjänsteplattform som kan utökas med Graph API:er.

Nya utvärderingsklienter kan se den offentliga förhandsversionen av den nya administratörsupplevelsen i Azure-portalen denna månad. I förhandsgranskningen levereras funktioner och paritet med den befintliga Intune-konsolen upprepade gånger.

Administratörsupplevelsen i Azure-portalen använder den redan meddelade nya grupperings- och målfunktionen. När din befintliga klient migreras till den nya grupperingsupplevelsen migreras du även till att förhandsgranska den nya administratörsupplevelsen på din klient. Om du under tiden vill testa eller titta på någon av de nya funktionerna fram tills klienten har migrerats kan du registrera dig för ett nytt utvärderingskonto för Intune eller ta en titt på den [nya dokumentationen](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Om du har frågor om tidslinjen för migrering av din klientorganisation, kontakta vårt migreringsteam på [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Du kan se vad som är nytt i Intunes förhandsversion i Azure [här](https://docs.microsoft.com/intune-azure/introduction/whats-new).

## <a name="whats-coming"></a>Kommande nyheter

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple kräver uppdateringar för Application Transport Security <!--748318-->

Apple har tillkännagivit att de från och med våren 2017 kommer att framtvinga vissa krav för Application Transport Security (ATS). ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS-appar i företagsportalen. Läs [Intunes supportblogg](https://aka.ms/compportalats) för mer information. 

### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Vad är nytt i förhandsversionen av Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Nyheter i företagsportalens gränssnitt](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui)
* [Nyhetsarkiv](whats-new-archive.md)

