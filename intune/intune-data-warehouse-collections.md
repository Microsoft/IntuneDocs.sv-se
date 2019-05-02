---
title: Intune-informationslagersamlingar
titleSuffix: Microsoft Intune
description: Intune-informationslagersamlingar innehåller information om API för informationslager.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 29f09230-dc56-43db-b599-d961967bda49
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 00a0bd4936d1ad8ba8dd52f1839e7d42505db60e
ms.sourcegitcommit: 601327125ac8ae912d8159422de8aac7dbdc25f6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59429232"
---
#  <a name="intune-data-warehouse-collections"></a>Intune-informationslagersamlingar

Följande Intune-informationslagersamlingar innehåller egenskaper, beskrivningar och exempel för v1.0-samlingar av informationslagrets API-entiteter. 

## <a name="apprevisions"></a>appRevisions
I entiteten **AppRevision** visas en lista över alla appversioner.

|          Egenskap          |                                      Beskrivning                                      |                Exempel               |
|:--------------------------:|:-------------------------------------------------------------------------------------:|:------------------------------------:|
| AppKey                     | Appens unika id.                                                         | 123                                  |
| ApplicationId              | Unik identifierare för appen – liknar AppKey, men den här nyckeln är naturlig.        | b66bc706-ffff-7437-0340-032819502773 |
| Revision                   | Versionen som anges av administratören under uppladdningen av binärfilen.                   | 2                                    |
| Titel                      | Appens titel.                                                                     | Excel                                |
| Utgivare                  | Appens utgivare.                                                                 | Microsoft                            |
| UploadState                | Appens uppladdningsstatus.                                                              | 1                                    |
| AppTypeKey                 | Referens till AppType som beskrivs i följande avsnitt.                            | 1                                    |
| VppProgramTypeKey          | Referens till VppProgramType som beskrivs nedan.                                        | 30876                                |
| SkapadTid               | Tidpunkt då versionen skapades.                                            | 11/23/2016 0:00                      |
| ModifiedTime               | Senaste ändring av något relaterat till den här versionen.                            | 11/23/2016 0:00                      |
| Storlek                       | Storlek på binärfilen i byte.                                                          | 120 392 000                          |
| StartDateInclusiveUTC      | Datum och tid i UTC när appversionen skapades i informationslagret.      | 11/23/2016 0:00                      |
| EndDateExclusiveUTC        | Datum och tid i UTC när appversionen blev inaktuell.                        | 11/23/2016 0:00                      |
| IsCurrent                  | Visar om appversionen i informationslagret är aktuell eller inte.         | Sant/falskt                           |
| RowLastModifiedDateTimeUTC | Datum och tid i UTC för senaste ändring av appversionen i informationslagret. | 11/23/2016 0:00                      |

## <a name="apptypes"></a>appTypes
Entiteten **AppType** visar en lista över installationskällan för en app.

|   Egenskap  |        Beskrivning        |
|:-----------:|:-------------------------:|
| AppTypeID   | Id för typen           |
| AppTypeKey  | Surrogatnyckel för nyckeln |
| AppTypeName | Typ av app                  |

### <a name="example"></a>Exempel

| AppTypeID |                Namn               |                     Beskrivning                     |
|:---------:|:---------------------------------:|:---------------------------------------------------:|
| 0         | Android-butiksapp               | En app från en Android-butik.                             |
| 1         | Verksamhetsspecifik Android-app                 | En verksamhetsspecifik app för Android.                  |
| 2         | Hanterad Android-butiksapp (MAM) | En app med aktiverad hantering från en Android-butik. |
| 3         | App Store-app                   | En App Store-app.                                 |
| 4         | Verksamhetsspecifik iOS-app                     | En verksamhetsspecifik app för iOS.                      |
| 5         | Hanterad App Store-app (MAM)     | En App Store-app med aktiverad hantering.       |
| 6         | O365 Pro Plus Suite             | Office 365 Pro Plus Suite för Windows 10.     |
| 7         | Webbapp                         | En webbapp.                                        |
| 8         | Windows Phone 8.1-Store-app     | En Windows Phone 8.1-app från Store.                    |
| 9         | Microsoft Store-app               | En Microsoft Store-app.                              |
| 10        | Verksamhetsspecifika Windows-appar                | En verksamhetsspecifik Windows AppX-app.              |
| 11        | Windows Mobile MSI              | En verksamhetsspecifik MSI-app.                      |
| 12        | Verksamhetsspecifik Windows Phone-app           | Verksamhetsspecifik Windows Phone-app.             |

## <a name="compliancepolicystatusdeviceactivities"></a>compliancePolicyStatusDeviceActivities
I följande tabell sammanfattas tilldelningsstatusen för efterlevnadsprinciper för enheter. Den visar antalet enheter som finns i varje kompatibilitetstillstånd.

|    Egenskap   |                                                                                      Beskrivning                                                                                     |  Exempel |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey       | Datumnyckel när sammanfattningen skapades för kompatibilitetsprincipen.                                                                                                                   | 20161204 |
| Okänt       | Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker.                                                                           | 5        |
| NotApplicable | Antalet enheter där kompatibilitetsprinciper som tilldelats av administratören inte kan användas.                                                                                     | 201      |
| Kompatibel     | Antalet enheter som har tillämpat en eller flera kompatibilitetsprinciper som administratören har satt upp som mål.                                                                        | 4083     |
| InGracePeriod | Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören.                                                                                  | 57       |
| NonCompliant  | Antalet enheter som inte har tillämpat en eller flera kompatibilitetsprinciper som administratören har satt upp som mål, eller där användaren inte har följt de principer som administratören har satt upp som mål. | 43       |
|    Fel      |    Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande.                                                                          |    3     |

## <a name="compliancepolicystatusdeviceperpolicyactivities"></a>compliancePolicyStatusDevicePerPolicyActivities
I följande tabell sammanfattas tilldelningsstatus för efterlevnadsprinciper för enheter per princip och per principtyp. Den visar antalet enheter som finns efter kompatibilitetstillstånd för varje tilldelad efterlevnadsprincip.

|      Egenskap     |                                                                                      Beskrivning                                                                                     |  Exempel |
|:-----------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|
| DateKey           | Datumnyckel när sammanfattningen skapades för kompatibilitetsprincipen.                                                                                                                   | 20161219 |
| PolicyKey         | Nyckel för efterlevnadsprincipen som sammanfattningen skapades för.                                                                                                                   | 10178    |
| PolicyPlatformKey | Nyckel för plattformstypen för efterlevnadsprincipen som sammanfattningen skapades för.                                                                                            | 5        |
| Okänt           | Antalet enheter som är offline eller inte kunde kommunicera med Intune eller Azure AD av andra orsaker.                                                                           | 13       |
| NotApplicable     | Antalet enheter där kompatibilitetsprinciper som tilldelats av administratören inte kan användas.                                                                                     | 3        |
| Kompatibel         | Antalet enheter som har tillämpat en eller flera kompatibilitetsprinciper som administratören har satt upp som mål.                                                                        | 45       |
| InGracePeriod     | Antalet enheter som inte är kompatibla men som är i respitperioden som angetts av administratören.                                                                                  | 3        |
| NonCompliant      | Antalet enheter som inte har tillämpat en eller flera kompatibilitetsprinciper som administratören har satt upp som mål, eller där användaren inte har följt de principer som administratören har satt upp som mål. | 7        |
| Fel             | Antalet enheter som inte kunde kommunicera med Intune eller Azure AD och returnerade ett felmeddelande.                                                                             | 3        |
## <a name="compliancestates"></a>complianceStates

