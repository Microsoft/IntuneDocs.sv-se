---
title: "Begränsa åtkomsten till SharePoint Online | Microsoft Intune"
description: "Skydda och styr åtkomsten till företagets data på SharePoint Online med villkorlig åtkomst."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: db1d43dd647122e7ba8ebd4e6df48e3c970a3392
ms.openlocfilehash: 76ac4c92d090ef0057bd7c9687b169cd12b901a1


---

# Begränsa åtkomsten till SharePoint Online med Microsoft Intune
Använd villkorlig åtkomst i [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] om du vill kontrollera åtkomsten till filer i SharePoint Online.
Villkorlig åtkomst består av två komponenter:
- Principen för enhetsefterlevnad som enheten måste uppfylla för att anses vara kompatibel.
- Principen för villkorlig åtkomst där du anger de villkor som enheten måste uppfylla för att komma åt tjänsten.
Mer information om hur villkorlig åtkomst fungerar finns i avsnittet [Begränsa åtkomsten till e-post, O365 och andra tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

Principerna för efterlevnad och villkorlig åtkomst distribueras till användaren. Alla enheter som användaren använder för att komma åt tjänsterna kontrolleras för att se att de följer principerna.

När en användare försöker ansluta till en fil med en app som stöds, till exempel OneDrive på sin enhet, görs följande utvärdering:

![Diagram som visar beslutspunkterna som avgör om en enhet får åtkomst till SharePoint eller blockeras ](../media/ConditionalAccess8-6.png)


**Innan** du konfigurerar en princip för villkorlig åtkomst för SharePoint Online måste du:
- Ha en **SharePoint Online-prenumeration**, och användarna måste ha licens för SharePoint Online.
- Ha en **Enterprise Mobility + Security- eller Azure Active Directory Premium-prenumeration**, och användarna måste ha licens för EMS eller Azure AD. Mer information finns på [sidan med priser för Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) eller [sida med priser för Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


  För att kunna ansluta till de nödvändiga filerna måste enheten:
-   Vara **registrerad** i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller vara en domänansluten dator.

-   **Registrera enheten** i Azure Active Directory (detta sker automatiskt när enheten registreras med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Vara kompatibel med eventuella [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-efterlevnadsprinciper

Enhetens tillstånd lagras i Azure Active Directory som beviljar eller blockerar tillgång till filerna baserat på de villkor du angivit.

Om ett villkor inte är uppfyllt, kommer användaren att visas ett följande meddelanden när de loggar in:

-   Om enheten inte är registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], eller om den inte är registrerad i Azure Active Directory, så visas ett meddelande med instruktioner om hur du installerar företagsportalappen och registrerar dig.

-   Om enheten inte är kompatibel visas ett meddelande som leder användaren till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-företagsportalens webbplats, som innehåller mer information om problemet och hur det kan åtgärdas.

**Villkorlig åtkomst tillämpas på alla SharePoint-platser och extern delning är blockerad**

>[!NOTE]
>Om du aktiverar villkorlig åtkomst för SharePoint Online rekommenderar vi att inaktiverar domänen i listan enligt beskrivningen i [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/en-us/library/dn917451.aspx).  

## Stöd för mobila enheter
- iOS 8.0 och senare
- Android 4.0 och senare, Samsung Knox Standard 4.0 eller senare
- Windows Phone 8.1 och senare

Du kan begränsa åtkomst till SharePoint Online vid åtkomst till denna från en webbläsare från **iOS**- och **Android**-enheter.  Åtkomst tillåts endast från endast webbläsare som stöds på kompatibla enheter:
* Safari (iOS)
* Chrome (Android)
* Hanterad webbläsare (iOS och Android)

**Webbläsare som inte stöds blockeras**.

## Stöd för datorer
- Windows 8.1 och senare (efter att ha registrerats i Intune)
- Windows 7.0, Windows 8.1 eller Windows 10 (om datorn är domänansluten),
> [!NOTE]
>Om du vill använda villkorlig åtkomst med Windows 10-datorer måste du uppdatera dessa datorer med Windows 10 Anniversary Update.

  - Domänanslutna datorer måste vara konfigurerade att [registreras automatiskt](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) med Azure Active Directory.
AAD DRS aktiveras automatiskt för Intune och Office 365-kunder. Kunder som redan har använt AD FS Device Registration Service ser inte registrerade enheter i sina lokala Active Directory-kataloger.

  - Om principen är konfigurerad att kräva domänanslutning och datorn inte är domänansluten visas ett meddelande som uppmanar användaren att kontakta IT-administratören.

  - Om principen är konfigurerad att kräva domänsanslutning eller efterlevnad och datorn inte uppfyller något av kraven visas ett meddelande med instruktioner som hjälper användaren att installera företagsportalappen och registrera sig.
  >[!NOTE]
  >Villkorlig åtkomst stöds inte på datorer som kör Intune-datorklienten.

-    [Modern Office 365-autentisering måste vara aktiverat](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) och alla de senaste Office-uppdateringarna måste vara installerade.

    Modern autentisering skapar stöd för ADAL-baserad (Active Directory Authentication Library) inloggning i Windows-baserade Office 2013-klienter och förbättrar säkerheten med bland annat **multifaktorautentisering** och **certifikatbaserad autentisering**.


## Konfigurera villkorlig åtkomst för SharePoint Online

### Steg 1: Konfigurera Active Directory-säkerhetsgrupper
Konfigurera säkerhetsgrupper för Azure Active Drive Directory för villkorlig åtkomstpolicy innan du börjar. Du kan konfigurera dessa grupper i **Office 365 admin center**, eller **Intune kontoportal**. Dessa grupper används för att bestämma målanvändare eller undantagna användare för principen. När en användare är angiven som mål för en policy, måste varje enhet de använder vara godkänd för att få åtkomst till resurser.

Du kan ange två grupptyper i en SharePoint Online policy:

-   **Målgrupper** – Innehåller grupper med användare som principen ska gälla för.

-   **Undantagna grupper** – Innehåller användargrupper som är undantagna från principen.

Om en användare finns i båda grupperna, kommer de att vara befriade från policyn.

### Steg 2: Ställ in och distribuera en efterlevnadsprincip
Om du inte redan har gjort det skapar du och distribuerar en efterlevnadsprincip för de användare som SharePoint Online-principen ska tillämpas på.

> [!NOTE]
> Medan efterlevnadsprinciper distribueras till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-grupper är principer för villkorlig åtkomst avsedda för Azure Active Directory-säkerhetsgrupper.

Mer information om hur du konfigurerar efterlevnadsprincipen finns i [Skapa en efterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT]
> Om du inte har distribuerat någon efterlevnadsprincip behandlas enheterna som kompatibla.

När du är klar, fortsätt till **Steg 3**.

### Steg 3: Ställ in SharePoint Online-principen
Konfigurera sedan policyn som kräver att enbart hanterade och godkända enheter kan komma åt SharePoint Online. Denna policy kommer att lagras i Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> Du kan även skapa principer för villkorlig åtkomst i Azure AD-hanteringskonsolen. Azure AD-hanteringskonsolen låter dig skapa principer för villkorlig åtkomst för Intune-enheter (kallas för **device-based conditional access policy** (enhetsbaserad princip för villkorlig åtkomst) i Azure AD) utöver andra principer för villkorlig åtkomst som multifaktorautentisering.  Du kan även ange principer för villkorlig åtkomst för tredje parts företagsappar som Salesforce och Box som Azure AD stöder. Mer information finns i [How to set Azure Active Directory device-based conditional access policy for access control to Azure Active Directory connected applications](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/) (Så ställer du in principer för Azure Active Directory-enhetsbaserad villkorlig åtkomst för åtkomstkontroll till program anslutna med Azure Active Directory).


1.  I [Microsoft Intune Administrationskonsol](https://manage.microsoft.com) väljer du **Princip** > **Villkorlig åtkomst** > **SharePoint Online-princip**.
![Skärmbild av sidan SharePoint Online-princip](../media/mdm-ca-spo-policy-configuration.png)

2.  Välj **Aktivera princip för villkorlig åtkomst för SharePoint Online**.

3.  Under **Programåtkomst** kan du välja att använda principen för villkorlig åtkomst för:

    -   **Alla plattformar**

        Detta kräver att alla enheter som används för att komma åt **SharePoint Online** registreras i Intune och att de uppfyller principkraven.  Klientprogram som använder **modern autentisering** omfattas av principen för villkorlig åtkomst. Om plattformen inte stöds av Intune för närvarande blockeras åtkomsten till **SharePoint Online**.

        Om alternativet **Alla plattformar** väljs innebär det att Azure Active Directory använder denna princip på alla autentiseringsbegäranden, oavsett vilken plattform som rapporteras av klientprogrammet.  Alla plattformar måste registreras och vara kompatibla, med undantag för:
        *   Windows-enheter måste registreras och vara kompatibla, domänanslutna med lokal Active Directory, eller båda
        * Plattformar som inte stöds, t.ex. Mac.  Appar som använder modern autentisering som kommer från dessa plattformar kommer dock fortfarande att blockeras.

    -   **Vissa plattformar**

         Principen för villkorlig åtkomst gäller alla klientappar som använder modern autentisering på de plattformar som du anger.

     För Windows-datorer måste datorn antingen vara domänansluten eller registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och kompatibel. Du kan ange följande krav:

     -   **Enheter måste vara domänanslutna eller kompatibla.** Välj det här alternativet om du vill att datorerna antingen ska vara domänanslutna eller kompatibla med principer som angetts i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Om datorn inte uppfyller något av dessa krav ombeds användaren att registrera enheten i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Enheter måste vara domänanslutna.** Välj det här alternativet om du vill kräva att datorerna ska vara domänanslutna för att få åtkomst till Exchange Online. Om datorn inte är domänansluten blockeras åtkomsten till e-posten och användaren uppmanas att kontakta IT-administratören.

     -   **Enheter måste vara godkända.** Välj det här alternativet om du vill kräva att datorerna ska vara registrerade i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och kompatibla. Om datorn inte är registrerad visas ett meddelande med instruktioner om hur du registrerar.

4.   Under **Webbläsaråtkomst** till SharePoint Online och OneDrive för företag kan du välja att tillåta åtkomst till Exchange Online endast genom de webbläsare som stöds: Safari (iOS) och Chrome (Android). Åtkomst från andra webbläsare kommer att blockeras.  De plattformsbegränsningar du valde för programåtkomst för OneDrive gäller även här.

  På **Android**-enheter måste användare aktivera webbläsaråtkomst.  Om du vill göra detta måste slutanvändaren aktivera alternativet "Aktivera webbläsaråtkomst" på den registrerade enheten enligt följande:
  1.    Starta **företagsportalappen**.
  2.    Gå till sidan **Inställningar** från de tre punkterna (…) eller knappen för maskinvara.
  3.    Tryck på knappen **Aktivera webbläsaråtkomst**.
  4.  I webbläsaren Chrome loggar du ut från Office 365 och startar om Chrome.

  På **iOS- och Android**-plattformar kommer för Azure Active Directory att utfärda ett TLS-certifikat (Transport layer security) för enheten för att identifiera den enhet som används för att få åtkomst till tjänsten.  Enheten visar certifikatet med en uppmaning till slutanvändaren om att markera certifikatet på det sätt som visas i skärmbilderna nedan. Slutanvändaren måste välja detta certifikat innan det går att fortsätta med att använda webbläsaren.

  **iOS**

  ![skärmbild av certifikatuppmaning på en ipad](../media/mdm-browser-ca-ios-cert-prompt.png)

  **Android**

  ![skärmbild av certifikatuppmaning på en Android-enhet](../media/mdm-browser-ca-android-cert-prompt.png)
5.  Under **Målgrupper**, välj **Modifiera** för att välja de Azure Active Directory-säkerhetsgrupper som principen ska gälla för. Du kan välja att rikta detta till alla användare eller bara vissa grupper med användare.

6.  Under **Undantagna Grupper** kan du alternativt välja **Modifiera** om det finns säkerhetsgrupper i Azure Active Directory som ska vara undantagna principen.

6.  När du är klar väljer du **Spara**.

Du behöver inte använda den villkorliga åtkomstpolicyn, den träder i kraft omedelbart.

### Steg 4: Övervaka efterlevnaden och principer för villkorlig åtkomst
På arbetsytan **Grupper** kan du visa enheternas status.

Välj en mobil enhetsgrupp och klicka på **enheter** -fliken, där väljer du något av följande **Filter**:

-   **Enheter som inte är registrerade i AAD** – Enheterna blockeras från SharePoint Online.

-   **Enheter som inte är godkända** – Enheterna blockeras från SharePoint Online.

-   **Enheter som är registrerade i AAD samt godkända** – Enheterna kan komma åt SharePoint Online.

### Se även
[Begränsa åtkomsten till e-post och O365-tjänster med Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Oct16_HO1-->


