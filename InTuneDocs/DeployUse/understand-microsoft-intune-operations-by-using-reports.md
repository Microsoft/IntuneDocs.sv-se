---
title: "Förstå aktiviteter med hjälp av rapporter | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 06/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 857309c2-61c9-4c22-becf-4839fedeaece
ms.reviewer: pbala
ms.suite: ems
ms.sourcegitcommit: 617f1cd42de49f0c8675bd450591a390af674e73
ms.openlocfilehash: b8af36cef1bcb9077d0ab611a14fb88c0f458ece


---

# Förstå Microsoft Intune-aktiviteter med hjälp av rapporter
Använd informationen i det här avsnittet om du vill ha hjälp med att skapa och hantera Microsoft Intune-rapporter som tillhandahåller information om programvara, maskinvara och programlicenser i din organisation.

## Använda rapporter
Intune-rapporter tillhandahåller information om programvara, maskinvara och licenser i din organisation. Rapporter kan hjälpa dig att bekräfta aktuella behov och göra prognoser för framtida utgifter. Arbetsytan **Rapporter** ger dig de verktyg du behöver för att skapa och hantera rapporter. Mer information om rapporter finns i [Förstå Microsoft Intune-aktiviteter med hjälp av rapporter](understand-microsoft-intune-operations-by-using-reports.md).

### Rapporttyper

|Rapporttyp|Beskrivning|
|---------------|---------------|
|**Uppdateringsrapporter**|Visar de programuppdateringar som har slutförts på datorer i din organisation, liksom de uppdateringar som har misslyckats, väntar eller som behöver göras. Mer information om programuppdateringar finns i [Hålla datorerna uppdaterade med programvaruuppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).|
|**Rapporter om identifierad programvara**|Visar den programvara som har installerats på datorer i din organisation, med information om programversioner. Du kan filtrera den information som visas utifrån utgivare och programkategori. Du kan expandera uppdateringarna i listan om du vill visa mer information (t.ex vilka datorer programmet har installerats på) genom att klicka på pilen bredvid listobjektet.<br /><br />När du återställer datorer eller ändrar deras gruppmedlemskap i Intune kan det ta flera minuter innan ändringarna återspeglas i rapporten om identifierad programvara. Om du vill ha så korrekt programinformation som möjligt bör du vänta några minuter från det att du har tagit bort datorer eller ändrat deras gruppmedlemskap och till dess att du kör en rapport för identifierad programvara som inkluderar dessa datorer.|
|**Datorinventeringsrapporter**|Visar information om hanterade datorer i din organisation. Använd den här rapporten du planerar maskinvaruinköp och vill veta mer om vilka behov av maskinvara som användarna i din organisation har. Mer information om hur du arbetar med hanterade datorer finns i [Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md).|
|**Rapporter om inventering av mobila enheter**|Visar information om mobila enheter i din organisation. Du kan filtrera den information som visas efter grupptillhörighet, huruvida enheten är jailbroken eller rotad eller efter operativsystem.|
|**Rapporter om licensinköp**|Visar programtitlar för alla licensierade program i de valda licensgrupperna, baserat på deras licensavtal. Om programlicensinformationen inte har uppdaterats på mer än 24 timmar uppdateras den när du skapar en licensrapport. En licensrapport är inte en exakt beräkning av det antal program som används eller bevis på avtalsefterlevnad. Rapporten är ett verktyg som hjälper dig att fatta beslut om volymlicensavtal beslut för din organisation. Intune upptäcker kanske inte alla produkter som kan ha Microsoft-volymlicenser. De tillgängliga filtren är:<br /><br />**Alla avtal**, som visar alla licensierade programvaruprodukter som hanteras av Intune.<br /><br />**Volymlicensavtal**, som endast visar VLSC-programvaruprodukter.<br /><br />**Andra programlicensavtal**, som visar programvaruprodukter som hanteras utanför VLSC.|
|**Licensinstallationsrapporter**|Jämför installerade program på datorer i din organisation med dina aktuella licensavtal enligt VLSC (Volume Licensing Service Center). Filtren är:<br /><br />**Alla avtal**, som visar alla licensierade programvaruprodukter som hanteras av Intune.<br /><br />**Volymlicensavtal**, som endast visar VLSC-programvaruprodukter.<br /><br />**Andra programlicensavtal**, som visar programvaruprodukter som hanteras utanför VLSC.|
|**Villkorsrapporter**|Visa om användarna har accepterat de villkor du distribuerat, och vilken version de har accepterat. Du kan ange upp till tio användare vars godkännande av de villkor som distribuerats till dem visas, eller visa godkännandestatusen för ett visst villkor som distribuerats till dem.|
|**Inkompatibilitetsrapporter för appar**|Visar information om de användare som har installerat appar som finns i din listor över kompatibla och inkompatibla appar. Använd den här rapporten om du vill hitta användare och enheter som inte uppfyller dina apprinciper.|
|**Rapporter om certifikatsefterlevnad**|Visa vilka certifikat som har utfärdats till användare och enheter via SCEP eller PKCS #12 (.PFX). Använd den här rapporten om du vill hitta certifikat som har utfärdats, upphört att gälla eller återkallats.|
|**Rapporter om enhetshistorik**|Visa en historisk logg över tillbakadragna, rensade och borttagna åtgärder. Använd den här rapporten om du vill se vem som tidigare har initierat åtgärder på enheterna.|
|**Hälsoattesteringsrapporter**|Visa hälsotillståndet för mobila enheter.|
|**Rapport för Mac OS X-maskinvara**|Visar information om maskinvara för alla registrerade Mac OS X-enheter i de grupper du väljer. Information om maskinvaruinventering som samlas in från dessa enheter finns i [Förstå dina enheter med inventering i Microsoft Intune](understand-your-devices-with-inventory-in-microsoft-intune.md).|
|**Rapport för Mac OS X-programvara**|Visar program som installeras på alla Mac OS X-enheter i de grupper som du valde. Rapporten innehåller programnamnen (som ett paket-ID), den korta namnversionen (eller eget namn), versionen och antalet enheter som programvaran är installerad på.|

