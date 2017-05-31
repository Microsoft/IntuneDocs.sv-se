---
title: "Användning av nätverksbandbredd i Intune | Microsoft Docs"
description: "Användning av nätverksbandbredd i Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0c7f813e00eebc9113ce9e395c02bf8e58e6d15c
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="intune-network-bandwidth-use"></a>Användning av nätverksbandbredd i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Den här vägledningen hjälper Intune-administratörerna att förstå Intune-tjänstens nätverkskrav. Du kan använda den här informationen för att förstå de krav på bandbredd, IP-adress och portinställningar som proxyinställningarna kräver.

## <a name="average-network-traffic"></a>Genomsnittlig nätverkstrafik
I den här tabellen visas den ungefärliga storleken och frekvensen för vanligt innehåll som skickas via nätverket för varje klient.

> [!NOTE]
> För att säkerställa att datorer och mobila enheter får nödvändiga uppdateringar och innehåll från Intune-tjänsten måste de regelbundet vara anslutna till Internet. Hur lång tid det tar att ta emot uppdateringar eller innehåll varierar, men som riktlinje bör de vara kontinuerligt anslutna till Internet minst en timme varje dag.

|Innehållstyp|Ungefärlig storlek|Frekvens och information|
|----------------|--------------------|-------------------------|
|Intune-klientinstallation<br /><br />**Följande krav gäller dessutom vid Intune-klientinstallation**|125 MB|**En gång**<br /><br />Storleken på klienthämtningen varierar beroende på operativsystemet på klientdatorn.|
|Klientregistreringspaket|15 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Endpoint Protection-agent|65 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Operations Manager-agent|11 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Principagent|3 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Fjärrhjälp via Microsoft Easy Assist-agenten|6 MB|**En gång**<br /><br />Ytterligare hämtningar kan utföras när det finns uppdateringar för den här innehållstypen.|
|Dagliga klientaktiviteter|6 MB|**Dagligen**<br /><br />Intune-klienten kommunicerar regelbundet med Intune-tjänsten för att söka efter uppdateringar och principer, samt rapportera klientens status till tjänsten.|
|Definitionsuppdateringar för skadlig kod i Endpoint Protection|Det varierar<br /><br />Vanligtvis 40 KB till 2 MB|**Dagligen**<br /><br />Upp till tre gånger per dag.|
|Uppdatering av Endpoint Protection-motorn|5 MB|**Varje månad**|
|Programuppdateringar|Det varierar<br /><br />Storleken beror på vilka uppdateringar som distribueras.|**Varje månad**<br /><br />Vanligtvis släpps programuppdateringar den andra tisdagen i varje månad.<br /><br />En nyligen registrerad eller distribuerad dator kan använda mer bandbredd i nätverket vid nedladdning av en fullständig uppsättning tidigare uppdateringar.|
|Service Pack|Det varierar<br /><br />Storleken varierar för varje Service Pack som du distribuerar.|**Det varierar**<br /><br />Beror på när du distribuerar Service Packs.|
|Programvarudistribution|Det varierar<br /><br />Storleken beror på vilken programvara som distribueras.|**Det varierar**<br /><br />Beror på när du distribuerar programvaran.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>Sätt att minska användningen av nätverksbandbredd
Du kan använda en eller flera av följande metoder för att minska användningen av nätverksbandbredd för Intune-klienter.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>Använd en proxyserver till att cachelagra innehållsbegäranden
Du kan använda en proxyserver som kan cachelagra innehåll för att minska duplicerade hämtningar och minska användningen av nätverksbandbredd från klienter som begär innehåll från Internet.

En proxyserver med cachelagring tar emot förfrågningar om innehåll från klientdatorer i nätverket, hämtar innehåll från Internet och kan sedan cachelagra både HTTP-svar och binära hämtningar. Servern använder den cachelagrade informationen för att besvara efterföljande förfrågningar från Intune-klientdatorer.

Nedan visas vanliga inställningar för en proxyserver som cachelagrar innehåll för Intune-klienter.

