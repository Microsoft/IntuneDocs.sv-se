---
title: Skapa enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller konfigurera en enhetskonfigurationsprofil i Microsoft Intune. Välj plattformstyp, konfigurera inställningarna och lägg till en omfångstagg.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570409"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Skapa en enhetsprofil i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Med enhetsprofiler kan du lägga till och konfigurera inställningar och sedan skicka dem till enheter i din organisation. [Tillämpa funktioner och inställningar på dina enheter med enhetsprofiler](device-profiles.md) innehåller mer information, inklusive vad du kan göra.

Den här artikeln:

- Se hur du skapar en profil.
- Visar hur du lägger till en omfångstagg för att ”filtrera” profilen.
- Visar en lista med incheckningstider för uppdateringscykeln när enheterna tar emot profiler och eventuella profiluppdateringar.

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.

2. Välj **Enhetskonfiguration**. Du kan välja mellan följande alternativ:

    - **Översikt**: Visar status för dina profiler och ytterligare information om de profiler som du har tilldelat till användare och enheter.
    - **Hantera**: Skapa enhetsprofiler, ladda upp anpassade [PowerShell-skript](intune-management-extension.md) att köra i profilen och lägg till dataplaner för enheter med hjälp av [eSIM](esim-device-configuration.md).
    - **Övervaka**: Kontrollera status för en profil och visa loggar för dina profiler.
    - **Installation**: Lägg till en SCEP- eller PFX-certifikatutfärdare eller aktivera [Kostnadsuppföljning av telekommunikation](telecom-expenses-monitor.md) i profilen.

3. Välj **Profiler** > **Skapa profil**. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett bra profilnamn är t.ex. **WP e-postprofil för hela företaget**.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj plattform för dina enheter. Alternativen är:  

       - **Android**
       - **Android enterprise**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 och senare**
       - **Windows 10 och senare**

   - **Profiltyp**: Välj den typ av inställningar du vill skapa. Vilken lista som visas beror på vilken **plattform** du väljer.
   - **Inställningar**: Läs en beskrivning av inställningarna för varje profiltyp i följande artiklar:

       - [Administrativa mallar](administrative-templates-windows.md)
       - [Anpassad](custom-settings-configure.md)
       - [Leveransoptimering](delivery-optimization-windows.md)
       - [Enhetsfunktioner](device-features-configure.md)
       - [Enhetsbegränsningar](device-restrictions-configure.md)
       - [Versionsuppgradering och lägesväxling](edition-upgrade-configure-windows-10.md)
       - [Utbildning](education-settings-configure.md)
       - [E-post](email-settings-configure.md)
       - [Slutpunktsskydd](endpoint-protection-configure.md)
       - [Identity Protection](identity-protection-configure.md)  
       - [Helskärmsläge](kiosk-settings.md)
       - [PKCS-certifikat](certficates-pfx-configure.md)
       - [SCEP-certifikat](certificates-scep-configure.md)
       - [Betrott certifikat](certificates-configure.md)
       - [Uppdateringsprinciper](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows informationsskydd](windows-information-protection-configure.md)

     Om du till exempel väljer **iOS** som plattform, ser alternativen för profiltypen ut ungefär så här:

     ![Skapa iOS-profil i Intune](./media/create-device-profile.png)

4. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar. Profilen skapas och visas i listan.

## <a name="scope-tags"></a>Omfångstaggar

När du har lagt till inställningarna kan du också lägga till en omfångstagg i profilen. Omfångstaggar tilldelar och filtrerar principer till specifika grupper, till exempel Personal eller Alla amerikanska NC-anställda.

Mer information om omfångstaggar och vad du kan göra finns i [Använda RBAC och omfångstaggar för distribuerad IT](scope-tags.md).

### <a name="add-a-scope-tag"></a>Lägga till en omfångstagg

1. Välj **Omfång (taggar)**.
2. Välj **Lägg till** för att skapa en ny omfångstagg. Eller välj en befintlig omfångstagg i listan.
3. Klicka på **OK** för att spara ändringarna.

## <a name="refresh-cycle-times"></a>Uppdatera cykeltider

Intune använder följande uppdateringscykler till att söka efter uppdateringar av konfigurationsprofiler:

| Plattform | Uppdateringscykel|
| --- | --- |
| iOS | Var 6:e timme |
| macOS | Var 6:e timme |
| Android | Var 8:e timme |
| Windows 10-datorer som registrerats som enheter | Var 8:e timme |
| Windows Phone | Var 8:e timme |
| Windows 8,1 | Var 8:e timme |

Om enheten nyligen har registrerats körs incheckningarna oftare:

| Plattform | Frekvens |
| --- | --- |
| iOS | Var 15:e minut i 6 timmar och därefter var 6:e timme |  
| macOS | Var 15:e minut i 6 timmar och därefter var 6:e timme | 
| Android | Var 3:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme | 
| Windows 10-datorer som registrerats som enheter | Var 3:e minut i 30 minuter och därefter var 8:e timme | 
| Windows Phone | Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme | 
| Windows 8,1 | Var 5:e minut i 15 minuter, därefter var 15:e minut i 2 timmar och sedan var 8:e timme | 

Användarna kan när de vill öppna företagsportalappen och synkronisera enheten för att söka efter profiluppdateringar.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
