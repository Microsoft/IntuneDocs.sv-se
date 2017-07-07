---
title: "Särskilda överväganden vid migrering"
description: "Syftet med den här artikeln är ge kunderna möjlighet att ta särskilda hänsyn vid migrering innan de startar en migreringskampanj."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>Särskilda överväganden vid migrering

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Det finns särskilda migreringsöverväganden som kan tillämpas beroende på din befintliga MDM-providermiljö.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Fabriksåterställning för Apples program för enhetsregistrering (DEP)

Apples program för enhetsregistrering (DEP) ställer in enhetskonfigurationer som användaren inte kan ta bort. Om du vill bevara de avancerade hanteringsfunktionerna i DEP måste du återställa enheten till sitt ursprungstillstånd genom fabriksåterställning innan du registrerar den i Intune.

Om du vill fortsätta att hantera enheter i Intune med DEP måste du [konfigurera registrering av iOS-enheter med DEP](/intune/device-enrollment-program-enroll-ios).


## <a name="next-steps"></a>Nästa steg 

[Fas 2: Migreringskampanj](migration-guide-campaign.md)
