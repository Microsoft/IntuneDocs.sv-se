---
title: Registrera Android Enterprise-arbetsprofilenheter i Intune
titleSuffix: Microsoft Intune
description: Läs om hur du registrerar Android Enterprise-arbetsprofilenheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4339f98ed133c3426faee8bd4b18024fd2648606
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72503351"
---
# <a name="set-up-enrollment-of-android-enterprise-work-profile-devices"></a>Konfigurera registrering av Android Enterprise-arbetsprofilenheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune hjälper dig att distribuera appar och inställningar till Android Enterprise-arbetsprofilenheter för att arbetsrelaterad och personlig information ska kunna hållas isär. Specifik information om Android Enterprise finns i [Krav för Android Enterprise](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012).

Du kan konfigurera Android Enterprise-arbetsprofilhantering så här:

1. [Anslut ditt Intune-klientorganisationskonto till ditt Android Enterprise-konto](connect-intune-android-enterprise.md).
2. Ange inställningar för Android Enterprise-arbetsprofilregistreringen. Android Enterprise-arbetsprofiler [stöds bara på vissa Android-enheter](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22). Alla enheter som har stöd för Android Enterprise-arbetsprofiler stöder även Android-enhetsadministratörhantering. Med Intune kan du ange hur enheter med stöd för Android Enterprise-arbetsprofiler ska hanteras inifrån [Registreringsbegränsningar](enrollment-restrictions-set.md).
    - **Blockera**:  Alla Android-enheter, inklusive enheter som stöder Android Enterprise Work-profiler, registreras som Android-enhetens administratörsenheter, om inte registrering av Android-enhetsadministratörer också är blockerat. 
    - **Tillåt (ange som standard)** : Alla enheter som stöder Android Enterprise-arbetsprofiler registreras som Android Enterprise-arbetsprofilenheter. Alla Android-enheter som inte stöder Android Enterprise Work-profiler registreras som Android-enhetens administratörsenheter, om inte registrering av Android-enhetsadministratörer är blockerat. 
> [!NOTE]
> Standardinställningen **Tillåt** gäller för nya klienter från och med juli 2019. Alla tidigare klienter se ingen ändring av sina registreringsbegränsningar och kommer att se de principer som de har angett i registreringsbegränsningar. För tidigare klienter som aldrig hade ändrat registreringsbegränsningarna kommer **Blockera** fortfarande vara standardinställningen för Android Enterprise-arbetsprofiler.

3. [Berätta för dina användare hur de registrerar sina enheter](/intune-user-help/create-a-work-profile-and-enroll-your-device-in-intune-android).  

Om du vill registrera enheter i Android Enterprise-arbetsprofiler, men enheterna redan har registrerats som Android-enhetsadministratörer, måste de enheterna först avregistreras och sedan registreras på nytt.
> [!NOTE]
> Som administratör kan du göra detta via en fjärranslutning med hjälp av funktionen **Dra tillbaka**. Den här funktionen finns i åtgärdsmenyn när du har valt enheten från bladet **Alla enheter**.

Om du registrerar Android Enterprise-arbetsprofilenheter med hjälp av ett konto för [Enhetsregistreringshanteraren](device-enrollment-manager-enroll.md), går det att registrera högst 10 enheter per konto.

Mer information finns i [Data som Intune skickar till Google](../protect/data-intune-sends-to-google.md).

## <a name="next-steps-for-android-enterprise-work-profiles"></a>Nästa steg för Android Enterprise-arbetsprofiler
- [Distribuera Android Enterprise-arbetsprofilappar](../apps/apps-add-android-for-work.md)
- [Lägga till konfigurationsprinciper för Android Enterprise-arbetsprofiler](../configuration/device-profiles.md)

## <a name="see-also"></a>Se även

[Konfigurera och felsöka Android-företagsenheter i Microsoft Intune](https://support.microsoft.com/help/4476974)
