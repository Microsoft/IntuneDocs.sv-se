---
title: "Villkorlig åtkomstpolicy för Exchange On-premises| Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Hur du kan konfigurera villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 581f9be824ea883fd0208abc3b2ecc09174cb911
ms.openlocfilehash: a80d6a19948291cc80e42ad5a9a2f016effb2f37


---

# <a name="how-to-create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated-in-microsoft-intune-azure-preview"></a>Så här skapar du en princip för villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i förhandsversionen av Microsoft Intune Azure


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Den här artikeln vägleder dig genom processen med att konfigurera villkorlig åtkomst för Exchange On-premises baserat på enhetsefterlevnad.

Om du har en Exchange Online Dedicated-miljö och vill veta om du har den nya eller gamla konfigurationen kontaktar du din kontoansvariga. Du kontrollerar e-poståtkomsten till Exchange On-premises eller till den äldre Exchange Online Dedicated-miljön genom att konfigurera villkorlig åtkomst till Exchange On-premises i Intune.

## <a name="prerequisites"></a>Förutsättningar

**Innan** du konfigurerar villkorlig åtkomst kontrollerar du följande:

- Din Exchange-version måste vara **Exchange 2010 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.
- Du måste använda **Exchange Active Sync:s lokala Exchange Connector** som ansluter Intune till Microsoft Exchange On-premises. Mer information om anslutaren finns i <link>

  - Intune-konsolens lokala Exchange Connector är specifik för din Intune-klientorganisation och kan inte användas med andra innehavare. Kontrollera också att Exchange-anslutningsappen för din klient är installerad **på endast en dator**.

Den här anslutningen bör hämtas från Intune-administrationskonsolen. En genomgång om hur du konfigurerar den lokala Exchange-anslutningen finns i <link to new topic>

Anslutningen kan installeras på valfri dator, förutsatt att datorn kan kommunicera med Exchange-servern.

- Anslutningen stöder **Exchange CAS-miljön**. Tekniskt sett kan du installera anslutningen på Exchange CAS-servern direkt om du vill, men det rekommenderas inte eftersom det ökar belastningen på servern. När du konfigurerar anslutningen måste du ställa in den så att den kommunicerar med en av Exchange CAS-servrarna.
- **Exchange ActiveSync** måste konfigureras med certifikatbaserad autentisering eller genom att användaren anger autentiseringsuppgifter.

Innan en användare kan ansluta till sin e-post när principer för villkorlig åtkomst har konfigurerats och tillämpats på användaren måste användarens **enhet**:

- Vara antingen **registrerad** med Intune eller en domänansluten dator.
- **Registreras i Azure Active Directory**. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.

AAD DRS aktiveras automatiskt för Intune och Office 365-kunder. Kunder som redan har använt AD FS Device Registration Service ser inte registrerade enheter i sina lokala Active Directory-kataloger. **Detta gäller inte för Windows-datorer och Windows Phone-enheter**.

- **Kompatibel** med alla efterlevnadspolicyer för Intune som distribuerats till enheten.

Om en enhet inte uppfyller inställningarna för villkorlig åtkomst visas något av följande meddelanden när användaren loggar in:

- Om enheten inte är registrerad i Intune eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med enhetsposten i Azure Active Directory.
- Om enheten inte är godkänd visas ett meddelande som leder användaren till webbplatsen för Intune-företagsportalen eller företagsportalappen där de kan hitta information om problemet och hur det kan åtgärdas.

## <a name="support-for-mobile-devices"></a>Stöd för mobila enheter

- Windows Phone 8.1 och senare
- Intern e-postapp för iOS.
- EAS-e-postklienter som Gmail på Android 4 eller senare.
- EAS-e-postklienter och **Android for Work-enheter:** Endast **Gmail** och **Nine Work**-appar i **arbetsprofilen** stöds på Android for Work-enheter. För villkorlig åtkomst till arbete med Android for Work måste du distribuera en e-postprofil för Gmail eller Nine Work-appen och distribuera de apparna som en nödvändig installation.

>[!NOTE]
>Microsoft Outlook-appen for Android and iOS stöds inte.

