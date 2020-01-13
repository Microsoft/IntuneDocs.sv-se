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
ms.openlocfilehash: 68c2dc7df123593513c14e16e2626c7426f50b01
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207425"
---
# <a name="create-a-custom-role-in-intune"></a>Skapa en anpassad roll i Intune

Du kan skapa en anpassad Intune-roll som innehåller alla behörigheter som krävs för en viss arbetsfunktion. Till exempel, om en IT-avdelningsgrupp hanterar applikationer, principer och konfigurationsprofiler kan du lägga till alla dessa behörigheter i en enda anpassad roll. När du har skapat en anpassad roll kan du [tilldela](assign-role.md) den till alla användare som behöver dessa behörigheter.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune Service-administratör**

## <a name="to-create-a-custom-role"></a>Skapa en anpassad roll

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Roller** > **Alla roller** > **Lägg till**.

2. På bladet **Lägg till anpassad roll** anger du namn och beskrivning för den nya rollen och klickar sedan på **Behörigheter**.

3. På bladet **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen.

4. På bladet **Omfång (taggar)** väljer du taggarna för den här rollen. Den här rollen kan komma åt resurser som också har dessa taggar.

5. När du är klar väljer du **OK**.

6. På bladet **Lägg till anpassad roll** klickar du på **Skapa**. Den nya rollen visas i listan på bladet **Intune-roller – Alla roller**.


## <a name="copy-a-role"></a>Kopiera en roll

Du kan även kopiera en befintlig roll.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Roller** > **Alla roller** > välj en roll i listan > **Duplicera**.

2. Under **Duplicera roll** anger du ett namn. Se till att du använder ett unikt namn.

3. Alla behörigheter och omfångstaggar från den ursprungliga rollen är redan markerade. Du kan senare ändra den duplicerade rollens **Namn**, **Beskrivning**, **Behörigheter**och **Omfång (taggar)** .

4. Välj **Skapa**. 

## <a name="next-steps"></a>Nästa steg
- [Tilldela en användare en roll](assign-role.md)
- [Lär dig mer om rollbaserad åtkomstkontroll i Intune](role-based-access-control.md)
