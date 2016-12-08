---
title: "Begränsa e-poståtkomst till Exchange Online | Microsoft Intune"
description: "Skydda och styr åtkomsten till företagets e-post på Exchange Online med villkorlig åtkomst."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09c82f5d-531c-474d-add6-784c83f96d93
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 07f18c0011624f760f4d1db05cf954551dee3a85
ms.openlocfilehash: d63f62011acaad154790b88f710eb4eda4fb261b


---

# <a name="restrict-email-access-to-exchange-online-and-new-exchange-online-dedicated-with-intune"></a>Begränsa åtkomsten för e-post till Exchange Online och nya Exchange Online Dedicated med Microsoft Intune

Om du har en Exchange Online Dedicated-miljö och vill veta om den har den nya eller gamla konfigurationen kontaktar du din kontoansvariga.

Du kontrollerar e-poståtkomsten till Exchange Online eller till din nya Exchange Online Dedicated-miljö genom att konfigurera villkorlig åtkomst till Exchange Online i Intune.
Mer information om hur villkorlig åtkomst fungerar finns i avsnittet [Begränsa åtkomsten till e-post, O365 och andra tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).


**Innan** du konfigurerar villkorlig åtkomst måste du:

-   Ha en **Office 365-prenumeration med Exchange Online (t.ex. E3)**, och användarna måste ha licens för Exchange Online.

- Ha en **Enterprise Mobility + Security- eller Azure Active Directory Premium-prenumeration**, och användarna måste ha licens för EMS eller Azure AD. Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) eller [sida med priser för Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).

