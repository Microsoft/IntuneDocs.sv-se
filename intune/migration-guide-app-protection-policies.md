---
title: Konfigurera appskyddsprinciper under en Intune-migrering
description: "Syftet med den här artikeln är att tillhandahålla de nödvändig åtgärder som krävs för att konfigurera appskyddsprinciper under en Intune-migrering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: cbe2c794a68ab37722c56448560a3c64f6087969
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="configure-app-protection-policies-optional"></a>Konfigurera appskyddsprinciper (valfritt)

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Men appskyddsprinciper kan du kryptera appar, ange en PIN-kod när appen öppnas, blockera appar från att köras på jailbrokade eller rotade enheter och mycket annat. Om användarens telefonnummer tappas bort eller blir stulet, kan du fjärrensa företagets data selektivt och lämna personuppgifterna intakta genom att tillämpa skyddsprinciper för mobila appar.

Appskyddsprinciperna tillämpar säkerhet på appnivå och kräver inte någon enhetsregistrering. De kan användas med både enheter som har registrerats och inte har registrerats i Intune. Dessutom kan de användas med enheter som registrerats hos en MDM-tredjepartsleverantör.

## <a name="app-protection-policies-with-lob-apps"></a>Appskyddsprinciper med verksamhetsspecifika appar

Du kan också utöka principerna för mobilappsskydd till dina verksamhetsspecifika appar med hjälp av [Microsoft Intune App-SDK:n](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) eller Microsoft Intune App Wrapping-verktyget för både [IOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True)- och [Android](https://www.microsoft.com/download/details.aspx?id=47267)-plattformar.

## <a name="how-do-app-protection-policies-help-during-migration"></a>Vad bidrar principerna för appskydd med under migreringen?

Migreringen kräver att enheterna tas bort från den gamla MDM-providern och registreras i Intune. Du bör planera för detta och uppmuntra dina slutanvändare att lämna den gamla MDM-providern och omedelbart registrera sig i Intune. Under migreringen kan det dock finnas användare som väntar med att slutföra registreringen och vars enheter inte hanteras av någondera MDM-provider.

Under den här perioden kan din organisation vara mer sårbar för stöld av enheter och förlust av företagsdata om åtkomst till resurserna fortfarande tillåts, och/eller förlust av användarproduktivitet om åtkomst till företagets resurser blockeras.

Intune kan erbjuda skydd av företagsdata under migreringen, så att dina företagsdata fortfarande åtnjuter skydd när det inte finns någon hantering på enhetsnivå.

När du inaktiverar villkorlig åtkomst i den gamla MDM-providern kan användarna fortfarande vara produktiva medan du integrerar dem i Intune.

## <a name="task-list-for-app-protection-policies"></a>Uppgiftslista för appskyddsprinciper

1. [Skapa en appskyddsprincip](/intune/app-protection-policies#create-an-app-protection-policy)
2. [Distribuera en princip](/intune/app-protection-policies#deploy-a-policy-to-users)


## <a name="next-steps"></a>Nästa steg 

[Särskilda överväganden vid migrering](migration-guide-considerations.md)
