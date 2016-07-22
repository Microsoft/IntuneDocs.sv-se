---
title: "Begränsa åtkomsten till nätverk med Cisco ISE | Microsoft Intune"
description: "Använd Cisco ISE med Intune så att enheterna registreras av Intune och följer principen innan de får åtkomst till Wi-Fi och VPN-styrs av Cisco ISE."
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 78945498a951e7b897164ae6f33c4e87d521ca5b


---

# Använda Cisco ISE med Microsoft Intune
Med Intune-integration i Cisco ISE kan du skapa nätverksprinciper i ISE-miljön med enhetsregistrering och kompatibilitetstillstånd i Intune. Dessa principer kan säkerställa att åtkomst till företagets nätverk är begränsad till enheter som hanteras av Intune och är kompatibla med Intune-principer. 

## Konfiguration

Om du vill aktivera den här integreringen behöver du inte göra några inställningar i Intune-klienten. Du behöver ge behörighet till Cisco ISE-servern att få åtkomst till Intune-klienten och när det är klart sker resten av installationen i Cisco ISE-servern. Den här artikeln innehåller anvisningar för att tillhandahålla ISE-servern med behörighet att komma åt Intune-klienten. 

### Steg 1: Hantera certifikaten
1. Exportera certifikatet i Azure Active Directory-konsolen (AAD). 

    #### Internet Explorer 11
        
    a. Kör Internet Explorer som administratör och logga in på AAD-konsolen.
  
    b. Välj låsikonen i adressfältet och välj **Visa certifikat**
    
    c. På fliken **Information** för certifikategenskaperna väljer du **Kopiera till fil**.

    d. På välkomstsidan i **guiden Exportera certifikat** väljer du **Nästa**. 

    e. På sidan **Filformat för export** låter du standardvalet **DER-kodad binär fil x.509 (.CER)** stå kvar och väljer **Nästa**.  

    f. På sidan **Fil som ska exporteras** väljer du **Bläddra** för att välja en plats där filen ska sparas och anger ett filnamn. Även om det verkar som om du väljer en fil att exportera namnger du faktiskt filen där det exporterade certifikatet ska sparas. Välj **Nästa** &gt; **Slutför**.

    #### Safari
    
    a. Logga in på AAD-konsolen.

    b. Välj låsikonen &gt;  **Mer information**.
    
    c. Välj **Visa certifikat** &gt; **Information**.

    d. Välj certifikatet och välj sedan **Exportera**.  


> [!IMPORTANT]
> Kontrollera när certifikatet upphör att gälla, eftersom du måste exportera och importera ett nytt certifikat när det här upphör att gälla.

    

2. I ISE-konsolen importerar du Intune-certifikatet (filen du exporterade) till lagringsplatsen **Betrodda certifikat**.
3. I ISE-konsolen går du till **Administration** > **Certifikat** > **Systemcertifikat**.
4. Välj ISE-certifikatet och välj sedan **Exportera**.
5. Redigera det exporterade certifikatet i en textredigerare:
 - Ta bort ** -----BEGIN CERTIFICATE-----**
 - Ta bort ** -----END CERTIFICATE-----**
 - Se till att all text är på en enda rad

### Steg 2: Skapa en app för ISE i AAD-klienten
1. I Azure Active Directory-konsolen (AAD) väljer du **Program** > **Lägg till ett program** > **Lägg till ett program som min organisation utvecklar**.
2. Ange ett namn och en webbadress för appen. Webbadressen kan vara företagets webbplats.
3. Hämta appmanifestet (en JSON-fil).
4. Redigera JSON-manifestfilen. I inställningen som heter **keyCredentials** anger du den redigerade certifikattexten från Steg 1 som inställningsvärde.
5. Spara filen utan att ändra dess namn.
6. Ge appen behörighet till Microsoft Graph och Microsoft Intune API.
    1. Välj följande för Microsoft Graph
        - **Behörigheter för program**: Läsa katalogdata
        - **Delegerad behörighet**: 
            - Få åtkomst till användarens data när som helst
          - Logga in användare
   2. För Microsoft Intune API väljer du **Hämta enhetsstatus och efterlevnad från Intune** under **Behörigheter för program**.

