---
title: "Skydda åtkomsten till nätverk med Cisco ISE | Microsoft Docs"
description: "Använd Cisco ISE med Intune så att enheterna registreras av Intune och följer principen innan de får åtkomst till Wi-Fi och VPN som styrs av Cisco ISE."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 9f34d54710f0ec662eecec85f7fa041061132a0d
ms.openlocfilehash: 8ef24e4d413662012f091c1be318d1d274e16439


---

# <a name="using-cisco-ise-with-microsoft-intune"></a>Använda Cisco ISE med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Intune-integration i Cisco Identity Services Engine (ISE) kan du skapa nätverksprinciper i ISE-miljön med hjälp av enhetsregistrering och kompatibilitetstillstånd i Intune. Med dessa principer kan du säkerställa att åtkomsten till företagets nätverk är begränsad till enheter som hanteras av Intune och är kompatibla med Intune-principer.

## <a name="configuration-steps"></a>Konfigurationssteg

Om du vill aktivera den här integreringen behöver du inte göra några inställningar i Intune-klienten. Du måste ge behörighet till Cisco ISE-servern för att få åtkomst till din Intune-klient. När det är klart görs de resterande inställningarna på Cisco ISE-servern. Den här artikeln innehåller anvisningar om hur du ger ISE-servern behörighet att komma åt Intune-klienten.

### <a name="step-1-manage-the-certificates"></a>Steg 1: Hantera certifikaten
Exportera certifikatet från Azure Active Directory (Azure AD)-konsolen och importera den sedan till arkivet Betrodda certifikat i ISE-konsolen:

#### <a name="internet-explorer-11"></a>Internet Explorer 11


   a. Kör Internet Explorer som administratör och logga in på Azure AD-konsolen.

   b. Välj låsikonen i adressfältet och välj **Visa certifikat**.

   c. På fliken **Information** för certifikategenskaperna väljer du **Kopiera till fil**.

   d. På välkomstsidan i **guiden Exportera certifikat** väljer du **Nästa**.

   e. På sidan **Filformat för export** låter du standardvalet **DER-kodad binär fil x.509 (.CER)** stå kvar och väljer **Nästa**.  

   f. På sidan **Fil som ska exporteras** väljer du **Bläddra** för att välja en plats där filen ska sparas och anger ett filnamn. Även om det verkar som om du väljer en fil att exportera namnger du faktiskt filen som det exporterade certifikatet ska sparas till. Välj **Nästa** &gt; **Slutför**.

   g. I ISE-konsolen importerar du Intune-certifikatet (filen du exporterade) till lagringsplatsen **Betrodda certifikat**.

#### <a name="safari"></a>Safari

 a. Logga in på Azure AD-konsolen.

b. Välj låsikonen &gt;  **Mer information**.

   c. Välj **Visa certifikat** &gt; **Information**.

   d. Välj certifikatet och välj sedan **Exportera**. 

   e. I ISE-konsolen importerar du Intune-certifikatet (filen du exporterade) till lagringsplatsen **Betrodda certifikat**.

> [!IMPORTANT]
>
> Kontrollera när certifikatet upphör att gälla, eftersom du måste exportera och importera ett nytt certifikat när det här upphör att gälla.


### <a name="obtain-a-self-signed-cert-from-ise"></a>Skaffa ett självsignerat certifikat från ISE 

1.  I ISE-konsolen väljer du **Administration** > **Certifikat** > **Systemcertifikat** > **Generera självsignerat certifikat**.  
2.       Exportera det självsignerade certifikatet.
3. Redigera det exporterade certifikatet i en textredigerare:

 - Ta bort ** -----BEGIN CERTIFICATE-----**
 - Ta bort ** -----END CERTIFICATE-----**
 
Se till att all text är på en enda rad


