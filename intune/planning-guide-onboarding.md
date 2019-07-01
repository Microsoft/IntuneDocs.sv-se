---
title: Intunes integrationsprocess
titleSuffix: Microsoft Intune
description: Den här artikeln hjälper dig med alla detaljer som ska övervägas vid registreringen av en Microsoft Intune-molnlösning i din miljö.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ed13994576f67c7b740a2ea895db9d1a0f42289
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044350"
---
# <a name="implement-your-microsoft-intune-plan"></a>Implementera din Microsoft Intune-plan

Under integrationsfasen distribuerar du Intune i produktionsmiljön. I själva implementeringsprocessen installerar du och konfigurerar Intune och externa beroenden (vid behov) baserat på dina [användningsfallskrav](planning-guide-requirements.md).

Följande avsnitt innehåller en översikt över processen för Intune-implementering som omfattar krav samt avancerade åtgärder.

## <a name="intune-requirements"></a>Krav för Intune

De huvudsakliga kraven för ett fristående Intune är:

-   Enterprise Mobility + Security (EMS)/Intune-prenumeration

-   Office 365-prenumeration (för Office-appar och appar som hanteras av en appskyddsprincip)

-   Apple APNs-certifikat (för att aktivera hantering av iOS-enhetsplattform)

-   Azure AD Connect (för katalogsynkronisering)

-   Intune On-Premises Connector för Exchange (för villkorlig åtkomst till Exchange On-Premises, om så behövs)

-   Intune Certificate Connector (för distribution av SCEP-certifikat, vid behov)

>[!TIP]
> Se listan över [enheter som stöds](supported-devices-browsers.md) för en fullständig lista över enheter som du kan hantera med Intune.

## <a name="intune-implementation-process"></a>Process för Intune-implementering

Vi har identifierat 13 diskreta uppgifter för implementeringen av en Intune-distribution. Beroende på dina affärskrav, din befintliga infrastruktur och din enhetshanteringsstrategi kanske vissa av dessa uppgifter redan har genomförts. Andra kanske inte är relevanta för din plan.

### <a name="task-1-get-an-intune-subscription"></a>Uppgift 1: Skaffa en Intune-prenumeration

Som vi redan nämnt i avsnittet för Intune-krav ovan behöver du en EMS- eller Intune-prenumeration. Om din organisation inte har någon kontaktar du Microsoft eller ditt Microsoft-kontoteam för information om hur du skaffar Enterprise Mobility + Security (EMS) eller Intune.

-   Läs mer om att [köpa Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing).

### <a name="task-2-add-office-365-subscription"></a>Uppgift 2: Lägga till Office 365-prenumeration

Det här är valfritt. Du behöver en Office 365-prenumeration om du ska använda Exchange Online och hantera Office-mobilappar med appskyddsprinciper. Om din organisation inte har någon Office 365-prenumeration kontaktar du Microsoft eller ditt Microsoft-kontoteam för information om hur du köper Office 365.

