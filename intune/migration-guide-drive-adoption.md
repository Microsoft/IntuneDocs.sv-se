---
title: "Genomför slutanvändarinförande med villkorlig åtkomst"
description: "Syftet med den här artikeln är att ge insikter om hur du kan använda villkorlig åtkomst för att underlätta Intune-registreringen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0b2fbcc1d63f229e1b63873841bc300bdde92fa3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="drive-end-user-adoption-with-conditional-access"></a>Genomför slutanvändarinförande med villkorlig åtkomst

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Att aktivera villkorliga åtkomstfunktioner med Intune, t.ex. blockera e-post för ej registrerade enheter, kan bidra till att underlätta registrering och efterlevnad, men det krävs inte för att migreringen ska lyckas. Dina migreringsmål och säkerhetskrav ska ge önskat resultat.

## <a name="migration-campaign-with-conditional-access"></a>Migreringskampanj med villkorlig åtkomst

Detta är en vanlig metod när man vill förbättra en migreringskampanj med villkorlig åtkomst:

1.  Ange att regler för villkorlig åtkomst ska tillämpas för alla användare, men exkludera uttryckligen de användare som måste migrera från den gamla MDM-providern. Du kan skapa en Azure AD-användargrupp med alla de användare som undantagits från villkorlig åtkomst.

2.  När användarna migrerar kan du ta bort dem från gruppen med användare som undantagits från villkorlig åtkomst.

3.  När migreringen är klar kan du konfigurera alla principer för villkorlig åtkomst så att de blockerar som standard såvida inte Intune tillåter åtkomst.

### <a name="advantages"></a>Fördelar

-   Tillhandahåller åtkomstkontroll för nya användarkonton eller användarkonton som inte hanterades av den tidigare lösningen.

-   Tillhandahåller en respitperiod för migreringen för användare av den tidigare lösningen.

-   Minimerar produktivitetsförlust

### <a name="disadvantages"></a>Nackdelar

-   Användare av den tidigare lösningen kan eventuellt få åtkomst till resurser som använder ohanterade enheter innan den villkorliga åtkomsten aktiveras för dessa användare.

> [!TIP]
> Det här är ett sätt av flera. Du kan välja en enklare process som skjuter upp all villkorlig åtkomst till efter det att varje fas har instruerats om registrering, eller så kan du välja en striktare process som tillämpar villkorlig åtkomst direkt från start och som kräver fullständig efterlevnad för all åtkomst.

-   Läs mer om [villkorlig åtkomst](/intune/conditional-access).

## <a name="task-list-for-conditional-access"></a>Uppgiftslista för villkorlig åtkomst

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Uppgift 1: Bestäm hur du tänker implementera villkorlig åtkomst

[Vanliga sätt att använda villkorlig åtkomst på](/intune/conditional-access-intune-common-ways-use).

### <a name="task-2-set-up-intune-conditional-access"></a>Uppgift 2: Konfigurera villkorlig åtkomst för Intune

Välj något av följande alternativ:

-   [Konfigurera villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [Install Exchange Connector lokalt med Intune](/intune/exchange-connector-install)

-   [Konfigurera appbaserade principer för villkorlig åtkomst för Exchange Online](/intune/app-based-conditional-access-intune-exchange-online-create)

-   [Konfigurera appbaserade principer för villkorlig åtkomst för SharePoint Online](/intune/app-based-conditional-access-intune-sharepoint-online-create)

-   [Blockera appar som inte använder modern autentisering (ADAL)](/intune/app-modern-authentication-block)

## <a name="next-steps"></a>Nästa steg

[Typisk migreringscykel](migration-guide-cycle.md)