|      Egenskap      |                       Beskrivning                      |
|:------------------:|:------------------------------------------------------:|
| complianceStatus   | Kompatibilitetsstatus för enheter med mdmStatusKey       |
| complianceStateKey | Kompatibilitetsnyckel för att matcha enhet och kompatibilitetsstatus |
| complianceStateID  | ID för att matcha kompatibilitetstillståndet                |

### <a name="example"></a>Exempel

|  complianceStatus  |                       Beskrivning                      |
|:------------------:|:------------------------------------------------------:|
|    Okänt         |    Okänt.                                                                        |
|    Kompatibel       |    Kompatibel.                                                                      |
|    Ej kompatibel    |       Enheten är icke-kompatibel och blockeras från företagsresurser.             |
|    Konflikt        |    Konflikt med andra regler.                                                      |
|    Fel           |       Fel.                                                                       |
|    ConfigManager   |    Hanteras av Config Manager.                                                      |
|    InGracePeriod   |       Enheten är icke-kompatibel men har tillgång till företagsresurser          |

## <a name="dates"></a>datum
Entiteten **datum** representerar datum som flera informationslagerentiteter refererar till.

|     Egenskap    |                       Beskrivning                      |    Exempel    |
|:---------------:|:------------------------------------------------------:|:-------------:|
| DateKey         | Unikt id för datumet i informationslagret. | 20160703      |
| FullDate        | Datumet i fullständigt datum/tid-format.        | 7/3/2016 0:00 |
| DayOfWeek       | Veckodag                                            | 1             |
| DayOfMonth      | Dag i månaden                                           | 3             |
| DayOfYear       | Dag på året                                            | 185           |
| WeekOfYear      | Vecka på året                                           | 28            |
| MonthOfYear     | Månad på året                                      | 7             |
| CalendarQuarter | Kalenderkvartal                                       | 3             |
| CalendarYear    | Kalenderår                                          | 2016          |
| DateKey         | Unikt id för datumet i informationslagret. | 20160703      |
| FullDate        | Datumet i fullständigt datum/tid-format.        | 7/3/2016 0:00 |
| DayOfWeek       | Veckodag                                            | 1             |
| DayOfMonth      | Dag i månaden                                           | 3             |
| DayOfYear       | Dag på året                                            | 185           |
| WeekOfYear      | Vecka på året                                           | 28            |
| MonthOfYear     | Månad på året                                      | 7             |
| CalendarQuarter | Kalenderkvartal                                       | 3             |
| CalendarYear    | Kalenderår                                          | 2016          |

## <a name="devicecategories"></a>deviceCategories

|      Egenskap      |                                    Beskrivning                                   |                Exempel               |
|:------------------:|:--------------------------------------------------------------------------------:|:------------------------------------:|
| deviceCategoryID   | Unik identifierare för enhetskategorin.                                       | fb415ba2-7c08-41f6-a5e5-685b50da2c4c |
| deviceCategoryKey  | Unik identifierare för enhetskategorin i informationslagret – surrogatnyckel | 1                                    |
| deviceCategoryName | Visningsnamn för enhetskategorin.                                            | Smartphones                          |

## <a name="deviceconfigurationprofiledeviceactivities"></a>deviceConfigurationProfileDeviceActivities
Entiteten **DeviceConfigurationProfileDeviceActivity** innehåller en lista över antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten visar hur många enheter som har en viss status vid en viss dag under de senaste 30 dagarna.

|  Egenskap |                                          Beskrivning                                          |  Exempel |
|:---------:|:---------------------------------------------------------------------------------------------:|:--------:|
| DateKey   | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. | 20160703 |
| Väntar   | Antalet unika enheter i väntande läge.                                                    | 123      |
| Lyckades | Antalet unika enheter med tillståndet lyckades.                                                    | 12       |
| Fel     | Antalet unika enheter med feltillstånd.                                                      | 10       |
| Misslyckades    | Antalet unika enheter med tillståndet misslyckades.                                                     | 2        |

## <a name="deviceconfigurationprofileuseractivities"></a>deviceConfigurationProfileUserActivities 
Entiteten **DeviceConfigurationProfileUserActivity** innehåller en lista över antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Antalet visar de enhetskonfigurationsprofiler som har tilldelats entiteten. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet. Entiteten **DeviceConfigurationProfileUserActivity** visar hur många användare som varit i ett visst tillstånd en viss dag under de senaste 30 dagarna. 

| Egenskap  | Beskrivning  | Exempel  |
|------------|----------------------------------------------------------------------------------------------|-----------|
| DateKey  | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret.  | 20160703  |
| Väntar  | Antalet unika användare i väntande läge.  | 123  |
| Lyckades  | Antalet unika användare med tillståndet lyckades.  | 12  |
| Fel  | Antalet unika användare med feltillstånd.  | 10  |
| Misslyckades  | Antalet unika användare med tillståndet misslyckades.  | 2  |

## <a name="devicepropertyhistories"></a>devicePropertyHistories

|          Egenskap          |                                                                                      Beskrivning                                                                                     |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DateKey                    | Referens till datumtabellen som visar dag.                                                                                                                                          |
| DeviceKey                  | Unik identifierare för enheten i informationslagret – surrogatnyckel. Det här är en referens till enhetstabellen som innehåller Intune-enhetens ID.                               |
| DeviceName                 | Namn på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn för andra egenskaper. Det här attributet kan inte göras tillgängligt för alla enheter. |
| DeviceRegistrationStateKey | Nyckeln för attributet enhetsregistreringstillstånd för den här enheten.                                                                                                                    |
| OwnerTypeKey               | Nyckeln för attributet ägartyp för den här enheten: företag, privat eller okänd.                                                                                                  |
| ManagementStateKey         | Nyckeln för det hanteringstillstånd som är kopplat till enheten och som visar det senaste tillståndet för en fjärråtgärd eller om den har brutits upp/rotats.                                                |
| AzureADRegistered          | Om enheten är registrerad i Azure Active Directory.                                                                                                                             |
| ComplianceStateKey         | En nyckel för ComplianceState.                                                                                                                                                            |
| OSVersion                  | OS-version.                                                                                                                                                                          |
| JailBroken                 | Om enheten har brutits upp eller rotats.                                                                                                                                         |
| DeviceCategoryKey          | Nyckeln för attributet enhetskategori för den här enheten.                                                                                                                                    |
## <a name="deviceregistrationstates"></a>deviceRegistrationStates
Entiteten **DeviceRegistrationState** representerar den registreringstyp som andra informationslagersamlingar hänvisar till. 

