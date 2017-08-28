---
title: "Lägg till företagsidentifierare i Intune"
titleSuffix: Intune on Azure
description: "Läs mer om hur du kan lägga till företagsidentifierare (registreringsmetod, IMEI- och serienummer) i Microsoft Intune. \""
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 03a278762401ee9697909cf45b3fe86212393e66
ms.sourcegitcommit: 0b164f806165d312acfc88815a60e325e3d02672
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2017
---
# <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du identifiera en enhet som företagsägd på en rad olika sätt. Intune kan samla in ytterligare information från företagsägda enheter. Du kan också ställa in enhetsbegränsningar för att förhindra registrering av enheter som inte är företagsägda.

En enhet identifieras som företagsägd när något av följande villkor är uppfyllt:

- Registrerad med ett [enhetsregistreringshanterar](device-enrollment-manager-enroll.md)-konto (alla plattformar)
- Registrerat med Apples [program för enhetsregistrering](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md) eller [Apple Configurator](apple-configurator-enroll-ios.md) (endast iOS)
- Förhandsdeklarerat med ett IMEI-nummer (alla plattformar med IMEI-nummer) eller serienummer (iOS och Android)
- Registrerad i Azure Active Directory eller Enterprise Mobility Suite som en Windows 10 Enterprise-enhet (endast Windows 10)
- Markerad som **Företag** i **Egenskaper** för enheten

För företagsägda enheter visas **Företag** i kolumnen **Ägarskap** i enhetsposterna i Intune. Gå till **Enheter** > **Alla enheter**.

## <a name="predeclare-a-device-with-imei-or-serial-number"></a>Förhandsdeklarera en enhet med IMEI- eller serienummer

Som Intune-administratör kan du skapa och importera en fil med kommateckenavgränsade värden (CSV) som innehåller en lista med IMEI- eller serienummer. Intune använder dessa identifierare för att ange att vissa enheter är företagsägda. Du kan deklarera IMEI-nummer för alla plattformar som stöds. Du kan endast deklarera serienummer för iOS- och Android-enheter. Varje IMEI-nummer eller serienummer kan innehålla information som anges i listan för administrativa ändamål.

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[Lär dig hitta serienumret för en Apple-enhet](https://support.apple.com/HT204308).<br>
[Lär dig hitta serienumret för en Android-enhet](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers"></a>Lägg till företagsidentifierare
För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till IMEI-numren eller serienumren i den vänstra kolumnen och informationen i den högra kolumnen. Endast en typ av ID kan importeras till en CSV-fil, antingen IMEI-nummer eller serienummer. Informationen är begränsad till 128 tecken och används endast i administrationssyfte. Informationen visas inte på enheten. Den aktuella gränsen är 500 rader per CSV-fil.

**Överför en CSV-fil med serienummer** – Skapa en lista med två kolumner och kommaavgränsade värden (CSV-fil) utan sidhuvud och begränsa listan till 5 000 enheter eller 5 MB per CSV-fil.

|||
|-|-|
|&lt;ID #1&gt;|&lt;Information om enhet nr 1&gt;|
|&lt;ID #2&gt;|&lt;Information om enhet nr 2&gt;|

CSV-filen när den visas i en textredigerare:

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> Vissa Android-enheter har flera IMEI-nummer. Intune läser bara ett IMEI-nummer per registrerad enhet. Om du importerar ett IMEI-nummer som inte är det IMEI-nummer som är inventerat i Intune så kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget. Om du importerar flera IMEI-nummer för en enhet så visas registreringsstatus för icke-inventerade nummer som **Okänt**.<br>
>Observera även att serienummer för Android inte är garanterat unika – de kanske inte ens finns. Hör efter med enhetens leverantören huruvida serienumret är ett tillförlitligt enhets-ID eller inte.
>Serienummer som rapporteras av enheten till Intune kanske inte matchar det ID som visas i menyerna Android-inställningar/Om på enheten. Kontrollera vilken typ av serienummer som rapporterats av tillverkaren av enheten.

### <a name="add-a-csv-list-of-corporate-identifiers"></a>Lägg till en CSV-lista över företagsidentifierare

1. I Intune på Azure Portal väljer du **Enhetsregistrering** > **Id:n för företagsenheter** och klickar sedan på **Lägg till**.

 ![Skärmbild av företagets arbetsyta med ID:n för enheter och knappen Lägg till markerad.](./media/add-corp-id.png)

2. På bladet **Lägg till identifierare** anger du ID-typ, **IMEI** eller **Serienummer**. Du kan ange om tidigare importerade siffror ska **skriva över information för befintliga identifierare**.

3. Klicka på mappikonen och ange sökvägen till listan du vill importera. Navigera till CSV-filen och välj **Lägg till**. Du kan klicka på **Uppdatera** om du vill visa de nya ID:na.

Importerade enheter registreras inte nödvändigtvis. Enheterna kan antingen ha tillståndet **Registrerad** eller **Ej kontaktad**. **Ej kontaktad** innebär att enheten aldrig har kommunicerat med Intune-tjänsten.

## <a name="delete-corporate-identifiers"></a>Ta bort företagsidentifierare

1. I Intune på Azure Portal väljer du **Enhetsregistrering** > **Id:n för företagsenheter**.
2. Markera de enhetsid:n du vill ta bort och välj **Ta bort**.
3. Bekräfta borttagningen.

Om du tar bort en företags-id för en registrerad enhet ändras inte ägarskapet för enheten. Om du vill ändra ägarskapet för en enhet går du till **Enheter** > **Alla enheter**, markerar enheten, väljer **Egenskaper** och ändrar **Ägarskap för enhet**.

## <a name="imei-specifications"></a>IMEI-specifikationer
Detaljerade specifikationer om IMEI (International Mobile Equipment Identifiers) finns i [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).
