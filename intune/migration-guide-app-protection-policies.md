---
title: Konfigurera appskyddsprinciper under en Intune-migrering
description: "Den här artikeln beskriver de steg du utför för att konfigurera appskyddsprinciper under en Intune-migrering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: c58ce51731b476cfca71851430297aff3edc5cd6
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/12/2017
---
# <a name="configure-app-protection-policies-optional"></a>Konfigurera appskyddsprinciper (valfritt)


Med appskyddsprinciper kan du:
* Kryptera appar
* Definiera en PIN-kod som krävs för att komma åt appen
* Förhindra att appar körs på jailbreakade eller rotade enheter, samt tillämpa många andra skydd.

Om användaren tappar bort sin telefon eller om den blir stulen kan du selektivt rensa företagsdata via en fjärranslutning utan att personliga data påverkas.

Appskyddsprinciperna tillämpar säkerhet på appnivå och kräver inte någon enhetsregistrering. Du kan använda dem med enheter som registrerats i Intune eller inte. Du kan också tillämpa dem på enheter som registrerats i en tredje parts MDM-provider.

## <a name="app-protection-policies-with-lob-apps"></a>Appskyddsprinciper med verksamhetsspecifika appar

Du kan också utöka principerna för mobilappsskydd till dina verksamhetsspecifika appar med hjälp av [Microsoft Intune App SDK](app-sdk-get-started.md) eller Microsoft Intune-programhanteringsverktyget för både [iOS](https://www.microsoft.com/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True)- och [Android](https://www.microsoft.com/download/details.aspx?id=47267)-plattformar.

## <a name="how-do-app-protection-policies-help-during-migration"></a>Vad bidrar principerna för appskydd med under migreringen?

Vid en migrering måste du ta bort enheter från den gamla MDM-providern och registrera dem i Intune. Du bör planera för detta och uppmuntra dina slutanvändare att lämna den gamla MDM-providern och omedelbart registrera sig i Intune. Under migreringen kan det dock finnas användare som väntar med att slutföra registreringen och vars enheter inte hanteras av någondera MDM-provider.

Under den här perioden kan din organisation vara mer sårbar för enhetsstöld och förlust av företagsdata om åtkomst till företagsdata fortfarande tillåts. Användarproduktiviteten kan också påverkas om åtkomsten till företagsresurser blockeras.

Intune kan erbjuda skydd av företagsdata under migreringen, så att dina företagsdata fortfarande åtnjuter skydd när det inte finns någon hantering på enhetsnivå.

När du inaktiverar villkorlig åtkomst i den gamla MDM-providern kan användarna fortfarande vara produktiva medan du integrerar dem i Intune.

## <a name="task-list-for-app-protection-policies"></a>Uppgiftslista för appskyddsprinciper

1. [Skapa en appskyddsprincip](app-protection-policies.md#create-an-app-protection-policy)
2. [Distribuera en princip](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>Nästa steg

[Särskilda överväganden vid migrering](migration-guide-considerations.md)
