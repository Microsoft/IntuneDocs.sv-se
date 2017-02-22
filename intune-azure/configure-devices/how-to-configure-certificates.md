---
title: "Hur du konfigurerar certifikat med Intune | Förhandsversionen av Intune Azure | Microsoft Docs"
description: "Förhandsversionen av Intune Azure: Information om hur du kan använda Intune för att skapa och tilldela certifikat som hjälper dig att skydda Wi-Fi, VPN och andra anslutningar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: a0183f2a170ed458b19c7688b20ee5ba5c2c696e


---

# <a name="how-to-configure-certificates-with-intune-azure-preview"></a>Hur du konfigurerar certifikat med förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

När du ger användare åtkomst till företagets resurser via VPN, Wi-Fi eller e-postprofiler kan du skydda åtkomsten genom att använda ett certifikat som installeras på varje användares enhet. Det prioriterade arbetsflödet ser ut så här:

1. Se till att du har rätt certifikatinfrastruktur på plats. Du kan använda [SCEP-certifikat](configure-certificate-infrastructure-for-scep.md) och [PKCS-certifikat](configure-certificate-infrastructure-for-pfx.md).
2. Installera ett rotcertifikat eller en mellanliggande certifikatutfärdare på alla enheter så att enheterna kan identifiera certifikatutfärdarens giltighet. Om du vill göra detta måste du skapa och tilldela en **betrodd certifikatprofil**. När du tilldelar den här profilen kommer enheter som du hanterar med Intune att begära och ta emot rotcertifikatet. Du måste skapa en separat profil för varje plattform. Profilerna för betrodda certifikat är tillgängliga för följande plattformar:
    - iOS 8.0 och senare
    - macOS 10.9 och senare
    - Android 4.0 och senare <!--Android for Work --->
    - Windows 8.1 och senare
    - Windows Phone 8.1 och senare
    - Windows 10 och senare
3. Skapa certifikatprofiler så att enheter begär ett certifikat som ska användas för autentisering av VPN, Wi-Fi och åtkomst av e-post. Du kan skapa och distribuera en **PKCS**- eller en **SCEP**-certifikatprofil för enheter som kör följande plattformar:
    - iOS 8.0 och senare
    - Android 4.0 och senare
    - Android for Work
    - Windows 10 (Desktop och Mobile) och senare

    Du kan bara använda en SCEP-certifikatprofil med dessa plattformar:

-   macOS 10.9 och senare
-   Windows Phone 8.1 och senare

Du måste skapa en separat profil för varje enhetsplattform. När du skapar profilen kopplar du den med den betrodda rotcertifikatprofilen som du redan skapat.

### <a name="further-considerations"></a>Ytterligare överväganden

- Du måste skapa en utfärdare av företagscertifikat om du inte redan har en.
- Om du, beroende på dina enhetsplattformar, väljer att använda SCEP-profilen (Simplified Certificate Enrollment Protocol) måste du också konfigurera en NDES-server (Network Device Enrollment Service).
- Om du planerar att använda SCEP- eller PKCS-profiler måste du hämta och konfigurera Microsoft Intune Certificate Connector.

## <a name="before-you-start"></a>Innan du börjar


### <a name="if-you-want-to-use-scep-certificates"></a>Om du vill använda SCEP-certifikat

Slutför de nödvändiga förutsättningarna i [Certifikatinfrastruktur för SCEP](/intune-azure/configure-devices/configure-certificate-infrastructure-for-scep).

### <a name="if-you-want-to-use-pkcs-certificates"></a>Om du vill använda PKCS-certifikat

Slutför de nödvändiga förutsättningarna i [Certifikatinfrastruktur för PKCS](/intune-azure/configure-devices/configure-certificate-infrastructure-for-pfx).

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>Uppgift 1: Exportera certifikatet för betrodd rotcertifikatutfärdare
Exportera certifikatet för betrodda rotcertifikatutfärdare som en **CER**-fil från den utfärdande certifikatutfärdaren eller från en enhet som litar på den utfärdande certifikatutfärdaren. Exportera inte den privata nyckeln.

Det här certifikatet importeras när du konfigurerar en certifikatprofil för en betrodd certifikatutfärdare.

## <a name="task-2-create-trusted-certificate-profiles"></a>Uppgift 2: Skapa certifikatprofiler för betrodda certifikatutfärdare
Du måste skapa en betrodd certifikatprofil innan du kan skapa en SCEP- eller PKCS-certifikatprofil. Du behöver en betrodd certifikatprofil och en SCEP- eller PKCS-profil för varje enhetsplattform.

### <a name="to-create-a-trusted-certificate-profile"></a>Så här skapar du en betrodd certifikatprofil

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för den betrodda certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta betrodda certifikat. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. Från listrutan **Profil** väljer du **Betrodda certifikat**.
7. Bläddra till certifikatet du sparade i uppgift 1 och klicka sedan på **OK**.
8. För Windows 8.1- och Windows 10-enheter, väjer du **Målarkiv** för det betrodda certifikatet från:
    - **Datorcertifikatarkiv – rot**
    - **Datorcertifikatarkiv – mellannivå**
    - **Användarcertifikatarkiv – mellannivå**
