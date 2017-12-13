---
title: "Fördelar med Intune App SDK"
description: "Intune App SDK, som finns för både iOS- och Android-plattformen, gör det möjligt att använda hanteringsfunktioner för mobilappar med Microsoft Intune."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 08/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c711152d8afb75d688f5f820f6c50bbe6465efb7
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/08/2017
---
# <a name="intune-app-sdk-overview"></a>Översikt över Intune App SDK
Intune App SDK, som finns för både iOS och Android, gör det möjligt för din app att använda Intunes appskyddsprinciper. Den arbetar för att minimera mängden kodändringar i programmet som utvecklare behöver göra. Som du kommer märka kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. För en ännu bättre upplevelse för slutanvändare och IT-administratörer kan du använda våra API:er för att anpassa din apps beteende till funktioner som kräver medverkan av din app.

När du har aktiverat din app för appskyddsprinciper kan IT-administratörer distribuera dessa principer för att skydda företagsdata i appen.

## <a name="app-protection-features"></a>Appskyddsfunktioner

Följande är exempel på Intune-appskyddsfunktioner som kan aktiveras med SDK:n.

### <a name="control-users-ability-to-move-corporate-files"></a>Styr användarnas möjligheter att flytta företagsfiler
IT-administratörer kan styra var arbets- eller skolkontodata i appen kan flyttas. De kan till exempel distribuera en princip som hindrar appar från att säkerhetskopiera företagsdata till molnet.

### <a name="configure-clipboard-restrictions"></a>Konfigurera begränsningar för Urklipp
IT-administratörer kan konfigurera beteendet för Urklipp i Intune-hanterade appar. De kan till exempel distribuera en princip för att förhindra att slutanvändare klipper ut eller kopierar data från appen och sedan klistra in dem i en icke-hanterad, personlig app.

### <a name="enforce-encryption-on-saved-data"></a>Framtvinga kryptering av sparade data
IT-administratörer kan tillämpa en princip som garanterar att data som sparas på enheten av appen krypteras.

### <a name="remotely-wipe-corporate-data"></a>Fjärrensa företagsdata
IT-administratörer kan rensa företagsdata från en Intune-hanterad app via en fjärranslutning. Den här funktionen är identitetsbaserad och tar endast bort filer associerade med slutanvändarens företagsidentitet. För att göra det kräver funktionen medverkan av appen. Appen kan ange identiteten som rensningen ska göras för baserat på användarinställningar. Om dessa användarinställningar inte anges från appen är standardbeteendet att rensa programkatalogen och att meddela slutanvändaren att åtkomsten har återkallats.

### <a name="enforce-the-use-of-a-managed-browser"></a>Framtvinga användningen av en hanterad webbläsare
IT-administratörer kan tvinga webblänkar i appen att öppnas i [Intune-appen Managed Browser](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies). Detta garanterar att länkar som visas i en företagsmiljö hålls inom domänen för Intune-hanterade appar.

### <a name="enforce-a-pin-policy"></a>Tillämpa en PIN-princip
IT-administratörer kan kräva att slutanvändaren anger en PIN-kod innan de ansluter till företagets data i appen. Detta garanterar att användaren som använder appen är samma användare som ursprungligen loggade in med sitt registrerade arbets- eller skolkonto. När slutanvändarna konfigurerar sina PIN-koder använder Intune App SDK Azure Active Directory för att kontrollera autentiseringsuppgifterna för slutanvändare mot det registrerade Intune-kontot.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>Kräv att användare loggar in med arbets-eller skolkonto för åtkomst till appen
IT-administratörer kan kräva att användarna loggar in med sina arbets- eller skolkonto för att använda appen. Intune App SDK använder Azure Active Directory för att tillhandahålla enkel inloggning, där de autentiseringsuppgifter som anges återanvänds vid efterföljande inloggningar. Vi stöder även autentisering av identitetshanteringslösningar som är federerade med Azure Active Directory.

### <a name="check-device-health-and-compliance"></a>Kontrollera enhetens hälsotillstånd och efterlevnad
IT-administratörer kan kontrollera enhetens hälsotillstånd och huruvida enheten följer Intunes principer innan slutanvändarna kan komma åt appar. På iOS kontrollerar den här principen om enheten har blivit jailbrokad. På Android kontrollerar den här principen om enheten har blivit rotad.

### <a name="multi-identity-support"></a>Stöd för flera identiteter
Stöd för flera identiteter är en SDK-funktion som gör att principhanterade konton (företag) och icke-hanterade konton (personliga) kan finnas i samma app.

Många användare konfigurerar till exempel både företagsspecifika och personliga e-postkonton i Office-mobilappar för iOS och Android. När en användare kommer åt data med sitt företagskonto måste IT-administratören vara säker på att appskyddsprincipen tillämpas. När en användare kommer åt ett personligt e-postkonto ska dessa data dock vara utanför IT-administratörens kontroll. Intune App SDK uppnår detta genom att rikta appskyddsprincipen **endast** mot företagsidentiteten i appen.

Funktionen för flera identiteter löser problemet med dataskydd som många organisationer ställs inför med Store-appar som stöder både personliga och arbetsrelaterade konton.
 
### <a name="app-protection-without-device-enrollment"></a>Appskydd utan enhetsregistrering

>[!IMPORTANT]
>Intunes appskydd utan enhetsregistrering är tillgängligt för Intunes programhanteringsverktyg, Intune App SDK för Android, Intune App SDK för iOS, SDK Xamarin-komponenten och SDK Cordova-plugin-programmet.

Många användare med personliga enheter vill kunna komma åt företagsdata utan att registrera sina personliga enheter med en MDM-leverantör för hantering av mobila enheter. MDM-registreringen kräver global kontroll över enheten men många användare är ovilliga att ge kontroll över deras personliga enheter till företagen.

Med appskydd utan enhetsregistrering kan Microsoft Intune-tjänsten distribuera appskyddsprincipen till en app direkt, utan att behöva använda en enhetshanteringskanal för att distribuera principen.
