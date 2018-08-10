---
title: Använd API:er för att registrera tredjeparts certifikatutfärdare – Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller integrera SCEP GitHub-lösningen för tredjeparts certifikatutfärdare (CA) för att utfärda SCEP-certifikat till enheter i Microsoft Intune. Den här lösningen innehåller Java- och C#-API:er som validerar, skickar meddelanden om lyckat och misslyckat till Intune samt använder SSL socket factory vid kommunikation med Intune. Se även en översikt över stegen för att testa din SCEP CA-konfiguration.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 423bfc02edb9260adadf0a6dc67e6299639c7fbb
ms.sourcegitcommit: 8f68cd3112a71d1cd386da6ecdae3cb014d570f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39575057"
---
# <a name="use-apis-to-add-third-party-cas-for-scep-to-intune"></a>Använda API:er för att lägga till tredjeparts certifikatutfärdare för SCEP i Intune

I Microsoft Intune kan du lägga till tredjeparts certifikatutfärdare (CA) och göra så att dessa certifikatutfärdare utfärdar och verifierar certifikat med hjälp av registreringstjänst för nätverksenheter (SCEP). [Lägg till tredjeparts certifikatutfärdare](certificate-authority-add-scep-overview.md) innehåller en översikt över den här funktionen och beskriver administratörsåtgärderna i Intune.

Det finns även vissa uppgifter för utvecklare som använder ett bibliotek med öppen källkod som Microsoft har publicerat på GitHub.com. Biblioteket innehåller ett API som:

- Verifierar det SCEP-lösenord som genereras dynamiskt av Intune
- Meddelar Intune om de certifikat som skapas på enheter som skickar SCEP-begäranden

Med detta API integrerar din tredjeparts SCEP-server med Intune SCEP-hanteringslösningen för MDM-enheter. Biblioteket avlägsnar aspekter såsom autentisering, tjänstplats och ODATA Intune-tjänst-API från dess användare.

## <a name="scep-management-solution"></a>SCEP-hanteringslösning

![Så integrerar tredjeparts certifikatutfärdar-SCEP med Microsoft Intune](./media/scep-certificate-vendor-integration.png)

Med Intune kan administratörer skapa SCEP-profiler och sedan tilldela dessa profiler till MDM-enheter. SCEP-profilerna innehåller parametrar, till exempel:

- SCEP-serverns URL
- Det betrodda rotcertifikatet för certifikatutfärdaren
- Certifikatattribut och mer

Enheter som checkar in med Intune tilldelas SCEP-profilen och konfigureras med dessa parametrar. Ett dynamiskt genererat SCEP-utmaningslösenord skapas av Intune och tilldelas sedan till enheten.

Den här utmaningen innehåller:

- Det dynamiskt genererade utmaningslösenordet
- Information om de parametrar som förväntas i den certifikatsigneringsbegäran (CSR) som enheten utfärdar till SCEP-servern
- Utmaningens förfallotid

Intune krypterar informationen, loggar in den krypterade bloben och paketerar denna information i SCEP-utmaningslösenordet.

Enheter som kontaktar SCEP-servern för att begära ett certifikat anger sedan det här SCEP-utmaningslösenordet. SCEP-servern skickar CSR och det krypterade SCEP-utmaningslösenordet till Intune för verifiering.  Det här utmaningslösenordet samt CSR måste klara verifiering för att SCEP-servern ska utfärda ett certifikat till enheten. När en SCEP-utmaning verifieras sker följande kontroller:


- Verifiering av signaturen för den krypterade bloben
- Verifiering att utmaningen inte har gått ut
- Verifiering att profilen fortfarande är riktad mot enheten
- Verifiering att de certifikategenskaper som begärs av enheten i CSR matchar de förväntade värdena

SCEP-hanteringslösningen innehåller även rapportering. En administratör kan få information om distributionsstatus för SCEP-profilen och om de certifikat som utfärdas till enheter.

## <a name="integrate-with-intune"></a>Integrera med Intune

Koden för att biblioteket ska integrera med Intune SCEP är tillgänglig för nedladdning på [GitHub-lagringsplatsen Microsoft/Intune-Resource-Access](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation).

