---
title: "Så här fjärradministrerar du Android-enheter med TeamViewer"
titlesuffix: Azure portal
description: "Lär dig hur du fjärradministrerar Android-enheter med TeamViewer.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0a6286760e1e49cdb090736e9444fe8ce18ddeb7
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="provide-remote-assistance-for-intune-managed-android-devices"></a>Ge fjärrhjälp för Intune-hanterade Android-enheter

Intune kan använda [TeamViewer](https://www.teamviewer.com)-programmet (köps separat) för att ge fjärrhjälp till användare med Android-enheter. Använd informationen i det här ämnet för att komma igång.

## <a name="before-you-start"></a>Innan du börjar

### <a name="required-permissions"></a>Behörigheter som krävs

Kontrollera att användaren i Azure-portalen har följande behörigheter som [Intune-roll](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Om du vill att administratören ska kunna ändra inställningarna för TeamViewer-anslutningsprogrammet beviljar du behörigheten **Uppdatera fjärrhjälp**.
- Om du vill att administratören ska kunna initiera en ny begäran om fjärrhjälp beviljar du behörigheten **Begär fjärrhjälp**. Användare med behörigheten **Begär fjärrhjälp** kan begära att initiera en session för valfri användare. De begränsas inte av någon omfattning för Intune-rolltilldelning. Intunes rolltilldelningsomfattningar begränsar inte vilka enheter eller användare som kan begära fjärrhjälp.

>[!NOTE]
>Genom att aktivera TeamViewer tillåter du att TeamViewer för Intune-anslutningsprogrammet kan skapa TeamViewer-sessioner, läsa Active Directory-data och spara TeamViewer-kontots åtkomsttoken.

### <a name="configure-the-intune-teamviewer-connector"></a>Konfigurera Intune TeamViewer-anslutningsprogrammet

Innan du kan ge fjärrhjälp till Android-enheter måste du konfigurera Intune TeamViewer-anslutningsprogrammet med följande steg:


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Konfiguration** > **TeamViewer-anslutningsprogram**.
5. På bladet **TeamViewer-anslutningsprogram** klickar du på **Aktivera** för att visa och godkänna licensavtalet för TeamViewer-tjänsten.
6. Välj **Logga in på TeamViewer och auktorisera**.
7. En webbsida öppnas med TeamViewer-webbplatsen. Ange dina autentiseringsuppgifter för TeamViewer-licensen och klicka sedan på **Logga in**.


## <a name="how-to-remotely-administer-an-android-device"></a>Så här fjärradministrerar du en Android-enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter** väljer du **Hantera** > **Alla enheter**.
5. Välj den enhet som du vill fjärradministrera och välj på egenskapsbladet för enheten **Mer** > **Ny fjärrhjälpssession**.
6. När Intune ansluter till TeamViewer-tjänsten visas information om Android-enheten. Välj **Anslut** för att starta fjärrsessionen.

![TeamViewer-fönster i Android](./media/android-teamviewer.png)

I TeamViewer-fönstret kan du utföra olika fjärråtgärder på Android-enheten, inklusive fjärrstyrning av enheten. Fullständig information om de åtgärder du kan utföra finns i [TeamViewer-dokumentationen](https://www.teamviewer.com/support/documents/).

Stäng TeamViewer-fönstret när du är klar.

## <a name="end-user-notifications"></a>Meddelanden till slutanvändare

Slutanvändarna ser en meddelandeflagga på ikonen för företagsportalappen på sin enhet och får även ett meddelande när appen öppnas. De kan då godkänna begäran om fjärrhjälp.

