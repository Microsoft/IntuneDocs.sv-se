---
title: Aktivera Mobile Threat Defense-anslutningsprogrammet för oregistrerade enheter
titleSuffix: Microsoft Intune
description: Aktivera Mobile Threat Defense-anslutningsprogrammet i Microsoft Intune för oregistrerade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9571f7d0ae10f33007d5ae50b403580232c2e870
ms.sourcegitcommit: 06dce5c8111592ad774247e86e539dd3128117e5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/30/2019
ms.locfileid: "75545946"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune för oregistrerade enheter

Vid installationen av Mobile Threat Defense (MTD) konfigurerade du en princip för klassificering av hot i Mobile Threat Defense-partnerkonsolen, och du skapade appskyddsprincipen i Intune. Om du redan har konfigurerat Intune-anslutningen i MTD-partnerkonsolen, kan du nu aktivera MTD-anslutningen för MTD-partnerprogram.

> [!NOTE]
> Den här artikeln gäller för alla Mobile Threat Defense-partner som har stöd för appskyddsprinciper: Better Mobile (Android), Zimperium (Android/iOS) samt Lookout for Work (Android/iOS).

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Klassiska principer för villkorlig åtkomst för MTD-appar

När du När du integrerar ett nytt program för Skydd mot mobilhot (MTD) i Intune och aktiverar anslutningen till Intune, skapar Intune en klassisk princip för villkorlig åtkomst i Azure Active Directory. Alla MTD-appar som du integrerar, inklusive [Defender ATP](advanced-threat-protection.md) eller något annat [MTD-partnerprogram](mobile-threat-defense.md#mobile-threat-defense-partners), skapar en ny klassisk princip för villkorlig åtkomst. Dessa principer kan ignoreras, men de får inte redigeras, tas bort eller inaktiveras.

Om den klassiska principen tas bort måste du ta bort anslutningen till Intune som var ansvarig för skapandet och sedan konfigurera den igen. Den här processen återskapar den klassiska principen. Den saknar stöd för att migrera klassiska principer för MTD-appar till den nya principtypen för villkorlig åtkomst.

Klassiska principer för villkorlig åtkomst för MTD-appar:

- Används av Intune MTD för att kräva att enheter registreras i Azure AD så att de har ett enhets-ID innan de kommunicerar med MTD-partners. ID:t krävs så att enheterna kan rapportera deras status till Intune.

- Har ingen påverkan på andra molnappar eller resurser.

- Är skilda från principer för villkorlig åtkomst som du kan skapa för att hantera MTD.

- Samverkar inte som standard med andra principer för villkorlig åtkomst som du använder för utvärdering.

Du kan visa klassiska principer för villkorlig åtkomst genom att gå till **Azure Active Directory** > **Villkorlig åtkomst** > **Klassiska principer** i [Azure](https://portal.azure.com/#home).

## <a name="to-enable-the-mtd-connector"></a>Så här aktiverar du MTD-anslutningen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Mobile Threat Defense**.

3. Välj **Lägg till** i fönstret **Mobile Threat Defense**.

4. Välj den MTD-lösning du använder som **Mobile Threat Defense-anslutning för konfigurationen** i listrutan.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Aktivera växlingsalternativen enligt kraven i din organisation. Växlingsalternativen som visas varierar beroende på MTD-partnern.

## <a name="mobile-threat-defense-toggle-options"></a>Växla alternativ för Mobile Threat Defense

Du kan bestämma vilka MTD-växlingsalternativ som behöver aktiveras enligt din organisations krav. Här finns mer information:

**Inställningar för appskyddsprincip**

- **Anslut Android-enheter med version 4.4 och senare till *\<MTD-partnernamn>* för utvärdering av appskyddsprincip**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.

- **Anslut iOS-enheter med version 11 och senare till *\<MTD-partnernamn>* för utvärdering av appskyddsprincip**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.

**Gemensamma delade inställningar**

- **Antalet dagar tills partnern är icke-kommunikativ**: Maximalt antal dagar av inaktivitet innan Intune betraktar partnern som icke-kommunikativ eftersom anslutningen har gått förlorad. Intune ignorerar efterlevnadsstatusen för MTD-partners som inte svarar.

> [!TIP]
> Du kan se **Anslutningsstatus** och tiden för **Senaste synkronisering** mellan Intune och MTD-partnern i fönstret Mobile Threat Defense.

## <a name="next-steps"></a>Nästa steg

- [Skapa en Mobile Threat Defense-appskyddsprincip (MTD) med Intune](~/protect/mtd-app-protection-policy.md).