### <a name="step-2-create-an-app-for-ise-in-your-azure-ad-tenant"></a>Steg 2: Skapa en app för ISE i Azure AD-klienten
1. I Azure AD-konsolen väljer du **Program** > **Lägg till ett program** > **Lägg till ett program som min organisation utvecklar**.
2. Ange ett namn och en webbadress för appen. Webbadressen kan vara företagets webbplats.
3. Hämta appmanifestet (en JSON-fil).
4. Redigera JSON-manifestfilen. I inställningen som heter **keyCredentials** anger du den redigerade certifikattexten från Steg 1 som inställningsvärde.
5. Spara filen utan att ändra dess namn.
6. Ge appen behörighet till Microsoft Graph och Microsoft Intune API.

 a. Välj följande för Microsoft Graph:
    - **Behörigheter för program**: Läsa katalogdata
    - **Delegerad behörighet**:
        - Få åtkomst till användarens data när som helst
        - Logga in användare

 b. För Microsoft Intune API väljer du **Hämta enhetsstatus och efterlevnad från Intune** under **Behörigheter för program**.

7. Välj **Visa slutpunkter** och kopiera följande värden som ska användas vid konfigurering av ISE-inställningar:

|Värde i Azure AD-portalen|Motsvarande fält i ISE-portalen|
|-------------------|---------------------------------|
|Microsoft Azure AD-diagram API-slutpunkt|URL för automatisk identifiering|
|OAuth 2.0-token för slutpunkt|Tokenutfärdande URL|
|Uppdatera koden med klient-ID|Klient-ID|

### <a name="step-4-upload-the-self-signed-certificate-from-ise-into-the-ise-app-you-created-in-azure-ad"></a>Steg fyra: Överför det självsignerade certifikatet från ISE till ISE-appen som du skapade i Azure AD
1.     Hämta det base64-kodade certifikatvärdet och tumavtrycket från en offentlig .cer-X509-cert-fil. Det här exemplet använder PowerShell:
   
      
      $cer = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2    $cer.Import(“mycer.cer”)    $bin = $cer.GetRawCertData()    $base64Value = [System.Convert]::ToBase64String($bin)    $bin = $cer.GetCertHash()    $base64Thumbprint = [System.Convert]::ToBase64String($bin)    $keyid = [System.Guid]::NewGuid().ToString()
 
    Lagra värdena för $base64Thumbprint, $base64Value och $keyid, som ska användas i nästa steg.
