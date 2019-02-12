---
title: Ta reda på hur många användare som omfattas av en princip
titlesuffix: Microsoft Intune
description: Ta reda på hur många användare som omfattas av en princip
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 38e8a2e2-2329-11e8-b467-0ed5f89f718b
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b059d3512576faaa6049bd2c91be9e94ff919058
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55844317"
---
# <a name="evaluate-how-many-users-are-targeted-by-a-policy"></a>Utvärdera hur många användare som omfattas av en princip
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda knappen **Utvärdera** för att ta reda på hur många användare som omfattas av en enhetsefterlevnads- eller enhetskonfigurationsprincip. Den här funktionen beräknar endast användare, inte enheter.

1.  I [Intune i Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsefterlevnad** eller **Enhetskonfiguration** och sedan **Principer**.
2.  Välj en av principerna, eller skapa en ny, och välj sedan **Tilldelningar**.
3.  Välj **Utvärdera**. Ett meddelande visas med hur många användare som omfattas av principen.

Om knappen **Utvärdera** är nedtonad kontrollerar du att principen har tilldelats till en eller flera grupper.

