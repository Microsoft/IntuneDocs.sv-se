---
title: "Anpassade Intune-inställningar för iOS-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs mer om vilka inställningar du kan använda i en anpassad iOS-profil."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: cfccdbf34437c5ab23cefba5307c53c60573ddb0


---

# <a name="intune-custom-settings-for-ios-devices-in-intune-azure-preview"></a>Anpassade Intune-inställningar för iOS-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd Microsoft Intunes anpassade profil för iOS för att distribuera inställningar som du har skapat med hjälp av [Apple Configurator-verktyget](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) till iOS-enheter. Med detta verktyg kan du skapa många inställningar som styr driften av dessa enheter och exportera dem till en konfigurationsprofil. Sedan kan du importera konfigurationsprofilen till en anpassad iOS-profil i Intune och tilldela inställningarna till användare och enheter i organisationen.

Med den här funktionen kan du distribuera iOS-inställningar som inte kan konfigureras med andra Intune-profiltyper.


1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](how-to-configure-custom-settings.md).
2. Ange följande på bladet **Skapa profil**:

- **Namn på anpassad konfigurationsfil** – Ge principen ett namn eftersom det ska visas på enheten och i Intune-statusen.
- **Fil för konfigurationsprofil** – Bläddra till den konfigurationsprofil som du skapat med hjälp av Apple Configurator.
Se till att inställningarna du exporterar från verktyget Apple Configurator är kompatibel med versionen av iOS på enheter som du distribuerar till en anpassad princip för iOS. Om du vill ha information om hur du löser inkompatibla inställningar kan du söka efter **Referens för konfigurationsprofil** och **Protokollreferens för hantering av mobila enheter** på webbplatsen [Apple Developer](https://developer.apple.com/).

Filen som du har importerat visas i bladområdet **Filinnehåll**.



<!--HONumber=Feb17_HO1-->


