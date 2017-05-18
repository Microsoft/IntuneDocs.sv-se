---
title: "Scenarier för att skydda e-post | Microsoft Docs"
description: "Några exempelscenarier och hur de kan genomföras med villkorlig åtkomst."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 454eab79-b620-42c9-b8e6-fada6e719fcd
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 33febef8787887401960592d95356347f6917681
ms.openlocfilehash: 7d0b9cee72e8810b4f39bd81bd8f49d0818618c4
ms.contentlocale: sv-se
ms.lasthandoff: 05/04/2017


---

# <a name="protect-access-to-email-with-microsoft-intune-example-scenarios"></a>Skydda åtkomsten till e-post med Microsoft Intune: Exempelscenarier

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="scenario-1-block-users-from-using-noncompliant-devices-to-access-exchange-online"></a>Scenario 1: Förhindra att användare kommer åt Exchange Online från icke-kompatibla enheter
### <a name="scenario-requirements"></a>Krav för scenario
- Alla användare i Azure Active Directory-säkerhetsgruppen **Bokföring** måste hindras från att komma åt Exchange Online om deras enhet inte är kompatibel med en efterlevnadsprincip som du har distribuerat.
- Om det finns användare i den här gruppen vars enheter inte stöds av Intune måste de hindras från att komma åt Exchange Online på den enheten.
- Användare i Azure Active Directory-säkerhetsgruppen **Finans** måste undantas från principen, även om de även ingår i säkerhetsgruppen **Bokföring**.

För att åstadkomma detta konfigurerar du en princip för villkorlig åtkomst för Exchange Online med följande inställningar:

- Välj **Aktivera princip för villkorlig åtkomst**.

- Välj önskade plattformar för att tillåta åtkomst från appar med modern autentisering.
- För Exchange ActiveSync-appar väljer du **Blockera inkompatibla enheter på plattformar som stöds av Microsoft Intune** och **Blockera alla andra enheter på plattformar som inte stöds av Microsoft Intune.**
-   I **Målgrupp** väljer du användargruppen **Bokföring** under **Valda säkerhetsgrupper**.

-   I **Undantagna grupper** väljer du användargruppen **Finans** under **Valda säkerhetsgrupper**.


Följande flöde används i scenariot för att bestämma vilka enheter som kan komma åt Exchange Online:

![Åtkomstflöde för enheter](./media/ConditionalAccess8-5.png)

## <a name="scenario-2-all-ios-devices-that-access-exchange-on-premises-must-be-managed-by-intune"></a>Scenario 2: Alla iOS-enheter som har åtkomst till Exchange On-premises måste hanteras av Intune
### <a name="scenario-requirements"></a>Krav för scenario
- Endast enheter som kör iOS ska kunna komma åt Exchange On-premises.
- Enheterna måste dessutom vara registrerade i Intune och uppfylla reglerna för efterlevnadsprinciper innan de kan användas för att komma åt Exchange.

Du åstadkommer detta genom att konfigurera följande princip för villkorlig åtkomst för Exchange On-premises med följande inställningar:

-   Välj alternativet **Blockera e-postappar från att få åtkomst till Exchange On-premises om enheten inte är kompatibel med eller inte är registrerad på Microsoft Intune**. När du väljer det här alternativet aktiveras principen för villkorlig åtkomst, vilket innebär att alla enheter måste vara registrerade i Microsoft Intune och uppfylla reglerna för efterlevnadsprinciper för att kunna komma åt Exchange.

-   För avancerade Exchange Active Sync-inställningar skapar du:

  -   Ett plattformsundantag som gör att enheter som kör iOS får tillgång till Exchange.   

  -   En standardregel som anger att enheter som inte omfattas av regeln för plattformsundantag ska blockeras från åtkomst till Exchange. Den här regeln ser till att enheter som inte kör iOS inte kan komma åt Exchange.

Du använder följande flöde för att bestämma vilka enheter som kan få tillgång till Exchange:

![Åtkomstflöde för enheter](./media/ConditionalAccess8-3.png)

## <a name="scenario-3-no-android-devices-can-access-exchange-on-premises"></a>Scenario 3: Inga Android-enheter kan komma åt Exchange On-premises
### <a name="scenario-requirements"></a>Krav för scenario
- Alla Android-enheter ska blockeras från att komma åt Exchange.
- Alla andra enheter som stöds kan få åtkomst till Exchange under förutsättning att de hanteras av Intune.

Du åstadkommer detta genom att konfigurera en princip för villkorlig åtkomst för Exchange On-premises med följande inställningar:

-   Välj alternativet **Blockera e-postappar från att få åtkomst till Exchange On-premises om enheten inte är kompatibel med eller inte är registrerad på Microsoft Intune**. När du väljer det här alternativet måste alla enheter vara registrerade i Intune och uppfylla reglerna för efterlevnadsprinciper.

- För avancerade Exchange Active Sync-inställningar skapar du:
  -   Ett plattformsundantag som blockerar enheter som kör Android från tillgång till Exchange. Den här regeln kontrollerar att Android-enheter inte kan användas för att komma åt Exchange.

  -   En standardregel som anger att enheter som inte omfattas av andra regler ska beviljas åtkomst till Exchange. Den här standardregeln ser till att enheter som kör andra plattformar än Android, men som stöds av Microsoft Intune, kan användas för att få åtkomst till Exchange. De måste dock vara registrerade i Intune och uppfylla reglerna för efterlevnadsprinciper.

Du använder följande flöde för att bestämma vilka enheter som kan få tillgång till Exchange:

![Åtkomstflöde för enheter](./media/ConditionalAccess8-4.png)

