---
title: Blockera appar utan modern autentisering i Intune
titleSuffix: Microsoft Intune
description: Läs om blockering av appar som inte använder modern autentisering (ADAL).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf8b323d6f7afa5fc7e3cfecbf04f61e0d11d9c5
ms.sourcegitcommit: 6ff5df63a2fff291d7ac5fed9c51417fe808650d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52167373"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockera appar som inte använder modern autentisering (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Appbaserad villkorlig åtkomst med appskyddsprinciper är beroende av program som använder [modern autentisering](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) som är en implementering av OAuth2. De senaste Office-programmen för mobila och stationära enheter använder modern autentisering. Det finns dock tredjepartsappar och äldre Office-program som använder andra autentiseringsmetoder, som grundläggande autentisering och formulärbaserad autentisering.

Om du vill blockera åtkomst till de här apparna rekommenderar vi följande metoder:

* Konfigurera ADFS-anspråksregler och blockera protokoll som inte stöder modern autentisering. Detaljerade anvisningar finns i scenario tre – [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (blockera all åtkomst till O365 förutom webbläsarbaserade program).
* För **Exchange och SharePoint Online** använder du villkorlig åtkomst i Azure Active Directory och PowerShell-cmdleten Set-SPOTenant för SharePoint Online. Detaljerade anvisningar finns i [Konfigurera SharePoint Online och Exchange Online för villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>Appbaserad CA kan inte användas med Azure Active Directory (Azure AD)-certifikatbaserad autentisering. Du kan endast ha en av dessa konfigurerade åt gången.

### <a name="see-also"></a>Se även
[Appbaserad villkorlig åtkomst med Intune](app-based-conditional-access-intune.md)
