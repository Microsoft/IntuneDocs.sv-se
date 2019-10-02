---
title: Ta reda på hur du kan få support för Microsoft Intune
titleSuffix: Microsoft Intune
description: Få online- och telefonsupport för Microsoft Intunes betalda prenumerationer och provprenumerationer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c4d40d3f15fe23511f3f15f7c13181a0fa72f6b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726524"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Ta reda på hur du kan få support för Microsoft Intune  

[!INCLUDE [azure_portal](../../intune-classic/includes/note-for-both-portals.md)]  
  
Microsoft tillhandahåller global teknisk, förförsäljnings-, fakturerings- och prenumerationssupport för Microsoft Intune. Support är tillgängligt både online och per telefon för såväl betal- som utvärderingsprenumerationer. Teknisk support online finns på engelska och japanska. Telefonsupport och faktureringssupport online är tillgänglig på fler språk.

Som Intune-administratör kan du använda alternativet **Hjälp och support** för att skicka en supportbegäran online för Intune via Azure-portalen. Om du vill skapa och hantera ett supportärende måste ditt konto ha en roll i Azure Active Directory (Azure AD) som innehåller *åtgärden* **microsoft.office365.supportTickets/tickets/manage**. Mer information om de Azure AD-roller och behörigheter som krävs för att skapa ett supportärende finns i avsnittet om [administratörsroller i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).  

>[!IMPORTANT]  
> Om du behöver teknisk support för produkter från tredje part som används med Intune (till exempel Saaswedo, Cisco eller Lookout) ska du först kontakta leverantören av produkten. Kontrollera att du har konfigurerat den andra produkten korrekt innan du öppnar ett ärende hos Intune-supporten.
>
> Information om hur du felsöker problem relaterade till Microsoft Intune finns i [felsökningsavsnittet](help-desk-operators.md) i Intune-dokumentationen.

## <a name="known-issues-for-creating-support-incidents"></a>Kända problem när supportärenden skapas  

Om ditt konto har behörigheterna som krävs, men inte har åtkomst till Hjälp och support eller kan skapa eller hantera supportärenden, går du igenom följande kända problem och lösningar:  
- Inaktuellt användartoken för ditt konto. Lös problemet genom att logga ut från alla aktiva konsolsessioner, logga in igen och försök sedan skapa eller hantera supportärendet. 
- Flera aktiva sessioner. Om du är inloggad med mer än en användare eller session, loggar du ut alla utom en konsol. När du bara har en enda aktiv session försöker du sedan skapa eller hantera ett supportärende.

Ytterligare åtgärder som kan vara nödvändiga för att lösa åtkomstproblem:
- Rensa alla cookies för din aktiva webbläsarsession och försök sedan skapa eller hantera ett supportärende.
- Använd en InPrivate-session i webbläsaren för att logga in på Intune och försök sedan skapa eller hantera ett supportärende.  

