---
title: "Grundläggande inställningar för Intune | Microsoft Docs"
description: "Syftet med den här artikeln är att tillhandahålla nödvändiga åtgärder för hur du konfigurerar Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 0fce3edb43a147491465d8a58d1a9a4f009fba55
ms.lasthandoff: 04/14/2017


---

# <a name="phase-1-basic-setup"></a>Fas 1: Grundläggande konfiguration

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

När du utvärderat miljön är det dags att konfigurera Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Externa beroenden för en Intune-distribution

### <a name="identity"></a>Identitet

Intune kräver Azure Active Directory (AAD) som leverantör av identitet och användargruppering.

-   Läs mer om [identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Läs mer om [katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Läs mer om [krav för multifaktorautentisering](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

-   Läs mer om att [planera användar- och enhetsgrupper](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Läs om att [skapa användar- och enhetsgrupper](https://docs.microsoft.com/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

Om företaget redan använder Office 365 är det viktigt att Intune använder samma Azure Active Directory-miljö.

### <a name="pki-optional"></a>PKI (valfritt)

Om du planerar att använda certifikatbaserad autentisering för VPN-, Wi-Fi- eller e-postprofiler med Intune måste du kontrollera att du har en [PKI-infrastruktur på plats](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) som stöds och är redo att skapa och distribuera certifikatprofiler.

Mer information om hur man konfigurerar certifikat i Intune finns nedan.

-   [Konfigurera certifikatinfrastruktur för SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Konfigurera certifikatinfrastruktur för PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Konfigurera Intune-certifikatsprofiler](file:///C:/intune/deploy-use/https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Konfigurera resursåtkomstprinciper](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="task-list-for-an-intune-setup"></a>Uppgiftslista för en Intune-installation

### <a name="task-1-intune-subscription"></a>Uppgift 1: Intune-prenumeration

Innan du kan migrera till Intune måste du ha en Intune-prenumeration.

-   Du kan besöka [den här sidan](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0). Här får du anvisningar om hur du kan:

    -   Skapa en ny Intune-prenumeration som är länkad till en ny AAD-klient.

    -   Länka Intune-prenumerationen genom att logga in till en befintlig AAD-klient.

### <a name="task-2-assign-intune-user-licenses"></a>Steg 2: Tilldela Intune-användarlicenser

-   Lär dig [hur man tilldelar Intune-användarlicenser](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

-   Om du har skapat en ny Azure Active Directory-klient kan du läsa om [hur du kan skapa nya användare eller synkronisera användare från din lokala Active Directory (AD).](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Uppgift 3: Konfigurera Intune som utfärdare för hantering av mobilenheter

Du kan hantera Intune via Azure Portal eller konsolen Configuration Manager Current Branch. Såvida du inte behöver integrera Intune med en Configuration Manager Current Branch-distribution så rekommenderar vi att du hanterar Intune från [Azure Portal](https://portal.azure.com).

Aktivera Intune Azure Portal genom att ange **Intune** som utfärdare för hantering av mobilenheter. Genom att använda en annan utfärdare för hantering av mobilenheter kan du låta Intune överföra hanteringen av mobilenheter till alternativa Microsoft-hanteringskonsoler. Dessa fall är ovanliga.

> [!IMPORTANT]
> Om du överför hanteringen av mobila enheter till Intune för första gången måste du ange Intune som utfärdare för hantering av mobilenheter.

-   Lär dig hur [man anger utfärdare för hantering av mobilenheter](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

## <a name="next-step"></a>Nästa steg

[Fas 1: Konfigurera principer för enhets- och apphantering](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

