---
title: "Anpassade inställningar för macOS-enheter i Intune"
titleSuffix: Azure portal
description: "Läs mer om vilka inställningar du kan använda i en anpassad macOS-profil.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d52b6aac830ff01ee5c05ebc51f923102bf3eef2
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Anpassade inställningar för macOS-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd Microsoft Intunes anpassade macOS-profil för att tilldela inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) till macOS-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Sedan kan du importera konfigurationsprofilen till en anpassad macOS-profil i Intune och tilldela inställningarna till användare och enheter i organisationen.

Med den här funktionen kan du tilldela macOS-inställningar som inte kan konfigureras med andra Intune-profiltyper.


1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. Ange följande på bladet **Skapa profil**:

- **Namn på anpassad konfigurationsfil** – Ge principen ett namn eftersom det ska visas på enheten och i Intune-statusen.
- **Fil för konfigurationsprofil** – Bläddra till den konfigurationsprofil som du skapat med hjälp av Apple Configurator.
Se till att inställningarna du exporterar från verktyget Apple Configurator är kompatibla med macOS-versionen på de enheter som du tilldelar den anpassade macOS-principen. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

Filen som du har importerat visas i bladområdet **Filinnehåll**.