Integrering av biblioteket i dina produkter innefattar följande steg. Dessa steg kräver kunskaper om arbete med GitHub-lagringsplatser och att skapa lösningar och projekt i Visual Studio.

1. Registrera dig för att få meddelanden från lagringsplatsen
2. Klona eller ladda ned lagringsplatsen
3. Gå till den biblioteksimplementering som du behöver under `\src\CsrValidation`-mappen (https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
4. Skapa biblioteket med hjälp av anvisningarna i README-filen
5. Inkludera biblioteket i det projekt som skapar din SCEP-server
6. Utför följande uppgifter på SCEP-servern:

    - Tillåt att administratören konfigurerar [Azure Application-identifierare, Azure Application-nyckel och klientorganisations-ID](#onboard-scep-server-in-azure) (i den här artikeln) som biblioteket använder för autentisering. Administratörer bör tillåtas att uppdatera Application-nyckeln.
    - Identifiera SCEP-begäranden som innehåller ett Intune-genererat SCEP-lösenord
    - Använd biblioteket **Validate Request API** (API för att verifiera begäran) för att verifiera Intune-genererade SCEP-lösenord
    - Använd biblioteksmeddelande-API:er för att meddela Intune om certifikat som utfärdas för SCEP-begäranden som har de Intune-genererade SCEP-lösenorden. Meddela även Intune om fel som kan uppstå vid bearbetning av dessa SCEP-begäranden.
    - Bekräfta att servern loggar tillräckligt med information för att hjälpa administratörer att felsöka problem

7. Fullständig [integreringstestning](#integration-testing) (i den här artikeln) och åtgärda eventuella problem
8. Ge kunden skriftlig vägledning som förklarar:

    - Hur SCEP-servern måste registreras i Azure-portalen
    - Hur Azure Application-ID och Azure Application-nyckel som behövs för att konfigurera biblioteket ska hämtas

### <a name="onboard-scep-server-in-azure"></a>Registrera SCEP-server i Azure

För att autentisera till Intune kräver SCEP-servern ett Azure Application-ID, en Azure Application-nyckel och ett klientorganisations-ID. SCEP-servern behöver även behörighet att komma åt Intune-API.

För att hämta dessa data loggar SCEP-serveradministratören in på Azure-portalen, registrerar programmet, ger programmet behörighet för **Microsoft Intune API\SCEP-utmaningsverifiering**, skapar en nyckel för programmet och laddar sedan ned program-ID, dess nyckel och klientorganisations-ID.

Anvisningar för att registrera ett program och hämta ID:n och nycklar finns på sidan om att [använda portalen för att skapa ett AAD-program och tjänstens huvudnamn för resursåtkomst](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

### <a name="java-library-api"></a>API för Java-bibliotek

Java-biblioteket implementeras som ett Maven-projekt som hämtar dess beroenden när det skapas. API:et implementeras under namnrymden `com.microsoft.intune.scepvalidation` av klassen `IntuneScepServiceClient`.

#### <a name="intunescepserviceclient-class"></a>Klassen IntuneScepServiceClient

Klassen `IntuneScepServiceClient` innehåller metoder som används av SCEP-tjänsten för att verifiera SCEP-lösenord, meddela Intune om certifikat som skapas och visa en lista över eventuella fel.

##### <a name="intunescepserviceclient-constructor"></a>Konstruktorn IntuneScepServiceClient

Signatur:

```java
IntuneScepServiceClient(
    Properties configProperties)
```

Beskrivning:

Instansiera och konfigurera ett `IntuneScepServiceClient`-objekt.

Parametrar:

    - configProperties    Egenskapsobjekt som innehåller klientkonfigurationsinformation

Konfigurationen måste innehålla följande egenskaper:

    - AAD_APP_ID="The Azure Application Id obtained during the onboarding process" (Det Azure Application-ID som hämtas under registreringsprocessen)
    - AAD_APP_KEY="The Azure Application Key obtained during the onboarding process" (Den Azure Application-nyckel som hämtas under registreringsprocessen)
    - TENANT="The Tenant Id obtained during the onboarding process" (Det klientorganisations-ID som hämtas under registreringsprocessen)
    - PROVIDER_NAME_AND_VERSION="Information used to identify your product and its version" (Den information som används för att identifiera din produkt och dess version)

Returnerar:

    - IllegalArgumentException    Returneras om konstruktorn körs utan ett korrekt egenskapsobjekt.

> [!IMPORTANT]
> Det är bäst att instansiera en instans av den här klassen och använda den för att bearbeta flera SCEP-begäranden. Detta minskar overhead eftersom det cachelagrar autentiseringstoken och information om tjänstens plats.

**Säkerhetskommentarer**  
SCEP-serverns implementerare måste skydda data som anges i konfigurationsegenskaper som lagras mot manipulering och avslöjande. Det rekommenderas att du använder rätt ACL:er och kryptering för att skydda informationen.

##### <a name="validaterequest-method"></a>Metoden ValidateRequest

Signatur:

```java
void ValidateRequest(
    String transactionId,
    String certificateRequest)
```

Beskrivning:

Verifiera en SCEP-certifikatförfrågning.

Parametrar:

    - transactionId         SCEP-transaktions-ID:t
    - certificateRequest    DER-kodad PKCS #10-certifikatbegäran Base64-kodad som en sträng

Returnerar:

    - IllegalArgumentException      Returneras om den anropas med en ogiltig parameter
    - IntuneScepServiceException    Returneras om det upptäcks att certifikatbegäran är ogiltig
    - Exception (undantag)                     Returneras om ett oväntat fel uppstår

> [!IMPORTANT]
> Undantag som returneras av den här metoden ska loggas av servern. Observera att `IntuneScepServiceException`-egenskaperna har detaljerad information om varför verifieringen av certifikatbegäran misslyckades.

**Säkerhetskommentarer**  

  - Om den här metoden returnerar ett undantag **får SCEP-servern inte** utfärda ett certifikat till klienten.
  - Fel med verifiering av SCEP-certifikatbegäran kan tyda på ett problem i Intune-infrastrukturen. Eller så det kan tyda på att en angripare försöker hämta ett certifikat.

##### <a name="sendsuccessnotification-method"></a>Metoden SendSuccessNotification

Signatur:

```java
void SendSuccessNotification(
    String transactionId,
    String certificateRequest,
    String certThumbprint,
    String certSerialNumber,
    String certExpirationDate,
    String certIssuingAuthority)
```

Beskrivning:

Meddelar Intune om ett certifikat skapas som en del av bearbetningen av en SCEP-begäran.

Parametrar:

    - transactionId           SCEP-transaktions-ID:t
    - certificateRequest      DER-kodad PKCS #10-certifikatbegäran Base64-kodad som en sträng
    - certThumprint           Tumavtryck för det etablerade certifikatet
    - certSerialNumber        Serienummer för det etablerade certifikatet
    - certExpirationDate      Utgångsdatum för det etablerade certifikatet. Strängen för datum och tid ska formateras som webb-UTC-tid (ÅÅÅÅ-MM-DDThh:mm:ss.sssTZD) ISO 8601.
    - certIssuingAuthority    Namnet på den utfärdare som utfärdade certifikatet

Returnerar:

    - IllegalArgumentException      Returneras om den anropas med en ogiltig parameter
    - IntuneScepServiceException    Returneras om det upptäcks att certifikatbegäran är ogiltig
    - Exception (undantag)                     Returneras om ett oväntat fel uppstår

> [!IMPORTANT]
> Undantag som returneras av den här metoden ska loggas av servern. Observera att `IntuneScepServiceException`-egenskaperna har detaljerad information om varför verifieringen av certifikatbegäran misslyckades.

**Säkerhetskommentarer**

  - Om den här metoden returnerar ett undantag **får SCEP-servern inte** utfärda ett certifikat till klienten.
  - Fel med verifiering av SCEP-certifikatbegäran kan tyda på ett problem i Intune-infrastrukturen. Eller så det kan tyda på att en angripare försöker hämta ett certifikat.

##### <a name="sendfailurenotification-method"></a>Metoden SendFailureNotification

Signatur:

```java
void SendFailureNotification(
    String transactionId,
    String certificateRequest,
    long  hResult,
    String errorDescription)
```

Beskrivning:

Meddelar Intune om att ett fel uppstod när en SCEP-begäran bearbetades. Den här metoden ska inte anropas för undantag som returneras av metoderna i den här klassen.

Parametrar:

    - transactionId         SCEP-transaktions-ID:t
    - certificateRequest    DER-kodad PKCS #10-certifikatbegäran Base64-kodad som en sträng
    - hResult               Den Win32-felkod som bäst beskriver det fel som inträffade. Se [Win32-felkoder](https://msdn.microsoft.com/library/cc231199.aspx)
    - errorDescription      Beskrivning av det fel som inträffade

Returnerar:

    - IllegalArgumentException      Returneras om den anropas med en ogiltig parameter
    - IntuneScepServiceException    Returneras om det upptäcks att certifikatbegäran är ogiltig
    - Exception (undantag)                     Returneras om ett oväntat fel uppstår

> [!IMPORTANT]
> Undantag som returneras av den här metoden ska loggas av servern. Observera att `IntuneScepServiceException`-egenskaperna har detaljerad information om varför verifieringen av certifikatbegäran misslyckades.

**Säkerhetskommentarer**

  - Om den här metoden returnerar ett undantag **får SCEP-servern inte** utfärda ett certifikat till klienten.
  - Fel med verifiering av SCEP-certifikatbegäran kan tyda på ett problem i Intune-infrastrukturen. Eller så det kan tyda på att en angripare försöker hämta ett certifikat.

##### <a name="setsslsocketfactory-method"></a>Metoden SetSslSocketFactory

Signatur:

```java
void SetSslSocketFactory(
    SSLSocketFactory factory)
```

Beskrivning:

Använd den här metoden för att meddela klienten om att den måste använda angiven SSL socket factory (i stället för standard) när den kommunicerar med Intune.

Parametrar:

    - factory    Den SSL socket factory som klienten ska använda för HTTPS-begäranden

Returnerar:

    - IllegalArgumentException    Returneras om den anropas med en ogiltig parameter

> [!NOTE]
> SSL Socket factory måste anges om den behövs innan de andra metoderna i den här klassen körs.

## <a name="integration-testing"></a>Integreringstestning

Att verifiera och testa att din lösning är korrekt integrerad med Intune är ett måste. Följande lista visar en översikt över stegen:

1. Konfigurera ett [Intune-utvärderingskonto](account-sign-up.md).
2. Registrera [SCEP-servern i Azure-portalen](#onboard-scep-server-in-azure) (i den här artikeln).
3. [Konfigurera SCEP-servern](certificates-scep-configure.md) med de ID:n och den nyckel som skapas vid registrering av SCEP-servern.
4. [Registrera enheter](device-enrollment.md) för att testa scenarier i [scenariotestningsmatrisen](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
5. [Skapa en profil för betrott rotcertifikat](certificates-scep-configure.md) för din certifikatutfärdare för testning.
6. Skapa SCEP-profiler för att testa de scenarier som anges i [scenariotestningsmatrisen](https://github.com/Microsoft/Intune-Resource-Access/blob/develop/src/CsrValidation/doc/TestMatrix.csv).
7. [Tilldela profilerna](device-profile-assign.md) till användare som registrerat sina enheter.
8. Vänta tills enheterna synkroniserar med Intune. Eller så kan du manuellt [synkronisera enheterna](device-sync.md).
9. Bekräfta att det betrodda rotcertifikatet och SCEP-[profilerna distribueras till enheterna](device-profile-monitor.md).
10. Bekräfta att det betrodda rotcertifikatet är installerat på alla enheter.
11. Bekräfta att SCEP-certifikaten för de tilldelade profilerna är installerade på alla enheter.
12. Bekräfta att egenskaperna för de installerade certifikaten matchar de egenskaper som angetts i SCEP-profilen.
13. Bekräfta att de utfärdade certifikaten visas korrekt i Intune-konsolen

## <a name="see-also"></a>Se även

- [Lägg till översikt för tredjeparts certifikatutfärdare](certificate-authority-add-scep-overview.md)
- [Konfigurera Intune](setup-steps.md)
- [Enhetsregistrering](device-enrollment.md)
- [Konfigurera SCEP-certifikatprofiler](certificates-scep-configure.md#create-a-scep-certificate-profile) (konfiguration för Microsoft NDES Server\Connector används inte för det här scenariot)
