---
title: "Förbered konfigurationen av appskyddsprinciper för Windows 10 | Microsoft Docs"
description: Konfigurera MAM-providern i Azure AD
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 86a59771fc57971a626f71083e81cd4b7d858cfa
ms.lasthandoff: 04/25/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Innan du skapar en appskyddsprincip för Windows 10 måste du aktivera hantering av mobila program (MAM) för Windows 10 genom att ställa in MAM-providern i Azure AD. Med den här konfigurationen kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune.

> [!NOTE]
> Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

## <a name="to-configure-the-mam-provider"></a>Konfigurera MAM-providern

1.  Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2.  Välj **Azure Active Directory** på menyn till vänster.

    ![Konfiguration av MAM-providern](../media/AppManagement/mam-provider-sc-1.png)

3.  **Azure AD**-bladet öppnas. Välj **Mobilitet (MDM och MAM)** och klicka sedan på **Microsoft Intune**.

    ![MDM- och MAM-mobilitet](../media/AppManagement/mam-provider-sc-1.png)

4.  Konfigurationsbladet öppnas. Välj **Återställ standard MAM-URL:er** och konfigurera sedan följande:

    a.  MAM-användaromfattning: Du kan använda MAM för att skydda företagets data för en specifik användargrupp som använder Windows 10-enheter eller alla användare.

    b.  MAM användningsvillkors-URL: Slutpunkten för MAM-tjänstens användningsvillkors-URL. Denna används för att visa MAM-tjänstens villkor för slutanvändarna.

    c.  MAM Identifierings-URL: Detta är den URL som enheterna söker efter när de behöver tillämpa appskyddsprinciper.

    d.  MAM kompatibilitets-URL:

5.  Välj **Spara** när du har konfigurerat inställningarna.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](https://docs.microsoft.com/intune/deploy-use/create-windows-information-protection-policy-with-intune)

