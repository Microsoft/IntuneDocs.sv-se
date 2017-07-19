---
title: "Kom igång med grupper"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 04843a918a3c661ab69dfa711f4d22a8feedf5f3
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-groups"></a>Kom igång med grupper

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[](./media/generic-users-groups.png)

Microsoft Intune använder Azure Active Directory (Azure AD) för [hantering av åtkomst till företagsresurser](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups). Den här åtkomsten kontrolleras med hjälp av roller i katalogen. Intune hanterar sedan den åtkomsten för mobila enheter, vilket ger medlemmar i gruppen åtkomst till resurserna.

__Hur skapar jag en grupp?__

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Sök efter **användare och grupper** med hjälp av **Sök resurser**.
3. När du har öppnat bladet **Användare och grupper** väljer du **Alla grupper**.
4. Välj kommandot **Ny grupp** på bladet **Användare och grupper – Alla grupper**.
5. Lägg till ett **namn** på och en **beskrivning** av gruppen på bladet **Grupp**.
6. Ange **Tilldelad** som **medlemskapstyp**. Välj inte **Aktivera Office-funktioner** för testgruppen.
7. Klicka på **Skapa**.

Om du har skapat en grupp ska den visas i listan **Alla grupper**. Om den inte visas där försöker du skapa en annan grupp.
