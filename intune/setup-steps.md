---
title: Konfigurera Intune
description: "Krav och förutsättningar för att börja använda din Intune-prenumeration"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 54f2bdd4a415cb8a4432a8bdcf93c56ba995c201
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2017
---
# <a name="set-up-intune"></a>Konfigurera Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

De här anvisningarna visar hur du aktiverar mobilenhetshantering (MDM). Enheterna måste vara hanterade innan du kan ge användarna åtkomst till företagsresurser eller hantera inställningar på enheterna.

Vissa anvisningar, till exempel konfigurering av en Intune-prenumeration och inställning av utfärdare för mobilenhetshantering krävs i de flesta scenarier. Andra åtgärder valfria, till exempel konfigurera en anpassad domän eller lägga till appar, beroende på företagets behov.

Om du använder Microsoft System Center Configuration Manager för att hantera datorer och servrar, kan du [utöka Configuration Manager till att hantera mobila enheter](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

>[!TIP]
>Om du köper minst 150 Intune-licenser inom ramen för en berättigad prenumeration kan du utnyttja *FastTrack Center-förmånen*. I den här tjänsten ingår hjälp från Microsoft-specialister med att förbereda din miljö för Intune. Mer information finns i [FastTrack Center-förmån för Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).



| Steg | Status  |
| ------------- |-------------|
| 1  | [Konfigurationer som stöds](supported-devices-browsers.md) – Viktig information innan du sätter igång. Här visas konfigurationer som stöds och krav på nätverk.|
| 2 |  [Logga in på Intune](account-sign-up.md) – Logga in på din utvärderingsprenumeration eller skapa en ny Intune-prenumeration. |  
| 3 | [Konfigurera domännamn](custom-domain-name-configure.md) – Ange DNS-registrering för att ansluta ditt företags domännamn till Intune. Användarna får en välbekant domän när de ansluter till Intune och använder resurserna.  |
| 4 | [Lägg till användare](users-add.md) – Lägg till användare manuellt eller anslut Active Directory om du vill synkronisera användare med Intune. Obligatoriskt såvida dina enheter inte är exempelvis användarlösa informationsdatorenheter. |
| 5 | [Tilldela licenser](licenses-assign.md) – Ge användarna behörighet att använda Intune. För varje användare eller användarlös enhet krävs en Intune-licens för att få åtkomst till tjänsten.|
| 6 |  [Lägg till grupper](groups-add.md) – Använd användar- och enhetsgrupper för att förenkla hanteringsuppgifter. Grupper används för att tilldela appar, inställningar och andra resurser. |
| 7 | [Lägg till appar](apps-add.md) – Appar kan tilldelas grupper och installeras automatiskt eller valfritt. |
| 8 | [Konfigurera enheter](device-profiles.md) – Ställ in profiler för hantering av enhetsinställningar. Inställningar för e-post, VPN, trådlösa anslutningar och enhetsfunktioner kan ställas in i förväg i enhetsprofiler. Profilerna kan även innehålla begränsningar för enheter för att skydda både enheter och data.  |
| 9 | [Anpassa företagsportalen](company-portal-app.md) – Anpassa den Intune-företagsportal där användarna registrerar enheter och installerar appar. Inställningarna visas både i företagsportalappen och på webbplatsen för Intune-företagsportal. |
| 10 | [Aktivera enhetsregistrering](mdm-authority-set.md) – Aktivera Intune-hantering av iOS-, Windows-, Android- och Mac-enheter genom att ange utfärdare för mobilenhetshantering och aktivera specifika plattformar. |
