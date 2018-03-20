---
title: "Begränsningsinställningar för Microsoft Intune-enheter i Windows Holographic for Business"
titleSuffix: 
description: "Läs om de Intune-inställningar du kan använda för att styra enhetsinställningar och funktioner på enheter som kör Windows Holographic for Business-enheter."
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9acce571330a754de85b65caf8ec71912fd36a69
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="microsoft-intune-windows-holographic-for-business-device-restriction-settings"></a>Inställningar för begränsningar för Windows Holographic for Business-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Följande begränsningsinställningar för enheter har stöd för enheter som kör Windows Holographic for Business, som till exempel Microsoft Hololens.

## <a name="general"></a>Allmänt

- **Manuell avregistrering** – Tillåter att användaren manuellt tar bort sitt arbetsplatskonto från enheten.
- **Cortana** – Aktivera eller inaktivera röstassistenten Cortana.
- **Geoplats** – Anger om enheten kan använda information om platstjänster.



## <a name="password"></a>Lösenord
-   **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Kräv lösenord när enheten lämnar inaktivt läge** – Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten.



## <a name="app-store"></a>Appbutik

-   **Uppdatera appar automatiskt från Store** – Appar som installeras från Microsoft Store uppdateras automatiskt.
-   **Installation av betrodd app** – Appar som signeras med ett betrott certifikat läses in separat.
-   **Lås upp via utvecklare** – Tillåter Windows utvecklarinställningar, till exempel att separat inlästa appar ska kunna ändras av användaren.

## <a name="edge-browser"></a>Microsoft Edge-webbläsare

-   **Microsoft Edge-webbläsare** – Tillåt användning av Edge-webbläsaren på enheten.
-   **Cookies** – Gör att webbläsaren sparar Internetcookies på enheten.
-   **Popup-fönster** – Blockerar popup-fönster i webbläsaren (gäller endast Windows 10 Desktop).
-   **Sökförslag** – Tillåter att din sökmotor föreslår webbplatser när du skriver sökfraser.
-   **Lösenordshanteraren** – Aktivera eller inaktivera lösenordshanteraren för Microsoft Edge.
- **Skicka Do Not Track-huvuden** – Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen för Microsoft Edge** – Aktivera Edge SmartScreen för att komma åt plats och filhämtningar.

## <a name="search"></a>Sök
- **Sök plats** – Ange om platsinformation får användas i sökning. information


## <a name="cloud-and-storage"></a>Moln och lagring
-   **Microsoft-konto** – Låter användaren associera ett Microsoft-konto med enheten.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

-   **Bluetooth** – Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
-   **Bluetooth-identifiering** – Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
-   **Bluetooth-annonsering** – Låter enheten ta emot annonser via Bluetooth.

## <a name="control-panel-and-settings"></a>Kontrollpanel och inställningar

- **Ändra systemtid** – Förhindrar att användaren ändrar enhetens datum och tid.

## <a name="reporting-and-telemetry"></a>Rapportering och telemetri

- **Dela användningsdata** – Välj nivå av diagnostikdata.