---
title: "Registrera dig för en 30 dagars kostnadsfri utvärderingsversion"
titleSuffix: Intune on Azure
description: "Så här registrerar du dig för Intune på Azure.\""
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 06/21/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7dafdb974dd975eaa7f3268119de6c047c50f858
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="sign-up-for-a-microsoft-intune-free-trial-for-the-azure-portal"></a>Registrera dig för en kostnadsfri utvärderingsversion av Microsoft Intune i Azure Portal


Den här artikeln vägleder dig genom registreringen av en utvärderingsversion av fristående Intune för Azure Portal.

1. Besök sidan för [Intune-registrering](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20) och fyll i registreringsformuläret för en utvärderingsprenumeration.
account-sign-up.md

  Om de flesta av dina IT-åtgärder och användare använder ett annat språk än du gör, vill du kanske ange detta språk under **Var finns ditt företag?**.

2. I slutet av registreringsprocessen får du ett meddelande med din nya kontoinformation. <br/> ![Bild av kontoinformation](./media/2-end-of-sign-up-process.png) <br/>Om du klickar på **Du är redo att sätta igång**, kommer du till Administrationscenter för Office 365 där du kan lägga till användare i din testmiljö. <br/><br/>Om du i stället vill gå direkt till Intune Azure Portal, öppnar du ett nytt webbläsarfönster och anger **https://portal.azure.com** i adressfältet. Du kommer till Azure-inloggningssidan där du kan använda autentiseringsuppgifterna som du fick för att kunna logga in. Använd den här adressen när du vill logga in på din utvärderingsversion av Intune. <br/> ![Bild av inloggningssidan för Azure-portalen](./media/azure-portal-signin.png)

Första gången du loggar in på Intune Azure Portal, så syns kanske inte Intune på instrumentpanelen i Azure. Lägga till Intune-tjänsten på instrumentpanelen i Azure:
1. Välj **Fler tjänster >** i listan över Azure-tjänster till vänster på instrumentpanelen och skriv **Intune** i sökrutan.
2. Välj **Intune** i listan och markera stjärnan för att lägga till tjänsten i listan över tjänster.<br/> ![Bild som visar val av Intune i en lista över tjänster](./media/azure-add-intune1.png)
3. Välj **Intune** i listan med tjänster som ska öppnas i Intune-instrumentpanelen.

När du registrerar dig för en utvärderingsversion skickas dessutom ett e-postmeddelande med din kontoinformation till den e-postadress som du angav när du registrerade dig. E-postmeddelandet bekräftar att din utvärderingsversion är aktiv.



## <a name="keeping-the-admin-experiences-straight"></a>Hålla ordning på administratörens erfarenheter


Det finns tre portaler som du använder för Intune Azure-portalen:
- Intune-instrumentpanel i Azure ([portal.azure.com](https://portal.azure.com)) där du kan utforska [Intune-funktionerna i Azure-portalen](what-is-intune.md).
- Administrationscenter för Office 365 ([portal.office.com](https://portal.office.com)) där du kan lägga till och hantera användare om du inte använder Azure Active Directory för detta. Du kan också hantera andra delar av ditt konto, inklusive fakturering och support.
- Den klassiska Intune-administratörskonsolen ([manage.microsoft.com](https://manage.microsoft.com)), där du kan utforska funktioner som ännu inte har lagts till i Azure.

Vanligtvis utför du ditt arbete i Intune-instrumentpanelen, som visas nedan. Detta är den plats där du kan konfigurera och hantera grupper, principer, enheter och appar.

Du kan gå till den klassiska Intune-administratörskonsolen från instrumentpanelen genom att välja **Klassisk portal** överst på instrumentpanelen.

Om du vill återgå till Intune Azure Portal skriver du https://portal.azure.com i webbläsarens adressfält och väljer **Intune** igen från listan över tjänster.

 ![Bild av Intune-instrumentpanel](./media/intune-azure-dashboard.png)


Du använder Office 365-administrationscenter (visas nedan) när du ska lägga till och hantera användare och olika kontofunktioner, t.ex. fakturering och support.

![Bild av Office 365-administratörscenter](./media/office-admin-center.png)

Om du vill gå från Office 365-administratörscentret till Intune-instrumentpanelen skriver du in https://portal.azure.com i webbläsarens adressfält. Välj **Intune** i listan över tjänster.

Om du vill gå från Intune tillbaka till Office 365-administratörscentret skriver du in https://portal.office.com i webbläsarens adressfält. Om du är redan inloggad i Intune kommer du direkt till Office 365-administratörscentret.

## <a name="next-steps"></a>Nästa steg

### <a name="intune-on-azure"></a>Intune på Azure
Läs mer om [Intune i Azure Portal](what-is-intune.md)
### <a name="classic-intune"></a>Klassisk Intune
Utvärderingsscenario: [Utvärdera mobilenhetshantering i Microsoft Intune](https://docs.microsoft.com/intune-classic/understand-explore/mobile-device-management-trial-guide-microsoft-intune)

### <a name="integration-with-other-products"></a>Integrering med andra produkter
Lär dig mer om hur du kan använda dina Azure Active Directory-användarkonton med Intune:
- [Identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)
- [Katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)
- [Multifaktorautentiseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

Läs mer om hur du kan använda [Intune med System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/hybrid-mobile-device-management)
