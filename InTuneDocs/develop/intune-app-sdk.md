---
title: "Fördelar med Intune App SDK | Microsoft Intune"
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b7f62c5ee18d8f69fa174f09a1c46b6925c7517c
ms.openlocfilehash: 3abf566831348de11f718370d6267e3ff4355bfb


---

# Översikt över Intune App SDK
Intune App SDK, som finns för både iOS- och Android-plattformen, gör det möjligt att använda hanteringsfunktioner för mobilappar med Microsoft Intune. Därutöver arbetar vi för att minska mängden kodändringar som utvecklare behöver göra. Som du kommer märka kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. För en ännu bättre upplevelse för slutanvändare och IT-administratörer kan du använda våra API:er för att anpassa din apps beteende till funktioner som kräver medverkan av din app. När du har aktiverat din app kan IT-administratörer distribuera principer till Intune-hanterade appar och utnyttja dessa funktioner för att skydda företagsdata i apparna.

## Vanliga funktioner

### Styra användarnas möjlighet att flytta företagsdokument
IT-administratörer kan styra hur företagsdokument kan flyttas i Intune-hanterade appar. De kan till exempel distribuera en princip som hindrar appar för säkerhetskopiering av filer från att säkerhetskopiera företagsdata till molnet.

### Konfigurera begränsningar för Urklipp
IT-administratörer kan konfigurera beteendet för Urklipp i Intune-hanterade appar. De kan till exempel distribuera en princip så att slutanvändare inte kan använda Urklipp för att klippa ut/kopiera från en Intune-hanterad app och klistra in i en icke-hanterad app.

### Konfigurera begränsningar för skärmdumpar
IT-administratörer kan hindra användare från att ta skärmdumpar om en Intune-hanterad app visas. Med den här begränsningen kan du förhindra att konfidentiellt företagsinnehåll sparas och lämnas ut till obehöriga. Den här funktionen är endast tillgänglig för Android-enheter.

### Framtvinga kryptering av sparade data
IT-administratörer kan tillämpa en princip som garanterar att data som sparas på enheten av appen krypteras.

### Fjärrensa företagsdata
IT-administratörer kan fjärrensa företagsdata från en Intune-hanterad app när enheten har avregistrerats från Microsoft Intune. Den här funktionen är identitetsbaserad och tar endast bort filer relaterade till slutanvändarens företagsidentitet. För att göra det kräver funktionen medverkan av appen. Appen kan ange identiteten som rensningen ska göras för baserat på användarinställningar. Om dessa användarinställningar inte anges från appen är standardbeteendet att rensa programkatalogen och att meddela slutanvändaren att åtkomsten till företagets resurser har återkallats.

### Framtvinga användningen av en hanterad webbläsare
IT-administratörer kan framtvinga användningen av en hanterad webbläsare när länkar öppnas inifrån Intune-hanterade appar. Microsoft Intunes hanterade webbläsare ser till att länkar i e-postmeddelanden (i en Intune-hanterad e-postklient) stannar i domänen för Intune-hanterade appar.

### Tillämpa en PIN-princip
IT-administratörer kan tillämpa en PIN-princip när en Intune-hanterad app startar. Den här principen ser till att slutanvändarna som registrerat sina enheter med Microsoft Intune är samma personer som startar apparna. När slutanvändarna konfigurerar sina PIN-koder använder Intune App SDK Azure Active Directory för att kontrollera autentiseringsuppgifterna för slutanvändare mot autentiseringsuppgifterna för enhetsregistreringen.

### Kräva att användarna anger autentiseringsuppgifter innan de kan starta appar
IT-administratörer kan kräva att användarna anger sina autentiseringsuppgifter innan de kan starta en Intune-hanterad app. Intune App SDK använder Azure Active Directory för att tillhandahålla enkel inloggning, där de autentiseringsuppgifter som anges återanvänds vid efterföljande inloggningar. Vi stöder också autentisering av identitetshanteringslösningar som är [federerade med Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### Kontrollera enhetens hälsotillstånd och efterlevnad
IT-administratörer kan kontrollera enhetens hälsotillstånd och huruvida enheten följer företagets principer innan slutanvändarna kan komma åt Intune-hanterade appar. På iOS-plattformen kontrollerar den här principen om enheten har blivit jailbreakad. På Android-plattformen kontrollerar den här principen om enheten har blivit rotad.

## Förhandsgranskningsfunktioner
Microsoft Intune App SDK innehåller flera funktioner som fortfarande har förhandsgranskningsstatus. Du kan börja integrera med förhandsgransknings-API:er, men endast för testningsändamål. Observera att dessa förhandsgranskningar kompletterar snarare än ersätter befintliga scenarier.

### Stöd för flera identiteter i Microsoft Intune App SDK
Stöd för flera identiteter är en funktion som gör att principhanterade konton (företag) och ohanterade konton (personliga) kan finnas i samma app.

### Exempel på ett scenario med flera identiteter
Många användare konfigurerar både företagsspecifika och personliga e-postkonton i Outlook-appen för iOS och Android. När en användare kommer åt data på sitt företagskonto måste IT-administratören vara säker på att MAM-principhanteringen tillämpas. När en användare kommer åt ett personligt e-postkonto ska dessa data dock vara utanför IT-administratörens kontroll. Microsoft Intune uppnår detta genom att rikta hanteringsprincipen endast mot företagskontot i programmet. Funktionen för flera identiteter löser problemet med dataskydd som många organisationer ställs inför med enheter och appar som stöder både personliga och arbetsrelaterade konton.

### Ge stöd för flera identiteter
Med förhandsgransknings-API:er kan du ange ett UPN (User Principal Name) med specifika dataåtgärder som t.ex urklipps- och filåtgärder. Microsoft Intune App SDK använder UPN för att matcha anropet till det UPN som användes för att registrera enheten med Microsoft Intune-tjänsten. Om UPN-namnen matchar behandlas anropet som ett anrop för ”företagsdata” och informationen skyddas. Om UPN-namnen inte matchar varandra behandlas anropet som ett anrop för ”personuppgifter” och informationen skyddas inte.

### Apphantering utan enhetsregistrering
Många användare med personliga enheter vill kunna komma åt och använda företagsdata utan att registrera sina personliga enheter med en MDM-produkt för hantering av mobila enheter. MDM-registreringen kräver global kontroll över enheten men många användare är ovilliga att ge sina företag den typen av global kontroll över deras egna personliga enheter.

Med apphantering utan enhetsregistrering kan Microsoft Intune-tjänsten distribuera MAM-principen till en app direkt, utan att behöva använda en MDM-kanal för att distribuera principen. Eftersom ingen MDM-kanal krävs, behövs inte MDM-registreringen.




<!--HONumber=Jun16_HO4-->


