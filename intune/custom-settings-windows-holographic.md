---
title: Anpassade inställningar för Windows Holographic for Business-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en anpassad profil för att använda OMA-URI-inställningarna för enheter som kör Windows Holographic for Business i Microsoft Intune. Du kan ange CSP-principinställningarna AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates och ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/26/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7272e8e088ae2c2ecad1756233281c42a80a279b
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "32328086"
---
# <a name="custom-device-settings-for-devices-running-windows-holographic-for-business-in-intune"></a>Anpassade enhetsinställningar för enheter som kör Windows Holographic for Business i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows Holographic for Business för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. Windows Holographic for Business gör många inställningar för konfigurationstjänstleverantörer tillgängliga. En översikt över CSP finns i [Introduction to configuration service providers (CSPs) for IT pros](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) (Introduktion till konfigurationstjänstleverantörer (CSP:er) för IT-proffs). Specifika CSP:er som stöds av Windows Holographic visas i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic).

Kom ihåg att om du letar efter en viss inställning så innehåller [enhetsbegränsningsprofilen i Windows Holographic for Business](device-restrictions-windows-holographic.md) många inställningar som är inbyggda och som innebär att du inte behöver ange några anpassade värden.

## <a name="create-the-custom-oma-uri-profile"></a>Skapa en anpassad OMA-URI-profil

1. Kom igång med hjälp av anvisningarna i [Konfigurera anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. I **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På sidan **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
4. Ange följande information för varje OMA-URI-inställning som du vill lägga till:
  - **Inställningsnamn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
  - **Inställningsbeskrivning**: Ange en beskrivning för inställningen.
  - **Datatyp**: Välj bland:
    - **Sträng**
    - **Sträng (XML)**
    - **Datum och tid**
    - **Heltal**
    - **Flyttal**
    - **Boolesk**
  - **OMA-URI (skiftlägeskänslig)**: Ange den OMA-URI som du vill tillhandahålla en inställning för.
  - **Värde**: Ange det värde som du vill associera med den OMA-URI som du har angett.
5. När du är klar går du tillbaka till **Skapa profil** och trycker på **Skapa**. Profilen skapas och visas i profillistan.

## <a name="recommended-custom-settings"></a>Rekommenderade anpassade inställningar

Följande inställningar är användbara för enheter som kör Windows Holographic for Business:

### <a name="allowfastreconnecthttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-authenticationauthentication-allowfastreconnect"></a>[AllowFastReconnect](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect|Heltal<br/>0 – inte tillåten<br/>1 – tillåten (standard)|

### <a name="allowupdateservicehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-allowupdateservice"></a>[AllowUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/AllowUpdateService|Heltal<br/>0 – Uppdateringstjänsten är inte tillåten <br/>1 – Uppdateringstjänsten är tillåten (standard).|

### <a name="allowvpnhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-settingssettings-allowvpn"></a>[AllowVPN](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Settings/AllowVPN|Heltal<br/>0 – inte tillåten<br/>1 – tillåten (standard)|

### <a name="requireupdatesapprovalhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-requireupdateapproval"></a>[RequireUpdatesApproval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval|Heltal<br/>0 – Inte konfigurerat. Enheten installerar alla tillämpliga uppdateringar.<br/>1 – Enheten installerar endast uppdateringar som både är tillämpliga och finns i listan med godkända uppdateringar. Ställ in principen på 1 om IT-avdelningen vill styra distributionen av uppdateringar till enheter, till exempel när testning krävs före distributionen.|

### <a name="scheduledinstalltimehttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-scheduledinstalltime"></a>[ScheduledInstallTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|Heltal 0–23, där 0 = 12AM och 23 = 11PM<br/>Standardvärdet är 3.|

### <a name="updateserviceurlhttpsdocsmicrosoftcomwindowsclient-managementmdmpolicy-csp-updateupdate-updateserviceurl"></a>[UpdateServiceURL](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl|Sträng<br/>URL – Enheten söker efter uppdateringar från WSUS-servern med angiven URL.<br/>Inte konfigurerad – Enheten söker efter uppdateringar från Microsoft Update.|

### <a name="approvedupdateshttpsdocsmicrosoftcomwindowsclient-managementmdmupdate-csp"></a>[ApprovedUpdates](https://docs.microsoft.com/windows/client-management/mdm/update-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |---|---|
> |./Vendor/MSFT/Update/ApprovedUpdates/*GUID*<br/><br/>**Viktigt!**<br/>Du måste läsa och godkänna uppdateringens användaravtal åt dina slutanvändare. Om detta inte utförs uppstår en juridisk säkerhetsöverträdelse eller ett avtalsbrott.|Nod för godkännanden av uppdateringar och licensavtal åt slutanvändaren.<br/><br/>Mer information finns i [Uppdatera CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp).|

### <a name="applicationlaunchrestrictionshttpsdocsmicrosoftcomwindowsclient-managementmdmapplocker-csp"></a>[ApplicationLaunchRestrictions](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy<br/><br/>**Viktigt!**<br/>I AppLocker CSP-artikeln används undantagna XML-exempel. Om du vill konfigurera inställningarna med anpassade Intune-profiler, måste du använda vanlig XML.|Sträng<br/>Mer information finns i [AppLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp).|

### <a name="deletionpolicyhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[DeletionPolicy](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy|Heltal<br/>0 – ta bort omedelbart när enheten återgår till ett tillstånd utan aktiva användare<br/>1 – ta bort vid tröskelvärde för lagringskapacitet (standard)<br/>2 – ta bort både vid tröskelvärde för lagringskapacitet och vid tröskelvärde för profilinaktivitet|

### <a name="enableprofilemanagerhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[EnableProfileManager](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager|Boolesk<br/>True – aktivera<br/>False – inaktivera (standard)|

### <a name="profileinactivitythresholdhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[ProfileInactivityThreshold](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold|Heltal<br/>Standardvärdet är 30.|


### <a name="storagecapacitystartdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStartDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion|Heltal<br/>Standardvärdet är 25.|

### <a name="storagecapacitystopdeletionhttpsdocsmicrosoftcomwindowsclient-managementmdmaccountmanagement-csp"></a>[StorageCapacityStopDeletion](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)

> [!div class="mx-tableFixed"]
> |OMA-URI|Datatyp|
> |----|---|
> |./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion|Heltal<br/>Standardvärdet är 50.|

## <a name="find-the-policies-you-can-configure"></a>Hitta principer som du kan konfigurera

Du hittar en fullständig lista över alla konfigurationstjänstleverantörer (CSP:er) som Windows Holographic har stöd för i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic). Alla inställningar är inte kompatibla med alla versioner av Windows Holographic. I tabellen i Windows-artikeln visas vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i artikeln. Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.
