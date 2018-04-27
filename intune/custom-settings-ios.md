---
title: Anpassade inställningar i Microsoft Intune för enheter som kör iOS
titleSuffix: ''
description: Läs om vilka inställningar du kan använda i en anpassad iOS-profil i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0ae4e757264465043ee6992033710c5a81d7157
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>Anpassade enhetsinställningar i Microsoft Intune för enheter som kör iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd Microsoft Intunes anpassade profil för iOS för att tilldela inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) till iOS-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Sedan kan du importera konfigurationsprofilen till en anpassad iOS-profil i Intune och tilldela inställningarna till användare och enheter i organisationen.

Med den här funktionen kan du tilldela iOS-inställningar som inte kan konfigureras med andra Intune-profiltyper.


1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. I fönstret **Anpassad konfigurationsprofil** konfigurerar du var och en av följande inställningar:

- **Namn på anpassad konfigurationsfil** – Ge principen ett namn eftersom det ska visas på enheten och i Intune-statusen.
- **Fil för konfigurationsprofil** – Bläddra till den konfigurationsprofil som du skapat med hjälp av Apple Configurator.
Se till att inställningarna du exporterar från verktyget Apple Configurator är kompatibla med versionen av iOS på enheter som du tilldelar till en anpassad princip för iOS. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

Filen som du har importerat visas i fönsterområdet **Filinnehåll**.
