---
title: Skapa en Exchange-princip för villkorlig åtkomst
titleSuffix: Microsoft Intune
description: Konfigurera villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 644297777e8a103d6ffdc5f025ebf8f29591fda8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188460"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Skapa en villkorlig åtkomstprincip för Exchange lokalt och äldre Exchange Online Dedicated

I den här artikeln beskrivs hur du konfigurerar villkorlig åtkomst för Exchange lokalt baserat på enhetsefterlevnad.

Om du har en Exchange Online Dedicated-miljö och vill veta om den har den nya eller gamla konfigurationen kontaktar du din kontoansvariga. Du kontrollerar e-poståtkomsten till Exchange On-premises eller till den äldre Exchange Online Dedicated-miljön genom att konfigurera villkorlig åtkomst till Exchange On-premises i Intune.

## <a name="before-you-begin"></a>Innan du börjar

Innan du kan konfigurera villkorlig åtkomst måste du kontrollera att följande inställningar finns:

- Din Exchange-version måste vara **Exchange 2010 SP1 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.

- Du måste ha installerat och använda [Exchange Active Syncs lokala Exchange Connector](exchange-connector-install.md) som ansluter Intune till Exchange lokalt.

    >[!IMPORTANT]  
    >Intune har stöd för flera lokala Exchange-anslutningsappar per prenumeration.  Den lokala Exchange-anslutningen dock är specifik för en enda Intune-klient och kan inte användas med någon annan klient.  Om du har fler än en lokal Exchange-organisation kan du ställa in en separat anslutningsapp för varje Exchange-organisation.

- Anslutningsappen för en lokal Exchange-organisation kan installeras på valfri dator, förutsatt att datorn kan kommunicera med Exchange-servern.

- Anslutningen stöder **Exchange CAS-miljön**. Intune har stöd för direkt installation av anslutningen på Exchange CAS-servern. Vi rekommenderar att du installerar den på en separat dator på grund av den extra belastningen som anslutningen medför på servern. När du konfigurerar anslutningen måste du ställa in den så att den kommunicerar med en av Exchange CAS-servrarna.

- **Exchange ActiveSync** måste konfigureras med certifikatbaserad autentisering eller genom att användaren anger autentiseringsuppgifter.

- Innan en användare kan ansluta till sin e-post när principer för villkorlig åtkomst har konfigurerats och tillämpats på användaren måste användarens **enhet**:
  - Vara antingen **registrerad** med Intune eller en domänansluten dator.
  - **Registreras i Azure Active Directory**. Dessutom måste klientens Exchange ActiveSync-ID registreras med Azure Active Directory.

- Azure AD DRS (Device Registration Service) aktiveras automatiskt för Intune- och Office 365-kunder. Kunder som redan har distribuerat ADFS Device Registration Service ser inte registrerade enheter i sin lokala Active Directory. **Detta gäller inte för Windows-datorer och Windows Phone-enheter**.

- **Kompatibel** med de efterlevnadsprinciper som distribueras till enheten.

- Om en enhet inte uppfyller inställningarna för villkorlig åtkomst visas något av följande meddelanden när användaren loggar in:
  - Om enheten inte är registrerad i Intune eller i Azure Active Directory visas ett meddelande med instruktioner för att installera företagsportalappen, registrera enheten och aktivera e-post. Den här processen associerar även enhetens Exchange ActiveSync-ID med enhetsposten i Azure Active Directory.
  - Om enheten inte är godkänd visas ett meddelande som leder användaren till webbplatsen för Intune-företagsportalen eller företagsportalappen. På företagsportalen hittar man information om problemet och hur det kan åtgärdas.

### <a name="support-for-mobile-devices"></a>Stöd för mobila enheter

- Windows Phone 8.1 och senare
- Intern e-postapp för iOS.
- EAS-e-postklienter som Gmail på Android 4 eller senare.
- EAS-e-postklienter på **Android-arbetsprofilenheter:** Endast **Gmail** och **Nine Work for Android Enterprise** i **arbetsprofilen** stöds på Android-arbetsprofilenheter. För villkorlig åtkomst till arbete med Android-arbetsprofiler måste du distribuera en e-postprofil för Gmail eller Nine Work for Android Enterprise-appen och distribuera de apparna som en nödvändig installation.

