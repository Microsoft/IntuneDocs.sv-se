---
title: "Enheter – Intune-informationslagret | Microsoft Docs"
description: "Referensavsnitt för kategorin Program för entitetssamlingar i API:et för Intune-informationslager."
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6955E12D-70D7-4802-AE3B-8B276F01FA4F
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f304e07de7ceefb09152aeb30d113c378e716d38
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="reference-for-devices-entities"></a>Referens för enhetsentiteter

Kategorin **Enheter** innehåller entiteter för mobilenheter som spårar information, till exempel:

  -  Enhetstyp
  -  Enhetsregistrering och registreringsstatus
  -  Äganderätt till enhet
  -  Status för enhetshantering
  -  Enhetsmedlemskap i Azure AD-status
  -  Registreringsstatus
  -  Tidigare information om enheten
  -  Inventering av appar på enheten

## <a name="devicetypes"></a>DeviceTypes

Entiteten **DeviceTypes** är den enhetstyp som andra informationslagerentiteter hänvisar till. Enhetstypen beskriver vanligtvis antingen enhetsmodell, tillverkare eller både och.

| Egenskap  | Description |
|---------|------------|
| DeviceTypeID |Unikt id för enhetstyp |
| DeviceTypeKey |Unikt id för enhetstypen i informationslagret – surrogatnyckel |
| DeviceTypeName |Enhetstyp |

## <a name="example"></a>Exempel

| deviceTypeID  | Namn | Description |
|---------|------------|--------|
| 0 |skrivbords- |Windows Desktop-enhet |
| 1 |WindowsRT |WindowsRT-enhet |
| 2 |WinMO6 |Windows Mobile 6.0-enhet |
| 3 |Nokia |Nokia-enhet |
| 4 |WindowsPhone |Windows Phone-enhet |
| 5 |Mac |Mac-enhet |
| 6 |WinCE |Windows CE-enhet |
| 7 |WinEmbedded |Windows Embedded-enhet |
| 8 |IPhone |iPhone-enhet |
| 9 |iPad |iPad-enhet |
| 10 |iPod |iPod-enhet |
| 11 |Android |Android-enhet som hanteras via enhetsadministratören |
| 12 |ISocConsumer |iSoc Consumer-enhet |
| 14 |MacMDM |Mac OS X-enhet som hanteras med den inbyggda MDM-agenten |
| 15 |HoloLens |Holo Lens-enhet |
| 16 |SurfaceHub |Surface Hub-enhet |
| 17 |AndroidForWork |Android-enhet som hanteras med hjälp av Android for Work-profilens ägare |
| 100 |Blackberry |Blackberry-enhet |
| 101 |Palm |Palm-enhet |
| 255 |Okänt |Okänd typ av enhet |

## <a name="clientregistrationstatetypes"></a>ClientRegistrationStateTypes

Entiteten **ClientRegistrationStateTypes** är den registreringstyp som andra informationslagertabeller hänvisar till.

| Egenskap  | Description |
|---------|------------|
| clientRegisterationStateID |Unikt id för registreringstillstånd |
| clientRegisterationStateKey |Unikt id för registreringstillståndet i informationslagret – surrogatnyckel |
| clientRegisterationStateName |Registreringstillstånd |

## <a name="example"></a>Exempel

| ClientRegisterationStateID  | Namn | Description |
|---------|------------|--------|
| 0 |NotRegistered |Inte registrerad |
| 1 |SMSIDConflict |Sms-identitetskonflikt |
| 2 |Registrerad |Registrerad |
| 3 |Revoked |Tillståndet innebär att it-administratören har blockerat klienten och att blockeringen kan tas bort. En enhet kan också vara i tillståndet Revoked när den har rensats eller tagits ur bruk. |
| 4 |KeyConflict |Nyckelkonflikt |
| 5 |ApprovalPending |Väntar på godkännande |
| 6 |ResetCert |Återställ certifikat |
| 7 |NotRegisteredPendingEnrollment |Inte registrerad, väntar på registrering |
| 8 |Okänt |Okänt tillstånd |

