---
title: Ta reda på hur du kan få support för Microsoft Intune
titleSuffix: Microsoft Intune
description: Få online- och telefonsupport för Microsoft Intunes betalda prenumerationer och provprenumerationer.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7fc95d17-098e-4da5-8a09-a96476569dd9
ms.reviewer: srik
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14ff8ad2d41a6f2235c18f155e3a5b865e3a32e4
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199311"
---
# <a name="how-to-get-support-for-microsoft-intune"></a>Ta reda på hur du kan få support för Microsoft Intune

Microsoft tillhandahåller global teknisk, förförsäljnings-, fakturerings- och prenumerationssupport för Microsoft Intune. Support är tillgängligt både online och per telefon för såväl betal- som utvärderingsprenumerationer. Teknisk support online finns på engelska och japanska. Telefonsupport och faktureringssupport online är tillgänglig på fler språk.

Som Intune-administratör kan du använda alternativet **Hjälp och support** för att skicka en supportbegäran online för Intune via Azure-portalen. Om du vill skapa och hantera ett supportärende måste ditt konto ha en roll i Azure Active Directory (Azure AD) som innehåller *åtgärden* **microsoft.office365.supportTickets**. Mer information om de Azure AD-roller och behörigheter som krävs för att skapa ett supportärende finns i avsnittet om [administratörsroller i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles-azure-portal).

>[!IMPORTANT]
> Om du behöver teknisk support för produkter från tredje part som används med Intune (till exempel Saaswedo, Cisco eller Lookout) ska du först kontakta leverantören av produkten. Kontrollera att du har konfigurerat den andra produkten korrekt innan du öppnar ett ärende hos Intune-supporten.
>
> Information om hur du felsöker problem relaterade till Microsoft Intune finns i [felsökningsavsnittet](help-desk-operators.md) i Intune-dokumentationen.


## <a name="help-and-support-experience"></a>Nytt gränssnitt för hjälp och support

