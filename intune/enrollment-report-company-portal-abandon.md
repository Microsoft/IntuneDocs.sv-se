---
title: Rapport om ofullständiga användarregistreringar i Intune
titleSuffix: Microsoft Intune
description: Läs mer om rapporten om ofullständiga användarregistreringar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b67adeac619e26de785addbab4c6312915a58f0
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071749"
---
# <a name="incomplete-user-enrollments-report"></a>Rapport om ofullständiga användarregistreringar

Den här rapporten visar var under företagsportalsregistreringen som användare inte slutför registreringsprocessen.

Visa rapporten genom att välja **Intune** > **Enhetsregistrering** > **Ofullständiga användarregistreringar**.

Med hjälp av den här informationen kan du uppdatera din hjälpdokumentation och underlätta för användarna att slutföra registreringen. Om du till exempel ser att många användare avbryter processen vid steget för användningsvillkoren kan du undersöka det området och göra det enklare för användarna.

## <a name="what-is-an-incomplete-enrollment"></a>Vad är en ofullständig registrering?

En ofullständig registrering innebär att en användare gör något av följande:

- Uttryckligen väljer en åtgärd för att avbryta registreringen
- Stänger företagsportalen under registreringen
- Låter det gå mer än 30 minuter mellan registreringsdelarna

Om en användare väljer att avbryta registreringen och börjar om flera gånger visas detta som flera försök och flera ofullständiga registreringar. Om en användare väntar i 30 minuter mellan olika registreringsskärmar betraktas det som flera ofullständiga registreringar.

## <a name="what-does-the-report-show"></a>Vad visar rapporten?

Rapporterna innehåller data för iOS- och Android-enheter.

Rapporterna visar data för de senaste två veckorna, men du kan filtrera rapporten och visa valfri period upp till 30 dagar bakåt i tiden.

Du kan filtrera efter datumintervall, operativsystem och registreringsdel genom att välja **Filtrera**.

### <a name="number-and-percentage-tiles"></a>Paneler för antal och procent

Högst upp i rapporten kan du se antalet och procentandelen ofullständiga registreringar i förhållande till alla registreringar.

- Initierade registreringar: Antalet registreringsförsök.
- Ofullständiga registreringar: Det antal registreringsförsök som inte resulterade i en helt registrerad och kompatibel enhet.
- Frekvens ofullständiga: Den procentandel registreringsförsök som övergavs (Övergivna registreringar/Påbörjade registreringar).

### <a name="line-graph"></a>Linjediagram

Linjediagrammet visar dagliga ofullständiga registreringar för vart och ett av de fyra primära registreringsavsnitten:

- Checklista för konfiguration
- Plattformsskärmar
- Villkor för användning
- Efterlevnad/aktivering

### <a name="user-abandonment-actions"></a>Avbrutna användaråtgärder

Följande tabeller visar listan över användaråtgärder som betraktas som upphovsgivande till en ofullständig registrering. Om du vill se exempel på registreringsskärmar kan du titta på videoinspelningarna om [iOS](https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment)- och [Android](https://channel9.msdn.com/Series/IntuneEnrollment/Android-Enrollment)-registrering. 


#### <a name="setup-checklist-section"></a>Avsnittet med checklistan för konfiguration

| Åtgärdsnamn | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| EnrollmentWrapUp | Uppmaning om att öppna sidan på företagsportalen | iOS/Android | **Avbryt** |
| EnrollmentWrapUp | Skärmen Registrerar enhet till slutet av **Läser in företagsresurser** | iOS/Android | Tog mer än 30 minuter |
| DeviceCategory | Val av enhetskategori (om administratören har konfigurerat det) tills användaren klickar på **Klar** | iOS/Android | Tog mer än 30 minuter |
| PreEnrollmentWizard | Skärmen Konfigurera åtkomst när registreringen har påbörjats men användaren har återvänt till åtkomstkonfigurationen | iOS/Android| **Senarelägg** |
| PreEnrollmentWizard | Skärmen Konfigurera åtkomst tills användaren klickar på **Nästa** på skärmen **Vad händer nu?** | iOS/Android | Tog mer än 30 minuter |

#### <a name="platform-screens-section"></a>Avsnittet med plattformsskärmar

| Åtgärdsnamn | Skärm eller flöde | Plattform | Action |
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

| Åtgärdsnamn | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| TermsofUse | Användningsvillkor (om administratören har konfigurerat det) | iOS/Android | **Avböj alla** |
| TermsofUse | Användningsvillkor tills **Godkänn allt** | iOS/Android | Tog mer än 30 minuter |

#### <a name="complianceactivation-section"></a>Avsnittet om efterlevnad/aktivering

| Åtgärdsnamn | Skärm eller flöde | Plattform | Action |
| ---- |---- |---- |---- |
| Efterlevnad | Enhetsefterlevnad (om administratören har konfigurerat det) visas som icke-grön vid åtkomstkonfiguration efter registreringen| iOS/Android | **Senarelägg** |
| Efterlevnad | Enhetsefterlevnad visas som icke-grön tills den uppdaterats att visas som grön | iOS/Android | Tog mer än 30 minuter |
| Aktivering | Aktiveringsregistreringen (om administratören har konfigurerat det) visas som icke-grön vid åtkomstkonfigurationen | iOS/Android | **Senarelägg** |
| Efterlevnad | Enhetsaktivering visas som icke-grön tills den uppdaterats att visas som grön | iOS/Android | Tog mer än 30 minuter |

## <a name="next-steps"></a>Nästa steg

När du har granskat statistiken för ofullständiga registreringar kan du gå igenom [registreringsalternativen](enrollment-options.md) och se om du kan göra några ändringar för att förbättra registreringen.
