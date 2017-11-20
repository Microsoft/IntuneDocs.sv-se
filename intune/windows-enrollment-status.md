---
title: "Lägga till skärmar för registreringsstatus"
titlesuffix: Azure portal
description: "Visa en hälsning för användare som registrerar Windows 10-enheter."
keywords: 
author: barlanmsft
ms.author: barlan
manager: arob98
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 01171fe0d7ac245233616134fea36f830ff7f4bd
ms.sourcegitcommit: ca10ab40fe40e5c9f4b6f6f4950b551eecf4aa03
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="set-up-an-enrollment-status-screen"></a>Konfigurera en skärm för registreringsstatus

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

När en slutanvändare registrerar en Windows-enhet förväntar sig den personen att kunna komma åt allt som behövs för att vara produktiv direkt efter registreringen. Det slutanvändarna inte inser är att innehåll, appar, principer och inställningar fortfarande håller på att skickas till enheten efter att registreringen har slutförts.

Du kan konfigurera en skärm för registreringsstatus för att tillhandahålla ytterligare information till slutanvändarna, så att de får information om vad som faktiskt händer efter registreringsprocessen. Dessa inställningar finns i **Enhetsregistrering** > **Windows-registrering** > **Skärm med registreringsstatus**.

![Skärm med registreringsstatus i Windows 10.](./media/win10-enrollment-status-admin-setup.png)

Det finns fyra fält som du kan definiera: **Hälsning**, **Meddelande** och **Hyperlänk för hjälp**, där du kan ange **Länktext** och **URL för användarhjälp**.

Slutanvändarna ser även förloppet för säkerhetsprofilen som installeras. 