## <a name="enrollmenttypes"></a>EnrollmentTypes

Entiteten **EnrollmentTypes** visar hur en enhet registrerades. Typ av registrering visar registreringsmetod. I exemplen visas olika typer av registrering och vad de innebär.

| Egenskap  | Description |
|---------|------------|
| managementStateID |Unikt id för hanteringstillståndet. |
| managementStateKey |Unikt id för hanteringstillståndet i informationslagret – surrogatnyckel. |
| managementStateName |Visar status för den fjärranslutna åtgärden som utförts på den här enheten. |

## <a name="example"></a>Exempel

| enrollmentTypeID  | Namn | Description |
|---------|------------|--------|
| 0 |Okänt |Registreringstyp samlades inte in |
| 1 |UserEnrollment |Användarinitierad registrering |
| 2 |DeviceEnrollment |Enhetsregistrering med användarlös profil |
| 3 |DeviceEnrollmentWithUDA |Enhetsregistrering med UDA-profil. |
| 4 |AzureDomainJoined |Användarinitierad enhetsregistrering via Azure Active Directory |
| 5 |UserEnrollmentWithServiceAccount |Användarinitierad registrering via tjänstkonto |
| 6 |DepDeviceEnrollment |Enhetsregistrering via DEP med användarlös profil |
| 7 |DepDeviceEnrollmentWithUDA |Enhetsregistrering via DEP med UDA-profil |
| 8 |AutoEnrollment |Kombinerad DRS- och MDM-registrering för BYOD-scenario |

## <a name="ownertypes"></a>OwnerTypes

Entiteten **EnrollmentTypes** visar om en enhet är företagsägd, privat ägd eller okänd.

| Egenskap  | Description | Exempel |
|---------|------------|--------|
| ownerTypeID |Unikt id för ägartyp. | |
| ownerTypeKey |Unikt id för ägartypen i informationslagret – surrogatnyckel. | |
| ownerTypeName |Representerar enheternas ägartyp:  <br>Företag – enheten är företagsägd. <br>Privat – enheten är privatägd (BYOD).  <br>Okänd – det finns ingen information om enheten. |Företag Privat Okänd |

## <a name="mdmstatuses"></a>MdmStatuses

Entiteten **MdmStatuses** visar enhetens regelefterlevnadsstatus.

| Egenskap  | Description |
|---------|------------|
| MdmStatusID |Unik identifierare för kompatibilitetstillstånd |
| MdmStatusKey |Unikt id för regelefterlevnadsstatus i informationslagret – surrogatnyckel | 
| ComplianceStatus |Kompatibilitetstillstånd för enheten, måste ha ett av värdena i tabellen nedan | 


## <a name="example"></a>Exempel

| MdmStatusID  | ComplianceStatus | Description |
|---------|------------|--------|
| 0 |Okänt |Enhetens kompatibilitetstillstånd är okänt. |
| 1 |Kompatibel |Enheten är kompatibel. |
| 2 |Ej kompatibel |Enheten är ej kompatibel. |
| 3 |Konflikt |Enhetens kompatibilitet resulterade i s-konflikt. |
| 4 |Fel |Fel uppstod vid läsning av enhetens kompatibilitetstillstånd. |


## <a name="managementstates"></a>ManagementStates

Entiteten **ManagementStates** innehåller information om enhetens tillstånd. Informationen kan vara användbar i fall där fjärråtgärder tillämpas, om enheten är jailbrokad eller rotad.

| Egenskap  | Description |
|---------|------------|
| managementStateID | Unikt id för hanteringstillståndet. |
| managementStateKey | Unikt id för hanteringstillståndet i informationslagret – surrogatnyckel. |
| managementStateName | Visar status för den fjärranslutna åtgärden som utförts på den här enheten. |

## <a name="example"></a>Exempel

