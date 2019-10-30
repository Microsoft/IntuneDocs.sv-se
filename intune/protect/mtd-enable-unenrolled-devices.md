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
ms.openlocfilehash: 63079757ee3610d825601921da1d33aa94f851b6
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794413"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune-for-unenrolled-devices"></a>Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune för oregistrerade enheter

Vid installationen av Mobile Threat Defense (MTD) konfigurerade du en princip för klassificering av hot i Mobile Threat Defense-partnerkonsolen, och du skapade appskyddsprincipen i Intune. Om du redan har konfigurerat Intune-anslutningen i MTD-partnerkonsolen, kan du nu aktivera MTD-anslutningen för MTD-partnerprogram.

> [!NOTE] 
> Den här artikeln gäller för alla Mobile Threat Defense-partner som har stöd för appskyddsprinciper: Better Mobile (Android), Zimperium (iOS) samt Lookout for Work (Android/iOS).

## <a name="to-enable-the-mtd-connector"></a>Så här aktiverar du MTD-anslutningen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

2. Välj **Enhetskompatibilitet** på **Intune-instrumentpanelen** och välj sedan **Mobile Threat Defense** i avsnittet **Konfiguration**.

3. Välj **Lägg till** i fönstret **Mobile Threat Defense**.

4. Välj den MTD-lösning du använder som **Mobile Threat Defense-anslutning för konfigurationen** i listrutan.

    <!-- ![MTD setup in Intune](PLACEHOLDER, need a new screenshot of this page) -->

5. Aktivera växlingsalternativen enligt kraven i din organisation. Växlingsalternativen som visas varierar beroende på MTD-partnern.

## <a name="mtd-toggle-options"></a>MTD-växlingsalternativ

Du kan bestämma vilka MTD-växlingsalternativ som behöver aktiveras enligt din organisations krav. Här finns mer information:

**Inställningar för appskyddsprincip**
- **Anslut Android-enheter med version 4.1 och senare till *\<MTD-partnernamn>* för utvärdering av appskyddsprincip**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.
- **Anslut iOS-enheter med version 8.0 och senare till *\<MTD-partnernamn>* för utvärdering av appskyddsprincip**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.

**Gemensamma delade inställningar**
- **Antalet dagar tills partnern är icke-kommunikativ**: Maximalt antal dagar av inaktivitet innan Intune betraktar partnern som icke-kommunikativ eftersom anslutningen har gått förlorad. Intune ignorerar efterlevnadsstatusen för MTD-partners som inte svarar.

> [!TIP]
> Du kan se **Anslutningsstatus** och tiden för **Senaste synkronisering** mellan Intune och MTD-partnern i fönstret Mobile Threat Defense.

> [!NOTE] 
> När du aktiverar Mobile Threat Defense-anslutningen till Intune skapar Intune en klassisk princip för villkorsstyrd åtkomst i Azure Active Directory. Alla MTD-appar som du integrerar, inklusive [Defender ATP](advanced-threat-protection.md) eller något annat [MTD-partnerprogram](mobile-threat-defense.md#mobile-threat-defense-partners), skapar en ny klassisk princip för villkorlig åtkomst. **Dessa principer kan ignoreras, men de bör inte redigeras, tas bort eller inaktiveras.**
> 
> Klassiska principer för villkorlig åtkomst för MTD-appar: 
> - Används av Intune MTD för att kräva att enheter registreras i Azure AD så att de har ett enhets-ID innan de kommunicerar med MTD-partners. ID:t krävs så att enheterna kan rapportera deras status till Intune.  
> - Har ingen påverkan på andra molnappar eller resurser.  
> - Är skilda från principer för villkorsstyrd åtkomst som du kan skapa för att hantera MTD eller för att kräv villkorsstyrd åtkomst med appskydd
> - Samverkar inte som standard med andra principer för villkorlig åtkomst som du använder för utvärdering.  
>
> Du kan visa klassiska principer för villkorlig åtkomst genom att gå till **Azure Active Directory** > **Villkorlig åtkomst** > **Klassiska principer** i [Azure](https://portal.azure.com/#home).

## <a name="next-steps"></a>Nästa steg

- [Skapa en Mobile Threat Defense-appskyddsprincip (MTD) med Intune](~/protect/mtd-app-protection-policy.md).