---
title: "Fördelar med Intune App SDK | Microsoft Docs"
description: 
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: e8f96499f006af590b6e7da295503696110dad4e


---

# <a name="intune-app-sdk-overview"></a>Översikt över Intune App SDK
Intune App SDK, som finns för både iOS- och Android-plattformen, gör det möjligt att använda hanteringsfunktioner för mobilappar med Microsoft Intune. Den arbetar för att minimera mängden kodändringar i programmet som utvecklare behöver göra. Som du kommer märka kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. För en ännu bättre upplevelse för slutanvändare och IT-administratörer kan du använda våra API:er för att anpassa din apps beteende till funktioner som kräver medverkan av din app. 

När du har aktiverat din app kan IT-administratörer distribuera principer till Intune-hanterade appar och utnyttja dessa funktioner för att skydda företagsdata i apparna.

## <a name="regular-features"></a>Vanliga funktioner

### <a name="control-users-ability-to-move-corporate-documents"></a>Styra användarnas möjlighet att flytta företagsdokument
IT-administratörer kan styra hur företagsdokument kan flyttas i Intune-hanterade appar. De kan till exempel distribuera en princip som hindrar appar för säkerhetskopiering av filer från att säkerhetskopiera företagsdata till molnet.

### <a name="configure-clipboard-restrictions"></a>Konfigurera begränsningar för Urklipp
IT-administratörer kan konfigurera beteendet för Urklipp i Intune-hanterade appar. De kan till exempel distribuera en princip så att slutanvändare inte kan använda Urklipp för att klippa ut/kopiera från en Intune-hanterad app och klistra in i en icke-hanterad, personlig app.

### <a name="enforce-encryption-on-saved-data"></a>Framtvinga kryptering av sparade data
IT-administratörer kan tillämpa en princip som garanterar att data som sparas på enheten av appen krypteras.

### <a name="remotely-wipe-corporate-data"></a>Fjärrensa företagsdata
IT-administratörer kan rensa företagsdata från en Intune-hanterad app via en fjärranslutning. Den här funktionen är identitetsbaserad och tar endast bort filer associerade med slutanvändarens företagsidentitet. För att göra det kräver funktionen medverkan av appen. Appen kan ange identiteten som rensningen ska göras för baserat på användarinställningar. Om dessa användarinställningar inte anges från appen är standardbeteendet att rensa programkatalogen och att meddela slutanvändaren att åtkomsten har återkallats.

### <a name="enforce-the-use-of-a-managed-browser"></a>Framtvinga användningen av en hanterad webbläsare
IT-administratörer kan framtvinga användningen av Intune Managed Browser-appen när länkar öppnas inifrån Intune-hanterade appar. Detta garanterar att länkar som visas i en företagsmiljö hålls inom domänen för Intune-hanterade appar.

### <a name="enforce-a-pin-policy"></a>Tillämpa en PIN-princip
IT-administratörer kan tillämpa en PIN-princip när en Intune-hanterad app startas. Detta garanterar att användaren som startar appen är samma användare som ursprungligen loggade in med ett registrerat arbets- eller skolkonto. När slutanvändarna konfigurerar sina PIN-koder använder Intune App SDK Azure Active Directory för att kontrollera autentiseringsuppgifterna för slutanvändare mot det registrerade Intune-kontot.

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Kräva att användarna anger autentiseringsuppgifter innan de kan starta appar
IT-administratörer kan kräva att användarna anger sina autentiseringsuppgifter innan de kan starta en Intune-hanterad app. Intune App SDK använder Azure Active Directory för att tillhandahålla enkel inloggning, där de autentiseringsuppgifter som anges återanvänds vid efterföljande inloggningar. Vi stöder också autentisering av identitetshanteringslösningar som är [federerade med Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### <a name="check-device-health-and-compliance"></a>Kontrollera enhetens hälsotillstånd och efterlevnad
IT-administratörer kan kontrollera enhetens hälsotillstånd och huruvida enheten följer företagets principer innan slutanvändarna kan komma åt Intune-hanterade appar. På iOS-plattformen kontrollerar den här principen om enheten har blivit jailbreakad. På Android-plattformen kontrollerar den här principen om enheten har blivit rotad.

### <a name="sdk-multi-identity-support"></a>SDK med stöd för multiidentitet
Stöd för flera identiteter är en funktion som gör att principhanterade konton (företag) och ohanterade konton (personliga) kan finnas i samma app.

Många användare konfigurerar till exempel både företagsspecifika och personliga e-postkonton i Outlook-appen för iOS och Android. När en användare kommer åt data på sitt företagskonto måste IT-administratören vara säker på att MAM-principhanteringen tillämpas. När en användare kommer åt ett personligt e-postkonto ska dessa data dock vara utanför IT-administratörens kontroll. Microsoft Intune uppnår detta genom att rikta hanteringsprincipen endast mot företagskontot i programmet. Funktionen för flera identiteter löser problemet med dataskydd som många organisationer ställs inför med enheter och appar som stöder både personliga och arbetsrelaterade konton.

* **Ge stöd för flera identiteter**: Microsoft Intune App SDK-API:er låter dig ange ett UPN (User Principal Name) med specifika dataåtgärder som t.ex urklipps- och filåtgärder. SDK använder UPN för att matcha anropet till det UPN som användes för att registrera enheten med Microsoft Intune-tjänsten. Om UPN-namnen matchar behandlas anropet som ett anrop för ”företagsdata” och informationen skyddas. Om UPN-namnen inte matchar varandra behandlas anropet som ett anrop för ”personuppgifter” och informationen skyddas inte.

### <a name="app-management-without-device-enrollment"></a>Apphantering utan enhetsregistrering

>[!IMPORTANT]
>Intunes hantering av mobila program utan registrering av enheter är för närvarande endast tillgängligt med Intune App SDK för iOS. 


Många användare med personliga enheter vill kunna komma åt och använda företagsdata utan att registrera sina personliga enheter med en MDM-produkt för hantering av mobila enheter. MDM-registreringen kräver global kontroll över enheten men många användare är ovilliga att ge sina företag den typen av global kontroll över deras egna personliga enheter.

Med apphantering utan enhetsregistrering kan Microsoft Intune-tjänsten distribuera MAM-principen till en app direkt, utan att behöva använda en MDM-kanal för att distribuera principen. Eftersom ingen MDM-kanal krävs, behövs inte MDM-registreringen.



<!--HONumber=Dec16_HO2-->


