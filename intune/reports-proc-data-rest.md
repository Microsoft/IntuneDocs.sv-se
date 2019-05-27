---
title: Hämta data från API för informationslager med en REST-klient
titleSuffix: Microsoft Intune
description: Det här avsnittet beskriver hur du hämtar data från Microsoft Intune-informationslagret med hjälp av ett RESTful-API.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 894ce1fcf270af0169661359c2ab088bb30fab62
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041163"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>Hämta data från API för Intune-informationslagret med en REST-klient

Du når datamodellen Intune-informationslager via RESTful-slutpunkter. Klienten måste auktorisera med Microsoft Azure Active Directory (Azure AD) med hjälp av OAuth 2.0 för att få åtkomst till dina data. Om du vill aktivera åtkomst måste du först ställa in en inbyggd app i Azure och ge behörighet till Microsoft Intune-API. Den lokala klienten får behörighet och kan sedan kommunicera med informationslagrets slutpunkter via den inbyggda appen.

När du ska ställa in en klient för att hämta data från informationslager-API:et måste du:

1. Skapa en klientapp som inbyggd app i Azure
3. Ge klientappen åtkomst till Microsoft Intune-API
3. Skapa en lokal REST-klient som ska hämta data

Följande anvisningar visar hur du auktoriserar och kommer åt API med en REST-klient. Börja med att använda en allmän REST-klient med Postman. Postman är ett verktyg som ofta används för felsökning och utveckling av REST-klienter som fungerar med API:er. Mer information om Postman finns på sajten [Postman](https://www.getpostman.com). Sedan kan du titta på ett C#-kodexempel. Det innehåller ett exempel för auktorisering av en klient och hämtning av data från API:et.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Skapa en klientapp som inbyggd app i Azure

Skapa en inbyggd app i Azure. Den här inbyggda appen är klientappen. Klienten som körs på din lokala dator hänvisar till Intune-informationslagrets API när den lokala klienten begär autentiseringsuppgifter.

1. Logga in på Azure Portal för din klientorganisation. Välj **Azure Active Directory** > **Appregistreringar** så att fönstret **Appregistreringar** öppnas.
2. Välj **Ny appregistrering**.
3. Ange information om appen.
    1.  Skriv ett eget namn, till exempel Intune Data Warehouse Client som **namn**.
    2.  Välj**Intern** som **Programtyp**.
    3.  Skriv en webbadress för **Inloggningswebbadress**. Inloggningswebbadressen beror på den särskilda situationen men om du tänkt använda Postman skriver du `https://www.getpostman.com/oauth2/callback`. Du kommer sedan använda callback (återanrop) för klientautentiseringen när du autentiserar till Azure AD.
4.  Välj **Skapa**.

     ![Intune Data Warehouse-klientapp](./media/reports-get_rest_data_client_overview.png)

5. Observera appens värde för **Program-ID**. Det här värdet ska användas i nästa avsnitt.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>Ge klientappen åtkomst till Microsoft Intune-API

Nu har du definierat en app i Azure. Bevilja åtkomst från inbyggda klientappen till Microsoft Intune-API.

1.  Välj den inbyggda appen. Du gav appen ett namn i stil med **Intune Data Warehouse Client**.
2.  Välj **Nödvändiga behörigheter** i fönstret **Inställningar**
3.  Välj **Lägg till** i fönstret **Nödvändiga behörigheter**.
4.  Välj **Välj en API**.
5.  Sök efter namnet på webbappen. Namnet är **Microsoft Intune API**.
6.  Välj appen i listan.
7.  Välj **Välj**.
8.  Markera rutan **Delegerade behörigheter** för att lägga till **Hämta informationslagerdata från Microsoft Intune**.

    ![Aktivera åtkomst – Microsoft Intune API](./media/reports-get_rest_data_client_access.png)

9.  Välj **Välj**.
10.  Välj **Klar**.
11.  Du kan också välja **Bevilja behörigheter** i fönstret Nödvändiga behörigheter. Då får alla konton i den aktuella katalogen åtkomst. Dialogrutan för medgivande visas inte för användarna i klientorganisationen. Mer information finns i [Integrating applications with Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) (Integrera program med Azure Active Directory).
12.  Välj **Ja**.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Hämta data från Microsoft Intune-API med Postman

Du kan arbeta med API för Intune-informationslager med en vanlig REST-klient, till exempel Postman. Postman kan ge information om API:ets funktioner, den underliggande OData-datamodellen och felsöka anslutningen till API-resurserna. I det här avsnittet hittar du information om hur du skapar en Auth2.0-token för en lokal klient. Token behövs för att klienten ska kunna autentiseras med Azure AD och få åtkomst till API-resurserna.

### <a name="information-you-will-need-to-make-the-call"></a>Information du behöver för att skicka anropet

Du behöver följande information för att skicka ett REST-anrop via Postman:

| Attribut        | Beskrivning                                                                                                                                                                          | Exempel                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| Callback URL (Webbadress för återanrop)     | Ställ in det här som webbadress för återanrop på appinställningssidan.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| Token Name (Tokennamn)       | En sträng som används för att skicka autentiseringsuppgifter till Azure-appen. Med den här processen skapas din token så att du kan anropa API för informationslagret.                          | Bearer                                                                                        |
| Auth URL (Auktoriseringswebbadress)         | Webbadressen som används för autentisering. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| Access Token URL (Webbadress för åtkomsttoken) | Webbadressen som används för att bevilja token.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| Klient-ID        | Du skapade och antecknade det här när du skapade den inbyggda appen i Azure.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| Scope (Optional) (Omfång, valfritt) | Tom                                                                                                                                                                               | Du kan lämna fältet tomt.                                                                     |
| Grant Type (Typ av beviljande)       | Token är en auktoriseringskod.                                                                                                                                                  | Authorization code (Auktoriseringskod)                                                                            |

### <a name="odata-endpoint"></a>OData-slutpunkt

Du behöver även slutpunkten. Du behöver URL för det anpassade flödet för att kunna hämta slutpunkten för informationslagret. Du kan hämta OData-slutpunkten från fönstret Informationslager.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Konfigurera Intune Data Warehouse** under **Andra uppgifter**.
4. Kopiera URL för det anpassade flödet under **Använd rapporteringstjänster från tredje part**. Det bör se ut ungefär så här: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0`

Slutpunkten följer följande format: `https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`

Entiteten **datum** ser till exempel ut som: `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`

Mer information finns i [API-slutpunkt för Intune-informationslager](reports-api-url.md).

### <a name="make-the-rest-call"></a>Skicka ett REST-anrop

Om du vill hämta en ny åtkomsttoken för Postman måste du lägga till Azure AD-auktoriseringswebbadressen, klient-id och klienthemlighet. Postman läser in auktoriseringssidan där du anger dina autentiseringsuppgifter.

#### <a name="add-the-information-used-to-request-the-token"></a>Lägg till informationen som används för att begära token

1.  Ladda ned Postman om det inte redan är installerat. Information om hur du laddar ned Postman finns i [www.getpostman](https://www.getpostman.com).
2.  Öppna Postman. Välj HTTP-åtgärden **GET**.
3.  Klistra in slutpunktswebbadressen i adressfältet. Det bör se ut ungefär så här:  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4.  Välj fliken **Authorization** (Auktorisering) och välj **OAuth 2.0** i listan **Type** (Typ).
5.  Välj **Get New Access Token** (Hämta ny åtkomsttoken).
6.  Kontrollera att du har lagt till webbadressen för återanrop i appen i Azure. Webbadressen för återanrop är `https://www.getpostman.com/oauth2/callback`.
7.  Skriv Bearer som **Token Name** (Namn på token).
8.  Lägg till **Auth URL** (autentiseringswebbadressen). Det bör se ut ungefär så här:  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9.  Lägg till **Access Token URL**(webbadress för token). Det bör se ut ungefär så här:  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Lägg till **Client ID** (Klient-id) från den inbyggda app du skapade i Azure med namnet `Intune Data Warehouse Client`. Det bör se ut ungefär så här:  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. Välj **Authorization Code** (Auktoriseringskod) och Request access token locally (Begär åtkomsttoken lokalt).

12. Välj **Request Token** (Begär token).

    ![Information för åtkomsttoken](./media/reports-postman_getnewtoken.png)

13. Ange dina autentiseringsuppgifter på auktoriseringssidan i Active AD. I listan över token i Postman finns nu token med namnet `Bearer`.
14. Välj **Använd token**. Listan över sidhuvuden innehåller det nya nyckelvärdet för auktorisering och värdet `Bearer <your-authorization-token>`.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Skicka anropet till slutpunkten via Postman

1.  Välj **Skicka**.
2.  Returnerade data visas i svarstexten i Postman.

    ![Postman-klientstatusen är lika med 200 OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Skapa en REST-klient (C#) för att hämta data från Intune-informationslagret

Följande exempel innehåller en enkel REST-klient. Koden använder klassen **httpClient** från .Net-biblioteket. När klienten har fått autentiseringsuppgifter till Azure AD skapar klienten ett GET REST-anrop för att hämta dates-entiteten från API:et för Intune-informationslager.

> [!Note]  
> Du kan öppna följande kodexempel [i GitHub](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs). De senaste ändringarna och uppdateringarna av exemplet hittar du i GitHub-databasen.

1. Öppna **Microsoft Visual Studio**.
2. Välj **File**(Arkiv) > **New project** (Nytt projekt). Expandera **Visual C#** och välj **Console App (.Net Framework)** (Konsolapp (.Net Framework)).
3. Ge projektet namnet ` IntuneDataWarehouseSamples`, bläddra dit där du vill spara projektet och välj sedan **OK**.
4. Högerklicka på namnet på lösningen i Solution Explorer och välj sedan **Manage NuGet Packages for Solution** (Hantera NuGet-paket för lösning). Välj **Bläddra** och skriv sedan `Microsoft.IdentityModel.Clients.ActiveDirectory` i sökrutan.
5. Välj paketet och markera projektet **IntuneDataWarehouseSamples** under Manage Packages for Your Solution (Hantera paket för lösningen) och välj sedan **Install** (Installera).
6. Välj **I Accept** (Jag accepterar) för att godkänna NuGet-paketlicensen.
7. Öppna `Program.cs` från Solution Explorer.

    ![Progam.cs och Solution Explorer i Visual Studio](./media/reports-get_rest_data_in.png)

8. Ersätt koden i *Program.cs* med följande kod:  
   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=v1.0";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. Uppdatera `TODO`-texten i kodexemplet.
10. Tryck på **Ctrl + F5** för att skapa och köra Intune.DataWarehouseAPIClient-klienten i felsökningsläge.

    ![Datumentitet som hämtats i JSON-format.](./media/reports-get_rest_data_output.png)

11. Granska konsolutdata. Utdata består av data i ett JSON-format som hämtats från **dates**-entiteten i din Intune-klientorganisation.

## <a name="next-steps"></a>Nästa steg

Du hittar information om auktorisering, API:ets webbadresstruktur och OData-slutpunkter i [API-slutpunkt för Intune-informationslager](reports-api-url.md).

I datamodellen Intune-informationslager hittar du också dataentiteterna i API:et. Mer information finns i [Datamodellen API för Intune-informationslager](reports-ref-data-model.md)
