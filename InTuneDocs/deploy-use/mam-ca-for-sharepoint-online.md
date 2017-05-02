---
title: "Konfigurera appåtkomst för SharePoint Online"
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 531b09bb-ddfd-498f-8ee3-6675d2466208
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 992273f88e4bbe234f11f936d6416dbaf0d394e9
ms.lasthandoff: 04/19/2017


---

# <a name="create-a-sharepoint-online-conditional-access-policy-to-only-allow-apps-supported-by-mam"></a>Skapa en princip för villkorlig åtkomst för SharePoint Online så att endast appar som stöds av MAM får åtkomst
Det här avsnittet innehåller stegvisa anvisningar för hur du konfigurerar villkorlig åtkomst för Exchange Online så att endast mobila appar som stöder MAM (Hantering av mobilprogram i Intune)-principer tillåts åtkomst.

## <a name="configure-a-sharepoint-online-policy"></a>Konfigurera en SharePoint Online-princip
**Steg 1:** Logga in på [Azure-portalen](https://portal.azure.com) där appåtkomstfunktionen finns. Om du inte har använt Azure Portal tidigare kan du läsa avsnittet [Azure portal for MAM policies](azure-portal-for-microsoft-intune-mam-policies.md) (Azure Portal för MAM-principer).

**Steg 2:** Gå till **Bläddra > Intune > Hantering av mobilprogram i Intune > Inställningar**. I avsnittet för **villkorlig åtkomst**, väljer du **SharePoint Online**.

![Skärmbild av inställningsbladet som visar avsnittet för villkorlig åtkomst och det öppna SharePoint Online-bladet](../media/mam-ca-settings-spo.png)

**Steg 3:** På bladet **Tillåtna appar** väljer du alternativet **Tillåt appar som stöder Intune-apprinciper** för att endast tillåta att appar som stöds av Intunes MAM-principer får åtkomst till SharePoint Online. När du väljer att endast tillåta appar som stöds av Intunes MAM-principer, visas listan med appar som stöds.

![Skärmbild av bladet med tillåtna appar som visar listan med appar](../media/mam-ca-spo-allowed-apps.png)

**Steg 4:** Om du vill tillämpa den här principen på användarna, öppnar du bladet **Begränsade användargrupper** och väljer **Lägg till användargrupp**. Välj en eller flera användargrupper som du vill tillämpa den här principen på.

![Skärmbild av bladet begränsade användargrupper med alternativet lägg till användargrupp markerat](../media/mam-ca-spo-restricted-groups.png)


**Steg 5:** Du kanske vill att vissa användare i den användargrupp du valde i föregående steg inte ska påverkas av den här principen. I sådana fall måste du lägga till dessa användare till listan över undantagna användare. Välj **Undantagna användargrupper** på bladet **SharePoint Online**. Välj **Lägg till användargrupp** för att öppna en lista med användargrupper. Välj de grupper som du vill undanta från den här principen.  

## <a name="modifying-an-existing-policy"></a>Ändra en befintlig princip
### <a name="adding-or-deleting-user-groups"></a>Lägga till eller ta bort användargrupper
Om du vill **ta bort en användargrupp** från listan med **begränsade användargrupper**, öppnar du bladet Begränsade användargrupper, markerar den grupp du vill ta bort och klickar sedan på ... för att se alternativet Ta bort. Välj **Ta bort** att ta bort användargruppen från listan. Du kan använda samma procedur för att ta bort en grupp från listan **exempted user group** (undantagna användargrupper).


## <a name="next-steps"></a>Nästa steg
[Konfigurera appåtkomst för Exchange Online](mam-ca-for-exchange-online.md)

[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Se även

[Skydda appdata med MAM-principer](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

