---
# required metadata

title: Inställningar för efterlevnadsprinciper för iOS-enheter | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Inställningar för efterlevnadsprinciper för iOS-enheter i Microsoft Intune

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör iOS 6 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för policy för efterlevnad för Android-enheter](android-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## Systemsäkerhetsinställningar
### Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:**    Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att komma åt sin enhet.

- iOS-enheter som använder lösenord krypteras.

-  **Tillåt enkla lösenord:** Ställ in
- på **Ja** för att låta användarna skapa enkla lösenord

- som till exempel '**1234**'eller'**1111**'. Minsta längd på lösenord:
  -   Ange det minsta antalet siffror eller tecken som
  -   användarens lösenord måste innehålla.
  -   **Lösenordstyp som krävs:** Ange om användarna måste skapa
  -   ett **alfanumeriskt**, eller ett **numeriskt** lösenord.

  **Minsta antal teckenuppsättningar:** Om du ställer in **Lösenordstyp som krävs** på

  **alfanumeriskt**, så kan du använda den här inställningen för att ange det minsta antalet
- teckenuppsättningar som lösenordet måste innehålla.

- De fyra teckenuppsättningarna är:

- Gemener

- Versaler

- Symboler Siffror

### Om du anger en hög siffra för den här inställningen kräver det att användarna skapar mer komplexa lösenord.
- För iOS-enheter refererar den här inställningen för antalet specialtecken (t.ex, **!**, **#**, **&amp;**) som måste inkluderas i lösenordet. **Minuter av inaktivitet innan lösenord krävs:**  Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.
  - **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla
  - och användaren måste ange ett nytt lösenord. **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** för att förhindra att användaren återanvända tidigare använda lösenord.


- **Förhindra återanvändning av tidigare lösenord:** Om du har valt **Spara lösenordshistorik** anger du det antal tidigare använda lösenord som inte får återanvändas.

     Kräv lösenord när enheten återgår från viloläge:

## Den här inställningen bör användas ihop med inställningen **Antal minuters inaktivitet innan lösenord krävs**.

- Slutanvändarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i

##  inställningen **Antal minuters inaktivitet innan lösenord krävs**.
- E-postprofil
**E-postkontot måste hanteras av Intune:** när det här alternativet är ställt på **Ja** måste enheten använda e-postkontot som distribuerats till enheten. Enheten betraktas som icke-kompatibel i följande situationer:

- E-postprofilen måste också distribueras till samma användargrupp som den som berörs av efterlevnadsprincipen, annars betraktas användarnas enheter som inkompatibla. Enheten rapporteras som inkompatibel om användaren redan har konfigurerat ett e-postkonto på enheten som matchar Intune-epostprofilen som distribuerats till enheten.


<!--HONumber=May16_HO2-->


