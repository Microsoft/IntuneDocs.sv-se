---
title: "Skapa en efterlevnadsprincip för macOS"
titleSuffix: Azure portal
description: "Lär dig hur du skapar en efterlevnadsprincip för macOS-enheter."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5f1caeddbd3d171092ef59cfb092404b31154f2
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2018
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>Skapa en enhetsefterlevnadsprincip för macOS-enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>Innan du börjar

Granska Intune-enhetens efterlevnadsprincip innan du skapar och tilldelar en enhetsefterlevnadsprincip.

- Läs mer om enhetsefterlevnadsprinciper i [Kom igång med enhetsefterlevnadsprinciper](device-compliance.md).

> [!IMPORTANT]
> Du måste skapa principer för efterlevnad för varje plattform. Intune-inställningarna för efterlevnadsprinciper är beroende av plattformsfunktioner, det vill säga inställningar som exponeras via MDM-protokollet.

Följande tabell beskriver också hur inkompatibla inställningar hanteras när en efterlevnadsprincip används med en princip för villkorlig åtkomst:


| Principinställningar | macOS 10.11 och senare |
| --- | --- |
| **Konfiguration av PIN-kod eller lösenord** | Åtgärdad |   
| **Enhetskryptering** | Åtgärdad (genom angiven PIN-kod) |
| **E-postprofil** | I karantän |
|**Lägsta version av operativsystemet** | I karantän |
| **Högsta version av operativsystemet** | I karantän |  


**Åtgärdad** = Enhetens operativsystem tillämpar efterlevnad. (Till exempel om användaren tvingas att ange en PIN-kod.)

**I karantän** = Enhetens operativsystem tillämpar inte efterlevnad. (Till exempel om Android-enheter inte tvingar användaren att kryptera enheten.) När enheten inte uppfyller efterlevnadskraven utförs följande åtgärder:

- Enheten blockeras om en princip för villkorlig åtkomst tillämpas för användaren.
- Företagsportalen meddelar användaren om eventuella efterlevnadsproblem.

## <a name="macos-compliance-policy-settings"></a>Inställningar för efterlevnadsprinciper för MacOS

Du har olika kategorier med olika inställningar att välja mellan när du skapar en ny enhetsefterlevnad med Intune:

- Enhetens hälsotillstånd

- Egenskaper för enhet

- Systemsäkerhet

### <a name="device-health"></a>Enhetens hälsotillstånd

- **Kräver systemintegritetsskydd** – Ställ in på **Krav** för att kontrollera om dina macOS enheter använder systemintegritetsskydd.

### <a name="device-properties"></a>Egenskaper för enheten

- **Lägsta operativsystemversion** – När en enhet inte uppfyller minimikraven för versionen av operativsystemet rapporteras den som inkompatibel. En länk med information om hur du uppgraderar visas. Användarna kan välja att uppgradera sina enheter. Därefter har de åtkomst till företagsresurser.

- **Högsta version av operativsystemet** – När en enhet använder en senare version av operativsystemet än den som angetts i regeln blockeras åtkomsten till företagsresurser och användaren ombeds kontakta sin IT-administratör. Enheten kan inte användas för att komma åt företagsresurser förrän regeln för att tillåta versionen av operativsystemet har ändrats.

### <a name="system-security-settings"></a>Inställningar för systemsäkerhet

#### <a name="password"></a>Lösenord

- **Kräv lösenord för att låsa upp mobila enheter** – Ställ in på **Krav** för att ställa in så att användare måste ange ett lösenord för att få åtkomst till sina enheter.

- **Enkla lösenord** – Ställ in på **Blockera** om du vill att användaren inte ska kunna skapa enkla lösenord som **1234** eller **1111**.

- **Minsta längd på lösenord** – Ange det minsta antalet siffror eller tecken som lösenordet måste innehålla.

- **Lösenordstyp** – Ange om användaren måste skapa ett **alfanumeriskt** lösenord eller ett **numeriskt** lösenord.

- **Antal bokstäver och siffror i lösenord** – Om du konfigurerar alternativet för **Krav på lösenordstyp** som **Alfanumeriskt** använder du den här inställningen för att specificera det minsta antal teckenuppsättningar som lösenordet måste innehålla. 

    > [!NOTE]
    > Om du anger en högre siffra måste användaren skapa ett lösenord som är mer komplext.

    > [!IMPORTANT]
    > För macOS-enheter refererar den här inställningen för antalet specialtecken (t.ex, **!** , **#**, **&amp;**) som måste inkluderas i lösenordet.

- **Max antal minuter av inaktivitet innan lösenord krävs** – Ange hur lång tid av inaktivitet som kan gå innan användaren måste ange sitt lösenord på nytt.

- **Lösenordets giltighetstid (dagar)** – Ange antalet dagar (mellan 1 och 250) tills lösenordet upphör att gälla och användaren måste ange ett nytt lösenord.

- **Förhindra återanvändning av tidigare lösenord** – Ange antalet tidigare lösenord som inte får återanvändas.

    > [!IMPORTANT]
    > När lösenordskravet ändras på en macOS-enhet börjar det inte gälla förrän nästa gång användaren ändrar sitt lösenord. Om du till exempel ställer in begränsning av lösenordslängd på åtta siffror och macOS-enheten för närvarande har lösenord med sex siffror fortsätter enheten att vara kompatibel till nästa gång användaren uppdaterar sitt lösenord på enheten.

## <a name="to-create-a-device-compliance-policy"></a>Skapa en princip för enhetsefterlevnad

1. Gå till [Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter.

2. När du har loggat in visas **Azure-instrumentpanelen**.

3. Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

4. Välj **Intune**. **Intune-instrumentpanelen** visas.

5. Välj **Enhetsefterlevnad** och välj **Principer** under **Hantera**.

6. Klicka på **Skapa princip**.

7. Skriv ett namn, ge en beskrivning och välj den plattform som du vill att den här principen ska tillämpas på.

8. Bladet **macOS efterlevnadsprincip** öppnas. Välj följande kategorier för enhetsefterlevnadsinställningar: **Säkerhet**, **Enhetens hälsotillstånd** och **Enhetsegenskap**.

10. När du har valt dina inställningar, väljer du **OK** under varje inställningskategori.

11. Välj **OK** och sedan **Skapa**.

## <a name="assign-user-groups"></a>Tilldela användargrupper

Om du vill tilldela en efterlevnadsprincip till användare, väljer du en princip som du har konfigurerat. Du hittar befintliga principer på bladet **Efterlevnadsprinciper**.

1. Välj den efterlevnadsprincip som du vill tilldela till användarna och välj **Tilldelningar**. Då öppnas det blad där du kan välja **Azure Active Directory-säkerhetsgrupper** och tilldela dem till principen.

2. Öppna bladet som visar säkerhetsgrupper för Azure AD genom att välja **Välj grupper**.

3. Välj **Välj** och sedan **spara** för att tilldela efterlevnadsprinciperna för enheter till Azure AD-säkerhetsgrupper.

4. När du har tilldelat efterlevnadsprinciperna för enheter till dina grupper kan du stänga bladet **Tilldelningar**.

    > [!TIP]
    > Enheternas efterlevnad kontrolleras som standard var åttonde timme men användare kan forcera processen med Intune-företagsportalappen.

## <a name="next-steps"></a>Nästa steg

[Så här övervakar du principer för enhetsefterlevnad](compliance-policy-monitor.md)
