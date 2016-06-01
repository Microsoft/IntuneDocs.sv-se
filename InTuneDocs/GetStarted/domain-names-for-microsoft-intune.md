---
# required metadata

title: Domännamn för Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c3c136f0-330d-432a-a91f-16f7dd097e55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Domännamn för Microsoft Intune

Innan du konfigurerar Microsoft Intune går du igenom det här avsnittet och andra krav som anges i [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)

När organisationen registrerar sig för en molnbaserad tjänst från Microsoft som Intune får du ett första domännamn som ser ut ungefär så här: **contoso.onmicrosoft.com**. I det här exemplet är **contoso** det domännamn som du angav när du registrerade dig och **onmicrosoft.com** är det suffix som tilldelas konton som du lägger till i din prenumeration. Du kan inte ändra domännamnet när du har slutfört registreringsprocessen. Men som global administratör kan du lägga till dina egna anpassade domännamn för din organisation att använda med tjänsten, eller ta bort domäner som du har lagt till tidigare.

Som standard när du använder onmicrosoft-domänen får varje användare som du importerar suffixet **onmicrosoft.com** som UPN (User Principal Name).

Om du vill använda ett domännamn som du äger i stället för det som du fick vid registreringen kan du lägga till domännamnet i Azure Active Directory. När du har lagt till domänen och det har verifierats att du äger den, kan du skapa konton och grupper som innehåller domännamnet genom att ändra DNS-resursposterna hos din DNS-värdtjänst. Om du vill förenkla hanteringen av användarkonton när du planerar att använda en anpassad domän kan du konfigurera ett anpassat domännamn till prenumerationen innan du börjar synkronisera användare från din lokala Active Directory.

Konfiguration av domännamn och DNS-resursposter för Intune görs på samma sätt som för andra Azure Active Directory-klienter. Anvisningar finns i [Lägga till ett anpassat domännamn för att förenkla inloggning med Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/).

### Se även
[Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO2-->


