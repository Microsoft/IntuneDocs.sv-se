---
title: Felsöka problem med registrering av iOS-enhet i Microsoft Intune
titleSuffix: Microsoft Intune
description: Förslag på fel sökning av några av de vanligaste problemen när du registrerar iOS-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a02e403fdba34b576aa90b82062b7a602cbb517
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735694"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Felsöka problem med registrering av iOS-enhet i Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem när de registrerar iOS-enheter i Intune.

## <a name="prerequisites"></a>Krav

Innan du påbörjar fel sökningen är det viktigt att samla in grundläggande information. Den här informationen kan hjälpa dig att bättre förstå problemet och minska tiden för att hitta en lösning.

Samla in följande information om problemet:

- Vilket är det exakta felmeddelandet?
- Var visas fel meddelandet?
- När började problemet? Har registreringen någonsin fungerat?
- Vilken plattform (Android, iOS, Windows) har problemet?
- Hur många användare påverkas? Påverkas alla användare eller bara vissa av dem?
- Hur många enheter påverkas? Påverkas alla enheter eller bara vissa av dem?
- Vad är MDM-utfärdare? Vilken version av Configuration Manager använder du om det är System Center Configuration Manager?
- Hur utförs registreringen? Är det "ta med din egen enhet" (BYOD) eller Apple Programmet för enhetsregistrering (DEP) med registrerings profiler?

## <a name="error-messages"></a>Felmeddelanden

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Det gick inte att installera profilen. Ett nätverks fel har uppstått.

**Orsak:** Det finns ett ospecificerat problem med iOS på enheten.

#### <a name="resolution"></a>Lösning

