---
title: Rensa hanterade företagsdata från appar
description: Läs om hur du tar bort företagsdata från enheter selektivt via fjärranslutning.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8d946b551118441b737335f6bd8c4603a49e0dd2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="wipe-company-app-data-with-intune-mam"></a>Rensa företagets appdata med Intune MAM

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Om en enhet tappas bort eller blir stulen eller om medarbetaren som använder enheten slutar på företaget vill du förmodligen ta bort företagets appdata från enheten. Men du kanske inte vill ta bort personliga data på enheten, särskilt inte om enheten ägs av den anställda.

Om du vill ta bort företagets appdata selektivt skapar du en rensningsbegäran genom att följa stegen i det här avsnittet. När begäran har slutförts tas företagsdata bort från appen nästa gång den körs på enheten.

>[!IMPORTANT]
> Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.

## <a name="create-a-wipe-request"></a>Skapa en rensningsbegäran

1.  Logga in på [Azure Portal](https://portal.azure.com).

2.  Välj **Fler tjänster**, skriv **Intune** i filtrets textruta och välj **Intune App Protection**. Bladet för hantering av mobilprogram i Intune öppnas.

    ![Skärmbild av bladet Ny rensningsförfrågan](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  På bladet **Inställningar** väljer du **Rensningsförfrågningar**.

3.  Välj  **Ny rensningsförfrågan**. Då öppnas bladet **Ny rensningsförfrågan**.

    ![Skärmbild av bladet Ny rensningsförfrågan](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  Välj **Användare** för att öppna bladet **Användare** och välj den användare vars appdata du vill rensa.

5.  Välj **Enhet**. Detta öppnar bladet **Enhet** med en lista över alla enheter som är associerade till den valda användaren. Den innehåller även två kolumner; namnet på enheten, som är ett eget namn som definierats av användaren, och typ av enhet, vilket är dess enhetsplattform. Välj den enhet som du vill rensa.

6.  Nu är du tillbaka på bladet **Ny rensningsförfrågan**. Välj **OK** för att skicka en rensningsförfrågan. 

Tjänsten skapar och spårar en separat rensningsförfrågan för varje skyddad app på enheten, samt för användaren som är associerad med rensningsförfrågningar.

>[!NOTE]
> Du kan också skapa **Rensningsförfrågningar** genom att klicka på **rutan Rensningsförfrågan** på bladet för hantering av mobilprogram i Intune.

## <a name="monitor-your-wipe-requests"></a>Övervaka dina rensningsbegäranden

Du kan få en sammanfattande rapport som visar övergripande status för rensningsförfrågan och som innehåller antalet väntande förfrågningar och fel. Följ dessa steg för mer information:

1.  Klicka på ikonen **Rensningsförfrågningar** på bladet för hantering av mobilprogram i Intune.

2.  Öppna bladet **Rensningsbegäran** genom att välja panelen **Rensningsbegäran** på bladet **Rensningsbegäran**.

3.  På bladet **Rensningsbegäran** ser du listan med dina begäranden grupperade efter användare. Eftersom systemet skapar en rensningsbegäran för varje skyddad app som körs på enheten kan flera begäranden visas för en användare. Statusen anger om en rensningsbegäran är **väntande**, **misslyckad**eller **lyckad**.

    ![Skärmbild av bladet Ny rensningsförfrågan](../media/AppManagement/wipe-request-status-1.png)

Dessutom kommer du att kunna se namnet på enheten och dess enhetstyp, vilket kan vara användbart vid läsning av rapporterna.

>[!IMPORTANT]
> Användaren måste öppna appen för att rensningen ska ske och rensningen kan ta upp till 30 minuter att slutföra efter att en begäran har gjorts.

## <a name="delete-a-wipe-request"></a>Ta bort en rensningsförfrågan

Rensningar med väntande status visas tills du tar bort dem manuellt.  Så här tar du bort en rensningsförfrågan manuellt

1.  Klicka på ikonen **Rensningsförfrågningar** på bladet för hantering av mobilprogram i Intune.

2.  Öppna bladet **Rensningsbegäran** genom att välja panelen **Rensningsbegäran** på bladet **Rensningsbegäran**.

3.  Högerklicka på den rensningsförfrågan som du vill ta bort och välj sedan **Ta bort rensningsförfrågan**.

    ![Skärmbild av bladet Ny rensningsförfrågan](../media/AppManagement/delete-wipe-request.png)

4.  Du uppmanas att bekräfta borttagningen. Välj **Ja** eller **Nej** och klicka på **OK**.


### <a name="see-also"></a>Se även
[Skydda appdata med principer för hantering av mobila appar](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Använda Azure Portal](azure-portal-for-microsoft-intune-mam-policies.md)
