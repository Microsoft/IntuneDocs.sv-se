---
title: Anpassade inställningar i Microsoft Intune för enheter som kör Windows 10
titlesuffix: ''
description: Läs om anpassade inställningar som du kan konfigurera i en anpassad Windows 10-profil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 36705c49a55c88c41470feaad14520e900dcb3dd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Anpassade inställningar i Microsoft Intune för enheter som kör Windows 10

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 finns flera CSP-inställningar (Configuration Service Provider), t.ex. [Princip-CSP (Policy Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Kom ihåg att om du letar efter en viss inställning, innehåller [enhetsbegränsningsprofilen i Windows 10](device-restrictions-windows-10.md) många inställningar som är inbyggda i Intune och som innebär att du inte behöver ange några anpassade värden.

## <a name="configure-custom-settings"></a>Konfigurera anpassade inställningar

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
1. I fönstret **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
1. Ange följande information för varje OMA-URI-inställning som du vill lägga till. Använd listan i den här artikeln om du vill veta mer om vilka inställningar du kan använda:
    - **Namn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Inställning** – Ange en beskrivning för inställningen (valfritt).
    - **OMA-URI (skiftlägeskänslig)** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Datatyp** – Välj bland:
        - **Sträng**
        - **Sträng (XML)**
        - **Datum och tid**
        - **Heltal**
        - **Flyttal**
        - **Boolesk**
        - **Base64**
    - **Värde** – Ange det värde eller den fil som ska associeras med den OMA-URI som du har angett.
1. När du är klar väljer du **OK**, går tillbaka till fönstret **Skapa profil** och väljer **Skapa**.
Profilen skapas och visas i fönstret med profillistan.

## <a name="example"></a>Exempel
I följande skärmbild har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en lista med alla CSP:er som har stöd för Windows 10 i [Referens till CSP (Configuration Service Provider)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) i dokumentationsbiblioteket för Windows.

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I tabellen i Windows-artikeln visas vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i artikeln. Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.
