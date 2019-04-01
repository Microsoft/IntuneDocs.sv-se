---
title: Testningsguide om Microsoft Intune-appens SDK för Android-utvecklare
description: Med Microsoft Intune App SDK för Android-testning guiden hjälper dig att testa din Intune-hanterade Android-app.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4203f424c395399cb0ed1e7472b006602aa0b210
ms.sourcegitcommit: db7a6b8fc9e82dae4f2111ca0b2d3c14e33658f9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072477"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Testningsguide om Microsoft Intune-appens SDK för Android-utvecklare

Med Microsoft Intune App SDK för Android-testning guiden är utformad för att testa din Intune-hanterade Android-app.  

## <a name="prerequisite-test-accounts"></a>Nödvändiga testkonton
Nya konton kan skapas med och utan förgenererade data. Skapa ett nytt konto:
1. Navigera till den [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant) plats. 
2. [Konfigurera Intune](https://docs.microsoft.com/intune/setup-steps) att aktivera hantering av mobilenheter (MDM).
3. [Skapa användare](https://docs.microsoft.com/intune/users-add).
4. [Skapa grupper](https://docs.microsoft.com/intune/groups-add).
5. [Tilldela licenser](https://docs.microsoft.com/intune/licenses-assign) som passar dina tester.


## <a name="azure-portal-policy-configuration"></a>Azure portal principkonfiguration
[Skapa och tilldela appskyddsprinciper](https://docs.microsoft.com/intune/app-protection-policies) i den [Intune-bladet i Azure portal](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Din [appkonfigurationsprincip](https://docs.microsoft.com/intune/app-configuration-policies-overview) också kan skapas och tilldelas i Intune-bladet.

> [!NOTE]
> Om din app inte visas i Azure-portalen kan du rikta den med en princip genom att välja den **fler appar** alternativet och ange paketets namn i textrutan.

> [!IMPORTANT]
> För en appkonfigurationsprincip att tillämpa registrera användaren vara mål för en [Intunes appskyddsprincip](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Testfall

Följande testfall innehåller steg för konfiguration och bekräftelse. Använd den här vägledningen för att felsöka problem med Intune-hanterade Android-app.

### <a name="required-pin-and-corporate-credentials"></a>Nödvändig PIN-kod och företagets autentiseringsuppgifter

Du kan kräva en PIN-kod för att få åtkomst till företagets resurser. Du kan också tillämpa företagets autentisering innan användarna kan använda hanterade appar. Använd följande steg för att ange dessa krav:

1. Konfigurera **Kräv PIN-kod för åtkomst** och **Kräv företagets autentiseringsuppgifter för åtkomst** till **Ja**. Mer information finns i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Bekräfta att följande villkor:
    - Appstart bör uppvisa en uppmaning för PIN-kod indata/konfiguration och/eller produktion användaren som användes vid registrering med Företagsportalen.
    - Underlåtenhet att tillhandahålla en giltig inloggningsuppmaning kan bero på ett felaktigt konfigurerade android manifest, särskilt värden för ADAL-integrering (SkipBroker, ClientID och behörighet).
    - Det gick inte att presentera prompten kan bero på ett felaktigt integrerad `MAMActivity` värde. Mer information om `MAMActivity`, se [Microsoft Intune App SDK för Android-utvecklarguiden](app-sdk-android.md).

> [!NOTE] 
> Om testet ovan inte fungerar, misslyckas sannolikt testerna nedan även. Granska [SDK](app-sdk-android.md##sdk-integration) och [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integrering.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Begränsa överföra och ta emot data med andra appar
Du kan styra dataöverföringen mellan företagets hanterade program på följande sätt:

1. Ange **Tillåt att appen överför data till andra appar** till **principhanterade appar**.
2. Ange **Tillåt att appen tar emot data från andra appar** till **Alla appar**. Användning av intents och innehållsleverantörer påverkas av dessa principer.
3. Bekräfta att följande villkor:
    - Öppna från en ohanterad app i dina app-funktioner på rätt sätt.
    - Dela innehåll mellan hanterade appar är tillåtet.
    - Delning från hanterade appar till icke-hanterade program (till exempel Chrome) är blockerad.

### <a name="restrict-cut-copy-and-paste"></a>Begränsa klipp ut, kopiera och klistra in
Du kan begränsa Urklipp till hanterade program på följande sätt:

1. Ange **begränsa klipp ut, kopiera och klistra in med andra appar** till **principhanterade med Klistra in**.
2. Bekräfta att följande villkor:
    - Kopierar text från din app till en hanterad är en ohanterad app (till exempel meddelanden) blockerad.

### <a name="prevent-save-as"></a>Förhindra **Spara som**
Du kan styra **Spara som** funktioner på följande sätt:

1. Om din app kräver [integrerad ”Spara som”-kontroller](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted)anger **förhindra Spara som** till **Ja**.
2. Bekräfta att följande villkor:
    - Spara är begränsad till lämpliga hanterade platser.

### <a name="file-encryption"></a>Filkryptering
Du kan kryptera data på enheten på följande sätt:

1. Ange **kryptera AppData** till **Ja**.
2. Bekräfta att följande villkor:
    - Normal programmets beteende påverkas inte.

### <a name="prevent-android-backups"></a>Förhindra Android-säkerhetskopieringar
Du kan kontrollera app-säkerhetskopiering på följande sätt:

1. Om du har angett [integrerad säkerhetskopiering begränsningar](app-sdk-android.md#protecting-backup-data), konfigurera **förhindra säkerhetskopiering av Android** till **Ja**.
2. Bekräfta att följande villkor:
    - Säkerhetskopior är begränsade.

### <a name="unenrollment"></a>Avregistrering
Du kan fjärrensa hanterade appar från som innehåller företagets e-post och dokument och personliga data dekrypteras när den administreras inte längre på följande sätt:

1. Från Azure-portalen [utfärda en rensning](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Om appen inte registreras för någon rensning hanterare Bekräfta följande villkor:
    - En fullständig rensning av appen inträffar.
3. Om din app har registrerat dig för `WIPE_USER_DATA` eller `WIPE_USER_AUXILARY_DATA`, bekräfta att följande villkor:
    - Hanterat innehåll tas bort från appen. Mer information finns i [Intune App SDK för Android-utvecklarguiden - selektiv rensning](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Flera identiteter
Integrera [stöd för flera identiteter](app-sdk-android.md#multi-identity-optional) ändras med hög risk som måste testas noggrant. De vanligaste problemen blir på grund av felaktig inställning av identiteten (kontext jämfört med hotnivån) och även spåra filer (`MAMFileProtectionManager`).

Minimalt följande scenarier för flera identiteter bör vara att verifiera om:

- **Spara som** principen fungerar korrekt för hanterade identiteter.
- Kopiera/Klistra in tillämpas korrekt begränsningar från hanterad till personliga.
- Endast de data som tillhör den hanterade identitet krypteras och personliga filer ändras inte.
- Selektiv rensning vid avregistrering tar endast bort data för hanterad identitet.
- Användaren uppmanas att ange villkorlig start när du byter från ohanterade till hanterade kontot (endast första gången).

### <a name="app-configuration-optional"></a>Konfiguration av (valfritt)
Du kan konfigurera beteendet för hanterade appar på följande sätt:

1. Om din app förbrukar alla konfigurationsinställningar för app, bör du testa att din app kan hantera alla värden som du (som administratör) kan ange. [Appkonfigurationsprinciper](https://docs.microsoft.com/intune/app-configuration-policies-overview) kan skapas och tilldelas i med hjälp av Intune.

## <a name="next-steps"></a>Nästa steg

- [Lägg till en verksamhetsspecifik app för Android i Microsoft Intune](lob-apps-android.md).
