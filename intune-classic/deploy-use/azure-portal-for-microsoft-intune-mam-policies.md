---
title: "Azure Portal för MAM-principer | Microsoft Docs"
description: "Skapa hanteringsprinciper för mobilprogram i Azure Portal. De principer som du skapar här kan tillämpas på enheter som har, eller som inte har, registrerats i Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e7fd0a83e21d499da39bd65502d8981bc3b1f61c
ms.contentlocale: sv-se
ms.lasthandoff: 05/31/2017


---

# <a name="azure-portal-for-intune-app-protection-policies"></a>Azure-portalen för Intune-appskyddsprinciper

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du använder Azure-portalen för att skapa och hantera appskyddsprinciper för:

- Appar som körs på enheter **som har registrerats och som hanteras i Intune**.

- Appar som körs på enheter som **inte är registrerade** i någon MDM-lösning.
- Appar som körs på enheter som **har registrerats i en MDM-lösning från tredje part**.

>[!IMPORTANT]
> Azure-portalen är den nya administratörskonsolen för att skapa appskyddsprinciper, men du kan även skapa en appskyddsprincip som stöder appar för enheter som har registrerats i Intune via [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) för MDM-scenarier.

> Du kanske inte ser alla inställningar för appskyddsprinciper i Intune-administratörskonsolen. Och om du skapar appskyddsprinciper i både Intune-administratörskonsolen och på Azure-portalen åsidosätter principerna som du skapat på Azure-portalen de som du skapat i Intune-administratörskonsolen. I det här scenariot används appskyddsprinciperna på Azure-portalen för apparna och distribueras till användare.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Logga in på Azure-portalen och anpassa startsidan

1.  Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter.

    ![Skärmbild av inloggningssidan för Azure-portalen](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  När du har loggat in visas **instrumentpanelen**. **Instrumentpanelssidan** kan anpassas.

    ![Skärmbild av instrumentpanelen i Azure portal](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

    ![Skärmbild av Bläddra-menyn med Intune markerat](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Välj **Intune-appskydd** > **Hantering av mobilprogram i Intune** > **Alla inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Valfritt:) Om du vill fästa ett blad på sidan **Start** kan du använda alternativet **fäst** på bladet. Klicka på fästikonen på **bladet för hantering av mobilappar i Intune** för att fästa bladet på sidan **Start** .

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med fästikonen markerad](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Skärmbild av instrumentpanelen med den fästa Intune-panelen](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Nästa steg
[Bli redo att konfigurera appskyddsprinciper](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

