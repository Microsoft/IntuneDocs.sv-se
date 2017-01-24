---
title: "Lägg till användare och tilldela behörigheter | Microsoft Docs"
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
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: 02b6dd389c94d2b31bd96b2095ae48b685084370


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>Lägg till användare och ge administrativ behörighet till Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Som administratör kan du lägga till användare direkt eller synkronisera användare från din lokala Active Directory. När de har lagts till, kan användare registrera enheter och få åtkomst till företagsresurser. Du kan även ge användarna ytterligare behörighet inklusive *innehavaradministratör*, *tjänstadministratör* och *hanteringsbehörigheter för enhetsregistrering*.

Det här avsnittet hjälper dig att:

- [Lägga till användare i Intune](#add-users-to-intune)
- [Bevilja ytterligare Intune-behörigheter](#grant-intune-permissions) inklusive:
  - [Innehavaradministratör](#tenant-administrator)
  - [Tjänstadministratör](#service-administrator)
  - [Hanterare av enhetsregistrering](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>Lägg till användare i Intune
Du kan manuellt lägga till användare till din Intune-prenumeration via [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854), de tilldelas inte automatiskt en licens för Intune. I stället måste en Intune-klientadministratör senare redigera användarkontot och tilldela en licens till användaren från Office 365-portalen. Anvisningar finns i [Lägga till användare individuellt eller i grupp till Office 365-portalen](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="sync-active-directory-and-add-users-to-intune"></a>Synkronisera Active Directory och lägga till användare i Intune
Du kan konfigurera katalogsynkronisering om du vill importera användarkonton från organisationens lokala Active Directory till Microsoft Azure Active Directory (Azure AD) som inkluderar Intune-användare. När din lokala Active Directory-tjänst är ansluten till alla dina Azure Active Directory-baserade tjänster blir hanteringen av användaridentiteter mycket enklare. Du kan också konfigurera funktioner för enkel inloggning som gör autentiseringen av dina användare välbekant och enkel. Genom att länka samma [Azure AD-klient](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) med flera tjänster, är de användarkonton som du tidigare har synkroniserat tillgängliga för alla molnbaserade tjänster.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Så här synkroniserar du lokala användare med Azure AD
Det enda verktyg som du behöver för att synkronisera dina användarkonton med Azure AD är [Azure AD Connect-guiden](https://www.microsoft.com/download/details.aspx?id=47594). Azure AD Connect-guiden är verktyget som steg för steg hjälper dig att ansluta den lokala identitetsinfrastrukturen till molnet.  Välj din topologi och dina behov (en eller flera kataloger, lösenordssynkronisering eller federation) så distribuerar och konfigurerar guiden alla komponenter som krävs för att få igång din anslutning. Exempel: Sync Services, Active Directory Federation Services (AD FS) och Azure AD PowerShell-modulen.

> [!TIP]
> Azure AD Connect innehåller funktioner som tidigare lanserats som Dirsync och Azure AD Sync. Lär dig mer om [katalogintegrering](http://technet.microsoft.com/library/jj573653.aspx). Mer information om fördelarna med att synkronisera användarkonton från din lokala katalog till Azure AD finns i [Likheter mellan Active Directory och Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-intune-permissions"></a>Tilldela Intune-behörigheter

När du har lagt till fler användare i din Intune-prenumeration rekommenderar vi att du ger några av användarkontona administratörsbehörighet. Om du vill administrera Intune kan du ge användare tre typer av Intune-behörighet
-   **Innehavaradministratör**: Använd Office 365-portalen om du vill att den här typen av administratör ska hantera din prenumeration, inklusive fakturering, molnlagring och hantering av användare som kan använda Intune.
-   **Tjänstadministratör**: Använd Microsoft Intune-administratörskonsol om du vill att den här typen av administratör ska utföra dagliga uppgifter, t.ex. hantering av enheter och datorer, distribution av principer och appar, samt rapportkörning.
-   **Hanterare av enhetsregistrering**: Använd Microsoft Intune-administratörskonsol om du vill att den här typen av administratör ska utföra dagliga uppgifter, t.ex. hantering av enheter och datorer, distribution av principer och appar, samt rapportkörning.


### <a name="tenant-administrator"></a>Innehavaradministratör


Innehavaradministratörer tilldelas en administratörsroll som definierar den administrativa omfattningen för den aktuella användaren och de aktiviteter som de kan hantera. Administratörsroller är gemensamma mellan de olika Microsoft-molntjänsterna, men vissa tjänster kanske inte stöder vissa roller. Intune använder följande roller:
- **Global administratör** – åtkomst till alla administrativa funktioner i Intune. Som standard blir den person som registrerar sig för Intune en global administratör. Globala administratörer är de enda administratörer som kan tilldela andra administratörsroller. Du kan ha fler än en global administratör i din organisation. Som metodtips rekommenderar vi att endast några personer i företaget har den här rollen för att minska risken för företaget.
- **Faktureringsadministratör** – Gör inköp, hanterar prenumerationer, hanterar supportärenden och övervakar tjänstens hälsa.
- **Lösenordsadministratör** – Återställer lösenord, hanterar tjänstbegäranden och övervakar tjänstens hälsa. Lösenordsadministratörer är begränsade till att återställa lösenord för användare.
- **Tjänstsupportadministratör** – Öppnar supportbegär med Microsoft och ser instrumentpanelen och meddelandecenter. Användaren har behörigheter för "Visa endast" utom för att öppna stödbiljetter och läsa dem.
- **Administratör för användarhantering** – Återställer lösenord, övervakar tjänstens hälsotillstånd, lägger till och tar bort användarkonton och hanterar tjänstbegäranden. Administratören för användarhantering kan inte ta bort en global administratör, skapa andra administratörsroller eller återställa lösenord för faktureringsadministratörer, globala administratörer och tjänstadministratörer.

Som standard är kontot du använder för att skapa Microsoft Intune-prenumerationen en innehavaradministratör med en global administratörsroll. Som innehavaradministratör använder du Intune-administratörskonsol för att hantera prenumerationen för Intune och tilldela innehavaradministratörer från [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854). Använd en innehavaradministratör med en global administrationsroll för åtkomst till portalen och tilldela din första tjänstadministratör. Du bör inte använda en innehavaradministratör för dagliga uppgifter. En innehavaradministratör kräver inte någon licens till Intune för att få åtkomst till Intune-administratörskonsol. Innehavaradministratör är ett gemensamt begrepp mellan Microsofts molntjänster. När du prenumererar på Intune är tjänsten en innehavaradministratör för Azure AD. Se avsnittet Azure AD-klient i [Vad är en Azure AD-katalog?](http://technet.microsoft.com/library/jj573650.aspx) för mer information.

Använd [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854) som en innehavaradministratör när du vill hantera din prenumeration, inklusive följande uppgifter när de tillåts av din administratörsroll:

- Hantera användarkonton och konfigurera katalogsynkronisering från din lokala Active Directory
- Hantera grupper av användare, s.k. säkerhetsgrupper
- Tilldela användarlicenser för Intune
- Konfigurera domännamnet för din prenumeration som används när användarna loggar in (t.ex. contoso.com)
- Hantera fakturering och inköp inklusive licenser och lagringsutrymme i molnet
- Hitta länkar för att visa hälsotillståndet för Intune-tjänsten

För att få åtkomst till Office 365-portalen måste ditt konto har inloggningsstatusen **Tillåten**. Denna status skiljer sig från att ha en licens för prenumerationen. Som standard har alla användarkonton statusen **Tillåten**. Användare utan administratörsbehörighet kan använda Office 365-portalen för att återställa lösenord för Intune.

### <a name="service-administrator"></a>Tjänstadministratör

Som standard tilldelar Intune inte någon tjänstadministratör. I stället måste du använda en innehavaradministratör med en global administratörsroll för att tilldela den första tjänstadministratören för din prenumeration. Som tjänstadministratör använder du [Intune-administratörskonsolen](https://manage.microsoft.com/) för att hantera dagliga uppgifter för Intune. Du tilldelar tjänstadministratörer från administratörskonsolen. En tjänstadministratör måste ha en licens till Intune för att få åtkomst till administrationskonsolen.

Tjänstadministratörer tilldelas en av följande behörigheter:
- **Fullständig åtkomst**: Obegränsad åtkomst till alla delar av Intune-administratörskonsolen, lägg till och hantera andra tjänstadministratörer
- **Skrivskyddad åtkomst**: Läsbehörighet till alla delar av Intune-administrationskonsolen, kan inte ändra data, men kan köra rapporter
- **Supportavdelning – Gruppnod**: Tillåter bara tjänstadministratör att utföra de aktiviteter som är kopplade till supportavdelningsscenarion, se [Anpassa Intune-konsolvyer i enlighet med administratörsroller](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)

Som tjänstadministratör kan du använda portalen för att hantera dagliga uppgifter, som bl.a.:

- Skapa och hantera principer för datorer och mobila enheter
- Överföra och distribuera programvaruuppdateringar och appar
- Hantera Endpoint Protection på datorer
- Visa enhetsstatus och köra rapporter

### <a name="device-enrollment-managers"></a>Hanterare av enhetsregistrering

Hanterare av enhetsregistrering är vanliga standardanvändarkonton med ytterligare behörighet att registrera många användarlösa enheter. Som standard kan varje Intune-användare registrera upp till 15 enheter. Som administratör kan ge du ett användarkonto behörighet som hanterare av enhetsregistrering. Kontot kan registrera ett stort antal företagsägda enheter. Detta är praktiskt när enheterna ska tilldelas användare tillfälligt eller kan fungera i ett helskärmsläge där en koppling mellan användare och enhet inte krävs. Mer information finns i [Hanterare av enhetsregistrering](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Domäninställningar**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Hantera Intune-licenser** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Jan17_HO2-->


