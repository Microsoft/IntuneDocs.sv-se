---
title: "Så här övervakar du appinformation och tilldelningar"
titlesuffix: Azure portal
description: "När du har tilldelat en app till användare eller enheter, kan du använda den här informationen för att övervaka dess status.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Så här övervakar du appinformation och tilldelningar med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune erbjuder ett antal olika sätt för att övervaka egenskaperna för appar som du hanterar, samt deras tilldelningsstatus.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj **Appar** i gruppen **Hantera** i arbetsbelastningen **Mobilappar**.
     
    ![Bladet installationsstatus för app.](./media/monitor-apps.png)
5. I listan med appblad väljer du en app. Du ser därefter bladet <*appnamn*> **Installationsstatus för enhet**.

Statusrapporten för enhetsinstallationen innehåller följande kolumner:

1.  **Enhetsnamn** Namnet på enhetstypen.
2.  **Användarnamn** Namnet på användaren.
3.   **Plattform** Operativsystemet som är installerat på enheten.
4.  **Version**: Programmets versionsnummer.
5.   **Status** De möjliga tillstånden för apparna är: **Installerad**, **Inte installerad**, **Installation väntar** och **Fel**.
6. **Statusinformation** En läsbar beskrivning av appens tillstånd på enheten.
7. **Senaste incheckning** När enheten senast checkade in i Intune.

Gör sedan något av följande för att lära dig mer om dina appar och deras tilldelningar.

## <a name="general"></a>Allmänt

- **Översikt** – Ger en översikt över appen och information om status för alla apptilldelningar. Du kan välja ett av dessa diagram för att öppna bladen **Installationsstatus för enhet** eller **Installationsstatus för användare** och få mer detaljerad information.

## <a name="manage"></a>Hantera

- **Egenskaper** – Låter dig visa och ändra information om den valda appen. Mer information om appegenskaper finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).
- **Tilldelningar** – Innehåller information om tilldelningar för den här appen. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

## <a name="monitor"></a>Övervakare

- **Installationsstatus för enhet** – Innehåller detaljerad information för varje enhet som du har tilldelat den valda appen till, inklusive namnet på enheten, operativsystem, när enheten senast checkades in på Intune och status för appinstallationen.
- **Installationsstatus för användare** – Innehåller detaljerad information från användaren som du har tilldelat den valda appen till, inklusive antalet installationer av appen som användaren har på alla sina enheter och information om eventuella installationsfel.