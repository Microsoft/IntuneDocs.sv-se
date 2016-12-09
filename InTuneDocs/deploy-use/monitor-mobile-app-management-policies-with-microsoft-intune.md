---
title: "Övervaka MAM-principer med Microsoft Intune | Microsoft Intune"
description: "Se hur många användare som principen tillämpas på och öka detaljnivån om du vill ha mer information."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 487fe778bae73c2ac5564f90c21328932060f576


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Övervaka hanteringsprinciper för mobilappar med Microsoft Intune
När du har skapat en princip för hantering av mobila appar (MAM) och tillämpat den på användare kan du övervaka efterlevnadsstatusen på [Azure-portalen](https://portal.azure.com). Azure-portalen innehåller information om de användare som påverkas av principen, efterlevnadsstatus och eventuella problem som slutanvändarna kan råka ut för.
## <a name="summary-view"></a>Sammanfattningsvy
På bladet **Hantering av mobilprogram i Intune** visas en sammanfattning av efterlevnadsstatusen:


![Panelen Sammanfattning på bladet Hantering av mobilprogram i Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Användare:** Totalt antal användare på företaget som använder de appar som är associerade med principen.

-   **HANTERAS AV PRINCIP:** Antalet användare som har använt minst en av apparna i arbetskontexten.

-   **INGEN PRINCIP**: Antalet användare som använder de appar som är associerade med principen, men som inte omfattas av principen. Du kan välja att lägga till dessa användare i principen.

- **Flaggade användare**: Antalet användare som har problem. För närvarande rapporteras endast användare med upplåsta enheter under **Flaggade användare**.


## <a name="detailed-view"></a>Detaljerad vy
Du kommer till den detaljerade vyn av sammanfattningen genom att välja panelen **Användarstatus** och panelen **Flaggade användare**.

### <a name="user-status"></a>Användarstatus
Du kan söka efter en enskild användare och kontrollera efterlevnadsstatusen för användaren. På bladet **Apprapportering** visas följande information för en vald användare:
- Enheter som är associerade med användarkontot

- Appar med en MAM-princip på enheten

- Status:

  - **Incheckad**: Principen har distribuerats till användaren och appen användes i arbetskontexten minst en gång.

  - **Inte incheckad:** Principen har distribuerats till användaren, men appen har inte använts i arbetskontexten sedan dess.

>[!NOTE]
> Om MAM-principen inte har distribuerats till den användare som du sökte efter visas ett meddelande om att inga apprinciper tillämpas för användaren.

Visa rapporter för en användare genom att följa anvisningarna:

1.  Du väljer en användare genom att välja panelen **Sammanfattning** eller alternativet **APPRAPPORTERING AV ANVÄNDARE** på bladet **Inställningar**:

    ![Alternativet Apprapportering på bladet Inställningar](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. På bladet **Apprapportering** som öppnas väljer du **Välj användare** för att söka efter en Azure Active Directory-användare.

    ![Alternativet Välj användare på bladet Apprapportering](../media/mam-azure-portal-app-reporting-select-user.png)

3. Välj användaren i listan. Du kan se informationen om användarens kompatibilitetsstatus.

    ![Information om apprapportering](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>Flaggade användare
I den detaljerade vyn visas felmeddelandet, appen som användes när felet inträffade, plattformen för enheten och en tidsstämpel.  

### <a name="see-also"></a>Se även
[Hantera dataöverföring mellan iOS-appar](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Vad som händer när din Android-app hanteras med MAM-principer](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


