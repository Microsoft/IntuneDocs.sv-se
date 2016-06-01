---
# required metadata

title: Azure Portal för MAM-principer | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure Portal för Microsoft Intune MAM-principer
## Åtkomst till Azure Portal
**Azure Portal** gör det möjligt att skapa och hantera hanteringsprinciper för mobilappar.

Azure Portal har stöd för att skapa MAM-principer för:
- Appar som körs på enheter som har **registrerats och hanteras av Intune**
- Appar som körs på enheter som **inte är registrerade** i någon MDM-lösning.
- Appar som körs på enheter som **är registrerade i en MDM-lösning från tredje part**

Om du för närvarande använder **Intune-administratörskonsolen** för att hantera enheter kan du skapa en MAM-princip som har stöd för enheter som har registrerats i Intune med [Intune-administratörskonsolen](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)
>[!IMPORTANT]
> Du kanske inte kan se alla MAM-principinställningar i Intune-administratörskonsolen. Azure Portal är den nya administratörskonsolen för att skapa MAM-principer.

## Logga in på Azure Portal och anpassa startsidan

1.  Gå till [Azure Portal](https://portal.azure.com) och logga in med dina autentiseringsuppgifter för [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

    ![Skärmbild av inloggningssidan för Azure portal](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  När du har loggat in visas sidan **instrumentpanelen**. På sidan för **instrumentpanelen** finns en rad standardpaneler som du kan ta bort eller lägga till nya för att anpassa sidan.

    ![Skärmbild av instrumentpanelen i Azure portal](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  På menyn **Bläddra** letar du reda på **Intune**.![Skärmbild av menyn Bläddra med Intune markerat](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  Klicka på **Intune > Hantering av mobilprogram i Intune > Inställningar**

    ![Skärmbild av bladet Hantering av mobilprogram i Intune](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > Om du vill fästa ett blad på sidan **Start** kan du använda alternativet **fäst** på bladet.  Klicka på fästikonen på **bladet för hantering av mobilappar i Intune**för att fästa den på sidan **Start** .

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med fästikonen markerad](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![Skärmbild av instrumentpanelen med den fästa Intune-panelen](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## Nästa steg
[Förbered dig för att konfigurera hanteringsprinciper för mobilappar](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->

