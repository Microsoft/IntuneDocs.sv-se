---
title: Lägg till företagsidentifierare i Intune
titleSuffix: ''
description: Läs mer om hur du kan lägga till företagsidentifierare (registreringsmetod, IMEI- och serienummer) i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: afc9d953e1d324adb3f00eb5209732a858bbbcda
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314671"
---
# <a name="identify-devices-as-corporate-owned"></a>Identifiera enheter som företagsägda

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Som Intune-administratör kan du förfina hanteringen och identifieringen genom att identifiera enheter som företagsägda. Intune kan utföra ytterligare hanteringsuppgifter och samla in ytterligare information, t.ex. telefonnummer och en inventering av appar från företagsägda enheter. Du kan också konfigurera enhetsbegränsningar för att förhindra registrering av enheter som inte är företagsägda.

Vid registreringen tilldelar Intune automatiskt statusen Företagsägd till enheter som har:

- Registrerad med ett [enhetsregistreringshanterar](device-enrollment-manager-enroll.md)-konto (alla plattformar)
- Registrerat med Apples [program för enhetsregistrering](device-enrollment-program-enroll-ios.md), [Apple School Manager](apple-school-manager-set-up-ios.md) eller [Apple Configurator](apple-configurator-enroll-ios.md) (endast iOS)
- [Identifierad som en företagsägd enhet innan registrering](#identify-corporate-owned-devices-with-imei-or-serial-number) med ett IMEI-nummer (alla plattformar med IMEI-nummer) eller serienummer (iOS och Android)
- Ansluten till Azure Active Directory med autentiseringsuppgifter för arbete eller skola. [Enheter som är Azure Active Directory-registrerade](https://docs.microsoft.com/azure/active-directory/devices/overview) kommer att markeras som personliga.
- Angetts som Företag i [enhetens egenskapslista](#change-device-ownership)

Efter registreringen kan du [ändra ägarskapsinställningen](#change-device-ownership) mellan **Personlig** och **Företag**.

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>Identifiera företagsägda enheter med IMEI- eller serienummer

Som Intune-administratör kan du skapa och importera en fil med kommateckenavgränsade värden (CSV) som innehåller en lista med 14-siffrigt IMEI- eller serienummer. Intune använder dessa identifierare för att ange att vissa enheter är företagsägda under enhetsregistreringen. Varje IMEI-nummer eller serienummer kan innehålla information som anges i listan för administrativa ändamål.

Den här funktionen stöds på följande plattformar:

| Plattform | IMEI-nummer | Serienummer |
|---|---|---|
| Windows | Stöds (Windows Phone) | Stöds inte |
| iOS/macOS | Stöds inte | Stöds |
| Enhetsadministratörhanterad Android OS-v10 | Stöds inte | Stöds inte |
| Annan Android | Stöds inte | Stöds |

<!-- When you upload serial numbers for corporate-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as corporate-owned. -->

[Lär dig hitta serienumret för en Apple-enhet](https://support.apple.com/HT204308).<br>
[Lär dig hitta serienumret för en Android-enhet](https://support.google.com/store/answer/3333000).

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>Lägga till företagsidentifierare med hjälp av en CSV-fil
För att skapa listan, skapar du en lista med kommateckenavgränsade fält (.csv) i två kolumner men utan rubrik. Lägg till 14-siffrigt IMEI-numren eller serienumren i den vänstra kolumnen och informationen i den högra kolumnen. Endast en typ av ID kan importeras till en CSV-fil, antingen IMEI-nummer eller serienummer. Informationen är begränsad till 128 tecken och används endast i administrationssyfte. Informationen visas inte på enheten. Den aktuella gränsen är 5 000 rader per CSV-fil.

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
> Vissa Android- och iOS-enheter har flera IMEI-nummer. Intune läser bara ett IMEI-nummer per registrerad enhet. Om du importerar ett IMEI-nummer som inte är det IMEI-nummer som är inventerat i Intune, kommer enheten att klassificeras som en personlig enhet i stället för en enhet som ägs av företaget. Om du importerar flera IMEI-nummer för en enhet så visas registreringsstatus för icke-inventerade nummer som **Okänt**.<br>
>Observera även: Serienummer är den rekommenderade identifieringsmetoden för iOS-enheter.
>Serienummer för Android är inte garanterat unika – de kanske inte ens finns. Hör efter med enhetens leverantören huruvida serienumret är ett tillförlitligt enhets-ID eller inte.
>Serienummer som rapporteras av enheten till Intune kanske inte matchar det ID som visas i menyerna Android-inställningar/Om på enheten. Kontrollera vilken typ av serienummer som rapporterats av tillverkaren av enheten.
>Vid försök att ladda upp en fil med serienummer som innehåller punkter (.) misslyckas överföringen. Serienummer med punkter stöds inte.

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>Ladda upp en CSV-lista med företagsidentifierare

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Sedan väljer du **Enhetsregistrering** > **ID:n för företagsenheter** > **Lägg till** > **Ladda upp CSV-fil**.

   ![Företagets arbetsyta med enhetsidentifierare och knappen Lägg till markerad](./media/corporate-identifiers-add/add-corp-id.png)

2. På bladet **Lägg till identifierare** anger du ID-typen: **IMEI** eller **Seriell**.

3. Klicka på mappikonen och ange sökvägen till listan du vill importera. Gå till CSV-filen och välj **Lägg till**. 

4. Om CSV-filen innehåller företagsidentifierare som redan finns i Intune, men som har olika detaljer, visas popup-fönstret **Granska dubbla identifierare**. Välj de identifierare som du vill skriva över i Intune och välj **OK** för att lägga till identifierarna. För varje identifierare jämförs endast den första dubbletten.

## <a name="manually-enter-corporate-identifiers"></a>Ange företagsidentifierare manuellt

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Sedan väljer du **Enhetsregistrering** > **ID:n för företagsenheter** > **Lägg till** > **Ange manuellt**.

2. På bladet **Lägg till identifierare** anger du ID-typen: **IMEI** eller **Seriell**.

3. Ange **Identifierare** och **Information** för varje identifierare som du vill lägga till. När du har angett identifierarna väljer du **Lägg till**.

5. Om du anger företagsidentifierare som redan finns i Intune, men som har olika detaljer, visas popup-fönstret **Granska dubbla identifierare**. Välj de identifierare som du vill skriva över i Intune och välj **OK** för att lägga till identifierarna. För varje identifierare jämförs endast den första dubbletten.

Du kan klicka på **Uppdatera** om du vill visa de nya ID:na.

Importerade enheter registreras inte nödvändigtvis. Enheterna kan antingen ha tillståndet **Registrerad** eller **Ej kontaktad**. **Ej kontaktad** innebär att enheten aldrig har kommunicerat med Intune-tjänsten.

## <a name="delete-corporate-identifiers"></a>Ta bort företagsidentifierare

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973). Sedan väljer du **Enhetsregistrering** > **ID:n för företagsenheter**.
2. Markera de enhetsid:n du vill ta bort och välj **Ta bort**.
3. Bekräfta borttagningen.

Om du tar bort en företags-id för en registrerad enhet ändras inte ägarskapet för enheten. Om du vill ändra ägarskapet för en enhet går du till **Enheter**, väljer enheten, väljer **Egenskaper** och ändrar **Ägarskap för enhet**.

## <a name="imei-specifications"></a>IMEI-specifikationer
Detaljerade specifikationer om IMEI (International Mobile Equipment Identifiers) finns i [3GGPP TS 23.003](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729).

## <a name="change-device-ownership"></a>Ändra enhetsägande

Enheters egenskaper visar **Ägarskap** för varje enhetspost i Intune. Som administratör kan du ange enheter som **Personliga** eller **Företagsägda**.

**Ändra enhetsägande:**
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), gå till **Enheter** och välj enheten.
2. Välj **Egenskaper**.
3. Ange **Äganderätt till enhet** som **Personlig** eller **Företagsägd**.

   ![Enhetsegenskaperna visar alternativ för Enhetskategori och Ägarskap för enhet](./media/corporate-identifiers-add/device-properties.png)
