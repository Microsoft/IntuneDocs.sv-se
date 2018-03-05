---
title: Ta bort en macOS-enhet
titlesuffix: Azure portal
description: "Lär dig hur du tar bort alla data, inklusive operativsystemet, från en macOS-enhet.”"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81f328004863e812b706174e74a9b74d0bdf80b6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>Radera alla data från en macOS-enhet

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan ta bort alla data från en macOS-enhet, inklusive operativsystemet. Enheten tas även bort från Intune-hantering. Ingen varning ges till slutanvändaren.

1. I [Intune i Azure Portal](https://aka.ms/intuneportal) väljer du till **Enheter** > **Alla enheter** > och väljer enheten som du vill ta bort.
![Skärmbild](./media/device-erase/choosedevice.png)
2. Klicka på **Mer** > **Radera** > och ange 6 siffror för **PIN-kod för återställning**. Det här är PIN-koden som du måste ge användarna så att de kan installera om operativsystemet på enheten. Se till att anteckna den här PIN-koden eftersom den inte är synlig igen när raderingsåtgärden har slutförts.
![Skärmbild](./media/device-erase/providepin.png)
3. Klicka på **OK** för att radera enheten.
