---
title: "Så här övervakar du appinformation och tilldelningar"
titleSuffix: Intune on Azure
description: "När du har tilldelat en app till användare eller enheter, kan du använda den här informationen för att övervaka dess status.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d588ecc8f2e211b5a8ccdfe7b7720869cc6327b8
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Så här övervakar du appinformation och tilldelningar med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune erbjuder ett antal olika sätt för att övervaka egenskaperna för appar som du hanterar, samt deras tilldelningsstatus.

1. Välj **Hantera** > **Appar** i arbetsbelastningen **Mobilappar**.
2. I bladet med applistan väljer du önskad app för att se dess information. Du ser därefter bladet <*appnamn*> **Installationsstatus för enhet**: ![bladet Status för appinstallation.](./media/monitor-apps.png)

Gör sedan något av följande för att lära dig mer om dina appar och deras tilldelningar.

## <a name="general"></a>Allmänt

- **Översikt** – Ger en översikt över appen och information om status för alla apptilldelningar. Du kan välja ett av dessa diagram för att öppna bladen **Installationsstatus för enhet** eller **Installationsstatus för användare** och få mer detaljerad information.

## <a name="manage"></a>Hantera

- **Egenskaper** – Låter dig visa och ändra information om den valda appen. Mer information om appegenskaper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).
- **Tilldelningar** – Innehåller information om tilldelningar för den här appen. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Övervakare

- **Installationsstatus för enhet** – Innehåller detaljerad information för varje enhet som du har tilldelat den valda appen till, inklusive namnet på enheten, operativsystem, när enheten senast checkades in på Intune och status för appinstallationen.
- **Installationsstatus för användare** – Innehåller detaljerad information från användaren som du har tilldelat den valda appen till, inklusive antalet installationer av appen som användaren har på alla sina enheter och information om eventuella installationsfel.