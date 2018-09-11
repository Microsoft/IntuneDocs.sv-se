---
title: Särskilda överväganden vid migrering
titlesuffix: Microsoft Intune
description: Den här artikeln innehåller särskilda migreringsöverväganden som du bör ha i åtanke innan du påbörjar en migreringskampanj till Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 23619048faca4cdf9d64b15b0db7c09cb958a082
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43314048"
---
# <a name="special-migration-considerations"></a>Särskilda överväganden vid migrering

Det finns särskilda migreringsöverväganden som kan vara relevanta beroende på din befintliga MDM-providermiljö.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Rensning för Apples program för enhetsregistrering (DEP)

Apples program för enhetsregistrering (DEP) ställer in enhetskonfigurationer som användaren inte kan ta bort. Om du vill bevara de avancerade hanteringsfunktionerna i DEP måste du återställa enheten till dess ursprungliga tillstånd genom en att rensa den innan du registrerar den i Intune.

Om du vill fortsätta att hantera enheter i Intune med DEP måste du [konfigurera registrering av iOS-enheter med DEP](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Nästa steg

[Steg 2: Migreringskampanjen](migration-guide-campaign.md)
