---
# required metadata

title: Begränsa åtkomsten till SharePoint Online | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Begränsa åtkomsten till SharePoint Online med Microsoft Intune
Använd villkorlig åtkomst i [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] om du vill kontrollera åtkomsten till filer i SharePoint Online.
Villkorlig åtkomst består av två komponenter:
- Principen för enhetsefterlevnad som enheten måste uppfylla för att anses vara kompatibel.
- Principen för villkorlig åtkomst där du anger de villkor som enheten måste uppfylla för att komma åt tjänsten.
Mer information om hur villkorlig åtkomst fungerar finns i avsnittet [Begränsa åtkomsten till e-post och O365-tjänster](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

När en användare försöker ansluta till en fil med en app som stöds, till exempel OneDrive på sin enhet, görs följande utvärdering:

![Diagram som visar beslutspunkterna som avgör om en enhet får åtkomst till SharePoint eller blockeras ](../media/ConditionalAccess8-6.png)

>[!IMPORTANT]
>Villkorlig åtkomst för datorer och Windows 10 Mobile-enheter med appar som använder modern autentisering är inte tillgängligt för alla Intune-kunder för närvarande. Om du redan använder dessa funktioner behöver du inte göra något. Du kan fortsätta använda dem.

>Om du inte har skapat principer för villkorlig åtkomst för datorer eller Windows 10 Mobile för appar som använder modern autentisering och vill göra det, måste du skicka en begäran.  Mer information om kända problem och hur du får åtkomst till den här funktionen finns på [Connect-webbplatsen](http://go.microsoft.com/fwlink/?LinkId=761472).

**Innan** du konfigurerar en princip för villkorlig åtkomst för SharePoint Online måste du:
- Ha en **SharePoint Online-prenumeration**, och användarna måste ha licens för SharePoint Online.
- Ha en prenumeration på **Enterprise Mobility Suite** eller **Azure Active Directory Premium**.

  För att kunna ansluta till de nödvändiga filerna måste enheten:
-   Vara **registrerad** i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] eller vara en domänansluten dator.

-   **Registrera enheten** i Azure Active Directory (detta sker automatiskt när enheten registreras med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]).


-   Vara kompatibel med eventuella [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-efterlevnadsprinciper

Enhetens tillstånd lagras i Azure Active Directory som beviljar eller blockerar tillgång till filerna baserat på de villkor du angivit.

Om ett villkor inte är uppfyllt, kommer användaren att visas ett följande meddelanden när de loggar in:

-   Om enheten inte är registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], eller om den inte är registrerad i Azure Active Directory, så visas ett meddelande med instruktioner om hur du installerar företagsportalappen och registrerar dig.

-   Om enheten inte är kompatibel visas ett meddelande som leder användaren till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-företagsportalens webbplats, som innehåller mer information om problemet och hur det kan åtgärdas.

## Stöd för mobila enheter
- iOS 7.1 och senare
- Android 4.0 och senare, Samsung Knox Standard 4.0 eller senare
- Windows Phone 8.1 och senare

## Stöd för datorer
- Windows 8.1 och senare (efter att ha registrerats i Intune)
- Windows 7.0 eller Windows 8.1 (om datorn är domänansluten)

  - Domänanslutna datorer måste vara konfigurerade att [registreras automatiskt](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) med Azure Active Directory.
AAD DRS aktiveras automatiskt för Intune och Office 365-kunder. Kunder som redan har använt AD FS Device Registration Service ser inte registrerade enheter i sina lokala Active Directory-kataloger.

  - Om principen är konfigurerad att kräva domänanslutning och datorn inte är domänansluten visas ett meddelande som uppmanar användaren att kontakta IT-administratören.

  - Om principen är konfigurerad att kräva domänsanslutning eller efterlevnad och datorn inte uppfyller något av kraven visas ett meddelande med instruktioner som hjälper användaren att installera företagsportalappen och registrera sig.
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

> [!NOTE] Medan efterlevnadsprinciper distribueras till [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]-grupper är principer för villkorlig åtkomst avsedda för Azure Active Directory-säkerhetsgrupper.

