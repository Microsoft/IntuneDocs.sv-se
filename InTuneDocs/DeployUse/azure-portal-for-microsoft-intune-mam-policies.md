---
title: "Azure Portal för MAM-principer | Microsoft Intune"
description: "Skapa hanteringsprinciper för mobilprogram i Azure Portal. De principer som du skapar här kan tillämpas på enheter som har, eller som inte har, registrerats i Intune."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9eb7e79bee2bc36dffab97ffdb6f665218bc739e
ms.openlocfilehash: 0acef421f179ebf922ec8af71ba336e3e5f96bd2


---

# Azure Portal för Microsoft Intune MAM-principer
## Använda Azure-portalen
På Azure-portalen kan du skapa och hantera MAM-principer för hantering av mobila appar.

Azure Portal har stöd för att skapa MAM-principer för:
- Appar som körs på enheter **som har registrerats i och som hanteras av Intune**.
- Appar som körs på enheter som **inte är registrerade** i någon MDM-lösning.
- Appar som körs på enheter som **har registrerats i en MDM-lösning från tredje part**.

>[!IMPORTANT]

> Om du hanterar enheter via Intune-administratörskonsolen kan du skapa en MAM-princip som kan användas med appar på enheter som har registrerats i Intune via [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Du kanske inte ser alla MAM-principinställningar på Intune-administratörskonsolen. Azure Portal är den nya administratörskonsolen för att skapa MAM-principer. Om du skapar MAM-principer i både Intune-administratörskonsolen och på Azure-portalen är det principen i Azure Portal som tillämpas på apparna och distribueras till användarna.

## Logga in på Azure-portalen och anpassa startsidan

1.  Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Skärmbild av inloggningssidan för Azure-portalen](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  När du har loggat in visas **instrumentpanelsidan**. **Instrumentpanelssidan** kan anpassas.

    ![Skärmbild av instrumentpanelen i Azure portal](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  På menyn **Bläddra** letar du upp **Intune**.![Skärmbild av menyn Bläddra med Intune markerat](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Välj **Intune** > **Hantering av mobilprogram i Intune** > **Inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Om du vill fästa bladet på **startsidan** väljer du fästikonen på bladet **Hantering av mobilprogram i Intune**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med fästikonen markerad](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Skärmbild av instrumentpanelen med den fästa Intune-panelen](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Nästa steg
[Förbered dig för att konfigurera hanteringsprinciper för mobilappar](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