Hjälp och support-gränssnittet för Intune är tillgängligt via [Microsoft 365 Enhetshantering-portalen](https://devicemanagement.microsoft.com) och på alla blad (eller sidor) under Intune i Azure-portalen.

*Hjälp och support*gränssnittet liknar det som finns i [Administrationscenter för Microsoft 365](https://admin.microsoft.com/) och ersätter det tidigare *Hjälp + support*, som blir kvar för andra tjänster i Azure.

> [!TIP]
> Från och med 18 november 2019 distribueras en uppdaterad och strömlinjeformad konsolupplevelse för att få hjälp och support. Om den nya upplevelsen inte är tillgänglig för dig än, kommer den att bli det inom kort.

### <a name="options-to-access-help-and-support"></a>Alternativ för att få åtkomst till hjälp och support

- **I Azure Portal:**

  - Välj **Hjälp och support** på valfritt blad eller valfri sida för Intune.

  > [!NOTE]  
  > Om din Intune-instans värdhanteras i det privata molnet för myndigheter (ett nationellt moln som t.ex. Azure Government), kan du läsa om [Intune-stöd för privat moln för myndigheter](#intune-support-for-private-cloud-for-government) senare i den här artikeln. Upplevelsen *Hjälp och support* i Intune blir inte tillgänglig i det privata molnet för myndigheter förrän nästa år.

- **På instrumentpanelen för enhetshantering:**
  - När du har valt ett funktionsområde för Intune väljer du alternativet för **Hjälp och support**.
  - Från valfri nod i portalen Enhetshantering väljer du **?** - ikonen i det övre högra hörnet i portalen och använder sedan listrutan för att välja den tjänst du vill ha hjälp med. **?** - ikonen i portalen Enhetshantering stöder flera tjänster och du måste välja den specifika tjänst du vill ha hjälp med.  

    ![Välj din tjänst](./media/get-support/select-a-service.png)

    När du har valt en tjänst visas sidan *Hjälp och support* för tjänsten. Där kan du ange information om det specifika problem som du vill [hitta lösningar](#find-solutions) för.

    Om resultaten för sökningen inte verkar matcha förväntningarna för tjänsten, kontrollerar du att rätt tjänst har valts. Den valda tjänsten visas precis efter *Hjälp och support*.  Om den rätta tjänsten inte har valts klickar du på *Välj en tjänst* för att återgå till listrutan för val av tjänst.

    ![Bekräfta tjänsten](./media/get-support/confirm-your-service-selection.png)

###  <a name="the-support-experience"></a>Supportupplevelsen

  När du öppnar Hjälp och support visar portalen fönstret **Behöver du hjälp?** :

  ![Visa fönstret Behöver du hjälp?](./media/get-support/need-help.png)

  I det vänstra övre hörnet finns det tre ikoner som du kan använda för att öppna olika rutor i fönstret *Behöver du hjälp?* . Den aktiva rutan visas med understruken text.

  Kunder med ett **Premier** eller **Unified** Support-avtal har [fler alternativ](#premier-and-unified-support-customers) för support och ser en banderoll i *Behöver du hjälp?* som liknar följande bild: ![Premier-banderoll](./media/get-support/premier-banner.png)

  *Behöver du hjälp?* öppnar fönstret *Hitta lösningar*. Om du har ett aktivt supportärende öppnas dock fönstret *Tjänstförfrågningar* där du kan se information om dina aktiva och avslutade supportärenden.

#### <a name="find-solutions"></a>Hitta lösningar

![Välj fönstret Hitta lösningar](./media/get-support/find-solutions.png)

I fönstret *Hitta lösningar* anger du mer information om problemet i textrutan. Utifrån din text om problemet, fylls fönstret med insikter som skulle kunna passa. Du får också länkar till rekommenderade artiklar som kan hjälpa dig att lösa problemet.

När en stark matchning hittas för den information som du beskriver, kan felsökningstips visas direkt i fönstret *Behöver du hjälp?* .

Du kan till exempel skriva **Fel vid lösenordssynkronisering**. Resultaten innehåller felsökningsvägledning direkt i fönstret, samt länkar till rekommenderade artiklar i vårt dokumentationsbibliotek.

![Visa felsökningsinformation](./media/get-support/troubleshooting-insights.png)

#### <a name="contact-support"></a>Kontakta supporten

![Välj fönstret Kontakta supporten](./media/get-support/contact-support.png)

I fönstret *Kontakta supporten* kan du skicka en begäran om hjälp. Det här fönstret visas när du har angett vissa grundläggande nyckelord i rutan *Hitta lösningar*.

När du begär hjälp beskriver du problemet med så mycket information som du kan.  När du har bekräftat din kontaktinformation med ditt telefonnummer och e-postadress, väljer du önskad kontaktmetod. I fönstret visas en svarstid för varje kontaktmetod, så att du vet när du kommer att bli kontaktad. Innan du skickar din begäran bör du bifoga filer som loggar eller skärmbilder som kan vara till hjälp när problemet ska lösas.

![Kontaktformulär för support](./media/get-support/contact-support-form.png)

När du har fyllt i den information som krävs väljer du **Kontakta mig** för att skicka din begäran.

#### <a name="service-requests"></a>Tjänstförfrågningar

![Välj fönstret Tjänstförfrågningar](./media/get-support/service-requests.png)

Ärendehistoriken visas i fönstret *Tjänstförfrågningar*. Aktiva ärenden visas överst i listan, men det går även att se avslutade ärenden.

![Visa en lista med dina tjänstbegäranden](./media/get-support/service-requests-pane.png)

Om du har ett aktivt supportärendenummer kan du ange det här för att gå direkt till problemet. Du kan också välja ett ärende i listan med aktiva och avslutade ärenden för att se mer information.

När du är klar med att se informationen om ett ärende väljer du den vänsterpil som visas längst upp i fönstret Tjänstbegäran precis ovanför de tre ikonerna i rutan *Behöver du hjälp?* . Bakåtpilen tar dig till listan med supportärenden som du har öppnat.

#### <a name="premier-and-unified-support-customers"></a>Premier och Unified Support-kunder

Om du har ett **Premier** eller **Unified** Support-avtal kan du ange en allvarlighetsgrad för ditt problem, samt schemalägga att bli uppringd av supporten en specifik tid och dag. De här alternativen är tillgängliga när du öppnar eller skickar ett nytt problem och när du redigerar ett aktivt supportärende.

**Allvarlighetsgrad** – Vilka alternativ som finns för att ange allvarlighetsgraden för ett problem beror på vilket supportavtal du har:

- *Premier*: Allvarlighetsgrad A, B eller C
- *Unified*: Kritiskt eller icke-kritiskt

Om du väljer allvarlighetsgrad **A** eller **Kritiskt**, blir ärendet ett telefonsupportärende, för att du ska få så snabb hjälp som möjligt.

**Schema för att bli uppringd** – Du kan begära att bli uppringd en speciell dag och tidpunkt.

## <a name="azure-help--support-experience"></a>Hjälp + support-gränssnittet i Azure

Du kan inte längre använda Azure-funktionen *Hjälp och support* för att få hjälp med Intune, såvida inte din prenumeration finns i ett privat moln för myndigheter.
Om din instans av Intune inte körs i ett privat moln för myndigheter och du navigerar genom Azure *Hjälp + support* omdirigeras du till Intune-upplevelsen *Hjälp och support* för att skapa och hantera supportärenden:

När du använder det vänstra navigeringsfönstret **Hjälp + support**, eller använder **?** - för att öppna fönstret *Hjälp* och sedan väljer **Hjälp + support**, öppnas Azure-sidan *Hjälp + support*. 


På den här sidan väljer du **+ Ny supportbegäran** för att öppna fliken *Grundläggande* på sidan *Hjälp + support + Ny support förfrågan*.

![Hjälp + stöd](./media/get-support/help-plus-support.png)

På den här sidan:

- Välj **Teknik** i *Typ av problem*.
- Ange **Microsoft Intune** i *Tjänst*.

  Sedan visas en länk som omdirigerar dig till [hjälp- och supportsidan för Intune](https://aka.ms/intunehelpsupport).
  
  ![Ny supportbegäran](./media/get-support/new-request.png)


## <a name="intune-support-for-private-cloud-for-government"></a>Intune-stöd för privat moln för myndigheter

När din Intune-prenumeration värdhanteras i det privata molnet för myndigheter (ett nationellt moln som t.ex. Azure Government), har du ännu inte åtkomst till den nyare Intune-funktionen Hjälp och support.  Använd istället följande information för att få support för Intune.

### <a name="create-an-online-support-ticket"></a>Skapa en supportbegäran online

>[!IMPORTANT]
> När *Hjälp och support* flyttas till ett nytt system som ännu inte är tillgängligt för det privata molnet för myndigheter gäller att när du skapar ett supportärende så identifierar portalen ett supportärende som använder ett 15-siffrigt ID-nummer. När det 15-siffriga ärendet skapas en spegling av ärendet skapas för användning av Microsoft Support. Det här spegelärendet skapas i ett nytt supportsystem, använder ett 8-siffrigt ärende-ID och används av supporttjänster för att spåra allt arbete och kommunikation för ditt supportärende. Kort efter att det 15-siffriga ärendet har skapats får du ett e-postmeddelande som identifierar det 8-siffriga numret för det speglade supportärendet som används av supporttjänster.
>
> Ge support för personligt arbete och kommunicera från det 8-siffriga supportärendet och använd bara det 8-siffriga supportärendet till att logga kommunikation och spåra ärendeförloppet. Därför får du e-postuppdateringar från det 8-siffriga supportärendet som fungerar som ärendets register. Ingen information loggas i det 15-siffriga supportärendet. När supporten avslutas och det 8-siffriga supportärendet stängs speglas den statusen av det 15 siffriga supportärendet som du kan se via Azure Portal.  Inga andra uppdateringar eller statusändringar ska förväntas för det 15-siffriga supportärendet.
>
> När flytten mellan supportverktyg slutförs senare i år kommer supportgränssnittet med Intune som värd i molnet för myndigheter att likna det standardinställda *Hjälp och support*-gränssnittet som för närvarande är tillgängligt för Intune-prenumerationer som finns i det offentligt molnet.

1. Logga in på Azure Portal (<https://portal.azure.us>) med dina administratörsautentiseringsuppgifter för Intune och välj **?** i det övre högra hörnet i portalen. Välj sedan **Hjälp + support** för att gå till sidan [Azure Hjälp + support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).

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
   > Kunder med privat moln för myndigheter kan bara visa det 15-siffriga supportärendenumret och ärendestatusen. All ärendekommunikation och spårning av arbete eller aviseringar skickas per e-post och refererar till det 8-siffriga supportärendenumret som skapas som en spegling av supportärendet som öppnades i Intune-konsolen.

## <a name="additional-resources"></a>Ytterligare resurser  

- [Support för fakturering och prenumerationer](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)
- [Volymlicensiering](https://go.microsoft.com/fwlink/p/?LinkID=282015)
- [Felsöka Intune-problem](help-desk-operators.md)
