---
title: Genomgång – Skapa administrativa mallar i Microsoft Intune – Azure | Microsoft Docs
description: Den här självstudien eller genomgången använder Microsoft Intune för att konfigurera ADMX-mallar för Office, Windows och Microsoft Edge på Windows 10 och nyare enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688096"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Självstudie: Använd molnet för att konfigurera grupprinciper på Windows 10-enheter med ADMX-mallar och Microsoft Intune

> [!NOTE]
> Den här självstudien skapades som en teknisk studiegrupp för Microsoft Ignite. Den har fler förutsättningar än de flesta självstudier eftersom den jämför användning av och konfiguration av ADMX-principer i Intune och lokalt.

Administrativa mallar för grupprinciper, som även kallas ADMX-mallar, innehåller inställningar som du kan konfigurera på Windows 10-enheter, däribland datorer. Inställningarna för ADMX-mallar är tillgängliga via olika tjänster. De här inställningarna används av MDM-leverantörer (Mobile Device Management, hantering av mobilenheter), inklusive Microsoft Intune. Du kan till exempel aktivera Designidéer i PowerPoint, ange en startsida i Microsoft Edge, blockera ActiveX-kontroller i Internet Explorer med mera.

ADMX-mallar är tillgängliga för följande tjänster:

- **Microsoft Edge**: Ladda ned på [Microsoft Edge-principfil](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office**: Ladda ned på [Office 365 ProPlus, Office 2019 och Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows**: Inbyggt i operativsystemet Windows 10.

Mer information om ADMX-principer finns i [Förstå ADMX-stödda principer](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

I Microsoft Intune är de här mallarna inbyggda i Intune-tjänsten och är tillgängliga som profiler med **administrativa mallar**. I den här profilen konfigurerar du de inställningar som du vill inkludera och ”tilldelar” sedan den här profilen till dina enheter.

I de här självstudierna får du:

> [!div class="checklist"]
> * En introduktion till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
> * Skapa användargrupper och enhetsgrupper.
> * Jämföra inställningarna i Intune med lokala ADMX-inställningar.
> * Skapa olika administrativa mallar och konfigurera de inställningar som är riktade mot de olika grupperna.

I slutet av den här labbuppgiften har du kunskaper för att komma igång med Intune och Microsoft 365 för att hantera dina användare samt distribuera administrativa mallar.

Den här funktionen gäller för:

- Windows 10-version 1703 och senare

## <a name="prerequisites"></a>Krav

- En Microsoft 365 E3- eller E5-prenumeration, som innefattar Intune och Azure Active Directory (AD) Premium. Om du inte har en E3- eller E5-prenumeration kan du [prova utan kostnad](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  Mer information om vad du får med de olika Microsoft 365-licenserna finns i [Omvandla företaget med Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- Microsoft Intune konfigureras som **Intune MDM-utfärdaren**. Mer information finns i [Ange utfärdare för hantering av mobila enheter](../fundamentals/mdm-authority-set.md).

  > [!div class="mx-imgBorder"]
  > ![Ange MDM-utfärdaren till Microsoft Intune i din klientorganisationsstatus](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- I en lokal Active Directory-domänkontrollant (DC):

  1. Kopiera följande Office- och Microsoft Edge-mallar till [den centrala lagringsplatsen (SYSVOL-mappen)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra):

      - [Administrativa mallar för Office](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Administrativa mallar för Microsoft Edge > Principfil](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Skapa en grupprincip för att skicka dessa mallar till en Windows 10 Enterprise-administratörsdator i samma domän som domänkontrollanten. I de här självstudierna har du

      - Den grupprincip som vi skapade med dessa mallar kallas **OfficeandEdge**. Du ser det här namnet i bilderna.
      - Den Windows 10 Enterprise-administratörsdator som vi använder kallas **Admindator**.

      I vissa organisationer har en domänadministratör två konton – ett vanligt domänarbetskonto och ett annat domänadministratörskonto som endast används för domänadministratörsuppgifter, till exempel grupprincip.

      Syftet med **Admindator** är att administratörer loggar in med sitt domänadministratörskonto och kommer åt verktyg som har utformats hantering av grupprinciper.

- På **Admindator**:

  - Logga in med ett domänadministratörskonto.

  - Installera **RSAT: Verktyg för grupprinciphantering**:

    1. Öppna appen **Inställningar** > **Appar** > **Valfria funktioner** > **Lägg till funktion**.
    2. Välj **RSAT: Verktyg för grupprinciphantering** > **Installera**.

        Vänta medan funktionen installeras i Windows. När det är klart visas den så småningom i appen **Administrationsverktyg för Windows**.

        > [!div class="mx-imgBorder"]
        > ![Appar för Administrationsverktyg för Windows, däribland appen Grupprinciphantering](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Se till att du har Internetåtkomst och administratörsbehörighet för Microsoft 365-prenumerationen, vilket inbegriper administrationscentret för Endpoint Manager.

## <a name="open-the-endpoint-manager-admin-center"></a>Öppna administrationscentret för Endpoint Manager

1. Öppna en Chromium-webbläsare, till exempel Microsoft Edge version 77 eller senare.
2. Gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Logga in med följande konto:

    **Användare**: Ange administratörskontot för din Microsoft 365-klientorganisationsprenumeration.  
    **Lösenord**: Ange dess lösenord.

Det här administrationscentret inriktar sig på enhetshantering och omfattar Azure-tjänster såsom Azure AD och Intune. Du ser kanske inte märkena **Azure Active Directory** och **Intune**, men är dem du använder.

Du kan även öppna administrationscentret för Endpoint Manager från [administrationscentret för Microsoft 365](https://admin.microsoft.com):

1. Gå till [https://admin.microsoft.com](https://admin.microsoft.com).
2. Logga in med administratörskontot för din Microsoft 365-klientorganisationsprenumeration.
3. Under **Administrationscenter** väljer du **Alla administrationscenter** > **Slutpunktshantering**. Administrationscentret för Endpoint Manager öppnas.

    > [!div class="mx-imgBorder"]
    > ![Visa alla administrationscenter i administrationscentret för Microsoft 365](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Skapa grupper och lägga till användare

Lokala principer tillämpas i LSDOU-ordningen (Local, Site, Domain, Organizational Unit (OU)) – lokalt, webbplats, domän och organisationsenhet. I den här hierarkin skriver OU-principer över lokala principer, domänprinciper skriver över webbplatsprinciper och så vidare.

I Intune tillämpas principer på användare och grupper som du skapar. Det finns ingen hierarki. Om två principer uppdaterar samma inställning visas inställningen som en konflikt. Om två efterlevnadsprinciper är i konflikt tillämpas den mest restriktiva principen. Om två konfigurationsprofiler är i konflikt tillämpas inte inställningen. Mer information finns i [Vanliga frågor, problem och lösningar med enhetsprinciper och profiler](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

I följande steg skapar du säkerhetsgrupper och lägger till användare i grupperna. Du kan lägga till en användare i flera grupper. Bland annat är det vanligt att en användare har flera enheter, till exempel en Surface Pro för arbete och en Android-mobilenhet för personligt bruk. Och det är vanligt att en person kommer åt organisationsresurser från dessa flera enheter.

1. I administrationscentret för Endpoint Manager väljer du **Grupper** > **Ny grupp**.

2. Ange följande inställningar:

    - **Grupptyp**: Välj **Säkerhet**.
    - **Gruppnamn:** Ange **Alla Windows 10 Student-enheter**.
    - **Typ av medlemskap**: Välj **Tilldelade**.

3. Välj **Medlemmar** och lägg till några enheter.

    Det är valfritt att lägga till enheter. Målet är att öva på att skapa grupper och att du vet hur enheter läggs till. Om du använder den här självstudien i en produktionsmiljö bör du vara medveten om vad du gör.

4. **Välj** > **Skapa** för att spara ändringarna.

    Ser du inte din grupp? Välj **Uppdatera**.

5. Välj **Ny grupp** och ange följande inställningar:

    - **Grupptyp**: Välj **Säkerhet**.
    - **Gruppnamn:** Ange **Alla Windows-enheter**.
    - **Typ av medlemskap**: Välj **Dynamisk enhet**.
    - **Dynamiska enhetsmedlemmar**: Konfigurera frågan:

        - **Egenskap**: Välj **deviceOSType**.
        - **Operator**: Välj **Lika med**.
        - **Värde**: Ange **Windows**.

        1. Välj **Lägg till uttryck**. Uttrycket visas i **regelsyntaxen**:

            > [!div class="mx-imgBorder"]
            > ![Skapa en dynamisk fråga och Lägg till uttryck i den administrativa mallen för Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            När användare eller enheter uppfyller de kriterier som du anger läggs de automatiskt till i de dynamiska grupperna. I det här exemplet läggs enheter automatiskt till i den här gruppen när operativsystemet är Windows. Om du använder den här självstudien i en produktionsmiljö bör du vara försiktig. Målet är att öva på att skapa dynamiska grupper.

        2. **Spara** > **Skapa** för att spara ändringarna.

6. Skapa gruppen **Alla lärare** med följande inställningar:

    - **Grupptyp**: Välj **Säkerhet**.
    - **Gruppnamn:** Ange **Alla lärare**.
    - **Typ av medlemskap**: Välj **Dynamisk användare**.
    - **Dynamiska användarmedlemmar**: Konfigurera frågan:

      - **Egenskap**: Välj **avdelning**.
      - **Operator**: Välj **Lika med**.
      - **Värde**: Ange **Lärare**.

        1. Välj **Lägg till uttryck**. Uttrycket visas i **regelsyntaxen**.

            När användare eller enheter uppfyller de kriterier som du anger läggs de automatiskt till i de dynamiska grupperna. I det här exemplet läggs användare automatiskt till i den här gruppen när deras avdelning är Lärare. Du kan ange avdelningen och andra egenskaper när användare läggs till i din organisation. Om du använder den här självstudien i en produktionsmiljö bör du vara försiktig. Målet är att öva på att skapa dynamiska grupper.

        2. **Spara** > **Skapa** för att spara ändringarna.

### <a name="talking-points"></a>Samtalsämnen

- Dynamiska grupper är en funktion i Azure AD Premium. Om du inte har Azure AD Premium är du endast licensierad för att skapa tilldelade grupper. Mer information om dynamiska grupper finns i:

  - [Dynamic Group Membership in Azure Active Directory (Part 1)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/) (Dynamiska gruppmedlemskap i Azure Active Directory (del 1)
  - [Dynamic Group Membership in Azure Active Directory (Part 2)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/) (Dynamiska gruppmedlemskap i Azure Active Directory (del 2)

- Azure AD Premium omfattar andra tjänster som ofta används vid hantering av appar och enheter, däribland [multifaktorautentisering (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) och [villkorsstyrd åtkomst](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

- Många administratörer undrar när de ska använda användargrupper och när de ska använda enhetsgrupper. Viss vägledning finns i [Användargrupper jämfört med enhetsgrupper](device-profile-assign.md#user-groups-vs-device-groups).

- Kom ihåg att användare kan tillhöra flera grupper. Du kan även skapa andra dynamiska användar- och enhetsgrupper, till exempel:

  - Alla studenter
  - Alla Android-enheter
  - Alla iOS-/iPadOS-enheter
  - Marknadsföring
  - Personalfrågor
  - Alla anställda i Charlotte
  - Alla Redmond-medarbetare
  - IT-administratörer på västkusten
  - IT-administratörer på östkusten

De användare och grupper som skapas visas även i [administrationscentret för Microsoft 365](https://admin.microsoft.com), Azure AD i Azure-portalen och [Microsoft Intune i Azure-portalen](https://go.microsoft.com/fwlink/?linkid=2090973). Du kan skapa och hantera grupper inom alla dessa områden för din klientorganisationsprenumeration. **Om ditt mål är enhetshantering använder du [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Granska gruppmedlemskap

1. Administrationscentret för Endpoint Manager väljer du **Användare** > välj namnet på valfri befintlig användare.

    > [!div class="mx-imgBorder"]
    > ![I administrationscentret för Endpoint Manager väljer du Användare](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Gå igenom en del av den information som du kan lägga till eller ändra. Titta till exempel på de egenskaper du kan konfigurera, däribland Jobbtitel, Avdelning, Ort, Kontorsplats och mer. Du kan använda dessa egenskaper i dynamiska frågor när du skapar dynamiska grupper.
3. Välj **Grupper** så visas medlemskapet för den här användaren. Du kan även ta bort användaren från en grupp.
4. Välj några av de andra alternativen om du vill se mer information och vad du kan göra. Du kan till exempel titta på den tilldelade licensen, användarens enheter och mer.

### <a name="what-did-i-just-do"></a>Vad gjorde jag nu?

I administrationscentret för Endpoint Manager skapade du nya säkerhetsgrupper och lade till befintliga användare och enheter i dessa grupper. Vi lägger till de här grupperna i senare steg i självstudien.

## <a name="create-a-template-in-intune"></a>Skapa en mall i Intune

I det här avsnittet skapar vi en administrativ mall i Intune, tittar på några inställningar i **Grupprinciphantering** och jämför samma inställningar i Intune. Målet är att visa en inställning i en grupprincip och visa samma inställning i Intune.

1. I administrationscentret för Endpoint Manager väljer du **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
2. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina profiler så att du enkelt kan identifiera dem senare. Ange till exempel **Adminmall – Windows 10 Student-enheter**.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Administrativa mallar**.

3. Välj **Skapa**. I listrutan **Välj en kategori** väljer du **Alla produkter**. Alla inställningar visas. Observera följande egenskaper i de här inställningarna:

    - **Sökvägen** till principen är samma som Grupprinciphantering eller GPEdit.
    - Inställningen gäller för användare eller enheter.

### <a name="open-group-policy-management"></a>Öppna Grupprinciphantering

I det här avsnittet visar vi en princip i Intune och dess matchande princip i Redigeraren Grupprinciphantering.

#### <a name="compare-a-device-policy"></a>Jämföra en enhetsprincip

1. På **Admindator** öppnar du appen **Grupprinciphantering**.

    Den här appen installeras med **RSAT: Verktyg för grupprinciphantering**, vilket är en valfri funktion som du installerar i Windows. I [Krav](#prerequisites) (i den här artikeln) visas de steg som behövs för att installera den.

2. Expandera **Domäner** > välj din domän. Välj exempelvis **contoso.net**.
3. Högerklicka på principen **OfficeandEdge** > **Redigera**. Då öppnas appen Redigeraren Grupprinciphantering.

    > [!div class="mx-imgBorder"]
    > ![Högerklicka på grupprincipen för Office och Edge ADMX och välj Redigera](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** är en grupprincip som innehåller ADMX-mallar för Office och Microsoft Edge. Den här principen beskrivs i [Krav](#prerequisites) (i den här artikeln).

4. Expandera **Datorkonfiguration** > **Principer** > **Administrativa mallar** > **Kontrollpanelen** > **Anpassning**. Observera de tillgängliga inställningarna.

    > [!div class="mx-imgBorder"]
    > ![Expandera Datorkonfiguration i Redigeraren Grupprinciphantering och gå till Anpassning](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Dubbelklicka på **Förhindra att låsskärmskameran aktiveras** och se de tillgängliga inställningarna:

    > [!div class="mx-imgBorder"]
    > ![Se alternativen för inställningen för datorkonfiguration i grupprincip](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. I administrationscentret för enhetshantering gå du till din mall **Adminmall – Windows 10 Student-enheter**.
6. Välj **Alla produkter** i listrutan och sök efter **anpassning**:

    > [!div class="mx-imgBorder"]
    > ![Sök efter anpassning i administrativ mall i Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Observera de tillgängliga inställningarna.

    Den här inställningstypen är **Enhet** och sökvägen är **\Kontrollpanelen\Anpassning**. Den här sökvägen liknar det du just såg i Redigeraren Grupprinciphantering. Om du öppnade inställningen ser du samma alternativ för **Inte konfigurerad**, **Aktiverad** och **Inaktiverad** som finns i Redigeraren Grupprinciphantering.

#### <a name="compare-a-user-policy"></a>Jämföra en användarprincip

1. I din administrativa mall söker du efter **InPrivate-surfning**. Observera sökvägen och att inställningen gäller för användare och enheter.

2. I **Redigeraren Grupprinciphantering** letar du upp matchande användare och enhetsinställningar:

    - Enhet: Expandera **Datorkonfiguration** > **Principer** > **Administrativa mallar** > **Windows-komponenter** > **Internet Explorer** > **Sekretess** > **Stäng av InPrivate-surfning**.
    - Användare: Expandera **Användarkonfiguration** > **Principer** > **Administrativa mallar** > **Windows-komponenter** > **Internet Explorer** > **Sekretess** > **Stäng av InPrivate-surfning**.

    > [!div class="mx-imgBorder"]
    > ![Stäng av InPrivate-surfning i Internet Explorer med hjälp av ADMX-mall](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> Om du vill se inbyggda Windows-principer kan du även använda GPEdit (appen **Redigera grupprincip**).

#### <a name="compare-an-edge-policy"></a>Jämföra en Edge-princip

1. I administrationscentret för enhetshantering gå du till din mall **Adminmall – Windows 10 Student-enheter**.
2. Välj **Edge-version 77 och senare** i listrutan.
3. Sök efter **start**. Observera de tillgängliga inställningarna.
4. I Redigeraren Grupprinciphantering letar du upp följande enhetsinställningar:

    - Enhet: Expandera **Datorkonfiguration** > **Principer** > **Administrativa mallar** > **Microsoft Edge** > **Start, startsida och ny fliksida**.
    - Användare: Expandera **Användarkonfiguration** > **Principer** > **Administrativa mallar** > **Microsoft Edge** > **Start, startsida och ny fliksida**

### <a name="what-did-i-just-do"></a>Vad gjorde jag nu?

Du skapade en administrativ mall i Intune. I den här mallen tittade vi på några ADMX-inställningar och samma ADMX-inställningar i Grupprinciphantering.

## <a name="add-settings-to-the-students-admin-template"></a>Lägga till inställningar i den administrativa mallen Studenter

I den här mallen konfigurerade vi några Internet Explorer-inställningar för att låsa enheter som delas av flera studenter.

1. I din mall **Adminmall – Windows 10 Student-enheter** söker du efter **Stäng av InPrivate-surfning** och väljer enhetsprincipen:

    > [!div class="mx-imgBorder"]
    > ![Stäng av enhetsprincip för InPrivate-surfning i administrativ mall i Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. I det här fönstret finns en beskrivning samt de värden som du kan ange. De här alternativen liknar dem som finns i grupprincip.
3. Välj **Aktiverad** > **OK** för att spara ändringarna.
4. Konfigurera även följande Internet Explorer-inställningar. Se till att klicka på **OK** för att spara ändringarna.

    - **Tillåt dra och släpp eller kopiera och klistra in filer**
      - **Typ**: Enhet
      - **Sökväg**: \Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen\Sidan Säkerhet\Zonen Internet
      - **Värde**: Inaktiverad

    - **Förhindra att certifikatfel ignoreras**
      - **Typ**: Enhet
      - **Sökväg**: \Windows-komponenter\Internet Explorer\Internet på Kontrollpanelen
      - **Värde**: Aktiverad

    - **Inaktivera ändring av inställningar för startsida**
      - **Typ**: Användare
      - **Sökväg**: \Windows-komponenter\Internet Explorer
      - **Värde**: Aktiverad
      - **Startsida**: Ange en URL, till exempel `contoso.com`.

5. Rensa sökfiltret. De inställningar som du konfigurerade visas längst upp:

    > [!div class="mx-imgBorder"]
    > ![Konfigurerade inställningar visas längst upp i Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Tilldela din mall

1. I mallen väljer du **Tilldelningar**. Du kan behöva stänga mallen och sedan välja den från listan **Enheter – Konfigurationsprofiler**:

    > [!div class="mx-imgBorder"]
    > ![Välj din profil för administrativ mall från listan Enhetskonfigurationsprofiler i Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Välj **Välj de grupper som ska inkluderas**. En lista över befintliga användare och grupper visas.
3. Välj gruppen **Alla Windows 10 Student-enheter** som du skapade tidigare > **Välj**.

    Om du använder den här självstudien i en produktionsmiljö bör du lägga till grupper som är tomma. Målet är att öva på att tilldela din mall.

4. **Spara** ändringarna.

När profilen har sparats tillämpas den på enheterna när de checkar in med Intune. Om enheterna är anslutna till Internet kan det ske omedelbart. Mer information om uppdateringstider för principer finns i [Hur lång tid tar det innan principerna, profilerna eller apparna når enheterna efter att de har tilldelats?](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Lås inte ute dig själv när du tilldelar strikta eller restriktiva principer och profiler. Överväg att skapa en grupp som är exkluderad från dina principer och profiler. Tanken är att det ska finnas åtkomst till felsökning. Övervaka den här gruppen för att bekräfta att den används som det är tänkt.

### <a name="what-did-i-just-do"></a>Vad gjorde jag nu?

I administrationscentret för Endpoint Manager skapade du en enhetskonfigurationsprofil för administrativ mall och tilldelade den här profilen till en grupp som du skapade.

## <a name="create-a-onedrive-template"></a>Skapa en OneDrive-mall

I det här avsnittet skapar du en administrativ mall för OneDrive i Intune för att kontrollera vissa inställningar. Dessa specifika inställningar väljs eftersom de används ofta av organisationer.

1. Skapa en till profil (**Enheter** > **Konfigurationsprofiler** > **Skapa profil**).

2. Ange följande egenskaper:

    - **Namn**: Ange **Adminmall – OneDrive-principer som gäller för alla Windows 10-användare**.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Administrativa mallar**.

3. Välj **Skapa**.
4. Välj **Office** i listrutan.
5. **Aktivera** följande inställningar. Se till att klicka på **OK** för att spara ändringarna.

    - **Logga in användare i tyst läge till OneDrive-synkroniseringsklienten med deras Windows-autentiseringsuppgifter**
    - **Använd Filer på begäran i OneDrive**
    - **Hindra användarna från att synkronisera personliga OneDrive-konton**

Inställningarna ser ut ungefär som följande inställningar:

> [!div class="mx-imgBorder"]
> ![Skapa en administrativ mall för OneDrive i Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Mer information om OneDrive-klientinställningar finns i [Använda grupprincip för att kontrollera inställningarna för OneDrive-synkroniseringsklient](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Tilldela din mall

1. I mallen väljer du **Tilldelningar**.
2. Välj **Välj de grupper som ska inkluderas**. En lista över befintliga användare och grupper visas.
3. Välj gruppen **Alla Windows-enheter** som du skapade tidigare > **Välj**.

    Om du använder den här självstudien i en produktionsmiljö bör du lägga till grupper som är tomma. Målet är att öva på att tilldela din mall.

4. **Spara** ändringarna.

Nu har du skapat några administrativa mallar och tilldelat dem till grupper som du har skapat. Nästa steg är att skapa en administrativ mall med hjälp av Windows PowerShell och Microsoft Graph API för Intune.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Valfritt: Skapa en princip med hjälp av PowerShell och Graph API

I det här avsnittet används följande resurser. Vi kommer att installera dessa resurser i det här avsnittet.

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [Microsoft Graph API för Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. På **Admindator** öppnar du **Windows PowerShell** som administratör:

    1. I sökfältet skriver du **powershell**.
    2. Högerklicka på **Windows PowerShell** > **Kör som administratör**.

    > [!div class="mx-imgBorder"]
    > ![Kör Windows PowerShell som administratör](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. Hämta och ange körningsprincipen.

    1. Ange: `get-ExecutionPolicy`

        Skriv ned den aktuella inställningen, som kan vara **Begränsad**. När du är färdig med självstudien ställer du tillbaka den till det ursprungliga värdet.

    2. Ange: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. Ange `Y` för att ändra det.

    PowerShell-körningsprincipen förhindrar körning av skadliga skript. Mer information finns i [Om körningsprinciper](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Ange: `Install-Module -Name Microsoft.Graph.Intune`

    Ange `Y` om:

    - Du uppmanas att installera NuGet-leverantören
    - Du uppmanas att installera modulerna från en icke-betrodd lagringsplats

    Det kan ta flera minuter att slutföra processen. När det är klart visas en prompt som liknar följande prompt:

    > [!div class="mx-imgBorder"]
    > ![Windows PowerShell-prompt efter installation av en modul](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. I webbläsaren går du till [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases) och väljer filen **Intune-PowerShell-SDK_v6.1907.00921.0001.zip**.

    1. Välj **Spara som** och välj en mapp som du kommer ihåg. `c:\psscripts` är ett bra val.
    2. Öppna mappen och högerklicka på .zip-filen > **Extrahera alla** > **Extrahera**. Mappstrukturen ser ut ungefär som i följande mapp:

        > [!div class="mx-imgBorder"]
        > ![Intune PowerShell SDK-mappstruktur efter extrahering](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. På fliken **Visa** kontrollerar du **Filnamnstillägg**:

    > [!div class="mx-imgBorder"]
    > ![Välj filnamnstillägg på fliken Visa i Utforskaren](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. I mappen går du till `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`. Högerklicka på varje .dll-fil > **Egenskaper** > **Avblockera**.

    > [!div class="mx-imgBorder"]
    > ![Avblockera DLL-filerna](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. I **Windows PowerShell**-appen anger du:

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Ange `R` om du uppmanas att köra från den icke-betrodda utgivaren.

8. Administrativa mallar för Intune använder betaversionen av Graph:

    1. Ange: `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. Ange: `Connect-MSGraph -AdminConsent`

    3. När du uppmanas till det loggar du in med samma Microsoft 365-administratörskonto. Dessa cmdletar skapar principen i din klientorganisation.

        **Användare**: Ange administratörskontot för din Microsoft 365-klientorganisationsprenumeration.  
        **Lösenord**: Ange dess lösenord.

    4. Välj **Godkänn**.

9. Skapa konfigurationsprofilen **Testkonfiguration**. Ange:

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    När dessa cmdletar slutförs skapas profilen. Bekräfta genom att gå till administrationscentret för Endpoint Manager > **Konfigurationsprofiler**. Din profil **Testkonfiguration** bör finnas med.

10. Hämta alla SettingDefinitions. Ange:

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Leta upp definitions-ID med hjälp av inställningens visningsnamn. Ange:

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Konfigurera en inställning. Ange:

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Visa din princip

1. I administrationscentret för Endpoint Manager > **Konfigurationsprofiler** > **Uppdatera**.
2. Välj din profil **Testkonfiguration** > **Inställningar**.
3. Välj **Alla produkter** i listrutan.

Du ser då att inställningen **Logga in användare i tyst läge till OneDrive-synkroniseringsklienten med deras Windows-autentiseringsuppgifter** konfigureras.

## <a name="policy-best-practices"></a>Bästa praxis för principer

När du skapar principer och profiler i Intune finns det några rekommendationer och bästa praxis att tänka på. Mer information finns i [bästa praxis för principer och profiler](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Rensa resurser

När resurser inte längre behövs kan du:

- Ta bort de grupper som du skapade:

  - **Alla Windows 10 Student-enheter**
  - **Alla Windows-enheter**
  - **Alla lärare**

- Ta bort de administrativa mallar som du skapade:

  - **Adminmall – Windows 10 Student-enheter**
  - **Adminmall – OneDrive-principer som gäller för alla Windows 10-användare**
  - **Testkonfiguration**

- Ställ tillbaka Windows PowerShell-körningsprincipen på dess ursprungliga värde. I följande exempel anges körningsprincipen till Begränsad:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>Nästa steg

I den här självstudien har du lärt dig mer om [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), använt frågebyggaren för att skapa dynamiska grupper samt skapat administrativa mallar i Intune för att konfigurera [ADMX-inställningar](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies). Du jämförde även användning av ADMX-mallar lokalt och i molnet med Intune. Dessutom använde du PowerShell-cmdletar för att skapa en administrativ mall.

Mer information om administrativa mallar i Intune finns här:

> [!div class="nextstepaction"]
> [Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Intune](administrative-templates-windows.md)