1. För att förhindra data förlust i följande steg (att återställa iOS tar bort alla data på enheten), se till att säkerhetskopiera dina data.
2. Sätt enheten i återställnings läge och Återställ den sedan. Se till att du konfigurerar den som en ny enhet. Mer information om hur du återställer iOS-enheter finns i [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Omregistrera enheten.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Det gick inte att installera profilen. Det gick inte att upprätta en anslutning till servern.

**Orsak:** Din Intune-klient är konfigurerad för att endast tillåta företagsägda enheter. 

#### <a name="resolution"></a>Lösning
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster**, sök efter Intune och välj sedan **Intune**.
3. Välj **Enhetsregistrering** > **Registreringsbegränsningar**.
4. Under **begränsningar för enhets typ**väljer du den begränsning som du vill ange **> Egenskaper** > **2 Välj plattformar** > Välj **Tillåt** för **iOS**och klicka sedan på **OK**.
5. Välj **Konfigurera plattformar**, Välj **Tillåt** för personligt ägda iOS-enheter och klicka sedan på **OK**.
6. Omregistrera enheten.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Den här tjänsten stöds inte. Ingen registreringsprincip.

**Orsak**: ett Apple MDM-Push-certifikat har inte kon figurer ATS i Intune eller så är certifikatet ogiltigt. 

#### <a name="resolution"></a>Lösning

- Om MDM-push-certifikatet inte har kon figurer ATS följer du stegen i [Hämta ett Apple MDM-Push-certifikat](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Om MDM-push-certifikatet är ogiltigt följer du stegen i [förnya Push-certifikat för Apple MDM](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Företagsportalen är för tillfället otillgänglig. Ett fel uppstod i Företagsportals appen. Om problemet kvarstår kontaktar du systemadministratören.

**Orsak:** Företagsportal appen är inaktuell eller skadad.

#### <a name="resolution"></a>Lösning
1. Ta bort företagsportalappen från enheten.
2. Ladda ner och installera **Microsoft Intune-företagsportalappen** från **App Store**.
3. Omregistrera enheten.

### <a name="device-cap-reached"></a>Enhetstaket har nåtts

**Orsak:** Användaren försöker registrera fler enheter än gränsen för enhets registrering.

#### <a name="resolution"></a>Lösning
1. Öppna [Intunes administrations portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) > **enheter** > **alla enheter**och kontrol lera antalet enheter som användaren har registrerat.
    > [!NOTE]
    > Du bör också ha den berörda användar inloggningen till [Intune-användargränssnittet](https://portal.manage.microsoft.com/) och kontrol lera enheter som har registrerats. Det kan finnas enheter som visas i [användar portalen för Intune](https://portal.manage.microsoft.com/) , men inte i [Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)-administrationskonsolen, och sådana enheter räknas även mot enhetens registrerings gräns.
2. Gå till **Admin** > **hantering av mobila enheter** > **registrerings regler** > kontrol lera enhets registrerings gränsen. Som standard är gränsen inställd på 15. 
3. Om antalet registrerade enheter har nått gränsen tar du bort onödiga enheter eller ökar gränsen för enhets registrering. Eftersom alla registrerade enheter förbrukar en Intune-licens rekommenderar vi att du alltid tar bort onödiga enheter först.
4. Omregistrera enheten.

### <a name="workplace-join-failed"></a>Workplace Join misslyckades

**Orsak:** Företagsportal appen är inaktuell eller skadad.  

#### <a name="resolution"></a>Lösning
1. Ta bort företagsportalappen från enheten.
2. Ladda ner och installera **Microsoft Intune-företagsportalappen** från **App Store**.
3. Omregistrera enheten.

### <a name="user-license-type-invalid"></a>Användar licens typen är ogiltig

**Orsak:** Den användare som försöker registrera enheten har ingen giltig Intune-licens.

#### <a name="resolution"></a>Lösning
1. Gå till [Microsoft 365 administrations Center](https://portal.office.com/adminportal/home#/homepage)och välj **användare** > **aktiva användare**.
2. Välj det berörda användar kontot > **produkt licenser** > **Redigera**.
3. Kontrol lera att den här användaren har tilldelats en giltig Intune-licens.
4. Omregistrera enheten.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Användarnamnet godkänns inte. Det här användar kontot har inte behörighet att använda Microsoft Intune. Kontakta system administratören om du anser att du har fått det här meddelandet i fel.

**Orsak:** Den användare som försöker registrera enheten har ingen giltig Intune-licens.

1. Gå till [Microsoft 365 administrations Center](https://portal.office.com/adminportal/home#/homepage)och välj **användare** > **aktiva användare**.
2. Välj det berörda användar kontot och välj sedan **produkt licenser** > **Redigera**.
3. Kontrol lera att den här användaren har tilldelats en giltig Intune-licens.
4. Omregistrera enheten.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Det gick inte att installera profilen. Den nya MDM-nyttolasten matchar inte den gamla nytto lasten.

**Orsak:** En hanterings profil har redan installerats på enheten.

#### <a name="resolution"></a>Lösning

1. Öppna **Inställningar** på iOS-enheten > **allmän** > **enhets hantering**.
2. Tryck på den befintliga hanterings profilen och tryck på **ta bort hantering**.
3. Omregistrera enheten.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Orsak:** APN-certifikatet (Apple Push Notification Service) saknas, är ogiltigt eller har upphört att gälla.

#### <a name="resolution"></a>Lösning
Kontrol lera att ett giltigt APN-certifikat har lagts till i Intune. Mer information finns i [Konfigurera iOS-och Mac-enhets hantering](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Orsak:** Det har uppstått ett problem med APNs-certifikatet (Apple Push Notification Service) som kon figurer ATS i Intune.

#### <a name="resolution"></a>Lösning
Förnya APNs-certifikatet och registrera sedan enheten på nytt.

> [!IMPORTANT]
> Se till att du förnyar APNs-certifikatet. Ersätt inte APNs-certifikatet. Om du ersätter certifikatet måste du Omregistrera alla iOS-enheter i Intune. 

- Information om hur du förnyar APN-certifikatet i fristående Intune finns i [förnya Apple MDM Push-certifikat](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Information om hur du förnyar APN-certifikatet i Intune hybrid med Configuration Manager finns i [Konfigurera iOS hybrid Device Management med System Center Configuration Manager och Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- Om du vill förnya APNs-certifikatet i Office 365, se [skapa ett APN-certifikat för iOS-enheter](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR-anslutningen är ogiltig

När du aktiverar en DEP-hanterad enhet som har tilldelats en registrerings profil, Miss lyckas registreringen och du får följande fel meddelande:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Orsak:** Det finns ett anslutnings problem mellan enheten och Apple DEP-tjänsten.

#### <a name="resolution"></a>Lösning
Åtgärda anslutnings problemet eller Använd en annan nätverks anslutning för att registrera enheten. Du kan också behöva kontakta Apple om problemet kvarstår.


## <a name="other-issues"></a>Andra problem

### <a name="dep-enrollment-doesnt-start"></a>DEP-registrering startar inte
När du aktiverar en DEP-hanterad enhet som har tilldelats en registrerings profil initieras inte Intunes registrerings process.

**Orsak:** Registrerings profilen skapas innan DEP-token laddas upp till Intune.

#### <a name="resolution"></a>Lösning

1. Redigera registrerings profilen. Du kan göra ändringar i profilen. Syftet med detta är att uppdatera profilens ändrings tid.
2. Synkronisera DEP-hanterade enheter: öppna Intune-portalen > **Admin** > **1 hantering av mobila enheter** > **iOS** > **programmet för enhetsregistrering** > **Synkronisera nu**. En synkroniseringsbegäran skickas till Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP-registrering fastnat vid användar inloggning
När du aktiverar en DEP-hanterad enhet som har tilldelats en registrerings profil, sker den första installationen efter att du angett autentiseringsuppgifter.

**Orsak:** Multi-Factor Authentication (MFA) har Aktiver ATS. För närvarande fungerar MFA inte under registreringen på DEP-enheter.

#### <a name="resolution"></a>Lösning
Inaktivera MFA och registrera sedan enheten på nytt.

## <a name="next-steps"></a>Nästa steg

- [Felsöka enhetsregistrering i Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Ställ en fråga i Intunes forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Kontrol lera Microsoft Intune support teamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Kontrol lera Microsoft Enterprise Mobility and Security-bloggen](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
