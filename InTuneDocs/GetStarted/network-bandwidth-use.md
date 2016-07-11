---
title: "Användning av nätverksbandbredd i Intune | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: e104dc52a8a9bdda4b2edb2939d8c7c36e8ecc12


---

# Användning av nätverksbandbredd i Intune

Innan du konfigurerar [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] går du igenom det här avsnittet och andra krav som anges i [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Använd informationen i följande avsnitt när du planerar nätverkstrafiken för [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-klienter.

## Genomsnittlig nätverkstrafik
I följande tabell visas ungefärlig storlek och frekvens för vanligt innehåll som skickas via nätverket för varje klient.

> [!NOTE]
> För att säkerställa att datorer och mobila enheter får nödvändiga uppdateringar och innehåll från [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-tjänsten måste de regelbundet vara anslutna till Internet. Hur lång tid det tar att ta emot uppdateringar eller innehåll varierar, men som riktlinje bör de vara kontinuerligt anslutna till Internet minst en timme varje dag.

|Innehållstyp|Ungefärlig storlek|Frekvens och information|
|----------------|--------------------|-------------------------|
|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -klientinstallation<br /><br />**Följande krav gäller dessutom vid [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klientinstallation**|125 MB|**En gång**<br /><br />Storleken på klienthämtningen varierar beroende på operativsystemet på klientdatorn.|
|Klientregistreringspaket|15 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Endpoint Protection-agent|65 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Operations Manager-agent|11 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Principagent|3 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Fjärrhjälp via Microsoft Easy Assist-agenten|6 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Dagliga klientaktiviteter|6 MB|**Dagligen**<br /><br />[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klienten kommunicerar regelbundet med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-tjänsten för att söka efter uppdateringar och principer, samt rapportera klientens status till tjänsten.|
|Definitionsuppdateringar för skadlig kod i Endpoint Protection|Det varierar<br /><br />Vanligtvis 40 KB till 2 MB|**Dagligen**<br /><br />Upp till tre gånger per dag.|
|Uppdatering av Endpoint Protection-motorn|5 MB|**Varje månad**|
|Programuppdateringar|Det varierar<br /><br />Storleken beror på vilka uppdateringar som distribueras.|**Varje månad**<br /><br />Vanligtvis släpps programuppdateringar den andra tisdagen i varje månad.<br /><br />En nyligen registrerad eller distribuerad dator kan använda mer bandbredd i nätverket vid nedladdning av en fullständig uppsättning tidigare uppdateringar.|
|Service Pack|Det varierar<br /><br />Storleken varierar för varje Service Pack som du distribuerar.|**Det varierar**<br /><br />Beror på när du distribuerar Service Packs.|
|Programvarudistribution|Det varierar<br /><br />Storleken beror på vilken programvara som distribueras.|**Det varierar**<br /><br />Beror på när du distribuerar programvaran.|

## Sätt att minska användningen av nätverksbandbredd
Du kan använda en eller flera av följande metoder för att minska användningen av nätverksbandbredd för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klienter.

### Använd en proxyserver till att cachelagra innehållsbegäranden
Du kan använda en proxyserver som kan cachelagra innehåll för att minska duplicerade hämtningar och minska användningen av nätverksbandbredd från klienter som begär innehåll från Internet.

En proxyserver med cachelagring tar emot förfrågningar om innehåll från klientdatorer i nätverket, hämtar innehåll från Internet och kan sedan cachelagra både HTTP-svar och binära hämtningar. Servern använder den cachelagrade informationen för att besvara efterföljande förfrågningar från [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klientdatorer.

Nedan visas vanliga inställningar för en proxyserver som cachelagrar innehåll för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klienter.

|Inställningar|Rekommenderat värde|Information|
|-----------|---------------------|-----------|
|Cachestorlek|5 GB till 30 GB|Värdet varierar beroende på hur många klientdatorer som finns i nätverket och vilka konfigurationer som du använder. Om du vill förhindra att filer tas bort för tidigt, ändrar du storleken på cacheminnet för din miljö.|
|Storlek för enskilda cachefiler|950 MB|Den här inställningen kanske inte är tillgänglig i alla proxyservrar med cachelagring.|
|Objekttyper som kan cachelagras|HTTP<br /><br />HTTPS<br /><br />BITS|[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -paket är CAB-filer som hämtas av BITS (Background Intelligent Transfer Service) via HTTP.|
Information om hur du använder en proxyserver till att cachelagra innehåll finns i dokumentationen för din proxyserverlösning.

### Använda BITS (Background Intelligent Transfer Service) på datorer
[!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] stöder användningen av BITS (Background Intelligent Transfer Service) på en Windows-dator för att minska den nätverksbandbredd som används under de timmar då konfiguration utförs. Du kan konfigurera BITS-principen på sidan **Nätverksbandbredd** i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-agentprincipen.

Läs mer om BITS och Windows-datorer i [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) i TechNet-biblioteket.

### Använda BranchCache på datorer
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] -klienter kan använda BranchCache för att minska WAN-trafiken (Wide Area Network). Följande operativsystem stöds för klienter som också har stöd för BranchCache:

-   [!INCLUDE[nextref_client_7](../includes/nextref_client_7_md.md)]

-   [!INCLUDE[win8_client_2](../includes/win8_client_2_md.md)]

-   [!INCLUDE[winblue_client_2](../includes/winblue_client_2_md.md)]

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-klienten installeras. Men om klienten redan har en grupprincip som inaktiverar BranchCache, åsidosätter inte [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] principen och BranchCache kommer att förbli inaktiverat på datorn.

Om du använder BranchCache bör du kommunicera med andra administratörer i din organisation som hanterar grupprincip och [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-brandväggsprincip för att säkerställa att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](http://technet.microsoft.com/library/hh831696.aspx).

### Se även
[Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=Jun16_HO4-->


