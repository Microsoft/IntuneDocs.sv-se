---
title: Aktivera Mobile Threat Defense-anslutningsprogrammet i Microsoft Intune
titleSuffix: Microsoft Intune
description: Aktivera anslutningsprogrammet mellan MTD-partnern (Mobile Threat Defense) och Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dbb6a37e-ba47-4b69-922c-d25e66c279f6
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ab9fef5a577783ebbdd512de6d00ab98483e754c
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513362"
---
# <a name="enable-the-mobile-threat-defense-connector-in-intune"></a>Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Vid installationen av Mobile Threat Defense (MTD) konfigurerade du en princip för att klassificera hot i MTD-partnerkonsolen och du skapade efterlevnadsprincipen för enheter i Intune. Om du redan har konfigurerat Intune-anslutningen i MTD-partnerkonsolen, kan du nu aktivera MTD-anslutningen i Intune.

## <a name="to-enable-the-mtd-connector"></a>Så här aktiverar du MTD-anslutningen

1. Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter. När du har loggat in visas **Azure-instrumentpanelen**.

2. Välj **Alla tjänster** i den vänstra menyn på **Azure-instrumentpanelen** och skriv sedan **Intune** i textrutefiltret.

3. Välj **Intune**. **Intune-instrumentpanelen** öppnas.

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
> Du måste lägga till och tilldela MTD-apparna innan du skapar principregler för enhetsefterlevnad och villkorlig åtkomst. Det säkerställer att MTD-appen är redo och tillgänglig för slutanvändarna att installera innan de kan få åtkomst till e-post och andra företagsresurser.

> [!TIP]
> Du kan se **Anslutningsstatus** och tiden för **Senaste synkronisering** mellan Intune och MTD-partnern i fönstret Mobile Threat Defense.
