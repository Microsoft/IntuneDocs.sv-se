---
title: Verifiera inställningen av din appskyddsprincip
titleSuffix: Microsoft Intune
description: Läs hur du testar att din appskyddsprincip har konfigurerats och fungerar som den ska.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6ea79a2e177b8a4e85454140c7efb9172defe5b6
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Hur du validerar inställningen av din appskyddsprincip

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verifiera att din appskyddsprincip är rätt konfigurerad och att den fungerar. Den här vägledningen gäller för appskyddsprinciper i Azure-portalen.

### <a name="checking-for-symptoms"></a>Söka efter problem
Det är inte troligt att användarna rapporterar dessa fel eftersom appskyddet är ett verktyg för att skydda data. Om det uppstår problem med konfigureringen av appskyddet får användaren obegränsad åtkomst, vilket användaren även skulle ha utan appskydd. Användaren är inte medveten om att det är något fel. Därför rekommenderar vi att du verifierar din appskyddskonfiguration genom att testa appskyddsprinciperna hos en liten grupp användare som avsiktligt kan testa appskyddsbegränsningarna.


### <a name="what-to-check"></a>Vad som ska kontrolleras

Om testningen visar att appskyddsprincipen inte fungerar som förväntat, rekommenderar vi att du kontrollerar följande:

- Är användarna licensierade för appskydd?
- Är användarna licensierade för O365?
- Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**.

#### <a name="user-app-protection-status"></a>Användarens appskyddstatus
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
1. Välj **Hantera appar** > **Övervakare** >  **Appskyddsstatus** > **Tilldelade användare**.

2. Välj en användare i listan (eller sök efter och välj en användare). Välj sedan **Välj användare**. Längst upp i kolumnen **Apprapportering** kan du se om användaren är licensierad för appskydd. Nedanför ser du också om användaren är licensierad för O365 och appstatus för alla användarens enheter.



### <a name="what-to-do"></a>Vad bör jag göra
Åtgärder som kan vidtas baserat på användarens status:

- Om användaren inte är licensierad för appskydd tilldelar du användaren en Intune-licens.
- Om användaren inte är licensierad för O365 skaffar du en licens för användaren.
- Om en användares app har status **Inte incheckad** kontrollerar du om appskyddsprincipen för appen är korrekt konfigurerad.
- Se till att dessa villkor används för alla användare som du vill att appskyddsprinciperna ska gälla för.

### <a name="see-also"></a>Se även

[Vad är appskyddsprincip i Intune?](app-protection-policies.md)
