---
title: Grundläggande inställningar för Microsoft Intune
description: Den här artikeln beskriver de steg du följer för att konfigurera Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 4cec5c593fd4191a9d73e77b13fd38df81a7fe8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179753"
---
# <a name="basic-setup"></a>Grundläggande konfiguration

När du har utvärderat din miljö är det dags att konfigurera Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Externa beroenden för en Intune-distribution

### <a name="identity"></a>Identitet

Intune kräver Azure Active Directory (AAD) som leverantör av identitet och användargruppering. Läs mer om:

-  [Identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

-   [Katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

-   [Krav på multifaktorautentisering (MFA)](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

-   [Planera dina användar- och enhetsgrupper](users-add.md)

-   [Skapa användar- och enhetsgrupper](groups-get-started.md)

Om din organisation redan använder Office 365 måste Intune använda samma Azure Active Directory-miljö.

### <a name="pki-optional"></a>PKI (valfritt)

Om du planerar att använda certifikatbaserad autentisering för VPN-, Wi-Fi- eller e-postprofiler med Intune måste du kontrollera att du har en [PKI-infrastruktur på plats](certificates-configure.md) som stöds och är redo att skapa och distribuera certifikatprofiler. Lär dig mer om hur du konfigurerar certifikat i Intune:

-   [Konfigurera certifikatinfrastrukturen för SCEP](/intune/certificates-scep-configure)

-   [Konfigurera certifikatinfrastruktur för PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Uppgiftslista för en Intune-konfiguration

### <a name="task-1-intune-subscription"></a>Uppgift 1: Intune-prenumeration

Innan du kan migrera till Intune måste du ha en Intune-prenumeration.

-   Du kan besöka [den här sidan](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0). Här får du anvisningar om hur du kan:

    -   Skapa en ny Intune-prenumeration som är länkad till en ny AAD-klient.

    -   Länka Intune-prenumerationen genom att logga in till en befintlig AAD-klient.

### <a name="task-2-assign-intune-user-licenses"></a>Steg 2: Tilldela Intune-användarlicenser

-   Lär dig [hur man tilldelar Intune-användarlicenser](licenses-assign.md).

-   Om du har skapat en ny Azure Active Directory-klient kan du läsa om [hur du kan skapa nya användare eller synkronisera användare från din lokala Active Directory (AD).](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Uppgift 3: Konfigurera Intune som utfärdare för hantering av mobilenheter

Du kan hantera Intune via Azure Portal eller konsolen Configuration Manager Current Branch. Såvida du inte behöver integrera Intune med en Configuration Manager Current Branch-distribution rekommenderar vi att du hanterar Intune från [Azure-portalen](https://portal.azure.com).

Aktivera Intune Azure-portalen genom att ange **Intune** som utfärdare för hantering av mobilenheter (MDM). Genom att använda en annan utfärdare för hantering av mobilenheter kan du låta Intune överföra hanteringen av mobilenheter till alternativa Microsoft-hanteringskonsoler. Dessa fall är ovanliga.

> [!IMPORTANT]
> Om du överför hanteringen av mobila enheter till Intune för första gången måste du ange Intune som utfärdare för hantering av mobilenheter.

Lär dig hur [man anger utfärdare för hantering av mobilenheter](mdm-authority-set.md).

## <a name="next-step"></a>Nästa steg

Konfigurera [principer för enhets- och apphantering](migration-guide-configure-policies.md).
