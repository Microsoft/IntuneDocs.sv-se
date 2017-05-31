---
title: Konfigurera appskyddsprinciper under en Intune-migrering | Microsoft Docs
description: "Syftet med den här artikeln är att tillhandahålla de nödvändig åtgärder som krävs för att konfigurera appskyddsprinciper under en Intune-migrering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ec990ecdedff0e1b7f4fd6fd9d45fd2edc1571bd
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>Fas 1: Konfigurera appskyddsprinciper (valfritt)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Men appskyddsprinciper kan du kryptera appar, ange en PIN-kod när appen öppnas, blockera appar från att köras på jailbrokade eller rotade enheter och mycket annat. Om användarens telefonnummer tappas bort eller blir stulet, kan du fjärrensa företagets data selektivt och lämna personuppgifterna intakta genom att tillämpa skyddsprinciper för mobila appar.

Appskyddsprinciperna tillämpar säkerhet på appnivå och kräver inte någon enhetsregistrering. De kan användas med både enheter som har registrerats och inte har registrerats i Intune. Dessutom kan de användas med enheter som registrerats hos en MDM-tredjepartsleverantör.

## <a name="app-protection-policies-with-lob-apps"></a>Appskyddsprinciper med verksamhetsspecifika appar

Du kan också utöka skyddsprinciperna för mobilappar till verksamhetsspecifika appar /intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) eller Microsoft Intunes programhanteringsverktyg för både [iOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True)- och [Android](https://www.microsoft.com/download/details.aspx?id=47267)-plattformar.

## <a name="how-do-app-protection-policies-help-during-migration"></a>Vad bidrar principerna för appskydd med under migreringen?

Migreringen kräver att enheterna tas bort från den gamla MDM-providern och registreras i Intune. Du bör planera för detta och uppmuntra dina slutanvändare att lämna den gamla MDM-providern och omedelbart registrera sig i Intune. Under migreringen kan det dock finnas användare som väntar med att slutföra registreringen och vars enheter inte hanteras av någondera MDM-provider.

Under den här perioden kan din organisation vara mer sårbar för stöld av enheter och förlust av företagsdata om åtkomst till resurserna fortfarande tillåts, och/eller förlust av användarproduktivitet om åtkomst till företagets resurser blockeras.

Intune kan erbjuda skydd av företagsdata under migreringen, så att dina företagsdata fortfarande åtnjuter skydd när det inte finns någon hantering på enhetsnivå.

När du inaktiverar villkorlig åtkomst i den gamla MDM-providern kan användarna fortfarande vara produktiva medan du integrerar dem i Intune.

## <a name="task-list-for-app-protection-policies"></a>Uppgiftslista för appskyddsprinciper

-   Uppgift 1: Lär dig [hur du förbereder konfiguration av skyddsprinciper för mobilappar](/intune-classic/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   Uppgift 2: Lär dig [hur du skapar och distribuerar skyddsprinciper för mobilappar](/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>Nästa steg 

[Fas 1: Särskilda överväganden vid migrering](/intune-classic/plan-design/migration-phase1-special-migration-considerations)

