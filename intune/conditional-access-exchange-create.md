---
title: Skapa en Exchange-princip för villkorlig åtkomst
titlesuffix: Microsoft Intune
description: Konfigurera villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 0a539000153ad45b5256e4e63086fa72fee44947
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186111"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Skapa en villkorlig åtkomstprincip för Exchange lokalt och äldre Exchange Online Dedicated

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs hur du konfigurerar villkorlig åtkomst för Exchange lokalt baserat på enhetsefterlevnad.

Om du har en Exchange Online Dedicated-miljö och vill veta om du har den nya eller gamla konfigurationen kontaktar du din kontoansvariga. Du kontrollerar e-poståtkomsten till Exchange On-premises eller till den äldre Exchange Online Dedicated-miljön genom att konfigurera villkorlig åtkomst till Exchange On-premises i Intune.

## <a name="before-you-begin"></a>Innan du börjar

Innan du kan konfigurera villkorlig åtkomst måste du kontrollera följande:

- Din Exchange-version måste vara **Exchange 2010 SP1 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.

- Du måste använda [Exchange Active Syncs lokala Exchange Connector](exchange-connector-install.md) som ansluter Intune till Exchange lokalt.

    >[!IMPORTANT]
    >Den lokala Exchange-anslutningen är specifik för din Intune-klient och kan inte användas med någon annan klient. Intune har nu stöd för flera lokala Exchange-anslutningar per prenumeration. Om du har fler än en lokal Exchange-organisation kan du ställa in en separat anslutningsapp för varje Exchange-organisation.

- Anslutningsappen för en lokal Exchange-organisation kan installeras på valfri dator, förutsatt att datorn kan kommunicera med Exchange-servern.

- Anslutningen stöder **Exchange CAS-miljön**. Tekniskt sett kan du installera anslutningsprogrammet på Exchange CAS-servern direkt om du vill, men det rekommenderas inte eftersom det ökar belastningen på servern. När du konfigurerar anslutningen måste du ställa in den så att den kommunicerar med en av Exchange CAS-servrarna.

- **Exchange ActiveSync** måste konfigureras med certifikatbaserad autentisering eller genom att användaren anger autentiseringsuppgifter.

- Innan en användare kan ansluta till sin e-post när principer för villkorlig åtkomst har konfigurerats och tillämpats på användaren måste användarens **enhet**:
    - Vara antingen **registrerad** med Intune eller en domänansluten dator.
    - **Registreras i Azure Active Directory**. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.
<br></br>
- Azure AD DRS (Device Registration Service) aktiveras automatiskt för Intune- och Office 365-kunder. Kunder som redan har distribuerat ADFS Device Registration Service ser inte registrerade enheter i sin lokala Active Directory. **Detta gäller inte för Windows-datorer och Windows Phone-enheter**.

- **Kompatibel** med de efterlevnadsprinciper som distribueras till enheten.

- Om en enhet inte uppfyller inställningarna för villkorlig åtkomst visas något av följande meddelanden när användaren loggar in:
    - Om enheten inte är registrerad i Intune eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med enhetsposten i Azure Active Directory.
    - Om enheten inte är godkänd visas ett meddelande som leder användaren till webbplatsen för Intune-företagsportalen eller företagsportalappen där de kan hitta information om problemet och hur det kan åtgärdas.

### <a name="support-for-mobile-devices"></a>Stöd för mobila enheter

- Windows Phone 8.1 och senare
- Intern e-postapp för iOS.
- EAS-e-postklienter som Gmail på Android 4 eller senare.
- EAS-e-postklienter och **Android-arbetsprofilenheter:** Endast **Gmail** och **Nine Work for Android Enterprise** i **arbetsprofilen** stöds på Android-arbetsprofilenheter. För villkorlig åtkomst till arbete med Android-arbetsprofiler måste du distribuera en e-postprofil för Gmail eller Nine Work for Android Enterprise-appen och distribuera de apparna som en nödvändig installation.

> [!NOTE]
> Microsoft Outlook för Android och iOS stöds inte via den lokala Exchange-anslutningsappen. Om du vill dra nytta av principerna för villkorsstyrd åtkomst för Azure Active Directory och Intune-appskydd med Outlook för iOS och Android för dina lokala postlådor bör du läsa [Använda modern hybridautentisering med Outlook för iOS och Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth). 

### <a name="support-for-pcs"></a>Stöd för datorer

Det interna **e-postprogrammet** i Windows 8.1 och senare (om det har registrerats med Intune)


