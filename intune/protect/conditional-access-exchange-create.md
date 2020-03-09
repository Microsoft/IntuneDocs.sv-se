---
title: Skapa en Exchange-princip för villkorlig åtkomst
titleSuffix: Microsoft Intune
description: Konfigurera villkorlig åtkomst för Exchange On-premises och den äldre Exchange Online Dedicated i Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/26/2020
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
ms.openlocfilehash: 6650c091917ea265783044efd78b19a7e032e6a7
ms.sourcegitcommit: 5511b4f2b8a3383176a7afe2a22ad5a8d42caf7b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169305"
---
# <a name="configure-exchange-on-premises-access-for-intune"></a>Konfigurera lokal Exchange-åtkomst för Intune

I den här artikeln beskrivs hur du konfigurerar villkorlig åtkomst för Exchange lokalt baserat på enhetsefterlevnad.

Om du har en Exchange Online Dedicated-miljö och vill veta om den har den nya eller gamla konfigurationen kontaktar du din kontoansvariga. Du kontrollerar e-poståtkomsten till Exchange On-premises eller till den äldre Exchange Online Dedicated-miljön genom att konfigurera villkorlig åtkomst till Exchange On-premises i Intune.

## <a name="before-you-begin"></a>Innan du börjar

Innan du kan konfigurera villkorlig åtkomst måste du kontrollera att följande inställningar finns:

- Din Exchange-version måste vara **Exchange 2010 SP1 eller senare**. Matrisen för Exchange Server-klientåtkomstservern (CAS) stöds.

- Du har installerat och använt [Exchange Active Syncs lokala Exchange-anslutningsprogram](exchange-connector-install.md) som ansluter Intune till Exchange lokalt.

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

- **Windows Phone 8.1 och senare** – om du vill skapa princip för villkorsstyrd åtkomst läser du [Skapa principer för villkorlig åtkomst](../protect/create-conditional-access-intune.md)
- **Intern e-postapp för iOS/iPadOS** – om du vill skapa princip för villkorsstyrd åtkomst läser du [Skapa principer för villkorlig åtkomst](../protect/create-conditional-access-intune.md)
- **EAS-e-postklienter såsom Gmail på Android 4 eller senare** – om du vill skapa princip för villkorsstyrd åtkomst läser du [Skapa principer för villkorlig åtkomst](../protect/create-conditional-access-intune.md)

- **EAS-e-postklienter och Android-arbetsprofilenheter** – endast *Gmail* och *Nine Work for Android Enterprise* stöds på Android-arbetsprofilenheter. För villkorsstyrd åtkomst till arbete med Android-arbetsprofiler måste du distribuera en e-postprofil för *Gmail* eller *Nine Work for Android Enterprise*-appen och distribuera de apparna som en nödvändig installation. När du har distribuerat appen kan du konfigurera enhetsbaserad villkorsstyrd åtkomst.

