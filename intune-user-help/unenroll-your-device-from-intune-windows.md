---
title: Ta bort en Windows-enhet från Intune-hanteringen
description: Beskriver hur du tar bort en Windows-enhet från Intune-hanteringen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 5984ac8ebe825a187b33945699a5fadc27e0c0cc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828422"
---
# <a name="remove-your-windows-device-from-management"></a>Ta bort din Windows-enhet från hanteringen

Ta bort en registrerad Windows-enhet från hanteringen när du inte längre vill eller behöver hantera den:  
* Använd din enhet på arbetet eller i skolan. 
* Komma åt arbetets eller skolans e-post, appar eller andra resurser.

När du avregistrerar enheten kan du inte längre komma åt skol- eller arbetsresurser från enheten. Du kan ta bort följande Windows-enheter från hanteringen.  
* Windows 10-enheter 
* Windows 8.1-dator
* Windows 8.1-telefon
 
Mer information om vad som händer när du tar bort enheten från hanteringen finns i [Vad händer om du tar bort enheten från Intune](what-happens-if-you-unenroll-your-device-from-intune-windows.md).  

## <a name="remove-your-windows-10-device"></a>Ta bort din Windows 10-enhet
Utför följande steg om du vill ta bort en Windows 10-enhet från hanteringen.

### <a name="remove-in-company-portal-app-home-page"></a>Ta bort via **startsidan** i företagsportalappen  

1. Öppna företagsportalappen.
2. Gå ned till avsnittet **Mina enheter** på **startsidan**.
3. Välj den enhet som du vill ta bort.
3. I det övre högra hörnet på appen, väljer du ikonen **Se mer**.
4. Välj **Ta bort**. 
5. Bekräfta borttagningen av enheten genom att välja **Ta bort**.  

### <a name="remove-in-company-portal-app-device-context-menu"></a>Ta bort via enhetens snabbmeny i företagsportalappen  

1. Öppna företagsportalappen och gå till **Mina enheter**.

    ![Exempel på skärmbild av startsidan i företagsportalappen för Windows, med fokus på avsnittet Mina enheter.](./media/1809_CheckAccess_Context_Select_Device.png)

2. Högerklicka på eller tryck på och håll ned en enhet för att öppna enhetens [snabbmeny](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus).  

3. Välj **Ta bort**.  

    ![Exempel på skärmbild av startsidan i företagsportalappen för Windows. Snabbmenyn för enheten visas i avsnittet **Mina enheter** på sidan och visar åtgärderna ”Byt namn”, ”Ta bort” och ”Kontrollera åtkomst”.](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. I bekräftelsen klickar du på **Läs mer** om du vill veta mer om hur din åtkomst till arbets- och skolresurser kan ändras. Bekräfta borttagningen av enheten genom att välja **Ta bort**.   

     ![Exempel på skärmbild av startsidan i företagsportalappen för Windows. Fältet Byt namn visas över enheten där användaren kan ange ett nytt namn och klicka på Byt namn eller Avbryt.](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>Ta bort i inställningsappen för enheten
1. Öppna inställningsappen. 
2. Gå till **Konton** > **Åtkomst till arbete eller skola**.
3. Välj det anslutna konto som du vill ta bort > **Koppla från**.
4. För att bekräfta borttagning av en enhet, välj **Ja**.

## <a name="remove-your-windows-81-computer"></a>Ta bort din Windows 8.1-dator
Utför följande steg om du vill ta bort en Windows 8.1-dator från Intune.

1.  Gå till **Datorinställningar** > **Nätverk** > **Arbetsplats**.
2.  Under **Anslut till arbetsplats** väljer du **Lämna**.
3.  Under **Turn on device management** (Aktivera enhetshantering) väljer du **Inaktivera**.
4.  I popup-fönstret som öppnas väljer du **Inaktivera**.

## <a name="remove-your-windows-81-phone"></a>Ta bort din Windows 8.1-telefon
Utför följande steg om du vill ta bort en Windows 8.1-telefon från Intune.

1.  Gå till **Inställningar** > **Arbetsplats**.
2.  Tryck på arbetsplatskontot som du vill avregistrera.
3.  Tryck på **Ta bort** längst ned på skärmen.
4.  Tryck på **Ta bort** i dialogrutan **Ta bort konto**.  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>Ta bort din personliga information när du tagit bort företagsportalen  

Det finns två typer av data som företagsportalen lagrar på din Windows-enhet:

-   **Diagnostikloggar**: Standarddata om appaktivitet som Microsoft samlar in. Dessa data raderas automatiskt när du avinstallerar företagsportalappen. Aktivitetsdata för appen är till exempel data om hur länge appen var öppen eller om appen har kraschat.
-   **Cacheminne**: Stödfiler som krävs för att appen ska fungerar, till exempel ikoner och inställningar.

Om du vill ta bort lagrade loggar och cacheminnet utför du något av följande steg:

* [Avinstallera företagsportalappen](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* Återställ företagsportalappen. Öppna appen **Inställningar** och välj > **Appar** > **Företagsportal** > **Avancerade alternativ** > **Återställ**. 

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
