---
title: "Översikt över Microsoft Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4cb153c601b83b113a22b2acf3da5200cdb70472


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Översikt över Microsoft Intune App SDK
Med Intune App-SDK:n, som finns för både iOS- och Android-plattformarna, kan du använda hanteringsfunktionerna för mobilappar med Microsoft Intune. Dessutom verkar den för att minska den mängd kodändringar som utvecklarna måste göra.

Som du kommer märka kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. Om du vill skapa en ännu bättre upplevelse för slutanvändarna och IT-administratörerna kan du använda våra API:er för att anpassa din apps beteende för de funktioner för vilka appen krävs.

När du har aktiverat din app kan IT-administratörer distribuera principer till Intune-hanterade appar och utnyttja dessa funktioner för att skydda företagsdata i apparna.

# <a name="features"></a>Funktioner
## <a name="control-users-ability-to-move-corporate-documents"></a>Styra användarnas möjlighet att flytta företagsdokument
IT-administratörer kan styra hur företagsdokument kan flyttas i Intune-hanterade appar. De kan t.ex. distribuera en princip som hindrar säkerhetskopieringsappar från att säkerhetskopiera företagsdata till molnet.  

## <a name="configure-clipboard-restrictions"></a>Konfigurera begränsningar för Urklipp
IT-administratörer kan konfigurera beteendet för Urklipp i Intune-hanterade appar. De kan t.ex. distribuera en princip så att slutanvändarna inte kan använda Urklipp för att klippa ut/kopiera från en Intune-hanterad app och klistra in i en icke-hanterad app.

## <a name="enforce-encryption-on-saved-data"></a>Framtvinga kryptering av sparade data
IT-administratörerna kan tillämpa en princip som garanterar att data som appen sparar på enheten krypteras.

## <a name="remotely-wipe-corporate-data"></a>Fjärrensa företagsdata
IT-administratörer kan fjärrensa företagsdata från en Intune-hanterad app när enheten har avregistrerats från Microsoft Intune. Den här funktionen är identitetsbaserad och tar endast bort filer som är kopplade till slutanvändarens företagsidentitet. För att göra det kräver funktionen medverkan av appen. Appen kan ange identiteten som rensningen ska göras för baserat på användarinställningar. Om dessa användarinställningar inte anges från appen är standardbeteendet att rensa programkatalogen och att meddela slutanvändaren att åtkomsten till företagets resurser har återkallats.

## <a name="enforce-the-use-of-a-managed-browser"></a>Framtvinga användningen av en hanterad webbläsare
IT-administratörerna kan göra det nödvändigt att använda en hanterad webbläsare när länkar öppnas inifrån Intune-hanterade appar. När slutanvändare använder Microsoft Intune-hanterade webbläsare är det till hjälp om de länkar som visas i e-postmeddelanden i Intune-hanterade e-postklienter förblir i domänen för Intune-hanterade appar.

## <a name="enforce-a-pin-policy"></a>Tillämpa en PIN-princip
IT-administratörer kan tillämpa en PIN-princip när en Intune-hanterad app startar. Den här principen ser till att slutanvändarna som registrerat sina enheter med Microsoft Intune är samma personer som startar apparna. När slutanvändarna konfigurerar sina PIN-koder använder Intune App-SDK:n Azure Active Directory för att verifiera sina autentiseringsuppgifterna mot enhetsregistreringens autentiseringsuppgifter.

## <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Kräva att användarna anger autentiseringsuppgifter innan de kan starta appar
IT-administratörer kan kräva av slutanvändarna att de måste ange sina autentiseringsuppgifter för att kunna starta en Intune-hanterad app. Intune App-SDK:n använder Azure Active Directory för att tillhandahålla enkel inloggning. Det innebär att när autentiseringsuppgifterna har angetts en gång, så återanvänds de vid efterföljande inloggningar. SDK:n stöder också autentisering av identitetshanteringslösningar som är [federerade med Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility).

## <a name="check-device-health-and-compliance"></a>Kontrollera enhetens hälsotillstånd och efterlevnad
IT-administratörer kan kontrollera enhetens hälsotillstånd och huruvida enheten följer företagets principer innan slutanvändarna kan komma åt Intune-hanterade appar. På iOS-plattformen kontrollerar den här principen om enheten har blivit jailbreakad. På Android-plattformen kontrollerar den här principen om enheten har blivit rotad.  



<!--HONumber=Nov16_HO5-->


