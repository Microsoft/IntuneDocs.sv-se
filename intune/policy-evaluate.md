---
title: Ta reda på hur många användare som omfattas av en princip
titlesuffix: Microsoft Intune
description: Ta reda på hur många användare som omfattas av en princip
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/09/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38e8a2e2-2329-11e8-b467-0ed5f89f718b
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 12e770a549d300b10000fa83ab68a0b6f3393b71
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238361"
---
# <a name="evaluate-how-many-users-are-targeted-by-a-policy"></a>Utvärdera hur många användare som omfattas av en princip
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda knappen **Utvärdera** för att ta reda på hur många användare som omfattas av en enhetsefterlevnads- eller enhetskonfigurationsprincip. Den här funktionen beräknar endast användare, inte enheter.

1.  I [Intune i Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsefterlevnad** eller **Enhetskonfiguration** och sedan **Principer**.
2.  Välj en av principerna, eller skapa en ny, och välj sedan **Tilldelningar**.
3.  Välj **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av principen.

Om knappen **Utvärdera** är nedtonad kontrollerar du att principen har tilldelats till en eller flera grupper.

