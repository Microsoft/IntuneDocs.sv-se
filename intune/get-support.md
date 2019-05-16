---
title: Ta reda på hur du kan få support för Microsoft Intune
titleSuffix: Microsoft Intune
description: Få online- och telefonsupport för Microsoft Intunes betalda prenumerationer och provprenumerationer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/05/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: cf1e87d40459d194f2c4aa0ff702a137e45504ab
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569759"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Ta reda på hur du kan få support för Microsoft Intune

[!INCLUDE [azure_portal](./includes/note-for-both-portals.md)]

Microsoft tillhandahåller global teknisk, förförsäljnings-, fakturerings- och prenumerationssupport för Microsoft Intune. Support är tillgängligt både online och per telefon för såväl betal- som utvärderingsprenumerationer. Teknisk support online finns på engelska och japanska. Telefonsupport och faktureringssupport online är tillgänglig på fler språk.

Som Intune-administratör kan du använda alternativet **Hjälp och support** för att skicka en supportbegäran online för Intune via Azure-portalen. Om du vill skapa och hantera ett supportärende måste ditt konto vara tilldelat till en roll i Azure Active Directory (Azure AD) som innehåller *åtgärden* **microsoft.office365.supportTickets/allEntities/allTasks**. Mer information om de Azure AD-roller och behörigheter som krävs för att skapa ett supportärende finns i avsnittet om [administratörsroller i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal). 

**Kända problem när supportärenden skapas**

Om ditt konto har behörigheterna som krävs, men inte har åtkomst till Hjälp och support eller kan skapa eller hantera supportärenden, går du igenom följande kända problem och lösningar:  
- Inaktuellt användartoken för ditt konto. Lös problemet genom att logga ut från alla aktiva konsolsessioner, logga in igen och försök sedan skapa eller hantera supportärendet. 
- Flera aktiva sessioner. Om du är inloggad med mer än en användare eller session, loggar du ut alla utom en konsol. När du bara har en enda aktiv session försöker du sedan skapa eller hantera ett supportärende.

Ytterligare åtgärder som kan vara nödvändiga för att lösa åtkomstproblem:
- Rensa alla cookies för din aktiva webbläsarsession och försök sedan skapa eller hantera ett supportärende.
- Använd en InPrivate-session i webbläsaren för att logga in på Intune och försök sedan skapa eller hantera ett supportärende.  

