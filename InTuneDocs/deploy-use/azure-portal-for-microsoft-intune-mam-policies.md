---
title: "Azure Portal för MAM-principer | Microsoft Intune"
description: "Skapa hanteringsprinciper för mobilprogram i Azure Portal. De principer som du skapar här kan tillämpas på enheter som har, eller som inte har, registrerats i Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: b377d527621693f4c231f6f8b16cab277853cdf7


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Azure Portal för Microsoft Intune MAM-principer

## <a name="use-the-azure-portal"></a>Använda Azure-portalen
På Azure-portalen kan du skapa och hantera MAM-principer för hantering av mobila appar.

Azure Portal har stöd för att skapa MAM-principer för:
- Appar som körs på enheter **som har registrerats och som hanteras i Intune**.

- Appar som körs på enheter som **inte är registrerade** i någon MDM-lösning.
- Appar som körs på enheter som **har registrerats i en MDM-lösning från tredje part**.

>[!IMPORTANT]


> Om du hanterar enheter via Intune-administratörskonsolen kan du skapa en MAM-princip som kan användas med appar på enheter som har registrerats i Intune via [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> Du kanske inte ser alla MAM-principinställningar på Intune-administratörskonsolen. Azure Portal är den nya administratörskonsolen för att skapa MAM-principer. Om du skapar MAM-principer i både Intune-administratörskonsolen och på Azure-portalen är det principen i Azure Portal som tillämpas på apparna och distribueras till användarna.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Logga in på Azure-portalen och anpassa startsidan

1.  Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Skärmbild av inloggningssidan för Azure-portalen](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  När du har loggat in visas **instrumentpanelen**. **Instrumentpanelssidan** kan anpassas.

    ![Skärmbild av instrumentpanelen i Azure portal](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  På **Bläddra**-menyn letar du upp **Intune**.![Skärmbild av Bläddra-menyn med Intune markerat](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Välj **Intune** > **Hantering av mobilprogram i Intune** > **Inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]

    > Om du vill fästa ett blad på sidan **Start** kan du använda alternativet **fäst** på bladet. Klicka på fästikonen på **bladet för hantering av mobilappar i Intune** för att fästa bladet på sidan **Start** .

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med fästikonen markerad](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Skärmbild av instrumentpanelen med den fästa Intune-panelen](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## <a name="next-steps"></a>Nästa steg
[Förbered dig för att konfigurera hanteringsprinciper för mobilappar](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