| managementStateID  | Namn | Description |
|---------|------------|--------|
| 0 |Hanterade | Hanterad utan väntande fjärråtgärder. |
| 1 |RetirePending | Ett kommando för tillbakadragande väntar på enheten. |
| 2 |RetireFailed | Det gick inte att utföra kommandot för tillbakadragande på enheten. |
| 3 |WipePending | Ett rensningskommando väntar på enheten. |
| 4 |WipeFailed | Det gick inte att utföra rensningskommandot på enheten. |
| 5 |Ohälsosamt | Ej felfritt tillstånd. |
| 6 |DeletePending | Ett borttagningskommando väntar på enheten. |
| 7 |RetireIssued | Ett kommando om tillbakadragande har utfärdats till enheten. |
| 8 |WipeIssued | Ett rensningskommando har utfärdats. |
| 9 |WipeCanceled | Rensningskommandot har avbrutits. |
| 10 |RetireCanceled | Kommandot för tillbakadragande har avbrutits. |
| 11 |Discovered | Enheten har nyligen identifierats av Intune. När den checkar in för första gången övergår den i tillståndet Managed (hanterad). |

## <a name="workplacejoinstatetypes"></a>WorkPlaceJoinStateTypes

Entiteten **WorkPlaceJoinStateTypes** visar enhetens Azure Active Directory Workplace Join-status.  Under registreringsarbetsflödet kan ett eller flera certifikat användas för att verifiera eller autentisera. När en enhet registreras för WorkPlace används certifikaten för att verifiera enheten och användaren. Utfärdandet av certifikat sker via en SCEP-server (Simple Certificate Enrollment Point). Värdena i entiteten visar olika tillstånd som en enhet kan befinna sig i under den här processen. Ett av tillståndet är misslyckad WorkPlace-anslutning på grund av att det inte gick att utfärda ett nödvändigt certifikat (från en SCEP-server). Om en enhet inte passerat det här arbetsflödet är värdet Unknown (okänt).

| Egenskap  | Description |
|---------|------------|
| WorkPlaceJoinStateID | Unikt id för status för arbetsplatsanslutning |
| WorkPlaceJoinStateKey | Unikt id för arbetsplatsanslutningsstatus i informationslagret – surrogatnyckel |
| WorkPlaceJoinStateName | Arbetsplatsanslutningsstatus |

## <a name="example"></a>Exempel

| workPlaceJoinStateID  | Namn | Description |
|---------|------------|--------|
| 0 |Okänt |Om en enhet inte är arbetsplatsansluten har den status Unknown (okänt) |
| 1 |Lyckades |Arbetsplatsanslutningen lyckades |
| 2 |FailureToGetScepMetadata |Det gick inte att hämta SCEP-metadata |
| 3 |FailureToGetScepChallenge |Det gick inte att hämta SCEP-kontroll |
| 4 |DeviceFailureToInstallScepCommand |Det gick inte att installera SCEP-kommando på enheten |
| 5 |DeviceFailureToGetCertificate |Det gick inte att hämta certifikat via SCEP på enheten |
| 6 |DeviceScepPending |Väntetillstånd: SCEP pågår fortfarande på enheten |
| 7 |DeviceScepFailed |Det gick inte att installera certifikat via SCEP på enheten |
| 8 |AADValidationFailed |Det gick inte att verifiera att enheten finns på AAD |

## <a name="managementagenttypes"></a>ManagementAgentTypes

Entiteten **ManagementAgentTypes** visar de agenter som används för att hantera en enhet.

| Egenskap  | Description |
|---------|------------|
| ManagementAgentTypeID | Unikt id för typ av hanteringsagent. |
| ManagementAgentTypeKey | Unikt id för typ av hanteringsagent i informationslagret – surrogatnyckel. |
| ManagementAgentTypeName |Visar vilken typ av agent som används för att hantera enheten. |

## <a name="example"></a>Exempel

