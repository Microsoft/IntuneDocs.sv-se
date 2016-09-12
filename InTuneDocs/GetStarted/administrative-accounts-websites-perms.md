---
title: "Administrativa konton, webbplatser och behörigheter | Microsoft Intune"
description: "administrativa konton behörigheter webbplatser"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0c1e08cc49d75303f6793894e3c8a040f6e7a8b1
ms.openlocfilehash: 29d6f9cd31e6fbf287ae30fb2171bf752ff71157


---

# Administrativa konton, webbplatser och behörigheter i Microsoft Intune

Innan du konfigurerar Microsoft Intune går du igenom det här avsnittet och andra krav som anges i [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

När du ska administrera Intune använder du:
- Två typer av administratörskonton
- Användarkonton med ytterligare behörighet
- Två webbaserade konsoler/portaler för administration som ger administratörerna tillgång till det de ska hantera.

I följande avsnitt beskrivs dessa konton och portaler.

## Administratörskonton och användarkonton med särskilda behörigheter

Nedan visas konton och behörigheter som du ska använda för Intune.

### Innehavaradministratör
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Innehavaradministratörer tilldelas en administratörsroll som definierar den administrativa omfattningen för den aktuella användaren och de aktiviteter som de kan hantera.<br /><br />Administratörsroller är gemensamma mellan de olika Microsoft-molntjänsterna, men vissa tjänster kanske inte stöder vissa roller.<br /><br /> Microsoft Intune använder följande roller:<br /><br />– Global administratör<br />– Faktureringsadministratör<br />– Lösenordsadministratör<br />– Tjänstsupportadministratör<br />– Administratör för användarhantering|Som standard är kontot du använder för att skapa Microsoft Intune-prenumerationen en innehavaradministratör med en global administratörsroll.<br /></br>  Som innehavaradministratör använder du [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] för att hantera prenumerationen för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och tilldela innehavaradministratörer från [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Använd en innehavaradministratör med en global administrationsroll för åtkomst till [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] och tilldela din första tjänstadministratör. Du bör inte använda en innehavaradministratör för dagliga uppgifter. En innehavaradministratör kräver inte någon licens till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] för att få åtkomst till [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Innehavaradministratör är ett gemensamt begrepp mellan Microsofts molntjänster. När du prenumererar på [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] är tjänsten en innehavaradministratör för Microsoft Azure AD. Se avsnittet Azure AD-klient i [Vad är en Azure AD-katalog?](http://technet.microsoft.com/library/jj573650.aspx).|


### Tjänstadministratör
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Tjänstadministratörer tilldelas en av följande behörigheter:<br /><br />**Fullständig åtkomst**: Ger åtkomst till alla delar av [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], utan begränsningar. Kan också lägga till och hantera andra tjänstadministratörer.<br /><br />**Skrivskyddad åtkomst**: Ger läsbehörighet till alla områden av [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. En skrivskyddad tjänstadministratör kan inte ändra data, men kan köra rapporter.<br /><br />**Supportavdelning – Gruppnod**: Ger behörigheter som gör det möjligt för tjänstadministratören att enbart genomföra en uppsättning uppgifter som vanligtvis är kopplade till supportavdelningsscenarion. Information om denna behörighetsgrupp finns i [Anpassa Intune-konsolvyer i enlighet med administratörsroller](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|Som standard tilldelar [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] inte någon tjänstadministratör. I stället måste du använda en innehavaradministratör med en global administratörsroll för att tilldela den första tjänstadministratören för din prenumeration. </br></br> Som tjänstadministratör använder du [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] för att hantera dagliga uppgifter för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].<br /><br />Du tilldelar tjänstadministratörer från administratörskonsolen. En tjänstadministratör måste ha en licens till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] innan kontot kan få åtkomst till administrationskonsolen.|



### Hanterare av enhetsregistrering
|Behörighetsnivåer|Mer information|
|--------------------------|-------------------------|
|Hanterare av enhetsregistrering är vanliga standardanvändarkonton som har ytterligare behörighet att registrera fler än fem enheter.|Som standard kan varje [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)]-användare registrera upp till fem enheter. Du kan dock ge ett användarkonto behörighet som hanterare av enhetsregistrering och sedan använda det kontot för att registrera stora grupper av företagsägda enheter. Detta är praktiskt när enheterna ska tilldelas användare tillfälligt eller kan fungera i ett helskärmsläge där en koppling mellan användare och enhet inte krävs.|


## Administrativa webbplatser för Intune
 Olika administrativa uppgifter kräver att du använder någon av följande administrativa webbplatser, som du kan komma åt med en [webbläsare som stöds](supported-web-browsers.md).

- [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune-administratörskonsol](https://admin.manage.microsoft.com/)

### [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**Använd portalen som en innehavaradministratör när du vill hantera din prenumeration**, inklusive följande uppgifter när de tillåts av din administratörsroll:

- Hantera användarkonton för prenumerationen och konfigurera katalogsynkronisering från din lokala Active Directory.
- Hantera grupper av användare, s.k. säkerhetsgrupper.
- Tilldela licenser till användare för att använda [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Konfigurera det domännamn som du använder med din prenumeration. Domännamnet definierar det konto som användare loggar in med.
- Hantera fakturerings- och köpinformation för din prenumeration, inklusive antalet licenser som du har, eller mängden molnlagringsutrymme som du kan använda.
- Hitta länkar för att visa hälsotillståndet för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-tjänsten.
- Som innehavaradministratör kan du logga in på Office 365-portalen för att hantera prenumerationen, även om ditt konto inte har tilldelats någon licens för att använda [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Alla användare som har en licens för Intune, men som är inte administratörer, kan använda portalen för att återställa sina kontolösenord och redigera sina profiler.
- För att få åtkomst till Office 365-portalen måste ditt konto har inloggningsstatusen **Tillåten**. Denna status skiljer sig från att ha en licens för prenumerationen. Som standard har alla användarkonton statusen **Tillåten**.


### [Microsoft Intune-administratörskonsol](https://admin.manage.microsoft.com/)

**Som tjänstadministratör kan du använda portalen för att hantera dagliga uppgifter**, som bl.a.:

- Ange principer för datorer och mobila enheter.
- Överföra och distribuera programvara, som t.ex. programuppdateringar och appar.
- Hantera [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection på datorer.
- Visa enhetsstatus och köra rapporter.
- Logga in på den här portalen. Du måste antingen ha behörighet som tjänsteadministratör eller vara en innehavaradministratör med den globala administratörsrollen för att logga in på den här portalen.


Endast användare med behörighet som tjänsteadministratör eller innehavaradministratören med den globala administratörsrollen kan logga in på den här portalen. Om du vill få åtkomst till administrationskonsolen måste kontot ha en licens för att använda [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och inloggningsstatusen **Tillåten**.

Lär dig mer om att [lägga till användare för prenumerationen](start-with-a-paid-subscription-to-microsoft-intune-step-3.md) och [tilldela licenser för prenumerationen](start-with-a-paid-subscription-to-microsoft-intune-step-4.md).

 ### Se även
 [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Aug16_HO5-->


