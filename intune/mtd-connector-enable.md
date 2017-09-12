---
title: Aktivera Mobile Threat Defense-anslutningen med Intune
titlesuffix: Azure portal
description: Aktivera Mobile Threat Defense-anslutningen i Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ed7ac5467fe3a37a133aac61a9ccffe2e6119e6
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="enable-mobile-threat-defense-in-intune"></a>Aktivera Mobile Threat Defense i Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Om du vill aktivera Mobile Threat Defense-anslutningen i Intune bör du redan ha konfigurerat Intune-anslutningen i konsolen för MTD-lösningen.

## <a name="to-enable-the-mtd-connector"></a>Så här aktiverar du MTD-anslutningen

1. Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter. När du har loggat in visas **Azure-instrumentpanelen**.

2. Välj **Fler tjänster** på den vänstra menyn på **Azure-instrumentpanelen** och skriv sedan **Intune** i textrutefiltret.

3. Välj **Intune**. **Intune-instrumentpanelen** öppnas.

4. Välj **Enhetskompatibilitet** på **Intune-instrumentpanelen** och välj sedan **Mobile Threat Defense** i avsnittet **Konfiguration**.

5. Välj **Lägg till** på bladet **Mobile Threat Defense**.

6. Välj den MTD-lösning du använder som **Mobile Threat Defense-anslutning för konfigurationen** i listrutan.

    ![MTD-konfiguration i Intune Azure-portalen](./media/enable-mtd-connector-1.png)

7. Aktivera växlingsalternativen enligt kraven i din organisation.

## <a name="mtd-toggle-options"></a>MTD-växlingsalternativ

Du kan bestämma vilka MTD-växlingsalternativ som behöver aktiveras enligt din organisations krav. Här följer mer information:

- **Ansluta Android 4.1 + enheter till [MTD-partnernamn] för Work MTD**: När du aktiverar det här alternativet kan du låta Android 4.1 + enheter rapportera säkerhetsrisker till Intune.
    - **Markera som icke-kompatibel om inga data tas emot**: Om Intune inte har tagit emot data om en enhet på den här plattformen från MTD-partnern, så kan du betrakta enheten som inkompatibel.
<br></br>
- **Ansluta iOS 8.0-enheter eller senare till [MTD-partnernamn] för Work MTD**: När du aktiverar det här alternativet kan du låta Android 4.1 + enheter rapportera säkerhetsrisker till Intune.
    - **Markera som icke-kompatibel om inga data tas emot**: Om Intune inte har tagit emot data om en enhet på den här plattformen från MTD-partnern, så kan du betrakta enheten som inkompatibel.
<br></br>
- **Blockera operativsystemversioner som inte stöds**: Blockera om enheten kör ett operativsystem är äldre än den äldsta version som stöds.

- **Antalet dagar tills partnern inte svarar**: Maximalt antal dagar av inaktivitet innan Intune betraktar partnern som icke-kommunikativ eftersom anslutningen har gått förlorad. Intune ignorerar efterlevnadsstatusen för MTD-partners som inte svarar.

> [!IMPORTANT] 
> Du måste lägga till och tilldela MTD-apparna innan du skapar principregler för enhetsefterlevnad och villkorlig åtkomst. Det säkerställer att MTD-appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post och andra företagsresurser.

> [!TIP]
> Du kan se **anslutningsstatusen** och tiden för **senaste synkronisering** mellan Intune och MTD-partnern på bladet Mobile Threat Defense.

## <a name="next-steps"></a>Nästa steg

[Skapa en princip för Mobile Threat Defense-enhetsefterlevnad med Intune](mtd-device-compliance-policy-create.md)
