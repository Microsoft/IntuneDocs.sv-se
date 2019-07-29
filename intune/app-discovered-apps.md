---
title: Identifierade appar
titleSuffix: Microsoft Intune
description: Lär dig mer om de identifierade appar som Intune hittade på en enhet.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1827375dc1905b5c881f743777a73340f0215e0c
ms.sourcegitcommit: 8023ba7d42e61bd37305c69f52a649cf83bf72e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388519"
---
# <a name="intune-discovered-apps"></a>Intune-identifierade appar

**Intune-identifierade appar** är en lista över identifierade appar på Intune-registrerade enheter i din klientorganisation. Den fungerar som en programvaruinventering för din klient. **Identifierade appar** är en separat rapport från [appinstallationsrapporterna](apps-monitor.md). För personliga enheter samlar Intune aldrig in information om program som inte hanteras. På företagsenheter samlas information om alla slags appar in i rapporten, oavsett om de är hanterade eller inte. Nedan visas en tabell med det förväntade beteendet. I allmänhet uppdateras rapporten var sjunde dag från tidpunkten för registreringen (inte en veckovis uppdatering för hela klientorganisationen). Det enda undantaget till den här uppdateringsperioden är programinformation som samlas in via Intune-hanteringstillägget för Win32-appar, som samlas in var 24:e timme.

## <a name="monitor-discovered-apps-with-intune"></a>Övervaka identifierade appar med Intune

Intune innehåller en lista över identifierade appar på Intune-registrerade enheter i din klientorganisation.

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I fönstret **Intune** väljer du **Klientappar** > **Identifierade appar**.

>[!NOTE]
>Du kan exportera listan över identifierade appar till en CSV-fil genom välja **Exportera** från bladet **Identifierade appar** .

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
| macOS | Alla appar som är installerade på enheten | Alla appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| Android | Endast hanterade appar | Alla appar som är installerade på enheten | Var sjunde dag från enhetsregistreringen |
| Android enterprise | Endast hanterade appar | Endast appar som har installerats i arbetsprofilen | Var sjunde dag från enhetsregistreringen |

Antal appar som identifieras kanske inte matchar statusen för antalet installerade appar. Här är några möjliga orsaker till skillnaden:
- En måländring för en installerad app som hanteras kan göra att antalet installerade appar på statusbladet minskar, men appen rapporteras fortfarande som identifierad.
- Om flera instanser av samma app är mål i en klientorganisation blir antalen olika eftersom användare eller enheter kan överlappa. Varje instans av appen räknar överlappande användare, men det kommer att finnas dubbletter bland de identifierade apparna.
- Identifierade appar och appstatus samlas in under olika tidsintervall, och det här kan leda till avvikelser i antalet appar.

## <a name="next-steps"></a>Nästa steg

- [Apptyper i Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Övervaka appinformation och tilldelningar med Microsoft Intune](apps-monitor.md)
