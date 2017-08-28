---
title: "Kom igång med grupper"
titleSuffix: Intune on Azure
description: "Dela upp användare i grupper för att göra det lättare att hantera principer och appar som de har åtkomst till."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 276a594abdd3c92051041a5faa34d3ee7633e32c
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2017
---
# <a name="get-started-with-groups"></a>Kom igång med grupper

Grupper används för att hantera användare och styra anställdas åtkomst till företagsresurserna. Resurserna kan tillhöra din katalog eller kan vara externa resurser, till exempel SaaS-appar eller SharePoint-webbplatser.

Microsoft Intune använder Azure Active Directory (Azure AD) för att hantera åtkomst till företagsresurser. Den här åtkomsten kontrolleras med hjälp av roller i katalogen. Intune hanterar sedan den åtkomsten för mobila enheter, vilket ger medlemmar i gruppen åtkomst till resurserna.

## <a name="how-do-i-create-a-group"></a>Hur gör jag för att skapa en grupp?

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Sök efter **Intune** med hjälp av **Sök resurser**.
3. När du har öppnat bladet **Microsoft Intune** väljer du **Grupper**.
4. Välj kommandot **Ny grupp** på bladet **Användare och grupper – Alla grupper**.
5. Lägg till ett **namn** på och en **beskrivning** av gruppen på bladet **Grupp**.
6. Ange **Tilldelad** som **medlemskapstyp**. Välj inte **Aktivera Office-funktioner** för testgruppen.
7. Klicka på **Skapa**.

Om du har skapat en grupp ska den visas i listan **Alla grupper**. Om den inte visas där försöker du skapa en annan grupp.

## <a name="next-steps"></a>Nästa steg

[Kom igång med principer](get-started-policies.md) - Skapa principer som hindrar användare från att använda enheten på ett obehörigt sätt.

## <a name="learn-more"></a>Läs mer

* [Ställa in registreringsbegränsningar med hjälp av grupper i Intune](groups-add.md)
* [Hantera åtkomst till företagsresurser med grupper i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
