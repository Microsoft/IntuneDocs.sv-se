---
title: Förhindra dataläckage på ej hanterade enheter
titleSuffix: Microsoft Intune
description: Tillåt åtkomst till företagsdata på enheter och skydda data från dataläckage med Microsoft Intune.
keywords: data protection prevent leaks device O365 Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21aac8bc4f241d2905bd2ba24ecdb8bbda3d1a67
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512275"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Förhindra dataläckage på ohanterade enheter med Microsoft Intune

Om du tillåter åtkomst till företagsdata som tillhandahålls genom Office 365 kan du styra hur användare delar och sparar data utan att riskera avsiktliga och oavsiktliga dataläckage. Microsoft Intune tillhandahåller appskyddsprinciper som du anger för att skydda företagsdata på enheter som ägs av användare. Enheterna behöver inte registreras i Intune-tjänsten. 

Appskyddsprinciper som konfigureras med Intune fungerar även på enheter som hanteras med en hanteringslösning för enheter som inte kommer från Microsoft. Personliga data på enheterna berörs inte, endast företagsdata hanteras av IT-avdelningen. 

Du kan ange appskyddsprinciper för Office-mobilappar på enheter som kör Windows, iOS eller Android för att skydda företagsdata. Med de här principerna kan du ange principer som appbaserad PIN-kod eller kryptering av företagsdata, eller mer avancerade inställningar som begränsar hur funktioner för att klippa ut, kopiera, klistra in och spara som används av användarna mellan hanterade och ej hanterade appar. Du kan även fjärrensa företagsdata utan att kräva att användarna registrerar enheter. 

Intunes appskyddsprinciper fungerar oberoende av enhetshantering. Appskyddsprinciper gör det möjligt att hantera Office-mobilappar på både ej hanterade enheter och Intune-hanterade enheter, samt enheter som hanteras av lösningar som inte kommer från Microsoft MDM. 

## <a name="before-you-begin"></a>Innan du börjar

Följande åtgärdsplan kan användas om du uppfyller följande krav:
* Företaget är redo för en säker övergång till molnet.
* Företaget använder Office 365 Exchange Online, SharePoint Online, OneDrive för företag eller Yammer.
* Företaget har licenser för Microsoft 365, Enterprise Mobility + Security (EMS) eller Azure Information Protection.
* Företaget tillåter att användarna får åtkomst till företagsdata från företagsägda eller personligt ägda Windows-, iOS- eller Android-enheter. 
* Företaget vill inte kräva registrering av personligt ägda enheter i en enhetshanteringstjänst. 

## <a name="action-plan"></a>Åtgärdsplan

För iOS- och Android-enheter: 

1. Lär dig hur [appskyddsprinciper](app-protection-policy.md) fungerar.
2. Lär dig att [skapa och distribuera appskyddsprinciper](app-protection-policies.md) för Office-mobilappar. 
3. [Övervaka appskyddsprinciperna](app-protection-policies-monitor.md) som du skapar och distribuerar. 

För Windows 10-enheter: 

1. Lär dig [hur Windows Information Protection (WIP) fungerar](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip). 
2. Förbered konfigurationen av [appskyddsprinciper för Windows 10](app-protection-policies-configure-windows-10.md).
3. [Skapa och distribuera WIP-appskyddsprinciper med Intune](windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>Information till anställda och studenter

Dela följande länkar för att tillhandahålla ytterligare information, efter behov: 
* [Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)
* [Vad som händer när din Android-app hanteras av appskyddsprinciper](app-protection-enabled-apps-android.md) 

## <a name="next-steps"></a>Nästa steg

Behöver du hjälp med att aktivera det här eller andra scenarier för EMS eller Office 365? Om du har minst 150 licenser för Microsoft 365, Enterprise Mobility + Security eller Azure Active Directory Premium kan du använda dina [FastTrack-förmåner](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
