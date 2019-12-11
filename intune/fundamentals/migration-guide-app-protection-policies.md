---
title: Konfigurera appskyddsprinciper under migrering
titleSuffix: Microsoft Intune
description: Den här artikeln beskriver de steg du måste utföra när du konfigurerar appskyddsprinciper under en Microsoft Intune-migrering.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fab3ea722e94f2613a0fb1e474a16ecb5971569
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585268"
---
# <a name="configure-app-protection-policies-optional"></a>Konfigurera appskyddsprinciper (valfritt)


Med appskyddsprinciper kan du:
* Kryptera appar
* Definiera en PIN-kod som krävs för att komma åt appen
* Förhindra att appar körs på jailbreakade eller rotade enheter, samt tillämpa många andra skydd.

Om användaren tappar bort sin telefon eller om den blir stulen kan du selektivt rensa företagsdata via en fjärranslutning utan att personliga data påverkas.

Appskyddsprinciperna tillämpar säkerhet på appnivå och kräver inte någon enhetsregistrering. Du kan använda dem med enheter som registrerats i Intune eller inte. Du kan också tillämpa dem på enheter som registrerats i en tredje parts MDM-provider.

## <a name="app-protection-policies-with-lob-apps"></a>Appskyddsprinciper med verksamhetsspecifika appar

Du kan även utöka principerna för mobilappsskydd till dina verksamhetsspecifika appar med hjälp av [Microsoft Intune App SDK](../developer/app-sdk-get-started.md) eller Microsoft Intune-programhanteringsverktyget för både iOS- och Android-plattformar. Mer information finns i [Programhanteringsverktyget för iOS](../developer/app-wrapper-prepare-ios.md) och [Programhanteringsverktyget för Android](./../developer/app-wrapper-prepare-android.md). Se dessutom [Förbered verksamhetsspecifika appar för appskydd](../developer/apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Vad bidrar principerna för appskydd med under migreringen?

Vid en migrering måste du ta bort enheter från den gamla MDM-providern och registrera dem i Intune. Du bör planera för detta och uppmuntra dina slutanvändare att lämna den gamla MDM-providern och omedelbart registrera sig i Intune. Under migreringen kan det dock finnas användare som väntar med att slutföra registreringen och vars enheter inte hanteras av någondera MDM-provider.

Under den här perioden kan din organisation vara mer sårbar för enhetsstöld och förlust av företagsdata om åtkomst till företagsdata fortfarande tillåts. Användarproduktiviteten kan också påverkas om åtkomsten till företagsresurser blockeras.

Intune kan erbjuda skydd av företagsdata under migreringen, så att dina företagsdata fortfarande åtnjuter skydd när det inte finns någon hantering på enhetsnivå.

När du inaktiverar villkorlig åtkomst i den gamla MDM-providern kan användarna fortfarande vara produktiva medan du integrerar dem i Intune.

## <a name="task-list-for-app-protection-policies"></a>Uppgiftslista för appskyddsprinciper

- [Hur du skapar och tilldelar skyddsprinciper för appar](~/apps/app-protection-policies.md)

## <a name="next-steps"></a>Nästa steg

[Särskilda överväganden vid migrering](migration-guide-considerations.md)
