---
title: Hantera dataöverföring mellan iOS-appar
titlesuffix: Microsoft Intune
description: Läs om hur du använder principer för hantering av mobilappar i Microsoft Intune för att hantera dataöverföringar mellan appar.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d5a2bc0939da5ee4cb35585a930f145b832a58ad
ms.sourcegitcommit: 0dbce0415e53fe963dc7f927ac4b0c06411f199c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2018
ms.locfileid: "52281113"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Hantera dataöverföring mellan iOS-appar med Microsoft Intune

För att skydda företagets data bör du begränsa överförandet av filer till de appar som du hanterar. Du kan hantera iOS-appar på följande sätt:

-   Förhindra förlust av företagets data genom att konfigurera en appskyddsprincip, något som vi kallar **principhanterade** appar. Se [alla Intune-hanterade appar som du kan hantera med appskyddsprinciper](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Distribuera och hantera appar med hjälp av **MDM-kanalen**, vilket kräver att enheterna registreras i en MDM-lösning (Mobile Device Management). De appar som du distribuerar kan vara **principhanterade** appar eller andra hanterade appar.

Med funktionen **Öppna i hantering** för iOS-enheter kan du begränsa överförandet av filer mellan appar som är distribuerade via **MDM-kanalen**. Ange begränsningar för funktionen *Öppna i hantering* i konfigurationsinställningarna och distribuera dem sedan via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.

##  <a name="use-app-protection-with-ios-apps"></a>Använda appskydd med iOS-appar
Använd appskyddsprinciper med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

-   **Medarbetarägda enheter som inte hanteras av en MDM-lösning:** Du kan konfigurera inställningarna för appskyddsprincipen med **Tillåt endast att appen överför data till principhanterade appar**. Beteendet *Öppna-i* för en principhanterad app visar enbart andra principhanterade appar som alternativ för delning. Om en användare försöker skicka en principskyddad fil som en bilaga från OneDrive i den inbyggda e-postappen kommer det inte gå att läsa filen.

-   **Enheter som hanteras av Intune:** Enheter som registreras i Intune tillåts automatiskt att överföra data mellan appar med appskyddsprinciper och andra hanterade iOS-appar som distribueras via Intune. Om du vill ange hur dataöverföring till andra appar ska tillåtas så aktiverar du inställningen **Tillåt att appen överför data till andra appar** och väljer önskad nivå för delningen. Om du vill ange hur en app ska ta emot data från andra appar så aktiverar du inställningen **Tillåt att appen tar emot data från andra appar** och väljer önskad nivå för datamottagning. Med funktionen **Öppna i hantering** kan du kontrollera dataöverföringen mellan appar som distribueras via Intune. Mer information om hur du tar emot och delar appdata finns i [Inställningar för dataflytt](app-protection-policy-settings-ios.md#data-relocation-settings).   

-   **Enheter som hanteras av en MDM-lösning från tredje part:** Du kan begränsa dataöverföringen till endast hanterade appar med hjälp av iOS-funktionen **Öppna i hantering**.
För att säkerställa att appar som du distribuerar med en MDM-lösning från tredje part också är associerade med dina Intune-appskyddsprinciper måste du konfigurera användarinställningen för UPN enligt beskrivningen i följande avsnitt: [Konfigurera användarinställningar för UPN](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). När appar distribueras med användarinställningen för UPN så tillämpas appskyddsprinciperna på appen när användaren loggar in med sitt arbetskonto.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurera inställningen för användar-UPN för Microsoft Intune eller en EMM-lösning från tredje part
Inställningen för användar-UPN **måste** konfigureras för enheter som hanteras av Intune eller en EMM-lösning från tredje part. UPN-konfigurationen används med de appskyddsprinciper som du distribuerar från Intune. Proceduren nedan beskriver det allmänna flödet för att konfigurera UPN-inställningen, samt den resulterande användarupplevelsen:

1.  [Skapa och tilldela en appskyddsprincip](app-protection-policies.md) för iOS på [Azure Portal](https://portal.azure.com). Konfigurera principinställningar enligt företagets krav och välj de iOS-appar som ska ha principen.

2.  Distribuera de appar och den e-postprofil som ska hanteras via Intune, eller MDM-lösningen från tredje part, genom att följa de allmänna stegen nedan. Se även *Exempel 1*.

3.  Distribuera appen med följande appkonfigurationsinställningar:

      **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

      Exempel: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]

4.  Distribuera principen **Öppna i hantering** med hjälp av Intune eller MDM-lösningen från tredje part till registrerade enheter.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exempel 1: Administratörsmiljön i Intune eller MDM-konsolen från tredje part

1. Gå till administratörskonsolen i Intune eller MDM-lösningen från tredje part. Gå till det avsnitt i konsolen där du kan distribuera inställningar för programkonfiguration till registrerade iOS-enheter.

2. Ange följande inställning i avsnittet för programkonfiguration:

   **nyckel** = IntuneMAMUPN,  **värde** = <username@company.com>

   Den exakta syntaxen för nyckel/värde-paret kan variera beroende på MDM-lösning. I följande tabell finns exempel på tredjepartsleverantörer av MDM-lösningar och de exakta värden som du bör ange för nyckel/värde-paret.

   |MDM-tredjepartsleverantör| Konfigurationsnyckel | Värdetyp | Konfigurationsvärde|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Sträng | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Sträng | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Sträng | ${userUPN} **eller** ${userEmailAddress} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Sträng | %upn% |


### <a name="example-2-end-user-experience"></a>Exempel 2: Slutanvändarupplevelse

1.  En användare installerar Microsoft Word-appen på en enhet.

2.  Användaren startar den hanterade interna e-postappen för att komma åt sin e-post.

3.  Användaren försöker öppna ett dokument från den interna e-postappen i Microsoft Word.

4.  När Word-appen startas ombeds användaren logga in med sitt arbetskonto. Det konto som användaren anger måste matcha kontot som du angav i appkonfigurationsinställningarna för Microsoft Word-appen.

    > [!NOTE]
    > Användaren kan lägga till och använda sina personliga konton med Word. Appskyddsprinciperna tillämpas inte när användaren använder Word utanför arbetet. 

5.  Efter inloggningen gäller inställningarna av appskyddsprinciperna för Word-appen.

6.  Nu fungerar dataöverföringen och dokumentet märks med ett företags-ID i appen.  Dina data behandlas i ett arbetssammanhang och principinställningarna tillämpas. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Verifiera inställningen för användar-UPN för en EMM-lösning från tredje part

När du har konfigurerat användarinställningen för UPN kontrollerar du att iOS-appen kan ta emot och följa Intunes appskyddsprincip.

Det är till exempel enkelt att testa principinställningen **Kräv PIN-kod för appen**. Om den här principinställningen är **Ja** uppmanas användarna att skapa eller ange en PIN-kod innan de får åtkomst till företagsdata.

Börja med att [skapa och tilldela en appskyddsprincip](app-protection-policies.md) till iOS-appen. Mer information om hur du testar appskyddsprinciper finns i [Verifiera appskyddsprinciper](app-protection-policies-validate.md).


### <a name="see-also"></a>Se även
[Vad är appskyddsprincip i Intune](app-protection-policy.md)
