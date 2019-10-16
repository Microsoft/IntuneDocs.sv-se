---
title: Datainsamling i Intune
titleSuffix: Microsoft Intune
description: Lär dig hur personliga data samlas in i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1171740-936d-46a5-af37-f418bd6fa63e
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d0de4b1ae930ebeff07539f9cfa8848f0b7ce
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306909"
---
# <a name="data-collection-in-intune"></a>Datainsamling i Intune

När användare registrerar sina företagsenheter eller personliga enheter med Intune samlar Intune in och delar vissa personliga data. Intune samlar in personliga data från följande källor:

- Administratörens användning av Intune i Azure-portalen.
- Slutanvändarenheter (när de registreras för hantering av Intune och under användning).
- Kundkonton på tjänster från tredje part (enligt administratörens anvisningar).
- Information om diagnostik, prestanda och användning.

Från dessa källor samlar Intune in data som tillhör följande tre kategorier: [identifierade](#identified-data), [pseudonymiserade](#pseudonymized-data), och [aggregerade](#aggregated-data).

> [!NOTE]
> Vi säljer inte några data som samlas in av vår tjänst till någon tredje part av någon anledning.

## <a name="identified-data"></a>Identifierade data

De flesta personliga data som samlas in av Intune är identifierade data. Dessa data är kopplade till en användare, en enhet eller ett program och är av stor vikt för hantering. Identifierade data används för att hantera en användares enhet och program och för att etablera Intune-tjänsten.

Identifierade data som samlas in av Intune kan inkludera, men är inte begränsade till: 

- Användarinformation
  - Ägarens namn/användarens visningsnamn (det Azure-registrerade namnet för användaren som identifieras av AzureUserID)
  - Användarens huvudnamn eller e-postadress
  - Användaridentifierare från tredje part (till exempel AppleID)
- Information om maskinvaruinventering
  - Enhetsnamn
  - Tillverkare
  - Operativsystem
  - Serienummer
  - IMEI-numret
  - IP-adress
  - Wi-Fi-Mac-adress
  - ICCID
  - Telefonnummer
- Information om spårningslogg, inklusive data om följande aktiviteter
  - Hantera
  - Skapa
  - Uppdatera (redigera)
  - Ta bort
  - Tilldela
  - Fjärråtgärder
- Supportinformation
  - Kontaktinformation (namn, telefonnummer, e-postadress)
  - E-postdiskussioner med Microsofts teammedlemmar om support, produkter och/eller kundupplevelser
- Information om åtkomstkontroll (Intune använder dessa data för att hantera åtkomst till administrativa roller och funktioner via funktioner som [rollbaserad åtkomstkontroll](../fundamentals/role-based-access-control.md).
  - Statiska autentiserare (kundens lösenord)
  - Sekretessnycklar för certifikat 
- Administratörs- och kontoinformation
  - Administratörsanvändares för- och efternamn
  - Administratörs användarnamn
  - UPN (e-post)
  - Telefonnummer
  - Kontoägarens e-postadress
  - Active Directory-ID för varje kunds IT-administratör
  - Betalningsdata för kundfakturering
  - Prenumerationsnyckel
- Programinventering såsom
  - appnamn
  - version
  - app-ID
  - ikoner
  - installationsplats
  - Programinventeringsdata samlas endast in om enheten har markerats av administratören som en företagsägd enhet eller om funktionen för kompatibel app har aktiverats.  
- Tredjeparts-ID: för kunden såsom Apple-ID. 

## <a name="pseudonymized-data"></a>Pseudonymiserade data

Pseudonymiserade data är associerade med en unik identifierare, vanligtvis ett tal som genereras av systemet som inte ensamt kan identifiera en enskild person men som används för att tillhandahålla företagstjänster till användare. 

Pseudonymiserade data som samlas in av Intune kan inkludera, men är inte begränsade till: 

- Diagnostik-, prestanda- och användningsdata som är kopplade till en användare och/eller en enhet
  - Det antal gånger som en funktion används
  - De kommandon som finns för funktionen
  - Svarstiden för en tjänst
  - Slutförandefrekvenser för installationer och andra processer
  - Programfel i Intune-företagsportalen
  - Användar- och enhetsidentifierare
  - Identifierare för referens-, korrelations- och hanteringsändamål 
- Enhetsdata som inte är kopplade till en enhet eller en användare (om dessa data är kopplade till en enhet eller en användare behandlar Intune dem som identifierade data)
  - Id för Intune-enhet
  - Azure Active Directory-enhets-ID
  - Intune-enhetshantering-ID
  - Klientorganisations-ID
  - Konto-ID
  - EAS-enhets-ID
  - Plattformsspecifika ID:n
  - AppleID för iOS-enheter
  - Mac-adress för Mac-enheter
  - Windows-ID för Windows-enheter
- Information om hanterat program
  - ID för hanterat program
  - Enhetstagg för hanterat program
  - Intune-enhetshantering-ID
  - Azure Active Directory-enhets-ID
  - Krypteringsnycklar

## <a name="aggregated-data"></a>Aggregerade data

Aggregerade data används för att etablera och förbättra Intune-tjänsten. 

Aggregerade data som samlas in av Intune kan inkludera, men är inte begränsade till: 

- Administratörsanvändningsdata från alla Intune-klientorganisationer (till exempel administratörskontroller som väljs vid interaktion med administratörskonsolen)
- Information om klientorganisationskonto (dessa data är tillgängliga från Intune-bladet)
  - Antalet enheter eller användare som är registrerade
  - Antalet identifierade enhetsplattformar  
  - Antalet installerade enheter
  - installedDeviceCount: det antal enheter som programmet har installerats på.
  - notApplicableDeviceCount: det antal enheter som programmet inte är tillämpligt för.
  - notInstalledDeviceCount: det antal enheter som programmet är tillämpligt för men inte installerat på.
  - pendingInstallDeviceCount: det antal enheter som programmet är tillämpligt för och för vilka installation väntar.

## <a name="next-steps"></a>Nästa steg

Lär dig mer om hur Intune [lagrar och bearbetar](privacy-data-store-process.md) samt [delar](privacy-data-secure-share.md) personliga data. 
