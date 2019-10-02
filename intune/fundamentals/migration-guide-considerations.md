---
title: Särskilda överväganden vid migrering
titleSuffix: Microsoft Intune
description: Den här artikeln innehåller särskilda migreringsöverväganden som du bör ha i åtanke innan du påbörjar en migreringskampanj till Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 45e2985bcf01d635e964ee8785938c0d5df4e4af
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727616"
---
# <a name="special-migration-considerations"></a>Särskilda överväganden vid migrering

Det finns särskilda migreringsöverväganden som kan vara relevanta beroende på din befintliga MDM-providermiljö.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Rensning för Apples program för enhetsregistrering (DEP)

Apples program för enhetsregistrering (DEP) ställer in enhetskonfigurationer som användaren inte kan ta bort. Om du vill bevara de avancerade hanteringsfunktionerna i DEP måste du återställa enheten till dess ursprungliga tillstånd genom en att rensa den innan du registrerar den i Intune.

Om du vill fortsätta att hantera enheter i Intune med DEP måste du [konfigurera registrering av iOS-enheter med DEP](../enrollment/device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Nästa steg

[Fas 2: Migreringskampanj](../migration-guide-campaign.md)
