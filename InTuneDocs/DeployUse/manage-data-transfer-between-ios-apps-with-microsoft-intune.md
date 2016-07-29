---
title: "Hantera dataöverföring mellan iOS-appar | Microsoft Intune"
description: "I det här avsnittet beskrivs hur du kan hantera dataöverföringar mellan appar med funktionen Öppna med i iOS och hanteringsprinciper för mobilappar."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: b95b721ba2d26f3d8f621a7ca5a4968bc86c1daf


---

# Hantera dataöverföring mellan iOS-appar med Microsoft Intune
## Hantera iOS-appar
För att skydda företagets data måste du se till att filöverföringar begränsas till appar som hanteras av dig.  Du kan hantera iOS-appar på följande sätt:

-   Förhindra förlust av företagets data genom att konfigurera MAM-principen för appar, något som vi kommer att referera till som **principhanterade** appar.

-   Du kan också distribuera och hantera appar via **MDM-kanalen**.  Detta kräver att enheterna har registrerats i MDM-lösningen. Det kan vara **principhanterade** appar eller andra hanterade appar.

Med funktionen **Öppna i hantering** för iOS-enheter kan du begränsa överförandet av filer mellan appar som är distribuerade via **MDM-kanalen**. Begränsningar för funktionen anges i inställningarna för konfiguration och distribueras via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.
##  Använda MAM med iOS-appar
Hanteringsprinciper för mobilappar (MAM) kan användas med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

-   **Medarbetarägda enheter som inte hanteras av en MDM-lösning:** Du kan konfigurera MAM-principinställningarna med **Tillåt endast att appen överför data till hanterade appar**. När slutanvändaren öppnar en skyddad fil i en app som inte är principhanterad går det inte att läsa filen.

-   **Enheter som hanteras av Intune:** Enheter som registreras i Intune tillåts automatiskt att överföra data mellan appar med principer för MAM och andra hanterade iOS-appar som distribueras via Intune. För att tillåta överföring av data mellan appar med principer för MAM, aktivera inställningen **Tillåt att appen överför data endast till hanterade appar**. Med funktionen **Öppna i hantering** kan du kontrollera dataöverföringen mellan appar som distribueras via Intune.   

-   **Enheter som hanteras av en tredje parts MDM-lösning:** Du kan begränsa dataöverföringen till endast hanterade appar med hjälp av iOS-funktionen **Öppna i hantering**.
För att säkerställa att appar som du distribuerar med en tredje parts MDM-lösning också är associerade med MAM-principer som du har konfigurerat i Intune, måste du konfigurera inställningen för UPN enligt beskrivningen i [Konfigurera UPN-inställningar](#configure-user-upn-setting).  När appar distribueras med inställningen för användar-UPN tillämpas MAM-principerna på appen när slutanvändaren loggar in med sitt arbetskonto.

> [!IMPORTANT]
> Inställningen för UPN krävs endast för appar som distribueras till enheter som hanteras av en tredje parts MDM.  Den här inställningen behövs inte för Intune-hanterade enheter.

## Konfigurera UPN-inställning
Den här konfigurationen krävs för enheter som hanteras av en tredje parts MDM-lösning. Nedan visas ett vanligt flöde för hur du implementerar UPN-inställningen och den resulterande användarupplevelsen:


1.  [Konfigurera en princip för hantering av mobila program](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för iOS-plattformen i Azure Portal. Konfigurera principinställningar enligt företagets krav och välj de appar som ska ha principen.

2.  Distribuera de appar och e-postprofiler som du vill ska hanteras **via din tredje part MDM-lösning** med hjälp av inställningen som beskrivs i steg 3 och 4.

3.  Distribuera appen med följande appkonfigurationsinställningar: key=IntuneMAMUPN, Value=<username@company.com> [example: ‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Distribuera principen Öppna i hantering till registrerade enheter.

### Exempel på slutanvändarupplevelse

1.  Slutanvändaren installerar Microsoft Word-appen på enheten.

2.  Slutanvändaren startar den hanterade interna e-postappen för att komma åt sin e-post.

3.  Slutanvändaren försöker öppna dokumentet från den interna e-postappen i Microsoft Word.

4.  När Word startas ombeds slutanvändaren logga in med sitt arbetskonto.  Arbetskontot användaren anger när den uppmanas ange ett konto bör matcha kontot som du angav i konfigurationsinställningarna för Microsoft Word-app.

    > [!NOTE]
    > Slutanvändaren kan lägga till andra personliga konton till Word för att utföra sitt personliga arbete och inte påverkas av MAM-principerna när de använder Word-appen i en personlig kontext.

5.  När inloggningen är klar tillämpas apprincipinställningarna för Word.

6.  Nu fungerar dataöverföringen och dokumentet märks med företagets ID i appen. Dessutom behandlas data i en arbetskontext och motsvarande principinställningar tillämpas.

### Se även
[Skydda appdata med hanteringsprinciper för mobila appar med Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