2.       Överför certifikatet via manifestfilen. Logga in på [Windows Azure-hanteringsportal](https://manage.windowsazure.com)
2.      Hitta det program som du vill konfigurera med ett X.509-certifikat i Azure AD-snapin-modulen.
3.      Hämta program-manifestfilen. 
5.      Ersätt den tomma egenskapen "KeyCredentials": [], med följande JSON.  Den komplexa typen av KeyCredentials dokumenteras i [Entity and complex type reference](https://msdn.microsoft.com/library/azure/ad/graph/api/entity-and-complex-type-reference#KeyCredentialType) (Entitet och komplex typreferens).

 
    “keyCredentials“: [ { “customKeyIdentifier“: “$base64Thumbprint_from_above”, “keyId“: “$keyid_from_above“, “type”: “AsymmetricX509Cert”, “usage”: “Verify”, “value”:  “$base64Value_from_above” }2. 
     ], 
 
Exempel:
 
    “keyCredentials“: [
    {
    “customKeyIdentifier“: “ieF43L8nkyw/PEHjWvj+PkWebXk=”,
    “keyId“: “2d6d849e-3e9e-46cd-b5ed-0f9e30d078cc”,
    “type”: “AsymmetricX509Cert”,
    “usage”: “Verify”,
    “value”: “MIICWjCCAgSgAwIBA***omitted for brevity***qoD4dmgJqZmXDfFyQ”
    }
    ],
 
6.      Spara ändringen till program-manifestfilen.
7.      Överför den redigerade programmanifestfilen genom Azure-hanteringsportalen.
8.      Valfritt: Hämta manifestet igen för att kontrollera att ditt X.509-certifikat finns på programmet.

>[!NOTE]
>
> KeyCredentials är en samling, så du kan överföra flera X.509-certifikat för förnyelser eller ta bort certifikat i komprometterande scenarier.


### <a name="step-4-configure-ise-settings"></a>Steg fyra: Konfigurera ISE-inställningar
Ange dessa inställningsvärden i ISE-administrationskonsolen:
  - **Servertyp**: Mobile Device Manager
  - **Autentiseringstyp**: OAuth – klientens autentiseringsuppgifter
  - **Automatisk identifiering**: Ja
  - **Automatisk identifiering av URL**: *Ange värdet från steg 1.*
  - **Klient-ID**: *Ange värdet från steg 1.*
  - **Tokenutfärdande URL**: *Ange värdet från steg 1.*



## <a name="information-shared-between-your-intune-tenant-and-your-cisco-ise-server"></a>Information som delas mellan Intune-klienten och Cisco ISE-servern
Den här tabellen innehåller den information som delas mellan Intune-klienten och Cisco ISE-servern för enheter som hanteras av Intune.

|Egenskap|    Beskrivning|
|---------------|------------------------------------------------------------|
|complianceState|Sant- eller falskt-strängen som anger om enheten är kompatibel eller inkompatibel.|
|isManaged|Sant- eller falskt-strängen som anger om klienten hanteras av Intune eller inte.|
|macAddress|Enhetens MAC-adress.|
|serialNumber|Enhetens serienummer. Gäller endast för iOS-enheter.|
|imei|IMEI-numret (15 decimaler: 14 siffror plus en kontrollsiffra) eller IMEISV-numret (16 siffror) innehåller information om ursprung, modell och serienumret för enheten. Strukturen för detta nummer anges i 3GPP TS 23.003. Gäller endast för enheter med SIM-kort.|
|udid|Unikt enhets-ID, en sekvens med 40 bokstäver och siffror. ID:t är specifikt för iOS-enheter.|
|meid|Identifierare för mobil utrustning. Det här är ett globalt unikt nummer som identifierar en fysisk CDMA-mobilstationsutrustning. Nummerformatet definieras av 3GPP2-rapporten S. R0048. Men i praktiken kan det här numret ses som ett IMEI-nummer, men med hexadecimala siffror. Ett MEID är 56 bitar långt (14 hexadecimala siffror). Det består av tre fält, inklusive en 8-bitars regional kod (RR), en 24-bitars tillverkarkod och ett 24-bitars serienummer som tilldelas av tillverkaren.|
|osVersion|Enhetens operativsystemversion.
|modell|Enhetsmodellen.
|manufacturer|Enhetstillverkaren.
|azureDeviceId|Enhets-ID när den har anslutits med Azure AD för arbetsplatsen. Det här är ett tomt GUID för enheter som inte är anslutna.|
|lastContactTimeUtc|Datum och tid när enheten senast checkade in hos Intune-hanteringstjänsten.


## <a name="user-experience"></a>Användarupplevelse

När en användare försöker få åtkomst till resurser med en enhet som inte är registrerad får användaren en uppmaning att registrera sin enhet, t.ex. en sådan som visas här:

![Exempel på registreringsfråga](../media/cisco-ise-user-iphone.png)

När en användare väljer att registrera sin enhet dirigeras användaren om till Intune-registreringsprocessen. Användarupplevelsen för registrering i Intune beskrivs i följande avsnitt:

- [Registrera en Android-enhet i Intune](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Registrera en iOS-enhet i Intune](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Registrera en Mac OS X-enhet i Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Registrera en Windows-enhet i Intune](/intune/enduser/enroll-your-device-in-intune-windows)</br>

Det finns också en [nedladdningsbar uppsättning anvisningar för direktregistrering](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) som du kan använda för att skapa anpassad vägledning för användarupplevelsen.


### <a name="see-also"></a>Se även

[Administratörsguide för Cisco Identity Services Engine, version 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Jan17_HO1-->


