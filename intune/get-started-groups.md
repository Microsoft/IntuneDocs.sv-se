---
title: Skapa en grupp i Microsoft Intune
titleSuffix: ''
description: Dela upp användare i grupper för att göra det lättare att hantera principer och appar som de har åtkomst till.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fcf6f3071e50304216a182a21dd542cace1b6390
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186468"
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>Skapa en grupp för att hantera användare och dataåtkomst

Grupper används för att hantera användare och styra de anställdas åtkomst till företagets resurser. Resurserna kan tillhöra din katalog eller kan vara externa resurser, till exempel SaaS-appar eller SharePoint-webbplatser.

Microsoft Intune använder Azure Active Directory (Azure AD) för att hantera åtkomst till företagsresurser. Den här åtkomsten kontrolleras med hjälp av roller i katalogen. Intune hanterar sedan den åtkomsten för mobila enheter, vilket ger medlemmar i gruppen åtkomst till resurserna.

## <a name="how-do-i-create-a-group"></a>Hur gör jag för att skapa en grupp?

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. När du har öppnat fönstret **Microsoft Intune** väljer du **Grupper**.
4. Välj kommandot **Ny grupp** i fönstret **Användare och grupper – Alla grupper**.
5. Välj **Grupptyp** i fönstret **Grupp**.
5. Ange ett **namn** och en **beskrivning** för vyn.
6. Ange **Tilldelad** som **medlemskapstyp**. Välj inte **Aktivera Office-funktioner** för testgruppen.
7. Välj **medlemmar** för gruppen.
7. Klicka på **Skapa**.

Om du har skapat en grupp ska den visas i listan **Alla grupper**. Om den inte visas där försöker du skapa en annan grupp.

## <a name="next-steps"></a>Nästa steg

[Kom igång med principer](get-started-policies.md) – Skapa principer som hindrar användare från att använda enheten på ett otillåtet sätt.

## <a name="learn-more"></a>Läs mer

* [Ställa in registreringsbegränsningar med hjälp av grupper i Intune](groups-add.md)
* [Hantera åtkomst till företagsresurser med grupper i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
