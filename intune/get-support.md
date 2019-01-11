---
title: Så här får du support för Microsoft Intune | Microsoft Intune
description: Få online- och telefonsupport för Microsoft Intunes betalda prenumerationer och provprenumerationer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 6a57a3a26a786e86775ce1509c5f751d2856f95b
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817304"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Ta reda på hur du kan få support för Microsoft Intune

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft tillhandahåller global teknisk, förförsäljnings-, fakturerings- och prenumerationssupport för Microsoft Intune. Support är tillgängligt både online och per telefon för såväl betal- som utvärderingsprenumerationer. Teknisk support online finns på engelska och japanska. Telefonsupport och faktureringssupport online är tillgänglig på fler språk.

>[!IMPORTANT]
> Om du behöver teknisk support för produkter från tredje part som används med Intune (till exempel Saaswedo, Cisco eller Lookout) ska du först kontakta leverantören av produkten. Kontrollera att du har konfigurerat den andra produkten korrekt innan du öppnar ett ärende hos Intune-supporten.
>
> Information om hur du felsöker problem relaterade till Microsoft Intune finns i [felsökningsavsnittet](help-desk-operators.md) i Intune-dokumentationen.

Som IT-administratör kan du använda alternativet **Hjälp + support** för att skicka en supportbegäran online för Intune via Azure Portal. För att du ska kunna skapa en supportbegäran måste ditt konto ha tilldelats någon av följande [administratörsroller i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal):

- Intune-administratör
- Global administratör
- Tjänstadministratör  

## <a name="get-context-sensitive-help"></a>Visa sammanhangsberoende hjälp
När du loggar in på Azure Portal och öppnar Intune kan du välja **Hjälp och support** från valfritt Intune-blad på Azure Portal, samt visa lösningar på vanliga problem för just den delen av Intune.

