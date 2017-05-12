---
title: "Registrera dig för en 30 dagars kostnadsfri utvärderingsversion"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Så här registrerar du dig för Intune på Azure."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 01/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: eaddfc647c5e755e6b033a7970e003ce516bba04
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal-preview"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune i Azure-portalens förhandsversion

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Den här artikeln vägleder dig genom registreringen av en utvärderingsversion av fristående Intune för Azure-portalens förhandsversion. <!---and prepares your trial with some users so that you can then follow the associated evaluation guide to see how Intune manages mobile devices. ---> <!---or app data when devices are not enrolled in Intune.--->

<!--- ## Assumptions
This sign-up article and the evaluation guide assume you are using the trial for evaluation purposes only and intend to start with a clean environment when you subscribe.

To make it easy for you to get started with the trial, we are setting up a very simple environment that uses only Intune and assumes it will be your sole method of managing devices (known as the mobile device management authority). However, throughout the guide we will point you to deeper technical content if you want to explore farther.

You can do everything in the trial version that you can do in a subscription version; the only difference is you are limited to 100 user accounts in the trial.--->

<!--- ## Sign up for your trial--->
1. Besök sidan för [Intune-registrering](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) och fyll i registreringsformuläret för en utvärderingsprenumeration.

 <!--- If you have a work or school account and want to use that for your Intune trial, follow [these sign-in instructions](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-1) instead. However, this article assumes that you are not using such an account.---><br/> ![Bild av registreringssidan](./media/1-clicking-try.png)

 > [!TIP]
> Om de flesta av dina IT-åtgärder och användare använder ett annat språk än du gör, vill du kanske ange detta språk under **Var finns ditt företag?**.

2. I slutet av registreringsprocessen får du ett meddelande med din nya kontoinformation. <br/> ![Bild av kontoinformation](./media/2-end-of-sign-up-process.png) <br/>Om du klickar på **Du är redo att sätta igång**, kommer du till Administrationscenter för Office 365 där du kan lägga till användare i din testmiljö. <br/><br/>Om du i stället vill gå direkt till Intune Azure-portalens förhandsversion, öppnar du ett nytt webbläsarfönster och anger **https://portal.azure.com** i adressfältet. Du kommer till Azure-inloggningssidan där du kan använda autentiseringsuppgifterna som du fick för att kunna logga in. Använd den här adressen när du vill logga in på din utvärderingsversion av Intune. <br/> ![Bild av inloggningssidan för Azure-portalen](./media/azure-portal-signin.png)

Första gången du loggar in på förhandsversionen av Intune Azure, kanske inte Intune syns på instrumentpanelen i Azure. Lägga till Intune-tjänsten på instrumentpanelen i Azure:
1. Välj **Fler tjänster >** i listan över Azure-tjänster till vänster på instrumentpanelen och skriv **Intune** i sökrutan.
2. Välj **Intune** i listan och markera stjärnan för att lägga till tjänsten i listan över tjänster.<br/> ![Bild som visar val av Intune i en lista över tjänster](./media/azure-add-intune1.png)
3. Välj **Intune** i listan med tjänster som ska öppnas i Intune-instrumentpanelen.

När du registrerar dig för en utvärderingsversion skickas dessutom ett e-postmeddelande med din kontoinformation till den e-postadress som du angav när du registrerade dig. E-postmeddelandet bekräftar att din utvärderingsversion är aktiv.


<!--- ## Add users
Before you leave the Office 365 Admin center for Intune, you need to add some users to your trial account.

