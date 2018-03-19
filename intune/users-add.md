---
title: "Lägg till användare och tilldela behörigheter"
titlesuffix: Microsoft Intune
description: "Synkronisera lokala användare med Azure AD och bevilja administratörsbehörighet för din Intune-prenumeration."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f8fe6d668885345f4bd710e4b96b8d7855f12632
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="add-users-and-grant-administrative-permission-to-intune"></a>Lägga till användare och ge administrativ behörighet till Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Som administratör kan du lägga till användare direkt eller synkronisera användare från din lokala Active Directory. När de har lagts till, kan användare registrera enheter och få åtkomst till företagsresurser. Du kan också ge användarna ytterligare behörigheter, inklusive behörigheter som *global administratör* och *tjänstadministratör*.

## <a name="add-users-to-intune"></a>Lägg till användare i Intune
Du kan lägga till användare i Intune-prenumerationen manuellt via [Office 365-portalen](https://www.office.com/signin) eller [Azure-portalen](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). En administratör kan redigera användarkonton för att tilldela Intune-licenser. Du kan tilldela licenser antingen på Office 365-portalen eller på Intune Azure-portalen. Mer information om hur du använder Office 365-portalen finns i [Lägga till användare individuellt eller flera samtidigt på Office 365-portalen](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Lägga till Intune-användare i administrationscenter för Office 365
1. Logga in på [Office 365-portalen](https://www.office.com/signin) med ett konto som global administratör eller användarhanteringsadministratör.
2. Välj **Admin** på Office 365-menyn.
3. Välj **Lägg till en användare** i administrationscentret.

  ![Skärmbild av avsnittet Lägg till användare](media/office-add-user.png)

4. Ange följande användarinformation:
  - **Förnamn**
  - **Efternamn**
  - **Visningsnamn**
  - **Användarnamn** – Användarens huvudnamn (UPN) som är lagrat i Azure Active Directory och används för att få åtkomst till tjänsten
  - **Position**
  - **Kontaktinformation** (valfritt)
  - **Lösenord** –Generera automatiskt eller ange manuellt

     ![Skärmbild av avsnittet Ny användare](media/office-add-user-details.png)

5. Tilldela en Intune-licens. Välj **Produktlicenser** och välj produktlicensen. En licens som omfattar Intune krävs.
6. Välj **Lägg till** för att skapa den nya användaren.

### <a name="add-intune-users-in-the-azure-portal"></a>Lägg till Intune-användare i Azure-portalen
1. Logga in på [Azure-portalen](https://portal.azure.com) och gå till **Alla tjänster** > **Övervakning + hantering** > **Intune**. Du kan också *söka efter resurser* för **Intune**.
2. Välj **Användare** > **Alla användare**.
3. Välj **Ny användare** i administrationscentret.
  ![Skärmbild av Lägg till ny användare](media/intune-add-user.png)
4. Ange följande användarinformation:
  - **Namn**
  - **Användarnamn** – Det nya namnet på Azure Active Directory-portalen ![Skärmbild av administrationscenter](media/intune-add-user-info.png) Fortsätt genom att välja **OK**.
5. Om du vill kan du ange följande användaregenskaper:
  - **Profil** – Arbetsrelaterad information inklusive **befattning** och **avdelning**
  -  **Grupper** – Välj de grupper du vill lägga till för användaren
  - **Katalogroll** – Ge användaren administratörsbehörighet, inklusive en administratörsroll för Intune-tjänsten.

  Välj **Skapa** för att lägga till den nya användaren i Intune.
6. Välj **Profil** och sedan en **Användningsplats** för den nya användaren. Användningsplatsen krävs innan du kan tilldela den nya användaren en Intune-licens. Fortsätt genom att välja **Spara**.
    ![Skärmbild av Användningsplats](media/intune-add-user-loc.png)
7. Välj **Licenser** och välj sedan **Tilldela** för att tilldela en Intune-licens till den här användaren. En Intune-licens krävs för att registrera enheter eller komma åt företagsresurser. Välj **Produkter**, välj licenstypen, välj **Välj** och välj sedan **Tilldela**.

## <a name="grant-admin-permissions"></a>Bevilja administratörsbehörigheter

När du har lagt till användare i Intune-prenumerationen rekommenderar vi att du ger några av användarna administratörsbehörighet.  Följ dessa steg för att bevilja administratörsbehörighet:

### <a name="give-admin-permissions-in-office-365"></a>Ge administratörsbehörigheter i Office 365
1. Logga in på [Office 365-portalen](https://www.office.com/signin) med ett konto som global administratör.
2. Välj **Admin** på Office 365-menyn.
3. I administrationscentret väljer du **Aktiva användare** och väljer sedan den användare som ska få administratörsbehörighet.

4. I kolumnen **Roller** väljer du **Redigera**.

    ![Skärmbild av Adminstratörsanvändare](./media/office-assign-roles-open.png)

5. Välj den administratörsbehörighet som ska beviljas från listan över tillgängliga roller.
![Skärmbild av tilldelning av roller](./media/office-assign-roles.png)
6. Välj **Spara**.

### <a name="give-admin-permissions-in-the-azure-portal"></a>Ge administratörsbehörigheter i Azure-portalen
1. Logga in på [Azure-portalen](https://www.office.com/signin) med ett globalt administratörskonto.
2. I Azure-portalen väljer du **Användare** och sedan den användare som du vill ge administratörsbehörigheter.
3. Välj **Katalogroll** och välj sedan behörigheten.
  ![Skärmbild av Katalogroll](./media/add-intune-directory-role.png)
4. Välj **Spara**.

### <a name="types-of-administrators"></a>Administratörstyper

Tilldela användare en eller flera administratörsbehörigheter. Dessa behörigheter definierar den administrativa omfattningen för användare och de uppgifter som de kan hantera. Administratörsbehörigheter är gemensamma mellan de olika Microsoft-molntjänsterna, men vissa tjänster kanske inte stöder vissa behörigheter. Både Azure-portalen och Office 365-portalen visar begränsade administratörsroller som inte används av Intune. Administratörsbehörighet för Intune innehåller följande alternativ:

- **Global administratör** – (Office 365 och Intune) Har åtkomst till alla administrativa funktioner i Intune. Som standard blir den person som registrerar sig för Intune en global administratör. Globala administratörer är de enda administratörer som kan tilldela andra administratörsroller. Du kan ha fler än en global administratör i din organisation. Vi rekommenderar att endast ett fåtal personer på företaget tilldelas den här rollen för att minska risken för företaget.
- **Lösenordsadministratör** – (Office 365 och Intune) Återställer lösenord, hanterar tjänstförfrågningar och övervakar tjänstens hälsostatus. Lösenordsadministratörer är begränsade till att återställa lösenord för användare.
- **Tjänstadministratör** – (Office 365 och Intune) Öppnar supportförfrågningar med Microsoft och övervakar instrumentpanelen och meddelandecenter. Användaren har behörigheter för "Visa endast" utom för att öppna stödbiljetter och läsa dem.
- **Faktureringsadministratör** – (Office 365 och Intune) Gör inköp, hanterar prenumerationer, hanterar supportärenden och övervakar tjänstens hälsostatus.
- **Användaradministratör** – (Office 365 och Intune) Återställer lösenord, övervakar tjänstens hälsostatus, lägger till och tar bort användarkonton och hanterar tjänstförfrågningar. Administratören för användarhantering kan inte ta bort en global administratör, skapa andra administratörsroller eller återställa lösenord för andra administratörer.
- **Intune-tjänstadministratör** – Alla globala administratörsbehörigheter för Intune förutom behörighet att skapa administratörer med alternativ för **Katalogroll**.

Det konto som du använder för att skapa Microsoft Intune-prenumerationen är en global administratör. Du bör inte använda en global administratör för dagliga uppgifter. Även om en administratör inte behöver en Intune-licens för att få åtkomst till Intune i Azure Portal så krävs en Intune-licens för att kunna utföra vissa hanteringsuppgifter, som till exempel att konfigurera anslutningsprogrammet för Exchange-tjänsten.

För att få åtkomst till Office 365-portalen måste ditt konto ha statusen **Sign-in allowed** (Inloggning tillåts). Under **Profil** i Azure-portalen anger du **Blockera inloggning** till **Nej** för att tillåta åtkomst. Denna status skiljer sig från att ha en licens för prenumerationen. Som standard har alla användarkonton statusen **Tillåten**. Användare utan administratörsbehörighet kan använda Office 365-portalen för att återställa lösenord för Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Synkronisera Active Directory och lägga till användare i Intune
Du kan konfigurera katalogsynkronisering om du vill importera användarkonton från organisationens lokala Active Directory till Microsoft Azure Active Directory (Azure AD) som inkluderar Intune-användare. När din lokala Active Directory-tjänst är ansluten till alla dina Azure Active Directory-baserade tjänster blir hanteringen av användaridentiteter mycket enklare. Du kan också konfigurera funktioner för enkel inloggning som gör autentiseringen av dina användare välbekant och enkel. Genom att länka samma [Azure AD-klient](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) med flera tjänster, är de användarkonton som du tidigare har synkroniserat tillgängliga för alla molnbaserade tjänster.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Så här synkroniserar du lokala användare med Azure AD
Det enda verktyg som du behöver för att synkronisera dina användarkonton med Azure AD är [Azure AD Connect-guiden](https://www.microsoft.com/download/details.aspx?id=47594). Azure AD Connect-guiden är verktyget som steg för steg hjälper dig att ansluta den lokala identitetsinfrastrukturen till molnet.  Välj topologi och preferenser (en eller flera kataloger, lösenordssynkronisering eller federation). Guiden distribuerar och konfigurerar alla komponenter som krävs för att upprätta anslutningen. Exempel: Sync Services, Active Directory Federation Services (AD FS) och Azure AD PowerShell-modulen.

> [!TIP]
> Azure AD Connect innehåller funktioner som tidigare lanserats som Dirsync och Azure AD Sync. Lär dig mer om [katalogintegrering](http://technet.microsoft.com/library/jj573653.aspx). Mer information om hur du synkroniserar användarkonton från en lokal katalog till Azure AD finns i [Likheter mellan Active Directory och Azure AD](http://technet.microsoft.com/library/dn518177.aspx).
