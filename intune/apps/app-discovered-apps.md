---
title: Identifierade appar
titleSuffix: Microsoft Intune
description: Lär dig mer om de identifierade appar som Intune hittade på en enhet.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2e7c9824711ecbfb43a7c7dde71cc01b306b7fab
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899417"
---
# <a name="intune-discovered-apps"></a>Intune-identifierade appar

**Intune-identifierade appar** är en lista över identifierade appar på Intune-registrerade enheter i din klientorganisation. Den fungerar som en programvaruinventering för din klient. **Identifierade appar** är en separat rapport från [appinstallationsrapporterna](apps-monitor.md). För personliga enheter samlar Intune aldrig in information om program som inte hanteras. På företagsenheter samlas information om alla slags appar in i rapporten, oavsett om de är hanterade eller inte. Nedan visas en tabell med det förväntade beteendet. I allmänhet uppdateras rapporten var sjunde dag från tidpunkten för registreringen (inte en veckovis uppdatering för hela klientorganisationen). Det enda undantaget till den här uppdateringsperioden är programinformation som samlas in via Intune-hanteringstillägget för Win32-appar, som samlas in var 24:e timme.

## <a name="monitor-discovered-apps-with-intune"></a>Övervaka identifierade appar med Intune

Intune tillhandahåller en sammanställd lista över detekterade appar på Intune-registrerade enheter på din klient.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Övervaka** > **Identifierade appar**.

>[!NOTE]
>Du kan exportera listan över identifierade appar till en CSV-fil genom välja **Exportera** i fönstret **Identifierade appar**.
>
>För upptäckta Win32-appar finns det för tillfället inget sammanlagt antal. Den här typen av data kan endast visas på specifika enheter.

Intune tillhandahåller dessutom en lista över upptäckta appar för den individuella enheten på din klient.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Alla enheter**.
3. Välj en enhet.
4. Om du vill visa identifierade appar för den här enheten väljer du **Identifierade appar** från området **Övervaka**.

## <a name="details-of-discovered-apps"></a>Information om identifierade appar

Följande lista innehåller appens plattformstyp, de appar som övervakas för personliga enheter, de appar som övervakas för företagsägda enheter och uppdateringscykeln. Mer information om vilka typer av appar som stöds av Intune finns i [Apptyper i Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Plattform | För personligt ägda enheter | För företagsägda enheter | Uppdateringscykel |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Windows 10 (Win32-appar) Obs! [Intune-hanteringstillägget krävs](intune-management-extension.md) på enheten | Ej tillämpligt | Alla Win32-appar som hittas i listan Lägg till eller ta bort program | Var 24:e timme från enhetsregistreringen |
| Windows 10 (moderna appar) | Endast hanterade moderna appar | Alla moderna appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| Windows 8,1 | Endast hanterade appar | Endast hanterade appar | Var sjunde dag från enhetsregistreringen |
| Windows Phone 8 | Endast hanterade appar | Endast hanterade appar | Var sjunde dag från enhetsregistreringen |
| Windows RT | Endast hanterade appar | Endast hanterade appar | Var sjunde dag från enhetsregistreringen |
| iOS | Endast hanterade appar | Alla appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| macOS | Endast hanterade appar | Alla appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| Android | Endast hanterade appar | Alla appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| Android enterprise | Endast hanterade appar | Endast appar som har installerats i arbetsprofilen | Var sjunde dag från enhetsregistreringen |

> [!NOTE]
> - Windows 10 Hybrid Azure AD-anslutna enheter som visas i apphanteringsarbetsbelastningen i konfigurationshanteraren samlar för närvarande inte in appinventering via Intune-hanteringstillägget enligt schemat ovan. För att undvika det här problemet bör arbetsbelastningen för apphantering i konfigurationshanteraren växlas till Intune för att installera IME på enheten (IME krävs för Win32-inventering och PowerShell-distribution). Observera att ändringar eller uppdateringar av det här beteendet presenteras i [under utveckling](../fundamentals/in-development.md) och/eller [vad som är nytt](../fundamentals/whats-new.md).
> - Personligt ägda macOS-enheter som registrerats före november 2019 kan fortsätta att visa alla appar som är installerade på enheten tills enheterna har registrerats igen.

Antal appar som identifieras kanske inte matchar statusen för antalet installerade appar. Här är några möjliga orsaker till skillnaden:

- En måländring för en installerad hanterad app kan medföra att antalet installerade appar i statusfönstret minskar, samtidigt som de fortfarande rapporteras som identifierade appar.
- Om flera instanser av samma app är mål i en klientorganisation blir antalen olika eftersom användare eller enheter kan överlappa. Varje instans av appen räknar överlappande användare, men det kommer att finnas dubbletter bland de identifierade apparna.
- Identifierade appar och appstatus samlas in under olika tidsintervall, och det här kan leda till avvikelser i antalet appar.

## <a name="next-steps"></a>Nästa steg

- [Apptyper i Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md)
