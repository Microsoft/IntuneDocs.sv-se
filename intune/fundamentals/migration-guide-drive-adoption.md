---
title: Genomför slutanvändarinförande med villkorlig åtkomst
titleSuffix: Microsoft Intune
description: Lär dig mer om att använda villkorlig åtkomst för att genomföra registrering i Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 115313816542fd642e6a0c67900abd48b7146e42
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510063"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Genomföra slutanvändarinförande med villkorlig åtkomst i Microsoft Intune

Aktivering av funktioner för villkorlig åtkomst med Intune, t.ex. blockering av e-post för oregistrerade enheter, kan vara positivt i registrerings- och efterlevnadshänseende, men krävs inte för att migreringen ska lyckas. Dina migreringsmål och säkerhetskrav ska ge önskat resultat.

## <a name="migration-campaign-with-conditional-access"></a>Migreringskampanj med villkorlig åtkomst

Detta är en vanlig metod när man vill förbättra en migreringskampanj med villkorlig åtkomst:

1. Ange att regler för villkorlig åtkomst ska tillämpas för alla användare, men exkludera uttryckligen de användare som måste migrera från den gamla MDM-providern. Du kan skapa en Azure AD-användargrupp med alla de användare som undantagits från villkorlig åtkomst.

2. När användarna migrerar kan du ta bort dem från gruppen med användare som undantagits från villkorlig åtkomst.

3. När migreringen är klar, kan du konfigurera alla principer för villkorlig åtkomst så att de blockerar som standard, såvida inte Intune tillåter åtkomst.

### <a name="advantages"></a>Fördelar

- Tillhandahåller åtkomstkontroll för nya användarkonton eller användarkonton som inte hanterades av den tidigare lösningen.

- Tillhandahåller en respitperiod för migreringen för användare av den tidigare lösningen.

- Minimerar produktivitetsförlust

### <a name="disadvantages"></a>Nackdelar

- Potentiellt kan användare av en tidigare lösning få åtkomst till resurser med hjälp av ohanterade enheter innan den villkorliga åtkomsten aktiveras för dessa användare.


Det här är ett sätt av flera. Du kan välja en enklare process som skjuter upp all villkorlig åtkomst till efter det att varje fas har instruerats om registrering, eller så kan du välja en striktare process som tillämpar villkorlig åtkomst direkt från start och som kräver fullständig efterlevnad för all åtkomst.

- Läs mer om [villkorlig åtkomst](../protect/conditional-access.md).

## <a name="task-list-for-conditional-access"></a>Uppgiftslista för villkorlig åtkomst

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>Uppgift 1: Bestäm hur du tänker implementera villkorlig åtkomst

[Vanliga sätt för att använda villkorlig åtkomst](../protect/conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>Uppgift 2: Konfigurera villkorlig åtkomst för Intune

Välj något av följande alternativ:

- [Konfigurera villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

- [Install Exchange Connector lokalt med Intune](../protect/exchange-connector-install.md)

- [Konfigurera appbaserade principer för villkorlig åtkomst för Exchange Online](../protect/app-based-conditional-access-intune-create.md)

- [Konfigurera appbaserade principer för villkorlig åtkomst för SharePoint Online](../protect/app-based-conditional-access-intune-create.md)

- [Blockera appar som inte använder modern autentisering (ADAL)](../protect/app-modern-authentication-block.md)

## <a name="next-steps"></a>Nästa steg

Läs mer om [den typiska migreringscykeln](../migration-guide-cycle.md).
