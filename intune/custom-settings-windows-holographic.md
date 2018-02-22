---
title: "Anpassade Intune-inställningar för Windows Holographic for Business-enheter"
titlesuffix: Azure portal
description: "Läs om inställningarna som du kan använda i en anpassad Windows Holographic for Business-profil.”"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 1/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ae46aef10ca294637a4d433ce273d3c53e695d64
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2018
---
# <a name="custom-device-settings-for-windows-holographic-for-business-devices-in-microsoft-intune"></a>Anpassade enhetsinställningar för Windows Holographic for Business-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows Holographic for Business för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. Windows Holographic for Business gör många inställningar för konfigurationstjänstleverantörer tillgängliga. En översikt över CSP finns i [Introduction to configuration service providers (CSPs) for IT pros](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) (Introduktion till konfigurationstjänstleverantörer (CSP:er) för IT-proffs). Specifika CSP:er som stöds av Windows Holographic visas i [CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic).

Kom ihåg att om du letar efter en viss inställning så innehåller [enhetsbegränsningsprofilen i Windows Holographic for Business](device-restrictions-windows-holographic.md) många inställningar som är inbyggda och som innebär att du inte behöver ange några anpassade värden.

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. På bladet **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På bladet **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
4. Ange följande information för varje OMA-URI-inställning som du vill lägga till. Använd listan i det här avsnittet om du vill veta mer om vilka inställningar du kan använda:
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
5. När du är klar, går du tillbaka till bladet **skapa profil** och trycker på **skapa**.
Profilen skapas och visas på bladet med profillistan.

## <a name="supported-custom-settings"></a>Anpassade inställningar som stöds

Windows Holographic for Business har stöd för följande anpassade inställningar:


|Inställningsnamn|OMA-URI|Datatyp  |
|---------|---------|---------|
|AllowFastReconnect     |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Heltal (0 – Tillåts inte 1 – Tillåts)|
|AllowVPN     |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Heltal (0 – Tillåts inte 1 – Tillåts)|



## <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en fullständig lista över alla konfigurationstjänstleverantörer (CSP:er) som Windows Holographic har stöd för i [CSPs supported in Windows Holographic](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic). Alla inställningar är inte kompatibla med alla versioner av Windows Holographic. I tabellen i avsnittet om Windows kan du se vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i avsnittet. Om du vill veta om Intune har stöd för den inställning som du vill använda, öppnar du avsnittet för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.


