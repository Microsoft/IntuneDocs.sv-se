---
title: Distribuera principer och appar
description: "Du kan aktivera principinställningar och distribuera appar som kommer att tillämpas när enheterna har registrerats till hantering."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0d1e88db4a0da250f449c8e87f674f7694904d7b
ms.sourcegitcommit: 1c71fff769ca0097faf46fc2b58b953ff28386e8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/08/2017
---
# <a name="create-policies-and-publish-apps"></a>Skapa principer och publicera appar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet riktar sig till Intune-administratörer och beskriver hur de kan skapa principer och publicera appar som de sedan kan distribuera till hanterade enheter.

Innan du börjar registrera appar i Intune kan du aktivera principinställningar och appar som kommer att distribueras så snar som enheterna börjar hanteras. Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program. Du kan konfigurera princip, lägga till appar och distribuera dessa appar så att enheter får inställningar och appar så snart de registreras i Intune.

Principer och program är plattformsspecifika.

## <a name="manage-device-settings"></a>Hantera inställningar för enheter

 Principinställningar för enheter konfigureras och hanteras enligt respektive plattform. På följande länkar finns listor över tillgängliga inställningar för respektive plattform:

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android och Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC och mobil)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows-gruppen](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Windows-datorer som kör programvaruklienten Intune](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Du kan läsa mer om att [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Lägg till och distribuera appar

Du kan lägga till appar i Intune och sedan distribuera dem till hanterade enheter på två sätt:
- **Nödvändig installation** – appar installerar automatiskt till hanterade enheter
- **Tillgänglig installation** – appar visas i Intune-företagsportalen så att användare kan välja att installera dem på sina enheter

### <a name="add-apps"></a>Lägga till appar

Först måste du göra appar tillgängliga i Intune med någon av följande metoder:
- [Lägga till appar för registrerade enheter](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Lägg till appar för klientdatorer med Intune-programvara](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Distribuera appar

Nu när appen är tillgänglig i Intune kan du distribuera den till hanterade enheter:
- [Distribuera appar till enheter](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Distribuera volyminköpta appar:
    - [iOS – Volyminköpta program](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Microsoft Store för företag](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    När du har konfigurerat appar för distribution kan du [konfigurera appar](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Ordna användare och enheter**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md) [**Anpassa företagsportalen** &rarr;](/intune/company-portal-customize)  
