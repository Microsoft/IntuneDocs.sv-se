---
title: "Konfigurera principer för enhetsefterlevnad och apphantering under en Intune-migrering | Microsoft Docs"
description: "Syftet med den här artikeln är att tillhandahålla de nödvändiga åtgärder som krävs för att konfigurera enhetsefterlevnad och apphantering under en Intune-migrering."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 5904b117ccab9046d2afde4a761b4724431a6302
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-device-compliance-and-app-management-policies"></a>Fas 1: Konfigurera principer för enhetsefterlevnad och apphantering

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

Den [klassiska Intune-portalen](https://manage.microsoft.com/) ger dig möjlighet att skapa enhetsgrupper när du utför en rad olika administrativa uppgifter utifrån enhetsidentitet istället för användaridentitet.

Enhetsgrupper är användbara när du hanterar enheter utan dedikerade användare, t.ex. enheter i helskärmsläge eller enheter som delas av skiftarbetare eller tilldelats en viss plats.

Genom att konfigurera enhetsgrupperna innan enhetsregistreringen genomförs kan du utnyttja enhetskategorierna för att gruppera enheterna automatiskt vid registreringen, så att de får sin grupps enhetsprinciper automatiskt.

-   Lär dig [hur man lägger till enhetsgrupper](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5).

-   Lär dig [hur man konfigurerar enhetskategorier](https://docs.microsoft.com/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Uppgift 2: Använd resursåtkomstprofiler (Wi-Fi, VPN och e-certifikat)

Resursåtkomstprofiler förser registrerade enheter med certifikat och åtkomstkonfigurationer.

Som tidigare beskrivs i avsnittet Utvärdera MDM-krav måste du, om du använder certifikatbaserad autentisering, ha en [PKI-infrastruktur på plats](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) för att kunna distribuera VPN-, Wi-Fi- och e-postcertifikat.

#### <a name="direct-import-of-resource-access-profiles-optional"></a>Direktimport av resursåtkomstprofiler (valfritt)

Om din befintliga MDM-lösning tillhandahåller en mekanism för att exportera e-post-, Wi-Fi- och VPN-profiler i XML-format, så kan du kanske utnyttja XML-filen och helt enkelt importera den till Intune och använda OMA-URI för att skapa anpassade profiler för iOS-, Android- och Windows-enheter.

-   Lär dig hur du lägger till en anpassad princip för [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)-, [Android](https://docs.microsoft.com/intune/deploy-use/android-policy-settings-in-microsoft-intune)- och [Windows](https://docs.microsoft.com/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune)-enheter.

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Uppgift 3: Skapa och distribuera enhetskonfigurationsprofiler

Du måste skapa en enhetskonfigurationsprofil om du vill framtvinga inställningar på enhetsnivå, som t.ex. avser inaktivering av kamera, App Store, konfiguration av enappsläge, startsidan och annat.

- Lär dig mer om [profiler för enhetskonfiguration](https://docs.microsoft.com/intune-azure/configure-devices/how-to-create-device-profiles).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Direktimport av iOS-konfigurationsprofiler (valfritt)

-   **Apple Configurator-profiler för iOS (iOS 7.1 och senare):** Om din befintliga MDM-lösning använder Apple Configurator-profiler (.mobileconfig-filer) kan Intune importera dem direkt som anpassade konfigurationsprinciper.

-   **iOS-konfigurationsprinciper för mobila program:** Om din befintliga MDM-lösning använder iOS-konfigurationsprinciper för mobila program kan Intune importera dem direkt förutsatt att de uppfyller det XML-format för egenskapslistor som anges av Apple.

- Lär dig hur du lägger till en anpassad princip för [iOS](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune#custom-policy-settings)

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Uppgift 4: Skapa och distribuera principer för enhetsefterlevnad (valfritt)

Principerna för enhetsefterlevnad utvärderar säkerhetsinriktade inställningar och tillhandahåller rapporter som visar huruvida enheterna är kompatibla med företagets standarder eller inte. Principerna för enhetsefterlevnad utvärderar säkerhetsinriktade faktorer som:

-   PIN-kodslängd

-   Jailbrokad status

-   OS-version

Se ytterligare resurser för enhetsefterlevnadsinställningar:

-   Lär dig mer om [principer för enhetsefterlevnad](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

-   Läs om [hur du skapar en princip för enhetsefterlevnad](https://docs.microsoft.com/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune).

### <a name="task-5-publish-and-deploy-apps"></a>Uppgift 5: Publicera och distribuera appar

När du använder Intune MDM kan du tillhandahålla appar genom att kräva att de ska installeras automatiskt eller genom att göra dem tillgängliga i företagsportalen.

-   Lär dig mer om [hur du lägger till appar](https://docs.microsoft.com/intune/deploy-use/add-apps).

-   Lär dig mer om [hur du distribuerar appar](https://docs.microsoft.com/intune/deploy-use/deploy-apps).

### <a name="task-6-enable-device-enrollment"></a>Uppgift 6: Aktivera enhetsregistrering

Registreringen upprättar hantering genom att tillhandahålla kontroll över enheten.

-   Lär dig mer om [hur du förbereder dig för att registrera företagsägda enheter och användarnas personliga enheter](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

-   Lär dig hur du [registrerar företagsägda enheter](https://docs.microsoft.com/intune/deploy-use/manage-corporate-owned-devices).

Om du behöver registrera delade eller användarlösa enheter kan du använda ett [konto för enhetsregistreringshanterare](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## <a name="next-steps"></a>Nästa steg 

[Fas 1: Konfigurera appskyddsprinciper (valfritt)](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-app-protection-policies)

