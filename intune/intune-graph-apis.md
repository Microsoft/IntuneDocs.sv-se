---
title: Använda Azure AD för att få åtkomst till Intune API:er i Microsoft Graph
titlesuffix: Microsoft Intune
description: Beskriver de steg som krävs för att appar ska kunna använda Azure AD till att få åtkomst till Intune API:er i Microsoft Graph.
keywords: intune graphapi c# powershell permission roles
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8625eddaa3c6223767c7c93022275b028b4a145b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566564"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Använda Azure AD för att få åtkomst till Intune API:er i Microsoft Graph

[Microsoft Graph API](https://developer.microsoft.com/graph/) har nu stöd för Microsoft Intune med specifika API:er och behörighetsroller.  Microsoft Graph API använder Azure Active Directory (Azure AD) för autentisering och åtkomstkontroll.  
För åtkomst till Intune API:er i Microsoft Graph krävs:

- Ett program-ID med:

    - Behörighet att anropa Azure AD och Microsoft Graph API:er.
    - Behörighetsomfattning som avser aktiviteter för specifika program.

- Användarautentiseringsuppgifter med:

    - Behörighet att få åtkomst till Azure AD-klienten som är associerad med programmet.
    - Rollbehörigheter krävs för att stödja behörighetsomfattningen för programmet.

- Slutanvändaren kan bevilja behörighet så att appen kan utföra uppgifter för program i sin Azure-klient.

Den här artikeln:

- Visar hur du registrerar ett program med åtkomst till Microsoft Graph API och relevanta behörighetsroller.

- Beskriver Intune API:ns behörighetsroller.

- Visar exempel på autentisering av Intune API för C# och PowerShell.

- Beskriver hur du ger stöd för flera klientorganisationer.

Mer information finns i:

- [Bevilja åtkomst till webbprogram med hjälp av OAuth 2.0 och Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Komma igång med Azure AD-autentisering](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Integrera program med Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [Förstå OAuth 2.0](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Registrera appar för att använda Microsoft Graph API

Registrera en app för att använda Microsoft Graph API:

1.  Logga in på [Azure-portalen](https://portal.azure.com) med administratörsautentisering.

    Om det behövs kan du använda:
    - Klientorganisationens administratörskonto.
    - Ett användarkonto för klientorganisationen med inställningen **Användare kan registrera program** aktiverad.

2.  I menyn väljer du **Azure Active Directory** &gt; **Appregistreringar**.

    <img src="./media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3.  Välj antingen **Ny programregistrering** för att skapa ett nytt program eller välj ett befintligt program.  (Om du väljer ett befintligt program hoppar du över nästa steg.)

4.  Ange följande på bladet **Skapa**:

    1.  Ett **Namn** på programmet (visas när användarna loggar in).

    2.  Värden för **Programtyp** och **Omdirigerings-URI**.

        Dessa varierar beroende på dina krav. Om du till exempel använder ett Azure AD-[autentiseringsbibliotek](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL), anger du **Programtyp** till `Native` och **Omdirigerings-URI** till `urn:ietf:wg:oauth:2.0:oob`.

        <img src="media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        Läs mer i [Autentiseringsscenarier för Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios).

5.  I programbladet:

    1.  Observera värdet för **Program-ID**.

    2.  Välj **Inställningar** &gt; **API-åtkomst** &gt; **Nödvändiga behörigheter**.

    <img src="media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6.  På bladet **Nödvändiga behörigheter** väljer du **Lägg till** &gt; **Lägg till API-åtkomst** &gt; **Välj en API**.

    <img src="media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7.  På bladet **Välj en API** väljer du **Microsoft Graph** &gt; **Välj**.  Bladet **Aktivera åtkomst** öppnas och visar en lista över de behörighetsomfattningar som är tillgängliga för ditt program.

    <img src="media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    Välj de roller som krävs för din app genom att göra en bockmarkering till vänster om namnen.  Mer information om specifika behörighetsomfattningar för Intune finns i [Intunes behörighetsomfattningar](#intune-permission-scopes).  Mer information om andra behörighetsomfattningar för Graph API finns i [Behörighetsreferens för Microsoft Graph](https://developer.microsoft.com/graph/docs/concepts/permissions_reference).

    För att få bäst resultat väljer du det minsta antal roller som krävs för att implementera ditt program.

    När du är klar väljer du **Välj** och **Klar** för att spara ändringarna.

Du kan nu också:

- Välja att bevilja behörighet för att alla klientkonton ska kunna använda appen utan att ange autentiseringsuppgifter.  

    Om du vill göra detta väljer du **Bevilja behörigheter** och godkänner bekräftelsefrågan.

    När du kör programmet första gången uppmanas du att ge appen behörighet att utföra de valda rollerna.

    <img src="media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- Gör appen tillgänglig för användare utanför din klientorganisation.  (Detta krävs vanligtvis endast för partners som har stöd för flera innehavare/organisationer.)  

    Så här gör du:

  1. Välj **Manifest** från programbladet. Bladet **Redigera manifest** öppnas.

     <img src="media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. Ändra värdet i inställningen `availableToOtherTenants` till `true`.

  3. Spara ändringarna.

## <a name="intune-permission-scopes"></a>Behörighetsomfattningar för Intune

Azure AD och Microsoft Graph använder behörighetsomfattningar för att styra åtkomsten till företagets resurser.  

Behörighetsomfattningen (kallas även _OAuth-omfattningar_) styr åtkomsten till specifika Intune-entiteter och deras egenskaper. Det här avsnittet sammanfattar behörighetsomfattningarna för Intune API-funktionerna.

Mer information:
- [Azure AD-autentisering](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [Behörighetsomfattningar för program](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

När du beviljar behörighet för Microsoft Graph kan du ange följande omfattningar för att styra åtkomsten till Intune-funktioner: I följande tabell sammanfattas behörighetsomfattningarna för Intune API.  Den första kolumnen visar namnet på den funktion som visas i Azure-portalen och den andra kolumnen innehåller namnet på behörighetsomfattningen.

Inställningen _Aktivera åtkomst_ | Namn på sökomfång
:--|:--
__Utföra användarpåverkande fjärråtgärder på Microsoft Intune-enheter__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Läsa och skriva Microsoft Intune-enheter__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Läsa Microsoft Intune-enheter__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Läsa och skriva RBAC-inställningar för Microsoft Intune__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Läsa RBAC-inställningar för Microsoft Intune__ | DeviceManagementRBAC.Read.All
__Läsa och skriva Microsoft Intune-appar__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Läsa Microsoft Intune-appar__ | [DeviceManagementApps.Read.All](#app-ro)
__Läsa och skriva enhetskonfiguration och principer för Microsoft Intune__ | DeviceManagementConfiguration.ReadWrite.All
__Läsa enhetskonfiguration och principer för Microsoft Intune__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Läsa och skriva Microsoft Intune-konfiguration__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Läsa Microsoft Intune-konfiguration__ | DeviceManagementServiceConfig.Read.All

Tabellen innehåller inställningarna i den ordning de visas i Azure-portalen. I följande avsnitt beskrivs omfattningarna i alfabetisk ordning.

Behörighetsomfattningar för Intune kräver för närvarande administratörsåtkomst.  Detta innebär att du måste ha motsvarande autentiseringsuppgifter när du kör appar eller skript som har åtkomst till Intune API-resurser.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- Inställningen **Aktivera åtkomst**: __Läsa Microsoft Intune-appar__

- Tillåter läsbehörighet till följande entitetsegenskaper och status:
    - Klientappar
    - Kategorier för mobilappar
    - Appskyddsprinciper
    - Appkonfigurationer

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- Inställningen **Aktivera åtkomst**: __Läsa och skriva Microsoft Intune-appar__

- Tillåter samma åtgärder som __DeviceManagementApps.Read.All__

- Tillåter också ändringar i följande entiteter:

    - Klientappar
    - Kategorier för mobilappar
    - Appskyddsprinciper
    - Appkonfigurationer

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- Inställningen **Aktivera åtkomst**: __Läsa enhetskonfiguration och principer för Microsoft Intune__

- Tillåter läsbehörighet till följande entitetsegenskaper och status:
    - Enhetskonfiguration
    - Efterlevnadsprincip för enhet
    - Meddelanden

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- Inställningen **Aktivera åtkomst**: __Läsa och skriva enhetskonfiguration och principer för Microsoft Intune__

- Tillåter samma åtgärder som __DeviceManagementConfiguration.Read.All__

- Appar kan också skapa, tilldela, ta bort och ändra följande entiteter:
    - Enhetskonfiguration
    - Efterlevnadsprincip för enhet
    - Meddelanden

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- Inställningen **Aktivera åtkomst**: __Utföra användarpåverkande fjärråtgärder på Microsoft Intune-enheter__

- Tillåter följande fjärråtgärder på en hanterad enhet:
    - Pensionera
    - Rensning
    - Återställa lösenord
    - Fjärrlåsning
    - Aktivera/inaktivera borttappat läge
    - Rensa datorn
    - Starta om datorn
    - Ta bort användare från en delad enhet

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- Inställningen **Aktivera åtkomst**: __Läsa Microsoft Intune-enheter__

- Tillåter läsbehörighet till följande entitetsegenskaper och status:
    - Hanterad enhet
    - Enhetskategori
    - Identifierad app
    - Fjärråtgärder
    - Information om skadlig kod

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- Inställningen **Aktivera åtkomst**: __Läsa och skriva Microsoft Intune-enheter__

- Tillåter samma åtgärder som __DeviceManagementManagedDevices.Read.All__

- Appar kan också skapa, ta bort och ändra följande entiteter:
    - Hanterad enhet
    - Enhetskategori

- Följande fjärråtgärder är också tillåtna:
    - Hitta enheter
    - Kringgå aktiveringslås
    - Begära fjärrhjälp

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- Inställningen **Aktivera åtkomst**: __Läsa RBAC-inställningar för Microsoft Intune__

- Tillåter läsbehörighet till följande entitetsegenskaper och status:
    - Rolltilldelningar
    - Rolldefinitioner
    - Resursåtgärder

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- Inställningen **Aktivera åtkomst**: __Läsa och skriva RBAC-inställningar för Microsoft Intune__

- Tillåter samma åtgärder som __DeviceManagementRBAC.Read.All__

- Appar kan också skapa, tilldela, ta bort och ändra följande entiteter:
    - Rolltilldelningar
    - Rolldefinitioner

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- Inställningen **Aktivera åtkomst**: __Läsa Microsoft Intune-konfiguration__

- Tillåter läsbehörighet till följande entitetsegenskaper och status:
    - Enhetsregistrering
    - Apple Push Notification-certifikat
    - Apples DEP (Device Enrollment Program)
    - Apples volymköpsprogram
    - Exchange Connector
    - Villkor
    - Kostnadsuppföljning av telekommunikation
    - Moln-PKI
    - Anpassning
    - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- Inställningen **Aktivera åtkomst**: __Läsa och skriva Microsoft Intune-konfiguration__

- Tillåter samma åtgärder som DeviceManagementServiceConfig.Read.All_

- Appar kan också konfigurera följande Intune-funktioner:
    - Enhetsregistrering
    - Apple Push Notification-certifikat
    - Apples DEP (Device Enrollment Program)
    - Apples volymköpsprogram
    - Exchange Connector
    - Villkor
    - Kostnadsuppföljning av telekommunikation
    - Moln-PKI
    - Anpassning
    - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Azure AD-autentiseringsexempel

I det här avsnittet visas hur du införlivar Azure AD i dina C#- och PowerShell-projekt.

I varje exempel måste du ange ett program-ID som har minst behörighetsomfattningen `DeviceManagementManagedDevices.Read.All` (se ovan).

När du testar något av exemplen kan du få HTTP-statusfel 403 (Förbjuden) som liknar följande:

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

Om det händer kontrollerar du att:

- Du har uppdaterat program-ID:t till en behörighet att använda Microsoft Graph-API och behörighetsomfattningen `DeviceManagementManagedDevices.Read.All`.

- Dina autentiseringsuppgifter för klienten har stöd för administrativa funktioner.

- Koden liknar de exempel som visas.


### <a name="authenticate-azure-ad-in-c"></a>Autentisera Azure AD i C\#

I det här exemplet visas hur du använder C# för att hämta en lista med enheter som är kopplade till ditt Intune-konto.

1.  Starta Visual Studio och skapa sedan ett nytt projekt i Visual C#-konsolens app (.NET Framework).

2.  Ange ett namn på ditt projekt och även annan information om du vill.

    <img src="media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3.  Använd Solution Explorer för att lägga till Microsoft ADAL NuGet-paketet i projektet.

    1.  Högerklicka på Solution Explorer.
    2.  Välj **Hantera NuGet-paket...** &gt; **Bläddra**.
    3.  Välj `Microsoft.IdentityModel.Clients.ActiveDirectory` och sedan **Installera**.

    <img src="media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4.  Lägg till följande uttryck överst i **Program.cs**:

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5.  Lägg till en metod för att skapa auktoriseringsrubriken:

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    Kom ihåg att ändra värdet för `application_ID` så att det minst matchar behörighetsomfattningen `DeviceManagementManagedDevices.Read.All`, enligt beskrivningen ovan.

6. Lägg till en metod för att hämta listan med enheter:

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7.  Uppdatera **Main** att anropa **GetMyManagedDevices**:

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8.  Kompilera och kör programmet.  

Du bör få två frågor när du kör programmet första gången.  Först begär den dina autentiseringsuppgifter och sedan ger den behörighet för `managedDevices`-begäran.  

Som referens visas här det slutförda programmet:

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Autentisera Azure AD (PowerShell)

Följande PowerShell-skript använder AzureAD PowerShell-modulen för autentisering.  Läs mer i [Azure Active Directory PowerShell Version 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) och [Intune PowerShell-exempel](https://github.com/microsoftgraph/powershell-intune-samples).

I det här exemplet uppdateras värdet för `$clientID` så att det matchar ett giltigt program-ID.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>Stöd för flera klienter och partners

Om din organisation har stöd för organisationer med egna Azure AD-klienter, kanske du vill tillåta att de använder programmet med sina klienter.

Så här gör du:

1.  Kontrollera att klientens konto finns i målets Azure AD-klient.

2.  Kontrollera att ditt klientkonto tillåter att användare registrerar program (se **Användarinställningar**).

3.  Upprätta en relation mellan varje klient.  

    Gör detta genom att antingen:

    a. Använda [Microsoft Partner Center](https://partnercenter.microsoft.com/) till att definiera en relation med din klient och deras e-postadress.

    b. Bjuda in användaren att bli gäst i din klient.

Så här bjuder du in användaren att bli gäst i din klient:

1.  Välj **Lägg till en gästanvändare** i panelen **Snabbuppgifter**.

    <img src="media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2.  Ange klientens e-postadress och lägg till ett personligt meddelande i inbjudan (valfritt).

    <img src="media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3.  Välj **Bjud in**.

En inbjudan skickas till användaren.

   <img src="media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   Användaren måste välja länken **Kom igång** för att acceptera din inbjudan.

När relationen upprättas (eller när din inbjudan har accepterats), läggs användarkontot till i **Katalogroll**.

Kom ihåg att lägga till användaren i andra roller om det behövs. Om du till exempel vill tillåta att användarna hanterar Intune-inställningar, måste de antingen vara **Global administratör** eller **Intune-tjänstadministratör**.

Du kan också:

- Använd https://admin.microsoft.com om du vill tilldela en Intune-licens till ditt användarkonto.

- Uppdatera programkod för att autentisera till klientens Azure AD-klientdomän i stället för din egen.

    Om din klientdomän exempelvis är `contosopartner.onmicrosoft.com` och klientens klientdomän är `northwind.onmicrosoft.com`, uppdaterar du din kod till att autentisera till klientens klient.

    Om du gör det i ett C#-program baserat på det tidigare exemplet, ändrar du värdet för `authority`-variabeln:

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    på

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
