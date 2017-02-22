---
title: "Anpassade inställningar i Intune för Windows 10-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig om inställningarna du kan använda i en anpassad Windows 10-profil."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0da8c0fe399f76f43439cc66eaecd12bb454f9a6
ms.openlocfilehash: 05856480f8bb76e561f2b459d4ab800f9909a40a


---

# <a name="custom-device-settings-for-windows-10-devices-in-intune-azure-preview"></a>Anpassade enhetsinställningar för Windows 10-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 är många inställningar tillgängliga via [Princip-CSP (Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](how-to-configure-custom-settings.md).
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
5. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.
Profilen skapas och visas på bladet med profillistan.

## <a name="example"></a>Exempel
I skärmbilden nedan har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)


## <a name="policy-settings"></a>Principinställningar

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt automatiskt uppdatering**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|Endast Desktop<br>**Datatyp:** heltal<br />**Värden:** **0** - **5** (standard: **1**)|
|**Schemalägg installationsdag**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|Endast Mobile<br>**Datatyp:** heltal<br />**Värden:**<br>**0** – Varje dag (standard)<br>**1** – Söndag<br>**2** – Måndag<br>**3** – Tisdag<br>**4** – Onsdag<br>**5** – Torsdag<br>**6** – Fredag<br>**7** – Lördag|
|**Schemalägg installationstid**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – **23** timmar (**0** är midnatt) (standard: **3**)|
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

## <a name="windows-defender-settings"></a>Inställningar för Windows Defender

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

## <a name="edge-browser-settings"></a>Inställningar för Edge-webbläsare

|Principnamn och URI|Information|
|---------------|------------|-----------|
|**Tillåt webbläsare**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|Endast Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**: Surfning av, **1**: Surfning på (standard)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0**: Visa inte förslag, **1**: Visa förslag (standard)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:**<br>**0**: Inaktiverad (öppna intranätsplatser i Microsoft Edge-webbläsare – standard)<br>**1** – Aktiverad (öppna intranätsplatser i Internet Explorer).|
|**Tillåt Spåra inte**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|Desktop och Mobile)<br />**Datatyp:** heltal<br />**Värden:** **0** – Inaktiverat (DNT skickas inte, standard), **1** – Aktiverat (DNT skickas)|
|**Konfigurera SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:** **0** – Tillåt inte, **1** – Tillåt (standard)|
|**Tillåt popup-fönster**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Blockera popup-fönster (standard), **1** – Tillåt poup-fönster|
|**Tillåt cookies**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Tillåt cookies från alla webbplatser (standard)<br>**1** – Blockera endast cookies från tredje part<br>**2** – Blockera alla cookies|
|**Tillåt att spara lösenord**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|Desktop och Mobile<br />**Datatyp:** heltal<br />**Värden:**<br>**0** – Lösenordshanteraren är inaktiverad; <br>**1** – Lösenordshanteraren är aktiverad (standard)|
|**Tillåt autofyll**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|Endast Desktop<br />**Datatyp:** heltal<br />**Värden:** **0** – Inaktiverat (standard), **1** – Aktiverat|
|**Konfigurera företagswebbplatslista**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|Endast Desktop<br />**Datatyp:** Sträng<br />**Värden:<br>**0** – Inte konfigurerat<br>**1** – Använd webbplatslista för företagsläge i IE om konfigurerat (standard)<br>**2** – Ange plats för webbplatslista för företagsläge|



<!--HONumber=Feb17_HO1-->


