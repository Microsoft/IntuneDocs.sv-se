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
translationtype: Human Translation
ms.sourcegitcommit: fe44466fbcef67d02b16d3d2d335f657251451d3
ms.openlocfilehash: fa8d839da1cf0b2d207edc0b28de8a714ba0df02


---

# <a name="azure-portal-for-microsoft-intune-mam-policies"></a>Azure Portal för Microsoft Intune MAM-principer

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

På Azure Portal kan du skapa och hantera principer för hantering av mobila appar (MAM) för:

- Appar som körs på enheter **som har registrerats och som hanteras i Intune**.

- Appar som körs på enheter som **inte är registrerade** i någon MDM-lösning.
- Appar som körs på enheter som **har registrerats i en MDM-lösning från tredje part**.

>[!IMPORTANT]
> Azure Portal är den nya administratörskonsolen för att skapa MAM-principer, men du kan även skapa en MAM-princip som stöder appar för enheter som har registrerats i Intune via [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) för MDM-scenarier.

> Du kanske inte ser alla MAM-principinställningar som är tillgängliga i Intune-administratörskonsolen. Om du dessutom skapar MAM-principer i både Intune-administratörskonsolen och på Azure Portal åsidosätter principerna som skapats i Azure Portal de som skapats i Intune-administratörskonsolen. I det här scenariot tillämpas Azure Portals MAM-principer på appar och distribueras till användare.


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>Logga in på Azure-portalen och anpassa startsidan

1.  Gå till [Azure-portalen](https://portal.azure.com) och logga in med dina autentiseringsuppgifter för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Skärmbild av inloggningssidan för Azure-portalen](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  När du har loggat in visas **instrumentpanelen**. **Instrumentpanelssidan** kan anpassas.

    ![Skärmbild av instrumentpanelen i Azure portal](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  Öppna menyn **Bläddra** och leta reda på **Intune**.

    ![Skärmbild av Bläddra-menyn med Intune markerat](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  Välj **Intune** > **Hantering av mobilprogram i Intune** > **Inställningar**.

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (Valfritt:) Om du vill fästa ett blad på sidan **Start** kan du använda alternativet **fäst** på bladet. Klicka på fästikonen på **bladet för hantering av mobilappar i Intune** för att fästa bladet på sidan **Start** .

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med fästikonen markerad](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Skärmbild av instrumentpanelen med den fästa Intune-panelen](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>Nästa steg
[Förbered dig för att konfigurera hanteringsprinciper för mobilappar](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


