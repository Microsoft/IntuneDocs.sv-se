---
title: Aktivera övervakat läge på iOS/iPadOS med Microsoft Intune
titleSuffix: ''
description: Lär dig hur du aktiverar övervakat läge på iOS/iPadOS med Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d266dbc9fa72b1579e05e7798315e2e718a9797
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413669"
---
# <a name="turn-on-iosipados-supervised-mode"></a>Aktivera övervakat läge på iOS/iPadOS


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Övervakat läge på Apple iOS/iPadOS ger administratörer fler alternativ vid hantering av Apple-enheter, vilket gör att det blir användbart för företagsägda enheter som distribueras i större skala. Du kan till exempel begränsa AirDrop eller hindra användare från att ändra namnet på enheten. [Inställningar för enhetsbegränsningar för iOS-enheter i Microsoft Intune](../configuration/device-restrictions-ios.md) innehåller en lista med inställningar som kräver övervakat läge.

Intune har stöd för övervakat läge som en del av Apples [program för enhetsregistrering (DEP)](../enrollment/device-enrollment-program-enroll-ios.md).

En lista över Apple-kontroller som kräver övervakning finns i Apples [referensdokument för nyttolastsinställningar](http://help.apple.com/configurator/mac/2.4/#/cad5370d089).

## <a name="turn-on-supervised-mode-during-enrollment"></a>Aktivera övervakat läge under registreringen

I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) kan du aktivera övervakat läge för enheter när du [skapar en Apple-registreringsprofil i DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Under **Inställningar för enhetshantering** markerar du rutan **Övervakad**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Aktivera övervakat läge efter registreringen

Efter registreringen går det endast att aktivera övervakat läge genom att ansluta en iOS/iPadOS-enhet till en Mac-dator och använda [Apple Configurator](../enrollment/apple-configurator-enroll-ios.md) (vilket återställer enheten). Du kan inte konfigurera en enhet för övervakat läge i Intune efter registreringen.

## <a name="identify-a-supervised-device"></a>Identifiera en övervakad enhet

Gå till låsskärmen eller sidan **Om** för att ta reda på om en enhet är övervakad:
- På enhetens låsskärm står det **This iPhone is managed by "Company Name"** (Denna iPhone hanteras av ”Företagsnamn”).
- På enhetens **Om**-sida står det **This iPhone is supervised (Denna iPhone är övervakad). Företagsnamnet kan övervaka din Internettrafik och hitta denna enhet.**

## <a name="next-steps"></a>Nästa steg

Mer information om alternativ för enhetshantering finns i [Vad är enhetshantering i Microsoft Intune?](device-management.md)
