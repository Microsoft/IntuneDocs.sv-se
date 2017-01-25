---
title: "Hantera iOS-aktiveringslås på enheter | Microsoft Docs"
description: "Microsoft Intune kan hjälpa dig att hantera iOS aktiveringslås, en funktion i Hitta Min iPhone appen för enheter med iOS 7.1 och senare."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: a6fa910c0a8ec1a9542e03a276dbb8d0757d75b4


---

# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>Skydda iOS-enheter med Kringgå Aktiveringslås för Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune kan hjälpa dig att hantera iOS-aktiveringslåset, en funktion i Hitta min iPhone-appen för enheter med iOS 8.0 och senare. Aktiveringslås aktiveras automatiskt när en användare öppnar appen Hitta min iPhone på en enhet. När den har aktiverats måste användarens Apple-ID och lösenord anges innan någon kan: 

-   Inaktivera Hitta Min iPhone

-   Rensa enheten

-   Återaktivera enheten

## <a name="how-activation-lock-affects-you"></a>Hur du påverkas av aktiveringslås
Även om aktiveringslås hjälper till att skydda iOS-enheter och förbättra chansen att få tillbaka en borttappad eller stulen enhet, så gör den här funktionen att du som IT-administratör står inför ett antal utmaningar. Exempel:

-   En användare ställer in aktiveringslås på en enhet. Användaren lämnar sen företaget och lämnar tillbaks enheten. Utan användarens Apple-ID och lösenord går det inte att återaktivera enheten.

-   Du behöver en rapport med alla enheter som har aktiveringslås aktiverat.

-   Du vill omtilldela några enheter till en annan avdelning under en enhetsuppdatering i organisationen. Du kan bara omtilldela enheter som inte har aktiveringslås aktiverat.

För att hjälpa att lösa de här problemen, så introducerade Apple med iOS 7.1 funktionen Kringgå Aktiveringslås. Den låter dig ta bort aktiveringslås från övervakade enheter utan att ha användarens Apple-ID och lösenord. Övervakade enheter kan generera en enhetsspecifik kod för att kringgå aktiveringslåset, vilken lagras på Apples aktiveringsserver.

> [!TIP]
> Övervakat läge för iOS-enheter gör att du kan använda Apple Configurator för att låsa en enhet och begränsa funktionerna till specifika företagsändamål. Övervakat läge är generellt sett bara till för företagsägda enheter.

## <a name="how-intune-helps-you-manage-activation-lock"></a>Hur Intune hjälper dig att hantera aktiveringslås
Intune kan begära status för aktiveringslåset för övervakade enheter som kör iOS 8.0 och senare. Enbart för övervakade enheter kan Intune hämta koden för att kringgå aktiveringslåset och skicka den direkt till enheten. Om enheten har rensats kan du få åtkomst till den direkt genom att använda ett tomt användarnamn och koden som lösenord.

**Företagets fördelar med detta är att**:

-   Användaren får säkerhetsfördelarna i Hitta Min iPhone-appen.

-   Du kan låta användarna sköta sitt arbete och samtidigt vara säker på att du kan avaktivera eller låsa upp en enhet när den behöver återanvändas.

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>Att kringgå aktiveringslås från Intunes administrationskonsol
> [!IMPORTANT]
> När du kringgått aktiveringslåset på en enhet aktiveras ett nytt aktiveringslås automatiskt om appen Hitta min iPhone öppnas. Därför **bör du ha fysisk tillgång till enheten innan du följer den här proceduren**.

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) väljer du **Grupper** &gt; **Alla enheter** &gt; **Alla företagsägda enheter**.

2.  Markera den enhet vars aktiveringslås du vill förbikoppla. Välj **Förbikoppla aktiveringslås**.

3.  Läs varningsmeddelandet. Välj **Ja** för att fortsätta.

Du kan kontrollera status för upplåsningsbegäran på informationssidan för enheten.

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>Hur man ser vilka enheter som använder aktiveringslås
Du kan se vilka enheter som använder aktiveringslås på två sätt:

-   Kör **Inventeringsrapporter för Mobila enheter**. Den här rapporten innehåller kolumnerna **Status Aktiveringslås** och **Övervakad** som visar enheternas status. Värdena för **Övervakad** är **Ja** eller **Nej**, och värdena för **Status Aktiveringslås** är:

    -   Aktiverad med kod för att kringgå

    -   Aktiverad utan kod för att kringgå (enheten är oövervakad)

    -   Aktiverad utan kod för att kringgå (ingen kontakt med enhet)

    -   Inte aktiverad

    Rutan **Status för aktiveringslås** är tom för enheter som inte kör iOS 8.0 eller senare.

-   Välj en enhet i en gruppvy för att se status för aktiveringslås i informationspanelen.

    Om du väljer en enhet i noden **Alla företagsägda enheter** och aktiveringslåset är aktiverat för enheten kan du också se koden för att kringgå. Koden kan användas för att manuellt kringgå aktiveringslåset.

    > [!IMPORTANT]
    >Intune hämtar information från enheter var sjunde dag för aktiveringslåset. Det innebär att enheterna kanske inte visas direkt med status för aktiveringslås i Intune-konsolen.


### <a name="see-also"></a>Se även
[Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md)
[Skydda dina enheter med fjärrlås och lösenordskodsåterställning](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->