Om ovanstående lösningar inte hjälper, går du till [Administrationscenter för Microsoft 365](https://admin.microsoft.com) och skapar ett supportärende därifrån. Vi arbetar med att ta fram en korrigering som ska vara tillgänglig i slutet av sommaren.  

## <a name="help-and-support-experience"></a>Nytt gränssnitt för hjälp och support  

Hjälp och support-gränssnittet för Intune är tillgängligt via [Microsoft 365 Enhetshantering-portalen](https://devicemanagement.microsoft.com) och på alla blad (eller sidor) under Intune i Azure-portalen. 

![Intune-blad](./media/get-support/intune-blades.png)


*Hjälp och support*gränssnittet liknar det som finns i [Administrationscenter för Microsoft 365](https://admin.microsoft.com/) och ersätter det tidigare *Hjälp + support*, som blir kvar för andra tjänster i Azure. 

Använd följande alternativ för att få åtkomst till Hjälp och support:  
- **Instrumentpanelen för Enhetshantering:**
  - När du har valt ett funktionsområde för Intune väljer du alternativet för **Hjälp och support**.
  - Från valfri nod i portalen Enhetshantering väljer du **?** - ikonen i det övre högra hörnet i portalen och använder sedan listrutan för att välja den tjänst du vill ha hjälp med. **?** - ikonen i portalen Enhetshantering stöder flera tjänster och du måste välja den specifika tjänst du vill ha hjälp med.  

    ![Välj din tjänst](./media/get-support/select-a-service.png)

    När du har valt en tjänst visas sidan *Hjälp och support* för den tjänst där du sedan kan [ange information](#specify-details-about-an-issue) om det specifika problem du vill ha hjälp med.  

    Om resultaten för sökningen inte verkar matcha förväntningarna för tjänsten kontrollerar du att rätt tjänst har valts. Den valda tjänsten visas precis efter *Hjälp och support*.  Om den rätta tjänsten inte har valts klickar du på *Välj en tjänst* för att återgå till listrutan för val av tjänst.   

    ![Bekräfta tjänsten](./media/get-support/confirm-your-service-selection.png) 


- **I Azure Portal:**
  - Välj **Hjälp och support** på valfritt blad eller valfri sida för Intune

  I Azure Portal, om du väljer **?** - ikonen i det övre högra hörnet eller **Hjälp + support** i det vänstra navigeringsfönstret öppnar du *Hjälp + support* för Azure. Från Azure *Help + Support* kan du inte öppna ett Intune-supportärende direkt men du kan komma till Intune *Hjälp och support*-sidan genom att göra följande: 
  1. När Ny supportbegäran.
  2. Ange Teknik i Typ av problem.
  3. Ange Microsoft Intune i Tjänst.
  4. Välj länken Intune Hjälp och support-sida.

> [!NOTE]  
> Om din instans av Intune finns på Government Compute Cloud (GCC), även känt som ett nationellt moln som Azure Government, se Intune-support för Government Compute Cloud, senare i den här artikeln. Gränssnittet *Hjälp och support* i Intune blir inte tillgänglig på GCC förrän senare i år. 


När du öppnar *Hjälp och support* visas i portalen en vy som beror på om du har aktiva supportärenden och, när du har Premier Support, några ytterligare element och alternativ:
- **Inga aktiva supportärenden**: Sidan **Behöver du hjälp?** visas, enligt följande bild på instrumentpanelen för Enhetshantering.  
- **Aktiva supportärenden**: Sidan [Supportärenden](#view-support-cases), som visar listan över dina aktiva ärenden.  
- **Premier Support-kontrakt**: Funktionen är densamma som för de två första alternativen men du ser följande ytterligare element på sidan Behöver du hjälp?: 
  - Efter sidrubriken **Behöver du hjälp?** visas Premier Support-banderollen:  
    ![Premier support-banderoll](./media/get-support/premier-banner.png)
  - I avsnittet **Få support** på sidan kan du ange den första **allvarlighetsgraden** när du skapar en tjänstbegäran per telefon.


![Instrumentpanelen för Enhetshantering och sidan Behöver du hjälp?](./media/get-support/help-support-dashboard.png)

I den här vyn kan du göra följande:

1. [Ange information](#specify-details-about-an-issue) om det specifika problemet du vill ha hjälp med  
2. [Visa sammanhangsberoende hjälp](#view-context-sensitive-help) och relaterade lösningar som baseras på den information som du har angett  
3. [Få support](#get-support) via e-post eller telefon  
4. [Visa supportärenden](#view-support-cases) som du har skapat tidigare med det nya arbetsflödet  

### <a name="specify-details-about-an-issue"></a>Ange information om ett problem 

När du öppnar Hjälp och support från en plats som har stöd av det nya gränssnittet, visas sidan **Behöver du hjälp?** . Du kan ange information om ett problem på den här sidan. När du anger information visar konsolen vanliga frågor baserat på de nyckelord som du använder. Välj ett av förslagen som visas eller skriv en egen problembeskrivning. Om du anger en egen beskrivning väljer du **Få hjälp** för att skicka den. När du har skickat en fråga returnerar konsolen sammanhangsberoende information som kan hjälpa dig att lösa problemet.

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

  > [!NOTE] 
  > E-postbegäranden för support är inte tillgängliga för alla klientorganisationer.  

- För en begäran om support via e-post anger du din e-postadress. Du kan lägga till bifogade filer om du vill. Välj **Skicka** för att skapa begäran. 

  ![E-postbegäran](./media/get-support/email-support.png)
  
- För en begäran om support via telefon anger du ditt telefonnummer. Om du vill kan du även ange din e-postadress och bifoga filer. Välj Ring mig för att skicka begäran.  



   ![Telefonbegäran](./media/get-support/phone-support.png)

**Premier Support**:  
Om du har ett Premier Support-kontrakt har du samma alternativ för att skapa ett telefonsupportärende. Du kan även ange **allvarlighetsgraden** för supportsamtalet och välja att skapa supportbegäran mot ditt Verksamhetskritiskt-kontrakt.  

![Premier Support-alternativ](./media/get-support/premier-phone-support-options.png)


### <a name="view-support-cases"></a>Visa supportärenden  

Välj historikknappen för att visa supportärenden som du har skapat.  

![Visa supportärenden](./media/get-support/view-support-tickets.png)

- Endast supportärenden som du skapar med det nya arbetsflödet visas inifrån det här arbetsflödet. Om du vill visa dem använder du en Hjälp och support-vy från konsolen för Enhetshantering eller via ett Intune-blad i Azure-portalen. Dessa ärenden har nummer som är åtta siffror långa. Du kan också visa dessa ärenden från Administrationscenter för Microsoft 365.  

- Ärenden du har öppnat när du inte använt Hjälp och support-funktionerna i Intune har inte ändrats. Om du vill visa dem måste du använda en Hjälp och support-vy som inte är en del av Intune-gränssnittet eller instrumentpanelen för Enhetshantering. Dessa ärenden har nummer som börjar med **117** eller **118** och är 15 siffror långa. Så här visar du dem:

    1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj *?* i det övre högra hörnet i portalen. Välj sedan *Hjälp + support* för att gå till sidan [Azure Hjälp + support](https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

    2. På sidan **Hjälp + support** kan du visa listan över **nya supportförfrågningar** och välja dem om du vill visa ytterligare information.
 

## <a name="azure-help--support-experience"></a>Hjälp + support-gränssnittet i Azure 

När du använder det vänstra navigeringsfönstret **Hjälp + support**, eller använder **?** - alternativet i det övre högra hörnet i Azure Portal öppnar du Azure Hjälp + support-gränssnittet, som är distinkt från Intune Hjälp och support-gränssnittet.  

Från och med april 2019 kan du inte komma åt Azure *Hjälp + support*-gränssnittet för att få hjälp med Intune, om din prenumeration inte finns på Government Compute Cloud (GCC).  

Om din instans av Intune inte körs på GCC och du navigerar genom Azure *Hjälp + support* omdirigeras du till Intune *Hjälp och support*-gränssnittet för att skapa och hantera supportärenden.  


## <a name="intune-support-for-government-compute-cloud"></a>Intune-support för Government Compute Cloud  

När din Intune-prenumeration som finns på Government Compute Cloud (GCC), som även är känt som ett nationellt moln som Azure Government, har du ännu inte åtkomst till det nyare Intune Hjälp och support-gränssnittet.  Använd istället följande information för att få support för Intune. 


### <a name="create-an-online-support-ticket"></a>Skapa en supportbegäran online 

>[!IMPORTANT]    
> Eftersom *Hjälp och support* flyttas till ett nytt system som ännu inte är tillgängligt för GCC identifierar portalen, när du skapar ett supportärende, ett supportärende som använder en 15-siffrigt ID-nummer. När det 15-siffriga ärendet skapas en spegling av ärendet skapas för användning av Microsoft Support. Det här spegelärendet skapas i ett nytt supportsystem, använder ett 8-siffrigt ärende-ID och används av supporttjänster för att spåra allt arbete och kommunikation för ditt supportärende. Kort efter att det 15-siffriga ärendet har skapats får du ett e-postmeddelande som identifierar det 8-siffriga numret för det speglade supportärendet som används av supporttjänster.  
> 
> Ge support för personligt arbete och kommunicera från det 8-siffriga supportärendet och använd bara det 8-siffriga supportärendet till att logga kommunikation och spåra ärendeförloppet. Därför får du e-postuppdateringar från det 8-siffriga supportärendet som fungerar som ärendets register. Ingen information loggas i det 15-siffriga supportärendet. När supporten avslutas och det 8-siffriga supportärendet stängs speglas den statusen av det 15 siffriga supportärendet som du kan se via Azure Portal.  Inga andra uppdateringar eller statusändringar ska förväntas för det 15-siffriga supportärendet.  
> 
> När flytten mellan supportverktyg slutförs senare i år kommer supportgränssnittet med Intune som värd i molnet för myndigheter att likna det standardinställda *Hjälp och support*-gränssnittet som för närvarande är tillgängligt för Intune-prenumerationer som finns i det offentligt molnet.  


1. Logga in på Azure Portal (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

   ![Bild av länken med frågetecken med länken Hjälp och support markerad](./media/get-support/azure-get-support.png)

2. På sidan **Hjälp och support** i Azure väljer du **Ny supportbegäran**.

   ![Bild av länken Ny supportbegäran markerad på Hjälp och support-sidan](./media/get-support/azure-support-ticket-link.png)

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

>[!IMPORTANT]
>Om du har en fråga om fakturering eller prenumerationer öppnar du ett ärende för att få support via [Administrationscenter för Microsoft 365](https://admin.microsoft.com/Support/SupportEntry.aspx).

### <a name="view-support-requests"></a>Visa supportförfrågningar  

Du kan visa dina supportbegäranden via Azure Portal. Men det finns begränsad information.  Så här visar du dina ärenden: 

1. Logga in i Azure (<https://portal.azure.com>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

2. På sidan **Hjälp + support** kan du visa listan över **Nya supportbegäranden**.

   > [!IMPORTANT]  
   > Government Compute Cloud-kunder kan bara visa det 15-siffriga supportärendenumret och ärendestatusen. All ärendekommunikation och spårning av arbete eller aviseringar skickas per e-post och refererar till det 8-siffriga supportärendenumret som skapas som en spegling av supportärendet som öppnades i Intune-konsolen.   

## <a name="additional-resources"></a>Ytterligare resurser  

- [Support för fakturering och prenumerationer](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volymlicensiering](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Felsöka Intune-problem](help-desk-operators.md)
