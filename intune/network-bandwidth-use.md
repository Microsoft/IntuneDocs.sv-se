---
title: Information om nätverkskrav och bandbredd för Microsoft Intune
titleSuffix: ''
description: Granska kraven för nätverkskonfiguration och bandbredd för Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6d5e8d76a06ac45fed2b9759e519ffc7fabf7ec
ms.sourcegitcommit: d2989b9992d10d133573d9bc31479659fb7e242c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71238313"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Krav för Intune-nätverkskonfiguration och bandbredd

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Du kan använda den här informationen för att förstå bandbreddskraven för dina Intune-distributioner.

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

Läs mer om BITS och Windows-datorer i [Background Intelligent Transfer Service](https://technet.microsoft.com/library/bb968799.aspx) i TechNet-biblioteket.

### <a name="delivery-optimization"></a>Leveransoptimering
Med Leveransoptimering kan du använda Intune för att minska bandbreddsförbrukningen när dina Windows 10-enheter laddar ned program och uppdateringar. Genom att använda en självorganiserande distribuerad cache kan nedladdningar hämtas från traditionella servrar och alternativa källor (som nätverks-peer).

Hela listan med Windows 10-versioner och innehållstyper som stöds av Leveransoptimering finns i [artikeln om Leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements).

Du kan [konfigurera Leveransoptimering](delivery-optimization-settings.md) som en del av dina enhetskonfigurationsprofiler.


### <a name="use-branchcache-on-computers"></a>Använda BranchCache på datorer
Intune-klienter kan använda BranchCache för att minska WAN-trafiken (Wide Area Network). BranchCache stöds i följande operativsystem:

- Windows 7
- Windows 8.0
- Windows 8,1
- Windows 10

Om du vill använda BranchCache måste klientdatorn ha BranchCache aktiverat och dessutom vara konfigurerat för **distribuerat cacheläge**.

Som standard aktiveras BranchCache och distribuerat cacheläge på en dator när Intune-klienten installeras. Men om en grupprincip har inaktiverat BranchCache, åsidosätter Intune inte den principen. Det innebär att BranchCache förblir inaktiverad.

Om du använder BranchCache bör du arbeta med andra administratörer i din organisation som hanterar grupprincip och Intune-brandväggsprincip. Kontrollera att de inte distribuerar en princip som inaktiverar BranchCache eller brandväggsundantag. Mer information om BranchCache finns i [BranchCache-översikt](https://technet.microsoft.com/library/hh831696.aspx).

> [!NOTE]
> Du kan använda Microsoft Intune för att hantera Windows-datorer [som mobila enheter med hantering av mobila enheter (MDM)](windows-enroll.md) eller som datorer med Intune-programvaruklienten. Microsoft rekommenderar att kunderna [använder MDM-hanteringslösningen](windows-enroll.md) närhelst det är möjligt. Vid hantering på det här sättet stöds inte BranchCache. Mer information finns i [Jämför hanteringen av Windows-datorer som datorer respektive mobila enheter](pc-management-comparison.md).


## <a name="next-steps"></a>Nästa steg

[Granska slutpunkter för Intune](intune-endpoints.md)

