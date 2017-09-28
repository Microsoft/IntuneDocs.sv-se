---
title: Skycure-anslutningsprogram med Intune
titlesuffix: Azure portal
description: Integrering av Skycure-anslutningsprogrammet med Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47df2c4a909c397ac5a6c0f736d11344de44736e
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2017
---
# <a name="skycure-mobile-threat-defense-connector"></a>Skycure Mobile Threat Defense-anslutningsprogram

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Skycure, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune. Risken bedöms utifrån telemetri som samlas in från enheter som kör Skycure och inkluderar:

-   Fysiskt skydd

-   Nätverksskydd

-   Programskydd

-   Skydd mot säkerhetsrisker

Du kan konfigurera principer för villkorlig åtkomst baserat på Skycures riskbedömning. Den aktiveras via Intunes efterlevnadsprinciper för enheter, som du kan använda för att tillåta eller blockera icke-kompatibla enheter för företagets resurser baserat på de hot som har identifierats.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>Hur skyddar Intune och Skycure företagets resurser?

Skycures mobilapp för Android eller iOS avbildar filsystem, nätverksstackar samt telemetri för enheter och program där det är tillgängligt. Detta skickas sedan till Skycures molntjänst som utvärderar enhetens risk för mobila hot.

Intune-enhetens efterlevnadsprincip innehåller en regel för Skycure Mobile Threat Defense, som är baserad på Skycures riskbedömning. När den här regeln är aktiverad utvärderar Intune enhetens efterlevnad med principen som du har aktiverat.

Om enheten utvärderats som inkompatibel kommer åtkomst till resurser som Exchange Online och SharePoint Online blockeras. Användarna av blockerade enheter får anvisningar i Skycures mobilapp för att lösa problemet och återfå åtkomsten till företagets resurser.

Intune stöder två lägen för integrering med Skycure:

-   **Grundinställning** är ett skrivskyddat läge som gör Skycure synligt för enheter i Intune.

-   **Fullständig integrering** tillåter att Skycure rapporterar information om enhetsrisker och säkerhetsincidenter till Intune.

## <a name="sample-scenarios"></a>Exempelscenarier

Nedan visas några vanliga scenarier:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Kontrollera åtkomst baserat på hot från skadliga program

När skadliga program som till exempel skadlig kod upptäckts på enheter kan du blockera enheterna till dess att hotet har åtgärdats:

-   Ansluta till företagets e-post

-   Synkronisera företagets filer med appen OneDrive för arbetet

-   Åtkomst till företagsappar

**Blockera när skadliga appar identifieras:**

![Skadliga appar har identifierats](./media/skycure-arch-1.png)

**Åtkomst beviljad när problemet är löst:**

![Beviljad åtkomst till skadliga appar upptäcktes](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Kontrollera åtkomst baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket, samt skydda åtkomsten till WiFi-nätverk baserat på enhetsrisken.

**Blockera nätverksåtkomst via Wi-Fi:**

![Blockera nätverksåtkomst via Wi-Fi](./media/skycure-arch-3.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Kontrollera åtkomst till SharePoint Online baserat på hot mot nätverket

Identifiera hot, till exempel **Man-in-the-middle**-angrepp i nätverket och förhindra synkronisering av företagsfiler baserat på enhetsrisken.

**Blockera SharePoint Online när hot identifieras på nätverket:**

![Blockera SharePoint Online när hot identifieras på nätverket](./media/skycure-arch-5.png)

**Åtkomst beviljad när problemet är löst:**

![Åtkomst beviljad när problemet är löst för Sharepoint-exempel](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>Plattformar som stöds

-   **Android 4.1 och senare**

-   **iOS 8 och senare**

## <a name="pre-requisites"></a>Förutsättningar

-   Azure Active Directory Premium

-   Microsoft Intune-prenumeration

-   Prenumeration på Skycure Mobile Threat Defense

Mer information hittar du på [Skycures webbplats](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Nästa steg

Här är de steg som du måste utföra om du vill integrera Intune med Skycure:

- [Konfigurera Skycure-integrering med Intune](skycure-mtd-connector-integration.md)

- [Lägg till och tilldela Skycure-appar, Microsoft Authenticator och konfigurationsprincip för iOS-appar](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Skapa Skycure-enhetens efterlevnadsprincip med Intune](mtd-device-compliance-policy-create.md)

- [Aktivera Skycures MTD-anslutning i Intune](mtd-connector-enable.md)
