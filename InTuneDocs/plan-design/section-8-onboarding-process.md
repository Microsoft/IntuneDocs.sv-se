---
title: "Onboarding-process för Intune | Microsoft Docs"
description: "Den här artikeln hjälper dig med alla detaljer som ska övervägas vid onboarding av Intune-molnlösningen i miljön."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: fa33bd3833f7f7198eed3f4f486c27bae3ba47d7
ms.openlocfilehash: 87832ec7f295c08678052d19164af9a8db051f9f
ms.lasthandoff: 12/30/2016


---

# <a name="intune-implementation"></a>Intune-implementering

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Under onboarding-fasen implementerar du Intune i produktionsmiljön. Implementeringsprocessen består av att ställa in och konfigurera Intune och externa beroenden (vid behov) baserat på dina [krav för användningsfall](section-3-determine-use-case-requirements.md) som togs upp i föregående avsnitt i den här handledningen.

Följande avsnitt innehåller en översikt över processen för Intune-implementering som omfattar krav samt avancerade åtgärder.

>[!TIP]
> Läs [Ytterligare resurser](additional-resources.md) om du vill ha mer information om processen för Intune-implementering.

## <a name="intune-requirements"></a>Krav för Intune

De viktigaste kraven för fristående Intune anges nedan:

-   EMS/Intune-prenumeration

-   Office 365-prenumeration (för Office-appar och MAM-principhanterade appar)

-   Apple APNs-certifikat (för att aktivera hantering av iOS-enhetsplattform)

-   Azure AD Connect (för katalogsynkronisering)

-   Intune On-Premises Connector för Exchange (för CA för Exchange On-Premises, vid behov)

-   Intune Certificate Connector (för distribution av SCEP-certifikat, vid behov)

