---
# required metadata

title: Hantering av mobila enheter med Exchange ActiveSync och Microsoft Intune | Microsoft Intune
description:
keywords:
author: nathbarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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
Principinställningar kan tillämpas via Intune-konsolen. Mer information finns i [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). En lista över Exchange ActiveSync-principinställningar och -funktioner som stöds av specifika mobila enheter finns i [Jämförelsetabell för Exchange ActiveSync-klienten](http://go.microsoft.com/fwlink/?LinkId=247270)

> Efter anslutning av Intune till en Microsoft Exchange-miljö återställs EAS-principen för alla användare som hanteras via Intune till den aktuella standardprincipen på Microsoft Exchange-servern, om inte en mer specifik princip har definierats i Intune.

## Rensa företagsdata på mobila enheter
Slutligen kan du [rensa företagsdata på EAS-hanterade mobila enheter](wipe-for-exchange-managed-mobile-devices.md) när de inte längre används, eller om enheter tappas bort eller blir stulna.


<!--HONumber=May16_HO2-->


