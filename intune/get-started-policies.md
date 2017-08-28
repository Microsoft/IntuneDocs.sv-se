---
title: "Komma igång med principer"
titleSuffix: Intune on Azure
description: "Skapa principer som hindrar användare från att använda enheten på ett otillåtet sätt."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b12b80ac13868b6706d2d4e7532ec13cba9a5b7e
ms.sourcegitcommit: 45204e0fb8cb4cce449e65f2f1d7bb6f6ac4ccf5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2017
---
# <a name="get-started-with-policies"></a>Kom igång med principer

Ett av de huvudsakliga målen med att komma igång med Intune är att registrera enheter och säkerställa att de är kompatibla med företagets principer för efterlevnad. Principer för efterlevnad hjälper dig inte bara att hantera särskilda enhetstyper, t.ex. företagsägda terminaler, men även personliga enheter (BYOD-enheter), surfplattor och användarlösa enheter.

![Instrumentpanel för efterlevnad med liten mängd data](/intune/media/generic-compliance-dashboard.png)

Principer för efterlevnad tillhandahåller följande hanteringsmöjligheter för mobila enheter:

* Reglera det antal enheter som varje användare kan registrera
* Hantera enhetsinställningar (t.ex. kryptering på enhetsnivå, lösenordslängd, kameraanvändning)
* Leverera appar, e-postprofiler, VPN-profiler osv.
* Utvärdera villkor på enhetsnivå för principer för säkerhetsefterlevnad

Principer för efterlevnad skapas separat för varje plattform. I den här övningen håller vi oss till iOS. Följande principer är tillgängliga för iOS-enheter:

* Konfiguration av PIN-kod eller lösenord
* Enhetskryptering
* Jailbroken enhet
* E-postprofil
* Lägsta version av operativsystemet
* Högsta version av operativsystemet

__Hur skapar jag en princip?__

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Sök efter **Intune** med **Sök resurser**.
3. Välj **Enhetsefterlevnad**.
4. Välj **Principer** på bladet **Enhetsefterlevnad**.
5. Välj **Skapa princip** och fyll i information som **namn** och **beskrivning**. Välj **iOS** som **plattform**.
6. Välj **Systemsäkerhet** i **Inställningar** och ändra sedan **Kräv lösenord för att låsa upp mobila enheter** till **Kräv**. Du kan också ange andra regler som **Minsta längd på lösenord**, **Krav på lösenordstyp** och **Antal inte alfanumeriska tecken i lösenordet**. Välj **OK** när du har konfigurerat klart principen.
7. Gå tillbaka till bladet **Skapa princip** och välj **Skapa**.
8. När principen har skapats väljer du **Tilldelningar** för att tilldela den till testgruppen. Välj testgruppen, som nu bör ha testanvändaren, och tilldela sedan principen till den gruppen genom att klicka på **Spara**.
9. Vänta några minuter. Den registrerade enheten ska nu meddela dig om att den behöver ett uppdaterat lösenord för att kunna fortsätta vara kompatibel med företagets princip för efterlevnad. Du kan också manuellt kontrollera det här i **företagsportalappen för iOS** genom att trycka på enhetsnamnet och sedan på knappen **Synkronisera**.

## <a name="next-steps"></a>Nästa steg

[Kom igång med att registrera enheter](get-started-enroll.md) – Lär dig hur hela registreringsprocessen genom att registrera en iOS-enhet.

## <a name="learn-more"></a>Läs mer

* [Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
* [Vanliga sätt att använda principer för villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md)
