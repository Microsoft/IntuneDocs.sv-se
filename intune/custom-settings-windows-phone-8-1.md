---
title: Lägga till anpassade inställningar för Windows Phone 8.1-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till eller skapa en anpassad profil för att använda OMA-URI-inställningarna för enheter som kör Windows Phone 8.1 i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97d656db3e828ef3377b927395a283fe995bb8a4
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389283"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Använda anpassade inställningar för Windows Phone 8.1-enheter i Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina Windows Phone 8.1-enheter med hjälp av ”anpassade profiler”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

Anpassade profiler i Windows Phone 8.1 använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera olika funktioner. De här inställningarna används vanligtvis av tillverkare av mobila enheter till att styra funktioner på enheten. [Windows Phone 8.1 MDM dokumenterad protokoll](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) visas inställningarna.

Den här artikeln visar hur du skapar en anpassad profil för Windows Phone 8.1-enheter. 

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `windows phone custom profile`.
    - **Beskrivning:** Ange en beskrivning för profilen.
    - **Plattform**: Välj **Windows Phone 8.1**.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen och eventuell annan relevant information som gör det enklare att hitta profilen.
    - **OMA-URI** (skiftlägeskänsligt): Ange den OMA-URI som du vill använda som inställning.
    - **Datatyp**: Välj den datatyp som du vill använda för den här OMA-URI-inställningen. Alternativen är:

        - Sträng
        - Sträng (XML-fil)
        - Datum och tid
        - Heltal
        - Flyttal
        - Boolesk
        - Base64 (fil)

    - **Värde**: Ange det datavärde som du vill associera med den OMA-URI som du har angett. Värdet beror på vilken datatyp du valt. Om du till exempel valde **Datum och tid**, väljer du värdet från en datumväljare.

    När du har lagt till några inställningar kan du välja **Exportera**. **Exportera** skapar en lista över alla värden som du har lagt till i en fil med kommaavgränsade värden (.csv).

5. Klicka på **OK** för att spara ändringarna. Fortsätt att lägga till fler inställningar efter behov.
6. När du är klar väljer du **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.

## <a name="example"></a>Exempel

I följande exempel hindras Windows 8.1 phone-enheter från att ändra mobila nätverk utanför täckning operatör.

- **Namn på**: Tillåt mobildata Roaming
- **Beskrivning av**: Tillåt eller Tillåt inte roaming av mobildata
- **OMA-URI** (skiftlägeskänsligt): ./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Datatyp**: heltal
- **Värde**: 0

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).

Se hur du skapar en anpassad profil på [Windows 10-enheter](custom-settings-windows-10.md).
