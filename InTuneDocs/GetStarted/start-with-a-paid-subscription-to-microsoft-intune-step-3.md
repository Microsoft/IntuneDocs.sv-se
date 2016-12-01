---
title: "Synkronisera Active Directory och lägga till användare i Intune | Microsoft Intune"
description: "Synkronisera lokala användare med Azure AD och bevilja administratörsbehörighet för din Intune-prenumeration"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>Synkronisera Active Directory och lägga till användare i Intune
Du kan konfigurera katalogsynkronisering om du vill importera användarkonton från organisationens lokala Active Directory till Microsoft Azure Active Directory (Azure AD). När din lokala Active Directory-tjänst är ansluten till alla dina Azure Active Directory-baserade tjänster blir hanteringen av användaridentiteter mycket enklare. Du kan också konfigurera funktioner för enkel inloggning som gör autentiseringen av dina användare välbekant och enkel.

Och för att göra saker ännu enklare när du använder flera tjänster med samma [Azure AD-klient](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) så är de användarkonton som du tidigare synkroniserade tillgängliga för alla molnbaserade tjänster som delar samma Azure AD-klientprenumeration.

## <a name="synchronize-on-premises-users-with-azure-ad"></a>Synkronisera lokala användare med Azure AD
Det enda verktyg som du behöver för att synkronisera dina användarkonton med Azure AD är [Azure AD Connect-guiden](https://www.microsoft.com/download/details.aspx?id=47594). Azure AD Connect-guiden är verktyget som steg för steg hjälper dig att ansluta den lokala identitetsinfrastrukturen till molnet.  Välj din topologi och dina behov (en eller flera kataloger, lösenordssynkronisering eller federation) så distribuerar och konfigurerar guiden alla komponenter som krävs för att få igång din anslutning. Exempel: Sync Services, Active Directory Federation Services (AD FS) och Azure AD PowerShell-modulen.

> [!TIP]
> Azure AD Connect innehåller funktioner som tidigare lanserats som Dirsync och Azure AD Sync. Lär dig mer om [katalogintegrering](http://technet.microsoft.com/library/jj573653.aspx). Mer information om fördelarna med att synkronisera användarkonton från din lokala katalog till Azure AD finns i [Likheter mellan Active Directory och Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-administrator-permissions"></a>Bevilja administratörsbehörighet

När du ska administrera Intune använder du:
- Två typer av administratörskonton
- Användarkonton med ytterligare behörighet
- Två webbaserade konsoler/portaler för administration som ger administratörerna tillgång till det de ska hantera.

När du har lagt till fler användare i din Intune-prenumeration rekommenderar vi att du ger några av användarkontona administratörsbehörighet Vilken konsol du använder för att tilldela administratörsbehörighet är beroende av vilken administratörstyp du vill tilldela:

-   **Innehavaradministratör**: Använd **Microsoft Intune-kontorportal** om du vill att den här typen av administratör ska hantera din prenumeration, inklusive fakturering, molnlagring och hantering av användare som kan använda.

-   **Tjänstadministratör**: Använd **Microsoft Intune-administratörskonsol** om du vill att den här typen av administratör ska utföra dagliga uppgifter, t.ex. hantering av mobila enheter eller datorer, distribution av principer eller programvara samt rapportkörning.

I följande avsnitt beskrivs dessa konton och portaler.

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>Administratörskonton och användarkonton med särskilda behörigheter

Nedan visas de konton och behörigheter som du ska använda för Intune.

### <a name="tenant-administrator"></a>Innehavaradministratör
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Innehavaradministratörer tilldelas en administratörsroll som definierar den administrativa omfattningen för den aktuella användaren och de aktiviteter som de kan hantera.<br /><br />Administratörsroller är gemensamma mellan de olika Microsoft-molntjänsterna, men vissa tjänster kanske inte stöder vissa roller.<br /><br /> Microsoft Intune använder följande roller:<br /><br />– Global administratör<br />– Faktureringsadministratör<br />– Lösenordsadministratör<br />– Tjänstsupportadministratör<br />– Administratör för användarhantering|Som standard är kontot du använder för att skapa Microsoft Intune-prenumerationen en innehavaradministratör med en global administratörsroll.<br /></br>  Som innehavaradministratör använder du [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] för att hantera prenumerationen för Intune och tilldela innehavaradministratörer från [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Använd en innehavaradministratör med en global administrationsroll för åtkomst till [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] och tilldela din första tjänstadministratör. Du bör inte använda en innehavaradministratör för dagliga uppgifter. En innehavaradministratör kräver inte någon licens till Intune för att få åtkomst till [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Innehavaradministratör är ett gemensamt begrepp mellan Microsofts molntjänster. När du prenumererar på Intune är tjänsten en innehavaradministratör för Microsoft Azure AD. Se avsnittet Azure AD-klient i [Vad är en Azure AD-katalog?](http://technet.microsoft.com/library/jj573650.aspx).|


### <a name="service-administrator"></a>Tjänstadministratör
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Tjänstadministratörer tilldelas en av följande behörigheter:<br /><br />**Fullständig åtkomst**: Ger åtkomst till alla delar av [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], utan begränsningar. Kan också lägga till och hantera andra tjänstadministratörer.<br /><br />**Skrivskyddad åtkomst**: Ger läsbehörighet till alla områden av [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. En skrivskyddad tjänstadministratör kan inte ändra data, men kan köra rapporter.<br /><br />**Supportavdelning – Gruppnod**: Ger behörigheter som gör det möjligt för tjänstadministratören att enbart genomföra en uppsättning uppgifter som vanligtvis är kopplade till supportavdelningsscenarion. Information om denna behörighetsgrupp finns i [Anpassa Intune-konsolvyer i enlighet med administratörsroller](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|Som standard tilldelar Intune inte någon tjänstadministratör. I stället måste du använda en innehavaradministratör med en global administratörsroll för att tilldela den första tjänstadministratören för din prenumeration. </br></br> Som tjänstadministratör använder du [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] för att hantera dagliga uppgifter för Intune.<br /><br />Du tilldelar tjänstadministratörer från administratörskonsolen. En tjänstadministratör måste ha en licens till Intune innan kontot kan få åtkomst till administrationskonsolen.|



### <a name="device-enrollment-managers"></a>Hanterare av enhetsregistrering
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Hanterare av enhetsregistrering är vanliga standardanvändarkonton som har ytterligare behörighet att registrera fler än fem enheter.|Som standard kan varje [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-användare registrera upp till fem enheter. Du kan dock ge ett användarkonto behörighet som hanterare av enhetsregistrering och sedan använda det kontot för att registrera stora grupper av företagsägda enheter. Detta är praktiskt när enheterna ska tilldelas användare tillfälligt eller kan fungera i ett helskärmsläge där en koppling mellan användare och enhet inte krävs.|




>[!div class="step-by-step"]

>[&larr; **Domäninställningar**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Hantera Intune-licenser** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


