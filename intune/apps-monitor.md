---
title: Övervaka appinformation och tilldelningar
titlesuffix: Microsoft Intune
description: När du har tilldelat en app till användare eller enheter kan du använda den här informationen för att övervaka appens status.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0408ce3a4c2d4224780b4b23b0fb1b7d690471fe
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Övervaka appinformation och tilldelningar med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune erbjuder ett antal olika sätt för att övervaka egenskaperna för appar som du hanterar, samt att hantera deras app-tilldelningsstatus.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I **Intune**-menyn väljer du **Mobilappar**.
4. I avsnittet**Hantera** på menyn, väljer du **Appar**.
5. Välj en app att övervaka i listan över appar. App-fönstret visas med en översikt över enhetens och användarens status.

## <a name="app-overview-pane"></a>Fönstret för översikt över appar

I app-fönstret kan du granska information om statusen för en app i din miljö.

### <a name="essentials"></a>Essentials
Avsnittet **Essentials** innehåller följande information om appen:

 | **Appinformation**            | **Beskrivning**                                                      |
|------------------------|------------------------------------------------------------------|
| **Utgivare**          | Appens utgivare.                                            |
| **Operativsystem**   | Appens operativsystem (Windows, iOS, Android, o.s.v.). |
| **Skapad**             | Datum och tid då versionen skapades.                         |
| **Tilldelade**           | Om appen har tilldelats (**Ja** eller **Nej**).                  |

### <a name="device-and-user-status-graphs"></a>Diagram för enhetens och användarens status
Diagrammet visar antal appar för följande status:

| **Enhetstillstånd**       | **Beskrivning**                                       |
|-----------------------|-------------------------------------------------------|
| **Installerat**         | Antalet installerade appar.                         |
| **Inte installerade**     | Antalet appar som inte är installerade.                     |
| **Misslyckades**            | Antalet misslyckade installationer.                   |
| **Installation väntar**   | Antalet appar som håller på att installeras. |
| **Inte tillämpligt**           | Antal appar för vilka status inte är tillämpligt.            |

### <a name="device-install-status"></a>Installationsstatus för enhet

En statuslista för enheten visas när du väljer **Installationsstatus för enhet** i avsnittet **Övervakare** i menyn. Tabellen med information innehåller följande kolumner:

| **Enhetskolumn**      | **Beskrivning**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Enhetsnamn**      | Namnet på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgänglig för några andra enheter.                                                                       |
| **Användarnamn**        | Användarens namn.                                                                                                                                                                                                                                      |
| **Plattform**         | Enhetens operativsystem (Windows, iOS, Android, o.s.v.).                                                                                                                                                                                           |
| **Version**          | Appens versionsnummer. För verksamhetsspecifika appar visas det fullständiga versionsnumret. Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis 2.2(2.2.17560800). |
| **Status**           | Appens status.                                                                                                                                                                                                                                     |
| **Statusinformation**   | Information om statusen.                                                                                                                                                                                                                                     |
| **Senaste incheckning**    | Datumet för den senaste enhetssynkroniseringen med Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Installationsstatus för användare

En lista för användarstatus visas när du väljer **Installationsstatus för användare** i avsnittet **Övervakare** i menyn. Tabellen med information innehåller följande kolumner:

| **Användarkolumn**     | **Beskrivning**                           |
|---------------------|-------------------------------------------|
| **Namn**            | Namnet på användaren i Azure Active Directory.         |
| **Användarnamn**       | Det unika namnet på användaren.              |
| **Installationer**   | Antalet appar som installerats av användaren. |
| **Fel**        | Antalet misslyckade installationer av appar för användaren.     |
| **Inte installerad**   | Antalet appar som inte installerats av användaren. |


## <a name="next-steps"></a>Nästa steg

- Läs om hur du arbetar med Intune-data i [Använd Intune-informationslagret](reports-nav-create-intune-reports.md).
- Mer information om appkonfigurationsprinciper finns i [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md).
