---
title: Använda härledda autentiseringsuppgifter för mobila enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd härledda autentiseringsuppgifter på mobila enheter som autentiseringsmetod för Intune-VPN, e-post, Wi-Fi-profiler, program samt S/MIME och kryptering. Härledda autentiseringsuppgifter är en implementering av NIST-riktlinjerna för Special Publication 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9e8bc347dc6336f665fcabfb4e716fef4818515
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207219"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Använda härledda autentiseringsuppgifter i Microsoft Intune

*Den här artikeln gäller för enheter som kör iOS*

I en miljö där smartkort krävs för autentisering eller kryptering och signering kan du nu använda Intune för att etablera mobila enheter med ett certifikat som härleds från en användares smartkort. Det certifikatet kallas för en *härledd autentiseringsuppgift*. Intune [stöder flera utfärdare av härledda autentiseringsuppgifter](#supported-issuers), men du kan bara använda en enda utfärdare per klientorganisation åt gången.

Härledda autentiseringsuppgifter är en implementering av riktlinjerna från National Institute of Standards and Technology (NIST) för härledda PIV-autentiseringsuppgifter (Personal Identity Verification) som en del av en Special Publication (SP) 800-157.

**Med Intunes implementering**:

- Intune-administratören konfigurerar sin klientorganisation så att den fungerar med en utfärdare av härledda autentiseringsuppgifter som stöds. Du behöver inte konfigurera några Intune-specifika inställningar i systemet för utfärdaren av härledda autentiseringsuppgifter.

- Intune-administratören anger **Härledda autentiseringsuppgifter** som *autentiseringsmetod* för följande objekt:

  - Vanliga profiltyper som Wi-Fi, VPN och e-post, som innehåller den inbyggda e-postappen för iOS

  - Appautentisering

  - S/MIME-signering och -kryptering

- Användare hämtar en härledd autentiseringsuppgift med hjälp av sitt smartkort på en dator för att autentisera till utfärdaren av härledda autentiseringsuppgifter. Utfärdaren utfärdar sedan ett certifikat som har härletts från smartkortet till den mobila enheten.

- När enheten har tagit emot den härledda autentiseringsuppgiften används den för autentisering samt för S/MIME-signering och -kryptering när appar eller resursåtkomstprofiler kräver den härledda autentiseringsuppgiften. 

## <a name="prerequisites"></a>Krav

Granska följande information innan du konfigurerar klientorganisationen att använda härledda autentiseringsuppgifter.

### <a name="supported-platforms"></a>Plattformar som stöds

Intune har stöd för härledda autentiseringsuppgifter på följande OS-plattformar:

- iOS/iPadOS

### <a name="supported-issuers"></a>Utfärdare som stöds

Intune har stöd för en enda utfärdare av härledda autentiseringsuppgifter för per klientorganisation. Du kan konfigurera Intune att fungera med följande utfärdare:

- **DISA Purebred**: https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercede**: https://www.intercede.com/

Viktig information om hur du använder olika utfärdare finns i vägledningen för respektive utfärdare<!-- , including the issuers end-user workflow-->. Mer information finns i [Planera för härledda autentiseringsuppgifter](#plan-for-derived-credentials) i den här artikeln.

> [!IMPORTANT]  
> Om du tar bort en utfärdare av härledda autentiseringsuppgifter från din klientorganisation kommer de härledda autentiseringsuppgifter som konfigurerades via den utfärdaren inte längre att fungera.
>
> Se [Ändra utfärdaren för härledda autentiseringsuppgifter](#change-the-derived-credential-issuer) senare i den här artikeln.

### <a name="company-portal-app"></a>Företagsportalappen

Planera för distribution av Intune-företagsportalappen till enheter som ska registreras för en härledd autentiseringsuppgift. Enhetsanvändare använder Företagsportal-appen för att starta processen för registrering av autentiseringsuppgifter.

Information om iOS-enheter finns i [Lägga till iOS-butiksappar till Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planera för härledda autentiseringsuppgifter

Förstå följande överväganden innan du konfigurerar en utfärdare av härledda autentiseringsuppgifter.

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) Granska dokumentationen för din valda utfärdare av härledda autentiseringsuppgifter  

Innan du konfigurerar en utfärdare bör du läsa igenom utfärdarens dokumentation för att förstå hur deras system levererar härledda autentiseringsuppgifter till enheter.

Beroende på vilken utfärdare du väljer kan du behöva ha personal tillgänglig vid tidpunkten för registreringen för att hjälpa användarna att slutföra processen. Du bör också granska dina aktuella Intune-konfigurationer för att se till att de inte blockerar åtkomst som krävs för att enheter eller användare ska kunna slutföra begäran om autentiseringsuppgifter.

Du kan till exempel använda villkorsstyrd åtkomst för att blockera åtkomst till e-post för icke-kompatibla enheter. Om du förlitar dig på e-postaviseringar för att uppmana användare att starta processen för registrering med härledda autentiseringsuppgifter får användarna kanske inte de instruktionerna förrän de efterlever principen.

På liknande sätt kräver vissa arbetsflöden för begäran av härledd autentiseringsuppgift användning av enhetskameran för att skanna en QR-kod på skärmen. Koden länkar den enheten till den autentiseringsbegäran som skedde mot utfärdaren av härledda autentiseringsuppgifter med användarens autentiseringsuppgifter för smartkort. Om principerna för enhetskonfiguration blockerar användningen av kameran kan användaren inte slutföra begäran om registrering med härledd autentiseringsuppgift.

Allmän information:

- Du kan endast konfigurera en enskild utfärdare per klientorganisation åt gången, och den utfärdaren är tillgänglig för alla användare och enheter som stöds i din klientorganisation.

- Användare meddelas inte om att de måste registrera sig för härledda autentiseringsuppgifter förrän du anger dem som mål för en princip som kräver härledda autentiseringsuppgifter.

- Avisering kan ske via appens avisering för Företagsportalen, via e-post eller både och. Om du väljer att använda e-postaviseringar och du använder aktiverad villkorsstyrd åtkomst får användarna kanske inte e-postaviseringen om deras enheter inte är kompatibla.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) Granska arbetsflödet för slutanvändare för din valda utfärdare

Nedan visas viktiga överväganden för varje partner som stöds.  Bekanta dig med den här informationen så att du kan se till att dina Intune-principer och konfigurationer inte blockerar användare och enheter från att slutföra registreringen för en härledd autentiseringsuppgift från den utfärdaren.

#### <a name="disa-purebred"></a>DISA Purebred

Granska [användararbetsflödet för DISA Purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Viktiga krav för det här arbetsflödet är:

- Användare behöver åtkomst till en dator eller KIOSK där de kan använda sina smartkort för att autentisera till utfärdaren.

- Enheter som ska registreras för en härledd autentiseringsuppgift måste installera Intune-företagsportalappen.

- Använd Intune för att [distribuera DISA Purebred-appen](#deploy-the-disa-purebred-app) till enheter som ska registreras för en härledd autentiseringsuppgift. Den här appen måste distribueras via Intune så att den hanteras och sedan kan fungera med Intune-företagsportalappen. Den här appen används av enhetsanvändare för att slutföra begäran om härledd autentiseringsuppgift.

- DISA Purebred-appen kräver ett [per-app-VPN](../configuration/vpn-settings-configure.md) för att se till att appen kan komma åt DISA Purebred under registreringen för den härledda autentiseringsuppgiften.

- Enhetsanvändare måste arbeta med supportpersonal under registreringsprocessen. Under registreringen får användaren tidsbegränsade engångslösenord under förloppet för registreringsprocessen.

Information om hur du hämtar och konfigurerar DISA Purebred-appen finns i [Distribuera DISA Purebred-appen](#deploy-the-disa-purebred-app) senare i den här artikeln.

#### <a name="entrust-datacard"></a>Entrust Datacard

Granska [användararbetsflödet för Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard). Viktiga krav för det här arbetsflödet är:

- Användare behöver åtkomst till en dator eller KIOSK där de kan använda sina smartkort för att autentisera till utfärdaren.

- Enheter som ska registreras för en härledd autentiseringsuppgift måste installera Intune-företagsportalappen.

- Användning av en enhetskamera för att skanna en QR-kod som länkar autentiseringsbegäran till begäran om härledd autentiseringsuppgift från den mobila enheten.

#### <a name="intercede"></a>Intercede

Granska [användararbetsflödet för Intercede](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Viktiga krav för det här arbetsflödet är:

- Användare behöver åtkomst till en dator eller KIOSK där de kan använda sina smartkort för att autentisera till utfärdaren.

- Enheter som ska registreras för en härledd autentiseringsuppgift måste installera Intune-företagsportalappen.

- Användning av en enhetskamera för att skanna en QR-kod som länkar autentiseringsbegäran till begäran om härledd autentiseringsuppgift från den mobila enheten.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) Distribuera ett betrott rotcertifikat till enheter

Ett betrott rotcertifikat används med härledda autentiseringsuppgifter för att verifiera att certifikatkedjan för härledda autentiseringsuppgifter är giltig och betrodd. Även utan direkt referens från princip krävs ett betrott rotcertifikat. Se [Konfigurera en certifikatprofil för enheterna i Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) Tillhandahålla instruktioner för slutanvändare om hur de hämtar den härledda autentiseringsuppgiften

Skapa och ge vägledning till dina användare om hur de startar processen för registrering med härledd autentiseringsuppgift samt hur de navigerar i arbetsflödet för registrering med härledd autentiseringsuppgift för din valda utfärdare.

Vi rekommenderar att du tillhandahåller en URL som är värd för din vägledning. Du anger den här URL:en när du konfigurerar utfärdaren av härledda autentiseringsuppgifter för din klientorganisation, och den URL:en görs tillgänglig från Företagsportal-appen. Om du inte anger din egen URL tillhandahåller Intune en länk till allmän information. Den här informationen kan inte omfatta alla scenarier och är kanske inte korrekt för din miljö.

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) Distribuera Intune-principer som kräver härledda autentiseringsuppgifter

Skapa nya principer eller redigera befintliga principer till att använda härledda autentiseringsuppgifter. Härledda autentiseringsuppgifter ersätter andra autentiseringsmetoder för appautentisering, Wi-Fi, VPN och e-post samt för S/MIME-signering och -kryptering.

Undvik att kräva användning av en härledd autentiseringsuppgift för åtkomst till en process som du kommer att använda som en del av processen för att hämta den härledda autentiseringsuppgiften, eftersom detta kan förhindra användare från att slutföra begäran.

## <a name="set-up-a-derived-credential-issuer"></a>Konfigurera en utfärdare för härledda autentiseringsuppgifter

Innan du skapar principer som kräver användning av en härledd autentiseringsuppgift konfigurerar du en utfärdare av autentiseringsuppgifter i Intune-konsolen. En utfärdare av härledda autentiseringsuppgifter är en inställning som gäller i hela klientorganisationen. Klientorganisationer har bara stöd för en enda utfärdare åt gången.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Administration av klientorganisation** > **Anslutningsappar och token** > **Härledda autentiseringsuppgifter**.

    > [!div class="mx-imgBorder"]
    > ![Konfigurera härledda autentiseringsuppgifter i konsolen](./media/derived-credentials/configure-provider.png)

3. Ange ett eget **Visningsnamn** för principen för utfärdare av härledda autentiseringsuppgifter.  Det här namnet visas inte för dina enhetsanvändare.

4. För **Utfärdare av härledda autentiseringsuppgifter**väljer du den utfärdare av härledda autentiseringsuppgifter som du har valt för din klientorganisation:
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

5. Ange en **hjälp-URL för härledd autentiseringsuppgift** för att tillhandahålla en länk till en plats som innehåller anpassade instruktioner som hjälper användarna att hämta härledda autentiseringsuppgifter för din organisation. Instruktionerna bör gälla specifikt för din organisation och för det arbetsflöde som krävs för att få en autentiseringsuppgift från din valda utfärdare. Länken visas i Företagsportal-appen och bör vara tillgänglig från enheten.

   Om du inte anger din egen URL tillhandahåller Intune en länk till allmän information som inte kan omfatta alla scenarier. Den här allmänna vägledningen är kanske inte korrekt för din miljö.

6. Välj ett eller flera alternativ för **Meddelandetyp**. Meddelandetyper är de metoder som du använder för att informera användarna om följande scenarier:

   - Registrera en enhet med en utfärdare för att hämta en ny härledd autentiseringsuppgift.
   - Hämta en ny härledd autentiseringsuppgift när den aktuella autentiseringsuppgiften är nära att upphöra.
   - Använd en härledd autentiseringsuppgift med en princip för autentisering via Wi-Fi, e-post eller app samt för S/MIME-signering och -kryptering.

7. När du är klar väljer du **Spara** för att slutföra konfigurationen av utfärdare av härledda autentiseringsuppgifter.

När du har sparat konfigurationen kan du göra ändringar i alla fält förutom *Utfärdare av härledda autentiseringsuppgifter*.  Om du vill ändra utfärdaren kan du läsa [Ändra utfärdaren av härledda autentiseringsuppgifter](#change-the-derived-credential-issuer).

## <a name="deploy-the-disa-purebred-app"></a>Distribuera DISA Purebred-appen

*Det här avsnittet gäller endast när du använder DISA Purebred*.

Om du vill använda **DISA Purebred** som utfärdare av härledda autentiseringsuppgifter för Intune måste du hämta DISA Purebred-appen och sedan använda Intune för att distribuera appen till enheter. Enhetsanvändare använder appen på sin enhet för att begära den härledda autentiseringsuppgiften från DISA Purebred.

Utöver att distribuera appen med Intune konfigurerar du ett per-app-VPN för Intune för DISA Purebred-programmet.

**Slutför följande steg**:
  
1. Ladda ned [DISA Purebred-programmet](https://cyber.mil/pki-pke/purebred/).
2. Distribuera DISA Purebred-programmet i Intune.  Se [Lägg till en verksamhetsspecifik app för iOS i Microsoft Intune](../apps/lob-apps-ios.md).
3. [Skapa ett per-app-VPN](../configuration/vpn-settings-configure.md) för DISA Purebred-programmet.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Använda härledda autentiseringsuppgifter för appautentisering samt för S/MIME-signering och -kryptering

Du kan ange **Härledd autentiseringsuppgift** för följande profiltyper och syften:

- [Program](#use-derived-credentials-for-app-authentication)
- [E-post](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME-signering och -kryptering](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  För Wi-Fi-profiler är *Autentiseringsmetod* endast tillgänglig när **EAP-typen** har angetts till något av följande värden:
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Använda härledda autentiseringsuppgifter för appautentisering

Använd härledda autentiseringsuppgifter för certifikatbaserad autentisering till webbplatser och program. Så här använder du en härledd autentiseringsuppgift för appautentisering:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ett bra profilnamn är till exempel **Härledd autentiseringsuppgift för iOS-enhetsprofil**.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
    - **Plattform**: Välj **iOS/iPadOS**.
    - **Profiltyp**: Välj **Härledd autentiseringsuppgift**.

4. Klicka på **OK** för att spara ändringarna.
5. När du är klar väljer du **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.
6. Välj din nya profil > **Tilldelningar**. Välj de grupper som ska ta emot principen.
 
Användare får appen eller e-postaviseringen beroende på vilka inställningar du angav när du konfigurerade utfärdaren av härledda autentiseringsuppgifter. Meddelandet uppmanar användaren att starta Företagsportalen så att de härledda autentiseringsuppgifterna kan bearbetas.

## <a name="renew-a-derived-credential"></a>Förnya en härledd autentiseringsuppgift

Härledda autentiseringsuppgifter kan inte utökas eller förnyas. Användarna måste i stället använda arbetsflödet för begäran om autentiseringsuppgifter för att begära en ny härledd autentiseringsuppgift för enheten.

Om du konfigurerar en eller flera metoder för **Meddelandetyp** meddelar Intune automatiskt användare när den aktuella härledda autentiseringsuppgiften når 80 % av sin livslängd. Meddelandet instruerar användarna att gå igenom processen för begäran om autentiseringsuppgifter för att få en ny härledd autentiseringsuppgift.

När en enhet får en ny härledd autentiseringsuppgift distribueras principer som använder härledda autentiseringsuppgifter på nytt till den enheten.


## <a name="change-the-derived-credential-issuer"></a>Ändra utfärdaren av härledda autentiseringsuppgifter

På klientorganisationsnivå kan du ändra utfärdaren av autentiseringsuppgifter. Dock stöds endast en enskild utfärdare för en klientorganisation åt gången.

När du har ändrat utfärdaren uppmanas användarna att hämta en ny härledd autentiseringsuppgift från den nya utfärdaren. De måste göra detta innan de kan använda en härledd autentiseringsuppgift för autentisering.

### <a name="change-the-issuer-for-your-tenant"></a>Ändra utfärdaren för din klientorganisation

> [!IMPORTANT]  
> Om du tar bort en utfärdare och omedelbart konfigurerar om samma utfärdare måste du fortfarande uppdatera profiler och enheter för att använda härledda autentiseringsuppgifter från den utfärdaren. Härledda autentiseringsuppgifter som hämtades innan du tar bort utfärdaren är inte längre giltiga.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Administration av klientorganisation** > **Anslutningsappar och token** > **Härledda autentiseringsuppgifter**.
3. Välj **Ta bort** för att ta bort den aktuella utfärdaren av härledda autentiseringsuppgifter.
4. Konfigurera en ny utfärdare.

### <a name="update-profiles-that-use-derived-credentials"></a>Uppdatera profiler som använder härledda autentiseringsuppgifter

När du har tagit bort en utfärdare och sedan lägger till en ny ska du redigera varje profil som använder härledda autentiseringsuppgifter. Den här regeln gäller även om du återställer den tidigare utfärdaren. Eventuella redigeringar av profilen utlöser en uppdatering, även om det gäller en en enkel redigering av profilens *Beskrivning*.

### <a name="update-derived-credentials-on-devices"></a>Uppdatera härledda autentiseringsuppgifter på enheter

När du har tagit bort en utfärdare och sedan lägger till en ny måste enhetsanvändare begära en ny härledd autentiseringsuppgift. Den här regeln gäller även när du lägger till samma utfärdare som du tog bort. Processen för att begära den nya härledda autentiseringsuppgiften är samma som för att registrera en ny enhet eller förnya en befintlig autentiseringsuppgift.

## <a name="next-steps"></a>Nästa steg

[Skapa profiler för enhetskonfiguration](../configuration/device-profile-create.md).
