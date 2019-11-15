---
title: Skapa enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller konfigurera en enhetskonfigurationsprofil i Microsoft Intune. Välj plattformstyp, konfigurera inställningarna och lägg till en omfångstagg.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51ec328a60ef2737c776bf6cf5d4b8dc1b32460c
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755309"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Skapa en enhetsprofil i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med enhetsprofiler kan du lägga till och konfigurera inställningar och sedan skicka dem till enheter i din organisation. [Tillämpa funktioner och inställningar på dina enheter med enhetsprofiler](device-profiles.md) innehåller mer information, inklusive vad du kan göra.

Den här artikeln:

- Se hur du skapar en profil.
- Visar hur du lägger till en omfångstagg för att ”filtrera” profilen.
- Beskriver tillämplighetsregler för Windows 10-enheter och visar hur du skapar en regel.
- Visar en lista med incheckningstider för uppdateringscykeln när enheterna tar emot profiler och eventuella profiluppdateringar.

## <a name="create-the-profile"></a>Skapa profilen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler**. Du kan välja mellan följande alternativ:

    - **Översikt**: Visar status för dina profiler och ytterligare information om de profiler som du har tilldelat till användare och enheter.
    - **Hantera**: Skapa enhetsprofiler, ladda upp anpassade [PowerShell-skript](../apps/intune-management-extension.md) att köra i profilen och lägg till dataplaner för enheter med hjälp av [eSIM](esim-device-configuration.md).
    - **Övervaka**: Kontrollera status för en profil och visa loggar för dina profiler.
    - **Installation**: Lägg till en SCEP- eller PFX-certifikatutfärdare eller aktivera [Kostnadsuppföljning av telekommunikation](telecom-expenses-monitor.md) i profilen.

3. Välj sedan **Skapa profil**. Ange följande egenskaper:

   - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett bra profilnamn är t.ex. **WP e-postprofil för hela företaget**.
   - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
   - **Plattform**: Välj plattform för dina enheter. Alternativen är:  

       - **Android**
       - **Android enterprise**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 och senare**
       - **Windows 10 och senare**

   - **Profiltyp**: Välj den typ av inställningar du vill skapa. Vilken lista som visas beror på vilken **plattform** du väljer.
   - **Inställningar**: Läs en beskrivning av inställningarna för varje profiltyp i följande artiklar:

       - [Administrativa mallar](administrative-templates-windows.md)
       - [Anpassad](../custom-settings-configure.md)
       - [Leveransoptimering](../delivery-optimization-windows.md)
       - [Enhetsfunktioner](../device-features-configure.md)
       - [Enhetsbegränsningar](device-restrictions-configure.md)
       - [Versionsuppgradering och lägesväxling](edition-upgrade-configure-windows-10.md)
       - [Utbildning](education-settings-configure.md)
       - [E-post](email-settings-configure.md)
       - [Slutpunktsskydd](../protect/endpoint-protection-configure.md)
       - [Identity Protection](../protect/identity-protection-configure.md)  
       - [Helskärmsläge](kiosk-settings.md)
       - [PKCS-certifikat](../protect/certficates-pfx-configure.md)
       - [PKCS-importerat certifikat](../protect/certificates-imported-pfx-configure.md)
       - [SCEP-certifikat](../protect/certificates-scep-configure.md)
       - [Betrott certifikat](../protect/certificates-configure.md)
       - [Uppdateringsprinciper](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows informationsskydd](../protect/windows-information-protection-configure.md)

     Om du till exempel väljer **iOS/iPadOS** som plattform, ser alternativen för profiltypen ut ungefär så här:

     ![Skapa iOS-profil i Intune](./media/device-profile-create/create-device-profile.png)

4. Välj **OK** > **Skapa** när du är klar för att spara dina ändringar. Profilen skapas och visas i listan.

## <a name="scope-tags"></a>Omfångstaggar

När du har lagt till inställningarna kan du också lägga till en omfångstagg i profilen. Omfångstaggar tilldelar och filtrerar principer till specifika grupper, till exempel Personal eller Alla amerikanska NC-anställda.

Mer information om omfångstaggar och vad du kan göra finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

### <a name="add-a-scope-tag"></a>Lägga till en omfångstagg

1. Välj **Omfång (taggar)** .
2. Välj **Lägg till** för att skapa en ny omfångstagg. Eller välj en befintlig omfångstagg i listan.
3. Klicka på **OK** för att spara ändringarna.

