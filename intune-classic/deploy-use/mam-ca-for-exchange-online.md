---
title: "Appåtkomst för Exchange Online"
description: "Det här avsnittet beskriver hur du konfigurerar en princip för villkorlig åtkomst för MAM-appar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f2cd1a1f-fd29-4081-8dfa-c40993a107d5
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 67a687af9396236af9685fd2bb423226a7e83797
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="create-an-exchange-online-conditional-access-to-only-allow-apps-supported-by-mam"></a>Konfigurera villkorlig åtkomst för Exchange Online så att endast appar som stöds av MAM får åtkomst

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet innehåller stegvisa anvisningar som beskriver hur du konfigurerar villkorlig åtkomst för Exchange Online så att endast mobila appar som stöder Intunes appskyddsprinciper tillåts åtkomst.


## <a name="create-an-exchange-online-policy"></a>Skapa en Exchange Online-princip
1.  Logga in på [Azure Portal](https://portal.azure.com) som innehåller appåtkomstfunktionen. Om du inte har använt Azure-portalen tidigare kan du läsa avsnittet [Azure portal for MAM policies](azure-portal-for-microsoft-intune-mam-policies.md) (Azure-portal för MAM-principer).

2.  Välj **Fler tjänster** och ange "Intune".

3.  Välj **Intune App Protection**.

4.  Välj panelen **Alla inställningar** på bladet **Hantering av mobilprogram i Intune** .

5.  I avsnittet **Villkorlig åtkomst** väljer du **Exchange Online**.

    ![Skärmbild av bladet inställningar som visar avsnittet villkorlig åtkomst med alternativet Exchange Online markerat](../media/MAM-conditional-access-1.png)

6. På bladet **Tillåtna appar** väljer du alternativet **Allow apps that support Intune app policies** (Tillåt appar som stöder Intunes apprinciper) för att endast tillåta att appar som stöds av Intunes appskyddsprinciper får åtkomst till Exchange Online. När du väljer det här alternativet visas listan över appar som stöds.

    >[!NOTE]
    >Alla e-postklienter för Exchange Active Sync, inklusive inbyggda e-postklienter på iOS och >Android som ansluter till Exchange Online, kommer inte att kunna skicka eller ta emot >e-post. I stället får användarna ett enda e-postmeddelande som informerar dem om att de måste använda e-postprogrammet >Outlook.

7. Om du vill tillämpa den här principen på användare öppnar du bladet **Begränsade användargrupper** och väljer **Lägg till användargrupp**. Välj en eller flera användargrupper som du vill tillämpa den här principen på.

    ![Skärmbild av bladet begränsade användargrupper med alternativet lägg till användargrupp markerat](../media/mam-ca-add-user-group.png)

8. Du kanske vill att vissa användare i den grupp du valde i föregående steg inte ska påverkas av den här principen. I sådana fall måste du lägga till dessa användare till listan över undantagna användare. Välj **Exempted user groups** (Undantagna användargrupper) på bladet **Exchange Online**. Välj **Lägg till användargrupp** för att öppna en lista med användargrupper. Välj de grupper som du vill undanta från den här principen.  

## <a name="modify-an-existing-policy"></a>Ändra en befintlig princip
### <a name="add-or-delete-user-groups"></a>Lägg till eller ta bort användargrupper

För att **delete a user group** (ta bort en användargrupp) från listan **begränsade användargrupper** öppnar du bladet **Begränsade användargrupper**, markerar den grupp du vill ta bort och klickar sedan på **ellipserna (...)** för att se alternativet **ta bort**. Välj **Ta bort** att ta bort användargruppen från listan. Du kan använda samma procedur för att ta bort en grupp från listan **exempted user group** (undantagna användargrupper).


## <a name="next-steps"></a>Nästa steg
[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)
### <a name="see-also"></a>Se även
[Skydda appdata med appskyddsprinciper](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
