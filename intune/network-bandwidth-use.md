---
title: Information om nätverkskrav och bandbredd för Microsoft Intune
titleSuffix: ''
description: Granska kraven för nätverkskonfiguration och bandbredd för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570799"
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
> [!NOTE]
> Om du använder en proxyserver till att cachelagra innehållsbegäranden, krypteras endast kommunikationen mellan klienten och proxyn och från proxyn till Intune. Anslutningen från klienten till Intune är inte krypterad från slutpunkt till slutpunkt.

Information om hur du använder en proxyserver till att cachelagra innehåll finns i dokumentationen för din proxyserverlösning.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>Använda BITS (Background Intelligent Transfer Service) på datorer
Under den tid då du konfigurerar kan du använda BITS på en Windows-dator för att minska nätverksbandbredden. Du kan konfigurera BITS-principen på sidan **Nätverksbandbredd** i Intune-agentprincipen.

> [!NOTE]
> Vid MDM-hantering i Windows använder bara operativsystemets hanteringsgränssnitt för apptypen MobileMSI BITS för nedladdning. AppX/MsiX använder sin egen nedladdningsstack utan BITS och Win32-appar via Intune-agenten använder leveransoptimering i stället för BITS.

Läs mer om BITS och Windows-datorer i [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx) i TechNet-biblioteket.

### <a name="use-branchcache-on-computers"></a>Använda BranchCache på datorer
Intune-klienter kan använda BranchCache för att minska WAN-trafiken (Wide Area Network). BranchCache stöds i följande operativsystem:

- Windows 7
- Windows 8.0
- Windows 8,1
- Windows 10

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när Intune-klienten installeras. Men om en grupprincip har inaktiverat BranchCache, åsidosätter Intune inte den principen. Det innebär att BranchCache förblir inaktiverad.

Om du använder BranchCache bör du arbeta med andra administratörer i din organisation som hanterar grupprincip och Intune-brandväggsprincip. Kontrollera att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](http://technet.microsoft.com/library/hh831696.aspx).

## <a name="network-communication-requirements"></a>Krav för nätverkskommunikation

Aktivera nätverkskommunikation mellan de enheter som du hanterar, samt de slutpunkter som krävs för molnbaserade tjänster.

Då Intune är en molnbaserad tjänst krävs inte någon lokal infrastruktur, till exempel servrar eller gateways.

Om du vill hantera enheter bakom brandväggar och proxyservrar, måste du aktivera kommunikation för Intune.

- Proxyservern måste ha stöd för både **HTTP (80)** och **HTTPS (443)** eftersom Intune-klienter använder båda protokollen
- För vissa åtgärder (t.ex. nedladdning av programuppdateringar) kräver Intune att det finns en oautentiserad åtkomst till proxyservern för att få åtkomst till manage.microsoft.com

Du kan ändra inställningarna för proxyservern på enskilda klientdatorer. Du kan också använda grupprincipinställningar till att ändra inställningarna för alla klientdatorer som finns bakom en angiven proxyserver.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

Hanterade enheter kräver konfigurationer som låter **Alla användare** komma åt tjänster genom brandväggar.

I följande tabeller visas de portar och tjänster som Intune-klienten har åtkomst till:

|**Domäner**|**IP-adress**|
|---------------------|-----------|
|login.microsoftonline.com | Läs mer i informationen om [webbadresser och IP-adressintervall för Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>enterpriseenrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Nätverksinformation för Apple-enhet


|Används för|Värdnamn (IP-adress/undernät)|Protokoll|Port|
|-----|--------|------|-------|
|Ta emot push-meddelanden från Intune-tjänsten via Apple Push Notification Service (APNS). Se Apples dokumentation [här](https://support.apple.com/en-us/HT203609)|                                    gateway.push.apple.com (17.0.0.0/8)                                  |    TCP     |     2195     |
|Skicka feedback till Intune-tjänsten via Apple Push Notification Service (APNS)|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Hämta och visa innehåll från Apple-servrar|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|Kommunikation med APNS-servrar|#-courier.push.apple.com (17.0.0.0/8)<br>”#” är ett slumpmässigt tal från 0 till 50.|    TCP     |  5223 och 443  |
|Olika funktioner, bland annat åtkomst till Internet, iTunes-butiken, macOS App Store, iCloud, meddelanden etc. |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 eller 443   |

Mer information finns i Apples [TCP- och UDP-portar som används av Apples programprodukter](https://support.apple.com/en-us/HT202944), [Om macOS, iOS och iTunes serveranslutningar för värden och iTunes bakgrundsprocesser](https://support.apple.com/en-us/HT201999) och [Om dina macOS- och iOS-klienter inte kommer åt Apples push-meddelanden](https://support.apple.com/en-us/HT203609).
