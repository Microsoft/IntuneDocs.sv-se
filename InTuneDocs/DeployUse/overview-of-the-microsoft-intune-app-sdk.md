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
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 8a9dfe8224b4e0e441691043eaffea73c456b3ec


---

# Översikt över Microsoft Intune App SDK
Intune App SDK, som finns för både iOS- och Android-plattformen, gör det möjligt att använda hanteringsfunktioner för mobilappar med Microsoft Intune. Därutöver arbetar vi för att minska mängden kodändringar som utvecklare behöver göra. Som du kommer märka kan du aktivera de flesta SDK-funktioner utan att ändra appens beteende. För en ännu bättre upplevelse för slutanvändare och IT-administratörer kan du använda våra API:er för att anpassa din apps beteende till funktioner som kräver medverkan av din app. 

När du har aktiverat din app kan IT-administratörer distribuera principer till Intune-hanterade appar och utnyttja dessa funktioner för att skydda företagsdata i apparna.

# Funktioner
## Styra användarnas möjlighet att flytta företagsdokument
IT-administratörer kan styra hur företagsdokument kan flyttas i Intune-hanterade appar. De kan till exempel distribuera en princip som hindrar appar för säkerhetskopiering av filer från att säkerhetskopiera företagsdata till molnet.  

## Konfigurera begränsningar för Urklipp
IT-administratörer kan konfigurera beteendet för Urklipp i Intune-hanterade appar. De kan till exempel distribuera en princip så att slutanvändare inte kan använda Urklipp för att klippa ut/kopiera från en Intune-hanterad app och klistra in i en icke-hanterad app.

## Konfigurera begränsningar för skärmdumpar
IT-administratörer kan hindra användare från att ta skärmdumpar om en Intune-hanterad app visas. Med den här begränsningen kan du förhindra att konfidentiellt företagsinnehåll sparas och lämnas ut till obehöriga. Den här funktionen är endast tillgänglig för Android-enheter. 

## Framtvinga kryptering av sparade data
IT-administratörer kan tillämpa en princip som garanterar att data som sparas på enheten av appen krypteras.

## Fjärrensa företagsdata
IT-administratörer kan fjärrensa företagsdata från en Intune-hanterad app när enheten har avregistrerats från Microsoft Intune. Den här funktionen är identitetsbaserad och tar endast bort filer relaterade till slutanvändarens företagsidentitet. För att göra det kräver funktionen medverkan av appen. Appen kan ange identiteten som rensningen ska göras för baserat på användarinställningar. Om dessa användarinställningar inte anges från appen är standardbeteendet att rensa programkatalogen och att meddela slutanvändaren att åtkomsten till företagets resurser har återkallats. 

## Framtvinga användningen av en hanterad webbläsare
IT-administratörer kan framtvinga användningen av en hanterad webbläsare när länkar öppnas inifrån Intune-hanterade appar. Microsoft Intunes hanterade webbläsare ser till att länkar i e-postmeddelanden (i en Intune-hanterad e-postklient) stannar i domänen för Intune-hanterade appar.

## Tillämpa en PIN-princip
IT-administratörer kan tillämpa en PIN-princip när en Intune-hanterad app startar. Den här principen ser till att slutanvändarna som registrerat sina enheter med Microsoft Intune är samma personer som startar apparna. När slutanvändarna konfigurerar sina PIN-koder använder Intune App SDK Azure Active Directory för att kontrollera autentiseringsuppgifterna för slutanvändare mot autentiseringsuppgifterna för enhetsregistreringen. 

## Kräva att användarna anger autentiseringsuppgifter innan de kan starta appar
IT-administratörer kan kräva att användarna anger sina autentiseringsuppgifter innan de kan starta en Intune-hanterad app. Intune App SDK använder Azure Active Directory för att tillhandahålla enkel inloggning, där de autentiseringsuppgifter som anges återanvänds vid efterföljande inloggningar. Vi stöder också autentisering av identitetshanteringslösningar som är [federerade med Azure Active Directory](https://msdn.microsoft.com/en-us/library/azure/jj679342.aspx). 

## Kontrollera enhetens hälsotillstånd och efterlevnad
IT-administratörer kan kontrollera enhetens hälsotillstånd och huruvida enheten följer företagets principer innan slutanvändarna kan komma åt Intune-hanterade appar. På iOS-plattformen kontrollerar den här principen om enheten har blivit jailbreakad. På Android-plattformen kontrollerar den här principen om enheten har blivit rotad.  





<!--HONumber=Jun16_HO4-->


