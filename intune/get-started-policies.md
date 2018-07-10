---
title: Kom igång med principer i Microsoft Intune – Azure | Microsoft Docs
description: Skapa principer för att skydda företagsdata och hantera slutanvändarnas enhetsanvändning för att få åtkomst till företagsresurser. Tilldela den principerna till grupper.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d7fa1b596a1800971919cfc0ab3e94d2d16ec328
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271532"
---
# <a name="get-started-with-creating-policies"></a>Kom igång med att skapa principer

Intune-principer är ett bra sätt att registrera enheter och kontrollera att de är kompatibla med företagets principer. Principer för efterlevnad hjälper dig att hantera särskilda enhetstyper, t.ex. företagsägda terminaler samt personliga enheter (BYOD-enheter), surfplattor och användarlösa enheter.

![Instrumentpanel för efterlevnad med mycket liten mängd data](/intune/media/generic-compliance-dashboard.png)

Mobila enheter kan hanteras med efterlevnadsprinciper, inklusive:

* Reglera det antal enheter som en användare registrerar i Intune
* Hantera enhetsinställningar såsom kryptering på enhetsnivå, lösenordslängd och kameraanvändning
* Leverera appar, e-postprofiler, VPN-profiler och mer
* Utvärdera villkor på enhetsnivå för principer för säkerhetsefterlevnad

Efterlevnadsprinciper skapas för varje plattform, till exempel iOS, Android, Windows och mer. I den här övningen använder du iOS. Följande principer är tillgängliga för iOS-enheter:

* Konfiguration av PIN-kod eller lösenord
* Enhetskryptering
* Jailbroken enhet
* E-postprofil
* Lägsta version av operativsystemet
* Högsta version av operativsystemet

## <a name="create-a-policy"></a>Skapa en princip

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
4. Ange ett **principnamn** och en **Beskrivning**. 
5. För **plattformen** väljer du **iOS**.
6. I **Inställningar** väljer du **Systemsäkerhet** och ställer sedan in **Kräv lösenord för att låsa upp mobila enheter** till **Kräv**. 

    Du kan även ange andra regler, till exempel: 
    - **Minsta längd på lösenord**
    - **Lösenordstyp krävs**
    - **Antal icke-alfanumeriska tecken i lösenord**
    
    När du har konfigurerat klart principen väljer du **OK**.
  
7. Gå tillbaka till **Skapa princip** och välj **Skapa**. Det här steget skapar principen och listar den i **Efterlevnad för enhet** > **Principer**.
8. Markera den nya principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
Välj Valda grupper för att se dina befintliga Azure AD-säkerhetsgrupper. Välj de användargrupper som du vill att den här principen ska tillämpas på och välj **Spara** för att distribuera principen till användare.

För att följa den nya företagsprincipen frågar den registrerade enheten efter ett uppdaterat lösenord efter några minuter. Du kan manuellt söka efter uppdateringen i **Företagsportalappen för iOS**. Öppna företagsportalappen, välj enhetsnamnet och välj sedan **Synkronisera**.

> [!NOTE]
> Nya principer som tillämpas på en dynamisk enhetsgrupp kan ta upp till åtta timmar att tillämpas på alla enheter i gruppen.

## <a name="next-steps"></a>Nästa steg

[Kom igång med att registrera enheter](get-started-enroll.md) – Lär dig hur hela registreringsprocessen genom att registrera en iOS-enhet.

## <a name="learn-more"></a>Läs mer

* [Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
* [Vanliga sätt att använda principer för villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md)
