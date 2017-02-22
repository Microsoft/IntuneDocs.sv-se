---
title: "Hantera dataöverföring mellan iOS-appar | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: I det här avsnittet beskrivs hur du kan hantera dataöverföringar mellan appar med funktionen Öppna med i iOS och hanteringsprinciper för mobilappar."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 8846417efd34db32d5a5c872ef438f5a0bc57e36


---

# <a name="how-to-manage-data-transfer-between-ios-apps"></a>Hur du hanterar dataöverföring mellan iOS-appar 
## <a name="manage-ios-apps"></a>Hantera iOS-appar
För att skydda företagets data måste du se till att filöverföringar begränsas till appar som hanteras av dig.  Du kan hantera iOS-appar på följande sätt:

-   Förhindra förlust av företagets data genom att konfigurera en appskyddsprincip, något som vi kommer att referera till som **principhanterade** appar.

-   Du kan också distribuera och hantera appar via **MDM-kanalen**.  Detta kräver att enheterna har registrerats i MDM-lösningen. Det kan vara **principhanterade** appar eller andra hanterade appar.

Med funktionen **Öppna i hantering** för iOS-enheter kan du begränsa överförandet av filer mellan appar som är distribuerade via **MDM-kanalen**. Begränsningar för funktionen anges i inställningarna för konfiguration och distribueras via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.
##  <a name="using-app-protection-with-ios-apps"></a>Använda appskydd med iOS-appar
Appskyddsprinciper kan användas med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

-   **Medarbetarägda enheter som inte hanteras av en MDM-lösning:** Du kan konfigurera inställningar för appskyddsprincip med **Tillåt endast att appen överför data till hanterade appar**. När slutanvändaren öppnar en skyddad fil i en app som inte är principhanterad går det inte att läsa filen.

-   **Enheter som hanteras av Intune:** Enheter som registreras i Intune tillåts automatiskt att överföra data mellan appar med appskyddsprinciper och andra hanterade iOS-appar som distribueras via Intune. För att tillåta överföring av data mellan appar med appskyddsprinciper aktivera inställningen **Tillåt att appen överför data endast till hanterade appar**. Med funktionen **Öppna i hantering** kan du kontrollera dataöverföringen mellan appar som distribueras via Intune.   

-   **Enheter som hanteras av en tredje parts MDM-lösning:** Du kan begränsa dataöverföringen till endast hanterade appar med hjälp av iOS-funktionen **Öppna i hantering**.
För att säkerställa att appar som du distribuerar med en tredje parts MDM-lösning också är associerade med appskyddsprinciper som du har konfigurerat i Intune, måste du konfigurera inställningen för UPN enligt beskrivningen i [Konfigurera UPN-inställningar](#configure-user-upn-setting).  När appar distribueras med inställningen för användar-UPN tillämpas appskyddsprinciperna när slutanvändaren loggar in med sitt arbetskonto.

> [!IMPORTANT]
> Inställningen för UPN krävs endast för appar som distribueras till enheter som hanteras av en tredje parts MDM.  Den här inställningen behövs inte för Intune-hanterade enheter.

## <a name="configure-user-upn-setting"></a>Konfigurera UPN-inställning
Den här konfigurationen krävs för enheter som hanteras av en tredje parts MDM-lösning. Nedan visas ett vanligt flöde för hur du implementerar UPN-inställningen och den resulterande användarupplevelsen:


1.  [Konfigurera en princip för hantering av mobila program](app-protection-policies.md) för iOS-plattformen i Azure Portal. Konfigurera principinställningar enligt företagets krav och välj de appar som ska ha principen.

2.  Distribuera de appar och e-postprofiler som du vill ska hanteras **via din tredje part MDM-lösning** med hjälp av inställningen som beskrivs i steg 3 och 4.

3.  Distribuera appen med följande appkonfigurationsinställningar: key=IntuneMAMUPN, Value=<username@company.com> [example: ‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Distribuera principen Öppna i hantering till registrerade enheter.

### <a name="example-end-user-experience"></a>Exempel på slutanvändarupplevelse

1.  Slutanvändaren installerar Microsoft Word-appen på enheten.

2.  Slutanvändaren startar den hanterade interna e-postappen för att komma åt sin e-post.

3.  Slutanvändaren försöker öppna dokumentet från den interna e-postappen i Microsoft Word.

4.  När Word startas ombeds slutanvändaren logga in med sitt arbetskonto.  Arbetskontot användaren anger när den uppmanas ange ett konto bör matcha kontot som du angav i konfigurationsinställningarna för Microsoft Word-app.

    > [!NOTE]
    > Slutanvändaren kan lägga till andra personliga konton till Word för att utföra sitt personliga arbete och inte påverkas av appskyddsprinciperna när de använder Word-appen i en personlig kontext.

5.  När inloggningen är klar tillämpas apprincipinställningarna för Word.

6.  Nu fungerar dataöverföringen och dokumentet märks med företagets ID i appen. Dessutom behandlas data i en arbetskontext och motsvarande principinställningar tillämpas.

### <a name="see-also"></a>Se även
[Vad är appskyddsprincip i Intune](what-is-app-protection-policy.md)



<!--HONumber=Feb17_HO1-->


