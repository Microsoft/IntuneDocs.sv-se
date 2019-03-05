---
title: Konfigurera enhets- och appefterlevnad under en Intune-migrering
titlesuffix: Microsoft Intune
description: Den här artikeln visar de steg som krävs för att konfigurera principer för enhetsefterlevnad och apphantering under en Microsoft Intune-migrering.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a0557eff752e1fc511716fc7e5de0ebe904172d
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230694"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Konfigurera principer för enhetsefterlevnad och apphantering vid migrering till Microsoft Intune

Det huvudsakliga målet vid migrering till Intune är att alla enheter ska registreras i Intune och uppfylla dess principer. Enhetsprinciperna hjälper dig inte enbart att hantera företagsägda enanvändarenheter utan även personliga BYOD-enheter och delade enheter, t.ex. informationsdatorer, kassadatorer, surfplattor som delas av flera elever i ett klassrum, eller användarlösa enheter (endast iOS).

Varje enhetsplattform kan erbjuda olika inställningar, men Intune-enhetsprinciperna fungerar med varje enhetsplattform genom att tillhandahålla följande funktioner för hantering av mobilenheter:

-   Reglera det antal enheter som varje användare kan registrera.

-   Hantera enhetsinställningar (t.ex. kryptering på enhetsnivå, lösenordslängd, kameraanvändning).

-   Leverera appar, e-postprofiler, VPN-profiler osv.

-   Utvärdera villkor på enhetsnivå för principer för säkerhetsefterlevnad.

> [!IMPORTANT]
> Principer för enhetshantering tilldelas inte direkt till enskilda enheter eller användare, men tilldelas istället till användargrupper. Principerna kan tillämpas direkt på en användargrupp, och därmed på användarenheten, eller så kan principerna tillämpas på en enhetsgrupp, och därmed på gruppmedlemmar.

## <a name="task-list-for-device-compliance-policies"></a>Uppgiftslista för principer för enhetsefterlevnad

### <a name="task-1-add-device-groups-optional"></a>Uppgift 1: Lägg till enhetsgrupper (valfritt)

Du kan skapa enhetsgrupper när du behöver utföra administrativa uppgifter utifrån enhetsidentitet istället för användaridentitet.

Enhetsgrupper är användbara när du hanterar enheter som inte har dedikerade användare, t.ex. enheter i helskärmsläge eller enheter som delas av skiftarbetare eller tilldelats en viss plats.

Genom att konfigurera enhetsgrupper före enhetsregistreringen kan du använda enhetskategorier för att automatiskt gruppera enheterna vid registrering. De får sedan sin grupps enhetsprinciper automatiskt. [Kom igång med grupper](groups-get-started.md).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Uppgift 2: Använd resursåtkomstprofiler (Wi-Fi, VPN och e-postcertifikat)

Resursåtkomstprofiler tillhandahåller registrerade enheter med certifikat och åtkomstkonfigurationer. Om du använder certifikatbaserad autentisering kan du [konfigurera certifikat](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Uppgift 3: Skapa och distribuera enhetskonfigurationsprofiler

Du måste skapa en enhetskonfigurationsprofil om du vill framtvinga inställningar på enhetsnivå, som t.ex. avser inaktivering av kamera, App Store, konfiguration av enappsläge, startsidan och annat. Lär dig mer om [enhetsprofiler](device-profiles.md).

####  <a name="directly-import-ios-configuration-profiles-optional"></a>Direktimport av iOS-konfigurationsprofiler (valfritt)

-   **Apple Configurator-profiler för iOS (iOS 7.1 och senare):** Om den befintliga MDM-lösningen använder Apple Configurator-profiler (.mobileconfig-filer), kan Intune importera dem direkt som anpassade konfigurationsprinciper.

-   **iOS-konfigurationsprinciper för mobilappar:** Om din befintliga MDM-lösning använder iOS-konfigurationsprinciper för mobila program, kan Intune importera dem direkt förutsatt att de uppfyller det XML-format för egenskapslistor som anges av Apple.

- Lär dig hur du lägger till en anpassad princip för [iOS](custom-settings-ios.md).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Uppgift 4: Skapa och distribuera principer för enhetsefterlevnad (valfritt)

Principerna för enhetsefterlevnad utvärderar säkerhetsinriktade inställningar och tillhandahåller rapporter som visar huruvida enheterna är kompatibla med företagets standarder eller inte. Sådana inställningar omfattar:

-   PIN-kodslängd

-   Jailbrokad status

-   OS-version

Se ytterligare resurser för enhetsefterlevnadsinställningar:

-   Lär dig mer om [principer för enhetsefterlevnad](device-compliance.md).

-   Läs om [hur du skapar en princip för enhetsefterlevnad](device-compliance-get-started.md).

### <a name="task-5-publish-and-deploy-apps"></a>Uppgift 5: Publicera och distribuera appar

När du använder Intune MDM kan du tillhandahålla appar genom att kräva att de installeras automatiskt eller genom att göra dem tillgängliga i företagsportalen.

-   [Lägga till appar](apps-add.md).

-   [Distribuera appar](apps-deploy.md).

### <a name="task-6-enable-device-enrollment"></a>Uppgift 6: Aktivera registrering av enheter

Enhetsregistrering krävs för att hantera enheten. Lär dig mer om [hur du förbereder dig för att registrera företagsägda enheter och användarnas personliga enheter](device-enrollment.md).

## <a name="next-steps"></a>Nästa steg

[Konfigurera appskyddsprinciper (valfritt)](migration-guide-app-protection-policies.md).
