---
title: "Skapa och tilldela en lokal princip för villkorlig åtkomst för Exchange"
titlesuffix: Azure portal
description: "Konfigurera villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 02/14/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 70c3de614b0f5ed5075b669ecdffc08e1226817d
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-create-and-assign-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated-in-microsoft-intune"></a>Så här skapar och tilldelar du en princip för villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Den här artikeln vägleder dig genom processen med att konfigurera villkorlig åtkomst för Exchange On-premises baserat på enhetsefterlevnad.

Om du har en Exchange Online Dedicated-miljö och vill veta om du har den nya eller gamla konfigurationen kontaktar du din kontoansvariga. Du kontrollerar e-poståtkomsten till Exchange On-premises eller till den äldre Exchange Online Dedicated-miljön genom att konfigurera villkorlig åtkomst till Exchange On-premises i Intune.

## <a name="before-you-begin"></a>Innan du börjar

Innan du kan konfigurera villkorlig åtkomst måste du kontrollera följande:

- Din Exchange-version måste vara **Exchange 2010 SP1 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.

- Du måste använda [Exchange Active Syncs lokala Exchange Connector](exchange-connector-install.md) som ansluter Intune till Exchange lokalt.

    >[!IMPORTANT]
    >Den lokala Exchange-anslutningen är specifik för din Intune-klient och kan inte användas med någon annan klient. Kontrollera också att Exchange-anslutningsappen för din klient är installerad **på endast en dator**.

- Anslutningen kan installeras på valfri dator, förutsatt att datorn kan kommunicera med Exchange-servern.

- Anslutningen stöder **Exchange CAS-miljön**. Tekniskt sett kan du installera anslutningen på Exchange CAS-servern direkt om du vill, men det rekommenderas inte eftersom det ökar belastningen på servern. När du konfigurerar anslutningen måste du ställa in den så att den kommunicerar med en av Exchange CAS-servrarna.

- **Exchange ActiveSync** måste konfigureras med certifikatbaserad autentisering eller genom att användaren anger autentiseringsuppgifter.

- Innan en användare kan ansluta till sin e-post när principer för villkorlig åtkomst har konfigurerats och tillämpats på användaren måste användarens **enhet**:
    - Vara antingen **registrerad** med Intune eller en domänansluten dator.
    - **Registreras i Azure Active Directory**. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.
<br></br>
- AAD DRS aktiveras automatiskt för Intune och Office 365-kunder. Kunder som redan har använt AD FS Device Registration Service ser inte registrerade enheter i sina lokala Active Directory-kataloger. **Detta gäller inte för Windows-datorer och Windows Phone-enheter**.

- **Kompatibel** med de efterlevnadsprinciper som distribueras till enheten.

- Om en enhet inte uppfyller inställningarna för villkorlig åtkomst visas något av följande meddelanden när användaren loggar in:
    - Om enheten inte är registrerad i Intune eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med enhetsposten i Azure Active Directory.
    - Om enheten inte är godkänd visas ett meddelande som leder användaren till webbplatsen för Intune-företagsportalen eller företagsportalappen där de kan hitta information om problemet och hur det kan åtgärdas.

### <a name="support-for-mobile-devices"></a>Stöd för mobila enheter

- Windows Phone 8.1 och senare
- Intern e-postapp för iOS.
- EAS-e-postklienter som Gmail på Android 4 eller senare.
- EAS-e-postklienter och **Android for Work-enheter:** Endast **Gmail** och **Nine Work**-appar i **arbetsprofilen** stöds på Android for Work-enheter. För villkorlig åtkomst till arbete med Android for Work måste du distribuera en e-postprofil för Gmail eller Nine Work-appen och distribuera de apparna som en nödvändig installation.

> [!NOTE]
> Microsoft Outlook-appen for Android and iOS stöds inte. 

### <a name="support-for-pcs"></a>Stöd för datorer

Det interna **e-postprogrammet** i Windows 8.1 och senare (om det har registrerats med Intune)


## <a name="configure-exchange-on-premises-access"></a>Konfigurera Exchange On-Premises-åtkomst

