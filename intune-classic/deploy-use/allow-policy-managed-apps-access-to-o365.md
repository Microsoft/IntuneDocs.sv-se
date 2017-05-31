---
title: "Appbaserad villkorlig åtkomst till 0365"
description: "Förstå hur MAM CA kan hjälpa till med att styra vilka program som har åtkomst till O365-tjänster."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/05/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8fc53e8717277a4075bc7ecde31fd60c3539a5f7
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>Tillåt bara åtkomst till Office 365-tjänster för mobilappar som stöder Intune-principer för appskydd

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Intune-appskyddsprinciper](protect-apps-and-data-with-microsoft-intune.md) hjälper dig att skydda företagets data på enheter som är registrerade för hantering i Intune. Du kan även använda appskyddsprinciper på **medarbetares enheter som inte har registrerats för hantering i Intune**.  Även om du inte hanterar enheten i det här fallet behöver du fortfarande se till att företagets data och resurser är skyddade. Med hjälp av appbaserad villkorlig åtkomst med MAM kan du skapa en princip som endast tillåter att mobila appar som stöder Intunes appskyddsprinciper får åtkomst till O365-tjänster som Exchange Online.

Till exempel kan du genom att bara tillåta **Microsoft Outlook-appen** att få åtkomst till Exchange Online **blockera inbyggda e-postappar på iOS och Android**, som inte har dataskydd från Intune MAM-principer, från att hämta e-post från **Exchange Online**. Du kan också blockera mobilappar som saknar stöd för Intune MAM från åtkomst till **SharePoint Online**.

Diagrammet nedan illustrerar flödet som används av appbaserade principer för villkorlig åtkomst för att avgöra om åtkomst ska tillåtas eller blockeras: ![Diagram som illustrerar de olika kriterierna för att avgöra om åtkomsten ska tillåtas eller blockeras ](../media/mam-ca-decision-flow_simple.png).

Beskrivning av förkortningarna som används i diagrammen:
* **CP**: Företagsportalappen
* **AA**: Azure Authenticator-appen
* **AAD**: Azure Active Directory
* **EAS**: Exchange Active Sync

## <a name="prerequisites"></a>Förutsättningar
**Innan** du kan skapa en appbaserad princip för villkorlig åtkomst måste du ha en **Enterprise Mobility + Security- eller Azure Active Directory Premium-prenumeration**, och användarna måste ha licens för EMS eller Azure AD. Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) eller [sida med priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).


## <a name="supported-apps"></a>Appar som stöds
**Exchange Online**:
* **Microsoft Outlook** för Android och iOS.

**SharePoint Online**
* Microsoft Word för iOS och Android
* Microsoft Excel för iOS och Android
* Microsoft PowerPoint för iOS och Android
* Microsoft OneDrive för företag för iOS och Android
* Microsoft OneNote för iOS

>[!IMPORTANT]
>För Android-enheter måste den initiala enhetsregistreringen utföras genom att logga in på OneDrive-appen eller Outlook-appen. OneNote-appen för Android har ännu inte stöd för MAM utan registrering.

Mer information om användarupplevelsen med en app som har appbaserade principer för villkorlig åtkomst finns i [Vad du kan förvänta dig när du använder en app med MAM CA](use-apps-with-mam-ca.md).


## <a name="next-steps"></a>Nästa steg
[Skapa en Exchange Online-princip för MAM-appar](mam-ca-for-exchange-online.md)

[Skapa en SharePoint Online-princip för MAM-appar](mam-ca-for-sharepoint-online.md)

[Blockera appar som inte har modern autentisering](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Se även

[Skydda appdata med appskyddsprinciper](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

