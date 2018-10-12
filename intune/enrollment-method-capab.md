---
title: Intune-funktioner efter registreringsmetod för Windows-enheter
titlesuffix: Microsoft Intune
description: Se vilka funktioner som varje registreringsmetod stöder för Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c9e440aef7f434cbe675506fd6f22a9bd26b2c31
ms.sourcegitcommit: 528d2bc70bfd25803a2d9f0fe9372c8a5f5e7dad
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446828"
---
# <a name="capabilities-by-enrollment-method-for-windows-devices"></a>Funktioner efter registreringsmetod för Windows-enheter
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med Intune kan du hantera personalens enheter och appar, samt hur de kommer åt företagsdata. Enheterna måste först registreras i Intune-tjänsten. Det finns flera metoder för att registrera personalens enheter. Olika metoder har olika metodtips och funktioner, som du ser i tabellerna nedan.

## <a name="best-practices-by-enrollment-method"></a>Metodtips efter registreringsmetod
| **Metodtips** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot](enrollment-autopilot.md)** |**[Bulk](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Vanliga i EDU|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Enheter kan användas som delade enheter|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Personliga enheter måste komma åt företagsresurser|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|
|Appar med självbetjäning|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktioner efter registreringsmetod

| **Funktioner** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot](enrollment-autopilot.md)** |**[Massregistrering](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **GPO** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Villkorlig åtkomst                                      |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Användaren associeras med enheten                    |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Kräver Azure AD Premium                               |![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|
|Enheten kan utvärdera resurser som skyddas av CA             |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Användarna får inte vara administratörer för sina enheter               |![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möjlighet att konfigurera enhetsinstallationsmiljön        |![X](media/xmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möjlighet att registrera enheter utan användarinteraktion      |![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|
|Möjlighet att köra PowerShell-skript                       |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Har stöd för automatisk registrering efter AD-domänanslutning      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|
|Har stöd för automatisk registrering efter Hybrid Azure AD-anslutning|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|
|Har stöd för automatisk registrering efter Azure AD-anslutning       |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Nästa steg

[Registreringsalternativ](enrollment-options.md)