Om ovanstående lösningar inte hjälper, går du till [Administrationscenter för Microsoft 365](https://admin.microsoft.com) och skapar ett supportärende därifrån. Vi arbetar med att ta fram en korrigering som ska vara tillgänglig i slutet av sommaren. 



>[!IMPORTANT]  
> Om du behöver teknisk support för produkter från tredje part som används med Intune (till exempel Saaswedo, Cisco eller Lookout) ska du först kontakta leverantören av produkten. Kontrollera att du har konfigurerat den andra produkten korrekt innan du öppnar ett ärende hos Intune-supporten.
>
> Information om hur du felsöker problem relaterade till Microsoft Intune finns i [felsökningsavsnittet](help-desk-operators.md) i Intune-dokumentationen.




## <a name="help-and-support-experience"></a>Nytt gränssnitt för hjälp och support
> [!TIP]   
> Det finns en ny hjälp och support för alla klienter. Om du inte ser den här nya funktionen i din klient, kan du prova med att rensa webbläsarens cacheminne och sedan läsa in sidan på nytt.

Hjälp och support-gränssnittet för Intune är tillgängligt via [Microsoft 365 Enhetshantering-portalen](http://devicemanagement.microsoft.com) och på alla blad (eller sidor) under Intune i Azure-portalen. 

![Intune-blad](./media/get-support/intune-blades.png)


Det här nya gränssnittet liknar det som finns i [Administrationscenter för Microsoft 365](https://admin.microsoft.com/) och ersätter de tidigare funktionerna för hjälp och support. 

Använd följande alternativ för att få åtkomst till Hjälp och support:  
- **Instrumentpanelen för Enhetshantering:**
   - Välj ett tillgängligt alternativ för **Hjälp och support**
   - Välj **?**-ikonen i det övre högra hörnet i portalen

- **I Azure-portalen:**
   - Välj **Hjälp och support** på valfritt blad eller valfri sida för Intune

   När du väljer **?**-ikonen i det övre högra hörnet eller **Hjälp + support** i det vänstra navigeringsfönstret på valfri plats i Azure-portalen öppnas *Hjälp + support* för Azure. De bästa funktionerna får du om du använder *Hjälp och support* på Intune-bladet.  

Med det nya gränssnittet får du åtkomst till vyn **Behöver du hjälp?**, som visas i följande bild på instrumentpanelen för Enhetshantering:  
![Instrumentpanelen för Enhetshantering och sidan Behöver du hjälp?](./media/get-support/help-support-dashboard.png)

I den här vyn kan du göra följande:

1. [Ange information](#specify-details-about-an-issue) om det specifika problemet du vill ha hjälp med  
2. [Visa sammanhangsberoende hjälp](#view-context-sensitive-help) och relaterade lösningar som baseras på den information som du har angett  
3. [Få support](#get-support) via e-post eller telefon  
4. [Visa supportärenden](#view-support-cases) som du har skapat tidigare med det nya arbetsflödet  

### <a name="specify-details-about-an-issue"></a>Ange information om ett problem
När du öppnar Hjälp och support från en plats som har stöd av det nya gränssnittet, visas sidan **Behöver du hjälp?**. Du kan ange information om ett problem på den här sidan. När du anger information visar konsolen vanliga frågor baserat på de nyckelord som du använder. Välj ett av förslagen som visas eller skriv en egen problembeskrivning. Om du anger en egen beskrivning väljer du **Få hjälp** för att skicka den. När du har skickat en fråga returnerar konsolen sammanhangsberoende information som kan hjälpa dig att lösa problemet.

Här följer några exempel på frågor som du kan skicka:
  
- *Det går inte att återställa en iOS-enhet*  
- *Det går inte att skapa en princip för villkorlig åtkomst*  

![Ange problemet på sidan Behöver du hjälp?](./media/get-support/describe-the-issue.png)

### <a name="view-context-sensitive-help"></a>Visa sammanhangsberoende hjälp
När du väljer ett av förslagen som visas eller när du skickar en egen fråga visas sammanhangsberoende resultat under **Visa lösningar**. De här resultaten omfattar både Intune-specifik självhjälp och ytterligare resultat som returneras från en webbsökning baserat på frågekriterierna.  
![Visa resultat](./media/get-support/view-results.png)

### <a name="get-support"></a>Få support
Om självhjälpen eller den webbaserade vägledningen inte hjälper dig att lösa problemet kan du använda konsolen för att skapa ett supportärende via e-post eller telefon.  
På sidan **Behöver du hjälp?** väljer du det alternativ som du vill använda.  

- För en begäran om support via e-post anger du din e-postadress. Du kan lägga till bifogade filer om du vill. Välj **Skicka** för att skapa begäran.  

  ![E-postbegäran](./media/get-support/email-support.png)
  
- För en begäran om support via telefon anger du ditt telefonnummer. Om du vill kan du även ange din e-postadress och bifoga filer. Välj Ring mig för att skicka begäran.  

   ![Telefonbegäran](./media/get-support/phone-support.png)

### <a name="view-support-cases"></a>Visa supportärenden
Välj historikknappen för att visa supportärenden som du har skapat.  

![Visa supportärenden](./media/get-support/view-support-tickets.png)

- Endast supportärenden som du skapar med det nya arbetsflödet visas inifrån det här arbetsflödet. Om du vill visa dem använder du en Hjälp och support-vy från konsolen för Enhetshantering eller via ett Intune-blad i Azure-portalen. Dessa ärenden har nummer som är åtta siffror långa. Du kan också visa dessa ärenden från Administrationscenter för Microsoft 365.  

- Ärenden du har öppnat när du inte använt Hjälp och support-funktionerna i Intune har inte ändrats. Om du vill visa dem måste du använda en Hjälp och support-vy som inte är en del av Intune-gränssnittet eller instrumentpanelen för Enhetshantering. Dessa ärenden har nummer som börjar med **117** eller **118** och är 15 siffror långa. Så här visar du dem:

    1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj *?* i det övre högra hörnet i portalen. Välj sedan *Hjälp + support* för att gå till sidan [Azure Hjälp + support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. På sidan **Hjälp + support** kan du visa listan över **nya supportförfrågningar** och välja dem om du vill visa ytterligare information.


## <a name="azure-help--support-experience"></a>Hjälp + support-gränssnittet i Azure
Följande information beskriver Hjälp + support-gränssnittet, som fortfarande är tillgängligt via Azure-portalen när du använder det vänstra navigeringsfönstret **Hjälp + support** eller använd **?**- alternativet i det övre högra hörnet i Azure-portalen. Från och med januari 2019 kan du inte komma åt *Hjälp + support*-gränssnittet i Azure via *Hjälp och support* som finns på Intune-bladen.  

### <a name="create-an-online-support-ticket"></a>Skapa en supportbegäran online

1. Logga in på Azure Portal (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Bild av länken med frågetecken med länken Hjälp och support markerad](./media/azure-get-support.png)

2. På sidan **Hjälp och support** i Azure väljer du **Ny supportbegäran**.

   ![Bild av länken Ny supportbegäran markerad på Hjälp och support-sidan](media/azure-support-ticket-link.png)

3. På fliken **Grundläggande** kan du för de flesta tekniska problem med Intune välja följande alternativ:
   - **Ärendetyp**: **Teknisk**
   - **Prenumeration**: <*din prenumeration*>
   - **Tjänst**: **Microsoft Intune**
   - **Problemtyp**: Välj din typ av problem från den nedrullningsbara menyn.
   - **Undergrupp av problem**: Välj din undergrupp av problem från den nedrullningsbara menyn.
   - **Ämne**: Beskriv kortfattat problemet som du vill ha hjälp med.

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
>Om du har en fråga om fakturering eller prenumerationer öppnar du ett ärende för att få support via [Administrationscenter för Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Visa supportförfrågningar
Du kan visa en supportbegäran via Azure Portal. Så här gör du:

1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. På sidan **Hjälp + support** kan du visa listan över **nya supportförfrågningar** och välja dem om du vill visa ytterligare information.

## <a name="additional-resources"></a>Ytterligare resurser
- [Support för fakturering och prenumerationer](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volymlicensiering](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Felsöka Intune-problem](help-desk-operators.md)
