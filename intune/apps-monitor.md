---
title: Så här övervakar du appinformation och tilldelningar
titlesuffix: Microsoft Intune
description: När du har tilldelat en app till användare eller enheter kan du använda den här informationen för att övervaka dess status.
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
ms.openlocfilehash: 2d1ca013b7000282316a17e02dcb38b3d4f27958
ms.sourcegitcommit: 820f950d1fc80b1eb5db1b0cf77f44d92a969951
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Så här övervakar du appinformation och tilldelningar med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune erbjuder ett antal olika sätt för att övervaka egenskaperna för appar som du hanterar, samt deras tilldelningsstatus.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i gruppen **Övervakning och hantering**.
3. Välj **Mobilappar** och sedan **Appar** i gruppen **Hantera**.
5. I listan med appar väljer du den app du vill övervaka. Appbladet visas med en översikt över enhetens och användarens status.

## <a name="app-overview-blade"></a>Bladet för översikt över appar

Du kan använda det specifika appbladet till att granska information om statusen för en app i din miljö.

### <a name="essentials"></a>Essentials
Avsnittet **Essentials** innehåller följande information om appen:

 | **Appinformation**            | **Beskrivning**                                                      |
|------------------------|------------------------------------------------------------------|
| **Utgivare**          | Appens utgivare.                                            |
| **Operativsystem**   | Appens operativsystem (Windows, iOS, Android, osv.) |
| **Skapad**             | Datum och tid då versionen skapades.                         |
| **Tilldelade**           | **Ja** eller **nej** om appen har tilldelats.                  |

### <a name="device-and-user-status-graphs"></a>Diagram för enhetens och användarens status
Diagrammet visar antal för följande status:

| **Enhetsstatus**       | **Beskrivning**                                       |
|-----------------------|-------------------------------------------------------|
| **Installerat**         | Antalet installerade appar.                         |
| **Inte installerade**     | Antalet appar som inte är installerade.                     |
| **Misslyckades**            | Antalet misslyckade installationer.                   |
| **Installation väntar**   | Antalet appar som håller på att installeras. |
| **Inte tillämpligt**           | Antal appar där status inte är tillämpligt.            |

### <a name="device-install-status"></a>Installationsstatus för enhet

En statuslista för enheten visas när du väljer **Installationsstatus för enhet** i avsnittet **Övervakare**. Tabellen med information innehåller följande kolumner:

| **Enhetskolumn**      | **Beskrivning**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Enhetsnamn**      | Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn från övriga egenskaper. Det här attributet är inte tillgängligt för alla enheter.                                                                       |
| **Användarnamn**        | Användarens namn.                                                                                                                                                                                                                                      |
| **Plattform**         | Enhetens operativsystem (Windows, iOS, Android, osv.)                                                                                                                                                                                           |
| **Version**          | Appens versionsnummer. För verksamhetsspecifika appar visas det fullständiga versionsnumret. Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis 2.2(2.2.17560800) |
| **Status**           | Appens status.                                                                                                                                                                                                                                     |
| **Statusinformation**   | Information om statusen.                                                                                                                                                                                                                                     |
| **Senaste incheckning**    | Datum för den senaste enhetssynkroniseringen med Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Installationsstatus för användare

En statuslista för användaren visas när du väljer **Installationsstatus för användare** i avsnittet **Övervakare**. Tabellen med information innehåller följande kolumner:

| **Användarkolumn**     | **Beskrivning**                           |
|---------------------|-------------------------------------------|
| **Namn**            | Namnet på användaren i Azure AD.         |
| **Användarnamn**       | Det unika namnet på användaren.              |
| **Installationer**   | Antalet installerade appar som används av användaren. |
| **Fel**        | Antalet misslyckade installationer som utförts av användaren.     |
| **Inte installerad**   | Antalet appar som inte installerats av användaren. |


## <a name="next-steps"></a>Nästa steg

- Läs om hur du arbetar med Intune-data i [Använd Intune-informationslagret](reports-nav-create-intune-reports.md).
- Mer information om appkonfigurationsprinciper finns i [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md).