---
title: "Principinställningar för Windows 10 |Microsoft Intune"
description: "Använd principinställningarna som anges i det här avsnittet om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b8522406a3c73746b09616c3ec917464cf751312
ms.openlocfilehash: 6e482beb5e2edce648ecb6f1821baa6214fa0f2f


---

# Intune-principinställningar för Windows 10-enheter i Microsoft Intune

Det här avsnittet innehåller information om de Intune-principinställningar som du kan använda för att hantera Windows 10-enheter. Läs det här avsnittet och metoderna i [Hantera inställningar och funktioner i enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter. Du kan inte använda dessa principer för datorer som kör [Intune-klientprogrammet](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Du kan välja mellan två principtyper:

- **Anpassad princip** – Använd Microsoft Intunes **anpassade princip** för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 är många inställningar tillgängliga via [Princip-CSP (Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Allmän konfigurationspolicy** – Använd den här principtypen när du vill välja inställningar från den inbyggda listan som medföljer Microsoft Intune.

## Anpassade principinställningar

Ange följande inställningar i en anpassad princip:

## &nbsp;&nbsp;&nbsp;Allmänt

Ange ett namn, och eventuellt en beskrivning, för principen så att du kan identifiera den i Intune-konsolen.

## &nbsp;&nbsp;&nbsp;OMA-URI-inställningar

Ange följande information för varje OMA-URI-inställning som du vill lägga till. Läs [URI-inställningar för Windows 10](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) i det här avsnittet om du vill veta mer om vilka inställningar du kan använda: 

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

### Exempel
I skärmbilden nedan har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)

## URI-inställningar för Windows 10
I det här avsnittet kan du läsa mer om OMA-URI-inställningar som du kan konfigurera med en **anpassad princip för Windows 10**.

## &nbsp;&nbsp;&nbsp;Princip

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt automatiskt uppdatering**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Endast Desktop<br>**Datatyp:** heltal<br />**Värden:** **0** - **5** (standard: **1**)|
|**Schema installationsdag**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Endast Mobile<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – Varje dag (standard)<br>**1** – Söndag<br>**2** – Måndag<br>**3** – Tisdag<br>**4** – Onsdag<br>**5** – Torsdag<br>**6** – Fredag<br>**7** – Lördag|
|**Schema installationstid**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – **23** timmar (**0** är midnatt) (standard: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – användaren kan inte ange respittiden för lösenordet, värdet ställs in som ”varje gång”<br>**1** – användaren kan ställa in respittiden för lösenordet (standard)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – **Tillåt inte Wi-Fi-anslutning**.<br>**1** –**Tillåt användning av Wi-Fi-anslutning** (standard)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Desktop och Mobile<br>**Datatyp:** heltal<br />**Värden:** **0** – Tillåt inte Internetdelning, **1** – Tillåt Internetdelning (standard)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Ingen Wi-Fi-anslutning utanför etablerad MDM är tillåtet.<br>**1** – Att lägga till nya SSID:er för nätverket utöver de som MDM redan har tillhandahållit tillåts (standard)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Desktop och Mobile<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – Inte tillåten (endast Enterprise inställningar)<br>**1** – Begränsad<br>**2** – Fullständig (standard)<br>**3** – Fullständig information och diagnostikinformation|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inte tillåten<br>**1** – Endast inställningar (standard)<br>**2** – Inställningar och experiment|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte antistöldläge<br>**1** Användarpreferenser (standard)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – VPN är inte tillåtet över mobilnät<br>**1** – VPN kan använda alla anslutningar inklusive mobil anslutning (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte att användaren aktiverar Bluetooth.<br>**1** – Reserverad. Användaren kan aktivera och konfigurera Bluetooth (stöds inte i Windows Phone 8.1 för MDM, EAS, Windows 10 Desktop eller Windows 10 Mobile)<br>**2** – Tillåts. Användaren kan aktivera och konfigurera Bluetooth (standard)|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåt inte roaming, **1** – Tillåt roaming (standard)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**, **1** (standard)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**, **1** (standard)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** (standard), **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – tillåt inte<br>Öppen utökad ordbok är avstängd.<br>En användare kan inte:<br>-Lägga till en ny utökad ordbok<br />-Lägga till en ny sökningsintegrerad konfigurationsfil<br>-Använd molnkandidatfunktionen<br>-Skicka användarregistrerat ord.<br>**1** – Tillåt<br>Öppen utökad ordbok kan läggas till och användas som standard. Dessutom kan integrationsfunktionssökningen användas som standard.<br>En användare kan:<br>Använda molnkandidatfunktionen.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Loggning av felkonverteringar är inaktiverat.<br>**1** – Loggning av felkonverteringar är aktiverat (standard).|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS-skifttecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br />**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken och EUDC-tecken filtreras|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Strikt, högsta filtrering mot vuxet innehåll<br>**1** – Måttlig, måttlig filtrering mot vuxet innehåll (giltiga sökresultat filtreras inte – standard)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**Forcerad startstorlek**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – tillåt användaren att ändra storlek (standard)<br>**1** – Framtvinga skärm som inte är helskärm<br>**2** – Framtvinga helskärm|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0**: skjut inte upp uppgradering (stanna i aktuell gren, CB – standard)<br>**1**: Aktivera uppdateringar och uppgraderingar som ska skjutas upp (enheten följer aktuell företagsgren, CBB, regler)<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Desktop och Mobile<br>**Beskrivning:** Princip för att skjuta upp programuppdateringar i upp till fyra veckor<br />**Datatyp:** heltal<br />**Värden:**<br> **0**: Tillämpa uppdateringar direkt (standard)<br>**1**-**4**: antal veckor som programvaruuppdateringarna ska skjutas upp.<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Desktop och Mobile<br>**Beskrivning:** Princip för att skjuta upp funktionsuppgraderingar i upp till åtta månader<br />**Datatyp:** heltal<br />**Värden:**<br>**0**: Tillämpa uppdateringar direkt (standard)<br>**1**-**8**: antal månader som funktionsuppgraderingar ska skjutas upp.<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Desktop och Mobile<br>**Beskrivning:** Tillåter att en enheter slutar få uppdateringar och uppgraderingar i fem veckor.<br />**Datatyp:** heltal<br />**Värden:**<br>**0**: Tillämpa uppdateringar direkt (standard)<br>**1**: Pausa uppdateringar och uppgraderingar (upphör att gälla efter 5 veckor)|

## &nbsp;&nbsp;&nbsp;Windows försvarare

|Principnamn och URI|Information|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Övervaka alla filer (standard)<br>**1** – Övervaka inkommande filer<br>**2** – Övervaka utgående filer|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** - **90** – Visar hur länge skadlig programvara kommer att hållas kvar<br>**Standard:** **0** – bevarar i karantänmappen för evigt, och tar inte bort automatiskt|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**1** – Snabbsökning (standard)<br>**2** – Full scanning|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Varje dag (standard)<br>**1** – Måndag<br>**2** – Tisdag<br>**3** – Onsdag<br>**4** – Torsdag<br>**5** – Fredag<br>**6** – Lördag<br>**7** – Söndag<br>**8** – Ingen schemalagd scanning|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1381** – Underhållsfönster|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Endast Desktop<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1380** – 11:00 pm|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** - **100** (standard: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Endast Desktop<br />**Datatyp:** heltal<br>**Värden:** **0** – Tillåts inte (standard), **1** – Tillåts|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte (standard), **1** – Tillåts|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte, **1** – Tillåts (s) – Körs även när RTP är aktiverad när den är inställd på tillåten|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Kontrollera inte signaturer i ett intervall<br>**1** – Kontrollera om signaturer finns varje timme<br>**2** – Kontrollera varannan timme etc.<br>**24** – Kontrollera varje dag<br>**Standardvärde:** 8 – Kontrollera var åttonde timme|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåts inte **1** – Tillåts (standard)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Fråga alltid (default)<br>**1** – Skicka säkra prover automatiskt<br>**2** – Skicka aldrig<br>**3** – Skicka alla prover automatiskt|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br>*&lt;lista över tillägg avgränsade med semikolon&gt;* Exempel: **obj;lib**<br>**Standard:** Inga tillägg utesluts|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br />*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br />Exempel: **c:\test;c:\test1.exe**<br />**Standardvärde:** Inga sökvägar utesluts|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br>*&lt;lista över sökvägar avgränsade med semikolon&gt;*<br>Exempel: **c:\test.exe;c:\test1.exe**<br>**Standardvärde:** Inga processer utesluts|

## &nbsp;&nbsp;&nbsp;Edge-webbläsare

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt webbläsare**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**: Surfning av, **1**: Surfning på (standard)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**: Visa inte förslag, **1**: Visa förslag (standard)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0**: Inaktiverad (öppna intranätsplatser i Microsoft Edge-webbläsare – standard)<br>**1** – Aktiverad (öppna intranätsplatser i Internet Explorer).|
|**Tillåt Do Not Track**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop och Mobile)<br />**Datatyp:** heltal<br />**Värden:** **0** – Inaktiverat (DNT skickas inte, standard), **1** – Aktiverat (DNT skickas)|
|**Konfigurera SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåt inte, **1** – Tillåt (standard)|
|**Tillåt popup-fönster**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Blockera popup-fönster (standard), **1** – Tillåt poup-fönster|
|**Tillåt cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt cookies från alla webbplatser (standard)<br>**1** – Blockera endast cookies från tredje part<br>**2** – Blockera alla cookies|
|**Tillåt att spara lösenord**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Lösenordshanteraren är inaktiverad; <br>**1** – Lösenordshanteraren är aktiverad (standard)|
|**Tillåt autofyll**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Inaktiverat (standard), **1** – Aktiverat|
|**Konfigurera företagswebbplatslista**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:<br>**0** – Inte konfigurerat<br>**1** – Använd webbplatslista för företagsläge i IE om konfigurerat (standard)<br>**2** – Ange plats för webbplatslista för företagsläge|

## Generella inställningar för konfigurationsprinciper

Använd den **allmänna konfigurationsprincipen** för Windows Intune för Windows 10 om du vill konfigurera inbyggda inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter. 

## &nbsp;&nbsp;&nbsp;Lösenord

|Inställningsnamn|Ytterligare information (där det behövs)|
|----------------|----------------------|
|**Kräv ett lösenord för att låsa upp enheter**|-|
|**Lösenordstyp krävs**|Anger om lösenordet måste vara endast numeriskt eller om det kan vara alfanumeriskt|
|**Krav på lösenordstyp** - **Minsta antal teckenuppsättningar**|Det finns fyra teckenuppsättningar: gemena bokstäver, versala bokstäver, siffror och symboler. Den här inställningen anger hur många av dessa teckenuppsättningar som lösenordet måste innehålla.|
|**Minsta längd på lösenord**|Gäller endast för Windows 10 Mobile|
|**Antal tillåtna, upprepad felinloggningar innan enheten rensas**|För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten placeras den i återställningsläget för BitLocker efter den gräns för antal misslyckade inloggningar som du har angett. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.<br>För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses.|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur lång tid enhetens lösenord måste ändras.|
|**Kom ihåg tidigare lösenord**|Anger om du vill hindra användaren från att återanvända tidigare lösenord.|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Anger hur många tidigare använda lösenord som sparas av enheten.|
|**Kräv lösenord när enheten återgår från viloläge**|Om den här inställningen är aktiverad måste användaren ange ett lösenord för att låsa upp enheten. (endast Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;Kryptering

|Inställningsnamn|Ytterligare information (där det behövs)|
|----------------|----------------------|
|**Filkryptering på mobil enhet**|Aktivera kryptering på målenheter.<br>(endast Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;System

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt skärmbild**|Låter användaren fånga enhetens skärm som en bild. (endast Windows 10 Mobile)|
|**Tillåt manuell avregistrering**|Tillåter att användaren manuellt raderar sitt arbetsplatskonto från enheten.|
|**Tillåt manuell installation av rotcertifikat**|Gäller för Windows 10 Mobile|
|**Tillåt att diagnostik- och användardata skickas till Microsoft**|Möjliga värden är:<br><br>**Nej** – Inga data skickas till Microsoft<br>**Grundläggande** – Begränsad information skickas till Microsoft<br>**Utökad** – Utökade diagnostikdata skickas till Microsoft<br>**Fullständig (rekommenderas)** –Skickar samma data som **Utökad**, plus ytterligare information om enhetens tillstånd|


## &nbsp;&nbsp;&nbsp;Konto och synkronisering

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt Microsoft-konto**|Låter användaren associera ett Microsoft-konto med enheten.|
|**Tillåt att lägga till icke-Microsoft konton manuellt**|Låter användaren lägga till e-postkonton till enheten som inte är associerade med ett Microsoft-konto.|
|**Tillåt synkronisering av inställningar för Microsoft-konton**|Tillåt att enhets- och appinställningar som associeras med ett Microsoft-konto synkroniseras mellan enheter.|

## &nbsp;&nbsp;&nbsp;Microsoft Edge

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt webbläsare**|Tillåt användningen av Microsoft Edge-webbläsaren på enheten.<br>(endast Windows 10 Mobile)|
|**Tillåt sökförslag i adressfältet**|Tillåter att din sökmotor föreslår platser när du skriver sökord.|
|**Tillåt att intranättrafik skickas till Internet Explorer**|Tillåter att användarna öppnar intranätsplatser i Internet Explorer.<br>(endast Windows 10 Desktop)|
|**Tillåt spåra inte**|Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker.|
|**Aktivera SmartScreen**|-|
|**Tillåt active scripting**|Tillåter att skript, t.ex. JavaScript, körs i Microsoft Edge-webbläsaren.|
|**Tillåt popup-fönster**|Gäller endast för Windows 10 Desktop|
|**Tillåt cookies**|-|
|**Tillåt autofyll**|Tillåt att användarna ändrar inställningarna för Komplettera automatiskt i webbläsaren.<br>(endast Windows 10 Desktop)|
|**Tillåt lösenordshanteraren**|Aktivera eller inaktivera lösenordshanteraren för Microsoft Edge.|
|**Listplats för Företagsläge-webbplats**|Anger var man hittar listan över webbsidor som öppnar i Enterprise-läge. Användare kan inte redigera den här listan.<br>(endast Windows 10 Desktop)|

## &nbsp;&nbsp;&nbsp;Appar

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt appbutik**|Gäller endast för Windows 10 Mobile|



## &nbsp;&nbsp;&nbsp;Mobilnät

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt dataroaming**|Tillåt växling mellan nätverk vid åtkomst till data.|
|**Tillåt VPN via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar när den är ansluten till ett mobilnät.|
|**Tillåt VPN-roaming via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar vid roaming i ett mobilnät.|

## &nbsp;&nbsp;&nbsp;Maskinvara

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt kamera**|-|
|**Tillåt flyttbara lagringsenheter**|Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.|
|**Tillåt Wi-Fi**|Gäller endast för Windows 10 Mobile|
|**Tillåt internetdelning**|Tillåt användningen av Internetanslutningsdelning på enheten.|
|**Tillåt manuell Wi-Fi konfiguration**|Styr huruvida användarna kan konfigurera egna trådlösa anslutningar eller om de endast kan använda anslutningar som konfigurerats med en Wi-Fi-profil.<br>(endast Windows 10 Mobile)|
|**Tillåt automatisk anslutning till kostnadsfria, trådlösa surfpunkter**|Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den godkänner eventuella villkor för anslutningen automatiskt.|
|**Tillåt geolokalisering**|Anger om enheten kan använda tjänsterna för platsinformation.|
|**Tillåt NFC**|Tillåter att enheten använder funktioner för närfältskommunikation.|
|**Tillåt Bluetooth**|-|
|**Tillåt att Bluetooth kan hittas**|Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.|
|**Tillåt Bluetoothreklam**|Tillåter att enheter tar emot reklam via Bluetooth.|
|**Tillåt telefonåterställning**|Styr huruvida användaren kan fabriksåterställa enheten.|
|**Tillåt USB-anslutning**|Styr huruvida enheter kan komma åt externa lagringsenheter via en USB-anslutning.|
|**Tillåt AntiTheft läge**|Konfigurera om Windows Antitheft läge är aktiverat.|

## &nbsp;&nbsp;&nbsp;Funktioner

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt kopiera och klistra in**|Gäller endast för Windows 10 Mobile|
|**Tillåt röstinspelning**|Gäller endast för Windows 10 Mobile|
|**Tillåt Cortana**|Aktivera eller inaktivera röstassistenten Cortana.|
|**Tillåt action center meddelanden**|Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm.<br>(endast Windows 10 Mobile)|

## &nbsp;&nbsp;&nbsp;Windows försvarare

Alla inställningar gäller endast Windows 10 Desktop.

|Inställningsnamn|Ytterligare information (om det behövs)|
|-|-|
|**Tillåt realtidsövervakning**|Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara.|
|**Tillåt beteendeövervakning**|Tillåter att Defender söker efter kända mönster på misstänkt aktivitet på enheter.|
|**Aktivera system för nätverksinspektion**|Kontrollsystemet för nätverk (NIS) hjälper till att skydda enheter mot nätverksbaserade kryphål genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik.|
|**Skanna alla hämtningar**|Kontrollerar om Defender söker igenom alla filer som hämtas från Internet.|
|**Tillåt skriptgenomsökning**|Tillåter att Defender genomsöker skript som används i Internet Explorer.|
|**Övervaka fil- och programaktivitet**|Aktivera den här inställningen om du vill att Defender ska övervaka fil- och programaktivitet på enheter.|
|**Dagar som löst skadlig kod ska spåras**|Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger så att du kan kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt. |
|**Tillåt användargränssnittåtkomst för klient**|Styr huruvida Windows Defender-användargränssnittet är dolt från slutanvändarna.<br>Om den här inställningen ändras börjar den gälla nästa gång slutanvändarens dator startas om.|
|**Schemalägg en snabb daglig genomgång**|Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer.|
|**Schemalägg en systemsökning**|Tillåter att du schemalägger en fullständig sökning eller en snabbsökning som körs regelbundet på den dag och vid den tidpunkt som du väljer.|
|**Begränsa CPU-användning under en skanning**|Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**)|
|**Skanna arkivfiler**|Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.|
|**Skanna e-postmeddelanden**|Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten.|
|**Skanna flyttbara enheter**|Tillåter att Defender söker igenom flyttbara enheter, t.ex. USB-minnen.|
|**Skanna mappade nätverksenheter**|Tillåter att Defender söker igenom filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Skanna filer som har öppnats från delade nätverksmappar**|Tillåter att Defender söker igenom filer på delade nätverksenheter, till exempel de som nås från en UNC-sökväg.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Intervall för signaturuppdatering**|Ange med vilket intervall som Defender ska söka efter nya signaturfiler.|
|**Tillåt molnskydd**|Tillåt eller förhindra att Microsoft Active Protection Service tar emot information om skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.|
|**Be användarna att skicka exempel**|Styr huruvida filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft.|
|**Identifiering av potentiellt oönskade program**|Du kan använda den här inställningen för att skydda registrerade Windows-skrivbordsenheter från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats.|
|**Filer och mappar som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera filer och mappar som **C:\Sökväg** eller **%ProgramFiles%\Sökväg\filnamn.exe** i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Filändelser som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till ett eller flera filnamnstillägg som **jpg** eller **txt** i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Processer som ska undantas när du kör en skanning eller använder realtidsskydd**|Lägg till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. De här processerna tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.| 


## &nbsp;&nbsp;&nbsp;Updates

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|---------------|
|**Tillåt automatiska uppdateringar**|Aktivera den här inställningen för att tillåta automatiska uppdateringar. Konfigurera sedan någon av följande inställningar för att kontrollera uppdateringsbeteende:<br />**Meddela om hämtning**<br />**Automatisk installation vid underhållstidpunkt**<br />**Automatisk installation och omstart vid underhållstidpunkt**<br />**Installera automatiskt och starta om enligt schema****Obs!** Om det här alternativet har valts kan du också konfigurera följande inställningar: **Meddela inte slutanvändare** och **Definiera installationsdag för schemalagda uppdateringar**.<br>(endast Windows 10 Desktop)|
|**Tillåt förhandsfunktioner**|Låter Microsoft distribuera förhandsversionsinställningar och -funktioner till Windows 10-enheter. Du kan välja att tillåta att endast inställningar eller alla förhandsversionsinställningar och -funktioner installeras.|

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)





<!--HONumber=Oct16_HO1-->


