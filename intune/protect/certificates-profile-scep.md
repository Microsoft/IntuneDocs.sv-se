---
title: Använda SCEP-certifikatprofiler med Microsoft Intune – Azure | Microsoft Docs
description: Skapa och tilldela SCEP-certifikatprofiler (Simple Certificate Enrollment Protocol) med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88b7411095aee1b1d3a892ce4845812ceb1a9ac9
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547070"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Skapa och tilldela SCEP-certifikatprofiler i Intune

När du har [konfigurerat din infrastruktur](certificates-scep-configure.md) för att stödja Simple Certificate Enrollment Protocol-certifikat (SCEP) kan du skapa och sedan tilldela SCEP-certifikatprofiler till användare och enheter i Intune.

> [!IMPORTANT]  
> Innan du skapar SCEP-certifikatprofiler måste enheter som kommer att använda en SCEP-certifikatprofil lita på din betrodda rotcertifikatutfärdare (CA). Använd en *betrodd certifikatprofil* i Intune för att etablera det betrodda rotcertifikatutfärdarcertifikatet till användare och enheter. Information om den betrodda certifikatprofilen finns i [Exportera det betrodda rotcertifikatutfärdarcertifikatet](certificates-configure.md#export-the-trusted-root-ca-certificate) och [Skapa betrodda certifikatprofiler](certificates-configure.md#create-trusted-certificate-profiles) i *Använda certifikat för autentisering i Intune*.


## <a name="create-a-scep-certificate-profile"></a>Skapa en SCEP-certifikatprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.

3. Ange följande egenskaper:

4. Ange ett **namn** och en **beskrivning** för SCEP-certifikatprofilen.

5. I listrutan **Plattform** väljer du en [enhetsplattform som stöds](certificates-configure.md#supported-platforms-and-certificate-profiles) för detta SCEP-certifikat.

6. I listrutan **Profil** väljer du **SCEP-certifikat**.  

   För **Android Enterprise**-plattformen är *Profiltyp* indelad i två kategorier: *Endast enhetens ägare* och *Endast arbetsprofil*. Se till att välja rätt SCEP-certifikatprofil för de enheter du hanterar.  

   SCEP-certifikatprofiler för profilen *Endast enhetens ägare* har följande begränsningar:

   1. Under Övervakning är inte certifikatsrapportering tillgängligt för SCEP-certifikatprofiler för enhetsägare.

   2. Du kan inte använda Intune för att återkalla certifikat som etablerades av SCEP-certifikatprofiler för enhetsägare. Du kan hantera återkallning via en extern process eller direkt med certifikatutfärdaren. 

   4. För dedikerade Android Enterprise-enheter stöds SCEP-certifikatprofiler endast för Wi-Fi-nätverksanslutning och -autentisering.  SCEP-certifikatprofiler på dedikerade Android Enterprise-enheter stöds inte för VPN- eller appautentisering.   

   
7. Välj **Inställningar** och slutför sedan följande konfigurationer:

   - **Certifikattyp**:

     *(Gäller för:  Android, Android Enterprise, iOS, macOS, Windows 8.1 och senare samt Windows 10 och senare.)*

     Välj en typ beroende på hur du kommer att använda certifikatprofilen:

     - **Användare**: Certifikat av typen *Användare* kan innehålla både användarattribut och enhetsattribut i certifikatets ämne och SAN.  
     - **Enhet**:  *Enhetscertifikat* kan endast innehålla enhetsattribut i certifikatets ämne och SAN.

       Använd **Enhet** för scenarier såsom användarlösa enheter, till exempel kiosker, eller för Windows-enheter. På Windows-enheter placeras certifikatet i den lokala datorns certifikatarkiv.

   - **Ämnesnamnets format**:

     Välj hur ämnesnamnet i certifikatbegäran ska skapas automatiskt av Intune. Alternativen för ämnesnamnets format beror på den certifikattyp du väljer, antingen **Användare** eller **Enhet**.

     > [!NOTE]
     > Det finns ett [känt problem](#avoid-certificate-signing-requests-with-escaped-special-characters) med att använda SCEP för att hämta certifikat när ämnesnamnet i den resulterande certifikatsigneringsförfrågan (CSR) innehåller något av följande tecken som undantaget tecken (med ett omvänt snedstreck \\):
     > - \+
     > - ;
     > - ,
     > - =

     - **Certifikattypen Användare**

       Formatalternativ för *Format för namn på certifikatmottagare* omfattar:

       - **Inte konfigurerat**
       - **Allmänt namn**
       - **Eget namn, inklusive e-post**
       - **Eget namn som e-post**
       - **IMEI (International Mobile Equipment Identity)**
       - **Serienummer**
       - **Anpassad**: När du väljer det här alternativet visas även textrutan **Anpassad**. Använd det här fältet om du vill ange ett anpassat format för ämnesnamnet, inklusive variabler. Anpassat format stöder två variabler: **Eget namn (CN)** och **E-postadress (E)** . **Eget namn (cn)** kan ställas in till någon av följande variabler:

         - **CN={{UserName}}** : Användarens huvudnamn, till exempel janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}** : Ett ID som tilldelas när du registrerar en enhet i Azure Active Directory (AD). Detta ID används vanligtvis för att autentisera med Azure AD.
         - **CN={{SERIALNUMBER}}** : Det unika serienummer (SN) som vanligtvis används av tillverkaren för att identifiera en enhet.
         - **CN={{IMEINumber}}** : Det unika IMEI-nummer (International Mobile Equipment Identity) som används för att identifiera en mobiltelefon.
         - **CN={{OnPrem_Distinguished_Name}}** : En sekvens med relativa unika namn avgränsade med kommatecken, till exempel *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

           Om du vill använda variabeln *{{OnPrem_Distinguished_Name}}* ska du synkronisera användarattributet *onpremisesdistinguishedname* med hjälp av [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

         - **CN={{onPremisesSamAccountName}}** : Administratörer kan synkronisera attributet samAccountName från Active Directory till Azure AD med hjälp av Azure AD Connect till ett attribut som heter *onPremisesSamAccountName*. Intune kan ersätta denna variabel som en del av en begäran om certifikatutfärdande i ämnet på ett certifikat. Attributet samAccountName är användarens inloggningsnamn som används för att stödja klienter och servrar från en tidigare version av Windows (före Windows 2000). Formatet på användarens inloggningsnamn är: *Domännamn\testUser* eller bara *testUser*.

            Om du vill använda variabeln *{{onPremisesSamAccountName}}* ska du synkronisera användarattributet *onPremisesSamAccountName* med hjälp av [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) till din Azure AD.

         Genom att kombinera en eller flera av dessa variabler och statiska strängar kan du skapa ett anpassat format för ämnesnamnet, till exempel:  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         Det exemplet omfattar ett format för ämnesnamnet som använder variablerna CN och E samt strängar för värdena för organisationsenhet, organisation, plats, tillstånd och land/region. [CertStrToName-funktionen](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) beskriver den här funktionen och dess strängar som stöds.

      - **Certifikattypen Enhet**

        Formatalternativ för Format för namn på certifikatmottagare omfattar följande variabler:

        - **{{AAD_Device_ID}}** eller **{{AzureADDeviceId}}** – Vilken som helst av variablerna kan användas för att identifiera en enhet med hjälp av dess Azure AD-ID.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(Gäller endast för Windows och domänanslutna enheter)*
        - **{{MEID}}**

        Du kan ange de här variablerna följt av texten för variabeln i textrutan. Till exempel kan det egna namnet för en enhet som heter *Device1* läggas till som **CN={{DeviceName}}Device1**.

        > [!IMPORTANT]
        > - När du anger en variabel omger du variabelnamnet inom klammerparenteser { } som det visas i exemplet, för att undvika ett fel.  
        > - Enhetsegenskaper som används i *ämnet* eller *SAN* för ett enhetscertifikat, till exempel **IMEI**, **SerialNumber** och **FullyQualifiedDomainName**, är egenskaper som kan förfalskas av en person med åtkomst till enheten.
        > - En enhet måste ha stöd för alla variabler som anges i en certifikatprofil för att den profilen ska installeras på den enheten.  Om till exempel **{{IMEI}}** används i ämnesnamnet för en SCEP-profil och tilldelas till en enhet som inte har något IMEI-nummer kommer profilen inte att installeras.

   - **Alternativt namn för certifikatmottagare**: Välj hur Intune automatiskt ska skapa det alternativa namnet för certifikatmottagare i certifikatbegäran. Alternativen för SAN beror på den certifikattyp du valde, antingen **Användare** eller **Enhet**.

      - **Certifikattypen Användare**

        Välj bland de tillgängliga attributen:

        - **E-postadress**
        - **UPN (User Principal Name)**

        Till exempel kan användarcertifikattyper innehålla användarens huvudnamn (UPN) i det alternativa namnet för certifikatmottagare. Om ett klientcertifikat används för att autentisera mot en nätverksprincipserver, måste du ange alternativt mottagarnamn som UPN.

      - **Certifikattypen Enhet**

        Använd listrutan **Attribut** och välj ett attribut, tilldela ett **Värde** och **Lägg till** det i certifikatprofilen. Du kan lägga till flera värden genom att välja ytterligare attribut.

        Tillgängliga attribut omfattar:

        - **E-postadress**
        - **UPN (User Principal Name)**
        - **DNS**

        Med certifikattypen *Enhet* kan du använda följande variabler för enhetscertifikat för värdet:

        - **{{AAD_Device_ID}}** eller **{{AzureADDeviceId}}** – Vilken som helst av variablerna kan användas för att identifiera en enhet med hjälp av dess Azure AD-ID.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Om du vill ange ett värde för ett attribut omger du variabelnamnet med klammerparenteser, följt av texten för den variabeln. Till exempel kan ett värde för DNS-attributet läggas till i **{{AzureADDeviceId}}.domain.com** där *.domain.com* är texten. För en användare med namnet *User1* visas en e-postadress kanske som {{FullyQualifiedDomainName}}User1@Contoso.com.

        > [!IMPORTANT]
        > - När du använder en variabel för enhetscertifikat omger du variabelnamnet med klammerparenteser { }.
        > - Använd inte klammerparenteser **{ }** , vertikalstreck **|** eller semikolon **;** i den text som kommer efter variabeln.
        > - Enhetsegenskaper som används i *ämnet* eller *SAN* för ett enhetscertifikat, till exempel **IMEI**, **SerialNumber** och **FullyQualifiedDomainName**, är egenskaper som kan förfalskas av en person med åtkomst till enheten.
        > - En enhet måste ha stöd för alla variabler som anges i en certifikatprofil för att den profilen ska installeras på den enheten.  Om till exempel **{{IMEI}}** används i SAN för en SCEP-profil och tilldelas till en enhet som inte har något IMEI-nummer kommer profilen inte att installeras.

   - **Certifikatets giltighetsperiod**:

     Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i certifikatmallen. Om du konfigurerade certifikatmallen för att [stödja ett anpassat värde som kan anges i Intune-konsolen](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template) använder du den här inställningen för att ange hur lång tid som återstår innan certifikatet upphör att gälla.

     Om giltighetsperioden i certifikatmallen till exempel är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.

   - **Nyckellagringsprovider (KSP)** :

     *(Gäller för:  Windows 8.1 och senare samt Windows 10 och senare)*

     Ange var nyckeln till certifikatet lagras. Välj bland följande värden:

     - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module) om TPM finns, annars till programvaruprovider för nyckellagring**
     - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module), rapportera annars fel**
     - **Registrera på Passport, rapportera annars fel (Windows 10 och senare)**
     - **Registrera till programvaruprovider för nyckellagring**

   - **Nyckelanvändning**:

     Välj alternativ för nyckelanvändning för certifikatet:

     - **Digital signatur**: Tillåt nyckelutbyte endast när en digital signatur skyddar nyckeln.
     - **Nyckelchiffrering**: Tillåt nyckelutbyte endast när nyckeln är krypterad.

   - **Nyckelstorlek (bitar)** :

     Välj antalet bitar i nyckeln.

   - **Hash-algoritm**:

     *(Gäller för Android, Android Enterprise, Windows Phone 8.1, Windows 8.1 och senare samt Windows 10 och senare)*

     Välj en av de tillgängliga typerna av hash-algoritmer som ska användas med det här certifikatet. Välj den högsta säkerhetsnivå som de anslutande enheterna har stöd för.

   - **Rotcertifikat**:

     Välj den *betrodda certifikatprofil* som du tidigare konfigurerade och tilldelade till aktuella användare och enheter för den här SCEP-certifikatprofilen. Den betrodda certifikatprofilen används för att etablera användare och enheter med betrott rotcertifikatutfärdarcertifikat. Information om den betrodda certifikatprofilen finns i [Exportera det betrodda rotcertifikatutfärdarcertifikatet](certificates-configure.md#export-the-trusted-root-ca-certificate) och [Skapa betrodda certifikatprofiler](certificates-configure.md#create-trusted-certificate-profiles) i *Använda certifikat för autentisering i Intune*. Om du har en rotcertifikatutfärdare och en utfärdande certifikatutfärdare väljer du den profil för betrott rotcertifikat som är associerad med den utfärdande certifikatutfärdaren.

   - **Förbättrad nyckelanvändning**:

     Lägg till värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet *klientautentisering* så att användaren eller enheten kan autentisera till en server. Du kan lägga till ytterligare nyckelanvändningar efter behov.

   - **Tröskelvärde för förnyelse (%)** :

     Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs. Om du till exempel anger 20 görs ett försök att förnya certifikatet när certifikatet är 80 % upphört. Förnyelseförsök fortsätter tills förnyelsen lyckas. Förnyelsen genererar ett nytt certifikat, vilket resulterar i ett nytt offentligt/privat nyckelpar.

   - **Webbadresser för SCEP-server**:

     Ange en eller flera webbadresser för de NDES-servrar som utfärdar certifikat via SCEP. Ange till exempel något i stil med *https://ndes.contoso.com/certsrv/mscep/mscep.dll* . Du kan lägga till ytterligare SCEP-URL:er för belastningsutjämning vid behov eftersom URL:er slumpmässigt skickas till enheten med profilen. Om någon av SCEP-servrarna inte är tillgänglig misslyckas SCEP-begäran, och vid senare enhetsincheckningar är det möjligt att certifikatbegäran kan göras mot samma server som är nere.

8. Välj **OK** och välj sedan **Skapa**. Profilen skapas och visas i listan *Enhetskonfiguration – Profiler*.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Undvik förfrågningar om certifikatsignering med undantagna specialtecken

Det finns ett känt problem för SCEP- och PKCS-certifikatbegäranden som innehåller ett ämnesnamn med ett eller flera av följande specialtecken som undantaget tecken. Ämnesnamn som innehåller ett av specialtecknen som ett undantaget tecken resulterar i en CSR med ett felaktigt ämnesnamn. Ett felaktigt ämnesnamn resulterar i att Intunes kontrollvalidering misslyckas och att inget certifikat utfärdas.

Specialtecknen är:
- \+
- ,
- ;
- =

Använd något av följande alternativ för att undvika den här begränsningen när ditt ämnesnamn innehåller specialtecken:

- Kapsla in värdet i ämnesnamnet som innehåller det specialtecken med citattecken.  
- Ta bort specialtecknet från ämnesnamnsvärdet.

Du kan **till exempel** ha ett ämnesnamn som visas som *testanvändare (TestCompany, LLC)* .  En CSR som innehåller ett ämnesnamn som har kommatecken mellan *TestCompany* och *LLC* ger upphov till problem.  Du kan undvika problemet genom att placera citattecken runt hela ämnesnamnet eller genom att ta bort kommatecken från mellan *TestCompany* och *LLC*:

- **Lägg till citattecken:** *CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Ta bort kommatecknet**: *CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 Om du försöker undanta kommatecknet med ett omvänt snedstreck kommer detta dock att misslyckas med ett fel i CRP-loggen:
 
- **Undantaget kommatecken**: *CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

Felet liknar följande fel:

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Tilldela certifikatprofilen

Tilldela SCEP-certifikatprofiler på samma sätt som du [distribuerar enhetsprofiler](../configuration/device-profile-assign.md) för andra syften. Tänk dock på följande innan du fortsätter:

- När du tilldelar SCEP-certifikatprofiler till grupper installeras filen för betrott rotcertifikatutfärdarcertifikat (såsom det anges i den *betrodda certifikatprofilen*) på enheten. Enheten använder SCEP-certifikatprofilen för att skapa en certifikatbegäran för det betrodda rotcertifikatutfärdarcertifikatet.

- SCEP-certifikatprofilen installeras endast på enheter som kör den plattform som du angav när du skapade certifikatprofilen.

- Du kan tilldela certifikatprofiler till användarsamlingar eller enhetssamlingar.

- Om du vill publicera certifikat till enheter kort efter att enheten registrerats, tilldelar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du tilldelar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten kan ta emot principer.

- Om du använder samhantering för Intune och Configuration Manager i Configuration Manager ska du [ange arbetsbelastningsreglaget](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads) för resursåtkomstprinciper till **Intune** eller **Pilot Intune**. Den här inställningen gör att Windows 10-klienter kan starta processen för att begära certifikatet.

- Även om du skapar och tilldelar den betrodda certifikatprofilen och SCEP-certifikatprofilen separat måste båda tilldelas. Om inte båda är installerade på en enhet misslyckas SCEP-certifikatprincipen. Se till att alla betrodda rotcertifikatprofiler också distribueras till samma grupper som SCEP-profilen.

> [!NOTE]
> När en SCEP-profil är associerad med en profil på enheter med iOS, t.ex. en Wi-Fi eller VPN-profil, tar enheten emot ett certifikat för var och en av de ytterligare profilerna. Detta resulterar i att iOS-enheten har flera certifikat som levereras av SCEP-certifikatbegäran.  Om ett enskilt certifikat önskas måste du använda PKCS-certifikat i stället för SCEP-certifikat.  Detta beror på skillnader i hur SCEP- och PKCS-certifikat levereras till enheter.

## <a name="next-steps"></a>Nästa steg

[Tilldela profiler](../configuration/device-profile-assign.md)
