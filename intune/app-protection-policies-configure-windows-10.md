---
title: "Förbered konfigurationen av appskyddsprinciper för Windows 10"
titleSuffix: Intune on Azure
description: Konfigurera MAM-providern i Azure AD
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bf56d3a80f0d167baa95e9dfdb20d08e02590984
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Innan du skapar en appskyddsprincip för Windows 10 måste du aktivera hantering av mobila program (MAM) för Windows 10 genom att ställa in MAM-providern i Azure AD. Med den här konfigurationen kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune.

> [!NOTE]
> Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

## <a name="to-configure-the-mam-provider"></a>Konfigurera MAM-providern

1.  Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Azure Active Directory** på menyn till vänster.

    ![Konfiguration av MAM-providern](./media/mam-provider-sc-1.png)

3.  **Azure AD**-bladet öppnas. Välj **Mobilitet (MDM och MAM)** och klicka sedan på **Microsoft Intune**.

    ![MDM- och MAM-mobilitet](./media/mam-provider-sc-1.png)

4.  Konfigurationsbladet öppnas. Välj **Återställ standard MAM-URL:er** och konfigurera sedan följande:

    a.  MAM-användaromfattning: Du kan använda MAM för att skydda företagets data för en specifik användargrupp som använder Windows 10-enheter eller alla användare.

    b.  MAM användningsvillkors-URL: Slutpunkten för MAM-tjänstens användningsvillkors-URL. Denna används för att visa MAM-tjänstens villkor för slutanvändarna.

    c.  MAM Identifierings-URL: Detta är den URL som enheterna söker efter när de behöver tillämpa appskyddsprinciper.

    d.  MAM kompatibilitets-URL:

5.  Välj **Spara** när du har konfigurerat inställningarna.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](windows-information-protection-policy-create.md)
