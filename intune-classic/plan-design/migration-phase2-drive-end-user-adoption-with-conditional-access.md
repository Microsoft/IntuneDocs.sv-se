---
title: "Genomför slutanvändarinförande med villkorlig åtkomst | Microsoft Docs"
description: "Syftet med den här artikeln är att ge insikter om hur du kan använda villkorlig åtkomst för att underlätta Intune-registreringen."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 55e437fa33af9d27223798cbac9f541b0bc1be2d
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="phase-2-drive-end-user-adoption-with-conditional-access"></a>Fas 2: Genomför slutanvändarinförande med villkorlig åtkomst

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

-   Läs mer om [villkorlig åtkomst](https://docs.microsoft.com/intune/conditional-access).

## <a name="task-list-for-conditional-access"></a>Uppgiftslista för villkorlig åtkomst

### <a name="task-1-get-ready-for-intune-conditional-access"></a>Uppgift 1: Förbered villkorlig åtkomst för Intune

-   Lär dig [hur man konfigurerar villkorlig åtkomst](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="task-2-set-up-intune-conditional-access"></a>Uppgift 2: Konfigurera villkorlig åtkomst för Intune

Välj någon av följande principtyper för villkorlig åtkomst om du vill veta mer:

-   [Exchange Online och nya Exchange Online Dedicated](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)

-   [Exchange On-premises och äldre Exchange Online Dedicated](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)

-   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

-   [Skype för företag – Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)

-   [Dynamics CRM Online](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)

-   [Exempelscenarion för e-poståtkomst](/intune-classic/deploy-use/restrict-email-access-example-scenarios)

## <a name="next-steps"></a>Nästa steg

[Fas 2: Normal migreringscykel](/intune-classic/plan-design/migration-phase2-typical-migration-cycle)

