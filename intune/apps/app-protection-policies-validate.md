---
title: Verifiera inställningen av din appskyddsprincip
titleSuffix: Microsoft Intune
description: Läs om hur du testar att din appskyddsprincip har konfigurerats och fungerar som den ska i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fefc784151b70d85fa0fd49d942c608b64467ef9
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725549"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Så här verifierar du konfigurationen av din appskyddsprincip i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Verifiera att din appskyddsprincip är rätt konfigurerad och att den fungerar. Den här vägledningen gäller för appskyddsprinciper i Azure-portalen.

## <a name="checking-for-symptoms"></a>Söka efter problem
Det är inte troligt att användarna rapporterar dessa fel eftersom appskyddet är ett verktyg för att skydda data. Om det uppstår problem med konfigurationen av appskyddet får användarna obegränsad åtkomst, vilket de även skulle ha utan appskydd. Användarna märker därmed inte att något är fel. Därför rekommenderar vi att du verifierar din appskyddskonfiguration genom att testa appskyddsprinciperna hos en liten grupp användare som avsiktligt kan testa appskyddsbegränsningarna.

## <a name="what-to-check"></a>Vad som ska kontrolleras

Om testningen visar att appskyddsprincipen inte fungerar som förväntat, bör du kontrollera följande:

- Är användarna licensierade för appskydd?
- Är användarna licensierade för O365?
- Har varje användare rätt status för sina appskyddsappar? Apparna kan ha status **Incheckad** och **Inte incheckad**.

### <a name="user-app-protection-status"></a>Användarens appskyddstatus
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** >  **Appskyddsstatus** och sedan ikonen **Tilldelade användare**. 
4. Ta fram en lista över användare och grupper genom att välja **Välj användare** på sidan **Apprapportering**. 
5. Sök efter och välj en användare från listan. Välj sedan **Välj användare**. Högst upp i fönstret **Apprapportering** kan du se om användaren är licensierad för appskydd. Nedanför ser du också om användaren har någon licens för O365 och vilken appstatus användarens alla enheter har.

## <a name="what-to-do"></a>Vad bör jag göra
Åtgärder som kan vidtas baserat på användarens status:

- Om användaren inte är licensierad för appskydd, tilldelar du användaren en [Intune-licens](../fundamentals/licenses.md).
- Om användaren inte är licensierad för O365 skaffar du en [licens](../fundamentals/licenses.md) för användaren.
- Om användarens app har status **Inte incheckad**, kontrollerar du om [appskyddsprincipen](app-protection-policies-validate.md) för appen är korrekt konfigurerad.
- Kontrollera att dessa villkor tillämpas för alla användare som du vill att [appskyddsprinciperna](app-protection-policies-monitor.md) ska gälla för.

## <a name="see-also"></a>Se även

- [Vad är appskyddsprincip i Intune?](app-protection-policies.md)
- [Licenser där Intune ingår](../fundamentals/licenses.md)
- [Tilldela licenser till användare så att de kan registrera enheter i Intune](../fundamentals/licenses-assign.md)
- [Så här verifierar du konfigurationen av din appskyddsprincip](app-protection-policies-validate.md)
- [Så här övervakar du appskyddsprinciper](app-protection-policies-monitor.md)

