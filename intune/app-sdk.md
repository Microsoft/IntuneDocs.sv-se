---
title: Fördelar med Intune App SDK
titlesuffix: Microsoft Intune
description: Med Intune App-SDK:n, som finns för både iOS- och Android-plattformarna, kan du använda hanteringsfunktionerna för mobilappar med Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 02f276c5ddcd77b2800eb7b83a269b47a0ba5233
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180688"
---
# <a name="intune-app-sdk-overview"></a>Översikt över Intune App SDK
Intune App SDK, som finns för både iOS och Android, gör det möjligt för din app att använda Intunes appskyddsprinciper. Den arbetar för att minimera mängden kodändringar i programmet som utvecklare behöver göra. Som du märker kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. För att få en ännu bättre upplevelse för slutanvändare och IT-administratörer kan du använda API:er för att anpassa din apps beteende till funktioner som kräver medverkan av din app.

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
IT-administratörer kan tvinga webblänkar i appen att öppnas i [Intune-appen Managed Browser](app-configuration-managed-browser.md). Denna funktion säkerställer att länkar som visas i en företagsmiljö hålls inom domänen för Intune-hanterade appar.

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
>Intunes appskydd utan enhetsregistrering är tillgängligt för Intunes programhanteringsverktyg, Intune App SDK för Android, Intune App SDK för iOS och Intune App SDK Xamarin-bindningar.

Många användare med personliga enheter vill kunna komma åt företagsdata utan att registrera sina personliga enheter med en MDM-leverantör för hantering av mobila enheter. MDM-registreringen kräver global kontroll över enheten men många användare är ovilliga att ge kontroll över deras personliga enheter till företagen.

Med appskydd utan enhetsregistrering kan Microsoft Intune-tjänsten distribuera appskyddsprincipen till en app direkt, utan att behöva använda en enhetshanteringskanal för att distribuera principen.

### <a name="on-demand-application-vpn-connections-with-citrix-mvpn"></a>VPN-anslutningar för program på begäran med Citrix mVPN 
Du kan hantera enheter och appar med en kombination av Citrix XenMobile MDX och Microsoft Intune. Den här kombinationen innebär att du kan hantera appar med princip för Intune-appskydd samtidigt som du använder Citrix mVPN-teknik. Integrationen med Citrix finns för Intune App SDK för iOS och Android, och med Intunes programhanteringsverktyg för iOS och Android (med flaggan -citrix).
 
Mer information om Citrix MDX finns i [Om MDX Toolkit](http://docs.citrix.com/en-us/mdx-toolkit/10/about-mdx-toolkit.html), [Programhanteringsverktyget Citrix MDX för iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) och [Programhanteringsverktyget Citrix MDX för Android](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-android.html).
