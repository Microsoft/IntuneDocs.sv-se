---
title: Skapa en grupp i Microsoft Intune
titleSuffix: 
description: "Dela upp användare i grupper för att göra det lättare att hantera principer och appar som de har åtkomst till."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e052f7c8d5742859d009816473fe97a98c499b17
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Skapa en grupp för att hantera användare och dataåtkomst

Grupper används för att hantera användare och styra de anställdas åtkomst till företagets resurser. Resurserna kan tillhöra din katalog eller kan vara externa resurser, till exempel SaaS-appar eller SharePoint-webbplatser.

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

[Kom igång med principer](get-started-policies.md) – Skapa principer som hindrar användare från att använda enheten på ett otillåtet sätt.

## <a name="learn-more"></a>Läs mer

* [Ställa in registreringsbegränsningar med hjälp av grupper i Intune](groups-add.md)
* [Hantera åtkomst till företagsresurser med grupper i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
