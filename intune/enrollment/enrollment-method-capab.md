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
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30b46fcbb7ec6963e855c79478dbdef5b5cd8b90
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723144"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Funktioner i Intune-registreringsmetoden för Windows-enheter
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Det finns flera olika metoder för att registrera personalens enheter i Intune. Olika metoder har olika metodtips och funktioner, som du ser i tabellerna nedan.

## <a name="best-practices-by-enrollment-method"></a>Metodtips efter registreringsmetod
| **Metodtips** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot (användarläge)](enrollment-autopilot.md)** |**[Azure AD-ansluten med Autopilot (självdistribuerande läge)](enrollment-autopilot.md)** |**[Massregistrering](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Vanliga i EDU|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Enheter kan användas som delade enheter|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Personliga enheter måste komma åt företagsresurser|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Appar med självbetjäning|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>Funktioner efter registreringsmetod

| **Funktioner** | **[Azure AD-ansluten](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Azure AD-ansluten med Autopilot (användarläge)](enrollment-autopilot.md)** |**[Azure AD-ansluten med Autopilot (självdistribuerande läge)](enrollment-autopilot.md)** |**[Massregistrering](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[Samhantering](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Villkorlig åtkomst                                      |![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Användaren associeras med enheten                    |![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Kräver Azure AD Premium                               |![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Enheten kan utvärdera resurser som skyddas av CA             |![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Användarna får inte vara administratörer för sina enheter               |![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Möjlighet att konfigurera enhetsinstallationsmiljön        |![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|Möjlighet att registrera enheter utan användarinteraktion      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Möjlighet att köra PowerShell-skript                       |![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|Har stöd för automatisk registrering efter AD-domänanslutning      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Har stöd för automatisk registrering efter Hybrid Azure AD-anslutning|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|
|Har stöd för automatisk registrering efter Azure AD-anslutning       |![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![Markering](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

\* Arbetsbelastningar för klientprogram i Configuration Manager måste flyttas till Intune Pilot eller Intune.

## <a name="next-steps"></a>Nästa steg

[Konfigurera registrering för Windows](windows-enroll.md)

