---
title: Snabbstart – Prova Microsoft Intune utan kostnad
titlesuffix: ''
description: I den här snabbstarten får du skapa en kostnadsfri utvärderingsprenumeration, lära dig om konfigurationer som stöds och krav på nätverk och eventuellt konfigurera ditt domännamn.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 37445cb2536e02937cf3002dc1cb56ab4b78f12f
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581401"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Snabbstart: Prova Microsoft Intune utan kostnad 

Microsoft Intune hjälper dig att skydda din arbetskrafts företagsdata genom att hantera enheter och appar. I den här snabbstarten skapar du en kostnadsfri prenumeration för att prova Intune i en testmiljö.

Intune ger hantering av mobilenheter (MDM) och hantering av mobilappar (MAM) från en säker molnbaserad tjänst som administreras med hjälp av Microsoft Azure-portalen. Med Intune kan du se till att personalens företagsresurser (data, enheter och appar) är korrekt konfigurerade och uppdaterade, har korrekt åtkomst och uppfyller företagets efterlevnadsprinciper och krav. 

## <a name="prerequisites"></a>Krav
Innan du konfigurerar Microsoft Intune, bör du granska följande krav:

   - [Operativsystem och webbläsare som stöds](supported-devices-browsers.md) 
   - [Krav för nätverkskonfiguration och bandbredd](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune

Du kan prova Intune utan kostnad i 30 dagar. Om du redan har ett arbets- eller skolkonto **loggar du in** med det kontot och lägger till Intune i din prenumeration. Annars kan du **registrera dig** för ett nytt konto så att du kan använda Intune i din organisation.

> [!IMPORTANT]
> Du kan inte kombinera ett befintligt arbets- eller skolkonto efter att du har registrerat dig för ett nytt konto.

1. Gå till sidan för [utvärderingsversionen av Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) och Fyll i formuläret.

    ![Skärmbild av webbsidan med kontoregistrering för en utvärderingsversion av Microsoft Intune](./media/account-sign-up-site-full-browser.png)

    Om de flesta av dina IT-åtgärder och användare använder ett annat språk än du gör, vill du kanske ange detta språk under **Land eller region**. Azure använder din regionala information för att leverera rätt tjänster. Den här inställningen kan inte ändras.

2. Skapa ett konto med företagets namn följt av **.onmicrosoft.com**. 

    ![Skärmbild av webbsidan med kontoregistrering för en utvärderingsversion av Microsoft Intune](./media/account-sign-up-site-user-id.png)

    Om ditt företag har sin egen anpassade domän som du vill använda utan **.onmicrosoft.com** kan du ändra valet i administrationsportalen för Office 365 som beskrivs senare i artikeln.

3. I slutet av registreringsprocessen får du ett meddelande med din nya kontoinformation.

    ![Bild av din kontoinformation](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>Logga in på Azure Portal

1. Öppna ett nytt webbläsarfönster och ange **https://portal.azure.com** i adressfältet. 
2. Använda de autentiseringsuppgifter som du fick i stegen ovan för att logga in.

    ![Bild på inloggningssidan i Azure-portalen](./media/azure-portal-signin.png)

3. Välj **Alla tjänster** på sidopanelen till vänster på sidan för att visa Microsoft Intune i Azure-portalen.
4. Sök efter **Microsoft Intune** i filterrutan och välj den.
5. Markera **stjärnan** för att lägga till Intune längst ned i listan över dina favorittjänster och öppna Intune-kontrollpanelen.

När du registrerar dig för en utvärderingsversion skickas dessutom ett e-postmeddelande med din kontoinformation till den e-postadress som du angav när du registrerade dig. E-postmeddelandet bekräftar att din utvärderingsversion är aktiv.

## <a name="set-the-mdm-authority-to-intune"></a>Ange Intune som utfärdare för hantering av mobila enheter

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.

Följ dessa steg om du vill ställa in utfärdare för hantering av mobila enheter till Intune.

1. Öppna ett nytt webbläsarfönster och ange **https://portal.azure.com** i adressfältet. 
2. Välj **Alla tjänster** > **Microsoft Intune**.
3. Välj den orangefärgade banderollen för att öppna inställningen **Utfärdare av Hantering av mobila enheter**. 

    > [!NOTE]
    > Den orangefärgade banderollen visas bara om du inte har angett MDM-utfärdaren än.

4. Under **Utfärdare av Hantering av mobila enheter** väljer du **Intune som utfärdare av hantering av mobila enheter**.

## <a name="configure-your-custom-domain-name-optional"></a>Så här konfigurerar du ditt domännamn (valfritt)

Om ditt företag har sin egen anpassade domän som du vill använda utan **.onmicrosoft.com** kan du ändra valet i administrationsportalen för Office 365. Du kommer att lägga till, verifiera och konfigurera ditt domännamn.  

> [!IMPORTANT]
> Du kan inte byta namn på eller ta bort det första **onmicrosoft.com**-domännamnet. Du kan lägga till, verifiera eller ta bort anpassade domännamn som används med Intune så att din företagsidentitet alltid är tydlig.

1. Gå till [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx) och logga in på ditt administratörskonto.

2. I navigeringsfönstret väljer du **Installation** > **Domäner** > **Lägg till domän**.

3. Skriv ditt eget domännamn. Välj **Nästa**.

   ![Skärmbild av administrationscenter för Office 365, där Inställningar > Domäner har valts och ett nytt domännamn läggs till](./media/domain-custom-add.png)

4. Kontrollera att du är ägare till domänen som du angav tidigare. 
    
    Om du väljer att **skicka kod via e-post** skickas ett e-postmeddelande till den registrerade kontakten för din domän. När du har fått e-postmeddelandet kopierar du koden och anger den i fältet som är märkt **Ange verifieringskoden här**. Om verifieringskoden matchar läggs domänen till din klient. E-postmeddelandet som visas kanske inte ser bekant ut. Vissa registratorer döljer den verkliga e-postadressen och sedan vad som har angetts när domänen registrerades.

   ![Skärmbild av Administrationscenter för Office 365 – verifiera domännamnet som har lagts till](./media/domain-custom-verify.png)

   > [!NOTE]
   > TXT-postverifieringsinformation finns i [Skapa DNS-poster för alla DNS-värdtjänster för Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Administratörsupplevelser

Det finns två portaler som du kan använda:
- Intune-instrumentpanel i Azure ([portal.azure.com](https://portal.azure.com)) där du kan utforska [Intune-funktionerna](what-is-intune.md). Vanligtvis utför du ditt arbete i Intune-instrumentpanelen.
- Administrationscenter för Office 365 ([portal.office.com](https://portal.office.com)) där du kan lägga till och hantera användare om du inte använder Azure Active Directory för detta. Du kan också hantera andra delar av ditt konto, inklusive fakturering och support.

## <a name="next-steps"></a>Nästa steg

Du har skapat en kostnadsfri prenumeration för att prova Intune i en testmiljö och eventuellt konfigurerat ett anpassat domännamn i den här snabbstarten. Om du vill veta mer om Microsoft Intune kan du fortsätta till nästa snabbstart om att lägga till användare och tilldela licenser.

> [!div class="nextstepaction"]
> [Skapa en användare](get-started-users.md)