-   Läs mer om att [köpa Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

### <a name="task-3-add-users-groups-in-azure-ad"></a>Uppgift 3: Lägga till användargrupper i Azure AD

Du kan behöva lägga till användare eller säkerhetsgrupper i Active Directory eller Azure Active Directory beroende på dina användningsfallsscenarier och krav för Intune-distributionen. Se över dina aktuella användare och säkerhetsgrupper i Active Directory eller Azure Active Directory och kontrollera om de uppfyller alla behov. När du lägger till nya användare och säkerhetsgrupper rekommenderar vi att du lägger till dem i Active Directory och synkroniserar med Azure Active Directory med hjälp av Azure AD Connect.


-   Läs mer om att [lägga till användare/grupper i Intune](users-permissions-add.md).
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Uppgift 4: Tilldela Intune- och Office 365-användarlicenser

Alla användare som EMS/Intune- och Office 365-distributionen ska omfatta måste ha en tilldelad licens. Du kan tilldela EMS/Intune- och Office 365-licenser i Microsoft 365-administrationscentret.

-   Läs mer om att [tilldela Intune-licenser](licenses-assign.md).

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Uppgift 5: Ange auktoritet för hantering av mobilenheter till Intune

Innan du kan börja installera, konfigurera, hantera och registrera enheter med Intune måste du ange Intune som enhetshanteringsutfärdare.

-   Läs mer om [hur du anger utfärdare för hantering av enheter](mdm-authority-set.md).

### <a name="task-6-enable-device-platforms"></a>Uppgift 6: Aktivera enhetsplattformar

De flesta enhetsplattformar är aktiverade som standard, förutom Apple-enheter (iOS och Mac). Innan iOS-enheter kan registreras och hanteras i Intune måste enhetsplattformen vara aktiverad. Om du vill aktivera dessa enheter måste du skapa ett MDM-pushcertifikat och lägga till det i Intune.

-   Läs mer om [hur du aktiverar Apple-enheter för registrering](apple-mdm-push-certificate-get.md).

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Uppgift 7: Lägga till och distribuera villkorsprinciper

Intune stöder villkorsprinciper. Lägg till villkorsprinciper efter behov och distribuera dem till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [lägga till och distribuera principer för villkor](terms-and-conditions-create.md).

### <a name="task-8-add-and-deploy-configuration-policies"></a>Uppgift 8: Lägga till och distribuera konfigurationsprinciper

Intune stöder två typer av konfigurationsprinciper: allmänna och anpassade. Lägg till konfigurationsprinciper efter behov och distribuera dem till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [lägga till och distribuera konfigurationsprinciper](device-profiles.md).

### <a name="task-9-add-and-deploy-resource-profiles"></a>Uppgift 9: Lägga till och distribuera resursprofiler

Intune stöder e-post-, Wi-Fi- och VPN-profiler. Lägg till dessa profiler efter behov och distribuera dem till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om [hur du ger åtkomst till företagsresurser med Intune](device-profiles.md).

### <a name="task-10-add-and-deploy-apps"></a>Uppgift 10: Lägg till och distribuera appar

Intune stöder distribution av webbappar, verksamhetsspecifika appar och offentliga Store-appar. Du kan också hantera appar som har integrerat Intune SDK genom att associera dem med appskyddsprinciper. Lägg till appar efter behov och distribuera dem till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om [hur du lägger till och distribuerar appar](app-management.md).

### <a name="task-11-add-and-deploy-compliance-policies"></a>Uppgift 11: Lägga till och distribuera efterlevnadsprinciper

Intune stöder efterlevnadspolicyer. Lägg till efterlevnadsprinciper efter behov och distribuera dem till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om [efterlevnadsprinciper](device-compliance.md).

### <a name="task-12-enable-conditional-access-policies"></a>Uppgift 12: Aktivera principer för villkorlig åtkomst

Intune stöder villkorlig åtkomst för Exchange Online, Exchange On-Premises, SharePoint Online, Skype för företag – Online och Dynamics CRM Online. Aktivera och konfigurera villkorlig åtkomst efter behov, baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om [villkorlig åtkomst](conditional-access.md).

### <a name="task-13-enroll-devices"></a>Uppgift 13: Registrera enheter

Intune stöder enhetsplattformarna iOS, Mac OS, Android, Windows och Windows Mobile. Registrera mobila enhetsplattformar efter behov baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [registrera enheter](device-enrollment.md).


## <a name="next-steps"></a>Nästa steg

Titta på denna [Intune-sessionsmodul för Microsoft Virtual Academy](https://mva.microsoft.com/en-US/training-courses/deploying-microsoft-enterprise-mobility-suite-16408) om du vill ha mer information om processen för Intune-implementering.


Läs mer om [hur du testar och validerar din Intune-distribution](planning-guide-test-validation.md).
