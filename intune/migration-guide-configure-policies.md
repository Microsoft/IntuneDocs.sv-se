---
title: "Konfigurera principer för enhetsefterlevnad och apphantering under en Intune-migrering"
description: "Syftet med den här artikeln är att tillhandahålla de nödvändiga åtgärder som krävs för att konfigurera enhetsefterlevnad och apphantering under en Intune-migrering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5e848dda6643a28141a8f5f1d0bdc01f2bd9d390
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="configure-device-compliance-and-app-management-policies"></a>Konfigurera principer för enhetsefterlevnad och apphantering

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Det huvudsakliga målet vid migrering till Intune är att alla enheter ska registreras och uppfylla dess principer. Enhetsprinciperna hjälper dig inte enbart med att hantera företagsägda enanvändarenheter utan även personliga BYOD-enheter och delade enheter, t.ex. informationsdatorer, kassadatorer, surfplattor som delas av flera elever i ett klassrum, eller användarlösa enheter (endast iOS).

Varje enhetsplattform kan erbjuda olika inställningar, men Intune-enhetsprinciperna fungerar med varje enhetsplattform genom att tillhandahålla följande funktioner för hantering av mobilenheter:

-   Reglera det antal enheter som varje användare kan registrera.

-   Hantera enhetsinställningar (t.ex. kryptering på enhetsnivå, lösenordslängd, kameraanvändning).

-   Leverera appar, e-postprofiler, VPN-profiler osv.

-   Utvärdera villkor på enhetsnivå för principer för säkerhetsefterlevnad.

> [!IMPORTANT]
> Principer för enhetshantering tilldelas inte direkt till enskilda enheter eller användare, men tilldelas istället till användargrupper. Principerna kan tillämpas direkt på en användargrupp, och därmed på användarenheten, eller så kan principerna tillämpas på en enhetsgrupp, och därmed på gruppmedlemmar.

## <a name="task-list-for-device-compliance-policies"></a>Uppgiftslista för principer för enhetsefterlevnad

### <a name="task-1-add-device-groups-optional"></a>Uppgift 1: Lägg till enhetsgrupper (valfritt)

Du kan skapa enhetsgrupper när du utför en rad olika administrativa uppgifter utifrån enhetsidentitet istället för användaridentitet.

Enhetsgrupper är användbara när du hanterar enheter utan dedikerade användare, t.ex. enheter i helskärmsläge eller enheter som delas av skiftarbetare eller tilldelats en viss plats.

Genom att konfigurera enhetsgrupperna innan enhetsregistreringen genomförs kan du utnyttja enhetskategorierna för att gruppera enheterna automatiskt vid registreringen, så att de får sin grupps enhetsprinciper automatiskt. [Kom igång med grupper](/intune/groups-get-started).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Uppgift 2: Använd resursåtkomstprofiler (Wi-Fi, VPN och e-certifikat)

Resursåtkomstprofiler förser registrerade enheter med certifikat och åtkomstkonfigurationer.

Om du använder certifikatsbaserad autentisering, så som tidigare diskuteras i avsnittet om att utvärdera MDM-krav, ska du [konfigurera certifikat](/intune/certificates-configure).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Uppgift 3: Skapa och distribuera enhetskonfigurationsprofiler

Du måste skapa en enhetskonfigurationsprofil om du vill framtvinga inställningar på enhetsnivå, som t.ex. avser inaktivering av kamera, App Store, konfiguration av enappsläge, startsidan och annat.

- Lär dig mer om [enhetsprofiler](/intune/device-profiles).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Direktimport av iOS-konfigurationsprofiler (valfritt)

-   **Apple Configurator-profiler för iOS (iOS 7.1 och senare):** Om din befintliga MDM-lösning använder Apple Configurator-profiler (.mobileconfig-filer) kan Intune importera dem direkt som anpassade konfigurationsprinciper.

-   **iOS-konfigurationsprinciper för mobila program:** Om din befintliga MDM-lösning använder iOS-konfigurationsprinciper för mobila program kan Intune importera dem direkt förutsatt att de uppfyller det XML-format för egenskapslistor som anges av Apple.

- Lär dig hur du lägger till en anpassad princip för [iOS](/intune/custom-settings-ios)

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Uppgift 4: Skapa och distribuera principer för enhetsefterlevnad (valfritt)

Principerna för enhetsefterlevnad utvärderar säkerhetsinriktade inställningar och tillhandahåller rapporter som visar huruvida enheterna är kompatibla med företagets standarder eller inte. Principerna för enhetsefterlevnad utvärderar säkerhetsinriktade faktorer som:

-   PIN-kodslängd

-   Jailbrokad status

-   OS-version

Se ytterligare resurser för enhetsefterlevnadsinställningar:

-   Lär dig mer om [principer för enhetsefterlevnad](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

-   Läs om [hur du skapar en princip för enhetsefterlevnad](/intune-classic/deploy-use/create-a-device-compliance-policy-in-microsoft-intune).

### <a name="task-5-publish-and-deploy-apps"></a>Uppgift 5: Publicera och distribuera appar

När du använder Intune MDM kan du tillhandahålla appar genom att kräva att de ska installeras automatiskt eller genom att göra dem tillgängliga i företagsportalen.

-   Lär dig mer om [hur du lägger till appar](/intune-classic/deploy-use/add-apps).

-   Lär dig mer om [hur du distribuerar appar](/intune-classic/deploy-use/deploy-apps).

### <a name="task-6-enable-device-enrollment"></a>Uppgift 6: Aktivera enhetsregistrering

Registreringen upprättar hantering genom att tillhandahålla kontroll över enheten. Lär dig mer om [hur du förbereder dig för att registrera företagsägda enheter och användarnas personliga enheter](/intune/device-enrollment).

## <a name="next-steps"></a>Nästa steg 

[Konfigurera appskyddsprinciper (valfritt)](migration-guide-app-protection-policies.md)
