---
title: "Synkronisera Active Directory och lägga till användare i Intune | Microsoft Intune"
description: "Beskriver hur du synkroniserar lokala användare med Azure AD och beviljar administratörsbehörigheter för din Intune-prenumeration"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 49eb9d1658df352c68677eaa3f29e1d57c43947e


---


# Synkronisera Active Directory och lägga till användare i Intune
Du kan konfigurera katalogsynkronisering om du vill importera användarkonton från organisationens lokala Active Directory till Microsoft Azure Active Directory (Azure AD). När din lokala Active Directory-tjänst är ansluten till alla dina Azure Active Directory-baserade tjänster blir hanteringen av användaridentiteter mycket enklare. Du kan också konfigurera funktioner för enkel inloggning som gör autentiseringen av dina användare välbekant och enkel.

Och för att göra saker ännu enklare när du använder flera tjänster med samma [Azure AD-klient](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant) så är de användarkonton som du tidigare synkroniserade tillgängliga för alla molnbaserade tjänster som delar samma Azure AD-klientprenumeration.

## Synkronisera lokala användare med Azure AD
Det enda verktyg som du behöver för att synkronisera dina användarkonton med Azure AD är [Azure AD Connect-guiden](https://www.microsoft.com/download/details.aspx?id=47594). Azure AD Connect-guiden är verktyget som steg för steg hjälper dig att ansluta den lokala identitetsinfrastrukturen till molnet.  Välj din topologi och dina behov (en eller flera kataloger, lösenordssynkronisering eller federation) så distribuerar och konfigurerar guiden alla komponenter som krävs för att få igång din anslutning. Exempel: Sync Services, Active Directory Federation Services (AD FS) och Azure AD PowerShell-modulen.

> [!TIP]
> Azure AD Connect innehåller funktioner som tidigare lanserats som Dirsync och Azure AD Sync. Lär dig mer om [katalogintegrering](http://technet.microsoft.com/library/jj573653.aspx). Mer information om fördelarna med att synkronisera användarkonton från din lokala katalog till Azure AD finns i [Likheter mellan Active Directory och Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## Bevilja administratörsbehörighet
När du har lagt till användare i din Intune-prenumeration rekommenderar vi att du ger några av användarkontona [administratörsbehörighet](administrative-accounts-websites-perms.md). Vilken konsol du använder för att tilldela administratörsbehörighet är beroende av vilken administratörstyp du vill tilldela:

-   **Innehavaradministratör**: Använd **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]** om du vill att den här typen av administratör ska hantera din prenumeration, inklusive fakturering, molnlagring och hantering av användare som kan använda [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **Tjänstadministratör**: Använd **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]** om du vill att den här typen av administratör ska utföra dagliga uppgifter, t.ex. hantering av mobila enheter eller datorer, distribution av principer eller programvara samt rapportkörning.


### Nästa steg
Gratulerar! Du är klar med steg 3 i *snabbstartsguiden för Intune*.

>[!div class="step-by-step"]

>[&larr; **Domäninställningar**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Hantera Intune-licenser** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jul16_HO4-->


