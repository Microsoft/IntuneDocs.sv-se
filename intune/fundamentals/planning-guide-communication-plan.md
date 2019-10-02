---
title: Utveckla en kommunikationsplan för distribution
titleSuffix: Microsoft Intune
description: Den här artikeln hjälper dig att utveckla en kommunikationsplan för din Microsoft Intune-distribution.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/30/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 393ebe75-d001-485a-b81c-6361c8b5e6ee
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1882a9d196cd9877cde37e9d7ef280b718b470cb
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727395"
---
# <a name="develop-a-rollout-communication-plan"></a>Utveckla en kommunikationsplan för distribution

Bra ändringshantering förlitar sig på tydlig och hjälpsam kommunikation om kommande ändringar. Om du vill göra Intune-distributionen smidigare bör din kommunikationsplan för distributionen täcka fyra områden:

- Vilken information som ska förmedlas

- Leveransmetod som används för kommunikationen

- Mottagaren av kommunikationen

- Tidslinje för kommunikation

Vi ska gå igenom varje område mer detaljerat.

## <a name="what-needs-to-be-communicated"></a>Vad behöver förmedlas?

Vilken information som ska förmedlas beror på när i Intune-distributionsprocessen som kommunikationen sker. Du kanske väljer att kommunicera i vågor till dina organisationsgrupper och användare, med början i en kickoff för Intune-distributionen, följt av information före registreringen och information efter registreringen. Vi ska nu ta upp vilken typ av information som kan förmedlas i varje våg.

**Kickoff-våg** <br/>Bred kommunikation som presenterar själva Intune-projektet. Innehållet i kommunikationen ska svara på frågor som Vad är Intune? och Varför har organisationen börjat använda Intune? (fördelarna för organisationen och användarna). Informationen ska också ge en översiktlig plan för distributionen.

**Våg före registreringen**<br/> Bred kommunikation som omfattar ytterligare information om Intune och kompletterande erbjudanden (t.ex. Office, Outlook, OneDrive), användarresurser och specifika tidslinjer för när organisationsgrupper och användare ska få Intune enligt planen.

**Registreringsvåg**<br/> Kommunikation riktad till organisationsgrupper och användare som är schemalagda för att få Intune. Innehållet i kommunikationen bör informera användarna om att de är redo att ta emot Intune och tillhandahålla registreringsanvisningar tillsammans med kontaktinformation om de behöver hjälp eller vill ställa frågor.

**Våg efter registreringen**<br/> Kommunikation riktad till organisationsgrupper och användare som har registrerat sig i Intune. Innehållet i kommunikationen ska tillhandahålla ytterligare resurser som kan vara användbara för användaren samt samla feedback om deras upplevelser under och efter registreringen.

Du kanske tycker att detta [Intune Adoption Kit](https://aka.ms/IntuneAdoptionKit) är användbart. Du kan använda det som det är eller anpassa det för din organisation.

## <a name="communication-delivery-methods"></a>Leveransmetoder för kommunikation

Det finns flera leveransmetoder som kan användas för att förmedla information om Intune-distribution till de organisationsgrupper och användare du riktar in dig på. I följande lista visas några exempel och för vilken våg du kan använda metoden:

- Organisationsomfattande personliga möten eller Microsoft Teams-möten används för kickoff-vågen

- E-post används för förregistrerings-, registrerings- och efterregistreringsvågorna

- Organisationens webbplatser används för alla vågor

- Yammer, affischer och informationsblad används för förregistrerings- och kickoff-vågorna

## <a name="communications-timeline"></a>Tidsplan för kommunikation

När du har fastställt vad du behöver förmedla och vilka metoder du ska använda fastställer du tidslinjen för kommunikationerna som inkluderar vem som ska få kommunikationen och när.

Den första kickoff-informationen om Intune-projektet kan exempelvis rikta in sig på hela organisationen eller bara en del, och kan ske under flera veckor innan Intune-distributionen börjar. Efter det kan information förmedlas i vågor till organisationsgrupper och användare, anpassat efter deras schema för Intune-distributionen. Här visas ett exempel på en utförlig kommunikationsplan för Intune-distribution:

  | **Kommunikationsplan** | **Juli** | **Augusti** | **September** | **Oktober** |
|:---:|:---:|:---:|:---:|:---:|
| Våg 1  | Alla |  |  |  |
| Kickoff-möte | Första veckan |  |  |  |
| Våg 2 | IT | Försäljning och marknadsföring | Återförsäljning | Personalavdelningen, ekonomiavdelningen och chefer |
| E-post före distribution 1 | Första veckan | Första veckan | Första veckan | Första veckan |
| Våg 3 | IT | Försäljning och marknadsföring | Återförsäljning | Personalavdelningen, ekonomiavdelningen och chefer |
| E-post före distribution 2 | Andra veckan | Andra veckan | Andra veckan | Andra veckan |
| Våg 4 | IT | Försäljning och marknadsföring | Återförsäljning | Personalavdelningen, ekonomiavdelningen och chefer |
| E-post om registrering | Tredje veckan | Tredje veckan | Tredje veckan | Tredje veckan |
| Våg 5 | IT | Försäljning och marknadsföring | Återförsäljning | Personalavdelningen, ekonomiavdelningen och chefer |
| E-post efter registrering | Fjärde veckan | Fjärde veckan | Fjärde veckan | Fjärde veckan |

Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att utveckla din kommunikationsplan.

## <a name="next-step"></a>Nästa steg

Nästa avsnitt innehåller råd om att [utveckla en supportplan](planning-guide-support-plan.md).
