---
title: Så här konfigurerar du ett eget domännamn
titleSuffix: Microsoft Intune
description: Lägga till ett anpassat domännamn för din Microsoft Intune-prenumeration
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d0c3d11eb3a031f34704dcd9ecf16f3312ac818
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2019
ms.locfileid: "59567250"
---
# <a name="configure-a-custom-domain-name"></a>Så här konfigurerar du ett eget domännamn

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Det här avsnittet beskriver hur administratörer kan skapa ett DNS CNAME för att förenkla och anpassa inloggningen med Microsoft Intune.

När organisationen registrerar sig för en molnbaserad tjänst från Microsoft, till exempel Intune, får du ett första domännamn i Azure Active Directory (AD) som ser ut så här: **din-domän.onmicrosoft.com**. I det här exemplet är **din-domän** det domännamn som du valde när du registrerade dig. **onmicrosoft.com** är det suffix som tilldelas de konton som du lägger till i din prenumeration. Du kan konfigurera och använda din organisations anpassade domän för att ansluta till Intune i stället för domännamnet som du fick med din prenumeration.

Innan du skapar användarkonton eller synkroniserar Active Directory, rekommenderar vi starkt att du bestämmer om du bara ska använda domänen .onmicrosoft.com eller om du ska lägga till ett eller flera av dina egna domännamn. Konfigurera en anpassad domän innan du lägger till användare för att förenkla användarhanteringen. På så sätt kan användarna logga in med de autentiseringsuppgifter som de använder för att komma åt andra resurser i domänen.

När du prenumererar på en molnbaserad tjänst från Microsoft blir din instans av den tjänsten en Microsoft [Azure AD-klient](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), som tillhandahåller identitets- och katalogtjänster för din molnbaserade tjänst. Eftersom stegen för att konfigurera Intune till att använda din organisations anpassade domännamn är samma som för andra Azure AD-klienter kan du använda informationen och procedurerna i [Lägg till din domän](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Mer information om anpassade domäner finns i [Conceptual overview of custom domain names in Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/) (Begreppsbaserad översikt över anpassade domännamn i Azure Active Directory).

Du kan inte byta namn på eller ta bort det första onmicrosoft.com-domännamnet. Du kan lägga till, verifiera eller ta bort anpassade domännamn som används med Intune så att din företagsidentitet alltid är tydlig.

## <a name="to-add-and-verify-your-custom-domain"></a>Så här lägger du till och verifierar en egen domän

1. Gå till [Administrationscenter för Microsoft 365](https://admin.microsoft.com/) och logga in på ditt administratörskonto.

2. I navigeringsfönstret väljer du **Installation** &gt; **Domäner**.

3. Välj **Lägg till domän** och skriv namnet på din domän. Välj **Nästa**.
   ![Skärmbild av Administrationscenter för Microsoft 365, där Inställningar > Domäner har valts och ett nytt domännamn läggs till](./media/domain-custom-add.png)
4. Därmed öppnas dialogrutan **Verifiera domän** som visar värdena för att skapa TXT-posten i din DNS-värdtjänst.
    - **GoDaddy-användare**: Administrationscenter för Microsoft 365 omdirigerar dig till inloggningssidan för GoDaddy. När du har angett dina autentiseringsuppgifter och accepterat avtalet för domänändringsbehörighet skapas TXT-posten automatiskt. Du kan också [skapa en TXT-post](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a) själv.
    - **Register.com-användare**: Följ [de stegvisa instruktionerna](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify) för att skapa TXT-posten.

Stegen för att lägga till och verifiera en anpassad domän kan också [utföras i Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

Ta reda på mer [om din första onmicrosoft.com-domän i Office 365](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)
