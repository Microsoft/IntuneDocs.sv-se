---
title: Kontrollera enhetsåtkomst | Microsoft Docs
description: Kontrollera enhetsåtkomsten för att ta reda på om din enhet uppfyller kraven och kan komma åt arbets- eller skolresurser.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 0cae5a5e398af77cc626f87f43fb5a21b0489b4e
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857012"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>Kontrollera åtkomst från företagsportalappen för Windows

Kontrollera att enheten har åtkomst till arbets- eller skolresurser. 

Organisationer ställer krav&ndash;, till exempel kryptering och lösenordsgränser&ndash;, för att se till att endast säkra, betrodda enheter kommer åt deras data. Hanterade enheter måste uppfylla och underhålla de här kraven för att få åtkomst till organisationens resurser.

Åtgärden **Kontrollera åtkomst** utvärderar din enhets inställningar och dess åtkomststatus. Sidan **Enhetsinformation** visar de inställningar som du behöver justera för att få åtkomst. 

Följ stegen i den här artikeln om du vill kontrollera åtkomsten från företagsportalappen för Windows.  

## <a name="check-access-from-device-details-page"></a>Kontrollera åtkomst från sidan med enhetsinformation  
1. Öppna företagsportalappen för Windows och gå till **Mina enheter**.  

    ![Exempel på skärmbild av startsidan i företagsportalappen för Windows, med fokus på avsnittet Mina enheter.](./media/1809_CheckAccess_Context_Select_Device.png)  
2. Välj en enhet.  
3. På sidan **Enhetsinformation** väljer du **Kontrollera åtkomst**. Appen synkroniserar enheten med din organisations krav och kontrollerar att enheten uppfyller dem. Den här kontrollen kan ta några minuter.  

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på knappen Kontrollera åtkomst.](./media/1809_CheckAccess_Checking_Status.png) 

4. Titta på statusuppdateringen. Den visar att enheten **har åtkomst till organisationens resurser** eller att den **inte har åtkomst till organisationens resurser**.  

   ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på avsnittet Status åtkomst.](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. Om enheten inte kan komma åt resurser går du till aviseringen överst på sidan. Klicka på **Mer** om du vill expandera dess egenskaper. Klicka på **Mindre** om du vill dölja dem.  

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på aviseringen överst på sidan.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Eventuella ytterligare hjälplänkar och rekommenderade åtgärder visas i meddelandet. Välj ett eller flera av dessa alternativ för att börja felsöka direkt. Lös-, synkroniserings- och kontaktåtgärderna &ndash;som beskrivs nedan&ndash;visas bara när du använder företagsportalen på den aktuella enheten.  

     * **Så här löser du problemet** öppnar en relevant hjälpartikel, om en sådan finns.  
     * **Lös** omdirigerar dig till inställningen på din enhet.  
     * **Synkronisera** utvärderar enheten och kontrollerar att den uppfyller din organisations krav.  
     * **Kontakta IT** omdirigerar dig till IT-teamets kontaktinformation.   
 
6. När du har uppdaterat inställningarna klickar du på **Kontrollera åtkomst** för att bekräfta enhetens status.  

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på avsnittet Status åtkomst.](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>Kontrollera åtkomst från enhetens snabbmeny  
1. Öppna företagsportalappen för Windows och gå till **Mina enheter**.  

    ![Exempel på skärmbild av startsidan i företagsportalappen för Windows, med fokus på avsnittet Mina enheter.](./media/1809_CheckAccess_Context_Select_Device.png)  

2. Högerklicka på eller tryck på och håll ned en enhet för att öppna enhetens [snabbmeny](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

    ![Exempel på skärmbild av startsidan i företagsportalappen för Windows. Snabbmenyn för enheten visas i avsnittet **Mina enheter** på sidan och visar åtgärderna ”Byt namn”, ”Ta bort” och ”Kontrollera åtkomst”.](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. Välj **Kontrollera åtkomst**. Appen synkroniserar enheten med din organisations krav och kontrollerar att enheten uppfyller dem. Den här kontrollen kan ta några minuter.  
 
4. Ett meddelande visas under enheten och anger att enheten **har åtkomst till företagsresurser** eller att den **inte har åtkomst till företagsresurser**. 

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på avsnittet Status åtkomst.](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. Om enheten inte kan komma åt resurser väljer du enheten.  
6. På sidan **Enhetsinformation** går du till aviseringen överst på sidan. Klicka på **Mer** om du vill expandera dess egenskaper. Klicka på **Mindre** om du vill dölja dem.  

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på aviseringen överst på sidan.](./media/1809_CheckAccess_Device_details_alert1.png)  

6. Eventuella ytterligare hjälplänkar och rekommenderade åtgärder visas i meddelandet. Välj ett eller flera av dessa alternativ för att börja felsöka direkt. Lös-, synkroniserings- och kontaktåtgärderna &ndash;som beskrivs nedan&ndash;visas bara när du använder företagsportalen på den aktuella enheten.  

     * **Så här löser du problemet** öppnar en relevant hjälpartikel, om en sådan finns.  
     * **Lös** omdirigerar dig till inställningen på din enhet.  
     * **Synkronisera** utvärderar enheten och kontrollerar att den uppfyller din organisations krav.  
     * **Kontakta IT** omdirigerar dig till IT-teamets kontaktinformation.    

7. När du har uppdaterat inställningarna klickar du på **Kontrollera åtkomst** längst ned på sidan.  

    ![Exempelskärmbild av sidan Enhetsinformation i företagsportalappen för Windows, med fokus på åtgärden Kontrollera åtkomst.](./media/1809_CheckAccess_Device_details_button.png) 


Behöver du mer hjälp? Leta upp kontaktuppgifter till företagets support på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980).
