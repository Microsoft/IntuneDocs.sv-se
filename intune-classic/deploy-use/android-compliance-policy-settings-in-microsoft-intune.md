---
title: Inställningar för policy för efterlevnad för Android
description: I det här avsnittet beskrivs inställningarna för efterlevnadsprinciper för Android-enheter.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 01/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e721c5c7-9678-4f3b-81d4-564da5efd337
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 63618f9af5f2bdb863a19c229c862e446dd4ea7a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="compliance-policy-settings-for-android-devices-in-microsoft-intune"></a>Inställningar för efterlevnadsprinciper för Android-enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Principinställningarna som beskrivs i det här avsnittet gäller enheter som kör Android 4.0 och senare eller Samsung KNOX 4.0 och senare.

Om du letar efter information om andra plattformar väljer du något av följande:
> [!div class="op_single_selector"]
- [Inställningar för policy för efterlevnad för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Windows-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Android for Work-enheter](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="system-security-settings"></a>Inställningar för systemsäkerhet
### <a name="password"></a>Lösenord
- **Kräv lösenord för att låsa upp mobila enheter**: Ställ in på **Ja** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.

-  **Minsta längd på lösenord**: Ange det minsta antal siffror eller tecken som användarens lösenord måste innehålla.

- **Lösenordskvalitet**: Den här inställningen identifierar om lösenordskraven som du anger är konfigurerade på enheten. Aktivera den här inställningen för att kräva att användare uppfyller vissa lösenordskrav för Android-enheter. Välj mellan:

  -   **Låg säkerhetsbiometri**
  -   **Obligatoriskt**
  -   **Minst numeriskt**
  -   **Minst alfabetiskt**
  -   **Minst alfanumeriskt**
  -   **Alfanumeriskt med symboler**

- **Minuter av inaktivitet innan lösenord krävs:**  Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.

- **Lösenordets giltighetstid (dagar)**: Ange antalet dagar tills användarens lösenord upphör att gälla och användaren måste ange ett nytt lösenord.

- **Spara lösenordshistorik**: Använd den här inställningen i tillsammans med **Förhindra återanvändning av tidigare lösenord** om du inte vill att användaren ska kunna återanvända tidigare använda lösenord.

- **Förhindra återanvändning av tidigare lösenord**: Ange hur många tidigare använda lösenord som inte får återanvändas (om **Spara lösenordshistorik** har valts).

- **Kräv lösenord när enheten lämnar inaktivt läge**: Använd den här inställningen tillsammans med **Minuter av inaktivitet innan lösenord måste anges**. Användarna uppmanas att ange ett lösenord för att få åtkomst till en enhet som har varit inaktiv under den tid som anges i inställningen **Minuter av inaktivitet innan lösenord måste anges**.

### <a name="encryption"></a>Kryptering
- **Kräv kryptering på den mobila enheten**: Välj **Ja** för den här inställningen om du vill kräva att enheter ska krypteras för att ansluta till resurser. Enheter krypteras när du konfigurerar inställningen **Kräv lösenord för att låsa upp mobila enheter**.

## <a name="device-health-and-security-settings"></a>Inställningar för enhetens för hälsotillstånd och säkerhet

- **Enheten får inte vara jailbrokad eller rotad**: Om du aktiverar den här inställningen utvärderas jailbrokade enheter som inkompatibla.
- **Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0 eller senare)**: Om du vill blockera enheter som har aktiverat **Säkerhet > Okända källor** på enheten aktiverar du inställningen och väljer **Ja**.  

>[!IMPORTANT]
>Inställningen **Okända källor** måste vara aktiverad för program med separat inläsning. Du bör endast tillämpa denna efterlevnadsprincip om du inte läser in Android-appar separat på enheter.

- **Kräv att USB-felsökning är inaktiverat (Android 4.2 eller senare)**: Ange om du vill kontrollera att USB-felsökning är aktiverat på enheten.
- **Kräv att ”Genomsök enhet efter säkerhetshot” (Android 4.2-4.4) är aktiverat på enheter**: Ange om funktionen **Verifiera appar** är aktiverad på enheten.
- **Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0 eller senare)**: Ange den lägsta Android-korrigeringsnivån.  Enheter som inte har minst den här korrigeringsnivån räknas som inkompatibla. Datumet måste ha formatet: ÅÅÅÅ-MM-DD.
- **Kräv att enhetsskydd är aktiverat**: Använd den här inställningen för att ta riskbedömningen från Lookout MTP-lösningen som ett villkor för efterlevnad. Välj den högsta tillåtna hotnivån, som är en av följande:

  - **Ingen (skyddad)**: Det här är det säkraste alternativet. Detta innebär att enheten inte kan ha några hot. Om hot identifieras på enheten utvärderas den som icke-kompatibel.
  - **Låg**: Enheten utvärderas som kompatibel om det bara finns hot på den låga nivån på enheten. Om hot på en högre nivå identifieras får enheten statusen icke-kompatibel.
  - **Medel**: Enheten utvärderas som kompatibel om hoten som finns på enheten är på en låg eller medelhög nivå. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Det här alternativet är minst säkert. I grunden innebär detta att alla hotnivåer tillåts, vilket kanske endast är användbart om du använder den här lösningen för rapportering.

  Mer information finns i [Skapa efterlevnadsprincip för Lookout-enhet](create-lookout-device-compliance-policy.md).

## <a name="device-property-settings"></a>Inställningar för enhetsegenskaper

- **Lägsta operativsystemversion som krävs:** När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel.
  En länk med information om hur du uppgraderar visas. Användaren kan välja att uppgradera enheten och kan sedan komma åt företagets resurser.

- **Högsta tillåtna version av operativsystemet**: När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.
