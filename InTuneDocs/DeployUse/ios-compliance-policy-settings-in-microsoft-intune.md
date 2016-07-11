---
title: "Inställningar för efterlevnadsprinciper för iOS-enheter | Microsoft Intune"
description: 
keywords: 
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a59d24f-ed58-49b1-b874-b2d4aea3ec76
ms.reviewer: chrisgre
ms.suite: ems
ms.sourcegitcommit: e736d688032dd2ddee5be9edf2a33d5e7ba5257b
ms.openlocfilehash: 591023ea08b669ca69e8cac45e37b5fb2689ddcd


---


# Inställningar för efterlevnadsprinciper för iOS-enheter i Microsoft Intune

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör iOS 6 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för policy för efterlevnad för Android-enheter](android-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## Systemsäkerhetsinställningar
### Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter. iOS-enheter som använder lösenord krypteras.

- **Tillåt enkla lösenord:** Ställ in på **Ja** för att låta användarna skapa enkla lösenord som '**1234**'eller'**1111**'.

-  **Minsta längd på lösenord:** Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.
- **Lösenordstyp som krävs**: Ange om användarna måste skapa ett **alfanumeriskt** eller **numeriskt lösenord**.

- **Minsta antal teckenuppsättningar:** Om du konfigurerar alternativet för **Krav på lösenordstyp** som **Alfanumeriskt** använder du den här inställningen för att specificera det minsta antal teckenuppsättningar som lösenordet måste innehålla. De fyra teckenuppsättningarna är:
  -   Gemener
  -   Versaler
  -   Symboler
  -   Siffror

  Om du anger en hög siffra för den här inställningen kräver det att användarna skapar lösenord som är mer komplexa.

  För iOS-enheter refererar den här inställningen för antalet specialtecken (t.ex, **!**, **#**,**&amp;**) som måste inkluderas i lösenordet.
- **Minuter av inaktivitet innan lösenord krävs:**  Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.

- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.

- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### E-postprofil
- **E-postkontot måste hanteras av Intune:** när det här alternativet är ställt på **Ja** måste enheten använda e-postkontot som distribuerats till enheten. Enheten betraktas som icke-kompatibel i följande situationer:
  - E-postprofilen måste också distribueras till samma användargrupp som den som berörs av efterlevnadsprincipen, annars betraktas användarnas enheter som inkompatibla.
  - Enheten rapporteras som inkompatibel om användaren redan har konfigurerat ett e-postkonto på enheten som matchar Intune-epostprofilen som distribuerats till enheten. Intune kan inte skriva över den användartillhandahållna profilen, och kan därför inte hantera den. För att försäkra sig om efterlevnad måste användaren ta bort de befintliga e-postinställningarna. Efter det kan Intune installera den hanterade e-postprofilen.


- **Välj den e-postprofil som måste hanteras av Intune:**
     Om inställningen **E-postkontot måste hanteras av Intune** har valts, välj **Välj** för att ange e-postprofilen för Intune. E-postprofilen måste finnas på enheten.

     Information om e-postprofiler finns i [Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md).

## Inställningar för enhetens hälsotillstånd

- **Enheten får inte vara jailbrokad eller rotad:** Om du aktiverar den här inställningen kommer jailbrokade enheter inte att vara kompatibla.

##  Egenskaper för enheten
- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet:** När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.



<!--HONumber=Jun16_HO4-->