#### <a name="to-set-up-conditional-access-for-android-work-profile-devices"></a>Konfigurera villkorsstyrd åtkomst för Android-arbetsprofilenheter

  1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Distribuera Gmail- eller Nine Work-appen som **Obligatorisk**.

  3. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil** och ange **Namn** och **Beskrivning** för profilen.

  4. Välj **Android Enterprise** i **Plattform** och välj **E-post** i **Profiltyp**.

  5. Konfigurera [inställningarna för e-postprofil](https://docs.microsoft.com/intune/configuration/email-settings-android-enterprise#android-enterprise).

  6. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

  7. När du har skapat e-postprofilen [tilldelar du den till grupper](https://docs.microsoft.com/intune/device-profile-assign).

  8. Konfigurera [enhetsbaserad villkorsstyrd åtkomst](https://docs.microsoft.com/intune/protect/conditional-access-intune-common-ways-use#device-based-conditional-access).

> [!NOTE]
> Microsoft Outlook för Android och iOS/iPadOS stöds inte via den lokala Exchange-anslutningsappen. Om du vill dra nytta av principerna för villkorsstyrd åtkomst för Azure Active Directory och Intune-appskydd med Outlook för iOS/iPadOS och Android för dina lokala postlådor bör du läsa [Använda modern hybridautentisering med Outlook för iOS/iPadOS och Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

### <a name="support-for-pcs"></a>Stöd för datorer

Det interna **e-postprogrammet** i Windows 8.1 och senare (om det har registrerats på MDM med Intune)

## <a name="configure-exchange-on-premises-access"></a>Konfigurera Exchange On-Premises-åtkomst

Innan du kan använda följande procedur för att konfigurera en lokal åtkomstkontroll för Exchange måste du installera och konfigurera minst ett [lokalt Intune Exchange-anslutningsprogram](exchange-connector-install.md) för lokal Exchange.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå till **Innehavaradministratör** > **Exchange-åtkomst** och välj sedan **Åtkomst till Exchange lokalt**.

3. I fönstret **Åtkomst till Exchange lokalt** väljer du **Ja** för att *	Aktivera åtkomstkontroll för Exchange lokalt*.

   > [!div class="mx-imgBorder"]
   > ![Exempel på skärmbild av den lokala Exchange-åtkomstskärmen](./media/conditional-access-exchange-create/exchange-on-premises-access.png)

4. Under **Tilldelning** väljer du **Välj grupper att inkludera** och sedan en eller flera grupper vars åtkomst du vill konfigurera.

   Princip för villkorlig åtkomst för Exchange lokalt har redan tillämpats på de grupper som du har valt. Användare som får den här principen måste registrera sina enheter i Intune och vara kompatibla med efterlevnadsprofilerna innan de kan komma åt Exchange lokalt.

   > [!div class="mx-imgBorder"]
   > ![Välj de grupper som ska inkluderas](./media/conditional-access-exchange-create/select-groups.png)

5. Om du vill utesluta grupper väljer du **Välj grupper att undanta** och välj sedan en eller flera grupper som är undantagna från kraven för att registrera enheter och vara kompatibla med efterlevnadsprinciper innan de får åtkomst till Exchange lokalt.

   Välj **Spara** om du vill spara konfigurationen och gå tillbaka till **Exchange-åtkomst**fönstret.

6. Konfigurera därefter den lokala Exchange-anslutningsappen för Intune. Välj **Klientadministration** > **Exchange-åtkomst**> **Lokalt anslutningsprogram för Exchange ActiveSync** och välj sedan anslutningsprogrammet för den Exchange-organisation som du vill konfigurera.

7. Öppna arbetsflödet **Redigera organisation** genom att välja **Redigera** för **Användarmeddelanden**, varefter du kan ändra meddelandet *Användaravisering*.

   > [!div class="mx-imgBorder"]
   > ![Exempel på skärmbild av arbetsflödet Redigera organisation för meddelanden](./media/conditional-access-exchange-create/edit-organization-user-notification.png)

   Andra standardmeddelandet som skickas per e-post till användarna om deras enhet inte är kompatibel och om de vill ha lokal åtkomst till Exchange. Meddelandemallen använder Markup Language. Du kan även se en förhandsgranskning av hur meddelandet blir medan du skriver

   Välj **Granska och spara**  och sedan **Spara** om du vill spara dina ändringar och slutföra konfigurationen av lokal åtkomst till Exchange.

   > [!TIP]
   > Läs mer om Markup Language i den här [artikeln](https://en.wikipedia.org/wiki/Markup_language) på Wikipedia.

8. Välj sedan **Avancerade åtkomstinställningar för Exchange ActiveSync** för att öppna arbetsflödet *Avancerade åtkomstinställningar för Exchange ActiveSync* där du kan konfigurera regler för enhetsåtkomst.

   > [!div class="mx-imgBorder"]
   > ![Exempel på skärmbild av arbetsflödet Redigera organisation för avancerade inställningar](./media/conditional-access-exchange-create/edit-organization-advanced-settings.png)

   - För **Åtkomst för ej hanterad enhet** ställer du in en global standardinställning för åtkomst från enheter som inte påverkas av villkorlig åtkomst eller andra regler:

     - **Tillåt åtkomst** – alla enheter får åtkomst till Exchange lokalt omedelbart. Enheter som tillhör användare i de konfigurerade grupperna blockeras om de senare utvärderas till att inte vara kompatibla med efterlevnadsprinciperna eller inte har registrerats i Intune.

     - **Blockera åtkomst** och **Karantän** –alla enheter blockeras omedelbart från att komma åt Exchange lokalt till att börja med. Enheter som tillhör användare i de grupper som du har konfigurerat enligt beskrivningen i föregående procedur får åtkomst efter att enheten registrerats i Intune och bedömt som kompatibel.

       Android-enheter som *inte* kör Samsung Knox Standard blockeras alltid eftersom de inte stöder den här inställningen.

   - Välj **Lägg till** för **Enhetsplattformsundantag** och ange sedan den plattformsinformation som krävs för din miljö.

      Om inställningen **Åtkomst för ohanterad enhet** är angiven till **Blockerad** kommer enheter som är registrerade och kompatibla att tillåtas, även om det finns ett plattformsundantag som ska blockeras.  

9. Klicka på **OK** för att spara dina ändringar.

10. Välj **Granska och spara** och sedan **Spara** om du vill spara principen för villkorlig åtkomst till Exchange.

## <a name="next-steps"></a>Nästa steg

Skapa sedan en efterlevnadsprincip och tilldela den till användare så att Intune kan utvärdera deras mobilenheter. Se [Komma igång med enhetsefterlevnad](device-compliance-get-started.md).

[Felsöka den lokala Exchange-anslutningsappen för Intune i Microsoft Intune](https://support.microsoft.com/help/4471887)