1. Gå till [Azure Portal](https://portal.azure.com/) och logga in med dina Intune-autentiseringsuppgifter.

2. När du har loggat in visas **Azure-instrumentpanelen**.

3. Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.

4. Välj **Intune**. **Intune-instrumentpanelen** visas.

5. Välj **On-Premise Access** (Lokal åtkomst) och välj sedan

6. Bladet **Lokalt** visar status för princip för villkorlig åtkomst och de enheter som påverkas av den.

7. Under **Hantera**, väljer du **Åtkomst till Exchange On-Premises**.

8. På bladet **Åtkomst till Exchange On-Premises** väljer du **Ja** för att aktivera åtkomstkontroll för Exchange On-Premises.

    > [!NOTE]
    > Det här alternativet inaktiveras om du inte har konfigurerat lokal anslutning för Exchange Active Sync.  Du måste först installera och konfigurera den här anslutningen innan du aktiverar villkorlig åtkomst för Exchange On-Premises. Du hittar mer information i [Installera Intune On-premises Exchange Connector](exchange-connector-install.md)

9. Under **Tilldelning**, väljer du **Inkluderade grupper**.  Använd den säkerhetsgrupp för användare där villkorlig åtkomst ska tillämpas. Detta skulle innebära att användarna måste registrera sina enheter i Intune och vara kompatibla med kompatibilitetsprofiler.

10. Om du vill exkludera en viss grupp av användare kan du göra detta genom att välja **Undantagna grupper** och välja en grupp som du vill ska vara undantagen från registrering av enheter och efterlevnad.

11. Under **Inställningar**, väljer du **Användarmeddelanden** för att ändra standard-e-postmeddelandet. Det här meddelandet skickas till användarna om deras enhet inte är kompatibel och de vill få åtkomst till Exchange On-Premises. Meddelandemallen använder Markup Language.  Du kan även se förhandsversionen av hur meddelandet visas när du skriver.
    > [!TIP]
    > Läs mer om Markup Language i den här [artikeln](https://en.wikipedia.org/wiki/Markup_language) på Wikipedia.

12. På sidan **Avancerade åtkomstinställningar för Exchange Active Sync**, anger du den globala standardregeln för åtkomst från enheter som inte hanteras av Intune och för regler på plattformsnivå såsom beskrivs i följande två steg.

13. För en enhet som inte påverkas av villkorlig åtkomst eller andra regler kan du välja att få åtkomst till Exchange eller blockera den.
  - När du ställer in det här alternativet för att tillåta åtkomst kommer alla enheter att kunna komma åt Exchange On-Premises omedelbart.  Enheter som tillhör användare i **Inkluderade grupper**, blockeras om de senare utvärderas till att inte vara kompatibla med efterlevnadsprinciperna eller inte har registrerats i Intune.
  - När du ställer in det här alternativet för att blockera åtkomst kommer alla enheter omedelbart att blockeras från att komma åt Exchange On-Premises från början.  Enheter som tillhör användare i **Inkluderade grupper** får åtkomst först när enheten har registrerats i Intune och utvärderats som kompatibel. Android-enheter som inte kör Samsung Knox blockeras alltid eftersom de inte stöder den här inställningen.
<br></br>
14. Under **Undantag för plattformsenhet**, väljer du **Lägg till** för att ange plattformarna. Om inställningen **Ohanterad enhetsåtkomst** är angiven till **blockerad**, kommer enheter som är registrerade och godkända tillåtas även om det finns ett plattformsundantag som ska blockeras. Välj **OK** för att spara inställningarna.

15. På bladet **Lokalt**, klickar du på **Spara** för att spara principen för villkorlig åtkomst.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Skapa principer för villkorlig åtkomst för Azure AD i Intune

Från och med version 1704 av Intune kan administratörer skapa principer för villkorlig åtkomst för Azure AD från Intune Azure Portal, vilket ger högre bekvämlighet eftersom du inte behöver växla mellan Azure och Intune-arbetsbelastningar.

> [!IMPORTANT]
> Du måste ha en Azure AD Premium-licens för att kunna skapa Azure AD-principer för villkorlig åtkomst från Intune Azure Portal.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst för Azure AD

1. Välj **villkorlig åtkomst** på **Intune-instrumentpanelen**.

2. På bladet **Principer** väljer du **Ny princip** om du vill skapa en ny Azure AD-princip för villkorlig åtkomst.

## <a name="see-also"></a>Se även

[Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
