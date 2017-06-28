---
title: Skapa en enhetsefterlevnadsprincip
description: "Skapa en efterlevnadsprincip för att skydda mobila enheter och datorer som används för att komma åt företagets data."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 3dcafbd3cfdbccdfa851e8d21572d834d629564b
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="create-a-device-compliance-policy-in-microsoft-intune"></a>Skapa en enhetsefterlevnadsprincip i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver de steg du kan använda för att skapa en efterlevnadsprincip som en enhet måste följa för att anses vara kompatibel.

##  <a name="step-1-add-a-new-policy"></a>Steg 1: Lägg till en ny princip
  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** &gt; **Efterlevnadsprinciper** &gt; **Lägg till**.

  ![Skärmbild av sidan för efterlevnadsprincip i Intune-administratörskonsolen, som visar alternativet Lägg till på menyn överst på sidan](./media/intune-sa-3a-add-compliance-policy.png)

##  <a name="step-2--configure-settings"></a>Steg 2: Konfigurera inställningar
Aktivera önskade inställningar på sidan **Skapa princip**:
  -   Inställningar för systemsäkerhet, t.ex. lösenord och kryptering.
  -   Inställningar för enhetens hälsotillstånd, t.ex. om en enhet är jailbrokad eller inte, eller om den rapporteras som felfri av Windows-tjänsten för attestering av hälsotillstånd.
  -   Inställningar för enhetsegenskaper, t.ex. minsta operativsystemversion som krävs eller högsta operativsystemversion som tillåts.
![Sidan Skapa princip på fliken Allmänt](./media/intune-sa-3b-create-policy.png)


##  <a name="step-3-save-the-policy"></a>Steg 3: Spara principen
När du är klar väljer du **Spara princip**.

Du kan välja att distribuera principen direkt efter att du har sparat den eller välja att distribuera den senare. Den nya principen visas i noden **Efterlevnadsprinciper** på arbetsytan **Principer**.

##  <a name="step-4-set-the-compliance-status-validity-period"></a>Steg 4: Ange giltighetsperioden för efterlevnadsstatus
Om du vill ange hur lång tid enheten har på sig att checka in innan den betraktas som icke-kompatibel, går du till inställningarna för efterlevnadsprinciper och ändrar tiden. Standardinställningen är 30 dagar.

![Alternativet Inställningar för efterlevnadsprinciper på principmenyraden](../media/mdm-compliance-policy-settings.png)

![Dialogrutan Efterlevnadsprincip](../media/mdm-ca-compliance-status-validity-period.png)

## <a name="supported-policy-settings"></a>Principinställningar som stöds
I följande tabell visas inställningarna för efterlevnadsprincip och de plattformar där de stöds.

-------------
|Inställningar|iOS|Android|Windows|
|-----|----|-----|-----|
|Kräv ett lösenord för att låsa upp mobila enheter|iOS 6 och senare|Android 4.0 och senare <br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare|
|Tillåt enkla lösenord|iOS 6 och senare|Stöds inte|Windows Phone 8.1 och senare|
|Minsta längd på lösenord|iOS 6 och senare| Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare| Windows Phone 8.1 och senare<br>Windows 8,1|
|Lösenordstyp krävs|iOS 6 och senare|Saknas|Windows Phone 8.1 och senare <br>Windows RT<br> Windows RT 8.1 <br>Windows 8,1|
|Lägst antal teckenuppsättningar|iOS 6 och senare|Saknas|Windows Phone 8.1 och senare <br>Windows RT<br> Windows RT 8.1 <br>Windows 8,1|
|Lösenordskvalitet|Saknas|Android 4.0 och senare <br>Samsung KNOX Standard 4.0 och senare|Saknas|
|Antal minuters inaktivitet innan lösenord krävs|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br>Windows RT och Windows RT 8.1<br>Windows 8,1|
|Lösenordets giltighetstid (i dagar)|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br>Windows RT och Windows RT 8.1<br>Windows 8,1|
|Kom ihåg tidigare lösenord|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br>Windows RT och Windows RT 8.1<br>Windows 8,1|
|Förhindra återanvändning av tidigare lösenord|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br>Windows RT och Windows RT 8.1<br>Windows 8,1|
|Kräv lösenord när enheten återgår från viloläge| Saknas| Saknas|Windows 10 Mobil|
|Filkryptering på mobil enhet|Inte tillämpligt|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br> Windows 8,1|
|Kräv att enheter rapporteras som felfria| Saknas| Saknas|Windows <br>Windows 10 Mobil|
|Enheten får inte vara jailbrokad eller rotad|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Saknas|
|E-postkontot måste hanteras av Intune|iOS 6 och senare|Saknas| Saknas|
|Välj den e-postprofil som måste hanteras av Intune|iOS 6 och senare|Saknas| Saknas|
|Lägsta version av operativsystemet krävs|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare| Windows Phone 8.1 och senare<br>Windows 8,1|
|Högsta tillåtna version av operativsystemet|iOS 6 och senare|Android 4.0 och senare<br>Samsung KNOX Standard 4.0 och senare|Windows Phone 8.1 och senare<br>Windows 8,1|

Välj något av följande om du vill veta mer om efterlevnadsinställningar som stöds på varje plattform:
> [!div class="op_single_selector"]
- [Inställningar för policy för efterlevnad för iOS-enheter](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Android-enheter](android-compliance-policy-settings-in-microsoft-intune.md)
- [Inställningar för efterlevnadsprinciper för Windows- och Windows Phone-enheter](windows-compliance-policy-settings-in-microsoft-intune.md)


## <a name="next-steps"></a>Nästa steg
[Distribuera och övervaka en efterlevnadsprincip](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>Se även
[Introduktion till efterlevnadsprinciper för enheter](introduction-to-device-compliance-policies-in-microsoft-intune.md)