|           Egenskap          |                                     Beskrivning                                     |
|:---------------------------:|:-----------------------------------------------------------------------------------:|
| deviceRegistrationStateID   | Unikt id för registreringstillstånd                                            |
| deviceRegistrationStateKey  | Unik identifierare för registreringstillståndet i informationslagret – surrogatnyckel |
| deviceRegistrationStateName | Registreringstillstånd                                                                  |
|    NotRegistered                     |    Inte registrerad                                                                                                                                                                  |
|    Registrerad                        |       Registrerad                                                                                                                                                                   |
|    Revoked                           |       Tillståndet innebär att IT-administratören har blockerat klienten och att blockeringen kan tas bort. En enhet kan också vara i tillståndet återkallad när den har rensats eller tagits ur bruk.        |
|    KeyConflict                       |    Nyckelkonflikt                                                                                                                                                                    |
|    ApprovalPending                   |    Väntar på godkännande                                                                                                                                                                |
|    CertificateReset                  |    Återställ certifikat                                                                                                                                                               |
|    NotRegisteredPendingEnrollment    |    Inte registrerad, väntar på registrering                                                                                                                                               |
|    Okänt                           |    Okänt tillstånd                                                                                                                                                                   |

## <a name="devices"></a>devices
Entiteten **enhet** innehåller en lista över alla registrerade enheter som hanteras och deras respektive egenskaper.

|          Egenskap          |                                                                                       Beskrivning                                                                                      |
|:--------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| DeviceKey                  | Unik identifierare för enheten i informationslagret – surrogatnyckel.                                                                                                               |
| DeviceId                   | Unik identifierare för enheten.                                                                                                                                                     |
| DeviceName                 | Namnet på enheten på plattformar som tillåter namngivning av enheter. På andra plattformar skapar Intune ett namn utifrån övriga egenskaper. Det här attributet kan inte göras tillgängligt för alla enheter. |
| DeviceTypeKey              | Nyckeln för attributet enhetstyp för den här enheten.                                                                                                                                    |
| DeviceRegistrationState    | Nyckeln för attributet klientregistreringstillstånd för den här enheten.                                                                                                                      |
| OwnerTypeKey               | Nyckeln för attributet ägartyp för den här enheten: företag, privat eller okänd.                                                                                                    |
| EnrolledDateTime           | Datum och tid då enheten registrerades.                                                                                                                                         |
| LastSyncDateTime           | Senast kända incheckning på Intune.                                                                                                                                              |
| ManagementAgentKey         | Nyckeln för den hanteringsagent som är kopplad till den här enheten.                                                                                                                             |
| ManagementStateKey         | Nyckeln för det hanteringstillstånd som är kopplat till enheten och som visar det senaste tillståndet för en fjärråtgärd eller om den har brutits upp/rotats.                                                |
| AzureADDeviceId            | Azure-deviceID för den här enheten.                                                                                                                                                  |
| AzureADRegistered          | Om enheten är registrerad i Azure Active Directory.                                                                                                                             |
| DeviceCategoryKey          | Nyckeln för den kategori som är kopplad till den här enheten.                                                                                                                                     |
| DeviceEnrollmentType       | Nyckeln för den registreringstyp som är kopplad till den här enheten och som visar registreringsmetod.                                                                                             |
| ComplianceStateKey         | Nyckel för den kompatibilitetsstatus som är kopplad till den här enheten.                                                                                                                             |
| OSVersion                  | Enhetens operativsystemversion.                                                                                                                                                |
| EasDeviceId                | Exchange ActiveSync-ID för enheten.                                                                                                                                                  |
| Serienummer               | Serienummer                                                                                                                                                                           |
| UserId                     | Unik identifierare för användaren som är kopplad till enheten.                                                                                                                           |
| RowLastModifiedDateTimeUTC | Datum och tid i UTC när den här enheten senast ändrades i informationslagret.                                                                                                       |
| Tillverkare               | Enhetstillverkaren                                                                                                                                                             |
| Modell                      | Enhetsmodell                                                                                                                                                                    |
| OperatingSystem            | Enhetens operativsystem. Windows, iOS, osv.                                                                                                                                   |
| IsDeleted                  | Binärt tal för att visa om enheten har tagits bort eller inte.                                                                                                                                 |
| AndroidSecurityPatchLevel  | Nivå för Android-säkerhetsuppdatering                                                                                                                                                           |
| MEID                       | MEID                                                                                                                                                                                   |
| isSupervised               | Status för övervakad enhet                                                                                                                                                               |
| FreeStorageSpaceInBytes    | Ledigt lagringsutrymme i byte.                                                                                                                                                                 |
| TotalStorageSpaceInBytes   | Totalt lagringsutrymme i byte.                                                                                                                                                                |
| EncryptionState            | Krypteringstillstånd på enheten.                                                                                                                                                      |
| SubscriberCarrier          | Abonnentens operatör på enheten                                                                                                                                                       |
| PhoneNumber                | Enhetens telefonnummer                                                                                                                                                             |
| IMEI                       | IMEI                                                                                                                                                                                   |
| CellularTechnology         | Enhetens mobilteknik                                                                                                                                                    |
| WiFiMacAddress             | Wi-Fi MAC                                                                                                                                                                              |


## <a name="devicetypes"></a>deviceTypes
Entiteten **deviceType** representerar den enhetstyp som andra informationslagerentiteter hänvisar till. Enhetstypen beskriver vanligtvis antingen enhetsmodell, tillverkare eller både och.

|    Egenskap    |                                  Beskrivning                                 |
|:--------------:|:----------------------------------------------------------------------------:|
| DeviceTypeID   | Unik identifierare för enhetstypen                                       |
| DeviceTypeKey  | Unik identifierare för enhetstypen i informationslagret – surrogatnyckel |
| DeviceTypeName | Enhetstyp                                                                |

### <a name="example"></a>Exempel

| deviceTypeID |        Namn       |                      Beskrivning                      |
|:------------:|:-----------------:|:-----------------------------------------------------:|
| -1           | Inte tillgänglig   | Enhetstypen är inte tillgänglig.                     |
| 0            | skrivbords-           | Windows-skrivbordsenhet                              |
| 1            | Windows           | Windows-enhet                                      |
| 2            | WinMO6            | Windows Mobile 6.0-enhet                           |
| 3            | Nokia             | Nokia-enhet                                        |
| 4            | WindowsPhone      | Windows Phone-enhet                                |
| 5            | Mac               | Mac-enhet                                          |
| 6            | WinCE             | Windows CE-enhet                                   |
| 7            | WinEmbedded       | Windows Embedded-enhet                             |
| 8            | IPhone            | iPhone-enhet                                       |
| 9            | iPad              | iPad-enhet                                         |
| 10           | iPod              | iPod-enhet                                         |
| 11           | Android           | Android-enhet som hanteras med hjälp av enhetsadministratör   |
| 12           | ISocConsumer      | iSoc Consumer-enhet                                |
| 13           | Unix              | UNIX-enhet                                         |
| 14           | MacMDM            | Mac OS X-enhet som hanteras med den inbyggda MDM-agenten |
| 15           | HoloLens          | HoloLens-enheter                                       |
| 16           | SurfaceHub        | Surface Hub-enhet                                  |
| 17           | AndroidForWork    | Android-enhet som hanteras med hjälp av Android-profilägare  |
| 18           | AndroidEnterprise | Android-företagsenhet.                          |
| 100          | Blackberry        | Blackberry-enhet                                   |
| 101          | Palm              | Palm-enhet                                         |
| 255          | Okänt           | Okänd enhetstyp                                 |

## <a name="deviceenrollmenttypes"></a>deviceEnrollmentTypes
Entiteten **deviceEnrollmentType** visar hur en enhet registrerades. Typ av registrering visar registreringsmetod. I exemplen visas olika typer av registrering och vad de innebär.