-  Överväga att konfigurera den valfria **tjänst-till-tjänst-anslutningen i Microsoft Intune** som ansluter [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] till Microsoft Exchange Online och som gör att du kan hantera enhetsinformationen via [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-konsolen. Du måste inte använda anslutningen för att kunna använda efterlevnadsprinciper eller principer för villkorlig åtkomst, men den krävs för att köra rapporter som utvärderar effekten av villkorlig åtkomst.

   > [!NOTE]
   > Konfigurera inte tjänst-till-tjänst-anslutningen om du planerar att använda villkorlig åtkomst för både Exchange Online och Exchange On-premises

   Anvisningar för hur du konfigurerar anslutningen finns i avsnittet om [Intunes tjänst-till-tjänst-anslutning](intune-service-to-service-exchange-connector.md)

Innan en användare kan ansluta till sin e-post när principer för villkorlig åtkomst har konfigurerats och tillämpats på användaren måste användarens **enhet**:

-   **Registreras** med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller vara en domänansluten dator.

-  **Registreras i Azure Active Directory**. Detta sker automatiskt när enheten registreras med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.

  AAD DRS aktiveras automatiskt för Intune och Office 365-kunder. Kunder som redan har använt AD FS Device Registration Service ser inte registrerade enheter i sina lokala Active Directory-kataloger.

-   Vara **kompatibel** med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-efterlevnadsprinciper som distribuerats till enheten, eller vara domänansluten till en lokal domän.

Om en princip för villkorlig åtkomst inte uppfylls visas något av följande meddelanden när användaren loggar in:

- Om enheten inte är registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med posten i Azure Active Directory.

-   Om enheten utvärderas som icke-kompatibel med reglerna för efterlevnadsprinciper dirigeras användaren till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-företagsportalens webbplats eller företagsportalappen som innehåller information om problemet och hur det kan åtgärdas.


Diagrammet nedan illustrerar flödet som används av principerna för villkorlig åtkomst för Exchange Online.

![Diagram som visar beslutspunkter som avgör om enheten beviljas åtkomst eller blockeras](../media/ConditionalAccess8-1.png)

## <a name="support-for-mobile-devices"></a>Stöd för mobila enheter
Du kan begränsa åtkomsten till Exchange Online-e-post från **Outlook** och andra **appar som använder modern autentisering**:

- Android 4.0 och senare, Samsung Knox Standard 4.0 och senare samt Android for Work
- iOS 8.0 och senare
- Windows Phone 8.1 och senare

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

Med **modern autentisering** kan Microsoft Office-klienter använda ADAL-baserad (Active Directory Authentication Library) inloggning.

-   ADAL-baserad autentisering gör det möjligt för Office-klienter att delta i webbläsarbaserad autentisering (även kallat passiv autentisering).  Användare som vill autentiseras omdirigeras till en inloggningswebbsida. Den här nya inloggningsmetoden ökar säkerheten med till exempel **multifaktorautentisering** och **certifikatbaserad autentisering**.
Den här [artikeln](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) innehåller mer detaljerad information om hur modern autentisering fungerar.
Konfigurera ADFS-anspråksregler och blockera protokoll som inte stöder modern autentisering. Detaljerade anvisningar finns i scenario 3 – [blockera all åtkomst till O365 utom webbläsarbaserade program](https://technet.microsoft.com/library/dn592182.aspx).

Du kan begränsa åtkomst till **Outlook Web Access (OWA)** i Exchange Online vid åtkomst från en webbläsare på **iOS**- och **Android**-enheter.  Åtkomst tillåts endast från endast webbläsare som stöds på kompatibla enheter:

* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS och Android 5.0 och senare)

**Webbläsare som inte stöds blockeras**.

**OWA-appen för iOS och Android kan ändras så att modern autentisering inte används och inte stöds.  Åtkomst från OWA-appen måste blockeras via ADFS-anspråksregler.**


Du kan begränsa åtkomsten till Exchange-e-post från den inbyggda **Exchange ActiveSync-e-postklienten** på följande plattformar:

- Android 4.0 och senare, Samsung Knox Standard 4.0 och senare

- iOS 8.0 och senare

- Windows Phone 8.1 och senare

## <a name="support-for-pcs"></a>Stöd för datorer

Du kan konfigurera villkorlig åtkomst för datorer som kör Office-datorprogram om du vill komma åt **Exchange Online** och **SharePoint Online** för datorer som uppfyller följande krav:

-   Datorn måste köra Windows 7.0, Windows 8.1 eller Windows 10.

  >[!NOTE]
  > Om du vill använda villkorlig åtkomst med Windows 10-datorer måste du uppdatera dessa datorer med Windows 10 Anniversary Update.

  Datorn måste antingen vara domänansluten eller kompatibel med reglerna för efterlevnadsprinciper.

  För att vara kompatibel måste datorn vara registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och uppfylla principerna.

  Domänanslutna datorer måste ställas in att [automatiskt registrera enheten](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) i Azure Active Directory.

  >[!NOTE]
    >Villkorlig åtkomst stöds inte på datorer som kör Intune-datorklienten.

-   [Modern Office 365-autentisering måste vara aktiverat](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) och alla de senaste Office-uppdateringarna måste vara installerade.

    Modern autentisering skapar stöd för ADAL-baserad (Active Directory Authentication Library) inloggning i Windows-baserade Office 2013-klienter och förbättrar säkerheten med bland annat **multifaktorautentisering** och **certifikatbaserad autentisering**.

-   Konfigurera ADFS-anspråksregler och blockera protokoll som inte stöder modern autentisering. Detaljerade anvisningar finns i scenario 3 – [blockera all åtkomst till O365 utom webbläsarbaserade program](https://technet.microsoft.com/library/dn592182.aspx).

## <a name="configure-conditional-access"></a>Konfigurera villkorlig åtkomst
### <a name="step-1-configure-and-deploy-a-compliance-policy"></a>Steg 1: Konfigurera och distribuera en efterlevnadsprincip
Se till att du [skapar](create-a-device-compliance-policy-in-microsoft-intune.md) och [distribuerar](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md) en efterlevnadsprincip till de användargrupper som även ska omfattas av principen för villkorlig åtkomst.


> [!IMPORTANT]
> Om du inte har distribuerat någon efterlevnadsprincip betraktas enheterna som kompatibla och beviljas åtkomst till Exchange.

### <a name="step-2-evaluate-the-effect-of-the-conditional-access-policy"></a>Steg 2: Utvärdera effekten av principen för villkorlig åtkomst
Du kan använda **inventeringsrapporterna för mobila enheter** för att identifiera enheter som kan hindras från att komma åt Exchange när du har konfigurerat principen för villkorlig åtkomst.

Om du vill göra det konfigurerar du en anslutning mellan [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och Exchange med hjälp av [Microsoft Intunes tjänst-till-tjänst-anslutning](intune-service-to-service-exchange-connector.md).
1.  Gå till **Rapporter -> Inventeringsrapporter för mobila enheter ->**.
![Skärmbild av sidan Inventeringsrapport för mobila enheter](../media/IntuneSA2bMobileDeviceInventoryReport.png)

2.  I rapportparametrarna väljer du den [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-grupp som du vill utvärdera och, om det behövs, de enhetsplattformar som principen ska gälla för.
3.  När du har valt kriterierna som uppfyller organisationens behov väljer du **Visa rapport**.
Rapportvisningsprogrammet öppnas i ett nytt fönster.
![Skärmbild av en exempelinventeringsrapport för mobila enheter](../media/IntuneSA2cViewReport.PNG)

Efter att du har har kört rapporten, undersök dessa fyra kolumner för att avgöra om en användare kommer att blockeras:

-   **Hanteringskanal** - Anger om enheten sköts av Intune, Exchange ActiveSync, eller bådadera.

-   **AAD Registrerade** - Anger om enheten är registrerad med Azure Active Directory (kallas Workplace Join).

-   **Anmärkning** - Anger om enheten är kompatibel med alla efterlevnadsprinciper som du har angivet.

-   **Exchange ActiveSync ID** - iOS och Android enheter måste ha sin Exchange ActiveSync ID i hopkopplad med anordningen som är registrerad i Azure Active Directory. Detta händer när användaren väljer länken **Aktivera e-post** i karantänmeddelandet.

    > [!NOTE]
    > Windows Phone enheter visar alltid ett värde i den här kolumnen.

Enheter som är en del av en målgrupp kommer att blockeras från att komma åt Exchange om kolumnvärdena matchar de som anges i följande tabell:

--------------------------
|Hanteringskanal|AAD registrerad|Kompatibel|Exchange ActiveSync ID|Resulterande åtgärd|
|----------------------|------------------|-------------|--------------------------|--------------------|
|**Hanterad av Microsoft Intune and Exchange ActiveSync**|Ja|Ja|Ett värde visas|Emailåtkomst tillåten|
|Vilket som helst annat värde|Nej|Nej|Inget värde visas|Emailåtkomst blockerad|
----------------------
Du kan exportera innehållet i rapporten och använda kolumnen **E-postadress** för att meddela användarna att de kommer att blockeras.

### <a name="step-3-configure-user-groups-for-the-conditional-access-policy"></a>Steg 3: Konfigurera användargrupper för principen för villkorlig åtkomst
Principer för villkorlig åtkomst är avsedda för olika Azure Active Directory-säkerhetsgrupper med användare. Du kan också undanta vissa användargrupper från den här principen.  När en användare är angiven som mål för en policy, måste varje enhet de använder vara kompatibla för att få åtkomst till email.

Du kan konfigurera dessa grupper i **Office 365 admin center**, eller **Intune kontoportal**.

Du kan ange två grupptyper i varje policy:

-   **Målriktade grupper** – Användargrupper som principen tillämpas på.

-   **Undantagna grupper** - användargrupper som är undantagna från policyn (tillval)

Om en användare finns i båda grupperna, kommer de att vara befriade från policyn.

Endast de grupper som omfattas av principen för villkorlig åtkomst utvärderas.

### <a name="step-4-configure-the-conditional-access-policy"></a>Steg 4: Konfigurera principen för villkorlig åtkomst

>[!NOTE]
> Du kan även skapa principer för villkorlig åtkomst i Azure AD-hanteringskonsolen. Azure AD-hanteringskonsolen låter dig skapa principer för villkorlig åtkomst för Intune-enheter (kallas för **device-based conditional access policy** (enhetsbaserad princip för villkorlig åtkomst) i Azure AD) utöver andra principer för villkorlig åtkomst som multifaktorautentisering.  Du kan även ange principer för villkorlig åtkomst för tredje parts företagsappar som Salesforce och Box som Azure AD stöder. Mer information finns i [How to set Azure Active Directory device-based conditional access policy for access control to Azure Active Directory connected applications](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/) (Så ställer du in principer för Azure Active Directory-enhetsbaserad villkorlig åtkomst för åtkomstkontroll till program anslutna med Azure Active Directory).


1.  I [Microsoft Intune Administrationskonsol](https://manage.microsoft.com) väljer du **Princip** > **Villkorlig åtkomst** > **Exchange Online-princip**.


2.  På **Exchange Online policy** sidan, välj **Aktivera villkorlig åtkomstpolicy för Exchange Online**.

    > [!NOTE]
    > Om du inte har distribuerat någon efterlevnadsprincip behandlas enheter som kompatibla.
    >
    > Oavsett efterlevnadsstatusen så måste alla användare som principen tillämpas på registrera sina enheter med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

3.  För appar som använder modern autentisering kan du välja vilka plattformar som principen ska gälla för på något av två sätt under **Programåtkomst**. Exempel på plattformar som stöds är Android, iOS, Windows och Windows Phone.

    -   **Alla plattformar**

        Detta kräver att alla enheter som används för att komma åt **Exchange Online** registreras i Intune och uppfyller principkraven.  Principen för villkorlig åtkomst tillämpas på klientprogram som använder **modern autentisering** och om plattformen inte stöds av Intune blockeras åtkomsten till **Exchange Online**.

        Om alternativet **Alla plattformar** väljs innebär det att Azure Active Directory använder denna princip på alla autentiseringsbegäranden, oavsett vilken plattform som rapporteras av klientprogrammet.  Alla plattformar måste registreras och vara kompatibla, med undantag för:
        *   Windows-enheter måste registreras och vara kompatibla, domänanslutna med lokal Active Directory, eller båda
        * Plattformar som inte stöds, t.ex. Mac OS.  Appar som använder modern autentisering som kommer från dessa plattformar kommer dock fortfarande att blockeras.

    -   **Vissa plattformar**

         Principen för villkorlig åtkomst gäller alla klientappar som använder **modern autentisering** på de enhetsplattformar som du anger.

4. Under **Outlook Web Access (OWA)** kan du välja att tillåta åtkomst till Exchange Online endast genom de webbläsare som stöds: Safari (iOS) och Chrome (Android). Åtkomst från andra webbläsare kommer att blockeras. De plattformsbegränsningar du valde för programåtkomst för Outlook gäller även här.

  På **Android**-enheter måste användare aktivera webbläsaråtkomst.  Om du vill göra detta måste slutanvändaren aktivera alternativet "Aktivera webbläsaråtkomst" på den registrerade enheten enligt följande:
  1.    Starta **företagsportalappen**.
  2.    Gå till sidan **Inställningar** från de tre punkterna (…) eller knappen för maskinvara.
  3.    Tryck på knappen **Aktivera webbläsaråtkomst**.
  4.    I webbläsaren Chrome loggar du ut från Office 365 och startar om Chrome.

  På **iOS- och Android**-plattformar kommer för Azure Active Directory att utfärda ett TLS-certifikat (Transport layer security) för enheten för att identifiera den enhet som används för att få åtkomst till tjänsten.  Enheten visar certifikatet med en uppmaning till slutanvändaren om att markera certifikatet på det sätt som visas i skärmbilderna nedan. Användarna måste välja det här certifikatet innan de kan fortsätta att använda webbläsaren.

  **iOS**

  ![skärmbild av certifikatfråga på en iPad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![skärmbild av certifikatuppmaning på en Android-enhet](../media/mdm-browser-ca-android-cert-prompt.png)

5.  Under **Exchange ActiveSync-appar** kan du välja att hindra icke-kompatibla enheter från att komma åt Exchange Online. Du kan också välja om du vill tillåta eller blockera åtkomst till e-post om enheten inte kör en plattform som stöds. Exempel på plattformar som stöds är Android, iOS, Windows och Windows Phone.

 Exchange Active Sync-appar **Android for Work**-enheter:
 -  Endast **Gmail** och **Nine Work**-appar i **arbetsprofilen** stöds på Android for Work-enheter. För villkorlig åtkomst till arbete på Android for Work-enheter måste du distribuera en e-postprofil för Gmail eller Nine Work-appen och distribuera den som en **nödvändig** installation.

6.  Under **Målgrupper**, välja aktiva säkerhetsgrupper av användare för vilka policyn kommer att gälla. Du kan välja att tillämpa principen på alla användare eller en vald lista med användargrupper.
![Skärmbild av sidan för Exchange Online-principer för villkorlig åtkomst med alternativen Målgrupper och Undantagna grupper](../media/IntuneSA5eTargetedExemptedGroups.PNG)
    > [!NOTE]
    > För användare som finns i **Målgrupper** ersätter Intune-principerna Exchange-regler och Exchange-principer.
    >
    > Exchange kommer bara att tillämpa blockerings- och karantänregler för Exchange och Exchange-principer om:
    >
    > -   Användaren inte är licensierad för Intune.
    > -   Användaren är licensierad för Intune, men användaren tillhör inte någon säkerhetsgrupp som villkorliga åtkomstprinciper riktas mot.

6.  Under **Undantagna grupper**, välj aktiva säkerhetsgrupper av användare som är undantagna från denna policy. Om en användare finns i båda grupperna, kommer de att vara befriade från policyn.

7.  När du är klar väljer du **Spara**.

-   Du behöver inte använda den villkorliga åtkomstpolicyn, den träder i kraft omedelbart.

-   Efter att en användare skapar ett emailkonto, blockeras enheten omedelbart.

-   Om en blockerad användare registrerar enheten med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och åtgärdar inkompatibilitetsproblem, avblockeras åtkomsten till e-posten inom två minuter.

-   Om användaren avregistrerar sin enhet blockeras e-posten efter cirka 6 timmar.

**Några exempelscenarier som beskriver hur du konfigurerar principer för villkorlig åtkomst för att begränsa enhetsåtkomsten finns i [exempelscenarier för att begränsa e-poståtkomst](restrict-email-access-example-scenarios.md).**

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Övervaka efterlevnaden och villkorlig åtkomstpolicy

#### <a name="to-view-devices-that-are-blocked-from-exchange"></a>För att visa enheter som är blockerade från Exchange

På [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-instrumentpanelen väljer du rutan **Blockerade enheter från Exchange** för att visa antalet blockerade enheter och länkar till mer information.
![Skärmbild av Intune-instrumentpanelen som visar antalet enheter som hindras från att komma åt Exchange](../media/IntuneSA6BlockedDevices.PNG)

## <a name="next-steps"></a>Nästa steg
[Begränsa åtkomsten till SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

[Begränsa åtkomsten till Skype för företag – Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)



<!--HONumber=Nov16_HO4-->

