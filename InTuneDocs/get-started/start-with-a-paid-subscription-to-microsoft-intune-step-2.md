---
title: "Konfigurera ett eget domännamn | Microsoft Docs"
description: "Lägga till ett anpassat domännamn för din Intune-prenumeration"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ad13897fe7bbe4fe13167bb4ce7f558b436a7a90
ms.openlocfilehash: 7e921e3f92b0c9b94e4fdc387513ab5c1627817a


---


# <a name="configure-a-custom-domain-name"></a>Så här konfigurerar du ett eget domännamn

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver hur administratörer kan skapa ett DNS CNAME för att förenkla och anpassa inloggningen.

När organisationen registrerar sig för en molnbaserad tjänst från Microsoft, till exempel Intune, får du ett första domännamn i Azure Active Directory (AD) som ser ut ungefär så här: **dindomän.onmicrosoft.com**. I det här exemplet är **dindomän** det domännamn som du angav när du registrerade dig och **onmicrosoft.com** är det suffix som tilldelas de konton som du lägger till i din prenumeration. Om din organisation äger en anpassad domän kan du konfigurera din instans av Intune att använda den domänen i stället för domännamnet som följer med din prenumeration.

Innan du skapar användarkonton eller synkroniserar Active Directory, rekommenderar vi starkt att du bestämmer om du bara ska använda domänen .onmicrosoft.com eller om du ska lägga till ett eller flera av dina egna domännamn. Att konfigurera en anpassad domän innan du lägger till användare kan underlätta hanteringen av användaridentiteter för prenumerationen, genom att du gör det möjligt för användarna att logga in med de autentiseringsuppgifter de använder för att komma åt andra resurser i domänen.

När du prenumererar på en molnbaserad tjänst från Microsoft blir din instans av den tjänsten en Microsoft [Azure AD-klient](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), som tillhandahåller identitets- och katalogtjänster för din molnbaserade tjänst. Och eftersom stegen för att konfigurera Intune att använda din organisations anpassade domännamn är samma som för andra Azure AD-klienter, kan du använda informationen och procedurerna i [Lägg till din domän](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

> [!TIP]
> Mer information om hur du använder domänen med en molnbaserad tjänst från Microsoft finns i [Översikt över anpassade domännamn i Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/).

Du kan inte byta namn på eller ta bort det inledande domännamnet. Men du kan lägga till, verifiera eller ta bort egna domännamn i Intune, om du till exempel vill använda företagsnamnet.

## <a name="to-add-and-verify-your-custom-domain"></a>Så här lägger du till och verifierar en egen domän

1. Gå till [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx) och logga in på ditt administratörskonto.

2. I navigeringsfönstret väljer du **Inställningar** &gt; **Domäner**.

3. Välj **Lägg till domän** och skriv namnet på din domän.

4. Därmed öppnas dialogrutan **Verifiera domän** som visar värdena för att skapa TXT-posten i din DNS-värdtjänst.
    - **GoDaddy-användare**: Office 365-hanteringsportalen omdirigerar dig till inloggningssidan för GoDaddy. När du har angett dina autentiseringsuppgifter och accepterat avtalet för domänändringsbehörighet skapas TXT-posten automatiskt. Du kan också [skapa en TXT-post](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US) själv.
    - **Register.com-användare**: Följ [instruktionerna](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) för att skapa TXT-posten.

    > [!TIP]
    > Se till att skapa ett DNS-alias (CNAME) för [registrering av Windows-enheter](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) medan du gör ändringar i DNS-värdtjänsten.

Stegen för att lägga till och verifiera en anpassad domän kan också [utföras i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/).

Ta reda på mer [om din första onmicrosoft.com-domän i Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

>[!div class="step-by-step"]

>[&larr; **Logga in i Intune**](.\start-with-a-paid-subscription-to-microsoft-intune-step-1.md)     [**Lägga till användare i Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-3.md)  



<!--HONumber=Feb17_HO3-->


