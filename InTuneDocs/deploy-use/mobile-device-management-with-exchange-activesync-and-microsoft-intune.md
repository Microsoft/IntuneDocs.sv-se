---
title: Enhetshantering med Exchange ActiveSync | Microsoft Docs
description: Hantera mobila enheter med Exchange ActiveSync-hantering (EAS) med Exchange Connector
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 4d1fc1af29dbd42c639afe079020d35a92360eb3
ms.lasthandoff: 12/10/2016


---

# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Exchange ActiveSync-hantering av mobila enheter med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

För att Microsoft Intune ska kunna hantera mobila enheter direkt måste enheterna [registreras i Intune](prerequisites-for-enrollment.md). Alternativt kan administratörer aktivera en mer begränsad hanteringslösning som använder Exchange ActiveSync-hantering (EAS) med Exchange Connector. Enheter kan hanteras med lokala Exchange-servrar eller Exchange Online med Office 365. Intune har endast stöd för en Exchange Connector-anslutning av valfri typ per prenumeration.

## <a name="exchange-access-rules-for-mobile-devices"></a>Exchange-åtkomstregler för mobila enheter ##

Exchange behöver en uppsättning regler som definierar vad som händer när mobila enheter försöker ansluta till EAS. De här reglerna hanteras i Intune-administrationskonsolen.

[Exchange-åtkomstregler för mobila enheter](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Installera Exchange Connector
Med Exchange Connector kan du hantera Exchange-distributionen i Intune-konsolen. Du måste först installera och konfigurera lämplig Intune-till-Exchange-anslutningstjänst. Välj lämpligt alternativ beroende på om Exchange-servern är lokal eller om den finns som en tjänst i molnet:

-   [Konfigurera Intune för Exchange Online eller nya Exchange Online Dedicated-miljöer](intune-service-to-service-exchange-connector.md)
-   [Installera Intune Connector för lokala Exchange-servrar och äldre Exchange Online Dedicated-miljöer](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Använda princip för Exchange-hanterade mobila enheter
Intune-konsolen kan användas för att hantera [EAS-principinställningar](exchange-activesync-policy-settings-in-microsoft-intune.md) och [begränsa åtkomsten till företagsresurser](restrict-access-to-email-and-o365-services-with-microsoft-intune.md). En lista över Exchange ActiveSync-principinställningar och Exchange ActiveSync-funktioner som stöds av specifika mobila enheter finns i [Jämförelsetabell för Exchange ActiveSync-klienten](http://go.microsoft.com/fwlink/?LinkId=247270).

> [!NOTE]
> Efter anslutning av Intune till en Microsoft Exchange-miljö återställs EAS-principen för alla användare som hanteras via Intune till den aktuella standardprincipen på Microsoft Exchange-servern, om inte en mer specifik princip har definierats i Intune.

## <a name="wipe-company-data-from-mobile-devices"></a>Rensa företagsdata på mobila enheter
Slutligen kan du [rensa företagsdata på EAS-hanterade mobila enheter](wipe-for-exchange-managed-mobile-devices.md) när de inte längre används, eller om enheter tappas bort eller blir stulna.

