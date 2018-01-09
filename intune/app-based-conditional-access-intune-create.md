---
title: "Appbaserad villkorlig åtkomst med Intune"
description: "I det här avsnittet beskrivs hur du konfigurerar en appbaserad princip för villkorlig åtkomst med Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ccbbe448a61d19b18c9f4f02f90aefa4f415d80b
ms.sourcegitcommit: 9fabf1a8db53842f7b00762374de5b137158ee25
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/22/2017
---
# <a name="set-up-app-based-conditional-access-policies"></a>Konfigurera principer för appbaserad villkorlig åtkomst

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet innehåller anvisningar för hur du konfigurerar principer för appbaserad villkorlig åtkomst för appar som ingår i listan över godkända appar. Listan över godkända appar består av appar som har testats av Microsoft.

> [!IMPORTANT]
> Det här avsnittet går igenom stegen för att lägga till en princip för appbaserad villkorlig åtkomst med Exchange Online, men du kan använda samma steg när du lägger till andra appar som SharePoint Online, Microsoft Teams m.m. från listan över godkända appar.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Så här skapar du en appbaserad princip för villkorlig åtkomst
1.  Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Fler tjänster** och ange "Intune".

3.  Välj **Intune App Protection**.

4.  Välj panelen **Alla inställningar** på bladet **Hantering av mobilprogram i Intune** .

5.  I avsnittet **Villkorlig åtkomst** väljer du **Exchange Online**.

    ![Skärmbild av bladet inställningar som visar avsnittet villkorlig åtkomst med alternativet Exchange Online markerat](./media/MAM-conditional-access-1.png)

6. På bladet **Tillåtna appar** väljer du alternativet **Allow apps that support Intune app policies** (Tillåt appar som stöder Intunes apprinciper) för att endast tillåta att appar som stöds av Intunes appskyddsprinciper får åtkomst till Exchange Online. När du väljer det här alternativet visas listan över appar som stöds.

    > [!NOTE]
    > Alla Exchange Active Sync-e-postklienter, inklusive inbyggda e-postklienter på iOS och Android som ansluter till Exchange Online, kommer inte att kunna skicka eller ta emot e-post. I stället får användarna ett enda e-postmeddelande som informerar dem om att de måste använda e-postprogrammet Outlook.

7. Om du vill tillämpa den här principen på användare öppnar du bladet **Begränsade användargrupper** och väljer **Lägg till användargrupp**. Välj en eller flera användargrupper som du vill tillämpa den här principen på.

    ![Skärmbild av bladet begränsade användargrupper med alternativet lägg till användargrupp markerat](./media/mam-ca-add-user-group.png)

8. Du kanske vill att vissa användare i den grupp du valde i föregående steg inte ska påverkas av den här principen. I sådana fall måste du lägga till dessa användare till listan över undantagna användare. Välj **Exempted user groups** (Undantagna användargrupper) på bladet **Exchange Online**. Välj **Lägg till användargrupp** för att öppna en lista med användargrupper. Välj de grupper som du vill undanta från den här principen.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Ändra eller ta bort användargrupper från en befintlig appbaserad villkorlig åtkomstprincip

1. Öppna bladet **Begränsade användargrupper** och markera sedan den användargrupp du vill ta bort.
2. Klicka på ellipsen för att se borttagningsalternativen.
3. Välj **Ta bort** att ta bort användargruppen från listan.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Skapa appbaserade principer för villkorlig åtkomst i Azure AD-arbetsbelastning

Från och med Intune version 1708 kan IT-administratörer skapa appbaserade principer för villkorlig åtkomst i Azure AD-arbetsbelastningen. Det här är bekvämt och gör att du inte behöver växla mellan Azure- och Intune-arbetsbelastningar.

> [!IMPORTANT]
> Du måste ha en Azure AD Premium-licens för att kunna skapa Azure AD-principer för villkorlig åtkomst från Intune Azure Portal.

### <a name="to-create-an-app-based-conditional-access-policy"></a>Så här skapar du en appbaserad princip för villkorlig åtkomst

> [!IMPORTANT]
> [Intune-appskyddsprinciper](app-protection-policies.md) måste tillämpas på apparna innan du använder appbaserade principer för villkorlig åtkomst.

1. Välj **villkorlig åtkomst** på **Intune-instrumentpanelen**.

2. På bladet **Principer** väljer du **Ny princip** om du vill skapa en ny appbaserad princip för villkorlig åtkomst.

4. Ange ett principnamn och konfigurera inställningarna i avsnittet **Tilldelningar** och välj sedan **Bevilja** under avsnittet **Åtkomstkontroller**.

5. Välj **Kräv godkänd klientapp** följt av **Välj** och sedan **OK** för att spara den nya principen.

## <a name="next-steps"></a>Nästa steg
[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)

### <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](app-protection-policies.md)
[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
