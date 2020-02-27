---
title: Felsöka problem med registrering av iOS/iPadOS-enhet i Microsoft Intune
titleSuffix: Microsoft Intune
description: Förslag på felsökning av några av de vanligaste problemen när du registrerar iOS-/iPad-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514327"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Felsöka problem med registrering av iOS/iPadOS-enhet i Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem när de registrerar iOS/iPad-enheter i Intune.

## <a name="prerequisites"></a>Krav

Innan du påbörjar felsökningen är det viktigt att samla in grundläggande information. Den här informationen kan hjälpa dig att bättre förstå problemet och minska tiden för att hitta en lösning.

Samla in följande information om problemet:

- Vilket är det exakta felmeddelandet?
- Var visas felmeddelandet?
- När började problemet? Har registreringen någonsin fungerat?
- Vilken plattform (Android, iOS/iPad, Windows) har problemet?
- Hur många användare påverkas? Påverkas alla användare eller bara vissa av dem?
- Hur många enheter påverkas? Påverkas alla enheter eller bara vissa av dem?
- Vad är MDM-utfärdare?
- Hur utförs registreringen? Är det ”ta med din egen enhet” (BYOD) eller Apple-programmet för enhetsregistrering (DEP) med registreringsprofiler?

## <a name="error-messages"></a>Felmeddelanden

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Det gick inte att installera profilen. Ett nätverksfel har uppstått.

**Orsak:** Det finns ett ospecificerat problem med iOS/iPad på enheten.

#### <a name="resolution"></a>Lösning

