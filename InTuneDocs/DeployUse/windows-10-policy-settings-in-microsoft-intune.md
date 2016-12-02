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
ms.sourcegitcommit: ad36bfd7b4f60626181ecaf27c51a9b108005979
ms.openlocfilehash: 8c970a4d1362def67e17da656b5e12e5bab2667b


---

# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Intune-principinställningar för Windows 10-enheter i Microsoft Intune

Det här avsnittet innehåller information om de Intune-principinställningar som du kan använda för att hantera Windows 10-enheter. Läs det här avsnittet och metoderna i [Hantera inställningar och funktioner på enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) om du vill konfigurera inbyggda och anpassade inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter. Du kan inte använda dessa principer för datorer som kör [Intune-klientprogrammet](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune).

Du kan välja mellan två principtyper:

- **Anpassad princip**: Använd Microsoft Intunes **anpassade princip** för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 är många inställningar tillgängliga via [Princip-CSP (Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Allmän konfigurationspolicy**: Använd den här principtypen om du vill välja inställningar från den inbyggda listan som medföljer Microsoft Intune.

## <a name="custom-policy-settings"></a>Anpassade principinställningar

Ange följande inställningar i en anpassad princip.

### <a name="general"></a>Allmänt

Ange ett namn, och eventuellt en beskrivning, för principen så att du kan identifiera den i Intune-konsolen.

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

Ange följande information för varje OMA-URI-inställning som du vill lägga till. Läs [URI-inställningar för Windows 10](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) i det här avsnittet om du vill veta mer om vilka inställningar du kan använda:

- **Inställningsnamn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
- **Inställningsbeskrivning**: Ange en beskrivning för inställningen.
- **Datatyp**: Välj från följande datatyper:
    - **Sträng**
    - **Sträng (XML)**
    - **Datum och tid**
    - **Heltal**
    - **Flyttal**
    - **Boolesk**
- **OMA-URI (skiftlägeskänslig)**: Ange den OMA-URI som du vill tillhandahålla en inställning för.
- **Värde**: Ange det värde som ska associeras med den OMA-URI som du har angett.

### <a name="example"></a>Exempel
I följande skärmbild har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)

## <a name="windows-10-uri-settings"></a>URI-inställningar för Windows 10
I det här avsnittet kan du läsa mer om OMA-URI-inställningar som du kan konfigurera med en **anpassad princip för Windows 10**.

### <a name="policy"></a>Princip

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt automatiskt uppdatering**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Endast Desktop<br>**Datatyp:** heltal<br />**Värden:** **0** - **5** (standard: **1**)|
|**Schemalägg installationsdag**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Endast Mobile<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – Varje dag (standard)<br>**1** – Söndag<br>**2** – Måndag<br>**3** – Tisdag<br>**4** – Onsdag<br>**5** – Torsdag<br>**6** – Fredag<br>**7** – Lördag|
|**Schemalägg installationstid**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0**–**23** timmar (**0** är midnatt) (standard: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Användaren kan inte ange respittiden för lösenordet, värdet ställs in som ”varje gång”<br>**1** – Användaren kan ställa in respittiden för lösenordet (standard)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte **användning av Wi-Fi-anslutning**<br>**1** – Tillåt **användning av Wi-Fi-anslutning** (standard)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|Desktop och Mobile<br>**Datatyp:** heltal<br />**Värden:<br>** **0** – Tillåt inte internetdelning <br> **1** – Tillåt internetdelning (standard)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt endast Wi-Fi-anslutningar som du konfigurerar med MDM.<br>**1** – Tillåt att lägga till nya SSID för nätverk utöver de SSID som redan har skapats av en MDM (standard)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|Desktop och Mobile<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåts inte (endast Enterprise-inställningar)<br>**1** – Begränsad<br>**2** – Fullständig (standard)<br>**3** – Fullständig information och diagnostikinformation|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inte tillåten<br>**1** – Endast inställningar (standard)<br>**2** – Inställningar och experiment|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte stöldskyddsläge<br>**1** – Användarpreferenser (standard)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|Endast Mobile<br />**Datatyp:** heltal<br />**Värden<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br>**1** – Tillåtet (standard)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – VPN är inte tillåtet över mobilnät<br>**1** – VPN kan använda alla anslutningar inklusive mobil anslutning (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte att användaren aktiverar Bluetooth.<br>**1** – Reserverad. Användaren kan aktivera och konfigurera Bluetooth (stöds inte i Windows Phone 8.1 för MDM, EAS, Windows 10 Desktop eller Windows 10 Mobile).<br>**2** – Tillåts. Användaren kan aktivera och konfigurera Bluetooth (standard).|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Tillåt inte roaming<br> **1** – Tillåt roaming (standard)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** (standard)<br> **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0**<br> **1** (standard)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** (standard)<br> **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** (standard)<br> **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** (standard)<br> **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0**<br> **1** (standard)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br> **0** (standard)<br> **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** (standard)<br> **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt inte.<br>Öppen utökad ordbok är avstängd.<br>En användare kan inte:<br>- Lägga till en ny öppen utökad ordbok.<br />- Lägga till en ny konfigurationsfil för sökintegration.<br>- Använd molnkandidatfunktionen.<br>-Skicka användarregistrerat ord.<br>**1** – Tillåt<br>Öppen utökad ordbok kan läggas till och användas som standard. Dessutom kan integrationsfunktionssökningen användas som standard.<br>En användare kan:<br>- Använd molnkandidatfunktionen.|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Loggning av felkonverteringar är inaktiverat<br>**1** – Loggning av felkonverteringar är aktiverat (standard).|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten <br>**1** – Tillåtet (standard)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS-skifttecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br />**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken filtreras|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inga tecken filtreras (standard)<br>**1** – Alla tecken utom JIS0208-tecken och EUDC-tecken filtreras|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|Endast Desktop<br />**Datatyp:** heltal<br />**Värden<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Strikt, högsta filtrering mot vuxet innehåll<br>**1** – Måttlig filtrering av vuxeninnehåll (giltiga sökresultat filtreras inte) (standard)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**Forcerad startstorlek**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt användaren att ändra storlek (standard)<br>**1** – Framtvinga skärm som inte är helskärm<br>**2** – Framtvinga helskärm|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Skjut inte upp uppgradering (stanna i aktuell gren, CB) (standard)<br>**1** – Tillåt att uppdateringar och uppgraderingar skjuts upp (enheten följer aktuell gren för företag, CBB, regler)<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|Desktop och Mobile<br>**Beskrivning:** Princip för att skjuta upp programuppdateringar i upp till fyra veckor<br />**Datatyp:** heltal<br />**Värden:**<br> **0** – Tillämpa uppdateringar direkt (standard)<br>**1**-**4** – Antal veckor som programvaruuppdateringarna ska skjutas upp<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|Desktop och Mobile<br>**Beskrivning:** Princip för att skjuta upp funktionsuppgraderingar i upp till åtta månader<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillämpa uppdateringar direkt (standard)<br>**1**-**8** – Antal månader som funktionsuppgraderingar ska skjutas upp<br />Mer information finns i:<br>[Introduktion till Windows 10-installation](https://technet.microsoft.com/library/mt598226.aspx)<br>[Planera för distribution av Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|Desktop och Mobile<br>**Beskrivning:** Tillåter att en enheter slutar få uppdateringar och uppgraderingar i fem veckor.<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillämpa uppdateringar direkt (standard)<br>**1** – Pausa uppdateringar och uppgraderingar (upphör att gälla efter fem veckor)|

### <a name="windows-defender"></a>Windows försvarare

|Principnamn och URI|Information|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br> **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Övervaka alla filer (standard)<br>**1** – Övervaka inkommande filer<br>**2** – Övervaka utgående filer|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** - **90** – Visar hur länge skadlig programvara kommer att hållas kvar<br>**0** – Behåller skadlig kod i karantänmappen för alltid och tar inte bort den automatiskt (standard)|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**1** – Snabbsökning (standard)<br>**2** – Full scanning|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Varje dag (standard)<br>**1** – Måndag<br>**2** – Tisdag<br>**3** – Onsdag<br>**4** – Torsdag<br>**5** – Fredag<br>**6** – Lördag<br>**7** – Söndag<br>**8** – Ingen schemalagd scanning|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1381** – Underhållsfönster|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|Endast Desktop<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – 12:00 am<br>**60** – 1:00 am<br>**120** – 02:00 (standard)<br>**180** – 3:00 am<br>**240** – 4:00 am<br>**300** – 5:00 am<br>**360** – 6:00 am<br>**420** – 7:00 am<br>**480** – 8:00 am<br>**540** – 9:00 am<br>**600** – 10:00 am<br>**660** – 11:00 am<br>**720** – 12:00 pm<br>**780** – 1:00 pm<br>**840** – 2:00 pm<br>**900** – 3:00 pm<br>**960** – 4:00 pm<br>**1020** – 5:00 pm<br>**1080** – 6:00 pm<br>**1140** – 7:00 pm<br>**1200** – 8:00 pm<br>**1260** – 9:00 pm<br>**1320** – 10:00 pm<br>**1380** – 11:00 pm|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** - **100** (standard: **50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|Endast Desktop<br />**Datatyp:** heltal<br>**Värden:<br>** **0** – Tillåts inte (standard)<br> **1** – Tillåten|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Tillåts inte (standard)<br> **1** – Tillåten|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåten (standard) – Körs även när RTP är aktiverad om den är inställd på tillåten|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Kontrollera inte signaturer i ett intervall<br>**1** – Kontrollera om signaturer finns varje timme<br>**2** – Kontrollera varannan timme <br>**24** – Kontrollera varje dag<br>**8** – Kontrollera var åttonde timme (standard)|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inte tillåten<br> **1** – Tillåtet (standard)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Fråga alltid (default)<br>**1** – Skicka säkra prover automatiskt<br>**2** – Skicka aldrig<br>**3** – Skicka alla prover automatiskt|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br>*&lt;Lista över tillägg avgränsade med semikolon&gt;* Exempel: **obj;lib**<br>**Standard –** Inga tillägg utesluts|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br />*&lt;Lista över sökvägar avgränsade med semikolon&gt;*<br />Exempel: **c:\test;c:\test1.exe**<br />**Standard –** Inga sökvägar utesluts|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br>*&lt;Lista över sökvägar avgränsade med semikolon&gt;*<br>Exempel: **c:\test.exe;c:\test1.exe**<br>**Standard –** Inga processer utesluts|

### <a name="edge-browser"></a>Edge-webbläsare

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt webbläsare**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Webbsökning inaktiverat <br>**1** – Webbsökning aktiverat (standard)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Visa inte förslag<br> **1** – Visa förslag (standard)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Inaktiverad (öppna intranätsplatser i Microsoft Edge-webbläsare – standard)<br>**1** – Aktiverad (öppna intranätsplatser i Internet Explorer)|
|**Tillåt Spåra inte**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop och Mobile)<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Inaktiverad (DNT skickas inte (standard))<br> **1** – Aktiverad (skicka DNT)|
|**Konfigurera SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Tillåt inte<br> **1** – Tillåt (standard)|
|**Tillåt popup-fönster**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:<br>** **0** – Blockera popup-fönster (standard)<br> **1** – Tillåt popup-fönster|
|**Tillåt cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt cookies från alla webbplatser (standard)<br>**1** – Blockera endast cookies från tredje part<br>**2** – Blockera alla cookies|
|**Tillåt att spara lösenord**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Lösenordshanteraren är inaktiverad <br>**1** – Lösenordshanteraren är aktiverad (standard)|
|**Tillåt autofyll**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Endast Desktop<br />**Datatyp:** heltal<br />**Värden**:<br> **0** – Inaktiverad (standard)<br> **1** – Aktiverad|
|**Konfigurera företagswebbplatslista**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:**<br>**0** – Inte konfigurerat<br>**1** – Använd Internet Explorers webbplatslista för företagsläge om den är konfigurerad (standard)<br>**2** – Ange plats för företagswebbplatslista|

## <a name="general-configuration-policy-settings"></a>Generella inställningar för konfigurationsprinciper

Använd den **allmänna konfigurationsprincipen** för Windows Intune för Windows 10 om du vill konfigurera inbyggda inställningar för registrerade Windows 10 Desktop- och Windows 10 Mobile-enheter.

### <a name="password"></a>Lösenord

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Kräv ett lösenord för att låsa upp enheter**|-|
|**Lösenordstyp krävs**|Anger om lösenordet måste vara alfanumeriskt eller endast numeriskt|
|**Krav på lösenordstyp** - **Minsta antal teckenuppsättningar**| Anger hur många teckenuppsättningar (gemener, versaler, siffror och symboler) som måste ingå i lösenordet|
|**Minsta längd på lösenord**|Gäller endast för Windows 10 Mobile|
|**Antal tillåtna, upprepade felinloggningar innan enheten rensas**.|För enheter som kör Windows 10: Om BitLocker är aktiverat på enheten placeras den i återställningsläget för BitLocker efter den gräns för antal misslyckade inloggningar som du har angett. Om BitLocker inte är aktiverat på enheten tillämpas inte den här inställningen.<br>För enheter som kör Windows 10 Mobile: Om inloggningen misslyckas ett visst antal gånger (som du angett) rensas enheten.|
|**Antal minuter av inaktivitet innan skärmen stängs av**|Anger hur lång tid en enhet måste vara inaktiv innan skärmen låses|
|**Lösenordets giltighetstid (i dagar)**|Anger efter hur lång tid enhetens lösenord måste ändras|
|**Kom ihåg tidigare lösenord**|Anger om du vill förhindra att användaren återanvänder tidigare använda lösenord|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Anger antalet tidigare använda lösenord som enheten sparar|
|**Kräv lösenord när enheten återgår från viloläge**|Anger att användaren måste ange ett lösenord för att låsa upp enheten (endast Windows 10 Mobile)|

### <a name="encryption"></a>Kryptering

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Filkryptering på mobil enhet**|Aktiverar kryptering på målenheter<br>(endast Windows 10 Mobile)|

### <a name="system"></a>System

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt skärmbild**|Användaren kan ta en skärmbild av enhetens skärm (endast Windows 10 Mobile)|
|**Tillåt manuell avregistrering**|Tillåter att användaren manuellt raderar sitt arbetsplatskonto från enheten|
|**Tillåt manuell installation av rotcertifikat**|Gäller för Windows 10 Mobile|
|**Tillåt att diagnostik- och användardata skickas till Microsoft**|Möjliga värden är:<br><br>**Nej** – Inga data skickas till Microsoft<br>**Grundläggande** – Begränsad information skickas till Microsoft<br>**Utökad** – Utökade diagnostikdata skickas till Microsoft<br>**Fullständig (rekommenderas)** –Skickar samma data som **Utökad**, plus ytterligare information om enhetens tillstånd|


### <a name="account-and-synchronization"></a>Konto och synkronisering

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt Microsoft-konto**|Låter användaren associera ett Microsoft-konto med enheten|
|**Tillåt att andra konton än Microsoft-konton får läggas till manuellt**|Låter användaren lägga till e-postkonton till enheten som inte är associerade med ett Microsoft-konto|
|**Tillåt synkronisering av inställningar för Microsoft-konton**|Tillåt att enhets- och appinställningar som associeras med ett Microsoft-konto synkroniseras mellan enheter|

### <a name="microsoft-edge"></a>Microsoft Edge

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt webbläsare**|Tillåter användningen av Microsoft Edge-webbläsaren på enheten<br>(endast Windows 10 Mobile)|
|**Tillåt sökförslag i adressfältet**|Tillåter att din sökmotor föreslår platser när du skriver sökord|
|**Tillåt att intranättrafik skickas till Internet Explorer**|Tillåter att användarna öppnar intranätsplatser i Internet Explorer<br>(endast Windows 10 Desktop)|
|**Tillåt Spåra inte**|Konfigurerar Microsoft Edge-webbläsaren så att Do Not Track-huvuden skickas till webbplatser som användarna besöker|
|**Aktivera SmartScreen**||
|**Tillåt Active scripting**|Tillåter att skript (exempelvis JavaScript) körs i webbläsaren Edge|
|**Tillåt popup-fönster**|Gäller endast för Windows 10 Desktop|
|**Tillåt cookies**||
|**Tillåt autofyll**|Tillåter att användarna kan ändra inställningarna för att automatiskt komplettera i webbläsaren<br>(endast Windows 10 Desktop)|
|**Tillåt lösenordshanteraren**|Aktiverar eller inaktiverar lösenordshanteraren i Edge|
|**Listplats för Företagsläge-webbplats**|Anger var du hittar listan över webbsidor som öppnas i Enterprise-läge. Användare kan inte redigera den här listan.<br>(endast Windows 10 Desktop)|

### <a name="apps"></a>Appar

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt appbutik**|Gäller endast för Windows 10 Mobile|



### <a name="cellular"></a>Mobilnät

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåter datanätverksväxling**|Tillåt växling mellan nätverk vid åtkomst till data.|
|**Tillåt VPN via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar när den är ansluten till ett mobilnät.|
|**Tillåt VPN-roaming via mobilnät**|Styr huruvida enheten kan komma åt VPN-anslutningar vid roaming i ett mobilnät.|

### <a name="hardware"></a>Maskinvara

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|
|**Tillåt kamera**|-|
|**Tillåt flyttbara lagringsmedier**|Anger om externa lagringsenheter, till exempel ett SD-kort, kan användas med enheten.|
|**Tillåt Wi-Fi**|Gäller endast för Windows 10 Mobile|
|**Tillåt internetdelning**|Tillåter användningen av internetanslutningsdelning på enheten|
|**Tillåt manuell Wi-Fi konfiguration**|Styr huruvida användarna kan konfigurera egna trådlösa anslutningar eller om de endast kan använda anslutningar som konfigurerats med en Wi-Fi-profil.<br>(endast Windows 10 Mobile)|
|**Tillåt automatisk anslutning till kostnadsfria trådlösa surfzoner**|Tillåter att enheten ansluter automatiskt till kostnadsfria trådlösa surfzoner och att den godkänner eventuella villkor för anslutningen automatiskt.|
|**Tillåt geolokalisering**|Anger om enheten kan använda tjänsterna för platsinformation.|
|**Tillåt NFC**|Tillåter att enheten använder funktioner för närfältskommunikation.|
|**Tillåt Bluetooth**|-|
|**Tillåt läge för identifierbart Bluetooth**|Tillåter att enheten kan upptäckas av andra Bluetooth-aktiverade enheter.|
|**Tillåt Bluetoothreklam**|Tillåter att enheter tar emot meddelanden via Bluetooth.|
|**Tillåt telefonåterställning**|Styr om användaren kan göra en fabriksåterställning på enheten eller inte|
|**Tillåt USB-anslutning**|Styr huruvida enheter kan komma åt externa lagringsenheter via en USB-anslutning.|
|**Tillåt AntiTheft läge**|Ange om stöldskyddsläge i Windows är aktiverat|

### <a name="features"></a>Funktioner

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt kopiera och klistra in**|Gäller endast för Windows 10 Mobile|
|**Tillåt röstinspelning**|Gäller endast för Windows 10 Mobile|
|**Tillåt Cortana**|Aktivera eller inaktivera röstassistenten Cortana.|
|**Tillåt action center meddelanden**|Aktivera eller inaktivera aviseringar från Åtgärdscenter på enhetens låsskärm.<br>(endast Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows försvarare

Alla inställningar gäller endast Windows 10 Desktop.

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|----------------------|---------------------|
|**Tillåt realtidsövervakning**|Tillåter genomsökning i realtid efter skadlig programvara, spionprogram och annan oönskad programvara|
|**Tillåt beteendeövervakning**|Tillåter att Defender söker efter kända mönster på misstänkt aktivitet på enheter|
|**Aktivera kontrollsystem för nätverk**|Kontrollsystemet för nätverk (NIS) hjälper till att skydda enheter mot nätverksbaserade kryphål genom att använda signaturerna för kända säkerhetsrisker från Microsoft Endpoint Protection Center för att identifiera och blockera skadlig trafik|
|**Sök igenom alla hämtningar**|Kontrollerar om Defender söker igenom alla filer som hämtas från Internet|
|**Tillåt skriptgenomsökning**|Tillåter att Defender genomsöker skript som används i Internet Explorer|
|**Övervaka fil- och programaktivitet**|Tillåter att Defender övervakar fil- och programaktivitet på enheter|
|**Dagar som löst skadlig kod ska spåras**|Tillåter att Defender fortsätter spåra åtgärdad skadlig kod det antal dagar som du anger så att du kan kontrollera tidigare berörda enheter manuellt. Om du ställer in antalet dagar till **0** finns skadlig kod kvar i karantänmappen och tas inte bort automatiskt. |
|**Tillåt användargränssnittsåtkomst för klient**|Styr huruvida Windows Defender-användargränssnittet är dolt från användarna.<br>När den här inställningen ändras börjar den gälla nästa gång användarens dator startas om.|
|**Schemalägg daglig snabbsökning**|Tillåter att du schemalägger en snabbgenomsökning som körs varje dag vid den tidpunkt som du väljer|
|**Schemalägg en systemsökning**|Tillåter att du schemalägger en fullständig sökning eller en snabbsökning som körs regelbundet på den dag och vid den tidpunkt som du väljer|
|**Begränsa processoranvändning under en sökning**|Tillåter att du begränsar hur mycket processorkraft som genomsökningarna får använda (från **1** till **100**)|
|**Sök igenom arkivfiler**|Tillåter att Defender söker igenom arkiverade filer, till exempel ZIP- eller CAB-filer.|
|**Sök igenom e-postmeddelanden**|Tillåter att Defender söker igenom e-postmeddelanden när de tas emot på enheten|
|**Sök igenom flyttbara enheter**|Tillåter att Defender söker igenom flyttbara enheter, t.ex. USB-minnen|
|**Sök igenom mappade nätverksenheter**|Tillåter att Defender söker igenom filer på mappade nätverksenheter.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Sök igenom filer öppnade från delade nätverksmappar**|Tillåter att Defender söker igenom filer på delade nätverksenheter, till exempel de som nås från en UNC-sökväg.<br>Om filerna på enheten är skrivskyddade kan Defender inte ta bort eventuell skadlig kod i dem.|
|**Intervall för signaturuppdatering**|Ange med vilket intervall som Defender ska söka efter nya signaturfiler.|
|**Tillåt molnskydd**|Tillåt eller förhindra att Microsoft Active Protection Service tar emot information om skadlig kod från enheter som du hanterar. Den här informationen används för att förbättra tjänsten i framtiden.|
|**Be användarna att skicka exempel**|Styr huruvida filer som kan kräva ytterligare analys av Microsoft för att avgöra om de är skadliga ska skickas automatiskt till Microsoft|
|**Identifiering av potentiellt oönskade program**|Skyddar registrerade Windows Desktop-enheter mot aktiv programvara som klassificerats som oönskad av Windows Defender. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats.|
|**Filer och mappar som ska undantas när en sökning körs eller när realtidsskyddet används**|Lägger till en eller flera filer och mappar som **C:\Sökväg** eller **%ProgramFiles%\Sökväg\filnamn.exe** i undantagslistan. Dessa filer och mappar tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Filnamnstillägg att undanta när en sökning körs eller när realtidsskyddet används**|Lägg till ett eller flera filnamnstillägg som **jpg** eller **txt** i undantagslistan. Filer med dessa filnamnstillägg tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|
|**Processer att undanta när en sökning körs eller när realtidsskyddet används**|Lägger till en eller flera processer av typen **.exe**, **.com** eller **.scr** i undantagslistan. Dessa processer tas inte med i realtidsgenomsökningar eller schemalagda genomsökningar.|


### <a name="updates"></a>Updates

|Inställningsnamn|Ytterligare information (om det behövs)|
|----------------|---------------|
|**Tillåt automatiska uppdateringar**|Tillåt automatiska uppdateringar. Konfigurera någon av följande inställningar för att kontrollera uppdateringsbeteendet:<br />**Meddela om hämtning**<br />**Automatisk installation vid underhållstidpunkt**<br />**Automatisk installation och omstart vid underhållstidpunkt**<br />**Installera automatiskt och starta om enligt schema**: Om det här alternativet har valts kan du också konfigurera följande inställningar: **Meddela inte slutanvändare** och **Definiera installationsdag för schemalagda uppdateringar**.<br>(endast Windows 10 Desktop)|
|**Tillåt förhandsfunktioner**|Låter Microsoft distribuera förhandsversionsinställningar och -funktioner till Windows 10-enheter. Du kan välja att tillåta att endast inställningar eller alla förhandsversionsinställningar och -funktioner installeras.|

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO4-->


