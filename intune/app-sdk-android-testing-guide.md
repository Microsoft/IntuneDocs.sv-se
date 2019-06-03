---
title: Testningsguide om Microsoft Intune-appens SDK för Android-utvecklare
description: Testningsguiden för Microsoft Intune App SDK för Android hjälper dig att testa din Intune-hanterade Android-app.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f8fa8f361e886c8eac697bb585ccf15eb9152f1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043847"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Testningsguide om Microsoft Intune-appens SDK för Android-utvecklare

Testningsguiden för Microsoft Intune App SDK för Android är utformat för att hjälpa dig att testa din Intune-hanterade Android-app.  

## <a name="prerequisite-test-accounts"></a>Nödvändiga testkonton
Nya konton kan skapas med och utan förgenererade data. Så här skapar du ett nytt konto:
1. Gå till webbplatsen för [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant). 
2. [Konfigurera Intune](https://docs.microsoft.com/intune/setup-steps) för att aktivera hantering av mobilenheter (MDM).
3. [Skapa användare](https://docs.microsoft.com/intune/users-add).
4. [Skapa grupper](https://docs.microsoft.com/intune/groups-add).
5. [Tilldela licenser](https://docs.microsoft.com/intune/licenses-assign) som passar din testning.


## <a name="azure-portal-policy-configuration"></a>Konfiguration av Azure-portalprinciper
[Skapa och tilldela appskyddsprinciper](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview) på [Azure-portalens Intune-blad](https://docs.microsoft.com/intune/app-protection-policies). Din [appkonfigurationsprincip](https://docs.microsoft.com/intune/app-configuration-policies-overview) kan också skapas och tilldelas på Intune-bladet.

> [!NOTE]
> Om din app inte visas i Azure-portalen kan du ange den som mål med en princip genom att välja alternativet **fler appar** och ange paketets namn i textrutan.

> [!IMPORTANT]
> För att en appkonfigurationsprincip ska gälla måste den registrerande användaren anges som mål av en [Intune-appskyddsprincip](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Testfall

Följande testfall innehåller steg för konfiguration och bekräftelse. Använd den här vägledningen för att felsöka problem med Intune-hanterade Android-appar.

### <a name="required-pin-and-corporate-credentials"></a>Nödvändig PIN-kod och företagets autentiseringsuppgifter

Du kan kräva en PIN-kod för åtkomst till företagsresurser. Du kan även tillämpa företagsautentisering innan användare kan använda hanterade appar. Använd följande steg för att ange dessa krav:

1. Konfigurera **Kräv PIN-kod för åtkomst** och **Kräv företagsautentiseringsuppgifter för åtkomst** till **Ja**. Mer information finns i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Bekräfta följande villkor:
    - Appstart bör visa en uppmaning för PIN-kodsinmatning/konfiguration och/eller den produktionsanvändare som användes vid registrering med företagsportalen.
    - Om en giltig inloggningsuppmaning inte visas kan det bero på ett felaktigt konfigurerade Android-manifest, specifikt värdena för ADAL-integrering (SkipBroker, ClientID och Authority).
    - Om ingen uppmaning visas alls kan det bero på ett felaktigt integrerat `MAMActivity`-värde. Mer information om `MAMActivity` finns i [utvecklarhandboken för Microsoft Intune App SDK för Android](app-sdk-android.md).

> [!NOTE] 
> Om testet ovan inte fungerar är det troligt att även testerna nedan misslyckas. Granska [SDK](app-sdk-android.md##sdk-integration)- och [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)-integrering.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Begränsa överföring och mottagande av data med andra appar
Du kan styra dataöverföring mellan företagshanterade program på följande sätt:

1. Ange **Tillåt att appen överför data till andra appar** till **Principhanterade appar**.
2. Ange **Tillåt att appen tar emot data från andra appar** till **Alla appar**. Användning av avsikter och innehållsprovidrar påverkas av dessa principer.
3. Bekräfta följande villkor:
    - Att öppna från en ohanterad app till din app fungerar korrekt.
    - Delning av innehåll mellan hanterade appar tillåts.
    - Delning från hanterade appar till icke-hanterade program (till exempel Chrome) blockeras.

### <a name="restrict-cut-copy-and-paste"></a>Begränsa klipp ut, kopiera och klistra in
Du kan begränsa systemets Urklipp till hanterade program på följande sätt:

1. Ange **Begränsa klipp ut, kopiera och klistra in med andra appar** till **Principhanterade appar med inklistring**.
2. Bekräfta följande villkor:
    - Kopiering av text från din app till en ohanterad app (till exempel Meddelanden) blockeras.

### <a name="prevent-save-as"></a>Förhindra **Spara som**
Du kan styra funktionalitet för **Spara som** på följande sätt:

1. Om din app kräver [integrerade ”Spara som”-kontroller](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted) anger du **Förhindra ”Spara som”** till **Ja**.
2. Bekräfta följande villkor:
    - Spara begränsas till att endast gälla för lämpliga hanterade platser.

### <a name="file-encryption"></a>Filkryptering
Du kan kryptera data på enheten på följande sätt:

1. Ange **Kryptera appdata** till **Ja**.
2. Bekräfta följande villkor:
    - Normalt programbeteende påverkas inte.

### <a name="prevent-android-backups"></a>Förhindra Android-säkerhetskopieringar
Du kan styra appsäkerhetskopiering på följande sätt:

1. Om du har angett [begränsningar för integrerad säkerhetskopiering](app-sdk-android.md#protecting-backup-data) konfigurerar du **Förhindra Android-säkerhetskopieringar** till **Ja**.
2. Bekräfta följande villkor:
    - Säkerhetskopior begränsas.

### <a name="unenrollment"></a>Avregistrering
Du kan fjärrensa hanterade appar från att innehålla företags-e-post, och dokument och personliga data dekrypteras när de inte längre administreras på följande sätt:

1. Från Azure-portalen [utför du en rensning](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Om appen inte registreras för några rensningshanterare bekräftar du följande villkor:
    - En fullständig rensning av appen sker.
3. Om appen har registrerats för `WIPE_USER_DATA` eller `WIPE_USER_AUXILARY_DATA` bekräftar du följande villkor:
    - Det hanterade innehållet tas bort från appen. Mer information finns i [utvecklarhandboken för Intune App SDK för Android – selektiv rensning](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Flera identiteter
Integrering av [stöd för flera identiteter](app-sdk-android.md#multi-identity-optional) är en ändring med hög risk som behöver testas ordentligt. De vanligaste problemen beror på felaktig inställning av identiteten (kontext kontra hotnivå) och även filspårning (`MAMFileProtectionManager`).

Som minst bör följande scenarier för flera identiteter omvalideras:

- **Spara som**-principen fungerar korrekt för hanterade identiteter.
- Begränsningar för Kopiera/Klistra in framtvingas korrekt från hanterat till personligt.
- Endast data som tillhör den hanterade identitet krypteras, och personliga filer ändras inte.
- Selektiv rensning vid avregistrering tar endast bort data för hanterad identitet.
- Slutanvändaren uppmanas att ange villkorlig start vid växling från ohanterat till hanterat konto (endast första gången).

### <a name="app-configuration-optional"></a>Appkonfiguration (valfritt)
Du kan konfigurera beteendet för hanterade appar på följande sätt:

1. Om din app förbrukar några inställningar för appkonfiguration bör du testa att appen korrekt hanterar alla värden som du (i egenskap av administratör) kan ange. [Appkonfigurationsprinciper](https://docs.microsoft.com/intune/app-configuration-policies-overview) kan skapas och tilldelas med hjälp av Intune.

## <a name="next-steps"></a>Nästa steg

- [Lägg till en verksamhetsspecifik app för Android i Microsoft Intune](lob-apps-android.md).
