---
title: Övervaka appinformation och tilldelningar
titlesuffix: Microsoft Intune
description: När du har tilldelat en app till användare eller enheter kan du använda den här informationen för att övervaka appens status.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bedd1108ce0c9e173e6e9519a29d3948f1320c3a
ms.sourcegitcommit: 1a8b34c7854a575bf6ce59f475c7b718fa038d66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/18/2018
ms.locfileid: "40251507"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Övervaka appinformation och tilldelningar med Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I Intune kan du övervaka egenskaperna för appar som du hanterar och hantera apptilldelningsstatus på flera sätt.

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I **Intune**-menyn väljer du **Mobilappar**.
4. I avsnittet**Hantera** på menyn, väljer du **Appar**.
5. Välj en app att övervaka i listan över appar. Appfönstret visas med en översikt över enhetens och användarens status.

> [!NOTE]
> Installationsstatus rapporteras inte för Android Store-appar som distribueras som **tillgängliga**.

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

> [!NOTE]
> Antal appar som identifieras kanske inte matchar statusen för antalet installerade appar. Här är några möjliga orsaker till skillnaden:
>    - En måländring för en installerad app som hanteras kan göra att antalet installerade appar på statusbladet minskar, men appen rapporteras fortfarande som identifierad.
>    - Om flera instanser av samma app är mål i en klientorganisation blir antalen olika eftersom användare eller enheter kan överlappa. Varje instans av appen räknar överlappande användare, men det kommer att finnas dubbletter bland de identifierade apparna.
>    - Identifierade appar och appstatus samlas in under olika tidsintervall, och det här kan leda till avvikelser i antalet appar.
 
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