In the Office 365 Admin center, you can add users individually or in bulk by uploading a .csv file. We will do both to set up your trial. However, in your production environment, you will probably want to take advantage of your Azure Active Directory user accounts, which you can learn more about in our [Getting Started guide](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) and in the [Next steps](#Next-steps) section of this article.

### Add an individual user
1. Choose either of the options to add a use to open a form that allows you to create a user. Only the items starred with an asterisk (\*) are required.
![Image of add user button options](./media/sign-up/add-user.png)


2.  When you add the user, the final step will be to send the user an email with their temporary Intune password. For the purposes of this evaluation, use your own work email address so you will receive the log-on information and see the email your users will get. You can then use these user identities to enroll test devices.<br/>

 ![Image of add user final step](./media/sign-up/new-user-2.png)

3. If you want to assign a user an admin role after you create it, you can edit the role in the Office 365 Admin center by selecting the user name from your list of users, and then choosing **Edit** in the Role line to see the list of user roles you can select from and assign to that user.

 ![Image of user  role options](./media/sign-up/change-user-role.png)

### Import multiple users
1. You will find the wizard for importing multiple users in the **More** list.

 ![Image of option to add multiple users](./media/sign-up/add-multiple-users.png)

2. To help you set up your .csv file correctly, you can download a template file to populate with your user data. Download the .csv file that contains headers and sample user information to see exactly the kind of data is needed for each field.

 ![Image of first step in bulk enrollment wizard](./media/sign-up/bulk-enroll-step-1.png)


3. After you’ve created and saved your .csv file, choose **Browse** to select the file. Verify, and choose **Next**. Your users will be uploaded and added to your list of active users.

> [!NOTE]
> Your users won't show up in Intune until they've enrolled a device to be managed.

Now it’s time to head over to Intune to start managing your users, their devices, and their apps.--->

## <a name="keeping-the-admin-experiences-straight"></a>Hålla ordning på administratörens erfarenheter
<!---### Classic Intune
There are two portals you will use for classic Intune:
- The Office 365 Admin center ([portal.office.com](https://portal.office.com))
- The Intune administration console ([manage.microsoft.com](https://manage.microsoft.com))

Normally, you’ll do your work in the Intune administration console, shown below. This is the site where you set up and manage your groups, policies, devices, and apps.

![Image of Intune administration console](./media/sign-up/intune-admin-console.png)

However, you will use the Office 365 Admin center, shown below, to add and manage your users and other aspects of your account, including billing and support.

![Image of Office 365 Admin center](./media/sign-up/office-admin-center.png)

You can navigate from the Office 365 Admin center to the Intune admin console. The admin centers are under the last item in the left navigation pane. Choose **Intune** to open the Intune admin console in a new tab.

![Image of link to Intune administration console](./media/sign-up/link-to-intune.png)

To get from Intune back to the Office 365 Admin center, choose the **Add Users** task on the Groups Overview page.

![Image of link back to Office 365  Admin center](./media/sign-up/task-add-users.png)--->

<!---### Intune Azure preview--->
Det finns tre portaler som du använder för förhandsversionen av Intune Azure:
- Intune-instrumentpanel i Azure ([portal.azure.com](https://portal.azure.com)) där du kan utforska [Intune-funktionerna i Azure-portalen](what-is-microsoft-intune.md).
- Administrationscenter för Office 365 ([portal.office.com](https://portal.office.com)) där du kan lägga till och hantera användare om du inte använder Azure Active Directory för detta. Du kan också hantera andra delar av ditt konto, inklusive fakturering och support.
- Den klassiska Intune-administratörskonsolen ([manage.microsoft.com](https://manage.microsoft.com)), där du kan utforska funktioner som ännu inte har lagts till i Azure.

Vanligtvis utför du ditt arbete i Intune-instrumentpanelen, som visas nedan. Detta är den plats där du kan konfigurera och hantera grupper, principer, enheter och appar.

Du kan gå till klassiska Intune-administratörskonsolen från instrumentpanelen genom att välja panelen **Öppna klassisk Intune-portal**.

Om du vill återgå till förhandsversionen av Intune Azure skriver du in https://portal.azure.com i webbläsarens adressfält och väljer **Intune** igen från listan över tjänster.

 ![Bild av Intune-instrumentpanel](./media/intune-azure-dashboard.png)


Du använder dock Office 365-administrationscenter, som visas nedan, när du ska lägga till och hantera användare och olika kontofunktioner, t.ex. fakturering och support.

![Bild av Office 365-administratörscenter](./media/office-admin-center.png)

Om du vill gå från Office 365-administratörscentret till Intune-instrumentpanelen skriver du in https://portal.azure.com i webbläsarens adressfält. Välj **Intune** i listan över tjänster.

Om du vill gå från Intune tillbaka till Office 365-administratörscentret skriver du in https://portal.office.com i webbläsarens adressfält. Om du är redan inloggad i Intune kommer du direkt till Office 365-administratörscentret.

## <a name="next-steps"></a>Nästa steg

### <a name="intune-azure-preview"></a>Förhandsversion av Intune Azure
Läs mer om [Förhandsgranskning av Intune i Azure-portalen](what-is-microsoft-intune.md)
### <a name="classic-intune"></a>Klassisk Intune
Utvärderingsscenario: [Utvärdera mobilenhetshantering i Microsoft Intune](https://docs.microsoft.com/intune/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>Integrering med andra produkter
Lär dig mer om hur du kan använda dina Azure Active Directory-användarkonton med Intune:
- [Identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Multifaktorautentiseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Läs mer om hur du kan använda [Intune med System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)

