---
title: Inställningar för Windows Holographic for Business-enheter – Microsoft Intune – Azure | Microsoft Docs
description: Läs om och konfigurera inställningar för enhetsbegränsning i Microsoft Intune för Windows Holographic for Business, inklusive avregistrering, geoplats, lösenord, installation av appar från app store, cookies och popup-fönster i Microsoft Edge, Windows Defender, sökning, moln och lagring, Bluetooth-anslutning, systemtid och användningsdata i Azure.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 10efed6bf1f6017881618ac692a190e26b8df638
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734758"
---
# <a name="windows-holographic-for-business-device-settings-to-allow-or-restrict-features-using-intune"></a>Enhetsinställningarna för Windows Holographic for Business tillåter eller begränsar funktioner med hjälp av Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln beskriver de olika inställningar som du kan styra på Windows Holographic for Business-enheter, till exempel Microsoft Hololens. Använd inställningarna som en del av din lösning för hantering av mobilenheter, för att tillåta eller inaktivera funktioner, kontrollera säkerheten etc.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Allmänt

- **Manuell avregistrering**: Låter användaren ta bort sitt arbetsplatskonto från enheten manuellt.
- **Cortana**: Aktiverar eller inaktiverar röstassistenten Cortana.
- **Geoplats**: Anger om enheten kan använda information om platstjänster.

## <a name="password"></a>Lösenord

- **Lösenord**: Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
- **Kräv lösenord när enheten lämnar inaktivt läge**: Anger att användaren måste ange ett lösenord för att kunna låsa upp enheten.

## <a name="app-store"></a>Appbutik

- **Uppdatera appar automatiskt från Store**: Appar som installeras från Microsoft Store uppdateras automatiskt.
- **Installation av betrodd app**: Appar som signeras med ett betrott certifikat läses in separat.
- **Lås upp via utvecklare**: Tillåter Windows utvecklarinställningar, till exempel att separat inlästa appar ska kunna ändras av användaren.

## <a name="microsoft-edge-browser"></a>Microsoft Edge-webbläsaren

- **Cookies**: Gör att webbläsaren sparar Internetcookies på enheten.
- **Popup-fönster**: Blockerar popup-fönster i webbläsaren (gäller endast Windows 10 Desktop).
- **Sökförslag**: Tillåter att din sökmotor föreslår webbplatser när du skriver sökfraser.
- **Lösenordshanteraren**: Aktivera eller inaktivera lösenordshanteraren för Microsoft Edge.
- **Skicka Do Not Track-huvuden**: Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **SmartScreen för Microsoft Edge**: Aktivera Microsoft Edge SmartScreen för åtkomst till webbplats och filnedladdningar.

## <a name="search"></a>Sök

- **Sök plats** – Ange om platsinformation får användas i sökning. information

## <a name="cloud-and-storage"></a>Moln och lagring

- **Microsoft-konto**: Låter användaren associera ett Microsoft-konto med enheten.

## <a name="cellular-and-connectivity"></a>Mobilnät och anslutning

- **Bluetooth**: Styr om användaren kan aktivera och konfigurera Bluetooth på enheten.
- **Bluetooth-identifiering**: Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.
- **Bluetooth-annonsering**: Låter enheten ta emot annonser via Bluetooth.

## <a name="control-panel-and-settings"></a>Kontrollpanel och inställningar

- **Ändra systemtid**: Förhindrar att slutanvändaren ändrar enhetens datum och tid.

## <a name="kiosk---obsolete"></a>Kiosk – föråldrad

De här inställningarna är skrivskyddade och kan inte ändras. Om du vill konfigurera helskärmsläge kan du läsa mer i [Kioskinställningar](kiosk-settings-holographic.md).

En helskärmslägesenhet kör vanligtvis en viss app. Användarna kommer inte åt funktioner på enheten utanför helskärmslägesappen.

- **Helskärmsläge**: Identifierar den typ av helskärmsläge som stöds av principen. Alternativen är:

  - **Inte konfigurerad** (standard): Den här principen aktiverar inte ett kioskläge. 
  - **Helskärmsläge för enskilda appar**: Profilen gör att enheten endast kan köra en app. Appen startas när användaren loggar in. Det här läget gör också att användaren inte kan öppna nya appar eller ändra appen som körs.
  - **Helskärmsläge för flera appar**: Profilen gör att enheten kan köra flera appar. Endast de appar som du lägger till är tillgängliga för användaren. Med helskärmsläge för flera appar skapas en mer användarvänlig upplevelse för användarna eftersom de endast ser de appar de behöver. Och de appar användarna inte behöver tas bort från deras vy. 
  
    När du lägger till appar för helskärmsläge för flera appar måste du också lägga till en layoutfil för startmenyn. [Layoutfilen för startmenyn](/hololens/hololens-kiosk#start-layout-file-for-mdm-intune-and-others) innehåller exempel-XML som kan användas i Intune. 

### <a name="single-app-kiosks"></a>Helskärmsläge för enskilda appar

Ange följande inställningar:

- **Användarkonto**: Ange det lokala (för enheten) användarkontot eller den Azure AD-kontoinloggning som associeras med helskärmsappen. För konton som är kopplade till Azure AD-domäner ska kontot anges i formatet `domain\username@tenant.org`. 

    Om helskärmsapparna finns i en miljö som riktar sig till allmänheten ska automatisk inloggning vara aktiverat och en användartyp med minsta privilegier (till exempel ett lokalt standardanvändarkonto) användas. Om du konfigurerar ett Azure Active Directory-konto (AD) för helskärmsläge använder du formatet `AzureAD\user@contoso.com`.

- **Appens programanvändarmodell-ID (AUMID)** : Ange AUMID för helskärmsappen. Läs mer i [Find the Application User Model ID of an installed app](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app) (Hitta programanvändarmodell-ID för en installerad app).

## <a name="reporting-and-telemetry"></a>Rapportering och telemetri

- **Dela användningsdata**: Välj nivå av diagnostikdata som skickas.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