| ManagementAgentTypeID  | Namn | Description |
|---------|------------|--------|
| 1 |EAS | Enheten hanteras via Exchange Active Sync |
| 2 |MDM | Enheten hanteras med hjälp av en agent för mobilenhetshantering |
| 3 |EasMdm | Enheten hanteras både av Exchange Active Sync och en agent för mobilenhetshantering |
| 4 |IntuneClient | Enheten hanteras av Intune PC-agenten |
| 5 |EasIntuneClient | Enheten hanteras både av Exchange Active Sync och Intune PC-agenten |
| 8 |ConfigManagerClient | enheten hanteras av System Center Configuration Manager-agenten |
| 16 |Okänt | Okänd typ av hanteringsagent |

## <a name="devices"></a>Egenskaper

Entiteten **Enheter** innehåller en lista över registrerade enheter som hanteras och deras respektive egenskaper.

| Egenskap  | Description |
|---------|------------|
| DeviceKey | Unikt id för enheten i informationslagret – surrogatnyckel. |
| DeviceId | Unikt id för enheten. |
| DeviceName | Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgängligt för alla enheter. |
| DeviceTypeKey | Nyckel för enhetstypattributet för den här enheten. |
| ClientRegisterationStateKey | Nyckeln för attributet klientregistreringsstatus för den här enheten. |
| OwnerTypeKey | Nyckeln för attributet ägartyp för den här enheten: företag, privat eller okänt. |
| objectSourceKey | Ignorera den här kolumnen. |
| CreatedDate | Datum då enhetens registrerades. |
| LastContact | Senast kända incheckning på Intune. |
| LastContactNotification | Senaste gången Intune aviserade enheten om att checka in på Intune. |
| LastContactWorkplaceJoin | Tidsstämpel som visar senast kända Workplace Join-status för den här enheten. |
| ManagementAgentKey | Nyckel för den hanteringsagent som är kopplad till den här enheten. |
| ManagementStateKey | Nyckel för det hanteringstillstånd som är kopplat till enheten och som visar den senaste statusen för en fjärråtgärd eller om den har jailbrokats/rotats. |
| ReferenceId | Enhetens id i Azure Active Directory. |
| WorkPlaceJoinStateKey | Nyckel för den arbetsplatsanslutningsstatus som är kopplad till den här enheten. |
| CategoryId | Ignorera den här kolumnen. |
| EnrollmentTypeKey | Nyckel för den registreringstyp som är kopplad till den här enheten och som visar registreringsmetod. |
| CertExpirationDate | Utgångsdatum för certifikatet för mobilenhetshantering. |
| MdmStatusKey | En nyckel till MdmStatus. |
| OSFamily | Operativsystemfamilj (Windows, iOS, Android o.s.v.) |
| OSVersion | OS-version |
| OSMajorVersion | Operativsystemets högre versionskomponent (major.minor.build.revision). |
| OSMinorVersion | Operativsystemets lägre versionskomponent (major.minor.build.revision). |
| OSBuildNumber | Operativsystemets build-versionskomponent (major.minor.build.revision). |
| OSRevisionNumber | Operativsystemets revisionsversionskomponent (major.minor.build.revision). |
| EasID | Enhetens EAS-id, om enheten hanteras av Exchange Active Sync. |
| GraphDeviceIsManaged | Senaste hanteringsstatus som Intune angett i Azure AD. |
| GraphDeviceIsCompliant | Senaste efterlevnadsstatus som Intune angett i Azure AD. |
| Serienummer | Enhetens serienummer, om det är tillgängligt. |
| EnrolledByUser | Id för den användare som registrerade enheten, hänvisar till kolumnen userId i användartabellen. |
| RowLastModifiedDateTimeUTC | Senaste ändring av den här posten. |
| ProcessorArchitecture | Processorarkitektur. |
| DeviceAction | Senast utfärdade enhetsåtgärd, ignorera för tillfället. |
| Tillverkare | Enhetstillverkaren. |
| Modell | Enhetsmodell. |
| LastPolicyUpdateUtc | Senaste principuppdatering på enheten. |
| LastExchangeStatusUtc | Senaste enhetssynkronisering med Exchange. |
| IsDeleted | Ange värdet True om enheten inte hanteras av Intune längre. Bevarar den senast kända statusen. |

