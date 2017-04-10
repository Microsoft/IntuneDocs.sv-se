---
title: "Hantera dataöverföring mellan iOS-appar | Microsoft Docs"
description: "I det här avsnittet beskrivs hur du kan hantera dataöverföringar mellan appar med funktionen Öppna med i iOS och hanteringsprinciper för mobilappar."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a4515c1-b325-4ac1-9f0a-45ac27e00681
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: c66226b7fc31f91669c4f4f0693ccbd7c679189f
ms.openlocfilehash: e71ebacec9d7b890b41e7650c8c50f42952c6326
ms.lasthandoff: 03/29/2017


---

# <a name="manage-data-transfer-between-ios-apps-with-microsoft-intune"></a>Hantera dataöverföring mellan iOS-appar med Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="manage-ios-apps"></a>Hantera iOS-appar
För att skydda företagets data måste du se till att filöverföringar begränsas till appar som hanteras av dig.  Du kan hantera iOS-appar på följande sätt:

-   Förhindra förlust av företagets data genom att konfigurera en appskyddsprincip, något som vi kommer att referera till som **principhanterade** appar.

-   Du kan också distribuera och hantera appar via **MDM-kanalen**.  Detta kräver att enheterna har registrerats i MDM-lösningen. Det kan vara **principhanterade** appar eller andra hanterade appar.

Med funktionen **Öppna i hantering** för iOS-enheter kan du begränsa överförandet av filer mellan appar som är distribuerade via **MDM-kanalen**. Begränsningar för funktionen anges i inställningarna för konfiguration och distribueras via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.

##  <a name="manage-data-transfer-between-ios-apps"></a>Hantera dataöverföring mellan iOS-appar
Appskyddsprinciper kan användas med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

-   **Personalägda enheter som inte hanteras av en MDM-lösning:** Du kan konfigurera [inställningar för appskyddsprinciper](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) med **Tillåt endast att appen överför data till hanterade appar**. När slutanvändaren öppnar en skyddad fil i en app som inte är principhanterad går det inte att läsa filen.

-   **Enheter som hanteras av Intune:** Enheter som registreras i Intune tillåts automatiskt att överföra data mellan appar med appskyddsprinciper och andra hanterade iOS-appar som distribueras via Intune. För att tillåta överföring av data mellan appar med appskyddsprinciper aktivera inställningen **Tillåt att appen överför data endast till hanterade appar**. Med funktionen **Öppna i hantering** kan du kontrollera dataöverföringen mellan appar som distribueras via Intune.   

-   **Enheter som hanteras av en tredje parts MDM-lösning:** Du kan begränsa dataöverföringen till endast hanterade appar med hjälp av iOS-funktionen **Öppna i hantering**.
För att säkerställa att appar som du distribuerar med en tredje parts MDM-lösning också är associerade med appskyddsprinciper som du har konfigurerat i Intune, måste du konfigurera inställningen för UPN enligt beskrivningen i [Konfigurera UPN-inställningar](#configure-user-upn-setting-for-third-party-emm).  När appar distribueras med inställningen för användar-UPN tillämpas appskyddsprinciperna när slutanvändaren loggar in med sitt arbetskonto.

> [!IMPORTANT]
> Inställningen för UPN krävs endast för appar som distribueras till enheter som hanteras av en tredje parts MDM.  Den här inställningen behövs inte för Intune-hanterade enheter.

## <a name="configure-user-upn-setting-for-third-party-emm"></a>Konfigurera inställningen för användar-UPN för en EMM-lösning från tredje part
Inställningen för användar-UPN **måste** konfigureras för enheter som hanteras av en EMM-lösning från tredje part. Proceduren nedan beskriver de allmänna steg du följer för att konfigurera UPN-inställningen samt den resulterande användarupplevelsen:


1.  [Konfigurera en appskyddsprincip](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för iOS-plattformen på Azure-portalen. Konfigurera principinställningar enligt företagets krav och välj de appar som ska ha principen.

2.  Distribuera apparna och den e-postprofil som ska hanteras **via MDM-lösningen från tredje part** genom att följa de allmänna stegen nedan. Se även Exempel 1.

  1.  Distribuera appen med följande appkonfigurationsinställningar:

      **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

      Exempel: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

  2.  Distribuera principen Öppna i hantering med hjälp av din MDM-lösning från tredje part till registrerade enheter.


### <a name="example-1-admin-experience-in-third-party-mdm-console"></a>Exempel 1: Administratörsmiljön i MDM-konsol från tredje part

1. Gå till administratörskonsolen för din MDM-lösning från tredje part. Gå till det avsnitt i konsolen där du kan distribuera inställningar för programkonfiguration till registrerade iOS-enheter.

2. Ange följande inställning i avsnittet för programkonfiguration:

  **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

  Den exakta syntaxen för nyckel/värde-paret kan variera beroende på MDM-lösning. Tabellen nedan innehåller exempel på tredjepartsleverantörer av MDM-lösningar och de exakta värden som du anger för nyckel/värde-paret.

|MDM-tredjepartsleverantör| Konfigurationsnyckel | Värdetyp | Konfigurationsvärde|
| ------- | ---- | ---- | ---- |
| VMware AirWatch | IntuneMAMUPN | Sträng | {UserPrincipalName}|
| MobileIron Core | IntuneMAMUPN | Sträng | $EMAIL$ **eller** $USER_UPN$ |
| MobileIron Cloud | IntuneMAMUPN | Sträng | ${userUPN} **eller** ${userEmailAddress} |

### <a name="example-2-end-user-experience"></a>Exempel 2: Slutanvändarupplevelse

1.  Slutanvändaren installerar Microsoft Word-appen på enheten.

2.  Slutanvändaren startar den hanterade interna e-postappen för att komma åt sin e-post.

3.  Slutanvändaren försöker öppna dokumentet från den interna e-postappen i Microsoft Word.

4.  När Word startas ombeds slutanvändaren logga in med sitt arbetskonto.  Arbetskontot användaren anger när den uppmanas ange ett konto bör matcha kontot som du angav i konfigurationsinställningarna för Microsoft Word-app.

    > [!NOTE]
    > Slutanvändaren kan lägga till andra personliga konton till Word för att utföra sitt personliga arbete och inte påverkas av appskyddsprinciperna när de använder Word-appen i en personlig kontext.

5.  När inloggningen är klar tillämpas inställningarna för appskyddsprinciperna för Word-appen.

6.  Nu har filöverföringen slutförts och dokumentet märkts med företagets ID i appen. Dessutom behandlas filen i en arbetskontext och motsvarande principinställningar tillämpas.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Verifiera inställningen för användar-UPN för en EMM-lösning från tredje part

När du har konfigurerat inställningen för användar-UPN kontrollerar du att iOS-appen kan ta emot och följa Intunes appskyddsprincip.

Det är till exempel enkelt att visuellt testa principinställningen **Require app PIN** (Kräv PIN-kod för app) på en enhet. Om den här inställningen är **Ja** uppmanas användaren att skapa eller ange en PIN-kod när han heller hon försöker komma åt företagsdata.

Börja med att [skapa och distribuera en appskyddsprincip](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) till iOS-appen. Mer information om hur du testar appskyddsprinciper finns i [Verifiera appskyddsprinciper](validate-mobile-application-management.md).



### <a name="see-also"></a>Se även
[Skydda appdata med hjälp av appskyddsprinciper med Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

