---
title: "Utvärdera mobilenhetshantering i Microsoft Intune"
description: "Utvärdera MDM i din kostnadsfria utvärderingsversion av Intune."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: adef9335d8f199e8dec56e92eb1fda8c180ac6ce
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>Utvärdera mobilenhetshantering i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Den här utvärderingsguiden visas hur mobilenhetshantering fungerar i Intune. Du kommer att:
- Registrera en enhet som ska hanteras av Intune.
- Skapa grupper för att organisera användare och enheter.
- Skapa och distribuera principer för hantering av vissa enheter till grupper.
- Publicera en app så att användare med registrerade enheter kan installera den på sina enheter.
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>Antaganden
I den här guiden förutsätter vi att du använder utvärderingsversionen i utvärderingssyfte och vill börja med en ren miljö när du prenumererar.

För att göra det lättare för dig att komma igång med utvärderingsversionen har vi konfigurerat en väldigt enkel miljö som enbart använder Intune och förutsätter att detta är din utfärdare för hantering av mobila enheter. Men igenom hela guiden gör vi dig uppmärksam på fördjupat tekniskt innehåll som du kan utforska vidare om du vill.

Du kan göra allt i utvärderingsversion som du kan göra i en prenumerationsversion. Den enda skillnaden är att du är begränsad till 100 användarkonton i utvärderingsversionen.

## <a name="whats-not-covered"></a>Vad som inte ingår
|Om du är intresserad av |Läs detta |
|------------------------|----------|
|MDM i en icke-testmiljö | [Komma igång](/intune/setup-steps) |
|MDM med Intune och System Center Configuration Manager | [Hantering av hybridmobilenheter](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management) |

Eftersom guiderna ovan hjälper dig att konfigurera Intune i produktionsmiljöer, så är de längre, och innehåller många fler beslutspunkter, än utvärderingsguiden.

När du bekantar dig med Intune föreslår vi att du börjar med utvärderigsgiden och sedan går vidare till de andra guiderna.

## <a name="prerequisites-for-this-evaluation"></a>Förutsättningar för den här utvärderingen
- Internet Explorer 10 eller senare
- En enhet som du använder för att testa hur Intune-användarna registrerar och hanterar sina enheter med hjälp av företagsportalen. Vi använder en iPad- och en Android-telefon för den här guiden.
- Om du vill hantera din iPad eller andra iOS-enheter måste du ha ett [Apple Push Notification Service-certifikat](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune).
- En [Intune-utvärderingsprenumeration](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>Ange MDM-auktoritet
Det första steget du måste vidta när du hanterar mobila enheter med Intune är att konfigurera din **MDM-auktoritet**.

Om du använder Intune fristående, vilket den här utvärderingsversionen förutsätter att du gör, eller om du använder Intune som en del av en EMS-prenumeration, så måste du konfigurera Intune som din MDM-auktoritet. Det innebär att du utser Intune till att vara den tjänst som du använder för att hantera mobilenheter i din organisation.

Kunder som vill använda Intune med System Center Configuration Manager för att hantera mobila enheter måste bestämma sig för om de vill använda Intune eller Configuration Manager för sin hantering av mobilenheter. Detta är ett viktigt beslut att fatta i en produktionsmiljö, eftersom det för närvarande är mycket svårt att ändra inställningarna när man väl har gjort dem, men det ligger utanför den här utvärderingsguidens område. Mer information om konsekvenserna av att konfigurera Intune eller Configuration Manager som din MDM-auktoritet finns i [Välja mellan fristående Intune-hantering och hybridmobilenhetshantering](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

Vi konfigurerar Intune som MDM-auktoritet för utvärderingsversionen. Detta påverkar inte din produktionsmiljö såvida du inte vill använda utvärderingsversionen för din produktionsmiljö.

1. I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Admin** &gt; **Hantering av mobila enheter**.
2. Välj **Ange MDM-auktoritet** i listan **Uppgifter** . Dialogrutan **Ange MDM-auktoritet** öppnas.
3. Intune begär bekräftelse på att du vill ha Intune som MDM-utfärdare. Markera kryssrutan och välj sedan **Ja** om du vill hantera mobila enheter med Intune.

## <a name="enroll-your-test-devices-into-intune"></a>Registrera dina testenheter i Intune

I den här guiden registrerar vi en Android-telefon- och en Apple iPad, men ger länkar till [Mer information om registrering av enheter i Intune](#Learn-more-about-device-enrollment) i slutet av det här avsnittet.
### <a name="android"></a>Android
Installera appen **Intune Company Portal** från Microsoft Corporation, som finns på [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612), och registrera dig med de Intune[-användarautentiseringsuppgifter som du skapade](sign-up-for-30-day-trial-microsoft-intune.md#add-users) när du registrerade dig för den kostnadsfria utvärderingsversionen.

### <a name="ios"></a>iOS
Innan användarna kan registrera sina iOS-enheter, måste du konfigurera Intune för att hantera dessa enheter.

1. **Hämta en certifikatsigneringsbegäran**<br/>
Logga in till Intune med ditt administratörskonto och gå till **Administration** > **Hantering av mobila enheter** > **iOS och Mac OS X** > **Överför ett APN-certifikat** och välj sedan **Hämta begäran om APN-certifikat**. Spara begäran om certifikatsignering (.csr) lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.
2.  **Hämta ett certifikat för Apple Push Notification Service**<BR/>
Gå till [Apple Push-certifikatprofilen](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2) och logga in med ditt företags Apple-ID för att skapa APN-certifikatet med hjälp av CSR-filen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil som inte kan användas för APN. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp Certifikat för servrar från tredje part och klicka på **Hämta**.<br/>
Hämta APN-certifikatet (.pem) och spara filen lokalt. Det här Apple-ID:t måste användas senare för att förnya ditt APN-certifikat.
3.  **Lägg till APN-certifikatet i Intune**<BR/>
Öppna Microsoft Intune-administratörskonsolen och gå till **Administration** > **Hantering av mobila enheter** > **iOS och Mac OS X** > **Överför ett APN-certifikat** och välj **Överför APN-certifikatet**. Gå till certifikatfilen (.pem), välj **Öppna** och ange ditt Apple-ID. Med APN-certifikatet. Intune kan registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.
4.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**<br/>
Registreringsinstruktioner för slutanvändare finns i [Registrera din iOS-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) och [Registrera din Mac OS X-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.


### <a name="learn-more-about-device-enrollment"></a>Läs mer om enhetsregistrering

Intune stöder följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

Kraven för att aktivera enhetshanteringen beror på vilka plattformar du vill hantera.
- Med mobila **Android**-enheter kan användarna [registrera sig med hjälp av företagsportalsappen](/intune-classic/deploy-use/set-up-android-management-with-microsoft-intune) som finns i Google Play. Det krävs ingen ytterligare konfiguration i Intune.
- [Konfigurera kraven för **iOS och Mac OS X**](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)

- [Konfigurera kraven för **Windows Phone**](/intune-classic/deploy-use/set-up-windows-phone-8.0-management-with-microsoft-intune).






## <a name="next-steps"></a>Nästa steg
[Organisera användare och enheter genom att skapa grupper](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)
