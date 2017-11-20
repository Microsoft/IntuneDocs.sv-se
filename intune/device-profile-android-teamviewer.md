---
title: "Så här fjärradministrerar du enheter med TeamViewer"
titlesuffix: Azure portal
description: "Lär dig hur du fjärradministrerar enheter med TeamViewer.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a4e2b3493467f922b844130829db8e5ba14b246
ms.sourcegitcommit: 474a24ba67f6bf4f00268bf9e4eba52331a6b82d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="provide-remote-assistance-for-intune-managed-devices"></a>Ge fjärrhjälp för Intune-hanterade enheter

Intune kan använda [TeamViewer](https://www.teamviewer.com)-programmet (köps separat) för att ge fjärrhjälp till användare med enheter som du hanterar. Använd informationen i det här ämnet för att komma igång.

## <a name="before-you-start"></a>Innan du börjar

### <a name="supported-devices"></a>Enheter som stöds

Intune-hanterade Android- och Windows-enheter stöder fjärradministration.

>[!NOTE]
>Windows Holographic (HoloLens), Windows Team (Surface Hub) och Windows 10 S stöds inte av programmet TeamViewer. 



### <a name="required-permissions"></a>Behörigheter som krävs

Kontrollera att användaren i Azure-portalen har följande behörigheter som [Intune-roll](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control):
- Om du vill att administratören ska kunna ändra inställningarna för TeamViewer-anslutningsprogrammet beviljar du behörigheten **Uppdatera fjärrhjälp**.
- Om du vill att administratören ska kunna initiera en ny begäran om fjärrhjälp beviljar du behörigheten **Begär fjärrhjälp**. Användare med behörigheten **Begär fjärrhjälp** kan begära att initiera en session för valfri användare. De begränsas inte av någon omfattning för Intune-rolltilldelning. Intunes rolltilldelningsomfattningar begränsar inte vilka enheter eller användare som kan begära fjärrhjälp.

>[!NOTE]
>Genom att aktivera TeamViewer tillåter du att TeamViewer för Intune-anslutningsprogrammet kan skapa TeamViewer-sessioner, läsa Active Directory-data och spara TeamViewer-kontots åtkomsttoken.

### <a name="configure-the-intune-teamviewer-connector"></a>Konfigurera Intune TeamViewer-anslutningsprogrammet

Innan du kan ge fjärrhjälp till enheter måste du konfigurera Intune TeamViewer-anslutningsprogrammet med följande steg:


1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Konfiguration** > **TeamViewer-anslutningsprogram**.
5. På bladet **TeamViewer-anslutningsprogram** klickar du på **Aktivera** för att visa och godkänna licensavtalet för TeamViewer-tjänsten.
6. Välj **Logga in på TeamViewer och auktorisera**.
7. En webbsida öppnas med TeamViewer-webbplatsen. Ange dina autentiseringsuppgifter för TeamViewer-licensen och klicka sedan på **Logga in**.


## <a name="how-to-remotely-administer-a-device"></a>Så här fjärradministrerar du en enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter** väljer du **Hantera** > **Alla enheter**.
5. Välj den enhet som du vill fjärradministrera och välj på egenskapsbladet för enheten **Mer** > **Ny fjärrhjälpssession**.
6. När Intune ansluter till TeamViewer-tjänsten visas information enheten. Välj **Anslut** för att starta fjärrsessionen.

![TeamViewer-exempel i Android](./media/android-teamviewer.png)

I TeamViewer-fönstret kan du utföra olika fjärråtgärder på enheten, inklusive fjärrstyrning av enheten. Fullständig information om de åtgärder du kan utföra finns i [TeamViewer-dokumentationen](https://www.teamviewer.com/support/documents/).

Stäng TeamViewer-fönstret när du är klar.

## <a name="next-steps"></a>Nästa steg

Slutanvändarna ser en meddelandeflagga på ikonen för företagsportalappen på sin enhet och får även ett meddelande när appen öppnas. De kan då godkänna begäran om fjärrhjälp.