## <a name="devicepropertyhistory"></a>DevicePropertyHistory

Entiteten **DevicePropertyHistory** innehåller samma egenskaper som enhetstabellen och dagliga ögonblicksbilder av varje enhetspost per dag under de senaste 90 dagarna. I kolumnen DateKey visas dagen för varje rad.

| Egenskap  | Description |
|---------|------------|
| DateKey |Referens till datumtabellen som visar dag. |
| DeviceKey |Unikt id för enheten i informationslagret – surrogatnyckel. Det här är en referens till enhetstabellen som innehåller Intune-enhetens id. |
| DeviceName |Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgängligt för alla enheter. |
| DeviceTypeKey |Nyckel för enhetstypattributet för den här enheten. |
| ClientRegisterationStateKey |Nyckeln för attributet klientregistreringsstatus för den här enheten. |
| OwnerTypeKey |Nyckeln för attributet ägartyp för den här enheten: företag, privat eller okänt. |
| objectSourceKey |Ignorera den här kolumnen. |
| CreatedDate |Datum då enhetens registrerades. |
| LastContact |Senast kända incheckning på Intune. |
| LastContactNotification |Senaste gången Intune aviserade enheten om att checka in på Intune. |
| LastContactWorkplaceJoin |Tidsstämpel som visar senast kända Workplace Join-status för den här enheten. |
| ManagementAgentKey |Nyckel för den hanteringsagent som är kopplad till den här enheten. |
| ManagementStateKey |Nyckel för det hanteringstillstånd som är kopplat till enheten och som visar den senaste statusen för en fjärråtgärd eller om den har jailbrokats/rotats. |
| ReferenceId |Enhetens id i Azure Active Directory. |
| WorkPlaceJoinStateKey |Nyckel för den arbetsplatsanslutningsstatus som är kopplad till den här enheten. |
| CategoryId |Ignorera den här kolumnen. |
| EnrollmentTypeKey |Nyckel för den registreringstyp som är kopplad till den här enheten och som visar registreringsmetod. |
| CertExpirationDate |Utgångsdatum för certifikatet för mobilenhetshantering. |
| MdmStatusKey |En nyckel till MdmStatus. |
| OSFamily |Operativsystemfamilj (Windows, iOS, Android o.s.v.) |
| OSVersion |OS-version. |
| OSMajorVersion |Operativsystemets högre versionskomponent (major.minor.build.revision). |
| OSMinorVersion |Operativsystemets lägre versionskomponent (major.minor.build.revision). |
| OSBuildNumber |Operativsystemets build-versionskomponent (major.minor.build.revision). |
| OSRevisionNumber |Operativsystemets revisionsversionskomponent (major.minor.build.revision). |
| EasID |Enhetens EAS-id, om enheten hanteras av Exchange Active Sync. |
| GraphDeviceIsManaged |Senaste hanteringsstatus som Intune angett i Azure AD. |
| GraphDeviceIsCompliant |Senaste efterlevnadsstatus som Intune angett i Azure AD. |
| Serienummer |Enhetens serienummer, om det är tillgängligt. |
| EnrolledByUser |Id för den användare som registrerade enheten, hänvisar till kolumnen userId i användartabellen. |
| RowLastModifiedDateTimeUTC |Senaste ändring av den här posten. |
| ProcessorArchitecture |Processorarkitektur. |
| DeviceAction |Senast utfärdade enhetsåtgärd, ignorera för tillfället. |
| Tillverkare |Enhetstillverkaren. |
| Modell |Enhetsmodell. |
| LastPolicyUpdateUtc |Senaste principuppdatering på enheten. |
| LastExchangeStatusUtc |Senaste enhetssynkronisering med Exchange. |

