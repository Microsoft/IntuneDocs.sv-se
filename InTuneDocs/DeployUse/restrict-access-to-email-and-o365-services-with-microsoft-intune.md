---
title: "Begränsa åtkomsten till e-post och O365-tjänster | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c564d292-b83b-440d-bf08-3f5b299b7a5e
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: f770bdc312879d1c833e8861494ecd2204ea603a
ms.openlocfilehash: ebce26b0e09bb5282475cb1a39c8070a5d5b44aa


---

# Begränsa åtkomsten till e-post, O365 och andra tjänster med Microsoft Intune
Du kan begränsa åtkomsten till företagsrelaterad e-post och O365-tjänster med villkorlig åtkomst i Intune. Med Intunes funktioner för villkorlig åtkomst kan du se till att åtkomsten till företagsrelaterad e-post och O365-tjänster är begränsad till enheter som är kompatibla med de regler som du anger.
## Hur fungerar villkorlig åtkomst?
Inställningar för efterlevnadsprinciper används för att utvärdera enhetens kompatibilitet. Principen för villkorlig åtkomst använder utvärderingen för att begränsa eller tillåta åtkomst till en specifik tjänst. När en princip för villkorlig åtkomst används i kombination med en efterlevnadsprincip kommer endast kompatibla enheter att kunna komma åt tjänsten.

Tänk på att en efterlevnadsprincip även måste distribueras till användaren som använder enheten för att enhetens efterlevnad ska kunna utvärderas.
Om ingen efterlevnadsprincip har distribuerats till användaren behandlas enheten som kompatibel och inga åtkomstbegränsningar tillämpas.

Om en enhet inte uppfyller de villkor som du har definierat i principerna vägleds användaren genom en process för att registrera enheten och åtgärda problemet som gör att enheten inte är kompatibel.

Så här ser ett typiskt flöde för villkorlig åtkomst ut:

![Diagrammet visar beslutspunkterna som används för att avgöra om en enhet har åtkomst till en tjänst eller om den blockeras](../media/ConditionalAccess4.png)

## Hur konfigurerar jag villkorlig åtkomst?
Använd villkorlig åtkomst om du vill hantera åtkomsten till Microsoft **Exchange On-premises**, **Exchange Online**, **Exchange Online Dedicated**, **SharePoint Online** och **Skype för företag – Online**.

Du konfigurerar villkorlig åtkomst genom att konfigurera en efterlevnadsprincip för enheter och en princip för villkorlig åtkomst.

Efterlevnadsprincipen omfattar inställningar som lösenord och kryptering samt huruvida en enheten är jailbrokad. Enheten måste uppfylla dessa regler för att anses vara kompatibel.

Du kan ange en princip för villkorlig åtkomst för att begränsa åtkomst baserat på:
- Enhetens efterlevnadsstatus.
- Plattformen som körs på enheten.
- Typen av appar som används för att komma åt tjänsterna.

Till skillnad från andra Intune-principer kan principer för villkorlig åtkomst inte distribueras. När du har konfigurerat principen och valt de användare som den ska gälla för, tillämpas principen i stället på alla målanvändare. När en användare är angiven som mål för en policy, måste varje enhet de använder vara godkänd för att få åtkomst till resurser.


## Nästa steg
1. [Läs mer om principer för enhetsefterlevnad och hur de fungerar ](introduction-to-device-compliance-policies-in-microsoft-intune.md)

2. [Skapa en efterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md)

2.  Skapa en princip för villkorlig åtkomst för något av följande:
> [!div class="op_single_selector"]
  - [Skapa en princip för villkorlig åtkomst för Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Exchange On-premises](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för nya Exchange Online Dedicated](restrict-access-to-exchange-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för gamla Exchange Online Dedicated](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  - [Skapa en princip för villkorlig åtkomst för Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Jun16_HO3-->


