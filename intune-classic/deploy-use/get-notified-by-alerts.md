---
title: "Håll dig informerad med aviseringar | Microsoft Docs"
description: "Läs om hur aviseringar ger dig koll på vad som händer i Microsoft Intune."
keywords: 
author: nathbarn
ms.author: angrobe
manager: angrobe
ms.date: 8/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft intune
ms.technology: 
ms.assetid: 396ea714 0433 4bd5 a934 8d0b477f28e4
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune classic
ms.openlocfilehash: 9a84cc5b294a1a330aab978de5ef0fd8cfa4c259
ms.sourcegitcommit: 30b51c625311398b371c0326d41216f55315f627
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/05/2017
---
#  <a name="use-alerts-to-get-notified-by-microsoft-intune"></a>Håll dig informerad med aviseringar från Microsoft Intune

[!INCLUDE[classic portal](../includes/classic-portal.md)]

Aviseringar låter dig ha koll på vad som händer i Microsoft Intune. Aviseringar kan exempelvis låta dig få reda på följande händelser:
- Ett problem med Exchange-anslutaren som påverkar mobil enhetshantering
- Skadlig kod har hittats på en dator
- En konflikt mellan två Intune-principer har upptäckts
- En distribution av Intune-programklienten misslyckas

## <a name="how-alerts-work"></a>Så fungerar aviseringar

Aviseringar genereras baserat på **aviseringstyper**, en uppsättning förinställda regler som finns inbyggda i Intune. Aviseringstypen **Molnlagringen har 10% eller mindre ledigt utrymme** låter dig exempelvis veta när du börjar få slut på utrymme att lagra dina appar i molnet. Du kan aktivera eller inaktivera aviseringstyper och konfigurera egenskaper för varje aviseringstyp. Genom att använda ovanstående aviseringstyp kan du exempelvis konfigurera:

- **Tillstånd:** Om aviseringstypen är aktiverad eller inaktiverad.
- **Allvarlighetsgrad:** Hur allvarlig är den här aviseringen?

|Allvarlighetsgrad|Information|
|--|---|
|**Kritisk varning**|Anger ett allvarligt problem som du bör undersöka så fort som möjligt, exempelvis om skadlig kod har upptäckts på en dator.|
|**Varning**|Anger ett problem som inte är allvarligt än, men som kan bli allvarligt om du inte tar tag i det. Ett exempel är säkerhetsuppdateringar som väntar på att installeras.|
|**Informationsavisering**|Visar information som inte är driftskritisk, exempelvis att en ny version av Exchange-anslutaren finns tillgänglig.|

Andra aviseringstyper kan ha olika konfigurerbara objekt, till exempel hur många enheter i procent som ska vara påverkade av ett problem innan en avisering genereras.

**När villkoret i en aviseringstyp uppfylls genereras en avisering som visas i Intune-administratörskonsolen.**

Du kan dessutom konfigurera Intune att meddela dig via e-post när en avisering genereras.

## <a name="set-up-alerts"></a>Ställa in aviseringar

I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Admin** &gt; **Aviseringar och meddelanden** och sedan något av följande:

|Aktivitet|Beskrivning|
|---|------|
|**Aviseringstyper**|Välj den aviseringstyp som du vill konfigurera och gör sedan något av följande:<br /><br />Välj **Konfigurera**. I dialogrutan **Konfigurera aviseringstyp** väljer du önskade inställningar och sedan **OK**.<br /><br />**Aktivera** eller **Inaktivera** aviseringen.<br /><br />Expandera noden **Aviseringstyper** och välj en kategori för att bara visa aviseringstyperna i den kategorin.|
|**Mottagare**|Klicka på **Lägg till** om du vill lägga till en ny e-postadress som ska ta emot de e-postmeddelanden som du konfigurerar.<br /><br />Du kan också **Redigera** eller **Ta bort** befintliga mottagare.<br /><br />För att ta emot aviseringar måste du även lägga till e-postadressen som mottagare under **Aviseringsregler**.|
|**Aviseringsregler**|Konfigurerar regler som definierar vem en e-postavisering kommer skickas till. Du kan antingen:<br /><br />**Välj en befintlig regel**   Välj en regel och välj sedan **Välj mottagare**. Sedan kan du välja alla mottagare som kommer få ett e-postmeddelande när en avisering som uppfyller regeln har genererats.<br /><br />**Skapa en ny regel**   Ange ett namn för regeln, välj aviseringskategorier och allvarlighetsgrad som ska gälla för reglerna, välj de enhetsgrupper som regeln gäller för och markera de användare som ska få ett e-postmeddelande när en avisering har genererats.<br /><br />Du kan också **Aktivera**, **Avaktivera**, **Redigera**, or **Ta bort** en befintlig regel.|

## <a name="working-with-alerts"></a>Arbeta med aviseringar

Använd följande alternativ för att hjälpa dig arbeta med aviseringar från Intunes adminstratörskonsol.

|Alternativ|Beskrivning|
|-----|----|
|**Visa aktiva aviseringar**|Välj något av:<br /><br />**Visa en aviseringssammanställning**   På arbetsytan **Instrumentpanel** visas de viktigaste felen i aviseringsfönstret. Klicka på fönstret om du vill se mer detaljerad information.<br /><br />Dessutom kan du visa en sammanställning av aviseringar på sidan **Översikt** i arbetsytan **Aviseringar** .<br /><br />**Visa alla aviseringar**   Gå till arbetsytan **Aviseringar** och klicka på **Alla aviseringar**.|
|**Visa meddelanden**|Välj något av:<br /><br />Gå till arbetsytan **Instrumentpanel** och välj **Meddelanden**.<br /><br />På arbetsytan **Aviseringar** väljer du **Alla aviseringar** &gt; **Aviseringar**.|
|**Stänga en avisering**|I listan över aviseringar väljer du den avisering som du vill stänga och sedan **Stäng avisering**.<br /><br />Stängda aviseringar tas bort permanent efter 90 dagar.|
|**Återaktivera en stängd avisering**|I listan över aviseringar öppnar du listrutan **Filter** och väljer **Stängd**.<br /><br />I listan över stängda aviseringar väljer du den avisering som du vill återaktivera och sedan **Återaktivera avisering**.|

Intune-aviseringar är aktiva tills:

- Det problem som orsakade aviseringen har lösts
- Aviseringen stängs manuellt.
- Det har gått 45 dagar sedan aviseringen genererades

> [!TIP]
> Om samma avisering genereras av enheter som kör olika operativsystem så är det möjligt att du ser flera versioner av samma avisering i aviseringslistan.
