---
title: Aktivera Mobile Threat Defense-anslutningsprogrammet i Microsoft Intune
titleSuffix: Microsoft Intune
description: Aktivera anslutningsprogrammet mellan MTD-partnern (Mobile Threat Defense) och Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b8243ae4014660a76c6327afd9c970ce8a9eae58
ms.sourcegitcommit: 960ffb2214c35d75ad219fa2571a999529a0abd4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74478843"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune

Vid installationen av Mobile Threat Defense (MTD) konfigurerade du en princip för klassificering av hot i Mobile Threat Defense-partnerkonsolen, och du skapade enhetsefterlevnadsprincipen i Intune. Om du redan har konfigurerat Intune-anslutningen i MTD-partnerkonsolen, kan du nu aktivera MTD-anslutningen för MTD-partnerprogram.

> [!NOTE]
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

## <a name="classic-conditional-access-policies-for-mtd-apps"></a>Klassiska principer för villkorlig åtkomst för MTD-appar

När du När du integrerar ett nytt program för Skydd mot mobilhot (MTD) i Intune och aktiverar anslutningen till Intune, skapar Intune en klassisk princip för villkorlig åtkomst i Azure Active Directory. Alla MTD-appar som du integrerar, inklusive [Defender ATP](advanced-threat-protection.md) eller något annat [MTD-partnerprogram](mobile-threat-defense.md#mobile-threat-defense-partners), skapar en ny klassisk princip för villkorlig åtkomst. Dessa principer kan ignoreras, men de får inte redigeras, tas bort eller inaktiveras.

Om den klassiska principen tas bort måste du ta bort anslutningen till Intune som var ansvarig för skapandet och sedan konfigurera den igen. Den här processen återskapar den klassiska principen. Den har inte stöd för att migrera klassiska principer för MTD-appar till den nya principtypen för villkorlig åtkomst.

Klassiska principer för villkorlig åtkomst för MTD-appar:

- Används av Intune MTD för att kräva att enheter registreras i Azure AD så att de har ett enhets-ID innan de kommunicerar med MTD-partners. ID:t krävs så att enheterna kan rapportera deras status till Intune.

- Har ingen påverkan på andra molnappar eller resurser.

- Är skilda från principer för villkorlig åtkomst som du kan skapa för att hantera MTD.

- Samverkar inte som standard med andra principer för villkorlig åtkomst som du använder för utvärdering.

Du kan visa klassiska principer för villkorlig åtkomst genom att gå till **Azure Active Directory** > **Villkorlig åtkomst** > **Klassiska principer** i [Azure](https://portal.azure.com/#home).

## <a name="to-enable-the-mobile-threat-defense-connector"></a>Så här aktiverar du Mobile Threat Defense-anslutningsprogrammet

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Administration av klientorganisation** > **Anslutning och token** > **Mobile Threat Defense**.

3. Välj **Lägg till** i fönstret **Mobile Threat Defense**.

4. Välj din MTD-lösning i listrutan **Mobile Threat Defense-anslutning för konfigurationen**.

5. Aktivera växlingsalternativen enligt kraven i din organisation. Växlingsalternativen som visas varierar beroende på MTD-partnern.  Följande bild visar till exempel de alternativ som är tillgängliga för Symantec Endpoint Protection:

   ![MTD-konfiguration i Intune Azure-portalen](./media/mtd-connector-enable/enable-mtd-connector-1.png)

## <a name="mobile-threat-defense-toggle-options"></a>Växla alternativ för Mobile Threat Defense

Du kan bestämma vilka MTD-växlingsalternativ som behöver aktiveras enligt din organisations krav. Det är inte alla av nedanstående alternativ som stöds av alla Mobile Threat Defense-partners:

**MDM-inställningar för efterlevnadsprinciper**

- **Anslut Android-enheter med version _\<versioner som stöds>_ till _\<MTD- partnernamn>_** : När du aktiverar det här alternativet kan du låta Android 4.1+-enheter rapportera säkerhetsrisker till Intune.

- **Anslut iOS-enheter med version _\<versioner som stöds>_ till _\<MTD- partnernamn>_** : När du aktiverar det här alternativet kan du låta iOS 8.0+-enheter rapportera säkerhetsrisker till Intune.

- **Aktivera appsynkronisering för iOS-enheter**: Tillåter denna Mobile Threat Defense-partner att begära metadata för iOS-program från Intune för att använda för hotanalyssyften.

- **Blockera operativsystemversioner som inte stöds**: Blockera om enheten kör ett operativsystem som är äldre än den äldsta version som stöds.

**Inställningar för appskyddsprincip**

- **Anslut Android-enheter med version *\<versioner som stöds>* till *\<MTD-partnernamn>* för utvärdering av appskyddsprincipen**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.

- **Anslut iOS-enheter med version *\<versioner som stöds>* till *\<MTD-partnernamn>* för utvärdering av appskyddsprincipen**: När du aktiverar det här alternativet utvärderar appskyddsprinciper som använder regeln för hotnivå för enhet enheter, däribland data från det här anslutningsprogrammet.

Mer information om hur du använder Mobile Threat Defense-anslutningsprogram för att utvärdera Intune-appskyddsprincip hittar du i [Konfigurera Mobile Threat Defense för oregistrerade enheter](~/protect/mtd-enable-unenrolled-devices.md).

**Gemensamma delade inställningar**

- **Antalet dagar tills partnern är icke-kommunikativ**: Maximalt antal dagar av inaktivitet innan Intune betraktar partnern som icke-kommunikativ eftersom anslutningen har gått förlorad. Intune ignorerar efterlevnadsstatusen för MTD-partners som inte svarar.

> [!IMPORTANT]
> När det är möjligt rekommenderar vi att du lägger till och tilldelar MTD-apparna innan du skapar principreglerna för enhetsefterlevnad och villkorlig åtkomst. Det säkerställer att MTD-appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post och andra företagsresurser.

> [!TIP]
> Du kan se **Anslutningsstatus** och tiden för **Senaste synkronisering** mellan Intune och MTD-partnern i fönstret Mobile Threat Defense.

## <a name="next-steps"></a>Nästa steg

- [Skapa en Mobile Threat Defense-appskyddsprincip (MTD) med Intune](~/protect/mtd-app-protection-policy.md).
