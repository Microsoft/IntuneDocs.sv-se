---
title: "Särskilda överväganden vid migrering | Microsoft Docs"
description: "Syftet med den här artikeln är ge kunderna möjlighet att ta särskilda hänsyn vid migrering innan de startar en migreringskampanj."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fas 1: Särskilda överväganden vid migrering

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Det finns särskilda migreringsöverväganden som kan tillämpas beroende på din befintliga MDM-providermiljö.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Fabriksåterställning för Apples program för enhetsregistrering (DEP)

Apples program för enhetsregistrering (DEP) ställer in enhetskonfigurationer som användaren inte kan ta bort. Om du vill bevara de avancerade hanteringsfunktionerna i DEP måste du återställa enheten till sitt ursprungstillstånd genom fabriksåterställning innan du registrerar den i Intune.

Om du vill fortsätta att använda DEP för att hantera enheter i Intune:

1.  Integrera [DEP i Intune](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)

2.  Gå till ditt Apple DEP-konto och [omtilldela DEP-enhetsserienumren](https://help.apple.com/deployment/business/#/tesf9562af26) från din befintliga MDM-provider till Intune.

3.  [Synkronisera](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) ditt DEP-konto med Intune

4.  [Skapa och tilldela](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) lämpliga DEP-registreringsprofiler till serienumren i Intune.

5.  Fabriksåterställ enheterna (antingen genom att fjärransluta till din aktuella MDM-provider eller genom att göra det manuellt på varje enskild enhet)

6.  Distribuera enheterna till slutanvändarna.

## <a name="next-steps"></a>Nästa steg 

[Fas 2: Migreringskampanj](/intune-classic/plan-design/migration-phase2-migration-campaign)