Om de vanliga lösningarna inte hjälper kan du välja **supportbegäran**. En ny supportbegäran öppnas då på fliken **Grunder** på sidan *Hjälp och support* i Azure. Om du vill fortsätta och skapa en supportbegäran går du till *steg 3* i proceduren [Skapa en supportbegäran online](#create-an-online-support-ticket).

## <a name="create-an-online-support-ticket"></a>Skapa en supportbegäran online

1. Logga in på Azure Portal (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Bild av länken med frågetecken med länken Hjälp och support markerad](./media/azure-get-support.png)

2. På sidan **Hjälp och support** i Azure väljer du **Ny supportbegäran**.

   ![Bild av länken Ny supportbegäran markerad på Hjälp och support-sidan](media/azure-support-ticket-link.png)

3. På fliken **Grundläggande** kan du för de flesta tekniska problem med Intune välja följande alternativ:
   - **Ärendetyp**: **Teknisk**
   - **Prenumeration**: <*din prenumeration*>
   - **Tjänst**: **Microsoft Intune**
   - **Problemtyp**: Välj din typ av problem från den nedrullningsbara menyn.
   - **Undergrupp av problem**: Välj din undergrupp av problem från den nedrullningsbara menyn.
   - **Ämne**: Beskriv kort ditt problem.

   ![Bild av fliken Grunder i Hjälp och support – sidan Ny supportbegäran](./media/get-support/help-new-support-case-basics.png)

   Välj **Nästa: Lösningar** för att fortsätta.
4. På fliken **Lösningar** kan du granska de rekommenderade stegen som kan hjälpa dig lösa problemet utan att skicka in något ärende. Om du fortfarande vill skapa en supportbegäran efter att ha granskat stegen, klickar du på **Nästa: Information**.

   ![Bild av fliken Lösningar i Hjälp och support – sidan Ny supportbegäran](./media/get-support/help-new-support-case-solutions.png)
5. På fliken **Information** fyller du i informationen om ditt problem, supportmetod och din kontaktinformation. Klicka sedan på **Nästa: Granska och skapa**.

   ![Bild av fliken Detaljer i Hjälp och support – sidan Ny supportbegäran](./media/get-support/help-new-support-case-details.png)
6. Granska informationen och kontrollera att den är korrekt. Välj sedan **Skapa** för att skicka din supportbegäran.

   ![Bild av fliken Granskning och skapa på sidan Ny supportbegäran](./media/get-support/help-new-support-case-create.png)

<!--
  - **Support plan**: **Technical support - included** (for Intune technical issues, support is complimentary) or **Premier**
     >[!IMPORTANT]
     >- If you are a **Premier customer** and don't see **Support plan: Premier**, contact your Technical Account Manager for help linking your contract and tenant.
     >- Support for Intune, and for Intune when used with Configuration Manager, is free of charge. To review details of the Premier Support offering, see the [Description of Services](https://enterprise.microsoft.com/en-us/services/services-list/) documentation, section 5.3.3 "Advisory Services."

4. On the **Problem** blade, to make sure your request is addressed by the right subject matter expert for your problem, select the following options:

   - **Severity**
   - **Problem type**
   - **Category**

     These details also let us provide **Related help** that might solve your problem without filing a ticket.

     ![Screenshot of Azure portal help and support page with Problem items filled out and displaying solutions based on your problem](./media/support-need-solutions.png)

     To help the support team research and resolve your problem, enter the following information:
    
   - **Details**
   - **Date**
   - **Time**
   - **Supplemental data**

   Choose **Next**.

5. Provide **Contact information** for this support request. Microsoft support uses this information to contact you.
6. Choose **Create** to submit your support request.
-->
>[!IMPORTANT]
>Om du har en fråga om fakturering eller prenumerationer öppnar du ett ärende för att få support genom [Administrationscenter för Office](https://portal.office.com/Support/SupportEntry.aspx).

## <a name="view-support-requests"></a>Visa supportförfrågningar
Du kan visa en supportbegäran via Azure Portal. Så här gör du:

1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. På sidan **Hjälp + support** kan du visa listan över **nya supportförfrågningar** och välja dem om du vill visa ytterligare information.

## <a name="new-help-and-support-experience"></a>Ny hjälp- och supportupplevelse
*Följande information gäller endast när du använder enhetshanteringsportalen och är en del av distributionen av den nya hjälp- och supportupplevelsen. Deltagare i den här distributionen väljs ut slumpmässigt bland de tillgängliga Intune-klientorganisationerna.*  

Hjälp- och supportuppdateringen för Intune är en ny upplevelse som är tillgänglig på [enhetshanteringsportalen för Microsoft 365](https://devicemanagement.microsoft.com) för vissa men inte alla klientorganisationer. Den här upplevelsen liknar den i [Administrationscenter för Microsoft 365](https://portal.office.com/AdminPortal/Home) och ersätter den tidigare hjälp- och supportupplevelsen vid åtkomst från vissa platser i enhetshanteringskonsolen.  

På enhetshanteringsportalen kommer du åt den nya upplevelsen när du väljer **Hjälp och support** från något av bladen under **Alla tjänster** > **Enhetshantering**, utom bladet **Felsökning**. När du går till hjälp- och supportavsnittet från andra platser, t.ex. från **Felsökning**, via **?**-alternativet längst upp till höger i konsolens banderoll, eller när du väljer **Hjälp och support** från listan med tjänster i den vänstra rutan, så kommer du till den ursprungliga upplevelsen.  

I den nya upplevelsen får du åtkomst till vyn **Behöver du hjälp?**, som visas i följande bild:  
![Instrumentpanelen för Enhetshantering och sidan Behöver du hjälp?](./media/get-support/help-support-dashboard.png)

I den här vyn kan du göra följande:

1. [Ange information](#specify-details-about-an-issue) om det specifika problemet du vill ha hjälp med  
2. [Visa sammanhangsberoende hjälp](#view-context-sensitive-help) och relaterade lösningar som baseras på den information som du har angett  
3. [Få support](#get-support) via e-post eller telefon  
4. [Visa supportärenden](#view-support-cases) som du har skapat tidigare med det nya arbetsflödet  

### <a name="specify-details-about-an-issue"></a>Ange information om ett problem
När du öppnar Hjälp och support från en plats som har stöd av den nya upplevelsen visas sidan  Behöver du hjälp? Du kan ange information om ett problem på den här sidan. När du anger information visar konsolen vanliga frågor baserat på de nyckelord som du använder. Du kan välja ett av förslagen som visas eller skriva en egen problembeskrivning. Om du anger en egen beskrivning väljer du **Få hjälp** för att skicka den. När du har skickat en fråga returnerar konsolen sammanhangsberoende information som kan hjälpa dig att lösa problemet.

Här följer några exempel på frågor som du kan skicka:
  
- *Det går inte att återställa en iOS-enhet*  
- *Det går inte att skapa en princip för villkorlig åtkomst*  

![Ange problemet på sidan Behöver du hjälp?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Visa sammanhangsberoende hjälp
När du väljer ett av förslagen som visas eller när du skickar en egen fråga visas sammanhangsberoende resultat under **Visa lösningar**. De här resultaten omfattar både Intune-specifik självhjälp och ytterligare resultat som returneras från en webbsökning baserat på frågekriterierna.  
![Bild av fönstret Visa resultat](./media/get-support/view-results.png)

### <a name="get-support"></a>Få support
Om självhjälpen eller den webbaserade vägledningen inte hjälper dig att lösa problemet kan du använda konsolen för att skapa ett supportärende för e-post eller telefon.  
På sidan **Behöver du hjälp?** väljer du det alternativ som du vill använda.  

- För en begäran om support via e-post anger du din e-postadress. Du kan lägga till bifogade filer om du vill. Välj **Skicka** för att skapa begäran.  

  ![Bild av fönstret E-postbegäran](./media/get-support/email-support.png)
  
- För en begäran om support via telefon anger du ditt telefonnummer. Om du vill kan du även ange din e-postadress och bifoga filer. Välj Ring mig för att skicka begäran.  

   ![Bild av fönstret Telefonbegäran](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>Visa supportärenden
Välj historikknappen för att visa supportärenden som du har skapat.  

![Bild av fönster Visa supportfall](./media/get-support/view-support-tickets.png)

- Endast supportärenden som du skapar med det nya arbetsflödet visas inifrån det här arbetsflödet. Om du vill visa dem använder du en hjälp- och supportvy från enhetshanteringskonsolen som hör till den nya upplevelsen. Dessa ärenden har nummer som är åtta siffror långa. Du kan också visa dessa ärenden från Administrationscenter för Microsoft 365.  

- Ärenden som du skapade innan ditt konto lades till i den nya hjälp- och supportupplevelsen ändras inte. För att visa dem måste du använda en hjälp- och supportvy som inte hör till den nya upplevelsen. Dessa ärenden har nummer som börjar med **117** eller **118** och är 15 siffror långa.  Om du vill visa ett supportärende som skapades innan du lades till i den nya upplevelsen använder du Azure-portalen. Så här gör du:

    1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj *?* i det övre högra hörnet i portalen. Välj sedan *Hjälp + support* för att gå till sidan [Azure Hjälp + support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. På sidan **Hjälp + support** kan du visa listan över **nya supportförfrågningar** och välja dem om du vill visa ytterligare information.

## <a name="additional-resources"></a>Ytterligare resurser
- [Kontakta telefonsupporten för Microsoft Intune](phone-support-contact.md)
- [Support för fakturering och prenumerationer](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volymlicensiering](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Felsöka Intune-problem](help-desk-operators.md)