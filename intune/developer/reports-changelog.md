---
title: Ändringslogg för Intune-informationslagret
titleSuffix: Microsoft Intune
description: Det här avsnittet innehåller en lista med ändringar för Microsoft Intune-informationslagrets API.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9740eed3ab727d76a9af4e46642d8279b310fd9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490520"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Ändringslogg för Intunes informationslager-API

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Håll dig uppdaterad om uppdateringar för Intune-informationslagret.

## <a name="1903-part-2"></a>1903 (del 2)
_Publicerad i april 2019_

### <a name="beta-changes"></a>Betaändringar

I följande tabell visas de senaste borttagna samlingarna och ersättningarna i Intune-informationslagret.

|    Samling                          |    Ändra     |    Ytterligare information                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    mobileAppDeviceUserInstallStatus    |    Borttaget    |    Använd [mobileAppInstallStatusCounts](intune-data-warehouse-collections.md#mobileappinstallstatuscounts) i stället.                                                                                                                                                                                                                                                                     |
|    EnrollmentTypes                     |    Borttaget    |    Använd [deviceEnrollmentTypes](intune-data-warehouse-collections.md#deviceenrollmenttypes) i stället.                                                                                                                                                                                                                                                                                      |
|    mdmStatuses                         |    Borttaget    |    Använd [complianceStates](intune-data-warehouse-collections.md#compliancestates) i stället.                                                                                                                                                                                                                                                                                               |
|    workPlaceJoinStateTypes             |    Borttaget    |    Använd `azureAdRegistered`-egenskapen i [devices](intune-data-warehouse-collections.md#devices)- och [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories)-samlingarna i stället.                                                                                                                                                                                                             |
|    ClientRegistrationStateTypes        |    Borttaget    |    Använd [deviceRegistrationStates](intune-data-warehouse-collections.md#deviceregistrationstates) i stället.                                                                                                                                                                                                                                                                             |
|    currentUser                         |    Borttaget    |    Använd [users](intune-data-warehouse-collections.md#users)-samlingen i stället.                                                                                                                                                                                                                                                                                                      |
|    mdmDeviceInventoryHistories         |    Borttaget    |    Många av egenskaperna var redundanta eller finns nu i [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories)- eller [devices](intune-data-warehouse-collections.md#devices)-samlingen. **mdmDeviceInventoryHistories**-egenskaper som inte redan visas i listan med de här två samlingarna är inte längre tillgängliga. Se informationen nedan.    |

I följande tabell visas de gamla egenskaper som tidigare ingick i **mdmDeviceInventoryHistories**-samlingen och ändringen/ersättningen. Egenskaper som fanns i **mdmDeviceInventoryHistories** men som inte visas nedan har tagits bort.

|    Tidigare egenskap                |    Ändring/ersättning                                                           |
|--------------------------------|---------------------------------------------------------------------------------|
|    cellularTechnology          |    cellularTechnology i devices-samlingen                                     |
|    deviceClientId              |    deviceId i devices-samlingen                                               |
|    deviceManufacturer          |    manufacturer i devices-samlingen                                           |
|    deviceModel                 |    model i devices-samlingen                                                  |
|    deviceName                  |    deviceName i devices-samlingen                                             |
|    deviceOsPlatform            |    deviceTypeKey i devices-samlingen                                          |
|    deviceOsVersion             |    osVersion i devicePropertyHistories-samlingen                              |
|    deviceType                  |    deviceTypeKey i devices-samlingen, som refererar till deviceTypes-samlingen    |
|    encryptionState             |    encryptionState-egenskap i devices-samlingen                           |
|    exchangeActiveSyncId        |    easDeviceId-egenskap i devices-samlingen                               |
|    exchangeDeviceId            |    easDeviceId i devices-samlingen                                            |
|    imei                        |    imei i devices-samlingen                                                   |
|    isSupervised                |    isSupervised-egenskap i devices-samlingen                              |
|    jailBroken                  |    jailBroken i devicePropertyHistories-samlingen                             |
|    meid                        |    meid-egenskap i devices-samlingen                                      |
|    oem                         |    manufacturer i devices-samlingen                                           |
|    osName                      |    deviceTypeKey i devices-samlingen, som refererar till deviceTypes-samlingen    |
|    phoneNumber                 |    phoneNumber i devices-samlingen                                            |
|    platformType                |    model i devices-samlingen                                                  |
|    product                     |    deviceTypeKey i devices-samlingen                                          |
|    productVersion              |    osVersion i devicePropertyHistories-samlingen                              |
|    serialNumber                |    serialNumber i devices-samlingen                                           |
|    storageFree                 |    freeStorageSpaceInBytes property i devices-samlingen                   |
|    storageTotal                |    totalStorageSpaceInBytes-egenskap i devices-samlingen                |
|    subscriberCarrierNetwork    |    subscriberCarrier-egenskap i devices-samlingen                         |
|    wifimac                     |    wiFiMacAddress i devices-samlingen                                         |

I följande tabell visas ändringar av egenskaper som finns i [devicePropertyHistories](intune-data-warehouse-collections.md#devicepropertyhistories)-samlingen: 

|    Tidigare egenskap                  |    Ändring/ersättning                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, som refererar till deviceCategories-samlingen       |
|    certExpirationDate            |    Borttaget                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime i devices-samlingen                           |
|    deviceTypeKey                 |    deviceTypeKey i devices-samlingen                              |
|    easID                         |    easDeviceId i devices-samlingen                                |
|    enrolledByUser                |    userId i devices-samlingen                                     |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey i devices-samlingen                    |
|    graphDeviceIsCompliant        |    Borttaget                                                          |
|    graphDeviceIsManaged          |    Borttaget                                                          |
|    lastContact                   |    lastSyncDateTime i devices-samlingen                           |
|    lastContactNotification       |    Borttaget                                                          |
|    lastContactWorkplaceJoin      |    Borttaget                                                          |
|    lastExchangeStatusUtc         |    Borttaget                                                          |
|    lastModifiedDateTimeUTC       |    Borttaget                                                          |
|    lastPolicyUpdateUtc           |    Borttaget                                                          |
|    managementAgentKey            |    managementStateKey                                               |
|    manufacturer                  |    manufacturer i devices-samlingen                               |
|    mdmStatusKey                  |    complianceStateKey, som refererar till complianceStates-samlingen    |
|    modell                         |    model i devices-samlingen                                      |
|    osFamily                      |    operatingSystem i devices-samlingen                            |
|    osRevisionNumber              |    osVersion i devices-samlingen                                  |
|    processorArchitecture         |    Borttaget                                                          |
|    referenceId                   |    azureAdDeviceId i devices-samlingen                            |
|    serialNumber                  |    serialNumber i devices-samlingen                               |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

I följande tabell visas ändringar av egenskaper som finns i [devices](intune-data-warehouse-collections.md#devices)-samlingen: 

|    Tidigare egenskap                  |    Ändring/ersättning                                               |
|----------------------------------|---------------------------------------------------------------------|
|    categoryId                    |    deviceCategoryKey, som refererar till deviceCategories-samlingen       |
|    certExpirationDate            |    Borttaget                                                          |
|    clientRegistrationStateKey    |    deviceRegistrationStateKey                                       |
|    createdDate                   |    enrolledDateTime                                                 |
|    easId                         |    easDeviceId                                                      |
|    enrolledByUser                |    userId                                                           |
|    enrollmentTypeKey             |    deviceEnrollmentTypeKey                                          |
|    graphDeviceIsCompliant        |    Borttaget                                                          |
|    graphDeviceIsManaged          |    Borttaget                                                          |
|    lastContact                   |    lastSyncDateTime                                                 |
|    lastContactNotification       |    Borttaget                                                          |
|    lastContactWorkplaceJoin      |    Borttaget                                                          |
|    lastExchangeStatusUtc         |    Borttaget                                                          |
|    lastPolicyUpdateUtc           |    Borttaget                                                          |
|    mdmStatusKey                  |    complianceStateKey, som refererar till complianceStates-samlingen    |
|    osFamily                      |    operatingSystem                                                  |
|    processorArchitecture         |    Borttaget                                                          |
|    referenceId                   |    azureAdDeviceId                                                  |
|    workplaceJoinStateKey         |    azureAdRegistered                                                |

I följande tabell visas ändringar av egenskaper som finns i [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities)-samlingen: 

|    Tidigare egenskap         |    Ändring/ersättning         |
|-------------------------|-------------------------------|
|    enrollmentTypeKey    |    deviceEnrollmentTypeKey    |

I följande tabell visas ändringar av egenskaper som finns i [mamApplications](intune-data-warehouse-collections.md#mamapplications)-samlingen: 

|    Tidigare egenskap       |    Ändring/ersättning    |
|-----------------------|--------------------------|
|    applicationKey     |    mamApplicationKey     |
|    applicationName    |    mamApplicationName    |
|    applicationId      |    mamApplicationId      |

I följande tabell visas ändringar av egenskaper som finns i [mamApplicationInstances](intune-data-warehouse-collections.md#mamapplicationinstances)-samlingen: 

|    Tidigare egenskap     |    Ändring/ersättning    |
|---------------------|--------------------------|
|    applicationId    |    mamApplicationId      |
|    deviceId         |    mamDeviceId           |
|    deviceType       |    mamDeviceType         |
|    deviceName       |    mamDeviceName         |

I följande tabell visas ändringar av egenskaper som finns i [mamCheckins](intune-data-warehouse-collections.md#mamcheckins)-samlingen: 

|    Tidigare egenskap      |    Ändring/ersättning    |
|----------------------|--------------------------|
|    applicationKey    |    mamApplicationKey     |

I följande tabell visas ändringar av egenskaper som finns i [users](intune-data-warehouse-collections.md#users)-samlingen: 

|    Tidigare egenskap             |    Ändring/ersättning    |
|-----------------------------|--------------------------|
|    startDateInclusiveUtc    |    Borttaget               |
|    endDateInclusiveUtc      |    Borttaget               |
|    isCurrent                |    Borttaget               |

## <a name="1903"></a>1903
_Utgiven mars 2019_

### <a name="v10-changes-reflecting-back-to-beta"></a>V1.0-ändringar som återspeglas i betaversionen
När V1.0 introducerades i 1808 skiljde den sig från beta-API:et på några betydande sätt. I 1903 återspeglas ändringarna tillbaka till beta-API-versionen. Om du har viktiga rapporter som använder beta-API-versionen rekommenderar vi starkt att du växlar de rapporterna till V1.0 för att undvika icke-bakåtkompatibla ändringar. Mer information om API-versioner för Data Warehouse och bakåtkompatibilitet finns i avsnittet med [API-versionsinformation](../reports-api-url.md). 

## <a name="1902"></a>1902 
_Publicerat i februari 2019_

### <a name="power-bi-compliance-app"></a>Power BI-efterlevnadsapp 

Få åtkomst till ditt Intune-informationslager i Power BI Online med hjälp av [Intune-efterlevnadsappen (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Med den här Power BI-appen kan du nu komma åt och dela i förväg skapade rapporter utan någon konfiguration och utan att lämna webbläsaren. 

> [!NOTE]
> Det finns ytterligare två filter som du kan använda för appen Intune Compliance.

#### <a name="add-additional-filters-to-the-intune-compliance-app"></a>Lägga till ytterligare filter i Intune Compliance-appen
1. Öppna appen [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) i webbläsaren.
2. Klicka på **Inkompatibla enheter** och välj **Inkompatibel** i **complianceStatus**-filtret. 
3. Klicka på **Okända enheter** och välj **Inte tillgängligt ännu** i **complianceStatus**-filtret. 

## <a name="1812"></a>1812 
_Publicerad december 2018_

### <a name="enrollment-activities-collection-released-to-v10"></a>Samlingen Registreringsaktiviteter har släppts som v1.0 

Samlingen Registreringsaktiviteter finns nu i v1.0. Du kan använda den här samlingen för att förstå volym och trender för registreringsfel i din miljö. Mer information finns i [enrollmentActivities](intune-data-warehouse-collections.md#enrollmentactivities), [enrollmentEventStatuses](intune-data-warehouse-collections.md#enrollmenteventstatuses), [enrollmentFailureCategories](intune-data-warehouse-collections.md#enrollmentfailurecategories) och [ enrollmentFailureReasons](intune-data-warehouse-collections.md#enrollmentfailurereasons).

## <a name="1808"></a>1808
_Publicerad augusti 2018_

### <a name="v10-collections"></a>v1.0-samlingar  

Det går nu att använda v1.0-versionen av Intune-informationslagret genom att ange frågeparametern `api-version=v1.0`. Uppdateringar av samlingar i datalagret är additiva och avbryter inte befintliga scenarier.

### <a name="enrollment-activities-collection-released-to-beta"></a>Samlingen Registreringsaktiviteter har släppts som betaversion

Den nya samlingen `Enrollment Activities` har släppts som betaversion. Du kan använda den här samlingen för att förstå hur registreringen framskrider genom att granska de vanligaste felen. 


## <a name="1805"></a>1805
_Utgiven: maj 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Korrigering av antal enheter i samlingen **Enheter** 

En korrigering har gjorts till samlingen **Enheter** som kan minska det totala antalet enheter som filtreras med attributet `isDeleted`. Den här sänkningen är ett resultat av korrigeringen och är inte ett fel. Mer information om samlingen **enheter** finns i [Referens för enhetsentiteter](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Publicerad i januari 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autentisering för enbart Intune-informationslagerprogram <!-- 1867540 -->

Du kan konfigurera ett program med Azure Active Directory (Azure AD) och autentisera till Intune-informationslagret. Mer information finns i [Autentisering endast med program för Intune-informationslager](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter <!-- 2077525 -->

- Det krävs inte längre att någon Intune-licens tilldelas till användaren vid åtkomst till Intune-informationslagret (inklusive API).
- Intune-rollnamnet har ändrats från **Rapporter** till **Intune-informationslager**. 

    Mer information finns i [Krav på Azure AD- och Intune-autentiseringsuppgifter](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>OData-frågealternativ <!-- 2077711 -->

Du kan använda <code>$select</code> som en OData-frågeparameter. Den aktuella versionen har stöd för följande OData-frågeparametrar: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> och <code>$top</code>. Mer information finns i [OData-frågealternativ](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nya entiteter i datamodellen för informationslager <!-- 2077804 -->

- Entiteten [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md) har lagts till. **MobileAppDeviceUserInstallStatus** representerar en mobilapps installationstillstånd för en viss enhet och en användare.
- Entiteten [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstates) har lagts till. Entiteten **MobileAppInstallState** visar installationsstatus för ett mobilt program när det har tilldelats till en grupp som innehåller enheter och/eller användare. 

## <a name="1710"></a>1710
_Publicerat november 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>En ny entitetssamling med namnet Aktuell användare är begränsad till för närvarande aktiva användardata <!-- 1544273 -->

Entitetssamlingen **Användare** innehåller alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

Den nya entitetssamlingen **aktuell användare** innehåller däremot bara användare som inte har tagits bort. Entitetssamlingen **aktuell användare** innehåller bara användare som är aktiva för tillfället. Mer information om entitetssamlingen **aktuell användare** finns i [referens för den aktuella användarentiteten](../reports-ref-current-user.md).

## <a name="1709"></a>1709
_Publicerad oktober 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Användarenhetens associationsentitetssamling lades till i datamodellen för Intunes informationslager <!-- 1187917 -->

Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar. Datamodellen kan nås via Power BI-filen (PBIX) som hämtas från Intune-sidan Informationslager via OData-slutpunkten, eller genom att utveckla en anpassad klient. Mer information finns i [användarenhetens associering](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nya entiteter i datamodellen för informationslager <!-- 1479526 --><!-- -->

- Entiteten [**UserDeviceAssociation**](reports-ref-user-device.md) har lagts till. **UserDeviceAssociation** innehåller användarenhetsassociationer i din organisation. Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar.  
- Entiteten, [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md), har lagts till. **IntuneManagementExtension** innehåller entiteter för mobila enheter som spårar information, t.ex. version och installationsstatus.

## <a name="next-steps"></a>Nästa steg
- Läs mer om [vad som är nytt i Intune varje vecka](../fundamentals/whats-new.md). Du kan också läsa mer om kommande ändringar, viktiga meddelanden om tjänsten och information om tidigare versioner.
- Läs [Microsoft Intune-bloggen](https://go.microsoft.com/fwlink/?LinkID=273882).
