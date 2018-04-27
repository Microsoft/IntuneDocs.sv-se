---
title: Hantera dataöverföring mellan iOS-appar
titlesuffix: Microsoft Intune
description: Läs om hur du använder principer för hantering av mobilappar i Microsoft Intune för att hantera dataöverföringar mellan appar.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecf3791a7b01a9214c95680816a0fae16aade8f2
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Hantera dataöverföring mellan iOS-appar med Microsoft Intune
## <a name="manage-ios-apps"></a>Hantera iOS-appar
För att skydda företagets data måste du se till att filöverföringar begränsas till appar som hanteras av dig.  Du kan hantera iOS-appar på följande sätt:

-   Förhindra förlust av företagets data genom att konfigurera en appskyddsprincip, något som vi kommer att referera till som **principhanterade** appar. Se [alla Intune-hanterade appar som du kan hantera med appskyddsprinciper](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Du kan också distribuera och hantera appar via **MDM-kanalen**.  Detta kräver att enheterna har registrerats i MDM-lösningen. Det kan vara **principhanterade** appar eller andra hanterade appar.

Med funktionen **Öppna i hantering** för iOS-enheter kan du begränsa överförandet av filer mellan appar som är distribuerade via **MDM-kanalen**. Begränsningar för funktionen anges i inställningarna för konfiguration och distribueras via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.

##  <a name="using-app-protection-with-ios-apps"></a>Använda appskydd med iOS-appar
Appskyddsprinciper kan användas med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

-   **Medarbetarägda enheter som inte hanteras av en MDM-lösning:** Du kan konfigurera inställningarna för appskyddsprincipen med **Tillåt endast att appen överför data till principhanterade appar**. Beteendet öppna-i för en principhanterad app, visar enbart andra principhanterade appar som alternativ för delning. Om en användare försöker skicka en principskyddad fil som en bilaga från OneDrive i den inbyggda e-postappen, kommer filen att vara oläslig.

-   **Enheter som hanteras av Intune:** Enheter som registreras i Intune tillåts automatiskt att överföra data mellan appar med appskyddsprinciper och andra hanterade iOS-appar som distribueras via Intune. För att tillåta överföring av data mellan appar med appskyddsprinciper aktivera inställningen **Tillåt att appen överför data endast till hanterade appar**. Med funktionen **Öppna i hantering** kan du kontrollera dataöverföringen mellan appar som distribueras via Intune.   

-   **Enheter som hanteras av en tredje parts MDM-lösning:** Du kan begränsa dataöverföringen till endast hanterade appar med hjälp av iOS-funktionen **Öppna i hantering**.
För att säkerställa att appar som du distribuerar med en tredje parts MDM-lösning också är associerade med appskyddsprinciper som du har konfigurerat i Intune, måste du konfigurera inställningen för UPN enligt beskrivningen i [Konfigurera UPN-inställningar](#configure-user-upn-setting-for-third-party-emm).  När appar distribueras med inställningen för användar-UPN tillämpas appskyddsprinciperna när slutanvändaren loggar in med sitt arbetskonto.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurera inställningen för användar-UPN för Microsoft Intune eller en EMM-lösning från tredje part
Inställningen för användar-UPN **måste** konfigureras för enheter som hanteras av Intune eller en EMM-lösning från tredje part. Proceduren nedan beskriver de allmänna steg du följer för att konfigurera UPN-inställningen samt den resulterande användarupplevelsen:

1.  [Skapa och tilldela en appskyddsprincip](app-protection-policies.md) för iOS på [Azure Portal](https://portal.azure.com). Konfigurera principinställningar enligt företagets krav och välj de iOS-appar som ska ha principen.

2.  Distribuera apparna och den e-postprofil som ska hanteras via Intune eller MDM-lösningen från tredje part genom att följa de allmänna stegen nedan. Se även Exempel 1.

3.  Distribuera appen med följande appkonfigurationsinställningar:

      **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

      Exempel: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Distribuera principen **Öppna i hantering** med hjälp av Intune eller MDM-lösningen från tredje part till registrerade enheter.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exempel 1: Administratörsmiljön i Intune eller MDM-konsolen från tredje part

1. Gå till administratörskonsolen i Intune eller MDM-lösningen från tredje part. Gå till det avsnitt i konsolen där du kan distribuera inställningar för programkonfiguration till registrerade iOS-enheter.

2. Ange följande inställning i avsnittet för programkonfiguration:

   **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

   Den exakta syntaxen för nyckel/värde-paret kan variera beroende på MDM-lösning. Tabellen nedan innehåller exempel på tredjepartsleverantörer av MDM-lösningar och de exakta värden som du anger för nyckel/värde-paret.

|MDM-tredjepartsleverantör| Konfigurationsnyckel | Värdetyp | Konfigurationsvärde|
| ------- | ---- | ---- | ---- |
|Microsoft Intune| IntuneMAMUPN | Sträng | {UserPrincipalName}|
|VMware AirWatch| IntuneMAMUPN | Sträng | {UserPrincipalName}|
|MobileIron | IntuneMAMUPN | Sträng | ${userUPN} **eller** ${userEmailAddress} |


### <a name="example-2-end-user-experience"></a>Exempel 2: Slutanvändarupplevelse

1.  Slutanvändaren installerar Microsoft Word-appen på enheten.

2.  Slutanvändaren startar den hanterade interna e-postappen för att komma åt sin e-post.

3.  Slutanvändaren försöker öppna dokumentet från den interna e-postappen i Microsoft Word.

4.  När Word startas ombeds slutanvändaren logga in med sitt arbetskonto.  Arbetskontot användaren anger när den uppmanas ange ett konto bör matcha kontot som du angav i konfigurationsinställningarna för Microsoft Word-app.

    > [!NOTE]
    > Slutanvändaren kan lägga till andra personliga konton till Word för att utföra sitt personliga arbete och inte påverkas av appskyddsprinciperna när de använder Word-appen i en personlig kontext.

5.  När inloggningen är klar tillämpas inställningarna för appskyddsprinciperna för Word-appen.

6.  Nu fungerar dataöverföringen och dokumentet märks med ett företags-ID i appen. Dessutom behandlas data i en arbetskontext och motsvarande principinställningar tillämpas.

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Verifiera inställningen för användar-UPN för en EMM-lösning från tredje part

När du har konfigurerat inställningen för användar-UPN kontrollerar du att iOS-appen kan ta emot och följa Intunes appskyddsprincip.

Det är till exempel enkelt att visuellt testa principinställningen **Require app PIN** (Kräv PIN-kod för app) på en enhet. Om den här inställningen är **Ja** uppmanas användaren att skapa eller ange en PIN-kod när han heller hon försöker komma åt företagsdata.

Börja med att [skapa och tilldela en appskyddsprincip](app-protection-policies.md) till iOS-appen. Mer information om hur du testar appskyddsprinciper finns i [Verifiera appskyddsprinciper](app-protection-policies-validate.md).


### <a name="see-also"></a>Se även
[Vad är appskyddsprincip i Intune](app-protection-policy.md)