1. För att förhindra dataförlust i följande steg (att återställa iOS/iPad tar bort alla data på enheten), se till att säkerhetskopiera dina data.
2. Sätt enheten i återställningsläge och återställ den sedan. Se till att du konfigurerar den som en ny enhet. Mer information om hur du återställer iOS/iPad-enheter finns i [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Omregistrera enheten.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Det gick inte att installera profilen. Det går inte att upprätta någon anslutning till servern.

**Orsak:** Din Intune-klient är konfigurerad för att endast tillåta företagsägda enheter. 

#### <a name="resolution"></a>Lösning
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter Intune och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Under **Begränsningar för enhetstyper**, väljer du den begränsning som du vill ställa in > **Egenskaper** > **Välj plattformar** > väljer **Tillåt** för **iOS**och klickar sedan på **OK**.
5. Välj **Konfigurera plattformar**, välj **Tillåt** för personligt ägda iOS/iPad-enheter och klicka sedan på **OK**.
6. Omregistrera enheten.

**Orsak:** De nödvändiga CNAME-posterna i DNS finns inte.

#### <a name="resolution"></a>Lösning
Skapa CNAME-DNS-resursposter för företagsdomänen. Om din företagsdomän exempelvis är contoso.com skapar du en CNAME-post i DNS-servern som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com.

Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

Om det finns fler än en verifierad domän, skapar du en CNAME-post för varje domän. CNAME-resursposten måste innehålla följande information:

|TYP|Värdnamn|Pekar på|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

> [!NOTE]
> Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

**Orsak:** Du registrerar en enhet som tidigare har registrerats med ett annat användarkonto och den tidigare användaren togs inte bort på rätt sätt från Intune.

#### <a name="resolution"></a>Lösning
1. Avbryt all aktuell profilinstallation.
2. Öppna [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) i Safari.
3. Omregistrera enheten.

> [!NOTE]
> Om registreringen fortfarande misslyckas kan du ta bort cookies i Safari (blockera inte cookies) och sedan registrera enheten på nytt.

**Orsak:** Enheten har redan registrerats med en annan MDM-provider.

#### <a name="resolution"></a>Lösning
1. Öppna **Inställningar** på iOS/iPad-enheten, gå till **Allmänt > Enhetshantering**.
2. Ta bort eventuell befintlig hanteringsprofil.
3. Omregistrera enheten.

**Orsak:** Den användare som försöker registrera enheten har ingen Microsoft Intune-licens.

#### <a name="resolution"></a>Lösning
1. Gå till [Administrationscentret för Office 365](https://portal.office.com/adminportal/home#/homepage) och välj **Användare > Aktiva användare**.
2. Markera det användarkonto som du vill tilldela en Intune-användarlicens och välj sedan **Produktlicenser > Redigera**.
3. Växla till **På** för den licens som du vill tilldela till den här användaren och välj sedan **Spara**.
4. Omregistrera enheten.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Den här tjänsten stöds inte. Ingen registreringsprincip.

**Orsak**: ett Apple MDM-pushcertifikat har inte konfigurerats i Intune eller så är certifikatet ogiltigt. 

#### <a name="resolution"></a>Lösning

- Om MDM-pushcertifikatet inte har konfigurerats följer du stegen i [Hämta ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Om MDM-pushcertifikatet är ogiltigt följer du stegen i [Förnya Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Företagsportalen är för tillfället otillgänglig. Ett fel uppstod i Företagsportalappen. Om problemet kvarstår kontaktar du systemadministratören.

**Orsak:** Företagsportalappen är inaktuell eller skadad.

#### <a name="resolution"></a>Lösning
1. Ta bort företagsportalappen från enheten.
2. Ladda ner och installera **Microsoft Intune-företagsportalappen** från **App Store**.
3. Omregistrera enheten.
 > [!NOTE]
    > Det här felet kan också inträffa om användaren försöker registrera fler enheter än enhetsregistreringen har konfigurerats för att tillåta. Följ lösningsstegen för **Enhetstaket har nåtts** nedan om de här stegen inte löser problemet.

### <a name="device-cap-reached"></a>Enhetstaket har nåtts

**Orsak:** Användaren försöker registrera fler enheter än gränsen för enhetsregistrering.

#### <a name="resolution"></a>Lösning
1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Alla enheter** och kontrollerar antalet enheter som användaren har registrerat.
    > [!NOTE]
    > Du bör också ha den berörda användarinloggningen till [Intune-användargränssnittet](https://portal.manage.microsoft.com/) och kontrollera enheter som har registrerats. Det kan finnas enheter som visas i [Intune-användarportalen](https://portal.manage.microsoft.com/), men inte i [Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)-administrationskonsolen, och sådana enheter räknas även mot enhetsregistreringsgränsen.
2. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Registreringsbegränsningar** > kontrollera enhetsregistreringsgränsen. Som standard är gränsen inställd på 15. 
3. Om antalet registrerade enheter har nått gränsen tar du bort onödiga enheter eller ökar enhetsregistreringsgränsen. Eftersom alla registrerade enheter förbrukar en Intune-licens rekommenderar vi att du alltid tar bort onödiga enheter först.
4. Omregistrera enheten.

### <a name="workplace-join-failed"></a>Workplace Join misslyckades

**Orsak:** Företagsportalappen är inaktuell eller skadad.  

#### <a name="resolution"></a>Lösning
1. Ta bort företagsportalappen från enheten.
2. Ladda ner och installera **Microsoft Intune-företagsportalappen** från **App Store**.
3. Omregistrera enheten.

### <a name="user-license-type-invalid"></a>Användarlicenstypen är ogiltig

**Orsak:** Den användare som försöker registrera enheten har ingen giltig Intune-licens.

#### <a name="resolution"></a>Lösning
1. Gå till [administrationscentret för Microsoft 365 ](https://portal.office.com/adminportal/home#/homepage) och välj sedan **Användare** > **Aktiva användare**.
2. Välj det påverkade användarkontot > **Produktlicenser** > **Redigera**.
3. Kontrollera att den här användaren har tilldelats en giltig Intune-licens.
4. Omregistrera enheten.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Användarnamnet godkänns inte. Det här användarkontot har inte behörighet att använda Microsoft Intune. Kontakta systemadministratören om du anser att du har fått det här meddelandet av misstag.

**Orsak:** Den användare som försöker registrera enheten har ingen giltig Intune-licens.

1. Gå till [administrationscentret för Microsoft 365 ](https://portal.office.com/adminportal/home#/homepage) och välj sedan **Användare** > **Aktiva användare**.
2. Välj det berörda användarkontot och välj sedan **Produktlicenser** > **Redigera**.
3. Kontrollera att den här användaren har tilldelats en giltig Intune-licens.
4. Omregistrera enheten.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Det gick inte att installera profilen. Den nya MDM-nyttolasten matchar inte den gamla nyttolasten.

**Orsak:** En hanteringsprofil har redan installerats på enheten.

#### <a name="resolution"></a>Lösning

1. Öppna **Inställningar** på iOS/iPad-enheten > **Allmänt** > **Enhetshantering**.
2. Tryck på den befintliga hanteringsprofilen och tryck på **Ta bort hantering**.
3. Omregistrera enheten.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Orsak:** APNs-certifikatet (Apple Push Notification Service) saknas, är ogiltigt eller har upphört att gälla.

#### <a name="resolution"></a>Lösning
Kontrollera att ett giltigt APNs-certifikat har lagts till i Intune. Mer information finns i [Konfigurera iOS/iPad-registrering](ios-enroll.md).

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Orsak:** Det har uppstått ett problem med APNs-certifikatet (Apple Push Notification Service) som konfigurerats i Intune.

#### <a name="resolution"></a>Lösning
Förnya APNs-certifikatet och registrera sedan enheten på nytt.

> [!IMPORTANT]
> Se till att du förnyar APNs-certifikatet. Ersätt inte APNs-certifikatet. Om du ersätter certifikatet måste du omregistrera alla iOS/iPad-enheter i Intune. 

- Information om hur du förnyar APNs-certifikatet i fristående Intune finns i [Förnya Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Om du vill förnya APNs-certifikatet i Office 365, se [Skapa ett APNs-certifikat för iOS/iPad-enheter](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR Anslutningen är ogiltig

När du aktiverar en DEP-hanterad enhet som har tilldelats en registreringsprofil, misslyckas registreringen och du får följande felmeddelande:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Orsak:** Det finns ett anslutningsproblem mellan enheten och Apple DEP-tjänsten.

#### <a name="resolution"></a>Lösning
Åtgärda anslutningsproblemet eller använd en annan nätverksanslutning för att registrera enheten. Du kan också behöva kontakta Apple om problemet kvarstår.


## <a name="other-issues"></a>Andra problem

### <a name="dep-enrollment-doesnt-start"></a>DEP-registrering startar inte
När du aktiverar en DEP-hanterad enhet som har tilldelats en registreringsprofil initieras inte Intune-registreringsprocessen.

**Orsak:** Registreringen skapas innan DEP-token laddas upp till Intune.

#### <a name="resolution"></a>Lösning

1. Redigera registreringsprofilen. Du kan göra ändringar i profilen. Syftet med detta är att uppdatera profilens ändringstid.
2. Synkronisera DEP-hanterade enheter: Gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), välj **Enheter** > **iOS** > **iOS-registrering** > **Registreringsprogramstoken** > välj en token > **Synkronisera nu**. En synkroniseringsbegäran skickas till Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP-registrering har fastnat vid användarinloggning
När du aktiverar en DEP-hanterad enhet som har tilldelats en registreringsprofil, sker den första installationen efter att du angett dina autentiseringsuppgifter.

**Orsak:** Multifaktorautentisering (MFA) har aktiverats. Förnärvarande fungerar inte MFA under registreringen på DEP-enheter.

#### <a name="resolution"></a>Lösning
Inaktivera MFA och registrera sedan enheten på nytt.


## <a name="next-steps"></a>Nästa steg

- [Felsöka enhetsregistrering i Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Ställ en fråga i Intunes forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Läs Microsoft Intune-supportteamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Läs bloggen om Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
