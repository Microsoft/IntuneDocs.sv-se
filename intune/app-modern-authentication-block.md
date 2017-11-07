---
title: Blockera appar utan modern autentisering i Intune
description: 
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6a7cf3b73f4be195b4e07c8c72edeae9fbc9073
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2017
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockera appar som inte använder modern autentisering (ADAL)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Appbaserad villkorlig åtkomst med appskyddsprinciper är beroende av program som använder [modern autentisering](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) som är en implementering av OAuth2. De senaste mobila och stationära Office-programmen använder modern autentisering. Det finns dock tredjepartsappar och äldre Office-program som använder andra autentiseringsmetoder, som grundläggande autentisering och formulärbaserad autentisering.

Om du vill blockera åtkomst till de här apparna rekommenderar vi följande:

* Konfigurera ADFS-anspråksregler och blockera protokoll som inte stöder modern autentisering. Detaljerade anvisningar finns i scenario tre – [block all access to O365 except browser-based applications](https://technet.microsoft.com/library/dn592182.aspx) (blockera all åtkomst till O365 förutom webbläsarbaserade program).
* I **SharePoint Online** inaktiverar du inaktuell autentisering i SharePoint Online-tjänsten med PowerShell-kommandot [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx) för att ange egenskapen för äldre autentiseringsprotokoll till falskt:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>Appbaserad CA kan inte användas med Azure Active Directory (Azure AD)-certifikatbaserad autentisering. Du kan endast ha en av dessa konfigurerade åt gången.

### <a name="see-also"></a>Se även
[Appbaserad villkorlig åtkomst med Intune](app-based-conditional-access-intune.md)