|Inställningar|Rekommenderat värde|Information|
|-----------|---------------------|-----------|
|Cachestorlek|5 GB till 30 GB|Värdet varierar beroende på hur många klientdatorer som finns i nätverket och vilka konfigurationer som du använder. Om du vill förhindra att filer tas bort för tidigt, ändrar du storleken på cacheminnet för din miljö.|
|Storlek för enskilda cachefiler|950 MB|Den här inställningen kanske inte är tillgänglig i alla proxyservrar med cachelagring.|
|Objekttyper som kan cachelagras|HTTP<br /><br />HTTPS<br /><br />BITS|Intune-paket är CAB-filer som hämtas av BITS (Background Intelligent Transfer Service) via HTTP.|
Information om hur du använder en proxyserver till att cachelagra innehåll finns i dokumentationen för din proxyserverlösning.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Använda BITS (Background Intelligent Transfer Service) på datorer
Intune stöder användningen av BITS (Background Intelligent Transfer Service) på en Windows-dator för att minska den nätverksbandbredd som används under de timmar då konfiguration utförs. Du kan konfigurera BITS-principen på sidan **Nätverksbandbredd** i Intune-agentprincipen.

Läs mer om BITS och Windows-datorer i [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) i TechNet-biblioteket.

### <a name="use-branchcache-on-computers"></a>Använda BranchCache på datorer
Intune-klienter kan använda BranchCache för att minska WAN-trafiken (Wide Area Network). Följande operativsystem stöds för klienter som också har stöd för BranchCache:

- Windows 7
- Windows 8.0
- Windows 8,1
- Windows 10

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när Intune-klienten installeras. Men om klienten redan har en grupprincip som inaktiverar BranchCache, åsidosätter inte Intune principen och BranchCache kommer att förbli inaktiverat på datorn.

Om du använder BranchCache bör du kommunicera med andra administratörer i din organisation som hanterar grupprincip och Intune-brandväggsprincip för att säkerställa att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Krav för nätverkskommunikation

Du måste aktivera nätverkskommunikationen mellan de enheter du hanterar och använder för att hantera din Intune-prenumeration, samt de webbplatser som krävs för molnbaserade tjänster.

Intune använder inte någon lokal infrastruktur såsom servrar med Intune-programvara, men det finns alternativ för att använda lokal infrastruktur, inklusive synkroniseringsverktyg för Exchange och Active Directory.

Om du vill hantera datorer som finns bakom brandväggar och proxyservrar måste du ställa in brandväggarna och proxyservrarna så att kommunikation tillåts för Intune. Tänk på följande om du vill hantera datorer som är bakom en proxyserver:

-   Proxyservern måste ha stöd för både **HTTP (80)** och **HTTPS (443)** eftersom Intune-klienter använder båda protokollen
-   Intune stöder oautentiserade proxyservrar

Du kan ändra inställningarna för proxyservern i enskilda klientdatorer, eller använda grupprincipinställningar för att ändra inställningarna för alla klientdatorer bakom en angiven proxyserver.

Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

I följande tabeller visas de portar och tjänster som Intune-klienten har åtkomst till:

|**Domäner**|**IP-adress**|
|---------------------|-----------|
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>enterpriseenrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |    13.64.198.190|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |13.64.188.173|
|fei.msua04.manage.microsoft.com<br> portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com |40.71.32.174|
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |13.64.197.181 |
|fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com |40.71.38.205|
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |13.64.191.182 |
|fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com |40.71.37.51 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |40.118.250.246 |
|fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com |13.90.142.194 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.64.250.226 |
|fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com |13.90.151.142 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.169.155.165 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com |52.174.188.97 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.178.190.24 |
|fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com |52.174.16.215 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |40.69.69.27 |
|fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com |52.166.196.199 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |40.69.71.164 |
|fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com |52.174.182.102 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |40.69.78.145 |
|fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com |52.174.192.105 |
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |13.94.46.250|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com |52.163.119.15 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |13.75.124.145 |
|fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com |52.163.119.5|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.175.35.226|
|fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com |52.163.119.6|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.175.38.24|
|fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com |52.163.119.3|

