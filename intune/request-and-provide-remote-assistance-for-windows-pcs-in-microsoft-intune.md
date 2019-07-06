---
title: Begära och tillhandahålla hjälp för Windows-datorer
titleSuffix: Microsoft Intune
description: Beskriver de steg som slutanvändarna och IT-administratören måste vidta för att fjärrhjälp för stationära Windows-datorer som hanteras som PC-datorer ska kunna fjärrstartas samt steg för att fjärrstarta en PC-dator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: a58339f8a956e4250064bc81e2f291a72c27c27f
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549138"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Begära och tillhandahålla hjälp för Windows-datorer

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Informationen i det här avsnittet gäller endast för stationära Windows-datorer som du hanterar som datorer med Intune-klientprogramvaran.

Intune kan använda [TeamViewer](https://www.teamviewer.com)-programvaran, som köps separat, för att göra det möjligt för dig att ge fjärrhjälp till de användare som kör Intune-programklienten. När en användare begär hjälp från Microsoft Intune Center informeras du genom en avisering, kan acceptera begäran och sedan erbjuda hjälp. Den här funktionen ersätter den befintliga Windows-fjärrhjälpsfunktionen i Intune.


## <a name="before-you-start"></a>Innan du börjar

Innan du börjar upprätta och svara på förfrågningar om fjärrhjälp måste du kontrollera att följande krav är uppfyllda:

- Du måste ha [registrerat ett TeamViewer-konto](https://login.teamviewer.com/LogOn#register) om du vill kunna logga in på TeamViewer-webbplatsen.
- Windows-datorer som du vill administrera måste [hanteras av Windows-klientprogrammet](manage-windows-pcs-with-microsoft-intune.md)
- Alla Windows-datoroperativsystem som stöds av Intune kan administreras.

## <a name="configure-the-teamviewer-connector"></a>Konfigurera TeamViewer-anslutningen

1. Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och välj **Admin**.
2. På arbetsytan **Admin** väljer du **TeamViewer**.
3. Välj **Aktivera** på sidan **TeamViewer** under **TeamViewer-anslutningsprogram**.
4. I dialogrutan **Aktivera TeamViewer** läser du igenom licensvillkoren och väljer **Godkänn**. Om du inte redan har en licens för TeamViewer, väljer du **Köp en licens för TeamViewer**.
5. När webbläsarfönstret till TeamViewer öppnas loggar du in på webbplatsen med autentiseringsuppgifterna till TeamViewer.
6. På TeamViewer-webbplatsen läser du igenom och godkänner alternativen för att tillåta att Intune ansluter till TeamViewer.
7. I Intune-konsolen kontrollerar du att objektet **TeamViewer-anslutningsprogram** visas som **Aktiverat**.


## <a name="open-a-remote-assistance-request-end-user"></a>Öppna en begäran om fjärrhjälp (slutanvändare)

1. Öppna **Microsoft Intune Center** på en Windows-klientdator.
2. Välj **Begär fjärrhjälp** under **Fjärrhjälp**.
3. När du har godkänt förfrågan (se nedan) öppnas TeamViewer på klienten. Användaren måste godkänna alla meddelanden som indikerar att webbläsaren försöker öppna TeamViewer-programmet.
4. Användaren ser ett meddelande med en förfrågan om du får styra personens dator. Användaren måste godkänna meddelandet för att kunna fortsätta.
5. Under fjärrhjälpssessionen ser användaren ett fönster som visar att du är ansluten. Om användaren stänger fönstret avslutas fjärrsessionen.

## <a name="respond-to-a-remote-assistance-request"></a>Svara på en begäran om fjärrhjälp

1. När en användare skickar en begäran om fjärrhjälp kan du visa den på arbetsytan **Aviseringar** under **Övervakning** > **Fjärrhjälp**. Exempel:
   > ![Skärmbild av en begäran om fjärrhjälp](/intune/media/team-viewer.png)

<br>Om en begäran inte besvaras på fyra timmar tas den bort.
2. Välj om du vill acceptera begäran väljer du **Godkänn begäran och starta Fjärrhjälp**.
3. I dialogrutan **En ny begäran om fjärrhjälp väntar** väljer du **Godkänn begäran om fjärrhjälp**. Om det inte redan är installerat installerar TeamViewer alla nödvändiga appar på datorn.
4. TeamViewer meddelar därefter slutanvändaren att du vill ta kontroll över datorn. När användaren har accepterat begäran öppnas TeamViewer-fönstren och du kan styra datorn.

Du kan använda alla tillgängliga TeamViewer-kommandon i en fjärrhjälpssession när du styr en fjärransluten dator. Om du vill få hjälp med de här kommandona hämtar det [Handbok för fjärrstyrning](http://www.teamviewer.com/en/support/documents/) från TeamViewer-webbplatsen.

## <a name="close-the-remote-assistance-session"></a>Stänga fjärrhjälpssessionen

Från menyn **Åtgärder** i fönstret **TeamViewer** väljer du **Avsluta sessionen**.

## <a name="remotely-restart-a-windows-pc"></a>Starta om en Windows-dator via en fjärranslutning
När du hjälper dina användare med deras problem kan du emellanåt behöva fjärrstarta om deras datorer. Fjärrstarta om en Windows-dator enligt följande steg.

1. I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator som du vill starta om).

2. Markera en eller flera datorer, och välj sedan **Fjärruppgifter** &gt; **Starta om datorn**.

3. Om du vill visa aktivitetens status väljer du **Fjärruppgifter** längst ner till höger på sidan.

4. I dialogrutan **Aktivitetsstatus** kan du granska aktuella fjärrhanteringsaktiviteter, aktivitetsstatus, enhetsnamn och eventuella rapporterade fel.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
