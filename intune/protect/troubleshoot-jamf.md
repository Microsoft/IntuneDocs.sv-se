---
title: Felsöka JAMF Pro-integrering med Microsoft Intune
titleSuffix: Microsoft Intune
description: Förslag på fel sökning av några av de vanligaste problemen när du integrerar JAMF Pro för Mac-enheter med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e92e3442e1347cb1a2cd1c737078912b74f075c9
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71817644"
---
# <a name="troubleshoot-integration-of-jamf-pro-with-microsoft-intune"></a>Felsök integrering av JAMF Pro med Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem med integrering av JAMF Pro för macOS med Intune.

> [!TIP]  
> Mycket av informationen i den här artikeln visades ursprungligen i [Felsöka problem när du integrerar JAMF med Microsoft Intune](https://support.microsoft.com/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune) på support.Microsoft.com.

## <a name="prerequisites"></a>Krav

Innan du påbörjar fel sökningen samlar du in lite grundläggande information som klargör problemet och minskar tiden för att hitta en lösning. Om du till exempel stöter på ett JAMF problem med Intune kontrollerar du alltid att kraven är uppfyllda. Granska följande överväganden innan du påbörjar fel sökningen:

- Granska kraven från [integrera JAMF Pro med Intune](conditional-access-integrate-jamf.md#prerequisites).
- Alla användare måste ha Microsoft Intune-och Microsoft AAD Premium P1-licenser 
- Du måste ha ett användar konto som har Microsoft Intune integrations behörighet i JAMF Pro-konsolen.
- Du måste ha ett användar konto som har globala administratörs behörigheter i Azure.


Överväg följande information när du undersöker JAMF Pro-integrering med Intune: 
- Vilket är det exakta felmeddelandet?
- Var finns fel meddelandet?
- När började problemet?  Har JAMF Pro-integrering med Intune någonsin arbetat?
- Hur många användare påverkas? Påverkas alla användare eller bara vissa av dem?
- Hur många enheter påverkas? Påverkas alla enheter eller bara vissa av dem?
 

## <a name="common-problems"></a>Vanliga problem 

Följande information kan hjälpa dig att identifiera och lösa vanliga problem för enheter när du har konfigurerat Intune och JAMF Pro-integration.  

| Problem   | Mer information                  |
|-----------------|--------------------------|
| **Enheter har marker ATS som besvarade i JAMF Pro**  | [Enheter kan inte checka in med JAMF Pro eller med Azure AD](#devices-are-marked-as-unresponsive-in-jamf-pro) |
| **Mac-enheter uppmanas att logga in på nyckel ringen när du öppnar en app-enheter kan inte registreras**  | [Användarna uppmanas att ange sina lösen ord för att tillåta att appar registreras med Azure AD](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app). |
| **Enheterna kan inte registreras**  | Följande orsaker kan vara tillämpliga: <br> **-** [ ***Orsak 1*** – JAMF Pro-appen i Azure har felaktig behörighet](#cause-1) <br> **-** [ ***Orsak 2*** – det finns ett problem med den *JAMF-inhemska MacOS-anslutningen* i Azure AD](#cause-2) <br> **-** [ ***Orsak 3*** – användaren har ingen giltig Intune-eller JAMF-licens](#cause-3) <br> **-** [ ***orsak 4*** – användaren använde inte JAMF Self service för att starta företagsportal-appen](#cause-4) <br> **-** [ ***Orsak 5*** -Intune-integrering är inaktive rad](#cause-5) <br> **-** [ ***orsak 6*** – enheten har tidigare registrerats i Intune, eller så har användaren försökt registrera enheten flera gånger](#cause-6) <br> **-** [ ***orsak 7*** -JamfAAD begär åtkomst till en "Microsoft Workplace Join Key" från användarnas nyckel Ring](#cause-7) |
|  **Mac-enheten visar kompatibel i Intune men inte kompatibel i Azure** | [Problem med enhets registrering](#mac-device-shows-compliant-in-intune-but-noncompliant-in-azure) |
| **Dubbla poster visas i Intune-konsolen för Mac-enheter som registrerats med hjälp av JAMF** | [Flera registreringar från samma enhet](#duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf) |
| **Efterlevnadsprincip kan inte utvärdera enheten** | [Princip mål enhets grupper](#compliance-policy-fails-to-evaluate-the-device) |
| **Det gick inte att hämta åtkomsttoken för Microsoft Graph-API** | Följande orsaker kan vara tillämpliga: <br> -[behörigheter för JAMF Pro-appen i Azure](#theres-a-permission-issue-with-the-jamf-pro-application-in-azure) <br> - -[licensen har upphört att gälla för JAMF eller Intune](#a-license-required-for-jamf-intune-integration-has-expired) <br> **--** [portar är inte öppna](#the-required-ports-arent-open-on-your-network)|
 

### <a name="devices-are-marked-as-unresponsive-in-jamf-pro"></a>Enheter har marker ATS som besvarade i JAMF Pro  

**Orsak**: följande är vanliga orsaker till att enheter som marker ATS som JAMF Pro inte *svarar* :

- Enheten kan inte checka in med JAMF Pro.  
  JAMF Pro förväntar sig att enheterna ska checka in var 15: e minut. Enheter markeras som ej besvarade av JAMF när de inte kan checka in under en 24-timmarsperiod.  

- Enheten kan inte checka in med Azure AD.  
  Med lyckad registrering till Azure AD tar macOS-enheter emot en Azure-token:
  - Denna token uppdateras var 12: e timme.   
  - När token-uppdateringen Miss lyckas i 24 timmar eller mer markerar JAMF-teknikern att enheten inte svarar.  
  - Om Azure-token upphör att gälla uppmanas användarna att logga in på Azure för att få en ny token. En uppdaterad token för Azure-åtkomst genereras var sjunde dag.

**Lösning**  
När en enhet har marker ATS som ej *svarar* av JAMF Pro, måste den registrerade användaren av enheten logga in för att korrigera tillstånd som inte svarar. Det måste vara den användare som har arbete som har anslutits till kontot när de har fått identiteten från Intune i inloggnings nyckel ringen.



### <a name="mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app"></a>Mac-enheter uppmanas att logga in på nyckel ringen när du öppnar en app  

När du har konfigurerat Intune och JAMF Pro-integrering och distribuerar principer för villkorlig åtkomst, får användare av enheter som hanteras med JAMF Pro ett lösen ord när de öppnar Microsoft Office 365-program, t. ex. team, Outlook och andra appar som kräver Azure AD-autentisering. 

Till exempel visas en prompt med text som liknar följande exempel när du öppnar Microsoft Teams:

``` 
  Microsoft Teams wants to sign using key “Microsoft Workplace Join Key” in your keychain.  
  To allow this, enter the “login” keychain password 
```

**Orsak**: dessa meddelanden genereras av JAMF Pro för varje tillämplig app som kräver Azure AD-registrering. 

**Lösning**   
Användaren måste ange enhetens lösen ord för att logga in på Azure AD vid prompten. Alternativen är:
- **Deny** – logga inte in och Använd inte appen.
- **Tillåt** -en inloggning med en tidpunkt. Nästa gång appen öppnas uppmanas du att logga in igen.
- **Tillåt alltid** -inloggnings uppgifterna cachelagras för programmet. Nästa gången appen öppnas uppmanas inte att logga in.  

Om du väljer *Tillåt alltid* för en app godkänns endast den appen för framtida inloggning. Ytterligare appar fråga efter autentisering tills de också är inställda så *att de alltid är tillåtna*. Det går inte att använda cachelagrade autentiseringsuppgifter för en app i en annan app.  

### <a name="devices-fail-to-register"></a>Enheterna kan inte registreras  

Det finns flera vanliga orsaker till Mac-enheter som inte kan registreras.  

#### <a name="cause-1"></a>Orsak 1  

**JAMF Pro Enterprise-programmet i Azure har fel behörighet eller har fler än en behörighet**  

  När du skapar appen i Azure måste du ta bort alla standard-API-behörigheter och sedan tilldela Intune en enda behörighet för *update_device_attributes*. 

  **Lösning**  
  Granska och om det behövs rätt behörighet för JAMF-appen som du skapade i Azure AD. Se proceduren för att [skapa ett program för JAMF i Azure AD](conditional-access-integrate-jamf.md#create-an-application-in-azure-active-directory). 

#### <a name="cause-2"></a>Orsak 2  

****JAMF Native MacOS Connector** -appen skapades inte i din Azure AD-klient eller så har ditt medgivande för anslutningen signerats av ett konto som inte har någon global administratörs behörighet**  

  **Lösning**  
  Mer information finns i avsnittet *Konfigurera MacOS Intune-integrering* i [integrera med Microsoft Intune](https://docs.jamf.com/10.13.0/jamf-pro/administrator-guide/Integrating_with_Microsoft_Intune.html) på docs.JAMF.com. 

#### <a name="cause-3"></a>Orsak 3

**Användaren har inte någon giltig Intune-eller JAMF-licens**  

  Brist på en giltig licens kan resultera i följande fel, vilket tyder på att JAMF-licensen har upphört att gälla:  
  ```
    Unable to connect to Microsoft Intune.  
    
    Check your Microsoft Intune Integration configuration.
  ```  

  **Lösning**
  - JAMF-licens: kontakta JAMF om du behöver hjälp med att skaffa en ny licens för JAMF.  
  - Intune-licens: tilldela användaren en giltig licens eller kontakta Microsoft eller din partner för information om hur du skaffar en aktuell licens.

#### <a name="cause-4"></a>Orsak 4  

**Användaren har inte använt *JAMF Self Service* för att starta företagsportal-appen**

För att en enhet ska kunna registrera sig och registrera med Intune via JAMF måste användaren använda JAMF Self service för att öppna Intune-företagsportal. Om användaren öppnar företags portalen manuellt registrerar enheten och registrerar sig utan anslutning till JAMF.  

För att avgöra vilken tjänst enheten som används för att registrera och registrera, se i Företagsportal-appen på enheten. När du har registrerat dig via JAMF bör du få ett meddelande om att öppna självbetjänings appen för att göra ändringar.

I Företagsportal-appen kan användaren se **`Not registered`** och en post som liknar följande exempel kan visas i företagsportal loggarna:  

```
   Line 7783: <DATE> <IP ADDRESS> INFO com.microsoft.ssp.application TID=1  
 
   WelcomeViewController.swift: 253 (startLogin()) Portal launched without WPJ only arg while account is under partner management
```

**Lösning**  
Ändra registrerings källan från Intune till JAMF:
1. [Avregistrera din macOS-enhet från Intune](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-macos). För att undvika ytterligare komplikationer för enheter som inte helt tas bort från Intune, se [*orsak 6*](#cause-6) i den här listan över orsaker.  

2. På enheten använder du JAMF Self service för att öppna appen Företagsportal och registrerar sedan enheten med Intune. Den här uppgiften kräver att du har [använt JAMF för att distribuera företagsportal-appen för MacOS](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)och att du har [skapat en princip i JAMF Pro som registrerar användarnas enheter med Azure AD](conditional-access-assign-jamf.md#create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory).  

3. När portalen öppnas visas den första skärmen där du får logga in. Använda ditt arbets- eller skolkonto  

4. Företagsportalen bekräftar kontoinformationen och visar statusen för Enhetsregistrering och Enhetsefterlevnad. Gula trianglar markerar de åtgärder du måste utföra för att skydda din macOS-enhet för skolan eller arbetet. Klicka på Börja för att starta registreringen.  

5. Om du uppmanas att göra det anger du datorns inloggningsinformation.  
     
Det kan ta några minuter att registrera enheten i hantering. Du kan göra andra saker på enheten under tiden. Du får ett meddelande när du har slutfört konfigurationen av företagsåtkomst så att du vet att du är färdig.

#### <a name="cause-5"></a>Orsak 5  

**Intune-integrering är inaktive rad**

Om Intune-integrering är inaktive rad får användarna ett popup-fönster i Företagsportal med följande meddelande när de försöker registrera en enhet:  

```
   Invalid command line input
   
   Registration-only command line flag (-r) can only be used when partner management is enabled in Intune. Please contact your IT admin.
```  

JAMF Pro-servern skickar en puls till Intune-servrarna när integreringen är inaktive rad, som talar om för Intune att integrationen är inaktive rad. 

**Lösning**  
Återaktivera Intune-integrering inom JAMF Pro. Se [Konfigurera Microsoft Intune-integrering i Jamf Pro](conditional-access-integrate-jamf.md#enable-intune-to-integrate-with-jamf-pro).


#### <a name="cause-6"></a>Orsak 6  

**Enheten har tidigare registrerats i Intune eller så har användaren försökt registrera enheten flera gånger**

Om en enhet har avregistrerats från JAMF men inte tas bort från Intune, eller om flera registrerings försök görs, kan du se flera instanser av samma enhet i portalen. Detta gör att JAMF-registreringen Miss fungerar.

**Lösning**  
1. Starta **Terminal**på Mac.
2. Kör **sudo JAMF removemdmprofile**.
3. Kör **sudo JAMF removeFramework**.
4. Ta bort datorns lager post på JAMF Pro-servern.
5. Ta bort enheten från AzureAD.
6. Ta bort följande filer på enheten om de finns:
   - /Library/Application Support/com. Microsoft. CompanyPortal. UserContext. info
   - /Library/Application Support/com. Microsoft. CompanyPortal
   - /Library/Application-Support/com. jamfsoftware. självbetjänings. Mac
   - /Library/Saved-program
   - State/com. jamfsoftware. självbetjänings. Mac. savedState
   - /Library/Saved program tillstånd/com. Microsoft. CompanyPortal. savedState
   - /Library/Preferences/com.microsoft.CompanyPortal.plist
   - /Library/Preferences/com.jamfsoftware.selfservice.mac.plist
   - /Library/Preferences/com.jamfsoftware.management.jamfAAD.plist
   - /Users/<username>/bibliotek/cookies/com. Microsoft. CompanyPortal. binarycookies
   - /Users/<username>/Library/cookies/com. JAMF. Management. jamfAAD. binarycookies
   - com. Microsoft. CompanyPortal
   - com. Microsoft. CompanyPortal. HockeySDK
   - enterpriseregistration.windows.net
   - https://device.login.microsoftonline.com
   - https://device.login.microsoftonline.com/
   - Microsoft session transport Key (offentliga och privata nycklar)
   - Microsoft Workplace Join nyckel (offentliga och privata nycklar)
7. Ta bort allt från nyckel ringen på enheten som refererar till *Microsoft*, *Intune*eller *företagsportal*, inklusive DeviceLogin.Microsoft.com-certifikat. Ta bort *JAMF* -referenser förutom JAMF offentliga och privata nyckeln. 
   > [!IMPORTANT]  
   > Om du tar bort den offentliga och privata nyckeln avbryts enhets registreringen.

8. Ta bort någon av följande poster som du hittar:  
   - Typ: lösen ord för program Konto: com. Microsoft. workplacejoin. tumavtryck
   - Typ: lösen ord för program Konto: com. Microsoft. workplacejoin. registeredUserPrincipalName
   - Typ: certifikat; Utfärdat av: MS-Organization-Access
   - Typ: identitets preferens; Namn (ADFS STS-URL om det finns): https://adfs\<DNSName>.com/adfs/ls
   - Typ: identitets preferens; Namn: https://enterpriseregistration.windows.net
   - Typ: identitets preferens; Namn: https://enterpriseregistration.windows.net/  
9. Starta om Mac-enheten.
10. Avinstallera Företagsportal från enheten.
11. Gå till portal.manage.microsoft.com och ta bort alla instanser av Mac-enheten. Vänta minst 30 minuter innan du går vidare till nästa steg.
12. Registrera enheten på nytt i JAMF Pro.
13. Öppna självbetjäning och starta registrerings princip.


#### <a name="cause-7"></a>Orsak 7  

**JamfAAD begär åtkomst till en "Microsoft Workplace Join Key" från användarnas nyckel Ring**

Vid registreringen får användaren av en macOS-enhet följande fråga för att ge JamfAAD åtkomst till en nyckel från nyckel ringen: 

```
   JamfAAD wants to access key “Microsoft Workplace Join Key" in your keychain. 
    
   To allow this, enter the “login” keychain password
```

**Lösning**  
För att kunna registrera enheten med Azure AD, kräver JAMF att användaren anger sina konto lösen ord och väljer **Tillåt**.

Den här begäran liknar [frågan om Mac-enheter för nyckel rings inloggning när du öppnar en app](#mac-devices-prompt-for-keychain-sign-in-when-you-open-an-app), tidigare i den här artikeln.  

 
### <a name="mac-device-shows-compliant-in-intune-but-noncompliant-in-azure"></a>Mac-enheten visar kompatibel i Intune men inte kompatibel i Azure  

**Orsak**: följande villkor kan orsaka att en enhet visas som kompatibel i Intune men inte som kompatibel i Azure:  
- Enheten är inte korrekt registrerad.  
- Enheten registrerades flera gånger utan nödvändig rensning.

**Lösning**  
Lös problemet genom att följa lösningen för [*orsak 6*](#cause-6) för *enheter som inte kan registreras*tidigare i den här artikeln. 


### <a name="duplicate-entries-appear-in-the-intune-console-for-mac-devices-enrolled-by-using-jamf"></a>Dubbla poster visas i Intune-konsolen för Mac-enheter som registrerats med hjälp av JAMF  
 
**Orsak**: en enhet registreras med Intune flera gånger, vilket vanligt vis registreras igen efter att den har tagits bort från Intune.  

När en enhet tas bort från Intune-och JAMF Pro-integreringen kan vissa data lämnas kvar bakom vilka kan göra att du kan skapa dubbla poster.  

**Lösning**  
Lös problemet genom att följa lösningen för [*orsak 6*](#cause-6) för *enheter som inte kan registreras*tidigare i den här artikeln. 

### <a name="compliance-policy-fails-to-evaluate-the-device"></a>Efterlevnadsprincip kan inte utvärdera enheten  

**Orsak**: JAMF-integrering med Intune stöder inte efterlevnadsprinciper som är mål för enhets grupper. 

**Lösning**  
Ändra efterlevnadsprincip för macOS-enheter som ska tilldelas till användar grupper. 


### <a name="could-not-retrieve-the-access-token-for-microsoft-graph-api"></a>Det gick inte att hämta åtkomsttoken för Microsoft Graph-API

Du får följande fel:

```
   Could not retrieve the access token for Microsoft Graph API. Check the configuration for Microsoft Intune Integration.
```   

Källan till det här felet kan vara en av följande orsaker: 

#### <a name="theres-a-permission-issue-with-the-jamf-pro-application-in-azure"></a>Det finns ett behörighets problem med JAMF Pro-programmet i Azure

Ett av följande tillstånd inträffade när JAMF Pro-appen registrerades i Azure:  
- Appen mottog fler än en behörighet.
- **Anslags administratörs medgivande för *\< företags >***  alternativet har inte valts.  

**Lösning**  
Se lösning för orsak 1 för [enheter som inte kan registreras](#devices-fail-to-register)tidigare i den här artikeln.

#### <a name="a-license-required-for-jamf-intune-integration-has-expired"></a>En licens som krävs för JAMF-Intune-integrering har upphört att gälla

**Lösning**: se lösning för orsak 3 för [enheter som inte kan registreras](#devices-fail-to-register). 

#### <a name="the-required-ports-arent-open-on-your-network"></a>De portar som krävs är inte öppna i nätverket

**Lösning**: Granska informationen för nätverks portar i [krav](conditional-access-integrate-jamf.md#prerequisites) för att integrera JAMF Pro med Intune.


## <a name="next-steps"></a>Nästa steg
Lär dig mer om att [integrera JAMF Pro med Intune](conditional-access-integrate-jamf.md)