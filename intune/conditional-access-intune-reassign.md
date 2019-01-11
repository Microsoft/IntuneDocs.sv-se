---
title: Migrera villkorlig åtkomst till Azure-portalen | Microsoft Intune
description: Gör en ny tilldelning av de villkorliga åtkomstprinciper som du skapade tidigare i den klassiska Intune-portalen till Azure-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d319ff39574565c3f326bd6b03b346e989bdc488
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53817440"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Gör om tilldelningen av principer för villkorlig åtkomst från den klassiska Intune-portalen till Azure-portalen

Med början i den nya Azure-portalen kan villkorlig åtkomst tillhandahålla stöd för fler principer per app och fler anpassningsmöjligheter. Om du tidigare skapade villkorliga åtkomstprinciper i den klassiska Intune-portalen, kan du migrera dem till Azure-portalen. 

## <a name="before-you-begin"></a>Innan du börjar

Om du är redo att gå över till Azure-portalen följer du stegen i det här avsnittet för att tilldela om de principer för villkorlig åtkomst som du skapade tidigare i den klassiska Intune-portalen:

- Samla in information om de principer för villkorlig åtkomst som du skapade tidigare så att du vet vilka inställningar du måste göra om senare.

- Följ stegen i detta avsnitt om du vill skapa dessa principer på nytt i Azure-portalen.

- Kontrollera att de nya principerna fungerar som förväntat i Azure-portalen innan du inaktiverar villkorsprinciperna i den klassiska Intune-portalen.
<br /><br />
    - **Innan du inaktiverar** principer för villkorlig åtkomst i den klassiska Intune-portalen måste du göra upp en plan för hur användarna ska flyttas över till den nya principen. Det finns två sätt:
<br /><br />
        - **Använda samma inkluderingsgrupp för att tillämpa principer som skapats i Azure-portalen och skapa en ny exkluderingsgrupp för att tillämpa principer som skapats i den klassiska Intune-portalen**.
            - Flytta några användare i taget till exkluderingsgruppen som angetts i den klassiska portalen. På så sätt hindrar du principer från den klassiska Intune-portalen att tillämpas. Principerna som har skapats och riktats mot samma användargrupp i Azure-portalen tillämpas, utöver de som tillämpas utifrån den klassiska Intune-portalen. 
<br /><br />
        - **Skapa en ny grupp som riktar in sig på principerna för villkorlig åtkomst i Azure-portalen**. Om du väljer den här metoden kan du behöva göra följande:
            - Ta bort några användare i taget från säkerhetsgrupper som har villkorliga åtkomstprinciper från den klassiska Intune-portalen.
            - Kontrollera att den nya principen fungerar för de här användarna innan du inaktiverar principen i den klassiska Intune-portalen. 
