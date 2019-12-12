---
title: Principer för att skydda Windows-datorer
titleSuffix: Microsoft Intune
description: Använd dessa principer för att säkerställa säkerheten för Windows-datorer när de hanteras av Intune-klientprogramvaran.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d081f466-45dd-41d1-ab25-6d974c72a52a
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 306c67e2744c38cfc8214d1c8dee2732cd0bd1ce
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504993"
---
# <a name="use-policies-to-help-protect-windows-pcs-that-run-the-intune-client-software"></a>Använd principer för att skydda Windows-datorer som kör Intune-klientprogramvaran

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune innehåller tre principer som du kan använda för att säkerställa säkerheten för Windows-datorer som hanteras av [Intune-klientprogramvaran](../manage-windows-pcs-with-microsoft-intune.md).


## <a name="software-updates"></a>Programuppdateringar

Intune gör det enkelt att [hålla Windows-datorer som du hanterar uppdaterade](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) genom att informera dig när det finns viktiga programuppdateringar från Microsoft och andra företag. Du kan sedan godkänna eller avvisa uppdateringarna. Godkända uppdateringar installeras automatiskt på alla tillämpliga datorer.

## <a name="windows-firewall"></a>Windows-brandvägg

Windows-brandväggen hjälper till att hålla hackare, skadlig kod och andra hot borta från Windows-datorer. Med Intune kan du [hantera inställningar och funktioner för Windows-brandväggen](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) på alla datorer som du hanterar.

## <a name="endpoint-protection"></a>Slutpunktsskydd

Som IT-administratör är en av dina högsta prioriteter att [hålla Windows-datorer som du hanterar fria från skadlig kod och virus](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md). Intune integreras med Endpoint Protection för att ge realtidsskydd mot hot från skadlig kod, hålla definitioner för skadlig kod aktuella och skanna datorer automatiskt. Endpoint Protection innehåller dessutom verktyg som hjälper dig att hantera och övervaka angrepp från skadlig kod.

## <a name="see-also"></a>Se även

[Vanliga frågor, problem och lösningar med enhetsprinciper och enhetsprofiler](../configuration/device-profile-troubleshoot.md)
