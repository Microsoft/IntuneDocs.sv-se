---
title: "Beskrivning av tjänst | Microsoft Intune"
description: "Intune är en molnbaserad tjänst som hjälper dig att hantera Windows-, iOS-, Mac OS X-, Android- och Windows Mobile-enheter."
keywords: 
author: lindavr
ms.author: lindavr
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
ms.sourcegitcommit: dccfccdb4f65a0c6ed90ede3ff673163b948c5ab
ms.openlocfilehash: 508f7c53ca5c7f6e649c6b04bee0616771c9c101


---

# <a name="microsoft-intune-service-description"></a>Beskrivning av Microsoft Intune-tjänsten

Microsoft Intune är en molnbaserad tjänst som hjälper dig att hantera enheter som kör Windows, Mac OS X, iOS, Android eller Windows Mobile. Intune hjälper också till att skydda företagsprogram och -data. Du kan använda bara Intune eller integrera det med System Center Configuration Manager för att utöka dina hanteringsfunktioner.

Microsoft erbjuder Intune Onboarding-förmåner för berättigade tjänster i berättigade planer. Med Onboarding-förmånerna kan du arbeta på distans med Microsoft-specialister för att färdigställa din Intune-miljö. Mer information om Onboarding-förmånen finns i [beskrivningen av Microsoft Intune Onboarding-förmånen](http://go.microsoft.com/fwlink/?LinkId=619281).

Du kan börja använda Intune med en kostnadsfri 30-dagars utvärderingsversion som innehåller 100 användarlicenser. Starta din kostnadsfria utvärderingsversion genom att [gå till sidan för Intune-registrering](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/). Om din organisation har ett företagsavtal eller motsvarande volymlicensavtal kontaktar du din Microsoft-representant för att konfigurera den kostnadsfria utvärderingsversionen.

> [!NOTE]
> Om din organisation redan har ett arbets- eller skolkonto för Microsoft Online Services och kanske kommer att fortsätta med den här Intune-prenumerationen i produktion efter det att utvärderingsperioden har löpt ut, väljer du alternativet **Logga in** på sidan Logga in och autentiserar med hjälp av din organisations globala administratörskonto. Den här åtgärden säkerställer att din Intune-utvärderingsversion länkar till det befintliga arbets- eller skolkontot.

En lista över inställningar som du kan konfigurera på mobila enheter finns här:

-   [Funktioner för hantering av registrerade enheter i Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Hantering av mobila hybridenheter (MDM) med System Center Configuration Manager och Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx)

Mer information om System Center Configuration Manager finns i [dokumentationen för System Center Configuration Manager](https://technet.microsoft.com/library/mt346023.aspx).

## <a name="learn-how-intune-service-updates-affect-you"></a>Lär dig hur uppdateringar av Intune-tjänsten påverkar dig
Eftersom Intune är en onlinetjänst kan Microsoft uppdatera den regelbundet.

Den här artikeln innehåller information om hur ofta dessa tjänsteuppdateringar görs samt om den avisering som vi skickar till dig när en uppdatering kan påverka din användning av tjänsten.

Information om ändringar i Intune-tjänsten finns i [Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune). I [Microsoft Intune-bloggen](http://blogs.technet.com/b/microsoftintune/) diskuteras också ändringar i tjänsten och du får nyttiga tips så att du kan få ut mesta möjliga av Intune.

Viktiga uppdateringar för tjänsten kommer också meddelas meddelandecentret till [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx). Om du installerar tillhörande [Office 365 Admin-mobilapp](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a) kan du ta emot meddelanden på din mobila enhet.

> [!NOTE]
> Du kan övervaka hälsotillståndet för Intune-tjänsten i den [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx). Välj **Tjänstens hälsa** i det vänstra fönstret.  

Här är de typer av meddelanden som Microsoft tillhandahåller om Intune-tjänsten:
-   För att hjälpa dig att planera för tjänständringar meddelar vi dig minst 30–90 dagar före tjänsteuppgraderingen, beroende på effekten av ändringen. Detta sker med hjälp av kommunikationskanaler i produkten som anslagstavleaviseringar. De här förändringarna kan innefatta:
    * Uppdateringar som kan påverka regelefterlevnaden
    * Ändringar av användarupplevelse, användargränssnitt och arbetsflöden
    * Nya eller ändrade API:er – du får ett meddelande om att du måste utföra tester för att säkerställa bakåtkompatibilitet för anpassade appar
    * Ändringar av systemkrav, till exempel hur gammal webbläsarversionen får lov att vara
    * Alla uppdateringar som kräver att du vidtar åtgärder för att aktivera funktionen eller för att undvika tjänstavbrott för funktionen.
-   Microsoft tillhandahåller information om nya funktioner och förbättringar av befintliga funktioner i vår månatliga tjänstuppdatering. I allmänhet skickar Microsoft ut tjänstuppdateringar runt mitten av varje månad. Uppdateringarna beskrivs i [Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune).
    -   Om Intune-tjänsten skulle dras tillbaka meddelas du 12 månader i förväg.

## <a name="choose-the-management-solution-thats-right-for-you"></a>Välj den hanteringslösning som passar dig
Du kan konfigurera Intune på flera olika sätt för att hantera och skydda företagets mobila enheter och datorer (kallas gemensamt för **enheter** i den här artikeln).

-**Fristående Intune-konfiguration.** Använd den webbaserade administrationskonsolen i Intune för att hantera enheter i organisationen. Intune kan användas utan en lokal IT-infrastruktur. Om du använder Intune med Active Directory Domain Services kan du använda domänanvändarkonton som du hanterar med Domain Services med Intune.

-**Intune med System Center Configuration Manager.** Använd hanteringskonsolen i Configuration Manager för att hantera datorer och mobila enheter i företaget. Den här konfigurationen kan hjälpa dig att hantera organisationens enheter genom en enda konsol, nämligen administratörskonsolen i Configuration Manager. Configuration Manager stöder ett stort antal mobila enheter, servrar och datorer. Mer information om Configuration Manager finns i [Hantering av mobila hybridenheter (MDM) med System Center Configuration Manager och Microsoft Intune](https://technet.microsoft.com/library/mt627883.aspx). Mer hjälp för att bestämma vilken metod som är bäst för dig finns i [Välj mellan fristående Microsoft Intune och hantering av mobila hybridenheter med Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx).


## <a name="learn-more-about-intune"></a>Läs mer om Intune
Använd dessa resurser om du vill veta mer om Intune:

- [Microsoft Intune Trust Center](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/) innehåller information om säkerhet och sekretess samt efterlevnadsregler för Intune och beskriver även några av certifieringarna för Intune.

- [Funktioner för hantering av registrerade enheter i Microsoft Intune](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

### <a name="see-also"></a>Se även
[Microsoft Intune](https://docs.microsoft.com/intune/)
[-dokumentationsbibliotek för System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682041.aspx)

[Nyheter i Microsoft Intune](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Nov16_HO3-->


