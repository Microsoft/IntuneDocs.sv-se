---
title: "Konfigurera ett eget domännamn | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed26d65b98a0ae1bbc4fbac682fb53fddd50b4e5
ms.openlocfilehash: a202f06fef0bc8b7eec730728ec10e5fbf234902


---


# Så här konfigurerar du ett eget domännamn

Som standard använder Intune domännamnet **<domain>.onmicrosoft.com** som skapades när du började prenumerera på tjänsten. Om din organisation äger en anpassad domän kan du konfigurera din instans av Intune att använda den domänen i stället för domännamnet som följer med din prenumeration.

Innan du skapar nya användarkonton eller synkroniserar konton från Active Directory, rekommenderar vi starkt att du bestämmer om du bara ska använda domänen .onmicrosoft.com eller om du ska lägga till ett eller flera av dina egna domännamn. Att konfigurera en anpassad domän innan du lägger till användare kan underlätta hanteringen av användaridentiteter för prenumerationen, genom att du gör det möjligt för användarna att logga in med de autentiseringsuppgifter de använder för att komma åt andra resurser i domänen.

När du prenumererar på en molnbaserad tjänst från Microsoft blir din instans av den tjänsten en Microsoft [Azure AD-klient](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), som tillhandahåller identitets- och katalogtjänster för din molnbaserade tjänst. Och eftersom stegen för att konfigurera Intune att använda din organisations anpassade domännamn är samma som för andra Azure AD-klienter, kan du använda informationen och procedurerna i [Lägg till din domän](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Mer information om hur du använder domänen med en molnbaserad tjänst från Microsoft finns i [Översikt över anpassade domännamn i Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

### Nästa steg
Gratulerar! Du är klar med steg 2 i *snabbstartsguiden för Intune*.

>[!div class="step-by-step"]

>[&larr; **Logga in i Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Lägga till användare i Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Jun16_HO4-->


