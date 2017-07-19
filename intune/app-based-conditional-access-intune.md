---
title: "Appbaserad villkorlig åtkomst med Intune"
description: "Förstå hur appbaserad villkorlig åtkomst fungerar med Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0893d511c73e4154c61063d96e26937ea2825467
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="app-based-conditional-access-with-intune"></a>Appbaserad villkorlig åtkomst med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[Intunes appskyddsprinciper](app-protection-policy.md) hjälper dig att skydda företagets data på enheter som är registrerade i Intune. Du kan även använda appskyddsprinciper på medarbetarnas enheter som inte har registrerats för hantering i Intune. Även om ditt företag inte hanterar enheten i det här fallet, måste du fortfarande se till att företagets data och resurser är skyddade.

Appbaserad villkorlig åtkomst och mobil programhantering ger ett extra säkerhetslager genom att kontrollera att endast mobilappar som har stöd för Intunes appskyddsprinciper får åtkomst till Exchange Online och andra Office 365-tjänster.

> [!NOTE]
> En hanterad app är en app som har tillämpade appskyddsprinciper och kan hanteras av Intune.

Du kan blockera inbyggda e-postappar i iOS och Android genom att bara tillåta att Microsoft Outlook-appen får åtkomst till Exchange Online. Dessutom kan du blockera appar där Intunes appskyddsprinciper inte har tillämpats för åtkomst till SharePoint Online.

## <a name="prerequisites"></a>Krav
Innan du skapar en appbaserad princip för villkorlig åtkomst måste du ha:

- **En prenumeration på Enterprise Mobility + Security eller Azure Active Directory Premium** och användarna måste ha licenser för EMS eller Azure AD.
    - Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) eller [sida med priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Appar som stöds

- **Exchange Online**:
    - Microsoft Outlook för Android och iOS.
<br></br>
- **SharePoint Online**
    - Microsoft Word för iOS och Android
    - Microsoft Excel för iOS och Android
    - Microsoft PowerPoint för iOS och Android
    - Microsoft OneDrive för företag för iOS och Android
    - Microsoft OneNote för iOS
<br></br>
- **Microsoft Teams**

    > [!NOTE] 
    > Appbaserad villkorlig åtkomst [stöder också LOB-appar](https://docs.microsoft.com/intune-classic/deploy-use/block-apps-with-no-modern-authentication), men de apparna måste använda [modern autentisering för Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).

## <a name="how-app-based-conditional-access-works"></a>Så här fungerar appbaserad villkorlig åtkomst

I det här exemplet har administratören tillämpat appskyddsprinciper på Outlook-appen, följt av en regel för villkorlig åtkomst som lägger till Outlook-appen i en lista med godkända appar som kan användas för att få åtkomst till företagets e-post.

> [!NOTE] 
> Flödesschemat för strukturen nedan kan användas för andra hanterade appar.

![Appbaserad villkorlig åtkomst med Intunes flödesschema](./media/ca-intune-common-ways-3.png)

1.  Användaren försöker autentisera till Azure AD från Outlook-appen.

2.  Användaren omdirigeras till appbutiken för att installera en koordinatorapp vid försök att autentisera för första gången. Koordinatorappen kan antingen vara Microsoft Authenticator för iOS eller Microsofts företagsportal för Android-enheter.

    > [!NOTE]
    > Om användaren i detta scenario försöker använda den ursprungliga e-postappen kommer en omdirigering ske till appbutiken där Outlook-appen kan installeras.

3.  Koordinatorappen installeras på enheten.

4.  Koordinatorappen startar Azure AD-registreringen som skapar en enhetspost i Azure AD. Detta är inte samma som registreringen vid hantering av mobilenheter (MDM), men den här posten är nödvändig för att principerna för villkorlig åtkomst ska kunna tillämpas på enheten.

5.  Koordinatorappen verifierar appens identitet. Det finns ett säkerhetslager för att koordinatorappen ska kunna verifiera om appen är godkänd att användas av användaren.

6.  Koordinatorappen skickar appens klient-ID till Azure AD som en del av användarens autentiseringsprocess, för att kontrollera om den finns i listan med godkända principer.

7.  Azure AD tillåter att användaren autentiserar och använder appen baserat på listan med godkända principer. Om appen inte finns med i listan med godkända principer nekar Azure AD åtkomst till appen.

8.  Outlook-appen kommunicerar med Outlooks molntjänst för att initiera kommunikation med Exchange Online.

9.  Outlooks molntjänst kommunicerar med Azure AD för att hämta en åtkomsttoken för Exchange Online-tjänsten åt användaren.

10.  Outlook-appen kommunicerar med Exchange Online för att hämta användarens e-post i företaget.

11.  Företagets e-post skickas till användarens postlåda.

## <a name="next-steps"></a>Nästa steg
[Skapa en appbaserad princip för villkorlig åtkomst](app-based-conditional-access-intune-create.md)

[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)