8. När du är klar väjer du **OK**, går tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).


> [!Note]
> Android-enheter visar ett meddelande om att en tredje part har installerat ett betrott certifikat.

## <a name="task-3-create-scep-or-pkcs-certificate-profiles"></a>Uppgift 3: Skapa SCEP- eller PKCS-certifikatprofiler
När du har skapat en certifikatprofil för betrodd certifikatutfärdare skapar du SCEP- eller PKCS-certifikatprofiler för varje plattform som du vill använda. När du skapar en SCEP-certifikatprofil måste du ange en betrodd certifikatprofil för samma plattform. Detta länkar de två certifikatprofilerna, men du måste fortfarande tilldela varje profil separat.

### <a name="to-create-an-scep-certificate-profile"></a>Så här skapar du en SCEP-certifikatprofil

1. I Azure-portalen väljer du arbetsbelastningen **Konfigurera enheter**.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för SCEP-certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta SCEP-certifikat. För närvarande kan du välja någon av följande plattformar för inställning av enhetsbegränsningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. Från listrutan **Profil** väljer du **SCEP-certifikat**.
7. På bladet **SCEP-certifikat**, konfigurerar du följande inställningar:
    - **Certifikatets giltighetsperiod** – Om du har kört kommandot **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** på certifikatutfärdaren, vilket gör att en anpassad giltighetsperiod kan användas, kan du ange hur lång tid som återstår innan certifikatet går ut.<br>Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren. 
    - **Nyckellagringsprovider (KSP)** (Windows Phone 8.1, Windows 8.1, Windows 10) – Ange var nyckeln till certifikatet ska lagras. Välj något av följande värden:
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module) om TPM finns, annars till programvaruprovider för nyckellagring**
        - **Registrera till nyckellagringsprovider för TPM (Trusted Platform Module), rapportera annars fel**
        - **Registrera på Passport, rapportera annars fel (Windows 10 och senare)**
        - **Registrera till programvaruprovider för nyckellagring**
    - **Format för namn på certifikatmottagare** – Välj i listan hur mottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om certifikatet avser en användare kan du ange användarens e-postadress i mottagarnamnet. Välj mellan:
        - **Inte konfigurerat**
        - **Allmänt namn**
        - **Eget namn, inklusive e-post**
        - **Eget namn som e-post**
    - **Alternativt namn för certifikatmottagare** – Ange hur värden för det alternativa certifikatmottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om du exempelvis valde en användarcertifikattyp kan du ange användarens huvudnamn (UPN) i det alternativa certifikatmottagarnamnet. Om klientcertifikatet ska användas för att autentisera mot en nätverksprincipserver måste du ange användarens huvudnamn som alternativt mottagarnamn. 
    - **Nyckelanvändning** – Ange alternativ för nyckelanvändning för certifikatet. Du kan välja bland följande alternativ: 
        - **Nyckelchiffrering:** Tillåt bara nyckelutbyte när nyckeln är krypterad. 
        - **Digital signatur:** Tillåt bara nyckelutbyte när en digital signatur skyddar nyckeln. 
    - **Nyckelstorlek (bitar)** – Välj antalet bitar som ska finnas i nyckeln. 
    - **Hash-algoritm** (Android, Windows Phone 8.1, Windows 8.1, Windows 10) – Välj en av de tillgängliga typerna av hash-algoritmer som ska användas med det här certifikatet. Välj den högsta säkerhetsnivå som de anslutande enheterna har stöd för. 
    - **Rotcertifikat** – Välj en certifikatprofil från en rotcertifikatutfärdare som du tidigare har konfigurerat och tilldelat till användaren eller enheten. Detta CA-certifikat måste vara rotcertifikatet för den certifikatutfärdare som kommer att utfärda det certifikat som du konfigurerar i den här certifikatprofilen. 
    - **Utökad nyckelanvändning** – Välj **Lägg till** om du vill lägga till värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet **Klientautentisering** så att användaren eller enheten kan autentisera till en server. Du kan dock lägga till alla andra nyckelanvändningar efter behov. 
    - **Registreringsinställningar**
        - **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
        - **Webbadresser för SCEP-server** – Ange en eller flera webbadresser för NDES-servrar som ska utfärda certifikat via SCEP. 
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

Följ anvisningarna på profilsidan för att konfigurera inställningarna för SCEP-certifikatet.
>[!Note]
> Endast för iOS-enheter: Välj Anpassad under Format för namn på certifikatmottagare om du vill ange ett eget format för namn på certifikatmottagare.
> De två variabler som stöds för närvarande för det anpassade formatet är **Nätverksnamn (cn)** och **E-post (e)**. Genom att använda en kombination av dessa variabler och statiska strängar kan du skapa ett eget format för namn på certifikatmottagare som det här: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US** I det här exemplet har du skapat ett format för namn som, utöver CN- och E-variabler, använder strängar för värden för organisationsenhet, organisation, plats, stat och land. [Det här avsnittet](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) visar funktionen **CertStrToName** och dess strängar som stöds.


### <a name="to-create-a-pkcs-certificate-profile"></a>Så här skapar du en PKCS-certifikatprofil

