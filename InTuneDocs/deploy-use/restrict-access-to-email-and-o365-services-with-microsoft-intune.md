---
title: "Begränsa åtkomst till e-post och Office 365-tjänster | Microsoft Intune"
description: "I det här avsnittet beskrivs hur du kan använda villkorlig åtkomst för att endast tillåta att kompatibla enheter får åtkomst till e-post och företagsdata i SharePoint Online och andra tjänster."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 3a58e075813fac6a37ec8f82a39e44a856ef1cce


---

# <a name="restrict-access-to-email-office-365-and-other-services-with-microsoft-intune"></a>Begränsa åtkomsten till e-post, Office 365 och andra tjänster med Microsoft Intune
Du kan begränsa åtkomsten till företagsrelaterad e-post, Office 365 och andra tjänster med hjälp av Intunes funktion för villkorlig åtkomst. Med Intunes funktioner för villkorlig åtkomst kan du se till att åtkomsten till företagsrelaterad e-post och Office 365-tjänster är begränsad till enheter som är kompatibla med de regler som du anger.
## <a name="how-does-conditional-access-work"></a>Hur fungerar villkorlig åtkomst?
Du kan utvärdera enhetens kompatibilitet med hjälp av inställningarna för efterlevnadsprinciper. En princip för villkorlig åtkomst använder utvärderingen för att begränsa eller tillåta åtkomst till en specifik tjänst. När du använder en princip för villkorlig åtkomst i kombination med en efterlevnadsprincip kommer endast kompatibla enheter åt tjänsten. Principen för efterlevnad och principen för villkorlig åtkomst distribueras till användaren. Alla enheter som användaren använder för att komma åt tjänsterna kontrolleras för att se att de följer principerna.

Tänk på att en efterlevnadsprincip måste distribueras till enhetsanvändaren för att enhetens efterlevnad ska kunna utvärderas.
Om ingen efterlevnadsprincip har distribuerats till användaren behandlas enheten som kompatibel och inga åtkomstbegränsningar tillämpas.

Om en enhet inte uppfyller de villkor som du har definierat i principerna vägleds användaren genom en process för att registrera enheten och åtgärda problemet som gör att enheten inte är kompatibel.

Så här ser ett typiskt flöde för villkorlig åtkomst ut:

![Ett diagram som visar de beslutspunkter som används för att avgöra om en enhet ska beviljas åtkomst till en tjänst eller om den ska blockeras](../media/ConditionalAccess4.png)

## <a name="how-to-configure-conditional-access"></a>Konfigurera villkorlig åtkomst
Använd villkorlig åtkomst om du vill hantera åtkomsten till Microsoft **Exchange On-premises**, **Exchange Online**, **Exchange Online Dedicated**, **SharePoint Online** och **Skype för företag – Online**.

Du konfigurerar villkorlig åtkomst genom att konfigurera en efterlevnadsprincip för enheter och en princip för villkorlig åtkomst.

Efterlevnadsprincipen omfattar inställningar som lösenord och kryptering samt huruvida en enheten är jailbrokad. Enheten måste uppfylla dessa regler för att anses vara kompatibel.

Du kan ange en princip för villkorlig åtkomst för att begränsa åtkomst baserat på:
- Enhetens efterlevnadsstatus.
- Den plattform som körs på enheten.
- Den typ av appar som används för att få åtkomst till tjänsterna.

Till skillnad från andra Intune-principer kan principer för villkorlig åtkomst inte distribueras. När du har konfigurerat principen och valt de användare som den ska gälla för, tillämpas principen i stället på alla målanvändare. När en användare är angiven som mål för en princip, måste varje enhet hen använder vara godkänd för att få åtkomst till resurserna.


## <a name="next-steps"></a>Nästa steg
1. [Läs mer om principen för enhetsefterlevnad och hur den fungerar](introduction-to-device-compliance-policies-in-microsoft-intune.md).

2. [Skapa en efterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md).

2.  Skapa en princip för villkorlig åtkomst för något av följande:
> [!div class="op_single_selector"]
  - [Skapa en princip för villkorlig åtkomst för Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Exchange On-premises](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för nya Exchange Online Dedicated](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för gamla Exchange Online Dedicated](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Nov16_HO4-->


