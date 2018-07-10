---
title: Anpassade inställningar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera anpassade OMA-URI-inställningar på enheter som kör Windows 10 med en anpassad profil i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bdbb6643a4ee8aace0db22cd7f9189f7ac6445f0
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36232834"
---
# <a name="custom-oma-uri-settings-for-windows-10-devices---intune"></a>Anpassade OMA-URI-inställningar för Windows 10-enheter – Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd Microsoft Intunes **anpassade** profil för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier). De här inställningarna används för att styra funktioner på enheter. I Windows 10 finns flera CSP-inställningar (Configuration Service Provider), t.ex. [Princip-CSP (Policy Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

Kom ihåg att om du letar efter en specifik inställning så innehåller [enhetsbegränsningsprofilen i Windows 10](device-restrictions-windows-10.md) många inställningar som är inbyggda i Intune och inte kräver anpassade värden.

## <a name="configure-custom-settings"></a>Konfigurera anpassade inställningar

1. Skapa en ny konfigurationsprofil med hjälp av profiltypen **Anpassad**. Stegen finns i [Konfigurera anpassade enhetsinställningar](custom-settings-configure.md).
2. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till** för att skapa en ny inställning. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
3. Ange följande information för varje OMA-URI-inställning som du vill lägga till:

- **Namn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
- **Beskrivning** – Ange en beskrivning för inställningen (valfritt).
- **OMA-URI (skiftlägeskänslig)**: Ange den OMA-URI som du vill tillhandahålla en inställning för.
- **Datatyp**: Välj bland:
  - **Sträng**
  - **Sträng (XML)**
  - **Datum och tid**
  - **Heltal**
  - **Flyttal**
  - **Boolesk**
  - **Base64**
- **Värde**: Ange det värde eller den fil som du vill associera med den OMA-URI som du har angett.

4. När du är klar väljer du **OK**. I **Skapa profil** väljer du **Skapa**. Profilen skapas och visas i profillistan.

## <a name="example"></a>Exempel
I följande exempel är inställningen **Connectivity/AllowVPNOverCellular** aktiverad. Med den här inställningen kan en Windows 10-enhet öppna en VPN-anslutning vid användning av ett mobilnät.

![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)

## <a name="find-the-policies-you-can-configure"></a>Hitta principer som du kan konfigurera

Du hittar en lista med alla konfigurationstjänstleverantörer (CSP) som Windows 10 har stöd för i [referensen till konfigurationstjänstleverantörer](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference).

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I [referensen till konfigurationstjänstleverantörer](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) står det vilka versioner som stöds för varje CSP.

Dessutom stödjer Intune inte alla inställningar som anges. Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.
