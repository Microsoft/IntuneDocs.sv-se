---
# required metadata

title: Skydda iOS-enheter med Kringgå Aktiveringslås för Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Skydda iOS-enheter med Kringgå Aktiveringslås för Microsoft Intune
Microsoft Intune kan hjälpa dig att hantera iOS aktiveringslås, en funktion i Hitta Min iPhone appen för enheter med iOS 7.1 och senare. Aktiveringslås aktiveras automatiskt när Hitta Min iPhone appen används på en enhet. När den har aktiverats måste användarens Apple-ID och lösenord anges innan någon kan:

-   Inaktivera Hitta Min iPhone

-   Rensa enheten

-   Återaktivera enheten

## Hur du påverkas av aktiveringslås
Även om aktiveringslås hjälper till att skydda iOS-enheter och förbättra chansen att få tillbaka dem om de tappas bort eller blir stulna, så gör den här funktionen att du som IT-administratör står inför ett antal utmaningar. Exempel:

-   En av dina användare ordnar aktiveringslås på en enhet. Användaren lämnar sen företaget och lämnar tillbaks enheten. Utan användarens Apple-ID och lösenord går det inte att återaktivera enheten.

-   Du behöver en rapport med alla enheter som har aktiveringslås aktiverat.

-   Under en enhetsuppdatering i din organisation, vill du omtilldela några enheter till en annan avdelning. Du kan bara omtilldela enheter som inte har aktiveringslås aktiverat.

För att hjälpa att lösa de här problemen, så introducerade Apple med iOS 7.1 funktionen Kringgå Aktiveringslås. Den låter dig ta bort aktiveringslås från övervakade enheter utan att ha användarens Apple-ID och lösenord. Övervakade enheter kan generera en enhetsspecifik kod för att kringgå aktiveringslåset, vilken lagras på Apples aktiveringsserver.

> [!TIP]
> Övervakat läge för iOS-enheter gör att du kan använda Apples Konfigureringsverktyg för att låsa en enhet och begränsa funktionaliteten till specifika företagsändamål. Övervakat läge är generellt sett bara till för företagsägda enheter.

## Hur Intune hjälper dig att hantera aktiveringslås
Intune kan begära status för aktiveringslås för både övervakade och oövervakade enheter som kör iOS 7.1 och senare. För övervakade enheter kan Intune hämta koden för att förbikoppla aktiveringslås och skicka den direkt till enheten. Om enheten har rensats kan du få åtkomst till den direkt genom att använda koden som användarnamn och ett tomt lösenord).

**Företagets fördelar med detta är att**:

-   Användaren får säkerhetsfördelarna i Hitta Min iPhone-appen.

-   Du kan låta användarna sköta sitt arbete och samtidigt vara säker på att du kan avaktivera eller låsa upp enheten när den behöver återanvändas.

## Att kringgå aktiveringslås från Intunes administrationskonsol
> [!IMPORTANT]
> När du kringgått aktiveringslåset på en enhet, kommer den automatiskt att aktivera ett nytt aktiveringslås om appen Hitta Min iPhone öppnas. Därför **bör du ha fysisk tillgång till enheten innan du följer den här proceduren**.

1.  I [Microsoft Intune administrationskonsol](https://manage.microsoft.com) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla företagsägda enheter**.

2.  Markera den enhet vars aktiveringslås du vill förbikoppla. Välj **Förbikoppla aktiveringslås**.

3.  Läs varningsmeddelandet. Välj **Ja** för att fortsätta.

Du kan kontrollera status för upplåsningsbegäran på informationssidan för enheten.

## Hur man ser vilka enheter som använder aktiveringslås
Du kan se vilka enheter som använder aktiveringslås på två sätt:

-   Kör **Inventeringsrapporter för Mobila enheter**. Den här rapporten visar kolumnerna **Status Aktiveringslås** och **Övervakad** vilka indikerar enheternas status. Värdena för **Övervakad** är **Ja** eller **Nej**, och värdena för **Status Aktiveringslås** är:

    -   Aktiverad med kod för att kringgå

    -   Aktiverad utan kod för att kringgå (enheten är oövervakad)

    -   Aktiverad utan kod för att kringgå (ingen kontakt med enhet)

    -   Inte aktiverad

    Fältet **Status Aktiveringslås** är tomt för enheter som inte kör iOS 7.1 eller senare.

-   Välj en enhet i gruppvyn, du kan se status för aktiveringslås i informationspenelen.

    Om du väljer en enhet i noden **Alla företagsägda enheter** och aktiveringslåset är aktiverat för enheten, så kan du också se koden för att förbikopplingskoden. Koden kan användas för att manuellt kringgå aktiveringslåset.

### Se även
[Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md)
[Skydda dina enheter med fjärrlåsning och lösenordsåterställning](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


