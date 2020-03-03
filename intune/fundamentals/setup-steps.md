---
title: Konfigurera Microsoft Intune
description: Krav och förutsättningar för att börja använda din Intune-prenumeration
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b12781c55abc3ce7d9e964b0f139fc4c1d1fd69b
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529370"
---
# <a name="set-up-intune"></a>Konfigurera Intune

De här anvisningarna visar hur du aktiverar mobilenhetshantering (MDM) med hjälp av Intune. Enheterna måste vara hanterade innan du kan ge användarna åtkomst till företagsresurser eller hantera inställningar på enheterna.

Vissa anvisningar, till exempel konfigurering av en Intune-prenumeration och inställning av utfärdare för mobilenhetshantering krävs i de flesta scenarier. Andra åtgärder valfria, till exempel konfigurera en anpassad domän eller lägga till appar, beroende på företagets behov.

Om du använder MicrosoftEndpoint Configuration Manager för att hantera datorer och servrar, kan du [fästa Configuration Manager i molnet med samhantering](https://docs.microsoft.com/configmgr/comanage/overview).

>[!TIP]
>Om du köper minst 150 Intune-licenser inom ramen för en berättigad prenumeration kan du utnyttja *FastTrack Center-förmånen*. I den här tjänsten ingår hjälp från Microsoft-specialister med att förbereda din miljö för Intune. Mer information finns i [FastTrack Center-förmån för Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).

| Steg | Status  |
|---|---|
|   1   | [Konfigurationer som stöds](supported-devices-browsers.md) – Viktig information innan du sätter igång. Här visas konfigurationer som stöds och krav på nätverk.|
|   2   |  [Logga in på Intune](account-sign-up.md) – Logga in på din utvärderingsprenumeration eller skapa en ny Intune-prenumeration. |
|   3   | [Konfigurera domännamn](custom-domain-name-configure.md) – Ange DNS-registrering för att ansluta ditt företags domännamn till Intune. Användarna får en välbekant domän när de ansluter till Intune och använder resurserna. |
|   4   | [Lägga till användare](users-add.md) och [grupper](../groups-add.md) – Lägg till användare och grupper, eller anslut Active Directory om du vill synkronisera med Intune. Obligatoriskt såvida dina enheter inte är exempelvis användarlösa informationsdatorenheter. Grupper används för att tilldela appar, inställningar och andra resurser.|
|   5   | [Tilldela licenser](../licenses-assign.md) – Ge användarna behörighet att använda Intune. För varje användare eller användarlös enhet krävs en Intune-licens för att få åtkomst till tjänsten. |
|   6   | [Ange utfärdare av mobilenhetshantering](../mdm-authority-set.md) – Använd användar- och enhetsgrupper för att förenkla hanteringsuppgifter. Grupper används för att tilldela appar, inställningar och andra resurser. |
|   7   | [Lägg till appar](../apps/apps-add.md) – Appar kan tilldelas grupper och installeras automatiskt eller valfritt. |
|   8   | [Konfigurera enheter](../configuration/device-profiles.md) – Ställ in profiler för hantering av enhetsinställningar. Inställningar för e-post, VPN, trådlösa anslutningar och enhetsfunktioner kan ställas in i förväg i enhetsprofiler. Profilerna kan även innehålla begränsningar för enheter för att skydda både enheter och data. |
|   9   |  [Anpassa företagsportalen](../apps/company-portal-app.md) – Anpassa den Intune-företagsportal där användarna registrerar enheter och installerar appar. Inställningarna visas både i företagsportalappen och på webbplatsen för Intune-företagsportal.       |
|  10   | [Aktivera enhetsregistrering](mdm-authority-set.md) – Aktivera Intune-hantering av iOS/iPadOS-, Windows-, Android- och Mac-enheter genom att ange utfärdare för mobilenhetshantering och aktivera specifika plattformar. |
|  11   |  [Konfigurera apprinciper](../apps/app-protection-policy.md) – Ange specifika inställningar baserat på principer för appskydd i Microsoft Intune. |
