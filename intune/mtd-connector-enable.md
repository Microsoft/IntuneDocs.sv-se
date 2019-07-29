---
title: Aktivera Mobile Threat Defense-anslutningsprogrammet i Microsoft Intune
titleSuffix: Microsoft Intune
description: Aktivera anslutningsprogrammet mellan MTD-partnern (Mobile Threat Defense) och Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4dd77be45c21db53dd82322049d377ced247c4c7
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427348"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Vid installationen av Mobile Threat Defense (MTD) konfigurerade du en princip för att klassificera hot i MTD-partnerkonsolen och du skapade efterlevnadsprincipen för enheter i Intune. Om du redan har konfigurerat Intune-anslutningen i MTD-partnerkonsolen, kan du nu aktivera MTD-anslutningen för MTD-partnerprogram.

När du integrerar ett nytt program för Skydd mot mobilhot (MTD) i Intune och aktiverar anslutningen skapar Intune en klassisk princip för villkorlig åtkomst i Azure Active Directory. Alla MTD-appar som du integrerar, till exempel [Defender ATP](advanced-threat-protection.md) eller något annat [MTD-partnerprogram](mobile-threat-defense.md#mobile-threat-defense-partners), skapar en ny klassisk princip för villkorlig åtkomst.  Dessa principer kan ignoreras, men de bör inte redigeras, tas bort eller inaktiveras.

Klassiska principer för villkorlig åtkomst för MTD-appar: 

- Används av Intune MTD för att kräva att enheter registreras i Azure AD så att de har ett enhets-ID. ID:t krävs så att enheterna kan rapportera deras status till Intune.  
- Är skilda från principer för villkorlig åtkomst som du kan skapa för att hantera MTD.
- Samverkar inte som standard med andra principer för villkorlig åtkomst som du använder för utvärdering.  

Du kan visa klassiska principer för villkorlig åtkomst genom att gå till **Azure Active Directory** > **Villkorlig åtkomst** > **Klassiska principer** i [Azure](https://portal.azure.com/#home).


## <a name="to-enable-the-mtd-connector"></a>Så här aktiverar du MTD-anslutningen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

4. Välj **Enhetskompatibilitet** på **Intune-instrumentpanelen** och välj sedan **Mobile Threat Defense** i avsnittet **Konfiguration**.

5. Välj **Lägg till** i fönstret **Mobile Threat Defense**.

6. Välj den MTD-lösning du använder som **Mobile Threat Defense-anslutning för konfigurationen** i listrutan.

    ![MTD-konfiguration i Intune Azure-portalen](./media/enable-mtd-connector-1.png)

7. Aktivera växlingsalternativen enligt kraven i din organisation. Växlingsalternativen som visas varierar beroende på MTD-partnern.

## <a name="mtd-toggle-options"></a>MTD-växlingsalternativ

Du kan bestämma vilka MTD-växlingsalternativ som behöver aktiveras enligt din organisations krav. Här finns mer information:

- **Ansluta Android 4.1+-enheter till [MTD-partnernamn] för Work MTD**: När du aktiverar det här alternativet kan du låta Android 4.1+-enheter rapportera säkerhetsrisker till Intune.
  - **Markera som icke-kompatibel om inga data tas emot**: Om Intune inte har tagit emot data om en enhet på den här plattformen från MTD-partnern, så kan du betrakta enheten som inkompatibel.
<br></br>
- **Ansluta iOS 8.0+-enheter till [MTD-partnernamn] för Work MTD**: När du aktiverar det här alternativet kan du låta iOS 8.0+-enheter rapportera säkerhetsrisker till Intune.
  - **Markera som icke-kompatibel om inga data tas emot**: Om Intune inte har tagit emot data om en enhet på den här plattformen från MTD-partnern, så kan du betrakta enheten som inkompatibel.
<br></br>
- **Aktivera appsynkronisering för iOS-enheter**: Tillåter denna Mobile Threat Defense-partner att begära metadata för iOS-program från Intune för att använda för hotanalyssyften.

- **Blockera operativsystemversioner som inte stöds**: Blockera om enheten kör ett operativsystem som är äldre än den äldsta version som stöds.

- **Antalet dagar tills partnern är icke-kommunikativ**: Maximalt antal dagar av inaktivitet innan Intune betraktar partnern som icke-kommunikativ eftersom anslutningen har gått förlorad. Intune ignorerar efterlevnadsstatusen för MTD-partners som inte svarar.

> [!IMPORTANT] 
> När det är möjligt rekommenderar vi att du lägger till och tilldelar MTD-apparna innan du skapar principreglerna för enhetsefterlevnad och villkorlig åtkomst. Det säkerställer att MTD-appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post och andra företagsresurser.

> [!TIP]
> Du kan se **Anslutningsstatus** och tiden för **Senaste synkronisering** mellan Intune och MTD-partnern i fönstret Mobile Threat Defense.
