---
title: Avbrutna företagsportalsregistreringar i Intune
titlesuffix: Microsoft Intune
description: Lär dig mer om avbrutna företagsportalsregistreringar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: ba1ee5a6811457b8c6e7343de7355261a2fcecdb
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236770"
---
# <a name="company-portal-abandonment-report"></a>Rapport över avbrutna företagsportalsregistreringar

Den här rapporten visar var under företagsportalsregistreringen som användare avbryter registreringsprocessen.

Visa rapporten genom att välja **Intune** > **Enhetsregistrering** > **Lämnade företagsportalsessioner**.

Med hjälp av den här informationen om avbrutna registreringar kan du uppdatera din hjälpdokumentation och underlätta för användarna att slutföra registreringen. Om du till exempel ser att många användare avbryter processen vid steget för användningsvillkoren kan du undersöka det området och göra det enklare för användarna.

## <a name="what-is-abandonment"></a>Vad är en avbruten registrering?

En avbruten registrering innebär att en användare gör något av följande:

-   Uttryckligen väljer en åtgärd för att avbryta registreringen
-   Stänger företagsportalen under registreringen
-   Låter det gå mer än 30 minuter mellan registreringsdelarna

Om en användare väljer att avbryta registreringen och börjar om flera gånger, visas detta som flera försök och flera avbrutna registreringar. Om en användare väntar i 30 minuter mellan olika registreringsskärmar, betraktas det som flera avbrutna registreringar.

## <a name="what-does-the-report-show"></a>Vad visar rapporten?

Registreringsrapporterna innehåller data för iOS- och Android-enheter.

Rapporterna visar data för de senaste två veckorna, men du kan filtrera rapporten och visa valfri period upp till 30 dagar bakåt i tiden.

Du kan filtrera efter datumintervall, operativsystem och registreringsdel genom att välja **Filtrera**.

### <a name="number-and-percentage-tiles"></a>Paneler för antal och procent

Högst upp i rapporten kan du se antalet och procentandelen övergivna registreringar i förhållande till alla registreringar.

-   Påbörjade registreringar: Antal registreringsförsök.
-   Lämnade registreringar: Antal registreringsförsök som inte resulterade i en helt registrerad och kompatibel enhet.
-   Lämningsfrekvens: Antal övergivna registreringsförsök i procent (Lämnade registreringar / Påbörjade registreringar).

### <a name="line-graph"></a>Linjediagram

Linjediagrammet visar avbrutna registreringar per dag för var och en av de fyra primära registreringsavsnitten:

-   Checklista för konfiguration
-   Plattformsskärmar
-   Villkor för användning
-   Efterlevnad/aktivering

### <a name="user-abandonment-actions"></a>Avbrutna användaråtgärder

Följande tabeller innehåller en lista med användaråtgärder som betraktas som avbrutna av användaren. Om du vill se exempel på registreringsskärmar kan du titta på videoinspelningarna om [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment)- och [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment)-registrering. 


#### <a name="setup-checklist-section"></a>Avsnittet med checklistan för konfiguration

| Namn på avbruten åtgärd | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Uppmaning om att öppna sidan på företagsportalen | iOS/Android | **Avbryt** |
| EnrollmentWrapUp | Skärmen Registrerar enhet till slutet av **Läser in företagsresurser** | iOS/Android | Tog mer än 30 minuter |
| DeviceCategory | Val av enhetskategori (om administratören har konfigurerat det) tills användaren klickar på **Klar** | iOS/Android | Tog mer än 30 minuter |
| PreEnrollmentWizard | Skärmen Konfigurera åtkomst när registreringen har påbörjats men användaren har återvänt till åtkomstkonfigurationen | iOS/Android| **Senarelägg** |
| PreEnrollmentWizard | Skärmen Konfigurera åtkomst tills användaren klickar på **Nästa** på skärmen **Vad händer nu?** | iOS/Android | Tog mer än 30 minuter |

#### <a name="platform-screens-section"></a>Avsnittet med plattformsskärmar

| Namn på avbruten åtgärd | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| iOSProfileLaunch | Uppmaning om att visa en konfigurationsprofil | iOS | **Ignorera** |
| iOSProfileLaunch | Skärmen Installera profil | iOS | **Avbryt** |
| iOSProfileLaunch | Uppmaning om att lita på profilens källa för att registrera enheten | iOS | **Avbryt** |
| iOSProfileLaunch | Skärmen Installera profil tills profilen har installerats | iOS | Tog mer än 30 minuter |
| AndroidPermissions | Aktiveringsskärm för enhetsadministratör | Android | **Avbryt** |
| AndroidPermissions | Från uppmaning om godkännande att ringa och hantera telefonsamtal tills enhetsadministratören väljer att **aktivera** | Android | Tog mer än 30 minuter |
| KnoxActivation | KLMS-agentaktivering (endast Samsung) | Android| **Avbryt** |
| KnoxActivation | KLMS-agentaktivering tills **Bekräfta** | Android | Tog mer än 30 minuter|

#### <a name="terms-of-use-section"></a>Avsnittet med användningsvillkor

| Namn på avbruten åtgärd | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| TermsofUse | Användningsvillkor (om administratören har konfigurerat det) | iOS/Android | **Avböj alla** |
| TermsofUse | Användningsvillkor tills **Godkänn allt** | iOS/Android | Tog mer än 30 minuter |

#### <a name="complianceactivation-section"></a>Avsnittet om efterlevnad/aktivering

| Namn på avbruten åtgärd | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| Efterlevnad | Enhetsefterlevnad (om administratören har konfigurerat det) visas som icke-grön vid åtkomstkonfiguration efter registreringen| iOS/Android | **Senarelägg** |
| Efterlevnad | Enhetsefterlevnad visas som icke-grön tills den uppdaterats att visas som grön | iOS/Android | Tog mer än 30 minuter |
| Aktivering | Aktiveringsregistreringen (om administratören har konfigurerat det) visas som icke-grön vid åtkomstkonfigurationen | iOS/Android | **Senarelägg** |
| Efterlevnad | Enhetsaktivering visas som icke-grön tills den uppdaterats att visas som grön | iOS/Android | Tog mer än 30 minuter |

## <a name="next-steps"></a>Nästa steg

När du har granskat statistiken för avbrutna registreringar kan du gå igenom [registreringsalternativen](enrollment-options.md) och se om du kan göra några ändringar för att förbättra registreringen.