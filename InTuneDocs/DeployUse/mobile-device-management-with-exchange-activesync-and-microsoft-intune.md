---
title: Enhetshantering med Exchange ActiveSync | Microsoft Intune
description: "Hantera mobila enheter som användarna inte har registrerat med Exchange ActiveSync-hantering (EAS) med Exchange Connector"
keywords: 
author: nathbarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9cbf5858cc4e860b540f421b6d463b8e7a429cf
ms.openlocfilehash: f545c7db4c29690a72c5a84dfcab6f179cbe72a2


---

# Hantering av mobila enheter med Exchange ActiveSync och Microsoft Intune
För att Microsoft Intune ska hantera mobila enheter direkt måste användare registrera enheter i Intune. För mobila enheter som användare inte har registrerat kan du aktivera Exchange ActiveSync-hantering (EAS) med Exchange Connector. Enheter kan hanteras med lokala Exchange-servrar och molnbaserad Exchange i Microsoft Office 365.

## Exchange-åtkomstregler för mobila enheter ##

Exchange behöver en uppsättning regler som definierar vad som händer när mobila enheter försöker ansluta till EAS. De här reglerna hanteras i Intune-administrationskonsolen.

[Exchange-åtkomstregler för mobila enheter](exchange-access-rules-for-mobile-devices.md)

## Installera Exchange Connector
Med Exchange Connector kan du hantera Exchange-distributionen i Intune-konsolen. Du måste först installera och konfigurera lämplig Intune-till-Exchange-anslutningstjänst. Välj lämpligt alternativ beroende på om Exchange-servern är lokal eller värdbaserad som en tjänst i molnet:

-   [Installera Intune Connector för lokal Exchange](intune-on-premises-exchange-connector.md)
-   [Konfigurera Intune Service To Service Connector för värdbaserad Exchange](intune-service-to-service-exchange-connector.md)

## Använda princip för Exchange-hanterade mobila enheter
Principinställningar kan tillämpas via Intune-konsolen. Mer information finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). En lista över Exchange ActiveSync-principinställningar och -funktioner som stöds av specifika mobila enheter finns i [Jämförelsetabell för Exchange ActiveSync-klienten](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Efter anslutning av Intune till en Microsoft Exchange-miljö återställs EAS-principen för alla användare som hanteras via Intune till den aktuella standardprincipen på Microsoft Exchange-servern, om inte en mer specifik princip har definierats i Intune.

## Rensa företagsdata på mobila enheter
Slutligen kan du [rensa företagsdata på EAS-hanterade mobila enheter](wipe-for-exchange-managed-mobile-devices.md) när de inte längre används, eller om enheter tappas bort eller blir stulna.



<!--HONumber=Jul16_HO4-->