>[!TIP]
> Mer information om kraven för fristående Intune finns [här](https://docs.microsoft.com/intune/get-started/what-to-know-before-you-start-microsoft-intune).

## <a name="intune-implementation-process"></a>Process för Intune-implementering

### <a name="overview-of-implementation-tasks"></a>Översikt över implementeringsaktiviteter

Följande är en översikt över varje åtgärd vid implementering av Intune.

#### <a name="task-1-add-intune-subscription"></a>Åtgärd 1: Lägg till Intune-prenumeration

En EMS- eller Intune-prenumeration krävs, vilket identifieras i föregående kravavsnitt. Om organisationen inte har en EMS- eller Intune-prenumeration kan du kontakta Microsoft eller Microsoft-kontoteamet angående att du är intresserad av att köpa Enterprise Mobility + Security (EMS) eller Intune.

-   Läs mer om att [köpa Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-pricing).

#### <a name="task-2-add-office-365-subscription"></a>Åtgärd 2: Lägga till Office 365-prenumeration

Det här är valfritt. En Office 365-prenumeration krävs om du planerar att använda Exchange Online och hantera Office-mobilappar med MAM-principer, vilket identifieras i föregående avsnitt. Om organisationen inte har en Office 365-prenumeration kan du kontakta Microsoft eller Microsoft-kontoteamet angående att du är intresserad av att köpa Office 365.

-   Läs mer om att [köpa Office 365](https://products.office.com/business/compare-office-365-for-business-plans).

#### <a name="task-3-add-users-groups-in-azure-ad"></a>Åtgärd 3: Lägga till användargrupper i Azure AD

Du kan behöva lägga till användare eller säkerhetsgrupper i AD eller AAD baserat på användningsfall och krav för Intune-distributionen. Du bör granska de aktuella användarna och säkerhetsgrupperna i Active Directory eller Azure Active Directory och fastställa om de uppfyller behoven helt. Nya användare och säkerhetsgrupper läggs oftast till i Active Directory och synkroniseras till Azure Active Directory via Azure AD Directory Connect.

-   Läs mer om att [lägga till användare/grupper i Intune](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3).

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>Åtgärd 4: Tilldela Intune- och Office 365-användarlicenser

Alla användare som ska vara mål för distributionen av EMS/Intune och Office 365 måste ha en tilldelad licens. Licenstilldelning för EMS/Intune och Office 365 kan göras i administrationscenterportalen för Office 365.

-   Läs mer om att [tilldela Intune-licenser](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>Åtgärd 5: Ange utfärdare för hantering av mobila enheter till Intune

Innan du kan börja installera, konfigurera, hantera och registrera enheter med Intune måste du ange utfärdare för hantering av enheter i Intune. Du anger utfärdare för hantering av enheter i Intune-administratörsportalen, i arbetsytan Admin.

-   Läs mer om att [ställa in utfärdare för hantering av enheter](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

#### <a name="task-6-enable-device-platforms"></a>Åtgärd 6: Aktivera enhetsplattformar

De flesta enhetsplattformar är aktiverade som standard i Intune-administratörskonsolen, förutom Apple-enheter (iOS och Mac). Innan iOS-enheter kan registreras och hanteras i Intune måste enhetsplattformen vara aktiverad. Aktivering av iOS-enhetsplattformen består av en process i tre steg: skapa och hämta APNs-certifikatet och ladda upp APNs-certifikatet till Intune.

-   Läs mer om [hur konfiguration av iOS- och Mac-enhetshantering fungerar.](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>Åtgärd 7: Lägga till och distribuera principer för villkor

Microsoft Intune har stöd för att lägga till och distribuera principer för villkor. Du lägger till och distribuerar principer för villkor i Intune-administratörsportalen, i arbetsytan Princip. Lägg till villkorsprinciper efter behov och distribuera till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [lägga till och distribuera principer för villkor](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune).

#### <a name="task-8-add-and-deploy-configuration-policies"></a>Åtgärd 8: Lägga till och distribuera konfigurationsprinciper

Microsoft Intune har stöd för att lägga till och distribuera två typer av konfigurationsprinciper, allmänna och anpassade. Du lägger till och distribuerar konfigurationsprinciper i Intune-administratörsportalen, i arbetsytan Princip. Lägg till konfigurationsprinciper efter behov och distribuera till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [lägga till och distribuera konfigurationsprinciper](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

#### <a name="task-9-add-and-deploy-resource-profiles"></a>Åtgärd 9: Lägga till och distribuera resursprofiler

Microsoft Intune har stöd för e-post-, Wi-Fi- och VPN-profiler. Du lägger till och distribuerar profiler i Intune-administratörsportalen, i arbetsytan Princip. Lägg till e-post-/Wi-Fi-/VPN-profiler efter behov och distribuera till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [ge åtkomst till företagsresurser med Intune](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

#### <a name="task-10-add-and-deploy-apps"></a>Åtgärd 10: Lägga till och distribuera appar

Microsoft Intune har stöd för distribution av webb-, LOB- och offentliga butiksappar. Dessutom stöds hantering av appar som har Intune SDK integrerat genom att koppla dem till MAM-principer. Du lägger till och distribuerar appar i Intune-administratörsportalen, i arbetsytan App. Du lägger till MAM-principer i Intune-administratörsportalen, i arbetsytan Princip. Lägg till appar efter behov och distribuera till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [lägga till och distribuera program](https://docs.microsoft.com/en-us/intune/deploy-use/deploy-apps).

#### <a name="task-11-add-and-deploy-compliance-policies"></a>Åtgärd 11: Lägga till och distribuera efterlevnadsprinciper

Microsoft Intune har stöd för efterlevnadsprinciper. Du lägger till och distribuerar efterlevnadsprinciper i Intune-administratörsportalen, i arbetsytan Princip. Lägg till efterlevnadsprinciper efter behov och distribuera till målgrupperna baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om [efterlevnadsprinciper](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

#### <a name="task-12-enable-conditional-access-policies"></a>Åtgärd 12: Aktivera principer för villkorlig åtkomst

Microsoft Intune har stöd för villkorlig åtkomst för Exchange Online och On-premises, SharePoint Online, Skype för företag – Online och Dynamics CRM Online. Du aktiverar principer för villkorlig åtkomst i Intune-administratörsportalen, arbetsytan Princip. Aktivera och konfigurera villkorlig åtkomst efter behov baserat på [användningsfall och krav för Intune-distributionen](section-3-determine-use-case-requirements.md).

-   Läs mer om [villkorlig åtkomst](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

#### <a name="task-13-enroll-devices"></a>Åtgärd 13: Registrera enheter

Intune har stöd för enhetsplattformarna iOS, Mac OS, Android, Windows och Windows Mobile. Registrera mobila enhetsplattformar efter behov baserat på användningsfall och krav för Intune-distributionen.

-   Läs mer om att [registrera enheter](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

>[!TIP]
> Titta på denna [Intune-sessionsmodul för Microsoft Virtual Academy](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676) om du vill ha mer information om processen för Intune-implementering.

## <a name="next-section"></a>Nästa avsnitt

Nästa avsnitt innehåller råd om att [testa och validera Intune-distributionen](section-9-test-and-validation.md).

