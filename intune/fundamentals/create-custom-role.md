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
ms.openlocfilehash: bfa2758546595d1e6237d88e128958c50759eb04
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569191"
---
# <a name="create-a-custom-role-in-intune"></a>Skapa en anpassad roll i Intune

Du kan skapa en anpassad Intune-roll som innehåller alla behörigheter som krävs för en viss arbetsfunktion. Till exempel, om en IT-avdelningsgrupp hanterar applikationer, principer och konfigurationsprofiler kan du lägga till alla dessa behörigheter i en enda anpassad roll. När du har skapat en anpassad roll kan du [tilldela](assign-role.md) den till alla användare som behöver dessa behörigheter.

För att kunna skapa, redigera eller tilldela roller måste ditt konto ha en av följande behörigheter i Azure AD:
- **Global administratör**
- **Intune Service-administratör**

## <a name="to-create-a-custom-role"></a>Skapa en anpassad roll

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Innehavaradministratör** > **Roller** > **Alla roller** > **Skapa**.

2. På sidan **Grundläggande inställningar** anger du ett namn och en beskrivning för den nya rollen. Välj sedan **Nästa**.

3. På sidan **Behörigheter** väljer du de behörigheter som du vill använda med den här rollen.

4. På sidan **Omfång (taggar)** väljer du taggarna för den här rollen. Den här rollen kan komma åt resurser som också har dessa taggar. Välj **Nästa**.

5. Välj **Skapa**på sidan **Granska + skapa** när du är klar. Den nya rollen visas i listan på bladet **Intune-roller – Alla roller**.

## <a name="copy-a-role"></a>Kopiera en roll

Du kan även kopiera en befintlig roll.

1. Gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Innehavaradministratör** > **Roller** > **Alla roller** > markera kryssrutan för en roll i listan > **Duplicera**.

2. Ange ett namn på sidan **Grundläggande inställningar**. Se till att du använder ett unikt namn.

3. Alla behörigheter och omfångstaggar från den ursprungliga rollen är redan markerade. Du kan senare ändra den duplicerade rollens **Namn**, **Beskrivning**, **Behörigheter**och **Omfång (taggar)** .

4. När du har gjort alla ändringar väljer du **Nästa** för att komma till sidan **Granska + skapa**. Välj **Skapa**. 

## <a name="next-steps"></a>Nästa steg
- [Tilldela en användare en roll](assign-role.md)
- [Lär dig mer om rollbaserad åtkomstkontroll i Intune](role-based-access-control.md)


