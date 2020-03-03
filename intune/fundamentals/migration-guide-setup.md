---
title: Grundläggande inställningar för Microsoft Intune
description: Den här artikeln beskriver de steg du följer för att konfigurera Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08041a57ab52f395283e57cda596d00ba168aba1
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556490"
---
# <a name="basic-setup"></a>Grundläggande konfiguration

När du har utvärderat din miljö är det dags att konfigurera Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Externa beroenden för en Intune-distribution

### <a name="identity"></a>Identitet

Intune kräver Azure Active Directory (AAD) som leverantör av identitet och användargruppering. Läs mer om:

- [Identitetskrav](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [Katalogsynkroniseringskrav](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Multifaktorautentisering (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [Planera dina användar- och enhetsgrupper](users-add.md)

- [Skapa användar- och enhetsgrupper](groups-get-started.md)

Om din organisation redan använder Office 365 måste Intune använda samma Azure Active Directory-miljö.

### <a name="pki-optional"></a>PKI (valfritt)

Om du planerar att använda certifikatbaserad autentisering för VPN-, Wi-Fi- eller e-postprofiler med Intune måste du kontrollera att du har en [PKI-infrastruktur på plats](../protect/certificates-configure.md) som stöds och är redo att skapa och distribuera certifikatprofiler. Lär dig mer om hur du konfigurerar certifikat i Intune:

- [Konfigurera certifikatinfrastrukturen för SCEP](/intune/certificates-scep-configure)

- [Konfigurera certifikatinfrastruktur för PFX](/intune/certficates-pfx-configure).

## <a name="task-list-for-an-intune-setup"></a>Uppgiftslista för en Intune-konfiguration

### <a name="task-1-intune-subscription"></a>Uppgift 1: Intune-prenumeration

Innan du kan migrera till Intune måste du ha en [Intune-prenumeration](account-sign-up.md).

### <a name="task-2-assign-intune-user-licenses"></a>Uppgift 2: Tilldela Intune-användarlicenser

- Lär dig [hur man tilldelar Intune-användarlicenser](licenses-assign.md).

- Om du har skapat en ny Azure Active Directory-klient kan du läsa om [hur du kan skapa nya användare eller synkronisera användare från din lokala Active Directory (AD).](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Uppgift 3: Ange din MDM-auktoritet till Intune

Vi rekommenderar att du hanterar Intune med hjälp av [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Ange din MDM-auktoritet som **Intune**. Genom att använda en annan utfärdare för hantering av mobilenheter kan du låta Intune överföra hanteringen av mobilenheter till alternativa Microsoft-hanteringskonsoler. Dessa fall är ovanliga.

> [!IMPORTANT]
> Om du överför hanteringen av mobila enheter till Intune för första gången måste du ange Intune som utfärdare för hantering av mobilenheter.

Lär dig hur [man anger utfärdare för hantering av mobilenheter](mdm-authority-set.md).

## <a name="next-step"></a>Nästa steg

Konfigurera [principer för enhets- och apphantering](../migration-guide-configure-policies.md).