> [!NOTE]
> Microsoft Outlook för Android och iOS stöds inte via den lokala Exchange-anslutningsappen. Om du vill dra nytta av principerna för villkorsstyrd åtkomst för Azure Active Directory och Intune-appskydd med Outlook för iOS och Android för dina lokala postlådor bör du läsa [Använda modern hybridautentisering med Outlook för iOS och Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Stöd för datorer

Det interna **e-postprogrammet** i Windows 8.1 och senare (om det har registrerats på MDM med Intune)

## <a name="configure-exchange-on-premises-access"></a>Konfigurera Exchange On-Premises-åtkomst

Innan du kan använda följande procedur för att konfigurera en lokal åtkomstkontroll för Exchange måste du installera och konfigurera minst ett [lokalt Intune Exchange-anslutningsprogram](exchange-connector-install.md) för lokal Exchange.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå till **Innehavaradministratör** > **Exchange-åtkomst** och välj sedan **Åtkomst till Exchange lokalt**.

3. I fönstret **Åtkomst till Exchange lokalt** väljer du **Ja** för att *	Aktivera åtkomstkontroll för Exchange lokalt*.

4. Under **Tilldelning** väljer du **Välj grupper att inkludera** och sedan en eller flera grupper vars åtkomst du vill konfigurera.

   Princip för villkorlig åtkomst för Exchange lokalt har redan tillämpats på de grupper som du har valt. Användare som får den här principen måste registrera sina enheter i Intune och vara kompatibla med efterlevnadsprofilerna innan de kan komma åt Exchange lokalt.

5. Om du vill utesluta grupper väljer du **Välj grupper att undanta** och välj sedan en eller flera grupper som är undantagna från kraven för att registrera enheter och vara kompatibla med efterlevnadsprinciper innan de får åtkomst till Exchange lokalt. 

6. Konfigurera därefter den lokala Exchange-anslutningsappen för Intune.  Under **Konfigurera** i fönstret *Åtkomst till Exchange lokalt* väljer du **Lokalt anslutningsprogram Exchange ActiveSync** och välj sedan anslutningsprogrammet för den Exchange-organisation som du vill konfigurera.

7. Under **Inställningar** väljer du **Användaraviseringar** för att ändra standardmeddelandet som skickas per e-post till användarna om deras enhet inte är kompatibel och de vill ha lokal åtkomst till Exchange. Meddelandemallen använder Markup Language.  Du kan även se en förhandsgranskning av hur meddelandet blir medan du skriver.
   > [!TIP]
   > Läs mer om Markup Language i den här [artikeln](https://en.wikipedia.org/wiki/Markup_language) på Wikipedia.
 
   Välj **OK** för att spara dina ändringar och slutföra konfigurationen av lokal åtkomst till Exchange.

8. Välj sedan **Avancerade åtkomstinställningar för Exchange ActiveSync** för att öppna fönstret *Avancerade åtkomstinställningar för Exchange ActiveSync* där du kan konfigurera regler för enhetsåtkomst:  

   - För **Åtkomst för ej hanterad enhet** ställer du in en global standardinställning för åtkomst från enheter som inte påverkas av villkorlig åtkomst eller andra regler:

     - **Tillåt åtkomst** – alla enheter får åtkomst till Exchange lokalt omedelbart. Enheter som tillhör användare i de konfigurerade grupperna blockeras om de senare utvärderas till att inte vara kompatibla med efterlevnadsprinciperna eller inte har registrerats i Intune.

     - **Blockera åtkomst** och **Karantän** –alla enheter blockeras omedelbart från att komma åt Exchange lokalt till att börja med. Enheter som tillhör användare i de grupper som du har konfigurerat enligt beskrivningen i föregående procedur får åtkomst efter att enheten registrerats i Intune och bedömt som kompatibel. 

       Android-enheter som *inte* kör Samsung Knox Standard blockeras alltid eftersom de inte stöder den här inställningen.

   -  För **Enhetsplattformsundantag** väljer du **Lägg till** och anger sedan den plattformsinformation som krävs för din miljö. 
   
      Om inställningen **Åtkomst för ohanterad enhet** är angiven till **Blockerad** kommer enheter som är registrerade och kompatibla att tillåtas, även om det finns ett plattformsundantag som ska blockeras.  
   
   Klicka på **OK** för att spara dina ändringar.

9. Välj **Spara** för att spara principen för villkorlig åtkomst till Exchange.

Skapa sedan en efterlevnadsprincip och tilldela den till användare så att Intune kan utvärdera deras mobilenheter. Se [Komma igång med enhetsefterlevnad](device-compliance-get-started.md).

## <a name="next-steps"></a>Nästa steg

[Felsöka den lokala Exchange-anslutningsappen för Intune i Microsoft Intune](https://support.microsoft.com/help/4471887)
