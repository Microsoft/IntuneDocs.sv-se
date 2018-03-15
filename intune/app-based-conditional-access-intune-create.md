---
title: "Konfigurera en appbaserad villkorlig åtkomstprincip med Intune"
description: "Läs mer om att skapa en appbaserad villkorlig åtkomstprincip med Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89ee7c0df2fde740c18b84f1d9f028d59ba5d81d
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Konfigurera appbaserade villkorliga åtkomstprinciper med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs hur du konfigurerar appbaserade villkorliga åtkomstprinciper för appar som ingår i listan med godkända appar. Listan över godkända appar består av appar som har testats av Microsoft.

> [!IMPORTANT]
> Den här artikeln går igenom stegen för att lägga till en appbaserad villkorlig åtkomstprincip med Exchange Online, men du kan använda samma steg när du lägger till andra appar som SharePoint Online, Microsoft Teams m.fl. från listan med godkända appar.

## <a name="to-create-an-app-based-conditional-access-policy"></a>Så här skapar du en appbaserad princip för villkorlig åtkomst
1.  Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Alla tjänster** och skriv: ”Intune”.

3.  Välj **Intune App Protection**.

4.  I **Intune-appskydd** under avsnittet **Villkorlig åtkomst** väljer du **Exchange Online**.

    ![Skärmbild av inställningsfönstret som visar avsnittet för villkorlig åtkomst med alternativet Exchange Online markerat](./media/MAM-conditional-access-1.png)

6. I fönstret **Tillåtna appar** väljer du alternativet **Tillåt appar som stöder Intunes apprinciper** för att endast tillåta att appar som stöds av Intunes appskyddsprinciper får åtkomst till Exchange Online. När du väljer det här alternativet visas listan över appar som stöds.

    > [!NOTE]
    > Alla e-postklienter i Exchange Active Sync, inklusive inbyggda e-postklienter i iOS och Android som ansluter till Exchange Online, förhindras från att skicka eller ta emot e-post. I stället får användarna ett enda e-postmeddelande som informerar dem om att de måste använda e-postprogrammet Outlook.

7. Om du vill tillämpa den här principen på användarna öppnar du fönstret **Begränsade användargrupper** och väljer **Lägg till användargrupp**. Välj en eller flera användargrupper som du vill tillämpa den här principen på.

    ![Skärmbild av fönstret Begränsade användargrupper med alternativet Lägg till användargrupp markerat](./media/mam-ca-add-user-group.png)

8. Du kanske vill att vissa användare i den grupp du valde i föregående steg inte ska påverkas av den här principen. I sådana fall måste du lägga till dessa användare till listan över undantagna användare. Välj **Exempted user groups** (Undantagna användargrupper) i fönstret **Exchange Online**. Välj **Lägg till användargrupp** för att öppna en lista med användargrupper. Välj de grupper som du vill undanta från den här principen.

## <a name="to-modify-or-delete-user-groups-from-an-existing-app-based-ca-policy"></a>Ändra eller ta bort användargrupper från en befintlig appbaserad villkorlig åtkomstprincip

1. Öppna fönstret **Begränsade användargrupper** och markera sedan den användargrupp som du vill ta bort.
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

2. I fönstret **Principer** väljer du **Ny princip** om du vill skapa en ny appbaserad villkorlig åtkomstprincip.

4. Ange ett principnamn och konfigurera inställningarna i avsnittet **Tilldelningar** och välj sedan **Bevilja** under avsnittet **Åtkomstkontroller**.

5. Välj **Kräv godkänd klientapp** följt av **Välj** och sedan **Skapa** för att spara den nya principen.

## <a name="next-steps"></a>Nästa steg
[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)

### <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](app-protection-policies.md)
[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