<br /><br />
- Om principen för villkorlig åtkomst är inställd på att använda Exchange Active Sync (EAS) i den klassiska Intune-portalen kan du läsa [anvisningarna i det här avsnittet](#reassign-intune-device-based-conditional-access-policies-for-eas-clients) för att ta reda på **hur man gör om tilldelningen av principer för villkorlig åtkomst med EAS i Azure-portalen**.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Så här gör du för att kontrollera principerna för enhetsbaserad villkorlig åtkomst i den klassiska Intune-portalen

1.  Gå till den [klassiska Intune-portalen](https://manage.microsoft.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Princip** i den vänstra menyn.

3.  Välj **Villkorlig åtkomst** och sedan den molntjänst från Microsoft (t.ex. Exchange Online eller SharePoint Online) du har skapat en princip för villkorlig åtkomst för.

4.  Anteckna inställningarna för villkorlig åtkomst och använd dessa som referens när du ska återskapa samma principer för villkorlig åtkomst i Azure-portalen.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>App- och enhetsbaserade principer för villkorlig åtkomst i samverkan

På bladet **Intune-appskydd** i Azure-portalen kan administratörer ange appbaserade villkorsregler så att endast appar som stöder Intunes principer för appskydd ges tillgång till företagets resurser. Du kan välja att överlappa de appbaserade principerna för villkorlig åtkomst med hjälp av enhetsbaserade principer för villkorlig åtkomst. Du kan kombinera de enhetsbaserade och de appbaserade villkorsprinciperna (logiskt AND) eller ange ett alternativ (logiskt OR). Om dina krav för princip för villkorlig åtkomst är följande:

- Kräver en kompatibel enhet **OCH** användning av godkänd app.
    - Konfigurera principer för villkorlig åtkomst med hjälp av [bladet för villkorlig åtkomst via Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) och [bladet för Intune-appskydd](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).
<br /><br />
- Kräver en kompatibel enhet **ELLER** användning av godkänd app.
    - Konfigurera principer för villkorlig åtkomst med hjälp av [den klassiska Intune-portalen](https://manage.microsoft.com) och [bladet Intune-appskydd](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0).

> [!TIP] 
> Det här avsnittet innehåller skärmbilder som du kan använda för att jämföra användarupplevelsen i den klassiska Intune-portalen med Azure-portalen.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Göra om tilldelning av enhetsbaserade principer för villkorlig åtkomst i Intune

1. Gå till [Villkorlig åtkomst i Azure-portalen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) och logga in med dina autentiseringsuppgifter.

2. Välj **Ny princip**.

3. Ange ett namn för principen.

4. Välj **Användare och grupper** under avsnittet **Tilldelningar** och ange den nya principen för villkorlig åtkomst.
    
    ![Bild med jämförelse av användargruppsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > Det val du gör för Azure Portal bör motsvara det val du har gjort för den klassiska portalen. Om du till exempel har valt alla användare i den klassiska Intune-portalen väljer du **Alla användare** i Azure-portalen. Om du dessutom har valt alternativet **Undanta grupper** i den klassiska Intune-portalen ska du även exkludera dessa grupper i Azure-portalen.

5. När du har valt gruppen klickar du på **Välj** och sedan på **Klar**.

6. Välj **Molnappar** i avsnittet **Tilldelningar**.

7. Välj **Välj appar** på bladet **Molnappar**.

8. Välj den app som du vill tillämpa den nya principen för villkorlig åtkomst på och klicka på **Välj**.

9. Klicka på **Klar**.

    ![Bild med jämförelse av molnappsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-3.png)

    > [!TIP] 
    > Om du har flera appar med samma princip kan du överväga att konsolidera dem till en enda princip i Azure-portalen.

10. Välj **Villkor** i avsnittet **Tilldelningar**.

11. På bladet **Villkor** väljer du **Enhetsplattformar** och sedan de tillämpliga enhetsplattformarna.

12. När du har valt enhetsplattformar klickar du på **Klar** två gånger.

    ![Bild med jämförelse av enhetsplattformsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-4.png)

    > [!TIP] 
    > Om du har valt individuella plattformar i den klassiska Intune-portalen måste du även välja individuella plattformar i Azure-portalen.

    > [!NOTE] 
    > Du kan vänta med att ange domänanslutning och kompatibilitetsalternativ för Windows till ett senare tillfälle.

13. Välj **Villkor** i avsnittet **Tilldelningar**.

14. På bladet **Villkor** väljer du **Klientappar** och sedan en klientapp.

15. När du har valt klientapp klickar du på **Klar** två gånger.

    ![Bild med jämförelse av klientappsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-6.png)

16. Om du har valt webbläsarinställningar i den klassiska Intune-portalen måste du välja både **webbläsare** och **mobilappar och skrivbordsklienter** i Azure-portalen. Om du inte har valt webbläsarinställningar i den klassiska Intune-portalen kan du endast välja **mobilappar och skrivbordsklienter**. 

17. Välj **Bevilja** i avsnittet **Åtkomstkontroller**.

18. Välj **Kräv att enheten är markerad som kompatibel** under **Grant Access Controls** (Bevilja åtkomstkontroller) och klicka sedan på **Välj**.

19. Om du har en princip som kräver att domänanslutna Windows-enheter används och tillåter Windows-enheter som är registrerade och kompatibla med Intune, väljer du **Kräv domänansluten enhet** och **Kräv att enheten är markerad som kompatibel** tillsammans med **Begär en av de valda kontrollerna**.

20. Om du inte tillåter Windows-enheter som är registrerade och kompatibla med Intune ska du undanta Windows-principen från den aktuella principen. Skapa sedan en separat princip där **Enhetsplattform** har inställningen **Windows**, använder samma villkor som ovan i övrigt och väljer **Kräv domänansluten enhet** under **Grant Access Controls** (Bevilja åtkomstkontroller).

21. Aktivera **Aktivera principen** på bladet för den **nya** principen för villkorlig åtkomst. Klicka på **Skapa**.

    ![Jämförelse av gränssnitt för aktivering av villkorlig åtkomstprincip i Intune- och Azure-portalerna](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>Gör om tilldelningen av enhetsbaserade principer för villkorlig åtkomst i Intune för EAS-klienter

Om du har konfigurerat inställningar för Exchange Active Sync som en del av en Exchange Online-princip i den klassiska Intune-portalen, måste du skapa en andra princip för villkorlig åtkomst i Azure-portalen.

1. Gå till [Villkorlig åtkomst i Azure-portalen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) och logga in med dina autentiseringsuppgifter.

2. Välj **Ny princip**.

3. Ange ett namn för principen.

4. Välj **Användare och grupper** under avsnittet **Tilldelningar** och ange den nya principen för villkorlig åtkomst.

    ![Bild som visar en jämförelse av en användargrupps användargränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Det val du gör för Azure-portalen bör motsvara det val du har gjort för Azure-portalen. Om du till exempel har valt alla användare i den klassiska Intune-portalen väljer du **Alla användare** i Azure-portalen. Om du dessutom har valt alternativet **Undanta grupper** i den klassiska Intune-portalen ska du även exkludera dessa grupper i Azure-portalen.

5. När du har valt gruppen klickar du på **Välj** och sedan på **Klar**.

6. Välj **Molnappar** i avsnittet **Tilldelningar**.

7. På bladet **Molnappar** klickar du på **Välj appar** och väljer **Exchange Online**. Klicka sedan på **Välj** och **Klar**.

    ![Bild med jämförelse av molnappsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > Principer för villkorlig åtkomst för EAS-klienter får inte inkludera några andra molnappar.

8. På bladet **Villkor** väljer du **Klientappar** och sedan en klientapp. Om du har valt att blockera klienter som inte stöds av Intune väljer du alternativet **Tillämpa bara principen på plattformar som stöds**.

    ![Bild som visar en jämförelse av klientappsgränssnitt i Intune- och Azure-portalerna](./media/reassign-ca-15.png)

9. När du har valt klientapp klickar du på **Klar** två gånger.

10. Välj **Bevilja** i avsnittet **Åtkomstkontroller**.

11. Välj **Kräv att enheten är markerad som kompatibel** under **Grant Access Controls** (Bevilja åtkomstkontroller) och klicka sedan på **Välj**.

    ![Bild med jämförelse av gränssnitt för att bevilja åtkomst i Intune- och Azure-portalerna](./media/reassign-ca-16.png)

12. Aktivera **Aktivera principen** på bladet för den **nya** principen för villkorlig åtkomst. Klicka på **Skapa**.

    ![Jämförelse av gränssnitt för aktivering av villkorlig åtkomstprincip i Intune- och Azure-portalerna](./media/reassign-ca-17.png)

> [!NOTE]
> Om du konfigurerar **Enhetsplattformar** kommer principen inte att sparas och felmeddelandet ”Principkonfigurationen stöds inte” visas. Exchange ActiveSync kan inte identifiera vilken plattform som används av den anslutande enheten. Därför stöds inte konfiguration av specifika enhetsplattformar när du skapar en princip för Exchange ActiveSync-enheter.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Inaktivera principer för villkorlig åtkomst i den klassiska Intune-portalen

När du har gjort om tilldelningen av principer för villkorlig åtkomst i Azure-portalen är det viktigt att gradvis inaktivera de principer för villkorlig åtkomst som du skapat tidigare i den klassiska Intune-portalen. Du kan dessutom behöva använda samma säkerhetsgrupp för att tillämpa principer för villkorlig åtkomst som skapats i Azure-portalen.

> [!NOTE]
> Läs igenom avsnittet [Innan du börjar](#before-you-begin) innan du inaktiverar dina principer för villkorlig åtkomst i den klassiska Intune-portalen.

### <a name="to-disable-the-conditional-access-policies"></a>Så här inaktiverar du principer för villkorlig åtkomst

1.  Gå till den [klassiska Intune-portalen](https://manage.microsoft.com) och logga in med dina autentiseringsuppgifter.

2.  Välj **Princip** i den vänstra menyn.

3.  Välj **Villkorlig åtkomst** och sedan den molntjänst från Microsoft (t.ex. Exchange Online eller SharePoint Online) som du har skapat en princip för villkorlig åtkomst för.

4.  Avmarkera alternativet **Aktivera princip för villkorlig åtkomst** och klicka på **Spara**.

    ![Bild av Inaktivera principer för villkorlig åtkomst i den klassiska Intune-portalen](./media/reassign-ca-18.png)

## <a name="see-also"></a>Se även

- [Vanliga sätt att använda villkorlig åtkomst på med Intune](conditional-access-intune-common-ways-use.md)
- [appbaserad villkorsstyrd åtkomst med Intune](app-based-conditional-access-intune.md)
- [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