## <a name="configure-exchange-on-premises-access"></a>Konfigurera Exchange On-Premises-åtkomst

1. Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

1. När du har loggat in visas **Azure-instrumentpanelen**.

1. Välj  **Alla tjänster**  på den vänstra menyn och skriv sedan  **Intune**  i textrutans filter.

1. Välj  **Intune**. **Intune-instrumentpanelen** visas.

1. Välj **Lokal åtkomst**. Fönstret **Lokal åtkomst** visar status för den villkorliga åtkomstprincipen och de enheter som påverkas av den.

1. Under **Hantera**, väljer du **Åtkomst till Exchange On-Premises**.

1. I fönstret **Exchange on-premises access** (Åtkomst till Exchange lokalt) väljer du **Ja** för att aktivera åtkomstkontroll för Exchange lokalt.

    > [!NOTE]
    > Det här alternativet inaktiveras om du inte har konfigurerat någon lokal anslutningsapp för Exchange Active Sync.  Du måste först installera och konfigurera minst en sådan här anslutning innan du aktiverar villkorlig åtkomst för Exchange On-Premises. Du hittar mer information i [Installera Intune On-premises Exchange Connector](exchange-connector-install.md)

1. Under **Tilldelning**, väljer du **Inkluderade grupper**.  Använd den säkerhetsgrupp för användare där villkorlig åtkomst ska tillämpas. Den här åtgärden innebär att användarna måste registrera sina enheter i Intune och följa kompatibilitetsprofilerna.

1. Om du vill exkludera en viss grupp av användare kan du göra detta genom att välja **Undantagna grupper** och välja en grupp som du vill ska vara undantagen från registrering av enheter och efterlevnad.

1. Under **Inställningar**, väljer du **Användarmeddelanden** för att ändra standard-e-postmeddelandet. Det här meddelandet skickas till användarna om deras enhet inte är kompatibel och de vill få åtkomst till Exchange On-Premises. Meddelandemallen använder Markup Language.  Du kan även se en förhandsgranskning av hur meddelandet blir medan du skriver.
    > [!TIP]
    > Läs mer om Markup Language i den här [artikeln](https://en.wikipedia.org/wiki/Markup_language) på Wikipedia.

1. I fönstret med **avancerade åtkomstinställningar för Exchange Active Sync** anger du den globala standardregeln för åtkomst från enheter som inte hanteras av Intune, samt för regler på plattformsnivå som beskrivs i de kommande två stegen.

1. För en enhet som inte påverkas av villkorlig åtkomst eller andra regler kan du välja att få åtkomst till Exchange eller blockera den.

   - När du ställer in det här alternativet för att tillåta åtkomst kommer alla enheter att få åtkomst till Exchange lokalt omedelbart.  Enheter som tillhör användare i **Inkluderade grupper**, blockeras om de senare utvärderas till att inte vara kompatibla med efterlevnadsprinciperna eller inte har registrerats i Intune.
   - När du ställer in det här alternativet för att blockera åtkomst kommer alla enheter omedelbart att blockeras från att komma åt Exchange lokalt till att börja med.  Enheter som tillhör användare i **Grupper som omfattas** får åtkomst när enheten har registrerats i Intune och utvärderats som kompatibel. Android-enheter som inte kör Samsung Knox Standard blockeras alltid eftersom de inte stöder den här inställningen.

1. Under **Undantag för plattformsenhet**, väljer du **Lägg till** för att ange plattformarna. Om inställningen **Åtkomst för ohanterad enhet** är angiven till **Blockerad** kommer enheter som är registrerade och kompatibla att tillåtas, även om det finns ett plattformsundantag som ska blockeras. Välj **OK** för att spara inställningarna.

1. I fönstret **Lokalt** klickar du på **Spara** för att spara den villkorliga åtkomstprincipen.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Skapa principer för villkorlig åtkomst för Azure AD i Intune

Från och med version 1704 av Intune kan administratörer skapa villkorliga åtkomstprinciper för Azure AD från Intune Azure-portalen, så du behöver inte växla mellan Azure- och Intune-arbetsbelastningarna.

> [!IMPORTANT]
> Du måste ha en Azure AD Premium-licens för att kunna skapa Azure AD-principer för villkorlig åtkomst från Intune Azure Portal.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst för Azure AD

1. Välj **villkorlig åtkomst** på **Intune-instrumentpanelen**.

2. I fönstret **Principer** väljer du **Ny princip** om du vill skapa en ny Azure AD-princip för villkorlig åtkomst.

## <a name="see-also"></a>Se även

[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