## <a name="applicability-rules"></a>Tillämpbarhetsregler

Gäller för:

- Windows 10 och senare

Med tillämplighetsregler kan administratörer rikta in sig på enheter i en grupp som uppfyller specifika villkor. Du kan till exempel skapa en profil för enhetsbegränsningar som gäller för gruppen **Alla Windows 10-enheter**. Och du vill att profilen endast ska tilldelas till enheter som kör Windows 10 Enterprise.

För att utföra den här åtgärden skapar du en **tillämpbarhetsregel**. Dessa regler är utmärkta för följande scenarier:

- Du använder Windows 10 Education (EDU). På universitetet Bellows College vill du sikta på alla Windows 10 EDU-enheter mellan RS3 och RS4.
- Du vill rikta in dig på alla användare i personalavdelningen på Contoso, men endast de enheter som kör Windows 10 Professional eller Enterprise.

För att du ska kunna nå dessa scenarier kan du:

- Skapa en enhetsgrupp som innehåller alla enheter på Bellows College. Lägg till en tillämplighetsregel i profilen så att den gäller om lägsta operativsystemversion är `16299` och den högsta versionen är `17134`. Tilldela den här profilen till enhetsgruppen Bellows College.

  När den är tilldelad gäller profilen för enheter mellan de lägsta och högsta versionerna som du anger. För enheter som inte är mellan de lägsta och högsta versionerna som du anger visas statusen som **Ej tillämpligt**.

- Skapa en användargrupp som omfattar alla användare i personalavdelningen (HR) på Contoso. Lägg till en tillämpbarhetsregel i profilen så att den gäller för enheter som kör Windows 10 Professional eller Enterprise. Tilldela den här profilen till gruppen HR-användare.

  När den är tilldelad tillämpas profilen på enheter som kör Windows 10 Professional eller Enterprise. För enheter som inte kör dessa versioner visas deras status som **Ej tillämpliga**.

- Om det finns två profiler med exakt samma inställningar tillämpas profilen utan en tillämplighetsregel. 

  Till exempel, ProfileA är riktad mot enhetsgruppen med Windows 10, aktiverar BitLocker och har inte någon tillämplighetsregel. ProfileB är riktad mot samma Windows 10-enhetsgrupp, aktiverar BitLocker och har en tillämplighetsregel för att endast tillämpa profilen på Windows 10 Enterprise.

  När båda profilerna tilldelas tillämpas ProfileA eftersom den inte har en tillämplighetsregel. 

När du tilldelar profilen till grupperna fungerar tillämplighetsreglerna som ett filter så att profilen endast tillämpas på de enheter som uppfyller dina kriterier.

### <a name="add-a-rule"></a>Lägg till en regel

1. Välj **Tillämpbarhetsregler**. Du kan välja **Regel**, **Egenskap** och **OS-utgåva**:

    ![Lägg till en tillämplighetsregel till en enhetskonfigurationsprofil i Microsoft Intune](./media/device-profile-create/applicability-rules.png)

2. I **Regel** väljer du om du vill inkludera eller exkludera användare eller grupper. Alternativen är:

    - **Tilldela profil om**: Innehåller användare eller grupper som uppfyller de kriterier som du anger.
    - **Tilldela inte en profil om**: Exkluderar användare eller grupper som uppfyller de kriterier som du anger.

3. I **Egenskap** väljer du ditt filter. Alternativen är: 

    - **Operativsystemutgåva**: I listan markerar du de Windows 10-versioner som du vill inkludera (eller exkludera) i din regel.
    - **Operativsystemversion**: Ange det **lägsta** och **högsta** versionnumret för Windows 10 som du vill inkludera (eller exkludera) i din regel. Båda värdena måste anges.

      Du kan till exempel ange `10.0.16299.0` (RS3 eller 1709) för lägsta version och `10.0.17134.0` (RS4 eller 1803) för högsta version. Eller så kan du vara mer ingående och ange `10.0.16299.001` för lägsta version och `10.0.17134.319` för högsta version.

4. Välj **Lägg till** för att spara dina ändringar.

## <a name="refresh-cycle-times"></a>Uppdatera cykeltider

Intune använder olika uppdateringscykler till att söka efter uppdateringar av konfigurationsprofiler. Om enheten nyligen har registrerats körs incheckningarna oftare. [Princip-och profil uppdaterings cykler](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) visar de uppskattade uppdateringstiderna.

Användarna kan när de vill öppna företagsportalappen och synkronisera enheten för att söka efter profiluppdateringar.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
