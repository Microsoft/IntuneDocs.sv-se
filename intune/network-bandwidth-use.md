---
title: Information om nätverkskrav och bandbredd för Microsoft Intune
titlesuffix: ''
description: Granska kraven för nätverkskonfiguration och bandbredd för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ba4cf212f44742ca9feb077a945a1f500ca1a78
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55840951"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Krav för Intune-nätverkskonfiguration och bandbredd

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Den här vägledningen hjälper Intune-administratörerna att förstå Intune-tjänstens nätverkskrav. Du kan använda den här informationen för att förstå de krav på bandbredd, IP-adress och portinställningar som proxyinställningarna kräver.

## <a name="average-network-traffic"></a>Genomsnittlig nätverkstrafik
I den här tabellen visas den ungefärliga storleken och frekvensen för vanligt innehåll som skickas via nätverket för varje klient.

> [!NOTE]
> För att säkerställa att enheter tar emot uppdateringar och innehåll från Intune måste de regelbundet anslutas till Internet. Hur lång tid det tar att ta emot uppdateringar eller innehåll varierar, men som riktlinje bör de vara kontinuerligt anslutna till Internet minst en timme varje dag.

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
En proxyserver som kan cachelagra innehåll för att minska duplicerade hämtningar och minska användningen av nätverksbandbredd från innehåll från Internet.

En cachelagrande proxyserver som tar emot innehållsbegäranden från klienter kan hämta innehållet och cachelagra både webbsvar och hämtade filer. Servern använder den cachelagrade informationen för att besvara efterföljande förfrågningar från klienter.

Nedan visas vanliga inställningar för en proxyserver som cachelagrar innehåll för Intune-klienter.


|          Inställningen           |           Rekommenderat värde           |                                                                                                  Information                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Cachestorlek         |             5 GB till 30 GB             | Värdet varierar beroende på hur många klientdatorer som finns i nätverket och vilka konfigurationer som du använder. Om du vill förhindra att filer tas bort för tidigt, ändrar du storleken på cacheminnet för din miljö. |
| Storlek för enskilda cachefiler |                950 MB                 |                                                                     Den här inställningen kanske inte är tillgänglig i alla proxyservrar med cachelagring.                                                                     |
|   Objekttyper som kan cachelagras    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune-paket är CAB-filer som hämtas av BITS (Background Intelligent Transfer Service) via HTTP.                                               |

Information om hur du använder en proxyserver till att cachelagra innehåll finns i dokumentationen för din proxyserverlösning.

### <a name="use-background-intelligent-transfer-service-on-computers"></a>Använda BITS (Background Intelligent Transfer Service) på datorer
Intune stöder användningen av BITS (Background Intelligent Transfer Service) på en Windows-dator för att minska den nätverksbandbredd som används under de timmar då konfiguration utförs. Du kan konfigurera BITS-principen på sidan **Nätverksbandbredd** i Intune-agentprincipen.

Läs mer om BITS och Windows-datorer i [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) i TechNet-biblioteket.

### <a name="use-branchcache-on-computers"></a>Använda BranchCache på datorer
Intune-klienter kan använda BranchCache för att minska WAN-trafiken (Wide Area Network). BranchCache stöds i följande operativsystem:

- Windows 7
- Windows 8.0
- Windows 8,1
- Windows 10

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när Intune-klienten installeras. Om en grupprincip har inaktiverat BranchCache, åsidosätter inte Intune den principen varmed BranchCache förblir inaktiverad.

Om du använder BranchCache bör du arbeta med andra administratörer i din organisation som hanterar grupprincip och Intune-brandväggsprincip. Kontrollera att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Krav för nätverkskommunikation

Du måste aktivera nätverkskommunikationen mellan de enheter du hanterar samt de webbplatser som krävs för molnbaserade tjänster.

Intune använder inte någon lokal infrastruktur såsom servrar med Intune-programvara, men det finns alternativ för att använda lokal infrastruktur, inklusive synkroniseringsverktyg för Exchange och Active Directory.

Om du vill hantera datorer bakom brandväggar och proxyservrar måste du aktivera kommunikation för Intune.

-   Proxyservern måste ha stöd för både **HTTP (80)** och **HTTPS (443)** eftersom Intune-klienter använder båda protokollen
-   Intune kräver åtkomst till manage.microsoft.com via oautentiserad proxyserver för åtgärder som t.ex. nedladdning av programvara och uppdateringar

Du kan ändra inställningarna för proxyservern i enskilda klientdatorer, eller använda grupprincipinställningar för att ändra inställningarna för alla klientdatorer bakom en angiven proxyserver.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

I följande tabeller visas de portar och tjänster som Intune-klienten har åtkomst till:

|**Domäner**|**IP-adress**|
|---------------------|-----------|
|login.microsoftonline.com | Läs mer i informationen om [webbadresser och IP-adressintervall för Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |40.86.181.86<br>13.82.59.78<br>13.74.184.100<br>40.68.188.2<br>13.75.42.6<br>52.230.25.184 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>enterpriseenrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 104.40.82.191 <br>13.82.96.212 <br>52.169.9.87 <br>52.174.26.23 <br>40.83.123.72 <br>13.76.177.110 <br>52.234.146.75 |
|portal.fei.msua01.manage.microsoft.com<br>m.fei.msua01.manage.microsoft.com |13.64.196.170|
|fei.msua01.manage.microsoft.com<br> portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com |40.71.34.120 |
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com |13.64.198.190|
|fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br> m.fei.msua02.manage.microsoft.com |  13.64.198.190|
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
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|23.97.165.17|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|enterpriseregistration.windows.net|52.175.211.189|

### <a name="apple-device-network-information"></a>Nätverksinformation för Apple-enhet

|         Värddatornamn         |                                        URL (IP-adress/undernät)                                        |  Protokoll  |     Port     |                          Enhet                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|------------|--------------|-----------------------------------------------------------|
|      Administrationskonsol       |                                  gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |                    Apple iOS och macOS                    |
|      Administrationskonsol       |                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |                    Apple iOS och macOS                    |
|      Administrationskonsol       | Apple iTunesitunes.apple.com, \*.mzstatic.com, \*.phobos.apple.com, \*.phobos.apple.com.edgesuite.net |    HTTP    |      80      |                    Apple iOS och macOS                    |
|        PI-server         |                gateway.push.apple.com(17.0.0.0/8) feedback.push.apple.com(17.0.0.0/8)                 |    TCP     |  2195, 2196  |         För molnmeddelanden med Apple iOS och macOS.          |
|     Enhetstjänster      |                                        gateway.push.apple.com                                         |    TCP     |     2195     |                           Apple                           |
|     Enhetstjänster      |                                        feedback.push.apple.com                                        |    TCP     |     2196     |                           Apple                           |
|     Enhetstjänster      |   Apple iTunesitunes.apple.com \*.mzstatic.com\*.phobos.apple.com \*.phobos.apple.com.edgesuite.net   |    HTTP    |      80      |                           Apple                           |
| Enheter (Internet/Wi-Fi) |                                 #-courier.push.apple.com(17.0.0.0/8)                                  |    TCP     | 5223 och 443 | Endast Apple. &#39;#&#39; är ett slumptal från 0 till 200. |
| Enheter (Internet/Wi-Fi) |                           phobos.apple.comocsp.apple.comax.itunes.apple.com                           | HTTP/HTTPS |  80 eller 443   |                        Endast Apple                         |