|         Egenskap         |                                    Beskrivning                                    |
|:------------------------:|:---------------------------------------------------------------------------------:|
| deviceEnrollmentTypeID   | Unik identifierare för registreringstypen.                                       |
| deviceEnrollmentTypeKey  | Unik identifierare för registreringstypen i informationslagret – surrogatnyckel. |
| deviceEnrollmentTypeName | Namn på registreringstyp.                                                           |

### <a name="example"></a>Exempel

| enrollmentTypeID |                Namn                |                                        Beskrivning                                       |
|:----------------:|:----------------------------------:|:----------------------------------------------------------------------------------------:|
| 0                | Okänt                            | Registreringstyp samlades inte in                                                      |
| 1                | UserEnrollment                     | Användardriven registrering via BYOD-kanal.                                           |
| 2                | DeviceEnrollmentManager            | Användarregistrering med ett konto för enhetsregistreringshanterare.                              |
| 3                | AppleBulkWithUser                  | Apple-massregistrering med användarkontrollfråga. (DEP, Apple Configurator)                   |
| 4                | AppleBulkWithoutUser               | Apple-massregistrering utan användarkontrollfråga.   (DEP, Apple Configurator, Mobile Config) |
| 5                | WindowsAzureADJoin                 | Azure AD-anslutning i Windows 10.                                                                |
| 6                | WindowsBulkUserless                | Windows 10-massregistrering via ICD med certifikat.                               |
| 7                | WindowsAutoEnrollment              | Automatisk registrering i Windows 10.   (Lägg till arbetskonto)                                    |
| 8                | WindowsBulkAzureDomainJoin         | Azure AD-massanslutning i Windows 10.                                                           |
| 9                | WindowsCoManagement                | Windows 10-samhantering utlöst av AutoPilot eller en grupprincip.                       |
| 10               | WindowsAzureADJoinsUsingDeviceAuth | Azure-anslutning med Device Auth i Windows 10.                                            |

## <a name="enrollmentactivities"></a>enrollmentActivities 
Entiteten **EnrollmentActivity** visar aktiviteten för en enhetsregistrering.

| Egenskap                      | Beskrivning                                                               |
|-------------------------------|---------------------------------------------------------------------------|
| dateKey                       | Nyckeln för det datum då den här registreringsaktiviteten registrerades.               |
| deviceEnrollmentTypeKey       | Nyckeln för registreringens typ.                                        |
| deviceTypeKey                 | Nyckeln för enhetens typ.                                                |
| enrollmentEventStatusKey      | Nyckeln för den status som visar om registreringen lyckades eller misslyckades.    |
| enrollmentFailureCategoryKey  | Nyckeln för registreringsfelets kategori (om registreringen misslyckades).        |
| enrollmentFailureReasonKey    | Nyckeln för registreringsfelets orsak (om registreringen misslyckades).          |
| osVersion                     | Enhetens operativsystemversion.                               |
| count                         | Totalt antal registreringsaktiviteter som matchar klassificeringarna ovan.  |

## <a name="enrollmenteventstatuses"></a>enrollmentEventStatuses 
Entiteten **EnrollmentEventStatus** visar resultatet för en enhetsregistrering.

| Egenskap                   | Beskrivning                                                                       |
|----------------------------|-----------------------------------------------------------------------------------|
| enrollmentEventStatusKey   | Unik identifierare för registreringsstatusen i informationslagret (surrogatnyckel)  |
| enrollmentEventStatusName  | Namnet på registreringsstatusen. Se exemplen nedan.                            |

### <a name="example"></a>Exempel

| enrollmentEventStatusName  | Beskrivning                            |
|----------------------------|----------------------------------------|
| Klart                    | En lyckad enhetsregistrering         |
| Misslyckades                     | En misslyckad enhetsregistrering             |
| Inte tillgängligt              | Registreringsstatusen är inte tillgänglig.  |

## <a name="enrollmentfailurecategories"></a>enrollmentFailureCategories 
Entiteten **EnrollmentFailureCategory** visar varför en enhetsregistrering misslyckades. 

| Egenskap                       | Beskrivning                                                                                 |
|--------------------------------|---------------------------------------------------------------------------------------------|
| enrollmentFailureCategoryKey   | Unik identifierare för registreringsfelets kategori i informationslagret (surrogatnyckel)  |
| enrollmentFailureCategoryName  | Namnet på registreringsfelets kategori. Se exemplen nedan.                            |

### <a name="example"></a>Exempel

| enrollmentFailureCategoryName   | Beskrivning                                                                                                   |
|---------------------------------|---------------------------------------------------------------------------------------------------------------|
| Ej tillämpligt                  | Registreringsfelets kategori är inte tillämplig.                                                            |
| Inte tillgängligt                   | Registreringsfelets kategori är inte tillgänglig.                                                             |
| Okänt                         | Okänt fel.                                                                                                |
| Autentisering                  | Autentiseringen misslyckades.                                                                                        |
| Auktorisering                   | Anropet har autentiserats, men inte auktoriserats för registrering.                                                         |
| AccountValidation               | Det gick inte att verifiera kontot för registrering. (Kontot är blockerat, registrering är inte aktiverat)                      |
| UserValidation                  | Det gick inte att verifiera användaren. (Användaren finns inte, licens saknas)                                           |
| DeviceNotSupported              | Enheten stöds inte för hantering av mobilenheter.                                                         |
| InMaintenance                   | Kontot genomgår underhåll.                                                                                    |
| BadRequest                      | Klienten skickade en begäran som inte förstås/stöds av tjänsten.                                        |
| FeatureNotSupported             | Funktioner som används av den här registreringen stöds inte för det här kontot.                                        |
| EnrollmentRestrictionsEnforced  | Registreringsbegränsningar som konfigurerats av administratören blockerade den här registreringen.                                          |
| ClientDisconnected              | Tidsgränsen gick ut för klienten eller så avbröts registreringen av slutanvändaren.                                                        |
| UserAbandonment                 | Registreringen lämnades av slutanvändaren. (Slutanvändaren inledde registrering men slutförde den inte inom rimlig tid)  |

## <a name="enrollmentfailurereasons"></a>enrollmentFailureReasons  
Entiteten **EnrollmentFailureReason** visar en mer detaljerad orsak till ett enhetsregistreringsfel inom en viss felkategori.  

| Egenskap                     | Beskrivning                                                                               |
|------------------------------|-------------------------------------------------------------------------------------------|
| enrollmentFailureReasonKey   | Unik identifierare för registreringsfelets orsak i informationslagret (surrogatnyckel)  |
| enrollmentFailureReasonName  | Namnet på registreringsfelets orsak. Se exemplen nedan.                            |

### <a name="example"></a>Exempel

