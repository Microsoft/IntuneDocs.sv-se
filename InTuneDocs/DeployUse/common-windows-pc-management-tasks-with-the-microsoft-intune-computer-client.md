---
# required metadata

title: Vanliga hanteringsuppgifter för Windows-dator | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vanliga hanteringsuppgifter för Windows-dator med Microsoft Intune datorklient
Studera det här avsnittet om du vill veta mer om hur du hanterar datorer som kör Intune-klienten. Om du inte har installerat klienten på dina datorer än läser du [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)


## Använd principer för att förenkla datorhantering
### Hantera Windows-brandväggen
Med principer förenklas administrationen av Windows-brandväggen på hanterade datorer. Mer information finns i [Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen i Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)

### Hantera Microsoft Intune Center
Med Microsoft Intune Center kan användarna:

-   Hämta program från företagsportalen.

-   Söka efter uppdateringar.

-   Hantera Microsoft Intune Endpoint Protection.

-   Begära fjärrhjälp.

Microsoft Intune Center är installerat på alla hanterade datorer. Du kan konfigurera följande inställningar i en Intune-princip och dessa visas för användaren i Microsoft Intune Center:

|Principinställningar|Information|
|------------------|--------------------|
|**Namn**|Namnet på den administratör som hanterar datorn.<br /><br />Maxlängd: 40 tecken|
|**Telefonnummer**|Telefonnumret till den administratör som hanterar datorn.<br /><br />Maxlängd: 20 tecken|
|**E-postadress**|E-postadressen till den administratör som hanterar datorn.<br /><br />Maxlängd: 40 tecken|
|**Webbplatsnamn**|Namnet på användarnas supportwebbplats.<br /><br />Maxlängd: 40 tecken|
|**Webbadress**|Webbadressen till supportwebbplatsen.<br /><br />Maxlängd: 150 tecken|
|**Anteckningar**|En kommentar som visas för användarna.<br /><br />Maxlängd: 120 tecken|

### Hantera inställningar för programuppdateringar
Använd principer för att konfigurera de inställningar som hanterade datorer använder för att söka efter och hämta uppdateringar från Microsoft och från tredje part. Mer information finns i [Hålla datorerna uppdaterade med programvaruuppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

### Hantera Endpoint Protection-inställningar
Använd principer för att konfigurera inställningar för Endpoint Protection , som du sedan distribuerar till hanterade datorer. De omfattar bland annat genomsökningsscheman och åtgärder som ska vidtas om skadlig kod upptäcks. Mer information finns i [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

## Visa maskinvaru- och programvaruinventering.
Intune samlar in detaljerad information om de hanterade datorernas maskinvara och programvara. Använd informationen i följande procedurer för att lära dig skapa:

-   En rapport som visar information om maskinvarukapaciteten hos datorerna.

-   En rapport som visar en lista över vilka program som finns installerade på varje dator.

-   Så här uppdaterar du en datorinventering för att säkerställa att data i rapporten är aktuella.

### Så här visar du information om datorerna

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Rapporter** &gt; **Datorinventeringsrapporter**

2.  På sidan **Skapa ny rapport** accepterar du standardvärdena eller anpassar dem om du vill filtrera resultatet som rapporten skickar tillbaka. Du kan till exempel välja att endast de datorer som kör Windows 8.1 ska visas i rapporten.

3.  Välj **Visa rapport** för att öppna **Datorinventeringsrapporter** i ett nytt fönster.

    Du kan sortera rapporten på valfri kolumn, t.ex. **Namn**, **Chassityp** eller **Tillverkare** genom att välja kolumnens rubrik.

### Så här ser du vilka program som är installerade på datorerna

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Rapporter** &gt; **Rapporter med identifierad programvara**

2.  På sidan **Skapa ny rapport** accepterar du standardvärdena eller anpassar dem om du vill filtrera resultatet som rapporten skickar tillbaka. Du kan till exempel välja att endast program som är utgivna av Microsoft ska visas i rapporten.

3.  Välj **Visa rapport** för att öppna **Upptäckta programvarurapporter** i ett nytt fönster.

    Du kan sortera rapporten på valfri kolumn, t.ex. **Namn**, **Utgivare** eller **Kategori** genom att välja kolumnens rubrik. Du kan expandera uppdateringarna i listan om du vill visa mer information (t.ex vilka datorer programmet har installerats på) genom att klicka på pilen bredvid listobjektet.

### Så här uppdaterar du datorinventeringen för att säkerställa att den är aktuell

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator du vill uppdatera inventeringen för).

2.  Välj en dator eller tryck och håll ned **Ctrl** för att välja flera datorer.

3.  Klicka på **Fjärruppgifter** &gt; **Uppdatera inventering** i verktygsfältet.

4.  Om du vill visa aktivitetens status väljer du **Fjärruppgifter** längst ner till höger på sidan.

    Dialogrutan **Aktivitetsstatus** visar aktuella fjärrhanteringsaktiviteter, aktivitetsstatus, enhetsnamn och eventuella rapporterade fel och innehåller en länk till felsökningsinformation.


## Starta om en Windows-dator via en fjärranslutning

1.  I [Microsoft Intune-administrattionskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator du vill starta om).

2.  Välj en eller flera datorer och klicka sedan på **Fjärruppgifter** &gt; **Starta om datorn**

3.  Om du vill visa aktivitetens status väljer du **Fjärruppgifter** längst ner till höger på sidan.

4.  I dialogrutan **Aktivitetsstatus** kan du granska aktuella fjärrhanteringsaktiviteter, aktivitetsstatus, enhetsnamn och eventuella rapporterade fel.

## Dra tillbaka en dator

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator du vill dra tillbaka).

