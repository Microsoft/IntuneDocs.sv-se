---
title: Symantec-anslutningsprogram med Microsoft Intune
titleSuffix: Microsoft Intune
description: Läs mer om hur du integrerar Intune med Symantec Endpoint Protection Mobile för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3c2cd696e2e8dabbe8c45a5758d1315c4ca31c4
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569720"
---
# <a name="symantec-endpoint-protection-mobile-connector"></a>Symantec Endpoint Protection Mobile-anslutningsprogram

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst baserat på riskbedömning som utförs av Symantec Endpoint Protection Mobile (SEP Mobile), en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör SEP Mobile och inkluderar:

-   Fysiskt skydd

-   Nätverksskydd

-   Programskydd

-   Skydd mot säkerhetsrisker

Du kan aktivera SEP Mobile-riskbedömning via Intunes efterlevnadsprinciper för enheter och använda principer för villkorlig åtkomst för att tillåta eller blockera åtkomst för icke-kompatibla enheter till företagets resurser baserat på de hot som har identifierats.

## <a name="how-do-intune-and-sep-mobile-help-protect-your-company-resources"></a>Hur skyddar Intune och SEP Mobile företagets resurser?

SEP Mobile-appen för Android eller iOS avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt. Detta skickas sedan till Symantecs molntjänst som utvärderar enhetens risk för mobila hot.

Intune-enhetens efterlevnadsprincip innehåller en regel för SEP Mobile, som är baserad på SEP Mobiles riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel blockeras åtkomst till resurser som Exchange Online och SharePoint Online. Användarna av blockerade enheter får anvisningar i SEP Mobile-app för att lösa problemet och återfå åtkomsten till företagets resurser.

Intune stöder två lägen för integrering med SEP Mobile:

-   **Grundinställning** är ett skrivskyddat läge som gör SEP Mobile synligt för enheter i Intune.

-   **Fullständig integrering** tillåter att SEP Mobile rapporterar information om enhetsrisker och säkerhetsincidenter till Intune.

## <a name="sample-scenarios"></a>Exempelscenarier

Nedan visas några vanliga scenarier:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna till dess att hotet har åtgärdats:

-   Ansluta till företagets e-post

-   Synkronisera företagets filer med appen OneDrive för arbetet

-   Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Konceptbild av skadliga appar som har identifierats](./media/symantec-arch-1.png)

**Åtkomst beviljad när problemet är löst:**

![Bild av Åtkomst beviljad när problemet är löst efter att skadliga appar har identifierats](./media/symantec-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket, samt skydda åtkomsten till WiFi-nätverk baserat på enhetsrisken.

**Blockera nätverksåtkomst via Wi-Fi:**

![Blockera nätverksåtkomst via Wi-Fi](./media/symantec-arch-3.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst](./media/symantec-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket och förhindra synkronisering av företagsfiler baserat på enhetsrisken.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Blockera SharePoint Online när hot identifieras på nätverket](./media/symantec-arch-5.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](./media/symantec-arch-6.png)

## <a name="supported-platforms"></a>Plattformar som stöds

-   **Android 4.1 och senare**

-   **iOS 8 och senare**

## <a name="pre-requisites"></a>Förutsättningar

-   Azure Active Directory Premium

-   Microsoft Intune-prenumeration

-   Symantec Endpoint Protection Mobile-prenumeration

Mer information hittar du på [Symantecs webbplats](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Nästa steg

Här är de steg som du måste utföra om du vill integrera Intune med SEP Mobile:

- [Konfigurera SEP Mobile-integrering med Intune](skycure-mtd-connector-integration.md)

- [Lägg till och tilldela SEP Mobile-appar, Microsoft Authenticator och konfigurationsprincip för iOS-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Skapa SEP Mobile-enhetens efterlevnadsprincip med Intune](mtd-device-compliance-policy-create.md)

- [Aktivera SEP Mobiles MTD-anslutning i Intune](mtd-connector-enable.md)