| enrollmentFailureReasonName      | Beskrivning                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Ej tillämpligt                   | Registreringsfelets orsak är inte tillämplig.                                                                                                                                                       |
| Inte tillgängligt                    | Registreringsfelets orsak är inte tillgänglig.                                                                                                                                                        |
| Okänt                          | Okänt fel.                                                                                                                                                                                         |
| UserNotLicensed                  | Användaren hittades inte i Intune eller har inte någon giltig licens.                                                                                                                                     |
| UserUnknown                      | Användaren är inte känd i Intune.                                                                                                                                                                           |
| BulkAlreadyEnrolledDevice        | Endast en användare kan registrera en enhet. Den här enheten har tidigare registrerats av en annan användare.                                                                                                                |
| EnrollmentOnboardingIssue        | Intune som utfärdare för hantering av mobilenheter (MDM) har inte konfigurerats ännu.                                                                                                                                 |
| AppleChallengeIssue              | Installationen av iOS-hanteringsprofilen försenades eller misslyckades.                                                                                                                                         |
| AppleOnboardingIssue             | Ett Apple MDM-pushcertifikat krävs för registrering i Intune.                                                                                                                                       |
| DeviceCap                        | Användaren försökte registrera fler enheter än maximalt tillåtna.                                                                                                                                        |
| AuthenticationRequirementNotMet  | Intune-registreringstjänsten kunde inte auktorisera den här begäran.                                                                                                                                            |
| UnsupportedDeviceType            | Den här enheten uppfyller inte minimikraven för Intune-registrering.                                                                                                                                  |
| EnrollmentCriteriaNotMet         | Det gick inte att registrera den här enheten på grund av en konfigurerad regel för registreringsbegränsning.                                                                                                                          |
| BulkDeviceNotPreregistered       | Den här enhetens IMEI (International Mobile Equipment Identifier) eller serienummer hittades inte.  Utan den här identifieraren betraktas enheter som privatägda enheter som för närvarande blockeras.  |
| FeatureNotSupported              | Användaren försökte få åtkomst till en funktion som ännu inte har släppts för alla kunder eller inte är kompatibel med Intune-konfigurationen.                                                            |
| UserAbandonment                  | Registreringen lämnades av slutanvändaren. (Slutanvändaren inledde registrering men slutförde den inte inom rimlig tid)                                                                                           |
| APNSCertificateExpired           | Apple-enheter kan inte hanteras med ett Apple MDM-pushcertifikat som har upphört att gälla.                                                                                                                            |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions
**IntuneManagementExtension** visar en lista över hälsan för **intuneManagementExtension** på varje Windows 10-enhet per dag. Data bevaras under de senaste 60 dagarna.

|       Egenskap      |                          Beskrivning                          | Exempel |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| DateKey             | Datumets unika id.                                | 123     |
| TenantKey           | Klientens unika id.                              | 456     |
| DeviceKey           | Unikt id för enheten.                              | 789     |
| ExtensionVersionKey | Unik identifierare för IntuneManagementExtension-versionen. | 1       |
| ExtensionStateKey   | Unikt id för hälsotillstånd.                            | 2       |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates
**IntuneManagementExtensionHealthState** visar en lista över alla möjliga hälsotillstånd för **IntuneManagementExtension**.

|      Egenskap     |                   Beskrivning                  | Exempel |
|:-----------------:|:----------------------------------------------:|:-------:|
| ExtensionStateKey | Unik identifierare för hälsotillstånd.           | 2       |
| ExtensionState    | Hälsotillståndet för en IntuneManagementExtension. | Felfri |

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions
Entiteten **IntuneManagementExtensionVersion** visar en lista över alla versioner som används av **IntuneManagementExtension**.

|       Egenskap      |                          Beskrivning                          | Exempel |
|:-------------------:|:-------------------------------------------------------------:|:-------:|
| ExtensionVersionKey | Unik identifierare för IntuneManagementExtension-versionen. | 1       |
| ExtensionVersion    | Det fyrsiffriga versionsnumret.                                   | 1.0.2.0 |

## <a name="mamapplications"></a>MamApplications

Entiteten **MamApplication** innehåller en lista över verksamhetsspecifika appar som hanteras via mobilappshantering (MAM) utan registrering i företaget.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| mamApplicationKey |Unikt ID för MAM-programmet. | 432 |
| mamApplicationName |Namn på MAM-programmet. |MAM exempel programnamn |
| mamApplicationId |Program-id för MAM-appen. | 123 |
| IsDeleted |Visar huruvida posten för MAM-appen har uppdaterats. <br>Sant: MAM-appen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appen. |Sant/falskt |
| StartDateInclusiveUTC |Datum och tid i UTC när MAM-appen skapades i informationslagret. |2016-11-23 12:00:00 |
| DeletedDateUTC |Datum och tid i UTC när IsDeleted ändrades till True. |2016-11-23 12:00:00 |
| RowLastModifiedDateTimeUTC |Datum och tid i UTC för senaste ändring av MAM-appen i informationslagret. |2016-11-23 12:00:00 |


## <a name="mamapplicationinstances"></a>MamApplicationInstances

Entiteten **MamApplicationInstance** innehåller en lista över appar som hanteras via mobilappshantering (MAM) som enskilda instanser per användare och enhet. Alla användare och enheter i listan är skyddade, vilket betyder att det finns minst en princip för mobilappshantering kopplad till dem.


|          Egenskap          |                                                                                                  Beskrivning                                                                                                  |               Exempel                |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------|
|   ApplicationInstanceKey   |                                                               Unikt id för MAM-appinstansen i informationslagret – surrogatnyckel.                                                                |                 123                  |
|           UserId           |                                                                              Användar-ID för den användare som har den här MAM-appen installerad.                                                                              | b66bc706-ffff-7437-0340-032819502773 |
|   ApplicationInstanceId    |                                              Unikt id för MAM-appinstansen, liknar ApplicationInstanceKey,men id:t är en naturlig nyckel.                                              | b66bc706-ffff-7437-0340-032819502773 |
| mamApplicationId | Program-Id för Mam-programmet som den här Mam-programinstans har skapats.   | 2016-11-23 12:00:00   |
|     ApplicationVersion     |                                                                                     Programversion för MAM-appen.                                                                                      |                  2                   |
|        CreatedDate         |                                                                 Datum då MAM-appinstansposten skapades. Värdet kan vara null.                                                                 |        2016-11-23 12:00:00        |
|          Plattform          |                                                                          Plattform för den enhet där MAM-appen är installerad.                                                                           |                  2                   |
|      PlatformVersion       |                                                                      Plattformsversion för enheten där MAM-appen är installerad.                                                                       |                 2.2                  |
|         SdkVersion         |                                                                            SDK-version där MAM-appen är paketerad.                                                                            |                 3.2                  |
| mamDeviceId | Enhets-Id för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceType | Enhetstyp för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
| mamDeviceName | Enhetsnamn för enheten där MAM-programinstans som är associerad med.   | 2016-11-23 12:00:00   |
|         IsDeleted          | Visar huruvida posten för MAM-appinstansen har uppdaterats. <br>Sant: MAM-appinstansen innehåller en ny post med uppdaterade fält i den här tabellen. <br>Falskt: den senaste posten för den här MAM-appinstansen. |              Sant/falskt              |
|   StartDateInclusiveUtc    |                                                              Datum och tid i UTC när MAM-appinstansen skapades i informationslagret.                                                               |        2016-11-23 12:00:00        |
|       DeletedDateUtc       |                                                                             Datum och tid i UTC när IsDeleted ändrades till True.                                                                              |        2016-11-23 12:00:00        |
| RowLastModifiedDateTimeUtc |                                                           Datum och tid i UTC för senaste ändring av MAM-appinstansen i informationslagret.                                                            |        2016-11-23 12:00:00        |

## <a name="mamcheckins"></a>MamCheckins

Entiteten **MamCheckin** visar data som samlas in när en hanterad mobilappinstans har checkat in på Intune-tjänsten. 

