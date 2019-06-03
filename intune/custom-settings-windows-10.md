---
title: Lägga till anpassade inställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en anpassad profil för att använda OMA-URI-inställningarna för enheter som kör Windows 10 i Microsoft Intune. Använd en anpassad profil för att lägga till anpassade inställningar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9d07b2d46e5128d96a578e9a000e17c2aca7cec
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373974"
---
# <a name="use-custom-settings-for-windows-10-devices-in-intune"></a>Använda anpassade inställningar för Windows 10-enheter i Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina Windows 10-enheter med hjälp av ”anpassade profiler”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

Anpassade profiler i Windows 10 använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera olika funktioner. De här inställningarna används vanligtvis av tillverkare av mobila enheter till att styra funktioner på enheten. 

I Windows 10 finns flera CSP-inställningar (Configuration Service Provider), t.ex. [Princip-CSP (Policy Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Glöm inte att [enhetsbegränsningsprofilen i Windows 10](device-restrictions-windows-10.md) innehåller många inbyggda inställningar som du kan använda. Det betyder att du kanske inte behöver ange anpassade värden.

Den här artikeln:

- Beskriver hur du skapar en anpassad profil för Windows 10-enheter
- Innehåller en lista med rekommenderade OMA-URI-inställningar
- Innehåller ett exempel på en anpassad profil som öppnar en VPN-anslutning

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `windows 10 custom profile`.
    - **Beskrivning:** Ange en beskrivning för profilen.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
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

I följande exempel är inställningen **Connectivity/AllowVPNOverCellular** aktiverad. Med den här inställningen kan en Windows 10-enhet öppna en VPN-anslutning vid användning av ett mobilnät.

![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Hitta principer som du kan konfigurera

Du hittar en lista med alla konfigurationstjänstleverantörer (CSP) som Windows 10 har stöd för i [referensen till konfigurationstjänstleverantörer](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I [referensen till konfigurationstjänstleverantörer](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) står det vilka versioner som stöds för varje CSP.

Observera att Intune inte stöder alla inställningar i [referensen för konfigurationstjänstleverantörer](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference). Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Add** (Lägg till), **Replace** (Ersätt) och **Get** (Hämta). Om det värde som returneras av åtgärden **Get** (Hämta) inte matchar det värde som anges av åtgärderna **Add** (Lägg till) eller **Replace** (Ersätt) rapporterar Intune ett efterlevnadsfel.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).