> Android for Work distribueras för närvarande på Intune-innehavare under de kommande månaderna.

Om du vill ha mer information om statusen för Android for Work-stöd läser du Android for Work-meddelandet i oktober 2016-utgåvan av [Nyheter i Microsoft Intune](https://docs.microsoft.com/en-us/intune/whats-new/whats-new-archive#october-2016).

## <a name="support-for-pcs"></a>Stöd för datorer

**E-post**-programmet i Windows 8.1 och senare (om det har registrerats med Intune)


## <a name="configure-exchange-on-premises-access"></a>Konfigurera Exchange On-Premises-åtkomst

1. Välj arbetsbelastningen **Villkorlig åtkomst** i Azure-portalen för att öppna bladet lokalt.
2. Bladet **Lokalt** visar status för princip för villkorlig åtkomst och de enheter som påverkas av den.
3. Under **Hantera**, väljer du **Åtkomst till Exchange On-Premises**.
4. På bladet **Åtkomst till Exchange On-Premises** väljer du **Ja** för att aktivera åtkomstkontroll för Exchange On-Premises.

  >[!NOTE]
  >Det här alternativet inaktiveras om du inte har konfigurerat lokal anslutning för Exchange Active Sync.  Du måste först installera och konfigurera den här anslutningen innan du aktiverar villkorlig åtkomst för Exchange On-Premises. Du hittar mer information i [Installera Intune On-premises Exchange Connector](install-intune-on-premises-exchange-connector.md)

5. Under **Tilldelning**, väljer du **Inkluderade grupper**.  Använd den säkerhetsgrupp för användare där villkorlig åtkomst ska tillämpas.  Detta skulle innebära att användarna måste registrera sina enheter i Intune och vara kompatibla med kompatibilitetsprofiler.
6. Om du vill exkludera en viss grupp av användare kan du göra detta genom att välja **Undantagna grupper** och välja en grupp som du vill ska vara undantagen från registrering av enheter och efterlevnad.
7. Under **Inställningar**, väljer du **Användarmeddelanden** för att ändra standard-e-postmeddelandet. Det här meddelandet skickas till användarna om deras enhet inte är kompatibel och de vill få åtkomst till Exchange On-Premises. Meddelandemallen använder Markup Language.  Du kan även se förhandsversionen av hur meddelandet visas när du skriver. Läs mer om Markup Language i den här [artikeln](https://en.wikipedia.org/wiki/Markup_language) på Wikipedia.
8. På sidan **Avancerade åtkomstinställningar för Exchange Active Sync**, anger du den globala standardregeln för åtkomst från enheter som inte hanteras av Intune och för regler på plattformsnivå såsom beskrivs i följande två steg.
9. För en enhet som inte påverkas av villkorlig åtkomst eller andra regler kan du välja att få åtkomst till Exchange eller blockera den.
  - När du ställer in det här alternativet för att tillåta åtkomst kommer alla enheter att kunna komma åt Exchange On-Premises omedelbart.  Enheter som tillhör användare i **Inkluderade grupper**, blockeras om de senare utvärderas till att inte vara kompatibla med efterlevnadsprinciperna eller inte har registrerats i Intune.
  - När du ställer in det här alternativet för att blockera åtkomst kommer alla enheter omedelbart att blockeras från att komma åt Exchange On-Premises från början.  Enheter som tillhör användare i **Inkluderade grupper** får åtkomst först när enheten har registrerats i Intune och utvärderats som kompatibel. Android-enheter som inte kör Samsung KNOX blockeras alltid eftersom de inte stöder den här inställningen.
10. Under **Undantag för plattformsenhet**, väljer du **Lägg till** för att ange plattformarna. Om inställningen **Ohanterad enhetsåtkomst** är angiven till **blockerad**, kommer enheter som är registrerade och godkända tillåtas även om det finns ett plattformsundantag som ska blockeras. Välj **OK** för att spara inställningarna.
11. På bladet **Lokalt**, klickar du på **Spara** för att spara principen för villkorlig åtkomst.



<!--HONumber=Feb17_HO1-->