> [!Note]  
> När en appinstans checkar in flera gånger per dag lagras den i informationslagret som en enda incheckning.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| DateKey |Datumnyckel när incheckningen av MAM-appen registrerades i informationslagret. | 20160703 |
| ApplicationInstanceKey |Nyckel för appinstansen som är kopplad till incheckningen av den mobilappshanterade appen. | 123 |
| UserKey |Nyckel för användaren som är kopplad till incheckningen av MAM-appen. | 4323 |
| mamApplicationKey |Nyckel för program som är associerade med MAM-programmet incheckning. | 432 |
| DeviceHealthKey |Nyckel för DeviceHealth som är koppla till den här incheckningen av MAM-appen. | 321 |
| PlatformKey |Visar plattformen för enheten som är kopplad till den här incheckningen av MAM-appen. |123 |
| LastCheckInDate |Datum och tid för den senaste incheckningen av MAM-appen. Värdet kan vara null. |2016-11-23 12:00:00 |

## <a name="mamdevicehealths"></a>MamDeviceHealths

Entiteten **MamDeviceHealth** motsvarar de enheter där principer för mobilappshantering (MAM) har distribuerats även om de är jailbrokade.

| Egenskap | Beskrivning | Exempel |
|---------|------------|--------|
| DeviceHealthKey |Unikt id för enheten med tillhörande hälsostatus i informationslagret – surrogatnyckel. |123 |
| DeviceHealth |Unikt id för enheten och dess tillhörande hälsostatus, liknar DeviceHealthKey men id:t är en naturlig nyckel. |b66bc706-ffff-7777-0340-032819502773 |
| DeviceHealthName |Visar enhetens status. <br>Inte tillgänglig: det finns ingen information om enheten. <br>Felfri: enheten är inte jailbrokad. <br>Ej felfri: enheten är jailbrokad. |Inte tillgänglig Felfri Ej felfri |
| RowLastModifiedDateTimeUtc |Datum och tid i UTC för senaste ändring av hälsotillståndet för mobilappshanterad enhet i informationslagret. |2016-11-23 12:00:00 |

## <a name="mamplatforms"></a>MamPlatforms

Entiteten **MamPlatform** innehåller en lista över namn på plattformar och typer där en mobilappshanterad app (MAM) har installerats.


|          Egenskap          |                                    Beskrivning                                    |                         Exempel                         |
|----------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------|
|        PlatformKey         |     Unikt id för plattformen i informationslagret – surrogatnyckel.      |                           123                           |
|          Plattform          | Unikt id för plattformen, liknar PlatformKey men är en naturlig nyckel. |                           123                           |
|        PlatformName        |                                   Namn på plattform                                   | Inte tillgängligt <br>Inga <br>Windows <br>iOS <br>Android. |
| RowLastModifiedDateTimeUtc | Datum och tid i UTC för senaste ändring av plattformen i informationslagret.  |                 2016-11-23 12:00:00                  |

## <a name="managementagenttypes"></a>managementAgentTypes
Entiteten **managementAgentType** representerar de agenter som används för att hantera en enhet.

|         Egenskap        |                                       Beskrivning                                       |
|:-----------------------:|:---------------------------------------------------------------------------------------:|
| ManagementAgentTypeID   | Unikt id för typ av hanteringsagent.                                         |
| ManagementAgentTypeKey  | Unik identifierare för typen av hanteringsagent i informationslagret – surrogatnyckel. |
| ManagementAgentTypeName | Visar vilken typ av agent som används för att hantera enheten.                              |

### <a name="example"></a>Exempel

| ManagementAgentTypeID |                Namn               |                                  Beskrivning                                 |
|:---------------------:|:---------------------------------:|:----------------------------------------------------------------------------:|
| 1                     | EAS                               | Enheten hanteras via Exchange Active Sync                         |
| 2                     | MDM                               | Enheten hanteras med hjälp av en MDM-agent                                   |
| 3                     | EasMdm                            | Enheten hanteras både av Exchange Active Sync och en MDM-agent        |
| 4                     | IntuneClient                      | Enheten hanteras av Intune PC-agenten                               |
| 5                     | EasIntuneClient                   | Enheten hanteras både av Exchange Active Sync och Intune PC-agenten |
| 8                     | ConfigManagerClient               | Enheten hanteras av System Center Configuration Manager-agenten     |
| 10                    | ConfigurationManagerClientMdm     | Enheten hanteras av Configuration Manager och MDM.                    |
| 11                    | ConfigurationManagerCLientMdmEas  | Enheten hanteras av Configuration Manager MDM- och Exchange Active Sync.               |
| 16                    | Okänt                           | Okänd typ av hanteringsagent                                              |
| 32                    | Jamf                              | Enhetens egenskaper hämtas från Jamf.                               |
| 64                    | GoogleCloudDevicePolicyController |  Enheten hanteras av Googles CloudDPC.                                 |

## <a name="managementstates"></a>managementStates
Entiteten **ManagementState** innehåller information om enhetens tillstånd. Informationen kan vara användbar i fall där fjärråtgärder tillämpas, om enheten är jailbrokad eller rotad.

|       Egenskap      |                                     Beskrivning                                    |
|:-------------------:|:----------------------------------------------------------------------------------:|
| managementStateID   | Unik identifierare för hanteringstillståndet.                                       |
| managementStateKey  | Unik identifierare för hanteringstillståndet i informationslagret – surrogatnyckel. |
| managementStateName | Visar tillståndet för fjärråtgärden som utförts på den här enheten.                 |

### <a name="example"></a>Exempel

| managementStateID |      Namn      |                                                   Beskrivning                                                   |
|:-----------------:|:--------------:|:---------------------------------------------------------------------------------------------------------------:|
| 0                 | Hanterade        | Hanterad utan väntande fjärråtgärder.                                                                       |
| 1                 | RetirePending  | Ett kommando för tillbakadragande väntar på enheten.                                                             |
| 2                 | RetireFailed   | Det gick inte att utföra kommandot för tillbakadragande på enheten.                                                                      |
| 3                 | WipePending    | Ett rensningskommando väntar på enheten.                                                               |
| 4                 | WipeFailed     | Det gick inte att utföra rensningskommandot på enheten.                                                                        |
| 5                 | Ohälsosamt      | Ej felfritt tillstånd.                                                                                              |
| 6                 | DeletePending  | Ett borttagningskommando väntar på enheten.                                                             |
| 7                 | RetireIssued   | Ett kommando om tillbakadragande har utfärdats till enheten.                                                               |
| 8                 | WipeIssued     | Ett rensningskommando har utfärdats.                                                                               |
| 9                 | WipeCanceled   | Rensningskommandot har avbrutits.                                                                               |
| 10                | RetireCanceled | Kommandot för tillbakadragande har avbrutits.                                                                             |
| 11                | Discovered     | Enheten har nyligen identifierats av Intune. När den checkar in för första gången övergår den till tillståndet hanterad. |

## <a name="mobileappinstallstates"></a>mobileAppInstallStates
Entiteten MobileAppInstallState representerar installationstillståndet för ett mobilprogram efter att det har tilldelats till en grupp som innehåller enheter och/eller användare.

|       Egenskap      |                        Beskrivning                       |
|:-------------------:|:--------------------------------------------------------:|
| AppInstallStateKey  | Unikt ID för appens installationstillstånd för ditt konto. |
| AppInstallState     | Uppräkningsvärde för appens installationstillstånd.                     |
| AppInstallStateName | Namn på appens installationstillstånd.                           |

