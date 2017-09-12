---
title: Verifiera appskyddsprinciper
titleSuffix: Azure portal
description: "Det här ämnet beskriver hur du kan testa och validera om din appskyddsprincip är korrekt konfigurerad och fungerar som förväntat.”"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angerobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0c97fbbffa416dce6b9aa8f56ecda7c265f377db
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Hur du validerar inställningen av din appskyddsprincip

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Det här avsnittet innehåller information om hur du felsöker problem när du har konfigurerat en appskyddsprincip. Den här vägledningen gäller för appskyddsprinciper i Azure-portalen.

### <a name="checking-for-symptoms"></a>Söka efter problem
Det är inte troligt att användarna rapporterar dessa fel eftersom appskyddet är ett verktyg för att skydda data. Om det finns ett problem med konfigureringen av appskyddet har användaren obegränsad åtkomst, vilket användaren även skulle ha utan appskydd, och användaren är inte medveten om felet. Därför rekommenderar vi att du verifierar din appskyddskonfiguration genom att testa appskyddsprinciperna med en liten grupp användare som avsiktligt kan testa appskyddsbegränsningarna.


### <a name="what-to-check"></a>Vad som ska kontrolleras

Om testningen visar att appskyddsprincipen inte fungerar som förväntat rekommenderar vi att du kontrollerar följande:

- Är användarna licensierade för appskydd?
- Är användarna licensierade för O365?
- Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**.

#### <a name="user-app-protection-status"></a>Användarens appskyddstatus
1. I Azure-portalen väljer du **Hantera appar** > **Övervaka** >  **Appskyddets användarstatus** > **användare**.

2. Välj en användare i listan (eller sök efter och välj en användare) och välj sedan **Välj användare**. Längst upp i kolumnen **Apprapportering** kan du se om användaren är licensierad för appskydd. Nedanför det kan du se om användaren är licensierad för O365 och appstatus för alla användarens enheter.



### <a name="what-to-do"></a>Vad bör jag göra
Åtgärder som kan vidtas baserat på användarens status:

- Om användaren inte är licensierad för appskydd tilldelar du användaren en Intune-licens.
- Om användaren inte är licensierad för O365 skaffar du en licens för användaren.
- Om en användares app har status **Inte incheckad** kontrollerar du om appskyddsprincipen för appen är korrekt konfigurerad.
- Se till att dessa villkor används för alla användare som du vill att appskyddsprinciperna ska gälla för.

### <a name="see-also"></a>Se även

[Vad är appskyddsprincip i Intune?](app-protection-policies.md)
