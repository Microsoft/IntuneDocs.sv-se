---
title: Snabbstart – Prova Microsoft Intune utan kostnad
titleSuffix: ''
description: I den här snabbstarten får du skapa en kostnadsfri utvärderingsprenumeration, lära dig om konfigurationer som stöds och krav på nätverk och eventuellt konfigurera ditt domännamn.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/16/2020
ms.topic: quickstart
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1baf0b4273a9074ac7172c08240a8e3c3a9d7fa
ms.sourcegitcommit: 70b40aa4743c8396f8d6a0163893c4a337d67c48
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541123"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>Snabbstart: Prova Microsoft Intune utan kostnad

Microsoft Intune hjälper dig att skydda din arbetskrafts företagsdata genom att hantera enheter och appar. I den här snabbstarten skapar du en kostnadsfri prenumeration för att prova Intune i en testmiljö.

Intune ger hantering av mobilenheter (MDM) och hantering av mobilappar (MAM) från en säker molnbaserad tjänst som administreras med hjälp av administrationscentret för Microsoft Endpoint Manager. Med Intune kan du se till att personalens företagsresurser (data, enheter och appar) är korrekt konfigurerade och uppdaterade, har korrekt åtkomst och uppfyller företagets efterlevnadsprinciper och krav.

## <a name="prerequisites"></a>Krav
Innan du konfigurerar Microsoft Intune, bör du granska följande krav:

