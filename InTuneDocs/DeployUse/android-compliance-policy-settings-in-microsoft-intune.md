---
title: "Inställningar för efterlevnadsprinciper för Android-enheter | Microsoft Intune"
description: "I det här avsnittet beskrivs inställningarna för efterlevnadsprinciper för Android-enheter."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: be1ebcdf2514e45d383dd49890e0e21acf6ede44
ms.openlocfilehash: f99158924b83254efedb8663b9d6175a6b6775b1


---


# Inställningar för efterlevnadsprinciper för Android-enheter i Microsoft Intune

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör Android 4.0 och senare eller Samsung KNOX 4.0 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för efterlevnadsprinciper för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## Systemsäkerhetsinställningar
### Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.

-  **Minsta längd på lösenord:** Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

- **Lösenordskvalitet:** Aktivera den här inställningen för att konfigurera lösenordskrav för Android-enheter. Välj mellan:
  -   **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  -   **Minst numeriskt**
  -   **Minst alfabetiskt**
  -   **Minst alfanumeriskt**
  -   **Alfanumeriskt med symboler **

- **Minuter av inaktivitet innan lösenord måste anges:** Anger efter hur lång tids inaktivitet som användaren måste ange lösenordet igen.

- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Om **Spara lösenordshistorik** har valts anger du hur många tidigare använda lösenord som inte får återanvändas.

- **Kräv lösenord när enheten lämnar inaktivt läge:** Den här inställningen bör användas tillsammans med inställningen **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### Kryptering
- **Kräv kryptering på den mobila enheten:** Välj **Ja** för den här inställningen om du vill kräva att enheter ska krypteras för att ansluta till resurser. Enheter krypteras när du konfigurerar inställningen **Kräv lösenord för att låsa upp mobila enheter**.

## Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad:** Om du aktiverar den här inställningen kommer jailbrokade enheter att utvärderas som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0 eller senare)** Om du vill blockera enheter som har aktiverat **Säkerhet > Okända källor** på enheten aktiverar du och väljer **Ja** för inställningen.  
>[!IMPORTANT]
>Inställningen **Okända källor** måste vara aktiverad för program med separat inläsning.  Du bör endast tillämpa denna efterlevnadsprincip om du inte läser in Android-appar separat på enheter.

- **Kräv att USB-felsökning är inaktiverat (Android 4.2 eller senare)**: Den här inställningen anger om du vill kontrollera om USB-felsökning är aktiverad på enheten.
- **Kräv att ”Genomsök enhet efter säkerhetshot” (Android 4.2-4.4) är aktiverat på enheter**: Den här inställningen anger att funktionen **Verifiera appar** är aktiverad på enheten.
- **Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0 eller senare)**: Använd den här inställningen för att ange den lägsta Android-korrigeringsnivå.  Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet ÅÅÅÅ-MM-DD.


## Inställningar för enhetsegenskaper
- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
  En länk med information om hur du uppgraderar visas. Slutanvändaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet:** När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.



<!--HONumber=Jul16_HO5-->