Mer information om hur du konfigurerar efterlevnadsprincipen finns i [Skapa en efterlevnadsprincip](create-a-device-compliance-policy-in-microsoft-intune.md).

> [!IMPORTANT] Om du inte har distribuerat någon efterlevnadsprincip behandlas enheterna som kompatibla.

När du är klar, fortsätt till **Steg 3**.

### Steg 3: Ställ in SharePoint Online-principen
Konfigurera sedan policyn som kräver att enbart hanterade och godkända enheter kan komma åt SharePoint Online. Denna policy kommer att lagras i Azure Active Directory.

#### <a name="bkmk_spopolicy"></a>

1.  I [Microsoft Intune Administrationskonsol](https://manage.microsoft.com) klickar du på **Princip** > **Villkorlig åtkomst** > **SharePoint Online-princip**.
![Skärmbild av sidan SharePoint Online-princip](../media/IntuneSASharePointOnlineCAPolicy.png)

2.  Välj **Aktivera princip för villkorlig åtkomst för SharePoint Online**.

3.  Under **Programåtkomst** kan du välja att använda principen för villkorlig åtkomst för:

    -   **Alla plattformar**

        Detta kräver att alla enheter som används för att komma åt **SharePoint Online** registreras i Intune och att de uppfyller principkraven.  Klientprogram som använder **modern autentisering** omfattas av principen för villkorlig åtkomst. Om plattformen inte stöds av Intune för närvarande blockeras åtkomsten till **SharePoint Online**.
        >[!TIP]
        >Du kanske inte ser det här alternativet om du inte redan använder villkorlig åtkomst för datorer.  Använd **Specifika plattformar** i stället. Villkorlig åtkomst för datorer är inte tillgängligt för alla Intune-kunder för närvarande.   Mer information om kända problem och hur du får åtkomst till den här funktionen finns på [webbplatsen för Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=761472).

    -   **Vissa plattformar**

         Principen för villkorlig åtkomst gäller alla klientappar som använder modern autentisering på de plattformar som du anger.

     För Windows-datorer måste datorn antingen vara domänansluten eller registrerad i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och kompatibel. Du kan ange följande krav:

     -   **Enheter måste vara domänanslutna eller kompatibla.** Välj det här alternativet om du vill att datorerna antingen ska vara domänanslutna eller kompatibla med principer som angetts i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Om datorn inte uppfyller något av dessa krav ombeds användaren att registrera enheten i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

     -   **Enheter måste vara domänanslutna.** Välj det här alternativet om du vill kräva att datorerna ska vara domänanslutna för att få åtkomst till Exchange Online. Om datorn inte är domänansluten blockeras åtkomsten till e-posten och användaren uppmanas att kontakta IT-administratören.

     -   **Enheter måste vara godkända.** Välj det här alternativet om du vill kräva att datorerna ska vara registrerade i [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] och kompatibla. Om datorn inte är registrerad visas ett meddelande med instruktioner om hur du registrerar.

4.  Under **Målgrupper**, klicka på **Modifiera** för att välja de Azure Active Directory säkerhetsgrupper som policyn ska gälla för. Du kan välja att rikta detta till alla användare eller bara vissa grupper med användare.

5.  Under **Undantagna Grupper**, kan du alternativt klicka på **Modifiera** om det finns säkerhetsgrupper i Azure Active Directory som ska vara undantagna policyn.

6.  När du är klar klicka på **Spara**.

Du behöver inte använda den villkorliga åtkomstpolicyn, den träder i kraft omedelbart.

### Steg 4: Övervaka efterlevnaden och principer för villkorlig åtkomst
På arbetsytan **Grupper** kan du visa enheternas status.

Välj en mobil enhetsgrupp och klicka på **enheter** -fliken, där väljer du något av följande **Filter**:

-   **Enheter som inte är registrerade i AAD** – Enheterna blockeras från SharePoint Online.

-   **Enheter som inte är godkända** – Enheterna blockeras från SharePoint Online.

-   **Enheter som är registrerade i AAD samt godkända** – Enheterna kan komma åt SharePoint Online.

### Se även
[Begränsa åtkomsten till e-post och O365-tjänster med Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


