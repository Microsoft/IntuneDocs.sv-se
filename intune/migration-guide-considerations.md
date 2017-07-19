---
title: "Särskilda överväganden vid migrering"
description: "Den här artikeln innehåller särskilda migreringsöverväganden som du bör ha i åtanke innan du påbörjar en migreringskampanj."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 7ff1180275fddc7f0d6ef957c4680d7c34ad471e
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/12/2017
---
# <a name="special-migration-considerations"></a>Särskilda överväganden vid migrering

Det finns särskilda migreringsöverväganden som kan vara relevanta beroende på din befintliga MDM-providermiljö.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Fabriksåterställning för Apples program för enhetsregistrering (DEP)

Apples program för enhetsregistrering (DEP) ställer in enhetskonfigurationer som användaren inte kan ta bort. Om du vill bevara de avancerade hanteringsfunktionerna i DEP måste du återställa enheten till dess ursprungliga tillstånd genom en fabriksåterställning innan du registrerar den i Intune.

Om du vill fortsätta att hantera enheter i Intune med DEP måste du [konfigurera registrering av iOS-enheter med DEP](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Nästa steg

[Fas 2: Migreringskampanj](migration-guide-campaign.md)
