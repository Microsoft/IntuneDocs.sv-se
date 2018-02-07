---
title: "Hur du rensar endast företagsdata från appar"
titleSuffix: Azure portal
description: "Läs hur du selektivt rensar appar med Microsoft Intune.”"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7a9690e75e0d0dced9ad30951b0178685813eeae
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Hur du rensar endast företagsdata från Intune-hanterade appar

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Om en enhet tappas bort eller blir stulen eller om medarbetaren som använder enheten slutar på företaget vill du förmodligen ta bort företagets appdata från enheten. Men du kanske inte vill ta bort personliga data på enheten, särskilt inte om enheten ägs av den anställda.

>[!NOTE]
> iOS och Android är de plattformar som för närvarande stöder rensning av företagsdata på Intune-hanterade appar.

Om du vill ta bort företagets appdata selektivt skapar du en rensningsbegäran genom att följa stegen i det här avsnittet. När begäran har slutförts tas företagsdata bort från appen nästa gång den körs på enheten.

>[!IMPORTANT]
> Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.

## <a name="create-a-wipe-request"></a>Skapa en rensningsbegäran

1.  Logga in på [Azure Portal](https://portal.azure.com).

2.  Välj **Fler tjänster**, skriv **Intune** i filtrets textruta och välj **Intune**. Intune-bladet öppnas. Välj bladet **Mobilappar**.

    ![Skärmbild på bladet Microsoft Intune](./media/apps-selective-wipe01.png)

3.  Välj **Selektiv radering av app** på bladet **Mobilappar**.

4.  Välj  **Ny rensningsförfrågan**. Då öppnas bladet **Ny rensningsförfrågan**.

    ![Skärmbild av bladet Ny rensningsförfrågan](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Välj **Användare** för att öppna bladet **Användare** och välj den användare vars appdata du vill rensa.

6.  Välj sedan **Enhet** på bladet **Ny rensningsförfrågan**. Detta öppnar bladet **Välj enhet** med en lista över alla enheter som är associerade med den valda användaren. Den innehåller även två kolumner: namnet på enheten, som är ett eget namn som definierats av användaren, och typ av enhet, vilket är dess enhetsplattform. Välj den enhet som du vill rensa.

7.  Nu är du tillbaka på bladet **Ny rensningsförfrågan**. Välj **OK** för att skicka en rensningsförfrågan.

Tjänsten skapar och spårar en separat rensningsförfrågan för varje skyddad app på enheten, samt för användaren som är associerad med rensningsförfrågningar.

## <a name="monitor-your-wipe-requests"></a>Övervaka dina rensningsbegäranden

Du kan få en sammanfattande rapport som visar övergripande status för rensningsförfrågan och som innehåller antalet väntande förfrågningar och fel. Följ dessa steg för mer information:

1.  På bladet **Mobilappar – Selektiv radering av app** kan du se en lista över dina önskemål grupperade efter användare. Eftersom systemet skapar en rensningsbegäran för varje skyddad app som körs på enheten kan flera begäranden visas för en användare. Statusen anger om en rensningsbegäran är **väntande**, **misslyckad**eller **lyckad**.

    ![Skärmbild på status för rensningsförfrågan på bladet Selektiv radering av app](./media/wipe-request-status-1.png)

Dessutom kommer du att kunna se namnet på enheten och dess enhetstyp, vilket kan vara användbart vid läsning av rapporterna.

>[!IMPORTANT]
> Användaren måste öppna appen för att rensningen ska ske och rensningen kan ta upp till 30 minuter att slutföra efter att en begäran har gjorts.

## <a name="delete-a-wipe-request"></a>Ta bort en rensningsförfrågan

Rensningar med väntande status visas tills du tar bort dem manuellt.  Så här tar du bort en rensningsförfrågan manuellt:

1.  På bladet **Mobilappar – Selektiv radering av app**.

2.  Högerklicka på den rensningsförfrågan som du vill ta bort och välj sedan **Ta bort rensningsförfrågan**.

    ![Skärmbild på listan för rensningsförfrågan på bladet Selektiv radering av app](./media/delete-wipe-request.png)

3.  Du uppmanas att bekräfta borttagningen. Välj **Ja** eller **Nej** och klicka på **OK**.

### <a name="see-also"></a>Se även
[Vad är appskyddsprincip](app-protection-policy.md)

[Vad är apphantering](app-management.md)
