---
title: "Anpassade inställningar för macOS-enheter i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig mer om vilka inställningar du kan använda i en anpassad macOS-profil."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 84902bb0e7ea67b388debd8bd7992d396d981a7b
ms.lasthandoff: 02/18/2017


---

# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Anpassade inställningar för macOS-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd Microsoft Intunes anpassade macOS-profil för att distribuera inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) till macOS-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Sedan kan du importera konfigurationsprofilen till en anpassad macOS-profil i Intune och tilldela inställningarna till användare och enheter i organisationen.

Med den här funktionen kan du distribuera macOS-inställningar som inte kan konfigureras med andra Intune-profiltyper.


1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](how-to-configure-custom-settings.md).
2. Ange följande på bladet **Skapa profil**:

- **Namn på anpassad konfigurationsfil** – Ge principen ett namn eftersom det ska visas på enheten och i Intune-statusen.
- **Fil för konfigurationsprofil** – Bläddra till den konfigurationsprofil som du skapat med hjälp av Apple Configurator.
Se till att inställningarna du exporterar från verktyget Apple Configurator är kompatibla med macOS-versionen på de enheter till vilka du distribuerar den anpassade macOS-principen. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

Filen som du har importerat visas i bladområdet **Filinnehåll**.