I Azure-portalen väljer du arbetsbelastningen **Konfigurera enheter**.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. På bladet **Skapa profil** anger du ett **Namn** och en **Beskrivning** för den PKCS-certifikatprofilen.
5. Från listrutan **Plattform** väljer du enhetsplattformen för detta PKCS-certifikat från:
    - **Android**
    - **iOS**
    - **Windows 10 och senare**
6. Från listrutan **Profil** väljer du **PKCS-certifikat**.
7. På bladet **PKCS-certifikat**, konfigurerar du följande inställningar:
    - **Tröskelvärde för förnyelse (%)** – Ange i procent hur mycket av certifikatets giltighetstid som får återstå innan förfrågningar om förnyat certifikat görs.
    - **Certifikatets giltighetsperiod** – Om du har kört kommandot **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE** på certifikatutfärdaren, vilket gör att en anpassad giltighetsperiod kan användas, kan du ange hur lång tid som återstår innan certifikatet går ut.<br>Du kan ange ett värde som är lägre men inte högre än giltighetsperioden i den angivna certifikatmallen. Om giltighetsperioden i certifikatmallen är två år kan du ange ett värde på ett år, men inte fem år. Värdet måste också vara lägre än den återstående giltighetsperioden för certifikatutfärdaren.
    - **Nyckellagringsprovider (KSP)** (Windows 10) –
    - **Certifikatutfärdare** -
    - **Namn på certifikatutfärdare** -
    - **Certifikatmallens namn** – Ange namnet på en certifikatmall som registreringstjänsten för nätverksenheter har konfigurerats att använda och som har lagts till i en certifikatutfärdare.
    Se till att namnet exakt matchar namnet på certifikatmallarna i listan i registret på den server som kör registreringstjänsten för nätverksenheter. Se till att du anger namnet på certifikatmallen och inte visningsnamnet på certifikatmallen. 
    Bläddra till följande nyckel om du vill söka efter namn på certifikatmallar: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP. Certifikatmallarna visas i listan som värden för **EncryptionTemplate**, **GeneralPurposeTemplate**och **SignatureTemplate**. Värdet för alla tre certifikatmallar är som standard IPSECIntermediateOffline vilket mappar till mallvisningsnamnet **IPSec (Offline request)**. 
    - **Format för namn på certifikatmottagare** – Välj i listan hur mottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om certifikatet avser en användare kan du ange användarens e-postadress i mottagarnamnet. Välj mellan:
        - **Inte konfigurerat**
        - **Allmänt namn**
        - **Eget namn, inklusive e-post**
        - **Eget namn som e-post**
    - **Alternativt namn för certifikatmottagare** – Ange hur värden för det alternativa certifikatmottagarnamnet i certifikatförfrågan ska skapas automatiskt i Intune. Om du exempelvis valde en användarcertifikattyp kan du ange användarens huvudnamn (UPN) i det alternativa certifikatmottagarnamnet. Om klientcertifikatet ska användas för att autentisera mot en nätverksprincipserver måste du ange användarens huvudnamn som alternativt mottagarnamn.
    - **Utökad nyckelanvändning** (Android) – Välj **Lägg till** om du vill lägga till värden för certifikatets avsedda syfte. I de flesta fall kräver certifikatet **Klientautentisering** så att användaren eller enheten kan autentisera till en server. Du kan dock lägga till alla andra nyckelanvändningar efter behov. 
    - **Rotcertifikat** (Android) – Välj en certifikatprofil från en rotcertifikatutfärdare som du tidigare har konfigurerat och tilldelat till användaren eller enheten. Detta CA-certifikat måste vara rotcertifikatet för den certifikatutfärdare som kommer att utfärda det certifikat som du konfigurerar i den här certifikatprofilen.
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.

## <a name="task-4-assign-certificate-profiles"></a>Uppgift 4: Tilldela certifikatprofiler

Tänk på följande innan du tilldelar certifikatprofiler till grupper:

- När du tilldelar certifikatprofiler till grupper installeras certifikatfilen från certifikatprofilen för betrodd certifikatutfärdare på enheten. Enheten använder SCEP- eller PKCS-certifikatprofilen för att skapa en certifikatbegäran.
- Certifikatprofiler installeras endast på enheter som kör den plattform som du använder när du skapade profilen.
- Du kan distribuera certifikatprofiler till användarsamlingar eller enhetssamlingar.
- Om du vill publicera certifikat till enheter snabbt efter att enheten registrerats, distribuerar du certifikatprofilen till en användargrupp i stället för en enhetsgrupp. Om du distribuerar till en enhetsgrupp krävs en fullständig enhetsregistrering innan enheten tar emot principer.
- Även om du distribuerar varje profil separat måste du också distribuera betrodd rotcertifikatutfärdare och SCEP- eller PKCS-profilen. Annars misslyckas SCEP- eller PKCS-certifikatprincipen.

## <a name="next-steps"></a>Nästa steg
Du hittar allmän information om hur du tilldelar enhetsprofilerna i [Tilldela enhetsprofilerna](how-to-assign-device-profiles.md).



<!--HONumber=Feb17_HO1-->


