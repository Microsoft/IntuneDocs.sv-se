---
title: Kom igång med principer i Microsoft Intune
titlesuffix: ''
description: Skapa principer för att skydda företagsdata och hantera slutanvändarnas enhetsanvändning för att få åtkomst till företagsresurser.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b8bffd0435988cc59c5c0e4d754b861729d466ae
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-with-creating-policies"></a>Kom igång med att skapa principer

Ett av de huvudsakliga målen med att komma igång med Intune är att registrera enheter och säkerställa att de är kompatibla med företagets principer för efterlevnad. Principer för efterlevnad hjälper dig inte bara att hantera särskilda enhetstyper, t.ex. företagsägda terminaler, men även personliga enheter (BYOD-enheter), surfplattor och användarlösa enheter.

![Instrumentpanel för efterlevnad med mycket liten mängd data](/intune/media/generic-compliance-dashboard.png)

Hantera mobila enheter i följande områden med efterlevnadsprinciper:

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

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enhetsefterlevnad**.
4. Välj **Principer** i fönstret **Enhetsefterlevnad**.
5. Välj **Skapa princip** och fyll i information som **namn** och **beskrivning**. 
6. Välj **iOS** som **plattform**.
6. Välj **Systemsäkerhet** i **Inställningar** och ändra sedan **Kräv lösenord för att låsa upp mobila enheter** till **Kräv**. Du kan också ange andra regler som **Minsta längd på lösenord**, **Krav på lösenordstyp** och **Antal inte alfanumeriska tecken i lösenordet**. Välj **OK** när du har konfigurerat klart principen.
7. Gå tillbaka till fönstret **Skapa princip** och välj **Skapa**.
8. När principen har skapats väljer du **Tilldelningar** för att tilldela den till testgruppen. Välj testgruppen, som nu bör ha testanvändaren, och tilldela sedan principen till den gruppen genom att klicka på **Spara**.
9. Vänta några minuter. Den registrerade enheten ska nu meddela dig om att den behöver ett uppdaterat lösenord för att kunna fortsätta vara kompatibel med företagets princip för efterlevnad. Du kan också manuellt kontrollera det här i **företagsportalappen för iOS** genom att trycka på enhetsnamnet och sedan på knappen **Synkronisera**.

## <a name="next-steps"></a>Nästa steg

[Kom igång med att registrera enheter](get-started-enroll.md) – Lär dig hur hela registreringsprocessen genom att registrera en iOS-enhet.

## <a name="learn-more"></a>Läs mer

* [Övervaka efterlevnadsprinciper för Intune-enheter](compliance-policy-monitor.md)
* [Vanliga sätt att använda principer för villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md)
