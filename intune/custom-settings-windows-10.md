---
title: "Anpassade inställningar i Microsoft Intune för enheter som kör Windows 10"
titlesuffix: 
description: "Läs om anpassade inställningar som du kan konfigurera i en anpassad Windows 10-profil."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 156d37874529b4ae5a8176d7e9a8873cf440c32c
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-10"></a>Anpassade inställningar i Microsoft Intune för enheter som kör Windows 10 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 finns flera CSP-inställningar (Configuration Service Provider), t.ex. [Princip-CSP (Policy Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Kom ihåg att om du letar efter en viss inställning, innehåller [enhetsbegränsningsprofilen i Windows 10](device-restrictions-windows-10.md) många inställningar som är inbyggda i Intune och som innebär att du inte behöver ange några anpassade värden.

## <a name="configure-custom-settings"></a>Konfigurera anpassade inställningar

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. På sidan **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På sidan **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
4. Ange följande information för varje OMA-URI-inställning som du vill lägga till. Använd listan i den här artikeln om du vill veta mer om vilka inställningar du kan använda:
    - **Inställningsnamn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Inställningsbeskrivning** – Ange en beskrivning för inställningen.
    - **Datatyp** – Välj bland:
        - **Sträng**
        - **Sträng (XML)**
        - **Datum och tid**
        - **Heltal**
        - **Flyttal**
        - **Boolesk**
    - **OMA-URI (skiftlägeskänslig)** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Värde** – Ange det värde som ska associeras med den OMA-URI som du har angett.
5. När du är klar går du tillbaka till sidan **Skapa profil** och trycker på **Skapa**.
Profilen skapas och visas på sidan med profillistan.

## <a name="example"></a>Exempel
I skärmbilden nedan har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en lista med alla CSP:er som har stöd för Windows 10 i [Referens till CSP (Configuration Service Provider)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) i dokumentationsbiblioteket för Windows.

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I tabellen i artikeln om Windows kan du se vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i artikeln. Om du vill veta om Intune har stöd för den inställning som du vill använda, öppnar du artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.


