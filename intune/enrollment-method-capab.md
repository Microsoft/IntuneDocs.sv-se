---
title: Funktioner i Intune-registreringsmetoden för Windows-enheter
titleSuffix: Microsoft Intune
description: Funktioner i varje registreringsmetod för Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: dd1dbb3280fbbb93423796b18f6dd85a50a41f11
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567549"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funktioner i Intune-registreringsmetoden för Windows-enheter
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det finns flera olika metoder för att registrera personalens enheter i Intune. Olika metoder har olika metodtips och funktioner, som du ser i tabellerna nedan.

## <a name="best-practices-by-enrollment-method"></a>Metodtips efter registreringsmetod
| **Metodtips** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot (användarläge)](enrollment-autopilot.md)** |**[Azure AD-ansluten med Autopilot (självdistribuerande läge)](enrollment-autopilot.md)** |**[Massregistrering](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Vanliga i EDU|![X](media/xmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Enheter kan användas som delade enheter|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Personliga enheter måste komma åt företagsresurser|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Appar med självbetjäning|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktioner efter registreringsmetod

| **Funktioner** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot (användarläge)](enrollment-autopilot.md)** |**[Azure AD-ansluten med Autopilot (självdistribuerande läge)](enrollment-autopilot.md)** |**[Massregistrering](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Villkorlig åtkomst                                      |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Användaren associeras med enheten                    |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Kräver Azure AD Premium                               |![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Enheten kan utvärdera resurser som skyddas av CA             |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Användarna får inte vara administratörer för sina enheter               |![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möjlighet att konfigurera enhetsinstallationsmiljön        |![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|
|Möjlighet att registrera enheter utan användarinteraktion      |![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Möjlighet att köra PowerShell-skript                       |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)| 
|Har stöd för automatisk registrering efter AD-domänanslutning      |![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Har stöd för automatisk registrering efter Hybrid Azure AD-anslutning|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|
|Har stöd för automatisk registrering efter Azure AD-anslutning       |![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![Markering](media/checkmark.png)|![X](media/xmark.png)|![X](media/xmark.png)|

## <a name="next-steps"></a>Nästa steg

[Konfigurera registrering för Windows](windows-enroll.md)