## <a name="mobileappinstallstatuscounts"></a>mobileAppInstallStatusCounts
Representerar installationstillståndet för ett mobilprogram för en viss enhetstyp som använder hantering av mobilprogram via Microsoft Intune.

|      Egenskap      |                                                          Beskrivning                                                          |
|:------------------:|:-----------------------------------------------------------------------------------------------------------------------------:|
| DateKey            | Nyckeln för det datum då appens installationstillstånd registrerades.                                                                     |
| AppKey             | Nyckeln för mobilprogrammet som används för att identifiera en instans av AppRevision.                                                          |
| DeviceTypeKey      | Nyckeln för den enhetstyp som har kopplats till mobilprogrammet.                                                              |
| AppInstallStateKey | Nyckeln för programmets installationstillstånd som används för att identifiera en instans av MobileAppInstallState.                                         |
| Felkod          | Felkoden som returnerades av installationsprogrammet, mobilplattformen eller tjänsten som hör till programmets installation. |
| Antal              | Totalt antal.                                                                                                                  |

## <a name="ownertypes"></a>ownerTypes
Entiteten **ownerType** visar om en enhet är företagsägd, privat ägd eller okänd.

|    Egenskap   |                                                                                     Beskrivning                                                                                    |           Exempel          |
|:-------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
| ownerTypeID   | Unikt id för ägartyp.                                                                                                                                               |                            |
| ownerTypeKey  | Unik identifierare för ägartypen i informationslagret – surrogatnyckel.                                                                                                       |                            |
| ownerTypeName | Representerar ägartypen för enheterna: Företag – enheten är företagsägd.  Privat – enheten är privatägd (BYOD).   Okänd – det finns ingen information om enheten. | Företag privat okänd |

> [!Note]  
> För den `ownerTypeName` filter i AzureAD när du skapar dynamiska grupper för enheter, måste du ange värdet `deviceOwnership` som `Company`. Mer information finns i [regler för enheters](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices). 

## <a name="policies"></a>policies
Entiteten **Princip** innehåller en lista över enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

|          Egenskap          |                                                                       Beskrivning                                                                      |                Exempel               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| PolicyKey                  | Unik nyckel för principen i informationslagret.                                                                                              | 123                                  |
| PolicyId                   | Unikt id för principen i informationslagret.                                                                                                 | b66bc706-ffff-7437-0340-032819502773 |
| PolicyName                 | Namnet på principen.                                                                                                                                    | "Windows 10 Baseline"                |
| PolicyVersion              | Principversion. Varje gång principen redigeras eller ändras skapas en ny version.                                                             | 1, 2, 3                              |
| IsDeleted                  | Visar om principposten har uppdaterats.  Sant – principen innehåller en ny post med uppdaterade fält.  Falskt – den senaste posten för principen. | Sant/falskt                           |
| StartDateInclusiveUTC      | Datum och tid i UTC när principen skapades i informationslagret.                                                                              | 11/23/2016 0:00                      |
| DeletedDateUTC             | Datum och tid i UTC när IsDeleted ändrades till True.                                                                                                   | 11/23/2016 0:00                      |
| RowLastModifiedDateTimeUTC | Datum och tid i UTC när principen senast ändrades i informationslagret.                                                                        | 11/23/2016 0:00                      |

## <a name="policydeviceactivities"></a>policyDeviceActivities
Följande tabell visar antalet enheter med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer, ökar antalet lyckade med ett för den dagen. Om det finns två tilldelade principer för en enhet, en med tillståndet lyckades och en med tillståndet fel, ökar antalet lyckade och enheten försätts i feltillstånd. Entiteten **policyDeviceActivity** visar en lista över hur många enheter som har ett visst tillstånd under en viss dag inom de senaste 30 dagarna.

|  Egenskap |                                           Beskrivning                                           |        Exempel        |
|:---------:|:-----------------------------------------------------------------------------------------------:|:---------------------:|
| DateKey   | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. | 20160703              |
| Väntar   | Antalet unika enheter i väntande tillstånd.                                                    | 123                   |
| Lyckades | Antalet unika enheter med tillståndet lyckades.                                                    | 12                    |
| PolicyKey | Principnyckel, kan kopplas till princip för att hämta policyName.                                  | Windows 10-baslinje |
| Fel     | Antalet unika enheter i feltillstånd.                                                      | 10                    |
| Misslyckades    | Antalet unika enheter med tillståndet misslyckades.                                                     | 2                     |

## <a name="policyplatformtypes"></a>policyPlatformTypes

|        Egenskap        |                      Beskrivning                      |     Exempel    |
|:----------------------:|:-----------------------------------------------------:|:--------------:|
| PolicyPlatformTypeKey  | Den unika nyckeln för principens plattformstyp.        | 20170519       |
| PolicyPlatformTypeId   | Den unika identifieraren för principens plattformstyp. | 1              |
| PolicyPlatformTypeName | Namnet på principens plattformstyp.              | AndroidForWork |

## <a name="policytypeactivities"></a>policyTypeActivities
Entiteten **PolicyTypeActivity** visat det sammanlagda antalet enheter med tillståndet lyckades, väntar misslyckades eller fel. Tillståndet visas avseende enhetskonfigurationsprofil, appkonfigurationsprofil eller efterlevnadsprincip per dag.

|    Egenskap   |                                          Beskrivning                                          |           Exempel           |
|:-------------:|:---------------------------------------------------------------------------------------------:|:---------------------------:|
| DateKey       | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. | 20160703                    |
| PolicyKey     | Principnyckel, kan kopplas till princip för att hämta policyName.                                | Windows 10-baslinje         |
| PolicyTypeKey | Typ av principnyckel, kan kopplas till principtyp för att hämta namnet på principtypen.             | Windows 10-efterlevnadsprincip |
| Väntar       | Antalet unika enheter i väntande läge.                                                    | 123                         |
| Lyckades     | Antalet unika enheter med tillståndet lyckades.                                                    | 12                          |
| Fel         | Antalet unika enheter med feltillstånd.                                                      | 10                          |
| Misslyckades        | Antalet unika enheter med tillståndet misslyckades.                                                     | 2                           |

## <a name="policytypes"></a>policyTypes
Entiteten **PolicyType** innehåller en lista över typer av enhetskonfigurationsprofiler, appkonfigurationsprofiler och efterlevnadsprinciper. Principerna med hantering av mobilenheter (MDM) kan tilldelas en grupp i företaget.

|    Egenskap    |                       Beskrivning                      |            Exempel            |
|:--------------:|:------------------------------------------------------:|:-----------------------------:|
| PolicyTypeId   | Unikt id för principen i källsystemet.  | 123                           |
| PolicyTypeKey  | Unikt id för principen i informationslagret. | 1                             |
| PolicyTypeName | Namn på principtypen.                               | Windows 10-efterlevnadsprincip. |

## <a name="policyuseractivities"></a>policyUserActivities
Följande tabell visar antalet användare med tillståndet lyckades, väntar, misslyckades eller fel per dag. Siffran återger data per principtypprofil. Om en enhet exempelvis har tillståndet lyckades för alla tilldelade principer ökar antalet lyckade med ett för den dagen. Om en användare har tilldelats två profiler, en med tillståndet lyckades och den andra med tillståndet fel, räknas användaren i feltillståndet. Entiteten **PolicyUserActivity** visar en lista över hur många användare som är i ett visst tillstånd under en viss dag inom de senaste 30 dagarna.

