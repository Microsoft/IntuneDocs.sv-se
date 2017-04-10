---
title: "Kända problem i förhandsversionen av Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Mer information om kända problem i förhandsversionen"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Kända problem i Microsoft Intune-förhandsversionen


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Läs det här avsnittet om du ha mer information om kända problem i Intune-förhandsversionen.

Om du vill rapportera en bugg som inte visas här, [öppnar du en supportförfrågan](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

Om du vill föreslå att en ny funktion läggs till i Intune kan du skicka en rapport på vår [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console)-plats.

## <a name="administration-and-accounts"></a>Administration och konton

- Globala administratörer (kallas även innehavaradministratörer) kan fortsätta att utföra dagliga administrationsuppgifter utan en separat Intune- eller EMS-licens (Enterprise Mobility Suite). Om globala administratörer vill använda tjänsten, t.ex. för att registrera sina egna enheter, företagsenheter eller för att använda Intunes företagsportal, behöver de dock en Intune- eller EMS-licens precis som andra användare.

## <a name="apple-enrollment-profile-migration"></a>Migrering av Apple-registreringsprofil
- Under de kommande månaderna kommer Intune att aktivera distributionshanteringen av Apples program för enhetsregistrering och Apple Configurator via nya Azure Portal. Om du tar bort Apples DEP-token och inte överför en uppdaterad token, så återställs den ursprungliga token i nya Azure Portal som en del av migreringen av ditt Intune-konto. Om du vill ta bort denna token och förhindra DEP-registrering tar du helt enkelt bort token i Azure Portal. 

