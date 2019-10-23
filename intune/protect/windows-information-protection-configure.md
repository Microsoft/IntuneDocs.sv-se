---
title: Inställningar för Windows informationsskydd i Microsoft Intune
titleSuffix: Microsoft Intune
description: Lär dig mer om Microsoft Intune-inställningar som du kan använda för att hantera Windows informationsskydd.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f4c8f30359869761482e55680c9d935722bdf67
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508737"
---
# <a name="how-to-configure-windows-information-protection-in-microsoft-intune"></a>Hur du konfigurerar inställningar för Windows informationsskydd i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Allt fler anställda använder egna enheter i företaget. Detta innebär en ökad risk för oavsiktliga dataläckage via appar och tjänster, till exempel e-post, sociala media och offentliga moln, som företaget inte har någon kontroll över. En medarbetare kan till exempel skicka de senaste ritningarna via sitt personliga e-postkonto, kopiera och klistra in produktinformation i en tweet eller spara en försäljningsrapport på en offentlig molnlagringsplats.

**Windows informationsskydd** bidrar till att skydda mot potentiella dataläckage utan att störa användarupplevelsen för de anställda. Informationsskyddet skyddar även företagsappar och företagsdata mot oavsiktliga dataläckage i företagsägda enheter och personliga enheter som medarbetarna tar med sig till jobbet utan att det behövs några ändringar i miljön eller andra appar.

Den här Intune-principen hanterar listan över appar som skyddas av Windows informationsskydd, företagsnätverksplatser, skyddsnivå och krypteringsinställningar.

>[!NOTE]
> Om du vill använda företagsportalappen för Windows 10 med Windows informationsskydd, måste du lägga till företagsportalappen i Windows informationsskyddsläget som **Undantag**. 

Mer information finns i:
- [Skydda företagsdata med hjälp av Windows Information Protection](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
- [Skapa en princip för Windows Information Protection (WIP) med den klassiska konsolen för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune)
- [Skapa en princip för Windows Information Protection (WIP) med MDM med hjälp av Azure Portal för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-intune-azure)
- [Skapa en princip för Windows Information Protection (WIP) med MAM med hjälp av Azure Portal för Microsoft Intune](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure)