#### Skapa en rapport

1.  Klicka på **Rapporter** i Intune-administrationskonsolen och klicka sedan på den rapporttyp som du vill generera. Rapporttyperna beskrivs i tabellen ovan.

2.  På sidan **Skapa ny rapport** accepterar du standardvärdena eller anpassar dem om du vill filtrera resultatet som rapporten skickar tillbaka. Du kan till exempel välja att endast program som är utgivna av Microsoft ska visas i rapporten om identifierade program.

3.  Öppna rapporten i ett nytt fönster genom att klicka på **Visa rapport** .

Sortera rapporten efter valfri kolumn genom att klicka på respektive kolumnrubrik. I vissa rapporter kan du dessutom utvidga posterna i listan om du vill visa mer information.

## Fler rapportåtgärder
Rapporterna stöder dessutom följande åtgärder:

|Action|Mer information|
|----------|--------------------|
|**Skriv ut**|Klicka på utskriftsikonen i en öppen rapport och följ sedan anvisningarna.|
|**Exportera**|Klicka på exportikonen i en öppen rapport och följ sedan anvisningarna. Du kan exportera en rapport till en CSV- eller HTML-fil.|
|**Spara**|På sidan **Skapa ny rapport** kan varje användare spara upp till 100 rapporter. Konfigurera rapportparametrarna enligt dina behov och klicka sedan på **Spara**, eller **Spara som** om du vill använda ett annat namn.|
|**Läs in**|Klicka på **Läs in** på sidan **Skapa ny rapport** om du vill läsa in en tidigare sparad uppsättning rapportparametrar.|
|**Ta bort**|Välj önskad rapporttyp på arbetsytan **Rapporter** , klicka på **Läs in**och klicka sedan, i listan över rapporter, på borttagningsikonen (x) intill rapporten.|

### Se även
[Övervakning och rapporter med Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)




<!--HONumber=Jun16_HO3-->