## <a name="mdmdeviceinventoryhistories"></a>MdmDeviceInventoryHistories

Entiteten **MdmDeviceInventoryHistories** innehåller dagliga ögonblicksbilder av inventeringsinformation för mobilenhetshanterade enheter (MDM) under de senaste 90 dagarna. I kolumnen DateKey visas radens dag. Vissa egenskaper kanske inte kan användas eller har inte fyllts i för alla enheter. Mer information finns på den här sidan. Mer information finns i [Förstå dina enheter med inventering i Microsoft Intune](https://docs.microsoft.com/Intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-Intune).

| Egenskap  | Description |
|---------|------------|
| DateKey | Referens till datumtabellen som visar dag. |
| DeviceKey |Unikt id för enheten i informationslagret – surrogatnyckel. Det här är en referens till enhetstabellen som innehåller Intune-enhetens id. |
| DeviceModel |Enhetsmodell. |
| Operativsystem |Enhetens operativsystem. |
| DeviceName |Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet är inte tillgängligt för alla enheter. |
| SoftwareVersion |I de flesta fall är det här en operativsystemversion förutom på Apple-plattformar där det skiljer sig från operativsystemversionen. |
| Imei |IMEI-numret |
| HardwareInventoryTimeUtc |Tid för första rapporterade inventeringen för enheten. |
| InventoryModifiedTimeUtc |Tid för senaste lagrade inventeringen när den här ögonblicksbilden togs. |
| InventoryReportingTimeUtc |Tid för senaste insamlade inventeringen för enheten. |
| ExchangeActiveSyncId |Enhets-id för Exchange ActiveSync. |
| ComputerSystemDescription |Systembeskrivning. |
| ComputerSystemName |Systemnamn. |
| ComputerSystemManufacturer |Systemtillverkare. |
| ComputerSystemModel |Systemmodell. |
| UserName |Användarnamn. |
| OSType |Typ av operativsystem. |
| OSCaption |Operativsystemrubrik. |
| OSName |Namn på operativsystem. |
| OSManufacturer |Operativsystemets tillverkare. |
| OSProductSuite |Operativsystemets produktserie. |
| OSProductType |Operativsystemets produkttyp. |
| Språk |Operativsystemets språk. |
| PhysicalMemoryCapacity |Kapacitet för fysiskt minne (i byte). |
| PhysicalMemoryRemovable |Flyttbart fysiskt minne (i byte). |
| SystemEnclosureChassisTypesInnerText |Visar enhetens typ av systemchassi. Talen anger följande värden:  <br>0 eller tom = Okänd   <br>1 = Det är en stationär dator   <br>2 = Det är en bärbar dator  <br>3 = Det är en arbetsstation  <br>4 = Det är en Enterprise Server  <br>100 = Det är en telefon  <br>101 = Det är en surfplatta  <br>102/103 = En annan okänd typ av mobil enhet |
| SystemEnclosureModel |Systemhöljets modell. |
| SystemEnclosureSerialNumber |Systemhöljets serienummer. |
| NetworkAdapterConfigurationText |Konfigurationstext på nätverkskort. |
| MacAddress |MAC-adress. |
| SmsID |Id för Intune-enhet. |
| CertExpiry |Utgångsdatum för certifikatet för mobilenhetshantering. |
| DeviceClientAgentVersion |Klientens agentversion. |
| DeviceClientID |Enhets klient-id. |
| Serienummer |Serienummer. |
| DeviceManufacturer |Enhetstillverkare. |
| DMVersion |Enhetstillverkarversion. |
| Version av inbyggd programvara |Version av fast installerad programvara. |
| HardwareVersion |Maskinvaruversion. |
| PlatformType |Plattformstyp. |
| ProcessorLevel |Processornivå. |
| ProcessorRevision |Processorrevision. |
| Produkt |Produkt. |
| ProductVersion |Produktversion. |
| OEM |Komponenttillverkare. |
| DeviceBuildVersion |Enhetens build-version. |
| Meid |MEID (Mobile Equipment Identifier). |
| PhoneNumber |Telefonnummer. |
| SubscriberCarrierNetwork |Namn på operatörsnätverk. |
| CellularTechnology |Typ av operatörsnätverk (CDMA/GSM). |
| Imsi |IMSI-nummer. |
| JailBroken |Sant om enheten är jailbrokad eller rotad. |
| IsActivationLockEnabled |Sant om aktiveringslås är aktiverat |
| DeviceType |Enhetstyp |
| IsSupervised |Övervakas |
| DeviceDisplayNumberOfColors |Antal färger på enhetens display |
| HorizontalResolution |Enhetens horisontella skärmupplösning |
| VerticalResolution |Enhetens vertikala skärmupplösning |
| StorageFree |Ledigt lagringsutrymme (i byte) |
| StorageTotal |Totalt lagringsutrymme (i byte) |
| ProgramFree |Ledigt programminne (i byte) |
| ProgramTotal |Totalt programminne (i byte) |
| RemovableStorageFree |Ledigt flyttbart lagringsutrymme (i byte) |
| RemovableStorageTotal |Totalt flyttbart lagringsutrymme (i byte) |
| DeviceMemoryDeviceCapacity |Enhetens minneskapacitet |
| DeviceMemoryAvailableDeviceCapacity |Enhetens tillgängliga minneskapacitet |
| DeviceOSVersion |OS-version |
| DeviceOSPlatform |Operativsystemplattform |
| DeviceOSLanguage |Operativsystemspråk |
| PasswordMaxAttemptsBeforeWipe |Högsta antal tillåtna lösenordsförsök innan enheten rensas |
| PasswordMinComplexChars |Lägsta antal avancerade tecken som krävs i lösenordet |
| PasswordMinLength |Kortast tillåtna längd på lösenord |
| PasswordHistory |Lösenord: minsta antal tidigare lösenord godkänns ej |
| PasswordEnabled |Lösenord - aktiverat? |
| PasswordExpiration |Förfallotid för lösenord. |
| AllowRecoveryPassword |Tillåt lösenordsåterställning. |
| PasswordAutoLockTimeout |Lösenord: tidsgräns för autolås. |
| PasswordType |Typ av lösenord. |
| BacklightACTimeout |Tidsgräns för bakgrundsbelysning vid anslutning till strömkälla. |
| BacklightBatTimeout |Tidsgräns för bakgrundsbelysning på batteri. |
| PowerBackupPercent |Säkerhetskopieringsprocent. |
| BatteryPercent |Återstående batteriprocent. |
| PlatformID |Plattforms-id. |
| ExchangeDeviceID |Id för Exchange-enhet. |
| SmsProcessorDescription |Beskrivning av processor. |
| OwnerEmailAddress |Ägarens e-postadress. |
| DeviceOSName |Namn på operativsystem. |
| WifiMac |Wifi MAC-adress. |
| EthernetMac |Ethernet MAC-adress. |
| RequireEncryption |Visar om enheten är krypterad eller inte. |
| ActivationLockBypassCode |Kod för att kringgå aktiveringslås. |

## <a name="applicationinventory"></a>ApplicationInventory

Entiteten **ApplicationInventory** innehåller en lista över appar som hittats på enheten under inventeringen.

| Egenskap  | Description |
|---------|------------|
| DeviceKey |En referens till enhetstabellen. |
| ApplicationKey |? (kopierat från ExchangeDeviceService\DeviceApplication). |
| ApplicationName |? (kopierat från ExchangeDeviceService\DeviceApplication). |
| ApplicationVersion |? (kopierat från ExchangeDeviceService\DeviceApplication). |
| BundleSize |? (kopierat från ExchangeDeviceService\DeviceApplication). |
