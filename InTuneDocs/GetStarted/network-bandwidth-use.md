---
title: "Användning av nätverksbandbredd i Intune | Microsoft Intune"
description: "Användning av nätverksbandbredd i Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: bee350eb0e371133f639fcd0dfb1eafc71775659


---

# <a name="intune-network-bandwidth-use"></a>Användning av nätverksbandbredd i Intune

Innan du konfigurerar Microsoft Intune går du igenom det här avsnittet och andra krav som anges i [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Använd informationen i följande avsnitt när du planerar nätverkstrafiken för Microsoft Intune-klienter.

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
- Windows 8,1
- Windows 10

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när Intune-klienten installeras. Men om klienten redan har en grupprincip som inaktiverar BranchCache, åsidosätter inte Intune principen och BranchCache kommer att förbli inaktiverat på datorn.

Om du använder BranchCache bör du kommunicera med andra administratörer i din organisation som hanterar grupprincip och Intune-brandväggsprincip för att säkerställa att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Krav för nätverkskommunikation

Du måste aktivera nätverkskommunikationen mellan de enheter du hanterar och använder för att hantera din Intune-prenumeration, samt de webbplatser som krävs för molnbaserade tjänster.

Intune använder inte någon lokal infrastruktur såsom servrar med Intune-programvara, men det finns alternativ för att använda lokal infrastruktur, inklusive synkroniseringsverktyg för Exchange och Active Directory.

Om du vill hantera datorer som finns bakom brandväggar och proxyservrar måste du ställa in brandväggarna och proxyservrarna så att kommunikation tillåts för Intune.

### <a name="requirements-for-proxy-servers"></a>Krav för proxyservrar
Tänk på följande om du vill hantera datorer som är bakom en proxyserver:

-   Proxyservern måste ha stöd för både **HTTP** och **HTTPS** eftersom Intune-klienter använder båda protokollen
-   Intune stöder oautentiserade proxyservrar

Du kan ändra inställningarna för proxyservern i enskilda klientdatorer, eller använda grupprincipinställningar för att ändra inställningarna för alla klientdatorer bakom en angiven proxyserver.

### <a name="requirements-for-firewalls-ports-and-domains"></a>Krav för brandväggar och portar och domäner
Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

I följande tabell visas de portar och tjänster som Intune-klienten har åtkomst till.

|**Domän**|**Portar**|**IP-adress**|
|------|----|---|
|manage.microsoft.com<br>a.manage.microsoft.com<br>admin.manage.microsoft.com<br>enterpriseenrollment.manage.microsoft.com<br>enterpriseenrollment-s.manage.microsoft.com<br>i.manage.microsoft.com<br>m.manage.microsoft.com<br>p.manage.microsoft.com<br>portal.manage.microsoft.com<br>r.manage.microsoft.com|80 och 443|134.170.168.254<br>134.170.51.126
|account.manage.microsoft.com|80 och 443|157.56.13.59
|fef.msua01.manage.microsoft.com|80 och 443|138.91.243.97
|fef.msua02.manage.microsoft.com|80 och 443|23.96.112.46
|fef.msua04.manage.microsoft.com|80 och 443|23.96.112.28
|fef.msua05.manage.microsoft.com|80 och 443|138.91.244.151
|fef.msub01.manage.microsoft.com|80 och 443|137.135.128.214
|fef.msub02.manage.microsoft.com|80 och 443|137.135.130.29
|fef.msub03.manage.microsoft.com|80 och 443|23.97.165.17
|fef.msub05.manage.microsoft.com|80 och 443|23.97.166.52
|fef.msuc01.manage.microsoft.com|80 och 443|207.46.225.1
|fef.msuc02.manage.microsoft.com|80 och 443|23.98.66.118
|fef.msuc03.manage.microsoft.com|80 och 443|23.101.0.100
|fef.msuc05.manage.microsoft.com|80 och 443|207.46.154.33
|fef.msua06.manage.microsoft.com|80 och 443|104.42.188.1
|fei.msua01.manage.microsoft.com|80 och 443|138.91.240.131
|fei.msua02.manage.microsoft.com|80 och 443|23.96.112.143
|fei.msua04.manage.microsoft.com|80 och 443|23.96.112.147
|fei.msua05.manage.microsoft.com|80 och 443|138.91.240.163
|fei.msub01.manage.microsoft.com|80 och 443|137.135.130.85
|fei.msub02.manage.microsoft.com|80 och 443|137.135.132.149
|fei.msub03.manage.microsoft.com|80 och 443|23.97.160.232
|fei.msub05.manage.microsoft.com|80 och 443|23.97.162.250
|fei.msuc01.manage.microsoft.com|80 och 443|207.46.224.73
|fei.msuc02.manage.microsoft.com|80 och 443|23.98.66.194
|fei.msuc03.manage.microsoft.com|80 och 443|23.101.2.105
|fei.msuc05.manage.microsoft.com|80 och 443|207.46.147.126
|fei.msua06.manage.microsoft.com|80 och 443|138.91.149.190
|m.fei.msua01.manage.microsoft.com|80 och 443|138.91.240.131
|m.fei.msua02.manage.microsoft.com|80 och 443|23.96.112.143
|m.fei.msua04.manage.microsoft.com|80 och 443|23.96.112.147
|m.fei.msua05.manage.microsoft.com|80 och 443|138.91.240.163
|m.fei.msub01.manage.microsoft.com|80 och 443|137.135.130.85
|m.fei.msub02.manage.microsoft.com|80 och 443|137.135.132.149
|m.fei.msub03.manage.microsoft.com|80 och 443|23.97.160.232
|m.fei.msub05.manage.microsoft.com|80 och 443|23.97.162.250
|m.fei.msuc01.manage.microsoft.com|80 och 443|207.46.224.73
|m.fei.msuc02.manage.microsoft.com|80 och 443|23.98.66.194
|m.fei.msuc03.manage.microsoft.com|80 och 443|23.101.2.105
|m.fei.msuc05.manage.microsoft.com|80 och 443|207.46.147.126
|m.fei.msua06.manage.microsoft.com|80 och 443|138.91.149.190
|m.msua01.manage.microsoft.com|80 och 443|157.55.50.182
|m.msua02.manage.microsoft.com|80 och 443|134.170.49.121
|m.msua04.manage.microsoft.com|80 och 443|134.170.49.126
|m.msua05.manage.microsoft.com|80 och 443|157.55.240.190
|m.msua06.manage.microsoft.com|80 och 443|134.170.49.114
|m.msub01.manage.microsoft.com|80 och 443|94.245.121.50
|m.msub02.manage.microsoft.com|80 och 443|94.245.121.58
|m.msub03.manage.microsoft.com|80 och 443|94.245.121.56
|m.msub05.manage.microsoft.com|80 och 443|157.56.113.123
|m.msuc01.manage.microsoft.com|80 och 443|104.44.84.187
|m.msuc02.manage.microsoft.com|80 och 443|104.44.84.188
|m.msuc03.manage.microsoft.com|80 och 443|104.44.84.189
|m.msuc05.manage.microsoft.com|80 och 443|111.221.76.60
|msua01.manage.microsoft.com|80 och 443|157.55.50.182
|msua02.manage.microsoft.com|80 och 443|134.170.49.121
|msua04.manage.microsoft.com|80 och 443|134.170.49.126
|msua05.manage.microsoft.com|80 och 443|157.55.240.190
|msub01.manage.microsoft.com|80 och 443|94.245.121.50
|msub02.manage.microsoft.com|80 och 443|94.245.121.58
|msub03.manage.microsoft.com|80 och 443|94.245.121.56
|msub05.manage.microsoft.com|80 och 443|157.56.113.123
|msuc01.manage.microsoft.com|80 och 443|104.44.84.187
|msuc02.manage.microsoft.com|80 och 443|104.44.84.188
|msuc03.manage.microsoft.com|80 och 443|104.44.84.189
|msuc05.manage.microsoft.com|80 och 443|111.221.76.60
|msua06.manage.microsoft.com|80 och 443|134.170.49.114
|ncufun.account.manage.microsoft.com|80 och 443|157.55.252.224
|neufun.account.manage.microsoft.com|80 och 443|65.52.229.134
|portal.fei.msua01.manage.microsoft.com|80 och 443|138.91.240.131
|portal.fei.msua02.manage.microsoft.com|80 och 443|23.96.112.143
|portal.fei.msua04.manage.microsoft.com|80 och 443|23.96.112.147
|portal.fei.msua05.manage.microsoft.com|80 och 443|138.91.240.163
|portal.fei.msub01.manage.microsoft.com|80 och 443|137.135.130.85
|portal.fei.msub02.manage.microsoft.com|80 och 443|137.135.132.149
|portal.fei.msub03.manage.microsoft.com|80 och 443|23.97.160.232
|portal.fei.msub05.manage.microsoft.com|80 och 443|23.97.162.250
|portal.fei.msuc01.manage.microsoft.com|80 och 443|207.46.224.73
|portal.fei.msuc02.manage.microsoft.com|80 och 443|23.98.66.194
|portal.fei.msuc03.manage.microsoft.com|80 och 443|23.101.2.105
|portal.fei.msuc05.manage.microsoft.com|80 och 443|207.46.147.126
|portal.fei.msua06.manage.microsoft.com|80 och 443|138.91.149.190
|portal.msua01.manage.microsoft.com|80 och 443|157.55.50.182
|portal.msua02.manage.microsoft.com|80 och 443|134.170.49.121
|portal.msua04.manage.microsoft.com|80 och 443|134.170.49.126
|portal.msua05.manage.microsoft.com|80 och 443|157.55.240.190
|portal.msub01.manage.microsoft.com|80 och 443|94.245.121.50
|portal.msub02.manage.microsoft.com|80 och 443|94.245.121.58
|portal.msub03.manage.microsoft.com|80 och 443|94.245.121.56
|portal.msub05.manage.microsoft.com|80 och 443|157.56.113.123
|portal.msuc01.manage.microsoft.com|80 och 443|104.44.84.187
|portal.msuc02.manage.microsoft.com|80 och 443|104.44.84.188
|portal.msuc03.manage.microsoft.com|80 och 443|104.44.84.189
|portal.msuc05.manage.microsoft.com|80 och 443|111.221.76.60
|portal.msua06.manage.microsoft.com|80 och 443|134.170.49.114
|ssu2.manage.microsoft.com|80 och 443|157.55.99.181
|status.manage.microsoft.com|80 och 443|157.55.99.170
|swda01.manage.microsoft.com<br>swda02.manage.microsoft.com<br>swdb01.manage.microsoft.com<br>swdb02.manage.microsoft.com<br>swdc01.manage.microsoft.com<br>swdc02.manage.microsoft.com|80 och 443|93.184.215.200
|*.microsoftonline-p.com|80 och 443||
|has.spserv.microsoft.com<br>Krävs för hälsoattesteringstjänst för enheter|443||
|*.microsoftonline-p.net|80 och 443||
|*.portal.office.com|80 och 443||
|*.spynet2.microsoft.com|443||
|c.microsoft.com|80 och 443||
|c1.microsoft.com|80 och 443||
|blob.core.windows.net|80 och 443||
|ajax.aspnetcdn.com|80 och 443||
|*.googleapis.com<br>Den här domänen krävs för JQuery-stöd när du använder webbplatsen för företagsportalen.|80 och 443||
|wustat.microsoft.com|80 och 443||
|Microsoft Update-tjänster|\*.update.microsoft.com<br>download.microsoft.com<br>update.microsoft.com<br>\*.download.windowsupdate.com<br>download.windowsupdate.com<br>\*.windowsupdate.com<br>windowsupdate.microsoft.com<br>ntservicepack.microsoft.com|80 och 443|
|DNS-sökningsbegäranden|manage.microsoft.com.nsatc.net|80|
|Samsung KNOX Standard-enhetskommunikation genom brandväggen|Om du vill att Samsung KNOX Standard-enheterna ska kontakta KNOX Standard-servrarna genom brandväggen följer du anvisningarna i Vanliga frågor och svar om Samsung KNOX Standard.||
|Kommunikation för villkorlig åtkomst|443|204.79.197.200|
|Dokumentation, hjälp och support:</br></br>*.livemeeting.com<br>\*.microsoftonline.com<br>\*.social.technet.microsoft.com<br>blogs.technet.com<br>go.microsoft.com<br>onlinehelp.microsoft.com<br>www.microsoft.com|80|||



<!--HONumber=Nov16_HO4-->