|  Egenskap |                                          Beskrivning                                          |       Exempel       |
|:---------:|:---------------------------------------------------------------------------------------------:|:-------------------:|
| DateKey   | Datumnyckel när incheckningen av enhetskonfigurationsprofilen registrerades i informationslagret. | 20160703            |
| Väntar   | Antalet unika enheter i väntande läge.                                                    | 123                 |
| Lyckades | Antalet unika enheter med tillståndet lyckades.                                                    | 12                  |
| PolicyKey | Principnyckel, kan kopplas till princip för att hämta policyName.                                | Windows 10-baslinje |
| Fel     | Antalet unika enheter med feltillstånd.                                                      | 10                  |

## <a name="termsandconditions"></a>termsAndConditions
En **termsAndConditions**-entitet representerar metadata och innehållet i en viss villkorsprincip (T&C). Innehållet i T&C-principer visas för användare vid det första försöket att registrera i Intune och därefter vid redigeringar där en administratör kräver nytt godkännande. De gör det möjligt för administratörer att meddela användare vad de måste godkänna för att registrera enheter i Intune.

|    Egenskap        |    Beskrivning    |    Exempel        |
|----------------------------------|-----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
|    termsAndConditionsKey    |    En nyckel som motsvarar en post i samlingen userTermsAndConditionsAcceptances    |    123    |
|    termsAndCondidionsId    |    ID för termsAndConditions-posten    |    276edcb7-7440-4339-b6c5-8b6fc556fee6    |
|    termsAndConditionsVersion    |    Versionen för villkorsposten    |    1    |
|    name    |    Namnet på termsAndConditions-posten.        |    Intune-villkor     |
|    description    |    Beskrivningen av dessa villkor.     |         |
|    title    |    Rubriken för dessa villkor.     |    Företagsprincip för enhetshantering        |
|    summaryOfTerms    |    Sammanfattningen av villkoren som tilldelats användaren.     |    Jag samtycker till villkoren.    |
|    termsAndConditionsBodyText    |    Villkorens brödtext.       |    *Enhetskryptering* Tillämpning av 6-siffrig PIN-kod    |
|    isDeleted    |    Sant eller falskt för om det här värdet har tagits bort.     |    Falskt    |
|    startDateInclusiveUTC    |    Startdatumet för dessa villkor.     |    8/23/2018 4:01:34 AM    |
|    endDateEclusiveUTC    |    Slutdatumet för dessa villkor.     |    12/31/9999 12:00:00 AM    |

## <a name="userdeviceassociations"></a>userDeviceAssociations
Entiteten **Användarenhetsassociation** innehåller användarenhetsassociationer i din organisation.

|        Namn        |                                             Beskrivning                                            |     Exempel     |
|:------------------:|:--------------------------------------------------------------------------------------------------:|:---------------:|
| UserKey            | Unikt id för användaren i informationslagret.   (Surrogatnyckel).                            | 123             |
| DeviceKey          | Unikt id för enheten i informationslagret.                                             | 123             |
| CreatedDateTimeUTC | Datum och tid när användarenhetsassociationen skapades. Använder UTC-formatet.                     | 11/23/2016 0:00 |
| IsDeleted          | Anger att användaren har avregistrerat enheten och att associationen inte längre är aktuell. | Sant/falskt      |
| EndedDateTimeUTC   | Datum och tid i UTC när IsDeleted ändrades till True.                                               | 6/23/2017 0:00  |

## <a name="users"></a>användare
Entiteten **user** visar en lista över alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i företaget.

Entitetssamlingen **user** innehåller användardata. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data från föregående månad. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

|          Egenskap          |                                                                                                           Beskrivning                                                                                                          |                Exempel               |
|:--------------------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------:|
| UserKey                    | Unik identifierare för användaren i informationslagret – surrogatnyckel.                                                                                                                                                         | 123                                  |
| UserId                     | Unik identifierare för användaren, liknar UserKey men är en naturlig nyckel.                                                                                                                                                    | b66bc706-ffff-7437-0340-032819502773 |
| UserEmail                  | Användarens e-postadress.                                                                                                                                                                                                     | John@constoso.com                    |
| userPrincipalName                        | Användarens huvudnamn.                                                                                                                                                                                               | John@constoso.com                    |
| DisplayName                | Användarens visningsnamn.                                                                                                                                                                                                      | John                                 |
| IntuneLicensed             | Anger om användaren är Intune-licensierad eller inte.                                                                                                                                                                              | Sant/falskt                           |
| IsDeleted                  | Anger om alla användarens licenser har gått ut och om användaren därför har tagits bort från Intune. Den här flaggan ändras inte för en enskild post. I stället skapas en ny post för ett nytt användartillstånd. | Sant/falskt                           |
| RowLastModifiedDateTimeUTC | Datum och tid i UTC när posten senast ändrades i informationslagret                                                                                                                                                 | 11/23/2016 0:00                      |

## <a name="usertermsandconditionsacceptances"></a>userTermsAndConditionsAcceptances
En **userTermsAndConditionsAcceptance**-entitet representerar godkännandestatusen för en viss villkorspolicy (T&C) för en viss användare. Användare måste godkänna den senaste versionen av villkoren för att behålla åtkomst till företagsportalen.

|    Egenskap    |    Beskrivning    |    Exempel    |
|-------------------------------|--------------------------------------------------------------------------------|----------------------------|
|    dateKey    |    En nyckel som motsvarar ett datumvärde i samlingen ”datum”.     |    20180823    |
|    userKey    |    En användarnyckel som mappar till en användare i samlingen ”användare”.     |    20000    |
|    termsAndConditionsKey    |    En nyckel som motsvarar en post i samlingen ”termsAndConditions”    |    1    |
|    acceptedDateTimeUTC    |    Tiden då användaren accepterade dessa villkor    |    8/23/2018 4:01:34 AM    |
|    lastModifiedDateTimeUTC    |    Den senaste gången som den här posten ändrades.     |    8/23/2018 4:01:34 AM    |

## <a name="vppprogramtypes"></a>vppProgramTypes 
Entiteten **vppProgramType** innehåller en lista över möjliga typer av volymköpsprogram för en app.

|      Egenskap      |          Beskrivning         |
|:------------------:|:----------------------------:|
| VppProgramTypeID   | ID för typen.           |
| VppProgramTypeKey  | Surrogatnyckel för nyckeln. |
| VppProgramTypeName | Typ av volymköpsprogram.          |

### <a name="example"></a>Exempel

|             VppProgramID             |         Namn        | Beskrivning                |
|:------------------------------------:|:-------------------:|----------------------------|
| 3DDA2474-470B-4503-9830-2665C21C1945 | Microsoft           | Microsofts volymköpsprogram. |
| 00000000-0000-0000-0000-000000000000 | Inte tillgängligt än | Standardvärde, inget volymköpsprogram.   |
| B54814E0-68EA-4BA4-8088-B5AAB58E737B | Apple               | Apples volymköpsprogram.     |

## <a name="next-steps"></a>Nästa steg

Mer information om Intune-informationslagret finns i [Datamodellen för informationslagret](https://docs.microsoft.com/intune/reports-ref-data-model).

