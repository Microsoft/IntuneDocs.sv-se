---
title: Övervaka appinformation och tilldelningar
titleSuffix: Microsoft Intune
description: När du har tilldelat en app till användare eller enheter kan du använda den här informationen för att övervaka appens status.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 72e1f95e2bd81d974d900acbcb0f785bb7966eaa
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563707"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Övervaka appinformation och tilldelningar med Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I Intune kan du övervaka egenskaperna för appar som du hanterar och hantera apptilldelningsstatus på flera sätt.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar**.
3. Välj en app att övervaka i listan över appar. Appfönstret visas med en översikt över enhetens och användarens status.

> [!NOTE]
> Installationsstatus rapporteras inte för Android Store-appar som distribueras som **tillgängliga**.
>
> För Managed Google Play-appar som distribueras till Android Enterprise-arbetsprofilenheter kan du visa status och versionsnumret för den app som är installerad på en enhet som använder Intune. 

## <a name="app-overview-pane"></a>Fönstret för översikt över appar

I app-fönstret kan du granska information om statusen för en app i din miljö.

### <a name="essentials"></a>Essentials
Avsnittet **Essentials** innehåller följande information om appen:

 | **Appinformation**            | **Beskrivning**                                                      |
|------------------------|------------------------------------------------------------------|
| **Utgivare**          | Appens utgivare.                                            |
| **Operativsystem**   | Appens operativsystem (Windows, iOS, Android, o.s.v.). |
| **Skapad**             | Datum och tid då versionen skapades. <b>**Obs**! Datumvärdet uppdateras när en IT-administratör ändrar appens metadata, till exempel appkategori eller appbeskrivning.                        |
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

> [!NOTE]
> Tänk på att Android LOB-appar (.APK) som distribueras som **Tillgänglig med eller utan registrering** bara rapporterar appens installationsstatus för registrerade enheter. Appens installationsstatus är inte tillgänglig för enheter som inte har registrerats i Intune.

### <a name="device-install-status"></a>Installationsstatus för enhet

En statuslista för enheten visas när du väljer **Installationsstatus för enhet** i avsnittet **Övervakare** i menyn. Tabellen med information innehåller följande kolumner:

| **Enhetskolumn**      | **Beskrivning**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Enhetsnamn**      | Namnet på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgänglig för några andra enheter.                                                                       |
| **Användarnamn**        | Användarens namn.                                                                                                                                                                                                                                      |
| **Plattform**         | Enhetens operativsystem (Windows, iOS, Android, o.s.v.).                                                                                                                                                                                           |
| **Version**          | Appens versionsnummer. För verksamhetsspecifika appar (LOB) och Microsoft Store-appar för företag visas appens fullständiga versionsnummer. Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis 2.2(2.2.17560800). Inga versioner visas för Store-standardappar. |
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

- Läs om hur du arbetar med Intune-data i [Använd Intune-informationslagret](../reports-nav-create-intune-reports.md).
- Mer information om appkonfigurationsprinciper finns i [Appkonfigurationsprinciper för Intune](app-configuration-policies-overview.md).
