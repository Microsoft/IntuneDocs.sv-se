---
title: Tilldela en roll till en Intune-användare
description: Lär dig hur du tilldelar en inbyggd eller anpassad roll till en användare i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83e321e932fa2214612836ec994a9a0aa8174dd7
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722208"
---
# <a name="assign-a-role-to-an-intune-user"></a>Tilldela en roll till en Intune-användare

Du kan tilldela en [inbyggd](role-based-access-control.md#built-in-roles) eller [anpassad](create-custom-role.md) roll till en Intune-användare.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune Service-administratör**

1. Logga in på [Azure-portalen](https://portal.azure.com).

2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.

3. På bladet **Intune** väljer du **Roller** > **Alla roller**.

4. På bladet **Intune-roller – Alla roller** väljer du den inbyggda roll som du vill tilldela.

5. På bladet <*rollnamn*> – **Översikt** väljer du **Hantera** > **Tilldelningar**.

6. På bladet anpassad roll väljer du **Tilldela**.

7. På bladet **Rolltilldelningar** anger du ett **Tilldelningsnamn** och en valfri **Tilldelningsbeskrivning** för tilldelningen.

8. I **Medlemmar (grupper)** väljer du den grupp som innehåller användaren som du vill ge behörighet till.

9. För **Omfång (grupper)** väljer du en grupp som innehåller de användare/enheter som ovanstående medlem ska kunna hantera.

10. För **Omfång (taggar)** väljer du de taggar som den här rolltilldelningen ska tillämpas på.

11. När du är klar väljer du **OK**. Den nya tilldelningen visas i listan över tilldelningar.


## <a name="next-steps"></a>Nästa steg
- [Lär dig mer om rollbaserad åtkomstkontroll i Intune](role-based-access-control.md)
- [Skapa en anpassad roll](create-custom-role.md)
