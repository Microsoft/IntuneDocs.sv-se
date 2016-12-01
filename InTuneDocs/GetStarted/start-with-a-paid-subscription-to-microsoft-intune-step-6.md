---
title: Distribuera principer och appar | Microsoft Intune
description: "Du kan aktivera principinställningar och distribuera appar som kommer att tillämpas när enheterna har registrerats till hantering."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d2a3e5c05180c1a3f2ee3bf91813df3b5fa7bc6
ms.openlocfilehash: 679c49d135c9161ecae5db704a3f6c96add003dc


---

# <a name="create-policies-and-publish-apps"></a>Skapa principer och publicera appar
Innan du börjar registrera appar i Intune kan du aktivera principinställningar och appar som kommer att distribueras så snar som enheterna börjar hanteras. Intune-principerna förser dig med inställningar som hjälper dig att kontrollera säkerhetsinställningarna på mobila enheter, underhålla Windows-brandväggen och Endpoint Protection-inställningarna för datorer, samt distribuera program. Du kan konfigurera princip, lägga till appar och distribuera dessa appar så att enheter får inställningar och appar så snart de registreras i Intune.

Principer och program är plattformsspecifika.

## <a name="manage-device-settings"></a>Hantera inställningar för enheter

 Principinställningar för enheter konfigureras och hanteras enligt respektive plattform. Du kan konfigurera princip för följande plattformar:

- [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android och Samsung KNOX Standard](https://docs.microsoft.com/intune/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](https://docs.microsoft.com/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC och mobil)](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](https://docs.microsoft.com/intune/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](https://docs.microsoft.com/intune/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows-gruppen](https://docs.microsoft.com/intune/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [Windows-datorer som kör programvaruklienten Intune](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Du kan läsa mer om att [Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Lägg till och distribuera appar

Du kan lägga till appar i Intune och sedan distribuera dem till hanterade enheter på två sätt:
- **Nödvändig installation** – appar installerar automatiskt till hanterade enheter
- **Tillgänglig installation** – appar visas i Intune-företagsportalen så att användare kan välja att installera dem på sina enheter

### <a name="add-apps"></a>Lägga till appar

Först måste du göra appar tillgängliga i Intune med någon av följande metoder:
- [Lägga till appar för registrerade enheter](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Lägg till appar för klientdatorer med Intune-programvara](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Distribuera appar

Nu när appen är tillgänglig i Intune kan du distribuera den till hanterade enheter:
- [Distribuera appar till enheter](https://docs.microsoft.com/intune/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Distribuera volyminköpta appar:
    - [iOS – Volyminköpta program](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Windows Store för företag](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](https://docs.microsoft.com/en-us/Intune/deploy-use/android-for-work-apps)

    När du har konfigurerat appar för distributionen kan du [konfigurera appar](https://docs.microsoft.com/intune/deploy-use/update-apps-using-microsoft-intune) och [övervaka appar](https://docs.microsoft.com/intune/deploy-use/monitor-apps-in-microsoft-intune).


### <a name="next-steps"></a>Nästa steg
Gratulerar! Du är klar med steg 6 i *snabbstartsguiden för Intune*.

>[!div class="step-by-step"]

>[&larr; **Ordna användare och enheter**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md) [**Anpassa företagsportalen** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-7.md)  



<!--HONumber=Nov16_HO4-->


