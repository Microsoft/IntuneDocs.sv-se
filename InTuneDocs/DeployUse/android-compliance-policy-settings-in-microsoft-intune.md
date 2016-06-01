---
# required metadata

title: Inställningar för efterlevnadsprinciper för Android-enheter | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Inställningar för efterlevnadsprinciper för Android-enheter i Microsoft Intune

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör Android 4.0 och senare eller Samsung KNOX 4.0 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för efterlevnadsprinciper för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för policy för efterlevnad för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)

## Systemsäkerhetsinställningar
### Lösenord
- **Kräv lösenord för att låsa upp mobila enheter:** Välj **Ja** för den här inställningen om användaren måste ange ett lösenord

-  för att komma åt sin enhet.

- **Minsta längd på lösenord:** Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla. **Lösenordskvalitet:** Aktivera den här inställningen för att konfigurera lösenordskrav för Android-enheter.
  -   **Välj mellan:**
  - **Låg säkerhetsbiometri**
  -   **Obligatoriskt**
  -   **Minst numeriskt**
  -   **Minst alfabetiskt**
  -   **Minst alfanumeriskt**

- Alfanumeriskt med symboler 

- **Minuter av inaktivitet innan lösenord måste anges:** Anger den inaktiva tiden innan användaren måste ange lösenordet på nytt.

- **Lösenordets giltighetstid (dagar):** Ange antalet dagar tills användarens lösenord upphör att gälla

- och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik:** Använd den här inställningen i kombination med **Förhindra återanvändning av tidigare lösenord** för att förhindra att användaren återanvänder tidigare använda lösenord.

### **Förhindra återanvändning av tidigare lösenord:** Om **Spara lösenordshistorik** väljs, så ange
- det antal tidigare använda lösenord som inte får återanvändas. Kräv lösenord när enheten återgår från viloläge:

## Den här inställningen bör användas ihop med inställningen **Antal minuters inaktivitet innan lösenord krävs**.

- Slutanvändarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i

## inställningen **Antal minuters inaktivitet innan lösenord krävs**.
- Kryptering
  **Kräv kryptering på den mobila enheten:** Välj **Ja** för den här inställningen om du vill kräva att enheten krypteras för att kunna ansluta till resurser.

- Enheter krypteras när du konfigurerar **Kräv lösenord för att
  låsa upp mobila enheter**


<!--HONumber=May16_HO2-->


