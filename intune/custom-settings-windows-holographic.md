---
title: Anpassade inställningar – Windows Holographic for Business-enheter – Microsoft Intune
description: Lägg till eller skapa en anpassad profil för att använda OMA-URI-inställningar för enheter som kör Windows Holographic for Business i Microsoft Intune, inklusive Microsoft Hololens. Du kan ange CSP-principinställningarna AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates och ApplicationLaunchRestrictions.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.article: article
ms.prod: ''
ms.service: microsoft-intune
ms.topic: article
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 2c4e6041f00ad55b18f8b20996da8002f5ce0247
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032205"
---
# <a name="use-custom-settings-for-windows-holographic-for-business-devices-in-intune"></a>Använda anpassade inställningar för Windows Holographic for Business-enheter i Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina Windows Holographic for Business-enheter med hjälp av ”anpassade profiler”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

Windows Holographic for Business-anpassade profiler använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera olika funktioner. De här inställningarna används vanligtvis av tillverkare av mobila enheter till att styra funktioner på enheten.

Windows Holographic for Business gör många inställningar för konfigurationstjänstleverantörer tillgängliga. En översikt över CSP finns i [Introduction to configuration service providers (CSPs) for IT pros](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) (Introduktion till konfigurationstjänstleverantörer (CSP:er) för IT-proffs). Specifika CSP:er som stöds av Windows Holographic visas i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic).

Glöm inte att [Windows Holographic for Business-enhetsbegränsningsprofilen](device-restrictions-windows-holographic.md) innehåller många inbyggda inställningar som du kan använda. Det betyder att du kanske inte behöver ange anpassade värden.

Den här artikeln beskriver hur du skapar en anpassad profil för Windows Holographic for Business-enheter. Den innehåller också en lista med rekommenderade OMA-URI-inställningar.

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `hololens custom profile`.
    - **Beskrivning**: Ange en beskrivning av profilen.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
    - **OMA-URI** (skiftlägeskänslig): Ange den OMA-URI som du vill använda som inställning.
    - **Datatyp**: Välj den datatyp som du vill använda för den här OMA-URI-inställningen. Alternativen är:

        - Sträng
        - Sträng (XML-fil)
        - Datum och tid
        - Heltal
        - Flyttal
        - Boolesk
        - Base64 (fil)

    - **Värde**: Ange det datavärde som du vill associera med den OMA-URI som du har angett. Värdet beror på vilken datatyp du valt. Om du till exempel valde **Datum och tid**, väljer du värdet från en datumväljare.

    När du har lagt till några inställningar kan du välja **Exportera**. **Exportera** skapar en lista över alla värden som du har lagt till i en fil med kommaavgränsade värden (.csv).

5. Klicka på **OK** för att spara ändringarna. Fortsätt att lägga till fler inställningar efter behov.
6. När du är klar väljer du **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.

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

Du hittar en fullständig lista över alla konfigurationstjänstleverantörer (CSP:er) som Windows Holographic har stöd för i [CSPs supported in Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) (CSP:er som stöds i Windows Holographic). Alla inställningar är inte kompatibla med alla versioner av Windows Holographic. Tabellen i avsnittet med [CSP:er som stöds i Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens) innehåller en lista över versionerna som stöds för varje CSP.

Observera att Intune inte stöder alla inställningar som anges i avsnittet med [CSP:er som stöds i Windows Holographic](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#hololens). Om du vill veta om Intune har stöd för den inställning som du vill använda, kan du öppna artikeln för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).

Se hur du skapar en anpassad profil på [Windows 10-enheter](custom-settings-windows-10.md).