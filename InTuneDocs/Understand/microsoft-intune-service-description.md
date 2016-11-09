---
title: "Beskrivning av tjänst | Microsoft Intune"
description: "Intune är en molnbaserad tjänst som hjälper dig att hantera Windows-datorer och mobila enheter med iOS, Mac OS X, Android och Windows."
keywords: 
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: e3694f80d6148abbce004bb0c7143bf394b313d9


---

# Beskrivning av Microsoft Intune-tjänsten

Microsoft Intune är en molnbaserad tjänst som hjälper dig att hantera Windows-datorer och mobila enheter med iOS, Mac OS X, Android och Windows. Intune hjälper också till att skydda företagsprogram och -data. Du kan använda Intune enbart eller integrera det med System Center Configuration Manager för att utöka dina hanteringsfunktioner. 

Microsoft erbjuder Intune Onboarding-förmåner för berättigade tjänster i berättigade planer. Med Onboarding-förmånerna kan du arbeta på distans med Microsoft-specialister för att färdigställa din Intune-miljö. Mer information finns i [Beskrivning av Microsoft Intune Onboarding-förmåner](http://go.microsoft.com/fwlink/?LinkId=619281).

Du kan börja använda Intune med en kostnadsfri 30-dagars utvärderingsversion som innehåller 100 användarlicenser. Påbörja din kostnadsfria utvärderingsperiod genom att [klicka här för att besöka sidan Intune-registrering](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Om din organisation har ett företagsavtal eller motsvarande volymlicensavtal, kontaktar du din Microsoft-representant om du vill konfigurera den kostnadsfria utvärderingsversionen.

> [!NOTE]
> Om din organisation redan har ett arbets- eller skolkonto för Microsoft Online Services och kanske kommer att fortsätta med den här Intune-prenumerationen i produktion efter det att utvärderingsperioden har löpt ut, klickar du på alternativet **Logga in** på sidan Logga in och autentiserar med hjälp av din organisations globala administratörskonto. Den här åtgärden säkerställer att din Intune-utvärderingsversion länkar till det befintliga arbets- eller skolkontot.

En lista över inställningar du kan konfigurera för mobila enheter finns här:

-   [Funktioner för hantering av registrerade enheter i Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune) 

-   [Hantering av mobila hybridenheter (MDM) med System Center Configuration Manager och Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx) 

Information om System Center Configuration Manager finns i [Dokumentation för System Center Configuration Manager](https://technet.microsoft.com/library/mt346023.aspx).

## Förstå hur uppdateringar av Intune-tjänsten påverkar dig
Eftersom Intune är en onlinetjänst kan Microsoft uppdatera den regelbundet.

Använd informationen i det här avsnittet för att förstå hur ofta dessa tjänsteuppdateringar genomförs och den avisering i förväg som vi skickar till dig när en uppdatering kan påverka din användning av tjänsten.

Information om ändringar i Intune-tjänsten finns i [Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune). På [Microsoft Intune-bloggen](http://blogs.technet.com/b/microsoftintune/) diskuteras också ändringar i tjänsten och du får nyttiga tips så att du kan få ut mesta möjliga av Intune. 

Viktiga uppdateringar för tjänsten kommer också meddelas meddelandecentret till [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx). Om du installerar tillhörande [Office 365 Admin-mobilapp](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) kan du ta emot meddelanden på din mobila enhet.

> [!NOTE]
> Du kan övervaka hälsotillståndet för Intune-tjänsten i den [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx). Välj **Tjänstens hälsa** i det vänstra fönstret.  

Här är de typer av meddelanden som Microsoft tillhandahåller om Intune-tjänsten:
-   Som hjälp att planera för tjänsteändringar meddelar vi dig minst 30–90 dagar innan tjänsteuppgraderingen beroende på effekten av ändringen. Detta sker med hjälp av kommunikationskanaler i produkten som anslagstavleaviseringar. Exempel på ändringar:
* Uppdateringar som kan påverka regelefterlevnaden
* Ändringar av användarupplevelse, användargränssnitt och arbetsflöden
* Nya eller ändrade API:er – du får ett meddelande om att du måste utföra tester för att säkerställa bakåtkompatibilitet för anpassade appar
* Ändringar av systemkrav, till exempel hur gammal webbläsarversionen får lov att vara
* Alla uppdateringar som kräver att du vidtar åtgärder för att aktivera funktionen eller för att undvika tjänsteavbrott för funktionen.
-   Microsoft tillhandahåller information om nya funktioner och förbättringar av befintliga funktioner i vår månatliga tjänstuppdatering. I allmänhet skickar Microsoft ut tjänstuppdateringar runt mitten av varje månad. Uppdateringarna beskrivs i [Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune).
-   Om Intune-tjänsten skulle dras tillbaka meddelas du 12 månader i förväg.

## Välj den hanteringslösning som passar dig
Du kan konfigurera Intune på ett antal sätt för att hantera och skydda företagets mobila enheter och datorer (kallas **enheter** i det här dokumentet).

-   **Fristående Intune-konfiguration.** Använd den webbaserade administrationskonsolen i Intune för att hantera enheter i organisationen. Intune kan användas utan att det finns någon lokal IT-infrastruktur, men om du använder Intune med Active Directory Domain Services, kan du använda domänanvändarkonton som du hanterar med domäntjänster med Intune.

-   **Intune med System Center Configuration Manager.** Använd hanteringskonsolen i Configuration Manager för att hantera datorer och mobila enheter i företaget. Den här konfigurationen kan hjälpa dig att hantera organisationens enheter genom en enda konsol, nämligen administratörskonsolen i Configuration Manager. Configuration Manager stöder ett stort antal mobila enheter, servrar och datorer. Se [Hantering av mobila hybridenheter (MDM) med System Center Configuration Manager och Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx) för mer information.  Mer hjälp för att bestämma vilken metod som är bäst för dig finns i [Välj mellan fristående Microsoft Intune och hantering av mobila hybridenheter med Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx). 


## Läs mer om Intune
Använd dessa resurser om du vill veta mer om Intune:

-   [Microsoft Intune Trust Center](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) innehåller information om säkerhet och sekretess samt efterlevnadsregler för Intune och beskriver även några av certifieringarna för Intune.

-   [Funktioner för hantering av registrerade enheter i Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune) 

### Se även
[Microsoft Intune](https://docs.microsoft.com/intune/)
[-dokumentationsbibliotek för System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Sep16_HO4-->


