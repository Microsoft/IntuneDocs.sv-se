---
title: Enhetsbegränsningar för Windows Holographic for Business i Microsoft Intune – Azure | Microsoft Docs
description: Läs om och konfigurera inställningar för enhetsbegränsning i Microsoft Intune för Windows Holographic for Business, inklusive avregistrering, geoplats, lösenord, installation av appar från app store, cookies och popup-fönster i Edge, Windows Defender, sökning, moln och lagring , bluetooth-anslutning, systemtid och användningsdata i Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/9/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5b0784aeb1dc1022b4be824c2f858f9525d03918
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="device-restriction-settings-for-windows-holographic-for-business-in-intune"></a>Inställningar för enhetsbegränsningar för Windows Holographic for Business i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

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

## <a name="kiosk-preview"></a>Helskärmsläge (förhandsgranskning)

En helskärmslägesenhet kör vanligtvis en viss app. Användarna kommer inte åt funktioner på enheten utanför helskärmslägesappen.

- **Helskärmsläge** – Identifierar vilken typ av helskärmsläge som stöds av principen. Alternativen är:

  - **Inte konfigurerad** (standard) – Principen aktiverar inte ett helskärmsläge. 
  - **Läget för enskilda appar för kiosk** – Profilen gör att enheten endast kan köra en app. Appen startas när användaren loggar in. Det här läget gör också att användaren inte kan öppna nya appar eller ändra appen som körs.

#### <a name="single-app-kiosks"></a>Läget för enskilda appar för kiosk
Ange följande inställningar:

- **Användarkonto** – Ange det lokala (för enheten) användarkontot eller den Azure AD-kontoinloggning som är associerad med kioskappen. För konton som är kopplade till Azure AD-domäner ska kontot anges i formatet `domain\username@tenant.org`. 

    Om kiosken finns i en miljö som riktar sig till allmänheten ska automatisk inloggning vara aktiverat och en användartyp med minsta privilegier (till exempel ett lokalt standardanvändarkonto) användas. Om du konfigurerar ett Azure Active Directory-konto (AD) för helskärmsläge använder du formatet `AzureAD\user@contoso.com`.

- **Appens programanvändarmodell-ID (AUMID)** – Ange AUMID för kioskappen. Läs mer i [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Hitta programanvändarmodell-ID för en installerad app).

## <a name="reporting-and-telemetry"></a>Rapportering och telemetri

- **Dela användningsdata** – Välj nivå av diagnostikdata.