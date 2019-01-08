---
title: Verifiera inställningen av din appskyddsprincip
titleSuffix: Microsoft Intune
description: Läs hur du testar att din appskyddsprincip har konfigurerats och fungerar som den ska.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2018
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0201f9a33fcdf3e7f5780f8e65a3666e6eb5d7d1
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816964"
---
# <a name="how-to-validate-your-app-protection-policy-setup"></a>Hur du validerar inställningen av din appskyddsprincip

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Verifiera att din appskyddsprincip är rätt konfigurerad och att den fungerar. Den här vägledningen gäller för appskyddsprinciper i Azure-portalen.

## <a name="checking-for-symptoms"></a>Söka efter problem
Det är inte troligt att användarna rapporterar dessa fel eftersom appskyddet är ett verktyg för att skydda data. Om det uppstår problem med konfiguren av appskyddet får användaren obegränsad åtkomst, vilket hen även skulle ha utan appskydd. Användaren kan därför inte vara medveten om att något är fel. Därför rekommenderar vi att du verifierar din appskyddskonfiguration genom att testa appskyddsprinciperna hos en liten grupp användare som avsiktligt kan testa appskyddsbegränsningarna.


## <a name="what-to-check"></a>Vad som ska kontrolleras

Om testningen visar att appskyddsprincipen inte fungerar som förväntat bör du kontrollera följande:

- Är användarna licensierade för appskydd?
- Är användarna licensierade för O365?
- Status för användarnas appskydds-appar. Apparna kan ha status **Incheckad** och **Inte incheckad**.

### <a name="user-app-protection-status"></a>Användarens appskyddstatus
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** > **Övervakare** >  **Appskyddsstatus**, och välj sedan panelen **Tilldelade användare**. 
4. Ta fram en lista över användare och grupper genom att välja **Välj användare** på sidan **Apprapportering**. 
5. Sök efter och välj en användare från listan. Välj sedan **Välj användare**. Högst upp i fönstret **Apprapportering** kan du se om användaren är licensierad för appskydd. Nedanför ser du också om användaren har någon licens för O365 och vilken appstatus användarens alla enheter har.



## <a name="what-to-do"></a>Vad bör jag göra
Åtgärder som kan vidtas baserat på användarens status:

- Om användaren inte är licensierad för appskydd tilldelar du användaren en Intune-licens.
- Om användaren inte är licensierad för O365 skaffar du en licens för användaren.
- Om en användares app har status **Inte incheckad** kontrollerar du om appskyddsprincipen för appen är korrekt konfigurerad.
- Se till att dessa villkor används för alla användare som du vill att appskyddsprinciperna ska gälla för.

## <a name="see-also"></a>Se även

[Vad är appskyddsprincip i Intune?](app-protection-policies.md)
