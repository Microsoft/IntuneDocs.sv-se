---
title: Lägga till anpassade inställningar för Windows Phone 8.1-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till eller skapa en anpassad profil för att använda OMA-URI-inställningarna för enheter som kör Windows Phone 8.1 i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ed1f43e7c7e6f0580cb22513a489fb32c30e5f6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206762"
---
# <a name="use-custom-settings-for-windows-phone-81-devices-in-intune"></a>Använda anpassade inställningar för Windows Phone 8.1-enheter i Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina Windows Phone 8.1-enheter med hjälp av ”anpassade profiler”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

Anpassade profiler i Windows Phone 8.1 använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera olika funktioner. De här inställningarna används vanligtvis av tillverkare av mobila enheter till att styra funktioner på enheten. [Windows Phone 8,1 MDM Protocol-dokumentationen](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-phone/dn499787(v=technet.10)) visar inställningarna.

Den här artikeln visar hur du skapar en anpassad profil för Windows Phone 8.1-enheter. 

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett användbart profil namn är till exempel **Windows Phone-anpassad profil**.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
    - **Plattform**: välj **Windows Phone 8,1**.
    - **Profil typ**: Välj **anpassad**.

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen och eventuell annan relevant information som gör det enklare att hitta profilen.
    - **OMA-URI** (skiftlägeskänslig): Ange den OMA-URI som du vill använda som inställning.
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

I följande exempel hindras Windows 8,1 Phone-enheter från att ändra mobila nätverk när de reser utanför området för bär Vågs täckning.

- **Namn**: Tillåt mobil data nätverks växling
- **Beskrivning**: Tillåt eller neka mobil data nätverks växling
- **OMA-URI** (Skift läges känslig):./Vendor/MSFT/PolicyManager/My/Connectivity/AllowCellularDataRoaming
- **Datatyp**: Heltal
- **Värde**: 0

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Skapa en anpassad profil på [Windows 10-enheter](../custom-settings-windows-10.md).
