---
title: Skapa en anpassad roll i Intune
description: Lär dig hur du skapar en anpassad roll i Microsoft Intune.
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
ms.openlocfilehash: b60e4d801d09a834e11119260d3054cf43251bbd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502969"
---
# <a name="create-a-custom-role-in-intune"></a>Skapa en anpassad roll i Intune

Du kan skapa en anpassad Intune-roll som innehåller alla behörigheter som krävs för en viss arbetsfunktion. Till exempel, om en IT-avdelningsgrupp hanterar applikationer, principer och konfigurationsprofiler kan du lägga till alla dessa behörigheter i en enda anpassad roll. När du har skapat en anpassad roll kan du [tilldela](assign-role.md) den till alla användare som behöver dessa behörigheter.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune Service-administratör**

## <a name="to-create-a-custom-role"></a>Skapa en anpassad roll

1. Logga in i [Azure-portalen](https://portal.azure.com) med dina inloggningsuppgifter för Intune.

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune** > **Roller** > **Alla roller** > **Lägg till**.

4. På bladet **Lägg till anpassad roll** anger du namn och beskrivning för den nya rollen och klickar sedan på **Behörigheter**.

5. På bladet **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen.

6. På bladet **Omfång (taggar)** väljer du taggarna för den här rollen. Den här rollen kan komma åt resurser som också har dessa taggar.

7. När du är klar väljer du **OK**.

8. På bladet **Lägg till anpassad roll** klickar du på **Skapa**. Den nya rollen visas i listan på bladet **Intune-roller – Alla roller**.

## <a name="next-steps"></a>Nästa steg
- [Tilldela en användare en roll](assign-role.md)
- [Lär dig mer om rollbaserad åtkomstkontroll i Intune](role-based-access-control.md)
