---
title: "Övervaka kompatibilitet för villkorlig åtkomst för Exchange lokalt och Exchange Online"
titleSuffix: Intune Azure preview
description: "Övervaka kompatibilitet för villkorlig åtkomst för Exchange lokalt och Exchange Online via Intune Azure Portal"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5712682d-285b-43fd-9978-3dcfd95ec5f9
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: d170958bbdc00423081aa606c9c7f4e7a8ec4b06
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="monitor-conditional-access-compliance-for-on-premises-exchange-and-exchange-online-in-intune-azure-preview"></a>Övervaka kompatibilitet för villkorlig åtkomst för Exchange lokalt och Exchange Online i förhandsversionen av Intune Azure

Från och med version 1704 av Intune kan administratörer se den rapportinformation som relaterar till Exchange ActiveSync-enhetsposter som har synkroniserats med Intune via Exchange Connector lokalt eller Intune Service to Service Connector (Exchange Online Connector). Efterlevnadsrapporteringen för villkorlig åtkomst innehåller en översikt över enheter med olika synkroniseringstillstånd:

-   **Tillåt**

-   **Blockera**

-   **Karantän**

## <a name="to-monitor-conditional-access-compliance"></a>Övervaka kompatibilitet för villkorlig åtkomst

1.  Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2.  När du har loggat in visas **Azure-instrumentpanelen**.

3.  Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

4.  Välj **Intune**. **Intune-instrumentpanelen** visas.

5.  Välj först **Villkorlig åtkomst** och sedan **Översikt**.

6.  Visa efterlevnadsrapportering för villkorlig åtkomst genom att välja något av de tre områdena (**Blockerad**, **Karantän** eller **Tillåten**) i diagrammet.

    ![Instrumentpanel för villkorlig åtkomst](./media/CA-reporting-intune-1.png)

När du har valt ett av tre områden kan du se mer information om vilka enheter som tillåts, blockeras eller har satts i karantän.

Du kan även öka detaljnivån för enskilda enheter om du vill se mer information om dem. Den enhet som valts på bilden nedan är t.ex. blockerad. I Intune kan du välja att ta bort företagsdata från bladet för efterlevnadsrapportering för villkorlig åtkomst.

![Detaljerad rapportering om villkorlig åtkomst för enhet](./media/CA-reporting-intune-3.png)

På bladet med enhetsinformation visas mer information:

-   **Översikt:** Här ser du följande enhetsegenskaper: OS-version, enhetsmodell, ägarskap, serienummer, tillverkare, telefonnummer och senaste tillfället då enheten checkades in.

-   **Egenskaper:** Här kan du ange enhetens ägarskap (privat eller företag).

-   **Maskinvara:** Här tillhandahålls den information som visas i översikten, liksom lagringsinformation (totalt utrymme och ledigt utrymme), systemomslutning, nätverksinformation, nätverkstjänst och mer information om villkorlig åtkomstblockering.

-   **Identifierade appar:** Här visas alla program som har installerats på enheten. Du kan också exportera listan över installerade appar i .CSV-format.

-   **Kompatibilitet:** Här visas all information om enhetens efterlevnadsprincip.

-   **Enhetskonfiguration:** Här visas all information om enhetens konfiguration.

-   **Exchange-åtkomst:** Här kan du läsa mer om enhetens tillstånd efter det att principerna för villkorlig åtkomst har tillämpats.