7. Välj **Visa slutpunkter** och kopiera följande värden som ska användas vid konfigurering av ISE-inställningar:

|Värde i AAD-portalen|Motsvarande fält i ISE-portalen|
|-------------------|---------------------------------|
|Microsoft Azure AD-diagram API-slutpunkt|URL för automatisk identifiering|
|OAuth 2.0-token för slutpunkt|Tokenutfärdande URL|
|Uppdatera koden med klient-ID|Klient-ID|


### Steg 3: Konfigurera ISE-inställningar 
2. Ange dessa inställningsvärden i ISE-administrationskonsolen: 
  - **Servertyp**: Mobile Device Manager
  - **Autentiseringstyp**: OAuth – klientens autentiseringsuppgifter
  - **Automatisk identifiering**: Ja
  - **Automatisk identifiering av URL**: Ange värdet från steg 1
  - **Klient-ID**: Ange värdet från steg 1
  - **Tokenutfärdande URL**: Ange värdet från steg 1



## Information som delas mellan Intune-klienten och Cisco ISE-servern
Den här tabellen innehåller den information som delas mellan Intune-klienten och Cisco ISE-servern för enheter som hanteras av Intune.

|Egenskap|  Beskrivning|
|---------------|------------------------------------------------------------|
|complianceState|   Sant eller falskt (sträng) anger om enheten är kompatibel eller inkompatibel.|
|isManaged| Sant eller falskt (anger om klienten hanteras av Intune eller inte.|
|macAddress|Enhetens MAC-adress.|
|serialNumber|Enhetens serienummer. Gäller endast för iOS-enheter.|
|imei|IMEI (15 decimaler: 14 siffror plus en kontrollsiffra) eller IMEISV (16 siffror) innehåller information om ursprung, modell och serienumret för enheten. Strukturen för IMEI/SA anges i 3GPP TS 23.003. Gäller endast för enheter med SIM-kort.)|
|udid|Unikt enhets-ID, en sekvens med 40 bokstäver och siffror som är specifika för iOS-enheter.|
|meid|Identifierare för mobil utrustning, ett globalt unikt nummer för att identifiera en fysisk CDMA-mobilstationsutrustning. Formatet definieras av rapporten 3GPP2 S. R0048 men i praktiken kan det ses som en IMEI men med hexadecimala siffror. Ett MEID är 56 bitar långt (14 hexadecimala siffror). Det består av tre fält, inklusive en 8-bitars regional kod (RR), en 24-bitars tillverkarkod och ett 24-bitars serienummer som tilldelas av tillverkaren.| 
|osVersion| Enhetens operativsystemversion.
|modell|Enhetsmodell.
|manufacturer|Enhetstillverkare.
|azureDeviceId| Enhets-ID när den har anslutits med Azure Active Directory för arbetsplatsen. Är ett tomt guid för enheter som inte är anslutna.|
|lastContactTimeUtc|Datum och tid när enheten senast checkade in hos Intune-hanteringstjänsten. 


## Användarupplevelse

När en användare försöker få åtkomst till resurser med en enhet som inte är registrerad får denne en uppmaning att registrera sin enhet, t.ex. en sådan som visas här:

![Exempel på registreringsfråga](../media/cisco-ise-user-iphone.png)

När användaren väljer att registrera sin enhet dirigeras denna om till Intune-registreringsprocessen. Användarupplevelsen för registrering i Intune beskrivs i följande avsnitt:

- [Registrera en Android-enhet i Intune](/intune/end-user/enroll-your-device-in-Intune-android)</br>
- [Registrera din iOS-enhet i Intune](/intune/end-user/enroll-your-device-in-intune-ios)</br>
- [Registrera din Mac OS X-enhet i Intune](/intune/end-user/enroll-your-device-in-intune-mac-os-x)</br>
- [Registrera din Windows-enhet i Intune](/intune/end-user/enroll-your-device-in-intune-windows)</br> 

Det finns också en [nedladdningsbar uppsättning anvisningar för direktregistrering](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) som du kan använda för att skapa anpassad vägledning för användarupplevelsen.


### Se även

[Administratörsguide för Cisco Identity Services Engine, version 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)




<!--HONumber=Jun16_HO4-->


