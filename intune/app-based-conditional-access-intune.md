---
title: Appbaserad villkorlig åtkomst med Intune
titlesuffix: Microsoft Intune
description: Läs om hur appbaserad villkorlig åtkomst fungerar med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 30f5b902619c84e6d1d193c252e76475d2e54e82
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816745"
---
# <a name="app-based-conditional-access-with-intune"></a>Appbaserad villkorlig åtkomst med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Intunes appskyddsprinciper](app-protection-policy.md) hjälper dig att skydda företagets data på enheter som är registrerade i Intune. Du kan även använda appskyddsprinciper på medarbetarnas enheter som inte har registrerats för hantering i Intune. Även om ditt företag inte hanterar enheten i det här fallet, måste du fortfarande se till att företagets data och resurser är skyddade.

Appbaserad, villkorsstyrd åtkomst och klientapphantering lägger till ett säkerhetslager genom att se till att enbart klientappar som stöder Intunes appskyddsprinciper kommer åt Exchange Online och andra Office 365-tjänster.

> [!NOTE]
> En hanterad app är en app som har tillämpade appskyddsprinciper och kan hanteras av Intune.

Du kan blockera inbyggda e-postappar i iOS och Android genom att bara tillåta att Microsoft Outlook-appen får åtkomst till Exchange Online. Dessutom kan du blockera appar där Intunes appskyddsprinciper inte har tillämpats för åtkomst till SharePoint Online.

## <a name="prerequisites"></a>Krav
Innan du skapar en appbaserad princip för villkorlig åtkomst måste du ha:

- **Enterprise Mobility + Security (EMS)** eller en **Azure Active Directory (AD) Premium-prenumeration**
- Användarna måste ha licens för EMS eller Azure AD

Mer information finns i [Priser för Enterprise Mobility](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) eller [Priser för Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

## <a name="supported-apps"></a>Appar som stöds

En lista över appar som har stöd för app-baserad villkorlig åtkomst finns i [Teknisk referensdokumentation om villkorlig åtkomst för Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)

Appbaserad villkorlig åtkomst [stöder också verksamhetsspecifika appar (LOB)](app-modern-authentication-block.md), men de apparna måste använda [modern autentisering för Office 365](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a). 

## <a name="how-app-based-conditional-access-works"></a>Så här fungerar appbaserad villkorlig åtkomst

I det här exemplet har administratören tillämpat appskyddsprinciper på Outlook-appen, följt av en regel för villkorlig åtkomst som lägger till Outlook-appen i en lista med godkända appar som kan användas för att få åtkomst till företagets e-post.

> [!NOTE]
> Flödesschemat för strukturen nedan kan användas för andra hanterade appar.

![Flödesdiagram över processen för appbaserad villkorlig åtkomst](./media/ca-intune-common-ways-3.png)

1. Användaren försöker autentisera till Azure AD från Outlook-appen.

2. Användaren omdirigeras till appbutiken för att installera en koordinatorapp vid försök att autentisera för första gången. Koordinatorappen kan antingen vara Microsoft Authenticator för iOS eller Microsofts företagsportal för Android-enheter.

   Om användaren försöker använda den ursprungliga e-postappen kommer en omdirigering ske till appbutiken där Outlook-appen kan installeras.

3. Koordinatorappen installeras på enheten.

4. Koordinatorappen startar Azure AD-registreringen som skapar en enhetspost i Azure AD. Detta är inte samma som registreringen vid hantering av mobilenheter (MDM), men den här posten är nödvändig för att principerna för villkorlig åtkomst ska kunna tillämpas på enheten.

5. Koordinatorappen verifierar appens identitet. Det finns ett säkerhetslager för att koordinatorappen ska kunna verifiera om appen är godkänd att användas av användaren.

6. Koordinatorappen skickar appens klient-ID till Azure AD som en del av användarens autentiseringsprocess, för att kontrollera om den finns i listan med godkända principer.

7. Azure AD tillåter att användaren autentiserar och använder appen baserat på listan med godkända principer. Om appen inte finns med i listan nekar Azure AD åtkomst till appen.

8. Outlook-appen kommunicerar med Outlooks molntjänst för att initiera kommunikation med Exchange Online.

9. Outlooks molntjänst kommunicerar med Azure AD för att hämta en åtkomsttoken för Exchange Online-tjänsten åt användaren.

10. Outlook-appen kommunicerar med Exchange Online för att hämta användarens e-post i företaget.

11. Företagets e-post skickas till användarens postlåda.

## <a name="next-steps"></a>Nästa steg
[Skapa en appbaserad princip för villkorlig åtkomst](app-based-conditional-access-intune-create.md)

[Blockera appar som inte har modern autentisering](app-modern-authentication-block.md)
