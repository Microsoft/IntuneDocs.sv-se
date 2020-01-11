---
title: Android-testguide för Microsoft Intune App SDK
description: Testningsguiden för Microsoft Intune App SDK för Android hjälper dig att testa din Intune-hanterade Android-app.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d473d29536b4ffdcc221c8cf61c63725bae0fa2
ms.sourcegitcommit: 8d7406b75ef0d75cc2ed03b1a5e5f74ff10b98c0
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75653911"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Android-testguide för Microsoft Intune App SDK

Den här guiden hjälper utvecklare att testa sina Intune-hanterade Android-appar.  

## <a name="prerequisite-test-accounts"></a>Nödvändiga testkonton
Du kan skapa nya konton med eller utan data som skapats i förväg. Så här skapar du ett nytt konto:
1. Gå till webbplatsen för [Microsoft-demonstrationer ](https://demos.microsoft.com/environments/create/tenant). 
2. [Konfigurera Intune](../fundamentals/setup-steps.md) för att aktivera hantering av mobilenheter (MDM).
3. [Skapa användare](../fundamentals/users-add.md).
4. [Skapa grupper](../fundamentals/groups-add.md).
5. [Tilldela licenser](../fundamentals/licenses-assign.md) som passar din testning.


## <a name="azure-portal-policy-configuration"></a>Konfiguration av Azure-portalprinciper
[Skapa och tilldela appskyddsprinciper](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview) på [Azure-portalens Intune-blad](../apps/app-protection-policies.md). Du kan också skapa och tilldela din [konfigurations princip för appar](../apps/app-configuration-policies-overview.md) på Intune-bladet.

> [!NOTE]
> Om din app inte visas på Azure-portalen kan du ange den som mål med en princip genom att välja alternativet **fler appar** och ange paketnamnet i textrutan.

## <a name="test-cases"></a>Testfall

Följande testfall innehåller steg för konfiguration och bekräftelse. Använd den här vägledningen för att felsöka problem med Intune-hanterade Android-appar.

### <a name="required-pin-and-corporate-credentials"></a>Nödvändig PIN-kod och företagets autentiseringsuppgifter

Du kan kräva en PIN-kod för åtkomst till företagsresurser. Du kan även tillämpa företagsautentisering innan användare kan använda hanterade appar. Så här gör du:

1. Konfigurera **Kräv PIN-kod för åtkomst** och **Kräv företagsautentiseringsuppgifter för åtkomst** till **Ja**. Mer information finns i [Inställningar för Android-appskyddsprinciper i Microsoft Intune](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Bekräfta följande villkor:
    - När appen startar uppmanas du att ange en PIN-kod eller autentiseringsuppgifterna för produktionsanvändaren som användes vid registreringen med företagsportalen.
    - Om det inte finns någon giltig inloggnings varning kan det bero på ett felaktigt konfigurerat Android-manifest, särskilt värdena för ADAL-integration (Azure Active Directory Authentication Library) (SkipBroker, ClientID och Authority).
    - Om ingen uppmaning visas kan det bero på ett felaktigt integrerat `MAMActivity`-värde. Mer information om `MAMActivity` finns i [utvecklarhandboken för Microsoft Intune App SDK för Android](app-sdk-android.md).

> [!NOTE] 
> Om det föregående testet inte fungerar kommer följande test troligen också att Miss beta. Granska [SDK](app-sdk-android.md##sdk-integration)- och [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)-integrering.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Begränsa överföring och mottagande av data med andra appar
Du kan styra dataöverföringen mellan företagshanterade program på följande sätt:

1. Ange **Tillåt att appen överför data till andra appar** till **Principhanterade appar**.
2. Ange **Tillåt att appen tar emot data från andra appar** till **Alla appar**. Användningen av avsikter och innehållsleverantörer påverkas av dessa principer.
3. Bekräfta följande villkor:
    - Att öppna från en ohanterad app till din app fungerar korrekt.
    - Delning av innehåll mellan hanterade appar tillåts.
    - Delning från hanterade appar till icke-hanterade program (till exempel Chrome) blockeras.

### <a name="restrict-cut-copy-and-paste"></a>Begränsa klipp ut, kopiera och klistra in
Du kan begränsa systemets Urklipp till hanterade program på följande sätt:

1. Ange **Begränsa klipp ut, kopiera och klistra in med andra appar** till **Principhanterade appar med inklistring**.
2. Bekräfta följande villkor:
    - Kopiering av text från din app till en ohanterad app (till exempel Meddelanden) blockeras.

### <a name="prevent-save"></a>Förhindra Spara som
Du kan styra funktionen **Spara som** på följande sätt:

1. Om din app kräver [integrerade ”Spara som”-kontroller](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted) anger du **Förhindra ”Spara som”** till **Ja**.
2. Bekräfta följande villkor:
    - Spara begränsas till att endast gälla för lämpliga hanterade platser.

### <a name="file-encryption"></a>Filkryptering
Du kan kryptera data på enheten på följande sätt:

1. Ange **Kryptera appdata** till **Ja**.
2. Bekräfta följande villkor:
    - Normalt program beteende påverkas inte.

### <a name="prevent-android-backups"></a>Förhindra Android-säkerhetskopieringar
Du kan styra säkerhetskopieringen av appar på följande sätt:

1. Om du har angett [begränsningar för integrerad säkerhetskopiering](app-sdk-android.md#protecting-backup-data) konfigurerar du **Förhindra Android-säkerhetskopieringar** till **Ja**.
2. Bekräfta följande villkor:
    - Säkerhetskopior begränsas.

### <a name="unenrollment"></a>Avregistrering
Du kan fjärrensa e-post och dokument som tillhör företaget på hanterade appar. Personliga data dekrypteras när de inte längre administreras. Så här gör du:

1. Från Azure-portalen [utför du en rensning](../apps/apps-selective-wipe.md).
2. Om appen inte registreras för några rensningshanterare bekräftar du följande villkor:
    - En fullständig rensning av appen sker.
3. Om appen har registrerats för `WIPE_USER_DATA` eller `WIPE_USER_AUXILARY_DATA` bekräftar du följande villkor:
    - Det hanterade innehållet tas bort från appen. Mer information finns i [utvecklarhandboken för Intune App SDK för Android – selektiv rensning](app-sdk-android.md#selective-wipe).

### <a name="multi-identity-support"></a>Stöd för flera identiteter
Integrering av [stöd för flera identiteter](app-sdk-android.md#multi-identity-optional) är en ändring med hög risk som behöver testas ordentligt. De vanligaste problemen beror på felaktig inställning av identiteten (kontext vs. Threat Level) och spårning av filer (`MAMFileProtectionManager`).

Kontrol lera minimalt att:

- **Spara som**-principen fungerar korrekt för hanterade identiteter.
- Begränsningar för Kopiera/Klistra tillämpas korrekt, från hanterat till personligt.
- Endast data som tillhör den hanterade identiteten krypteras. Personliga filer ändras inte.
- Selektiv rensning vid avregistrering tar endast bort data för hanterad identitet.
- Villkorlig start krävs när användaren växlar från ett ohanterat till ett hanterat konto (endast första gången).

### <a name="app-configuration-optional"></a>Appkonfiguration (valfritt)
Du kan konfigurera beteendet för hanterade appar. Om din app förbrukar några inställningar för appkonfiguration bör du testa att appen korrekt hanterar alla värden som du (i egenskap av administratör) kan ange. Du kan skapa och tilldela [konfigurations principer för appar](../apps/app-configuration-policies-overview.md) i Intune.

## <a name="next-steps"></a>Nästa steg

- [Lägga till en verksamhetsspecifik app för Android i Microsoft Intune](../apps/lob-apps-android.md)