- [Operativsystem och webbläsare som stöds](supported-devices-browsers.md)
- [Krav för nätverkskonfiguration och bandbredd](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune

Du kan prova Intune utan kostnad i 30 dagar. Om du redan har ett arbets- eller skolkonto **loggar du in** med det kontot och lägger till Intune i din prenumeration. Annars kan du **registrera dig** för ett nytt konto så att du kan använda Intune i din organisation.

> [!IMPORTANT]
> Du kan inte kombinera ett befintligt arbets- eller skolkonto efter att du har registrerat dig för ett nytt konto.

1. Gå till sidan för [utvärderingsversionen av Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2019088) och Fyll i formuläret.

    ![Skärmbild av webbsidan med kontoregistrering för en utvärderingsversion av Microsoft Intune](./media/free-trial-sign-up/account-sign-up-site-full-browser.png)

    Om de flesta av dina IT-åtgärder och användare använder ett annat språk än du gör, vill du kanske ange detta språk under **Land eller region**. Azure använder din regionala information för att leverera rätt tjänster. Den här inställningen kan inte ändras.

2. Skapa ett konto med företagets namn följt av **.onmicrosoft.com**. 

    ![Skärmbild av ny autentiseringsprocess för Microsoft Intunes konto för kostnadsfri utvärderingsversion](./media/free-trial-sign-up/account-sign-up-site-user-id.png)

    Om ditt företag har sin egen anpassade domän som du vill använda utan **.onmicrosoft.com** kan du ändra valet i administrationscentret för Microsoft 365 enligt beskrivningen senare i artikeln.

3. I slutet av registreringsprocessen får du ett meddelande med din nya kontoinformation.

    ![Bild av din kontoinformation](./media/free-trial-sign-up/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-intune-in-the-microsoft-endpoint-manager"></a>Logga in på Intune i Microsoft Endpoint Manager

Om du inte redan har loggat in på portalen utför du följande steg:

1. Öppna ett nytt webbläsarfönster och ange **https://devicemanagement.microsoft.com** i adressfältet. 
2. Använd det användar-ID som du angav i stegen ovan för att logga in ( *yourID@yourdomain* .onmicrosoft.com).

    ![Bild på inloggningssidan i portalen](./media/free-trial-sign-up/azure-portal-signin.png)

När du registrerar dig för en utvärderingsversion skickas dessutom ett e-postmeddelande med din kontoinformation till den e-postadress som du angav när du registrerade dig. E-postmeddelandet bekräftar att din utvärderingsversion är aktiv.

> [!TIP]
> När du arbetar med Microsoft Endpoint Manager får du kanske bättre resultat om du arbetar med en webbläsare i standardläge, i stället för i privat läge.

## <a name="confirm-the-mdm-authority-in-intune"></a>Bekräfta MDM-utfärdaren i Intune

Som standard ställs MDM-utfärdaren in när du skapar din kostnadsfria utvärderingsversion. Du kan bekräfta att MDM-utfärdaren har ställts in med hjälp av följande steg:

1. Om du inte redan har loggat in loggar du in på Microsoft Endpoint Manager.
2. Klicka på **Klientadministration**.
3. Visa information om klienten. **MDM-utfärdaren** ska vara inställd på **Microsoft Intune**.

Om du när du har loggat in på Microsoft Endpoint Manager visas en orange banderoll som anger att du ännu inte har angett någon MDM-utfärdare kan du aktivera den nu. Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. MDM-utfärdaren måste anges innan användarna kan registrera enheter för hantering.

### <a name="to-set-the-mdm-authority-to-intune-follow-these-steps"></a>Följ dessa steg om du vill ställa in utfärdare för hantering av mobila enheter till Intune:

1. Öppna ett nytt webbläsarfönster och ange **https://portal.azure.com** i adressfältet. 
2. Välj **Alla tjänster** > **Microsoft Intune**.
3. Välj banderollen som anger att du inte har aktiverat enhetshantering, eller välj **Enhetsregistrering** om du inte genast ser popup-meddelandet. Bladet **Välj utfärdare av mobilenhetshantering** visas om du inte har aktiverat enhetshantering än.

    > [!NOTE]
    > Om du har angett MDM-utfärdaren visas värdet för MDM-utfärdaren på bladet **Enhetsregistrering**. Den orangefärgade banderollen visas bara om du inte har angett MDM-utfärdaren än. 

    ![Bild av bladet Välj utfärdare av mobilenhetshantering](./media/free-trial-sign-up/choose-mdm-authority.png) 

4. Om MDM-utfärdare inte har angetts ska du under **Välj utfärdare av mobilenhetshantering** ange **Intune-utfärdare för mobilenhetshantering** som din MDM-utfärdare.

Mer information om MDM-utfärdaren finns i [Ange utfärdare för hantering av mobila enheter](mdm-authority-set.md).

## <a name="configure-your-custom-domain-name-optional"></a>Så här konfigurerar du ditt domännamn (valfritt)

Om ditt företag har sin egen anpassade domän som du vill använda utan **.onmicrosoft.com** kan du ändra valet i administrationscentret för Microsoft 365. Du kan lägga till, verifiera och konfigurera ditt anpassade domännamn med följande steg.  

> [!IMPORTANT]
> Du kan inte byta namn på eller ta bort den *initiala* **onmicrosoft.com**-delen av domännamnet. Däremot kan du lägga till, verifiera eller ta bort *anpassade* domännamn som används med Intune så att din företagsidentitet alltid är tydlig. Mer information finns i avsnittet [Så här konfigurerar du ett eget domännamn](custom-domain-name-configure.md).

1. Gå till [administrationscentret för Microsoft 365](https://admin.microsoft.com) och logga in med ditt administratörskonto.

2. I navigeringsfönstret väljer du **Installation** > **Domäner** > **Lägg till domän**.

3. Skriv ditt eget domännamn. Välj **Nästa**.

   ![Skärmbild av administrationscentret för Microsoft 365 – Lägg till domän](./media/free-trial-sign-up/domain-custom-add.png)

4. Kontrollera att du är ägare till domänen som du angav i det föregående steget. 
    
    Om du väljer att **skicka kod via e-post** skickas ett e-postmeddelande till den registrerade kontakten för din domän. När du har fått e-postmeddelandet kopierar du koden och anger den i fältet som är märkt **Ange verifieringskoden här**. Om verifieringskoden matchar läggs domänen till din klient. E-postmeddelandet som visas kanske inte ser bekant ut. Vissa registratorer dölja den verkliga e-postadressen. E-postadressen kan också vara en annan än den som har angetts när domänen registrerades.

   ![Skärmbild av administrationscentret för Microsoft 365 – Verifiera domän](./media/free-trial-sign-up/domain-custom-verify.png)

   > [!NOTE]
   > TXT-postverifieringsinformation finns i [Skapa DNS-poster för alla DNS-värdtjänster för Office 365](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166).

## <a name="admin-experiences"></a>Administratörsupplevelser

Det finns två portaler som används oftast:
- I administrationscentret för Microsoft Endpoint Manager ([https://devicemanagement.microsoft.com/](https://devicemanagement.microsoft.com/)) kan du utforska [funktionerna i Intune](what-is-intune.md). Det är här som administratören arbetar med Intune.
- I administrationscentret för Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) kan du lägga till och hantera användare om du inte använder Azure Active Directory för detta. Du kan också hantera andra delar av ditt konto, inklusive fakturering och support.

## <a name="next-steps"></a>Nästa steg

I den här snabbstarten skapade du en kostnadsfri prenumeration för att prova Intune i en testmiljö. Mer information om hur du konfigurerar Intune finns i [Konfigurera Intune](setup-steps.md).

Om du vill följa den här serien med Intune-snabbstarter fortsätter du till nästa snabbstart.

> [!div class="nextstepaction"]
> [Snabbstart: Skapa en användare och tilldela en licens till den](quickstart-create-user.md)
