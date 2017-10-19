---
title: "Inställningar för efterlevnadsprinciper för iOS-enheter"
description: "Det här avsnittet beskriver de regler och inställningar som du kan ange i en efterlevnadsprincip för iOS-enheter."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cd64a833aa9dbddd2e85dbc427f5c5d5d2bca64
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="compliance-policy-settings-for-ios-devices-in-microsoft-intune"></a>Inställningar för efterlevnadsprinciper för iOS-enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör iOS 8.0 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för efterlevnadsprinciper för Android-enheter](android-compliance-policy-settings-in-microsoft-intune.md)
- [Kompatibilitetsprincipinställningar för Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Systemsäkerhetsinställningar
### <a name="password"></a>Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** om du vill kräva att användarna anger ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.

- **Tillåt enkla lösenord**: Välj **Ja** om du vill att användaren ska kunna skapa enkla lösenord som **1234** eller **1111**.

-  **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

- **Krav på lösenordstyp**: Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.

- **Minsta antal teckenuppsättningar:** Om du konfigurerar alternativet för **Krav på lösenordstyp** som **Alfanumeriskt** använder du den här inställningen för att specificera det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  -   Gemener
  -   Versaler
  -   Symboler
  -   Siffror

  Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

  För iOS-enheter refererar den här inställningen för antalet specialtecken (t.ex, **!**, **#**,**&amp;**) som måste inkluderas i lösenordet.

- **Minuter av inaktivitet innan lösenord krävs**: Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.

- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Om du har valt **Spara lösenordshistorik** anger du hur många tidigare använda lösenord som inte får återanvändas.

- **Kräv lösenord när enheten lämnar inaktivt läge**: Använd den här inställningen tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användaren uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### <a name="email-profile"></a>E-postprofil
- **E-postkontot måste hanteras av Intune:** Om det här alternativet är inställt på **Ja** måste enheten använda e-postprofilen som har distribuerats till enheten. Enheten betraktas som icke-kompatibel i följande situationer:
  - E-postprofilen har distribuerats till en annan användargrupp än användargruppen som är kompatibilitetsprincipens mål.
  - Användaren har redan konfigurerat ett e-postkonto på enheten som matchar Intune-e-postprofilen som distribuerats till enheten. Intune kan inte skriva över den användartillhandahållna profilen, och kan därför inte hantera den. För att säkerställa efterlevnad måste användaren ta bort de befintliga e-postinställningarna. Sedan kan Intune installera den hantera e-postprofilen.

- **Välj den e-postprofil som måste hanteras av Intune**: Om inställningen **E-postkontot måste hanteras av Intune** har valts väljer du **Välj** för att ange Intune-e-postprofilen. E-postprofilen måste finnas på enheten.

     Information om e-postprofiler finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## <a name="device-health-settings"></a>Inställningar för enhetens hälsotillstånd

- **Enheten får inte vara jailbrokad eller rotad**: Om du aktiverar den här inställningen kommer jailbrokade enheter inte att vara kompatibla.

##  <a name="device-properties"></a>Egenskaper för enheten
- **Lägsta operativsystemversion som krävs**: När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
En länk med information om hur du uppgraderar visas. Användarna kan välja att uppgradera sina enheter. Därefter har de åtkomst till företagsresurser.

- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.
