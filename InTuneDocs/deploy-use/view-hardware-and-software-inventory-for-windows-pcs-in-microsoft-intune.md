---
title: "Visa maskin- och programvaruinventering för Windows-datorer | Microsoft Intune"
description: "Så här visar du maskin- och programvaruinformation om Windows-datorer som du hanterar med Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 807599d4a6a979c88732ab969fdecb64552a83d5


---

# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Visa maskin- och programvaruinventering för Windows-datorer

Intune samlar in detaljerad information om de hanterade datorernas maskinvara och programvara. Använd informationen i följande procedurer för att lära dig skapa:

-   En rapport som visar information om maskinvarukapaciteten hos de datorer som du hanterar.

-   En rapport som visar en lista över vilka program som finns installerade på varje dator.

-   Så här uppdaterar du en datorinventering för att säkerställa att data i rapporten är aktuella.

## <a name="to-display-information-about-computers-you-manage"></a>Så här visar du information om de datorer du hanterar

1.  Gå till [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) och välj **Rapporter** &gt; **Datorinventeringsrapporter**.

2.  På sidan **Skapa ny rapport** accepterar du standardvärdena eller anpassar dem om du vill filtrera resultatet som rapporten skickar tillbaka. Du kan till exempel välja att endast de datorer som kör Windows 8.1 ska visas i rapporten.

3.  Välj **Visa rapport** för att öppna **Datorinventeringsrapporter** i ett nytt fönster.

    Du kan sortera rapporten på valfri kolumn, t.ex. **Namn**, **Chassityp** eller **Tillverkare** genom att välja kolumnens rubrik.

## <a name="to-display-software-installed-on-computers-you-manage"></a>Så här visar du vilka program som har installerats på de datorer du hanterar

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) och välj **Rapporter** &gt; **Rapporter om identifierad programvara**.

2.  På sidan **Skapa ny rapport** accepterar du standardvärdena eller anpassar dem om du vill filtrera resultatet som rapporten skickar tillbaka. Du kan till exempel välja att endast program som är utgivna av Microsoft ska visas i rapporten.

3.  Välj **Visa rapport** för att öppna **Upptäckta programvarurapporter** i ett nytt fönster.

    Du kan sortera rapporten på valfri kolumn, t.ex. **Namn**, **Utgivare** eller **Kategori** genom att välja kolumnens rubrik. Du kan expandera uppdateringarna i listan om du vill visa mer information (t.ex. vilka datorer som programmet har installerats på) genom att klicka på riktningspilen bredvid listposten.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>Så här uppdaterar du datorinventeringen för att säkerställa att den är aktuell

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) och välj **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator som du vill uppdatera inventeringen för).

2.  Välj en dator eller tryck och håll ned **Ctrl** för att välja flera datorer.

3.  Klicka på **Fjärruppgifter** &gt; **Uppdatera inventering** i aktivitetsfältet.

4.  Om du vill visa aktivitetens status väljer du **Fjärruppgifter** längst ner till höger på sidan.

    Dialogrutan **Aktivitetsstatus** visar aktuella fjärrhanteringsaktiviteter, aktivitetsstatus, enhetsnamn och eventuella rapporterade fel och innehåller en länk till felsökningsinformation.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->