2.  Markera de enheter som du vill dra tillbaka och välj sedan **Dra tillbaka/rensa**

Om du vill återregistrera en dator i Intune installerar du om klientprogrammet på datorn med hjälp av informationen i avsnittet [Installera Windows PC-klienten med Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Om en dator inte kan ansluta till Intune visas ett meddelande i arbetsytan **Instrumentpanel**.

När du drar tillbaka en dator:

-   Tas den bort från Intune-inventeringen och licensen som är kopplad till datorn görs tillgänglig så att den kan användas igen.

-   Visas dess status inte längre i Intune-konsolen.

-   Intune tar bort klientprogrammet från datorn. Om datorn inte är ansluten till Intune-tjänsten tas klientprogrammet bort nästa gång datorn ansluts.

-   Microsoft Endpoint Protection tas bort från datorn. Om datorn har ett annat slutpunktsprogram installerat och det inaktiveras kan programmet aktiveras igen efter att Microsoft Intune Endpoint Protection har tagits bort, så att datorerna skyddas.

-   Principer tas bort från datorn och de värden som angavs av principen kommer att ändras.

-   Datorn kommer inte längre att ta emot programuppdateringar eller uppdaterade definitioner för skadlig programvara från Intune-tjänsten.

-   Beroende på datorernas konfiguration kan de eventuellt fortfarande kan ta emot uppdateringar via Windows Server Update Services, Windows Update eller Microsoft Update.

    > Om klientprogrammet har installerats med en hjälp av ett grupprincipobjekt (GPO), måste du ta bort grupprincipobjektet innan du kan ta bort klientprogrammet, för att förhindra att programvaran installeras på nytt.

    Om det inte går att avinstallera klienten läser du [Felsöka Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) om du behöver mer hjälp.

## Hantera länkning av användarenheter
Innan du kan distribuera programvara till en användare måste du koppla användaren till en dator. Du kan koppla en användare till flera datorer, men varje dator kan bara kopplas till en enda användare. Användarna länkas automatiskt till alla datorer som de registrerar i Intune med hjälp av företagsportalen.

### Så här länkar du en användare till en dator

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator som du vill länka till en användare).

2.  Markera den dator du vill länka till en användare och välj sedan **Länka användare**

    Dialogrutan **Länka användare** visar en lista över tillgängliga användare med deras visningsnamn, användar-ID och hur många datorer som varje användare för närvarande är länkad till. Om en användare redan är länkad till den valda datorn visas användarens namn och användar-ID under **Aktuell användare**. Om datorn inte är länkad till någon användare visas **Ingen användare** under **Aktuell användare**

3.  Gör något av följande:

    -   Om du vill låta datorn fortsätta att vara kopplad till den aktuella användaren, om det finns en sådan, väljer du **Avbryt**

    -   Om du vill ta bort länken till den aktuella användaren, om det finns en sådan, väljer du **Ta bort länk**&gt;**OK**

    -   För att länka datorn till en ny användare väljer du en användare i listan **Alla användare** . Bekräfta att informationen är korrekt och välj sedan **OK**

> Om du vill begränsa slutanvändarnas möjlighet att länka sig själva till datorer aktiverar du alternativet **Begränsa användarnas möjlighet att länka sig själva till datorer** i principen **Agentinställningar för Microsoft Intune**.

## Svara på en begäran om Fjärrhjälp
Användarna kan begära hjälp via Fjärrhjälp med hjälp av Microsoft Easy Assist som installeras automatiskt på hanterade datorer. När en begäran skickas visas en avisering i Intune-konsolen.

> Fjärrhjälp stöds inte på datorer som kör Windows 8 eller senare.
>
> Om du accepterar en begäran om Fjärrhjälp från en dator som inte har Microsoft Easy Assist installerat, uppmanas användaren att installera det. Datorn måste startas om för att installationen ska slutföras. Det kan vara bra att läsa in Microsoft Easy Assist i förväg på användarnas datorer för att undvika denna omstart.

### Så här hanterar du en begäran om Fjärrhjälp

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Aviseringar** &gt; **Fjärrhjälp**

2.  Markera en begäran om Fjärrhjälp i listan **Aviseringar** för att öppna egenskapssidan för begäran.

3.  Välj **Godkänn begäran och starta Fjärrhjälp** för att öppna en dialogruta med alternativ för att åtgärda aviseringen.

4.  Gör något av följande:

    -   **Godkänn begäran** – Om du vill ansluta till fjärrsessionen klickar du på **Godkänn begäran om Fjärrhjälp**

        Användaren ser meddelandet: **Din begäran accepterades. Följ instruktionerna i Easy Assist för att dela ett program eller ditt skrivbord med systemadministratören**

        > Du kan inte acceptera en begäran om Fjärrhjälp på en Mac-dator som kör Intune-administratörskonsolen.

    -   **Neka begäran** – Stäng fönstret **Visa felsökningsinformation** och välj **Stäng den här aviseringen** i fönstret Egenskaper för aviseringen.

        Begäran stängs och användaren ser ett meddelande om att begäran har nekats. För att begära Fjärrhjälp igen måste användaren skicka en ny begäran om Fjärrhjälp. Om du råkar stänga en avisering om Fjärrhjälp måste du kontakta den användare som skickade begäran om Fjärrhjälp och be användaren att skicka en ny begäran.


<!--HONumber=May16_HO2-->


