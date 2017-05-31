---
title: Blockera appar utan modern autentisering
description: 
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 0f192c0e41cf3b639cbfdac3f8c4fc3b8167266d
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockera appar som inte använder modern autentisering (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

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
[Tillåt endast appar som stöds av Intune att komma åt O365-tjänster](allow-policy-managed-apps-access-to-o365.md)

