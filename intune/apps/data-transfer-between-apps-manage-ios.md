---
title: Hantera dataöverföring mellan iOS-appar
titleSuffix: Microsoft Intune
description: Läs om hur du använder principer för hantering av mobilappar i Microsoft Intune för att hantera dataöverföringar mellan appar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a1ba4a5e6096f77c87560554fd2c9cd601a33e4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511726"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Hantera dataöverföring mellan iOS-appar med Microsoft Intune

För att skydda företagets data bör du begränsa överförandet av filer till de appar som du hanterar. Du kan hantera iOS-appar på följande sätt:

- Skydda organisationsdata för arbets- eller skolkonton genom att konfigurera en appskyddsprincip för apparna. som vi kallar för *principhanterade appar*.  Se [alla Intune-hanterade appar som du kan hantera med appskyddsprinciper](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Distribuera och hantera apparna via iOS-enhetshantering, vilket kräver att enheterna registreras i en MDM-lösning (Mobile Device Management). De appar som du distribuerar kan vara *principhanterade* appar eller andra iOS-hanterade appar.

Funktionen **Öppna i hantering** för registrerade iOS-enheter kan begränsa filöverföringar mellan iOS-hanterade appar. Ange begränsningar för funktionen *Öppna i hantering* i konfigurationsinställningarna och distribuera dem sedan via din MDM-lösning.  Begränsningarna du angett tillämpas när användaren installerar den distribuerade appen.

## <a name="use-app-protection-with-ios-apps"></a>Använda appskydd med iOS-appar
Använd appskyddsprinciper med iOS-funktionen **Öppna i hantering** för att skydda företagets data på följande sätt:

- **Enheter som inte hanteras av en MDM-lösning:** Du kan ange inställningarna för appskyddsprinciper för att styra delning av data med andra program via tilläggen *Öppna i* eller *Dela*.  För att göra det konfigurerar du inställningen **Skicka organisationsdata till annan app** med värdet **Principhanterade appar med Öppna i/Dela-filtrering**.  Beteendet *Öppna i/Dela* i den *principhanterade appen* presenterar bara andra *principhanterade appar* som alternativ för delning. 

- **Enheter som hanteras av en MDM-lösning**: För enheter som registrerats i Intune eller tredje parts MDM-lösningar styrs datadelning mellan appar med appskyddsprinciper och andra hanterade iOS-appar som distribuerats via MDM av principer för Intune APP och iOS-funktionen **Open in management**. För att säkerställa att appar som du distribuerar med en MDM-lösningockså är associerade med dina Intune-appskyddsprinciper måste du konfigurera användarinställningen för UPN enligt beskrivningen i följande avsnitt: [Konfigurera användarinställningar för UPN](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Om du vill ange hur dataöverföring till andra appar ska tillåtas så aktiverar du inställningen **Skicka organisationsdata till andra appar** och väljer önskad nivå för delningen. Om du vill ange hur en app ska ta emot data från andra appar så aktiverar du inställningen **Ta emot data från andra appar** och väljer önskad nivå för datamottagning. Mer information om hur du tar emot och delar appdata finns i [Inställningar för dataflytt](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Konfigurera inställningen för användar-UPN för Microsoft Intune eller en EMM-lösning från tredje part
Inställningen för användar-UPN **måste** konfigureras för enheter som hanteras av Intune eller en EMM-lösning från tredje part för att identifiera det registrerade användarkontot. UPN-konfigurationen används med de appskyddsprinciper som du distribuerar från Intune. Proceduren nedan beskriver det allmänna flödet för att konfigurera UPN-inställningen, samt den resulterande användarupplevelsen:

1. [Skapa och tilldela en appskyddsprincip](app-protection-policies.md) för iOS/iPadOS i [Azure Portal](https://portal.azure.com). Konfigurera principinställningar enligt företagets krav och välj de iOS-appar som ska ha principen.

2. Distribuera de appar och den e-postprofil som ska hanteras via Intune, eller MDM-lösningen från tredje part, genom att följa de allmänna stegen nedan. Se även *Exempel 1*.

3. Distribuera appen med följande inställningar för appkonfiguration till den hanterade enheten:

      **nyckel** = IntuneMAMUPN, **värde** = <username@company.com>

      Exempel: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > I Intune måste principen för App Configuration vara för registreringstypen **Hanterade enheter**.
     > Dessutom behöver appen antingen installeras från Intune-företagsportalen om den har angetts som tillgänglig eller push-överföras till enheten vid behov. 

4. Distribuera principen **Öppna i hantering** med hjälp av Intune eller MDM-lösningen från tredje part till registrerade enheter.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exempel 1: Administratörsmiljön i Intune eller MDM-konsolen från tredje part

1. Gå till administratörskonsolen i Intune eller MDM-lösningen från tredje part. Gå till det avsnitt i konsolen där du kan distribuera inställningar för programkonfiguration till registrerade iOS-enheter.

2. Ange följande inställning i avsnittet för programkonfiguration:

   **nyckel** = IntuneMAMUPN, **värde** = <username@company.com>

   Den exakta syntaxen för nyckel/värde-paret kan variera beroende på MDM-lösning. I följande tabell finns exempel på tredjepartsleverantörer av MDM-lösningar och de exakta värden som du bör ange för nyckel/värde-paret.

   |MDM-tredjepartsleverantör| Konfigurationsnyckel | Värdetyp | Konfigurationsvärde|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Sträng | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Sträng | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Sträng | ${userUPN} **eller** ${userEmailAddress} |
   |Hantering av Citrix-slutpunkt | IntuneMAMUPN | Sträng | ${user.userprincipalname} |
   |ManageEngine Mobile Device Manager | IntuneMAMUPN | Sträng | %upn% |

> [!NOTE]  
> Om du distribuerar en appkonfigurationsprincip för hanterade enheter i Outlook för iOS/iPadOS med alternativet ”Använda konfigurationsdesigner” och aktiverar **Tillåt endast arbets- eller skolkonton** konfigureras konfigurationsnyckeln IntuneMAMUPN automatiskt i bakgrunden för principen. Mer information finns i vanliga frågor och svar för [Ny appkonfigurationsprincip för Outlook för iOS och Android – allmän appkonfiguration](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>Exempel 2: Upplevelse för slutanvändaren

*Delning från en* priniciphanterad app *till andra program med OS-delning*

1. En användare öppnar Microsoft OneDrive-appen på en registrerad iOS-enhet och loggar in på deras arbetskonto.  Det konto som användaren anger måste matcha kontots användarhuvudnamn som du angav i appkonfigurationsinställningarna för Microsoft OneDrive-appen.

2. Efter inloggningen gäller dina administratörskonfigurerade APP-inställningar för användarkontot i Microsoft OneDrive.  Det här inkluderar att konfigurera inställningen **Skicka organisationsdata till andra appar** med värdet **Principhanterade appar med operativsystemdelning**.

3. Användaren förhandsgranskar en arbetsfil och försöker dela via Öppna i till iOS-hanterad app.  

4. Dataöverföringen utförs och data skyddas nu av **Öppna i hantering** i den iOS-hanterade appen.  Intunes appskyddsprincip gäller inte för program som inte är *principhanterade appar*.

*Delning från en* iOS-hanterad app *till en* principhanterad app *med inkommande organisationsdata*

1. En användare öppnar det inbyggda E-post på en registrerad iOS-enhet med en hanterad e-postprofil.  

1. Användaren öppnar ett bifogat arbetsdokument från det inbyggda E-post i Microsoft Word.

1. När Word-appen startar sker någon av följande två funktioner:
   1. Data skyddas med Intunes appskyddsprincip när:
      - Användaren loggas in på det arbetskonto som matchar kontots användarhuvudnamn du har angett i appkonfigurationsinställningarna för Microsoft Word-appen. 
      - Dina administratörskonfigurerade APP-inställningar gäller för användarkontot i Microsoft Word.  Detta omfattar att konfigurera **Ta emot data från andra appar** med värdet **Alla appar med inkommande organisationsdata**.
      - Dataöverföringen utförs och dokumentet märks med ett arbetsidentiteten i appen.  Intunes appskyddsprincip skyddar användaråtgärderna för dokumentet.
   1. Data skyddas **inte** med Intunes appskyddsprincip när:
      - Användaren loggas **inte** in på arbetskontot.
      - Dina administratörskonfigurerade inställningar tillämpas **inte** för Microsoft Word eftersom användaren inte är inloggad.
      - Dataöverföringen utförs och dokumentet märks **inte** med ett arbetsidentiteten i appen.  Intunes appskyddsprincip skyddar **inte** användaråtgärderna för dokumentet eftersom den inte är aktiv.

    > [!NOTE]
    > Användaren kan lägga till och använda sina personliga konton med Word. Appskyddsprinciperna tillämpas inte när användaren använder Word utanför arbetet. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Verifiera inställningen för användar-UPN för en EMM-lösning från tredje part

När du har konfigurerat användarinställningen för UPN kontrollerar du att iOS-appen kan ta emot och följa Intunes appskyddsprincip.

Det är till exempel enkelt att testa principinställningen **Kräv PIN-kod för appen**. Om den här principinställningen är **Kräv** uppmanas användarna att skapa eller ange en PIN-kod innan de får åtkomst till företagsdata.

Börja med att [skapa och tilldela en appskyddsprincip](app-protection-policies.md) till iOS-appen. Mer information om hur du testar appskyddsprinciper finns i [Verifiera appskyddsprinciper](app-protection-policies-validate.md).


## <a name="see-also"></a>Se även
[Vad är appskyddsprincip i Intune](app-protection-policy.md)
