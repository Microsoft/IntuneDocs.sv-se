---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3645d07fe9a703f182e05bc9a7f9fbb93c413ddc
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816246"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Under utveckling för Microsoft Intune – maj 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Dessutom:

- Om vi tror att du måste vidta åtgärder innan en ändring genomförs publicerar vi ett extra inlägg i Meddelandecenter för Office.
- När en funktion distribueras i produktionsmiljön, antingen som en förhandsversion eller som en allmänt tillgänglig version, flyttas funktionsbeskrivningen från den här sida till [sidan Nyheter](whats-new.md).
- Den här sidan och [sidan Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [M365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!Note]
> Den här informationen återspeglar Microsofts planer gällande Intune-funktioner i kommande versioner. Datum och enskilda funktioner kan ändras. Alla komponenter som är under utveckling har inte en funktionsbeskrivning på den här sidan.

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Baslinjestöd för nyckelordssökning  <!-- 3082036         -->
När du skapar eller redigerar en profil för säkerhetsbaslinjen kommer du snart att kunna använda *sökfunktionen* för att filtrera inställningarna som visas i konsolen.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Återställa och rensa enheter i grupp med hjälp av Graph API <!-- 3295288 -->
Du kommer att kunna återställa och rensa upp till 100 enheter i grupp med Graph API.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Enhetsanvändare kan visa alla hanterade appar som de har installerat eller försökt att installera <!-- 2352913 -->
Företagsportalen för Windows visar alla hanterade appar, både nödvändiga och tillgängliga, som är installerade på en användares enhet. Användare kommer att kunna visa installationsförsök och väntande installationer, och deras aktuella status. Om din organisation inte gör appar obligatoriska eller tillgängliga ser användarna ett meddelande som förklarar att inga företagsappar har installerats. Användarna kommer också att kunna sortera eller filtrera appar baserat på installationsstatus.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Använd ”tillämplighetsregler” när du skapar konfigurationsprofiler för Windows 10-enheter <!-- 2549910 -->
Du skapar konfigurationsprofiler för Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10** som plattform). Du kommer att kunna skapa en **tillämpningsregel** så att profilen endast gäller för en viss utgåva eller en specifik version. Exempelvis kan du skapa en profil som aktiverar vissa BitLocker-inställningar. När du lägger till profilen använder du en tillämpningsregel så att profilen endast gäller för enheter som kör Windows 10 Enterprise.

Gäller för: 
- Windows 10 och senare



## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


