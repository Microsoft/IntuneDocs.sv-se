---
title: Autentisering för enbart Intune-informationslagerprogram
titleSuffix: Microsoft Intune
description: Det här ämnet beskriver autentisering som enbart görs av Intune-informationslagerprogram för Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4edf6e1e2b0ed57ec221e445bc171895fb9e0072
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042675"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Autentisering för enbart Intune-informationslagerprogram

Du kan konfigurera ett program med Azure Active Directory (Azure AD) och autentisera till Intune-informationslagret. Den här processen är användbar för webbplatser, appar och bakgrundsprocesser där programmet inte ska ha åtkomst till användarens autentiseringsuppgifter. Med följande steg kan du godkänna ditt program med Azure AD med hjälp av OAuth 2.0.

## <a name="authorization"></a>Auktorisering

I Azure Active Directory (Azure AD) används OAuth 2.0 för att du ska kunna bevilja åtkomst till webbprogram och webb-API:er i din klientorganisation. Den här guiden visar hur du autentiserar ditt program med C#. OAuth 2.0-auktoriseringskodflödet beskrivs i avsnitt 4.1 i OAuth 2.0-specifikationen. Mer information finns i [Bevilja åtkomst till webbprogram med hjälp av OAuth 2.0 och Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code).


## <a name="azure-keyvault"></a>Azure KeyVault

Följande process använder en privat metod för att bearbeta och konvertera en app-nyckel. Den här privata metoden heter SecureString. Du kan använda Azure KeyVault som ett alternativ för lagring av app-nyckeln. Mer information finns i [Key Vault](https://azure.microsoft.com/services/key-vault/).

## <a name="create-a-web-app"></a>Skapa en webbapp

I det här avsnittet anger du information om det webbprogram som du vill peka på Intune. En webbapp är ett klientserverprogram. Servern tillhandahåller webbappen, som inkluderar användargränssnitt, innehåll och funktioner. Den här typen av app underhålls separat på webben. Du använder Intune för att ge ett webbprogram åtkomst till Intune. Dataflödet initieras av webbprogrammet. 

1.  Logga in på [Azure Portal](https://portal.azure.com).
2.  Med hjälp av fältet **Sök resurser, tjänster och dokument** längst upp i Azure-portalen, söker du efter **Azure Active Directory**.
3.  I listmenyn, väljer du **Azure Active Directory** under **Tjänster**.
4.  Välj **Appregistreringar**.
5.  Klicka **Ny appregistrering** för att visa **Skapa**-bladet.
6.  I **Skapa**-bladet lägger du till din appinformation:

    - Ett appnamn som *Intune App-enbart auktorisering*.
    - **Programtypen**. Välj **Webbprogram / API** för att lägga till en app som representerar ett webbprogram, en web-API eller båda.
    - **Inloggnings-URL** för programmet. Detta är den plats som användarna automatiskt går till vid autentiseringsprocessen. De måste bevisa att de är den de säger att de är. Mer information finns i [Vad är programåtkomst och enkel inloggning med Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)

7.  Klicka på **Skapa** längst ned i **Skapa**-bladet.

    >[!NOTE] 
    > Kopiera **Program-ID** från **Registrerad app**-bladet för senare användning.

## <a name="create-a-key"></a>Skapa en nyckel

I det här avsnittet genererar Azure AD ett nyckelvärde för din app.

1.  På **Appregistreringar**-bladet väljer du din nyligen skapade app för att visa appbladet.
2.  Välj **inställningar** överst på bladet för att visa **Inställningar**-bladet.
3.  Välj **Nycklar** på **Inställningar**-bladet.
4.  Lägg till nyckeln **Beskrivning**, en **Förfaller**-varaktighet och **Värde** för nyckeln.
5.  Klicka på **spara** för att spara och uppdatera programmets nycklar.
6.  Du måste kopiera det genererade nyckelvärdet (base64-kodat).

    >[!NOTE] 
    > Nyckelvärdet försvinner när du lämnar **Nycklar**-bladet. Det går inte att hämta nyckeln från det här bladet senare. Kopiera det för att använda senare.

## <a name="grant-application-permissions"></a>Bevilja programbehörigheter

I det här avsnittet, beviljar du behörigheter till program.

1.  Välj **Nödvändiga behörigheter** på **Inställningar**-bladet.
2.  Klicka på **Lägg till**.
3.  Välj **Lägg till en API** för att visa **Välj en API**-bladet.
4.  Välj **Microsoft Intune API (MicrosoftIntuneAPI)** och klicka sedan på **Välj** från **Välj en API**-bladet. Steget **Välj behörigheter** väljs och **Aktivera åtkomst**-bladet visas.
5.  Välj alternativet **Hämta informationslagerinformation från Microsoft Intune** från avsnittet **Programbehörigheter**.
6.  Klicka på **Välj** från **Aktivera åtkomst**-bladet.
7.  Klicka **Klar** från **Lägg till API-åtkomst**-bladet.
8.  Klicka på **Bevilja behörighet** från **Nödvändiga behörigheter**-bladet och klicka på **Ja** när du tillfrågas för att uppdatera befintliga behörigheter som programmet redan har.

## <a name="generate-token"></a>Generera token

Med Visual Studio, skapar du ett konsolprogram (.NET Framework)-projekt som har stöd för .NET Framework och använder C# som kodningsspråk.

1.  Välj **Fil** > **Nytt** > **Projekt** för att visa dialogrutan **Nytt projekt**.
2.  Till vänster, väljer du **Visual C#** för att visa alla .NET Framework-projekt.
3.  Välj **Konsolapp (.NET Framework)** , lägg till ett appnamn och klicka sedan på **OK** för att skapa appen.
4.  I **Solution Explorer** väljer du **Program.cs** för att visa koden.
5.  I popup-menyn, väljer du **Lägg till** > **Nytt objekt**. Dialogrutan **Lägg till nytt objekt** visas.
6.  Till vänster under **Visual C#** väljer du **Kod**.
7.  Välj **Klass**, ändra namnet på klassen till *IntuneDataWarehouseClass.cs* och klicka på **Lägg till**.
8.  Lägg till följande kod i <code>Main</code>-metoden:

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. Lägg till ytterligare namnområden genom att lägga till följande kod högst upp i kodfilen:

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. Efter <code>Main</code>-metoden, lägger du till följande privata metod för att bearbeta och konvertera appnyckeln:

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. I **Solution Explorer**, högerklickar du på **Referenser** och väljer **Hantera NuGet-paket**.
12. Sök efter *Microsoft.IdentityModel.Clients.ActiveDirectory* och installera det relaterade Microsoft NuGet-paketet.
13. I **Solution Explorer** väljer du och öppnar filen *App.config*.
14. Lägg till <code>appSettings</code>-avsnittet så att xml visas enligt följande:

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. Uppdatera värdena <code>appId</code>, <code>appKey</code> och <code>tenantDomain</code> så att de matchar dina unika apprelaterade värden.
16. Skapa din app.

    >[!NOTE] 
    > Ytterligare implementeringskod finns i [Kodexempel för Intune informationslager](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp ).

## <a name="next-steps"></a>Nästa steg
Läs mer om Azure Key Vault genom att granska [Vad är Azure Key Vault?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)

