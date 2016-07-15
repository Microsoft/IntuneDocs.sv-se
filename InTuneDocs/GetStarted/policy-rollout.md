---
title: Principdistribution | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 390d5adf-86d2-4e23-ba93-1e61e6b1028b
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d82d0ae4820d2e2141848235b8741abccaec3bc6
ms.openlocfilehash: 8935fbc42d7b406a5bcdbfc4353209b4447ae413


---

# Principdistribution
Det här avsnittet innehåller specifika rekommendationer för en fasindelad distribution av principer i Microsoft Intune. Den här metoden gäller för de första principerna som du tillämpar i en ny Intune-distribution eller principer som du lägger till i en befintlig distribution.

Allmän information om distributionsfaser finns i [Distributionsfaser för distribution av Microsoft Intune](rollout-phases-for-microsoft-intune-deployment.md).

### Faser i principdistribution
Faserna i principdistribution är:

-   Projektomfång

-   Konceptbevis

-   Pilot

-   Företagsomfattande distribution

-   Åtgärder och underhåll

## Projektomfång
Definiera omfånget för Intune-principdistributionen:

-   För en ny implementering kräver detta att du definierar önskade enhetsbeteenden och säkerhetskrav som du vill skapa med principuppsättningen.

-   Bestäm vilka användare och enheter som du vill påverka med dessa principer.

-   Designa användar- och enhetsgrupperna så att du kan tillämpa de nya principerna på ett lämpligt sätt.

-   Kontrollera om det finns begränsningar eller krav för varje operativsystem som påverkar principens syfte.

-   Fundera på detaljer för principdesign, till exempel vilken principtyp och mall som ska användas.

-   Oavsett om du lanserar den första uppsättningen med principer eller lägger till nya principer i en befintlig principuppsättning, bör du tänka på hur olika principer interagerar och det sannolika enhetsbeteendet. Problem med principinteraktioner och -konflikter kan identifieras i pilotfasen, men identifiering av principkonflikter under tidig planering förenklar utförande av piloten.

## Konceptbevis
Under fasen Konceptbevis testar du principdistributionen i en laboratoriemiljö på enheter och användare som du har konfigurerat endast i testsyfte.

-   Låt supportavdelningen delta i denna fas för att ta reda på vilka problem som kan uppstå under pilot- och produktionsdistribution. Information om felsökning finns i [Felsöka principer i Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).

-   Under den här delen av processen bör du ta fram kommunikationsplaner för pilot- och produktionsanvändare. Planen bör minst omfatta vilka enhetsbeteenden som ändras och när, affärssyftet med ändringen och vad användarna eller IT-personalen kan göra om de stöter på problem, både information för självhjälp och hur de kontaktar supportavdelningen.

## Pilot
Under piloten distribuerar du principen till en liten grupp testanvändare och -enheter. Det finns saker att tänka på vid en princippilot i Intune:

-   Testgruppen ska vara representativ för gruppen som principen kommer att tillämpas på för produktionsdistribution.

-   Utbilda supportavdelningen om ändringarna av principen och se till att de är beredda att hjälpa användare i testgruppen.

-   Aktivera kommunikationsplanen för pilotanvändare.

-   Piloten kan först utföras i isolerat läge, där enheten inte omfattas av andra principer som kan orsaka konflikter och oönskat beteende.

-   Det slutliga testet måste ta hänsyn till den nya principen och alla befintliga principer som tillämpas på samma enhet.

## Företagsomfattande distribution

-   Baserat på resultatet av piloten justerar du den planerade principen och åtgärdar principkonflikter och oväntat beteende.

-   Meddela supportavdelningen om schemat för den företagsomfattande distributionen. Ha funktioner redo för att besvara hjälpförfrågningar och anpassa distributionen efter behov.

-   Var beredd på att felsöka principen om problem uppstår.

-   Aktivera kommunikationsplanen för produktionsanvändare.

-   Tillämpa principerna inkrementellt på ytterligare grupper, och övervaka principtillståndet för berörda enheter och spåra förfrågningar till supportavdelningen som kan vara relaterade till den nya principen.

## Åtgärder och underhåll
**Åtgärder:** Övervaka Intune-konsolen för aviseringar och problem med användare eller enheter, och kontrollera att principer fungerar enligt planen.

**Support:** Se till att supportavdelningen är medveten om eventuella ändringar i principer som påverkar användarupplevelsen, eftersom dessa kan leda till supportärenden.


### Se även
[Förbered dig för att konfigurera hanteringsprinciper för mobila appar med Microsoft Intune](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

[Felsökningsprinciper i Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)



<!--HONumber=Jun16_HO4-->


