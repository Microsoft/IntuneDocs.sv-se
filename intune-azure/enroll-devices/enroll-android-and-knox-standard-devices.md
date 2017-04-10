---
title: Registrera Android-enheter i Intune
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Information om hur du registrerar Android-enheter i Intune Azure-förhandsversionen."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: b664620f424f9ef612d17beb810564dbdd68ff79
ms.lasthandoff: 03/22/2017


---

# <a name="enroll-android-devices"></a>Registrera Android-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune låter dig hantera Android-enheter, inklusive Samsung Knox Standard-enheter. Användarna måste registrera sina enheter genom att hämta Intunes företagsportalapp som är tillgänglig från Google Play och sedan öppna appen och följa anvisningarna för att registrera sig för att aktivera hantering av enheter. När Android-enheter är hanterade kan du [skapa efterlevnadsprinciper](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android), [hantera appar](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management) och mer.

## <a name="prerequisite"></a>Krav

Du måste ange MDM-utfärdare för **Microsoft Intune** så att du kan hantera mobila enheter. Fler anvisningar finns i [Ange MDM-utfärdare](set-mdm-authority.md). Du anger det här objektet bara en gång, och det är när du först konfigurerar Intune för hantering av mobila enheter. Så det kan hända att du redan har gjort de här inställningarna.

## <a name="set-up-android-enrollment"></a>Konfigurera Android-registrering

Som standard tillåter redan Intune registrering av Android- och Samsung Knox Standard-enheter.

Se [Ange begränsningar för enhetstyp](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions) för att blockera Android-enheter eller endast blockera personligt ägda Android-enheter från registrering.

Se [Ange begränsningar för enhetsgräns](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions) för att ange det maximala antalet enheter som en användare kan registrera.

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurserna

Du måste instruera slutanvändarna att de ska gå till Google Play för att hämta Intune-företagsportalappen, öppna appen och följa anvisningarna för att registrera sina enheter. Appen hjälper användarna genom registreringsprocessen och förklarar vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

Du kan även skicka dem en länk till stegen för registrering online: [Registrera en Android-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android).

Information om andra slutanvändaraktiviteter finns i de här artiklarna:

- [Resurser om slutanvändarupplevelsen med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Använda en Android-enhet med Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

