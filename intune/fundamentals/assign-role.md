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
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 780a248f16a8a5028875c9c2401921ea23d0af24
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76540936"
---
# <a name="assign-a-role-to-an-intune-user"></a>Tilldela en roll till en Intune-användare

Du kan tilldela en [inbyggd](role-based-access-control.md#built-in-roles) eller [anpassad](create-custom-role.md) roll till en Intune-användare.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune Service-administratör**

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) går du till **Klientadministratör** > **Roller** > **Alla roller**.

2. På bladet **Intune-roller – Alla roller** väljer du den inbyggda roll som du vill tilldela.

3. På bladet <*rollnamn*> – **Översikt** väljer du **Hantera** > **Tilldelningar**.

4. På bladet anpassad roll väljer du **Tilldela**.

5. På bladet **Rolltilldelningar** anger du ett **Tilldelningsnamn** och en valfri **Tilldelningsbeskrivning** för tilldelningen.

6. I **Medlemmar (grupper)** väljer du den grupp som innehåller användaren som du vill ge behörighet till.

7. För **Omfång (grupper)** väljer du en grupp som innehåller de användare/enheter som ovanstående medlem ska kunna hantera.

8. För **Omfång (taggar)** väljer du de taggar som den här rolltilldelningen ska tillämpas på.

9. När du är klar väljer du **OK**. Den nya tilldelningen visas i listan över tilldelningar.


## <a name="next-steps"></a>Nästa steg
- [Lär dig mer om rollbaserad åtkomstkontroll i Intune](role-based-access-control.md)
- [Skapa en anpassad roll](create-custom-role.md)
