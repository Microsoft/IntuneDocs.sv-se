---
title: "Domännamn för Microsoft Intune | Microsoft Intune"
description: "Lägga till domännamn för Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: swadhwa
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 38159f6dbcae2eeb4dca47141e60eed12cd7f6ee
ms.openlocfilehash: abcf37e7ec3150b5a2fe4cda910631f83d4c510a


---



# Anpassade domännamn med Microsoft Intune

När organisationen registrerar sig för en molnbaserad tjänst från Microsoft, till exempel Intune, får du ett första domännamn i Azure Active Directory som ser ut ungefär så här: **dindomän.onmicrosoft.com**. I det här exemplet är **dindomän** det domännamn som du angav när du registrerade dig och **onmicrosoft.com** är det suffix som tilldelas de konton som du lägger till i din prenumeration.

Du kan inte byta namn på eller ta bort det inledande domännamnet. Men du kan lägga till, verifiera eller ta bort egna domännamn i Intune, om du till exempel vill använda företagsnamnet.

## Så här lägger du till och verifierar en egen domän 

1. Gå till [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx) och logga in på ditt administratörskonto.

2. I navigeringsfönstret väljer du **Inställningar** &gt; **Domäner**.

3. Välj **Lägg till domän** och skriv namnet på din domän.

4. Därmed öppnas dialogrutan **Verifiera domän** som visar värdena för att skapa TXT-posten i din DNS-värdtjänst.
    - **GoDaddy-användare**: Office 365-hanteringsportalen omdirigerar dig till inloggningssidan för GoDaddy. När du har angett dina autentiseringsuppgifter och accepterat avtalet för domänändringsbehörighet skapas TXT-posten automatiskt. Du kan också [skapa en TXT-post](https://support.office.com/en-us/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a?ui=en-US&rs=en-US&ad=US) själv.
    - **Register.com-användare**: Följ [instruktionerna](https://support.office.com/en-us/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e?ui=en-US&rs=en-US&ad=US#BKMK_verify) för att skapa TXT-posten.

    > [!TIP] 
    > Se till att skapa ett DNS-alias (CNAME) för [registrering av Windows-enheter](/Intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) medan du gör ändringar i DNS-värdtjänsten.

Stegen för att lägga till och verifiera en anpassad domän kan också [utföras i Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-add-domain/).

I ett scenario med hybridmoln kan du fortsätta att hantera användarkonton i din lokala Active Directory efter att du har lagt till ditt domännamn och det har verifierats att din organisation äger domänen. Sedan kan du synkronisera domänen med Azure AD.

## Så här synkroniserar du lokala användare med Azure AD##

1. [Lägg till UPN-suffixet](https://technet.microsoft.com/en-us/library/cc772007.aspx) för din egna domän i din lokala Active Directory.
2. Ange det nya UPN-suffixet för de lokala användare som du tänker importera.
3. Kör [Azure AD Connect-synkronisering](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) för att integrera dina lokala användare med Azure AD.
4. När informationen om användarkontot har synkroniserats kan du tilldela Microsoft Intune-licenser med [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).

### Se även

[Om din första onmicrosoft.com-domän i Office 365](https://support.office.com/en-us/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A?ui=en-US&rs=en-US&ad=US)

[Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


