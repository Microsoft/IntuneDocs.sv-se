---
title: "Rensa hanterade företagsdata från appar | Microsoft Intune"
description: "Läs om hur du tar bort företagsdata från enheter selektivt via fjärranslutning."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: d32a66ee283906586e25173e736c02ee8bf23042


---

# <a name="wipe-managed-company-app-data-with-microsoft-intune"></a>Rensa hanterade företagsdata från appar med Microsoft Intune
Om en enhet tappas bort eller blir stulen eller om medarbetaren som använder enheten slutar på företaget vill du förmodligen ta bort företagets appdata från enheten. Men du kanske inte vill ta bort personliga data på enheten, särskilt inte om enheten ägs av den anställda.

Om du vill ta bort företagets appdata selektivt skapar du en rensningsbegäran genom att följa stegen i det här avsnittet. När begäran har slutförts tas företagsdata bort från appen nästa gång den körs på enheten.
>[!NOTE]
> Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.



## <a name="create-a-wipe-request"></a>Skapa en rensningsbegäran

1.  Välj panelen **Rensningsförfrågningar** på bladet **Hantering av mobilprogram i Intune** .

    ![Skärmbild av bladet Hantering av mobilprogram i Intune med sammanfattningspaneler](../media/AppManagement/AzurePortal_MAM_WipeRequests.png)

2.  Välj  **Ny rensningsförfrågan**. Nu öppnas bladet **Ny rensningsförfrågan**.

    ![Skärmbild av bladet Ny rensningsförfrågan](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

3.  Välj **Användare** för att öppna bladet **Användare** och välj den användare vars appdata du vill rensa.

4.  Välj **Enhet**.  När du gör det öppnas bladet **Enhet** som visar en lista över alla enheter som är associerade med den valda användaren.  Välj den enhet som du vill rensa.

5.  Nu är du tillbaka på bladet **Ny rensningsförfrågan**. Välj **OK** för att skicka en rensningsförfrågan. Tjänsten skapar och spårar en separat rensningsbegäran för varje skyddad app på enheten.


![Skärmbild av rutan Rensningsförfrågningar ](../media/AppManagement/AzurePortal_MAM_WipeRequestsSummary.png)

## <a name="monitor-your-wipe-requests"></a>Övervaka dina rensningsbegäranden
Bladet **Hantering av mobilprogram i Intune** innehåller en sammanfattad rapport på ikonen **Rensningsbegäran** .  Bladet visar den allmänna statusen och innehåller antalet väntande begäranden och misslyckade begäranden. Du kan få mer information genom att följa dessa steg:

1.  Öppna bladet **Rensningsförfrågan** genom att välja panelen **Rensningsförfrågan** på bladet **Hantering av mobilprogram i Intune** .

2.  På bladet **Rensningsbegäran** ser du listan med dina begäranden grupperade efter användare. Eftersom systemet skapar en rensningsbegäran för varje skyddad app som körs på enheten kan flera begäranden visas för en användare. Statusen anger om en rensningsbegäran är **väntande**, **misslyckad**eller **lyckad**.

Användaren måste öppna appen för att rensningen ska ske och rensningen kan ta upp till 30 minuter att slutföra efter att en begäran har gjorts.

Rensningar med väntande status visas tills du tar bort dem manuellt.  Högerklicka och välj Ta bort för att ta bort en rensningsbegäran manuellt.

### <a name="see-also"></a>Se även
[Skydda appdata med principer för hantering av mobila appar](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Använda Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md)



<!--HONumber=Dec16_HO2-->


