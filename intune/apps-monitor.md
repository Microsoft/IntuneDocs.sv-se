---
title: "Så här övervakar du appinformation och tilldelningar"
titlesuffix: Azure portal
description: "När du har tilldelat en app till användare eller enheter kan du använda den här informationen för att övervaka dess status."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0298fc255b3c11a12b5bf225968d6f2303192053
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Så här övervakar du appinformation och tilldelningar med Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune erbjuder ett antal olika sätt för att övervaka egenskaperna för appar som du hanterar, samt deras tilldelningsstatus.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj **Appar** i gruppen **Hantera** i arbetsbelastningen **Mobilappar**.
5. I listan med appblad väljer du en app. Du ser därefter bladet <*appnamn*> **Installationsstatus för enhet**.

## <a name="app-overview-blade"></a>Bladet för översikt över appar

Du kan använda bladet <*appnamn*> **Installationsstatus för enhet** för att granska information om statusen för en app i din miljö.

### <a name="essentials"></a>Essentials

Avsnittet **Essentials** innehåller följande information om appen:

 - **Utgivare**  
Appens utgivare.
 - **Operativsystem**  
Appens operativsystem (Windows, iOS, Android, osv.)
 - **Skapa**  
Tidpunkt då versionen skapades.
 - **Tilldelade**  
**Ja** eller **nej** om appen har tilldelats.

### <a name="status"></a>Status
Varje diagram visar antalet med följande status:

 - **Installerat**  
Antalet installerade appar.
 - **Inte installerade**  
Antalet appar som inte är installerade.
 - **Installation väntar**  
Antalet appar som håller på att installeras.
 - **Misslyckades**  
Antalet misslyckade installationer.
 - **Okänt**  
Antal appar med okänd status.

### <a name="device-status"></a>Enhetstillstånd

Enhetstillstånd. Ett ringdiagram som visar installationsstatus för appen på enheter. Klicka på diagrammet för att öppna en lista med information om enhetens status. Tabellen med information innehåller följande kolumner:

 - **Enhetsnamn**  
Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgängligt för alla enheter.
 - **Användarnamn**  
Användarens namn.
 - **Plattform**  
Enhetens operativsystem (Windows, iOS, Android, osv.)
 - **Version**  
Appens versionsnummer. För verksamhetsspecifika appar visas det fullständiga versionsnumret. Det fullständiga versionsnumret identifierar en specifik version av appen. Numret visas som _Version_(_Build_). Exempelvis, 2.2(2.2.17560800)
 - **Status**  
Appens status.
 - **Statusinformation**  
Information om statusen.
 - **Senaste incheckning**  
Datum för den senaste enhetssynkroniseringen med Intune.


### <a name="user-status"></a>Användarstatus

Användarstatus. Ett ringdiagram som visar installationsstatus för appen för användare. Klicka på diagrammet för att öppna en lista med information om enhetens status. Tabellen med information innehåller följande kolumner:
 - **Namn**  
Namnet på användaren i Azure AD.
 - **Användarnamn**  
Det unika namnet på användaren.
 - **Installationer**  
Antalet installerade appar som används av användaren.
 - **Fel**  
Antalet misslyckade installationer som utförts av användaren.
 - **Inte installerad**  
Antalet appar som inte installerats av användaren.


## <a name="next-steps"></a>Nästa steg

Läs om hur du arbetar med Intune-data i [Använd Intune-informationslagret](reports-nav-create-intune-reports.md).