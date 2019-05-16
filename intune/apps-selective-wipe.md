---
title: Hur du rensar endast företagsdata från appar
titleSuffix: Microsoft Intune
description: Lär dig hur du selektivt rensar endast företagsdata från Intune-hanterade appar med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/24/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83cc1f43faba1ee98bde680b1ff2b74c78ff65e4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389505"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Hur du rensar endast företagsdata från Intune-hanterade appar

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Om en enhet tappas bort eller blir stulen eller om medarbetaren som använder enheten slutar på företaget vill du förmodligen ta bort företagets appdata från enheten. Men du kanske inte vill ta bort personliga data på enheten, särskilt inte om enheten ägs av medarbetaren.

>[!NOTE]
> iOS, Android och Windows 10 är de plattformar som för närvarande stöder rensning av företagsdata på Intune-hanterade appar. Intune-hanterade appar är program som innehåller Intune APP-SDK:n och har ett licensierat användarkonto för organisationen. Distribution av programskyddsprinciper krävs inte för att aktivera selektiv radering av app.

Om du vill ta bort företagets appdata selektivt skapar du en rensningsbegäran genom att följa stegen i det här avsnittet. När begäran har slutförts tas företagsdata bort från appen nästa gång den körs på enheten. Utöver att skapa en rensningsbegäran kan du konfigurera en selektiv rensning av organisationens data som en ny åtgärd när villkoren för åtkomstinställningar för appskyddsprinciper inte uppfylls. Den här funktionen gör att du kan skydda och ta bort känsliga organisationsdata från appar baserat på förkonfigurerade kriterier.

>[!IMPORTANT]
> Kontakter som synkroniseras direkt från appen till den interna adressboken tas bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för Microsoft Outlook-appen.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Distribuerade WIP-principer utan användarregistrering
WIP-principer (Windows Information Protection) kan distribueras utan att MDM-användare behöver registrera sina Windows 10-enheter. Med den här konfigurationen kan företag skydda sina företagsdokument baserat på WIP-konfigurationen, samtidigt som användarna kan fortsätta att hantera sina egna Windows-enheter. När dokument skyddas med en WIP-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-principen oanvändbara. Från Intune på Azure-portalen väljer du **Klientapp** > **Selektiv radering av app**. Mer information finns i [Skapa och distribuera en WIP-appskyddsprincip med Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Skapa en rensningsbegäran

1.  Logga in på [Azure Portal](https://portal.azure.com).

2.  Välj **Alla tjänster**, skriv **Intune** i filtrets textruta och välj **Intune**. Intune-fönstret öppnas. Välj fönstret **Klientappar**.

    ![Skärmbild på fönstret Microsoft Intune](./media/apps-selective-wipe01.png)

3.  Välj **Selektiv radering av app** i fönstret **Klientappar**.

4.  Välj  **Ny rensningsförfrågan**. Då öppnas fönstret **Ny rensningsförfrågan**.

    ![Skärmbild av fönstret Ny rensningsförfrågan](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Välj en användare och sedan **Välj** för att välja användaren vars appdata du vill rensa.

6.  Välj sedan **Enhet** i fönstret **Ny rensningsförfrågan**. Detta öppnar fönstret **Välj enhet** med en lista över alla enheter som är associerade med den valda användaren. Den innehåller även två kolumner: namnet på enheten, som är ett eget namn som definierats av användaren, och typ av enhet, vilket är dess enhetsplattform. Välj den enhet som du vill rensa.

7.  Nu är du tillbaka i fönstret **Ny rensningsförfrågan**. Välj **OK** för att skicka en rensningsförfrågan.

Tjänsten skapar och spårar en separat rensningsförfrågan för varje skyddad app på enheten, samt för användaren som är associerad med rensningsförfrågningar.

## <a name="monitor-your-wipe-requests"></a>Övervaka dina rensningsbegäranden

Du kan få en sammanfattande rapport som visar övergripande status för rensningsförfrågan och som innehåller antalet väntande förfrågningar och fel. Följ dessa steg för mer information:

1.  I fönstret **Klientappar – Selektiv radering av app** kan du se en lista över dina önskemål grupperade efter användare. Eftersom systemet skapar en rensningsbegäran för varje skyddad app som körs på enheten kan flera begäranden visas för en användare. Statusen anger om en rensningsbegäran är **väntande**, **misslyckad**eller **lyckad**.

    ![Skärmbild på status för rensningsförfrågan i fönstret Selektiv radering av app](./media/wipe-request-status-1.png)

Dessutom kan du se namnet på enheten och dess enhetstyp, vilket kan vara användbart vid läsning av rapporterna.

>[!IMPORTANT]
> Användaren måste öppna appen för att rensningen ska ske och rensningen kan ta upp till 30 minuter att slutföra efter att en begäran har gjorts.

## <a name="delete-a-wipe-request"></a>Ta bort en rensningsförfrågan

Rensningar med väntande status visas tills du tar bort dem manuellt. Så här tar du bort en rensningsförfrågan manuellt:

1.  I fönstret **Klientappar – Selektiv radering av app**.

2.  Högerklicka på den rensningsförfrågan som du vill ta bort och välj sedan **Ta bort rensningsförfrågan**.

    ![Skärmbild på listan för rensningsförfrågan i fönstret Selektiv radering av app](./media/delete-wipe-request.png)

3.  Du uppmanas att bekräfta borttagningen. Välj **Ja** eller **Nej** och klicka på **OK**.

### <a name="see-also"></a>Se även
[Vad är appskyddsprincip](app-protection-policy.md)

[Vad är apphantering](app-management.md)
