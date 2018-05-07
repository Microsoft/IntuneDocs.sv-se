---
title: Använda Windows Defender ATP i Microsoft Intune – Azure | Microsoft Docs
description: Se hur du aktiverar Windows Defender Advanced Threat Protection (ATP) i ett scenario för slutpunkt till slutpunkt, inklusive aktivera ATP i Intune och Windows Defender Security Center (ATP-portal), publicera enheter med hjälp av en ATP-konfigurationsprofil, skapa en efterlevnadsprincip för en Intune-enhet, skapa en villkorlig åtkomstprincip för Azure AD och övervaka enheternas kompatibilitet.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2e99ed0bd1eb5bae90913aedba5973e5e1282f70
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/02/2018
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>Aktivera Windows Defender ATP med villkorlig åtkomst i Intune

Windows Defender Advanced Threat Protection (ATP) och Microsoft Intune arbetar tillsammans för att förhindra säkerhetsintrång och begränsa effekten av överträdelser inom en organisation.

Den här funktionen gäller för: Windows 10-enheter

Någon skickar till exempel en Word-fil med inbäddad skadlig kod till en användare i din organisation. Användaren öppnar den bifogade filen och aktiverar innehållet. En attack med utökade privilegier startar och en angripare från en fjärrdator har administratörsrättigheter till den drabbade enheten. Angripare har sedan via fjärranslutning tillgång till användarens andra enheter.

Det här säkerhetsintrånget kan påverka hela organisationen.

Windows Defender ATP kan lösa säkerhetshändelser som det här scenariot. Windows Defender Security Center (ATP-konsol) rapporterar enheterna som ”hög risk” och innehåller en detaljerad rapport om misstänkt aktivitet. I vårt exempel identifierar Windows Defender ATP att enheten körde onormal kod, upplevde en processeskalering, infogade skadlig kod och utfärdade ett misstänkt fjärrgränssnitt. Windows Defender ATP ger dig sedan alternativ för att minska risken.

Med Intune kan du skapa en efterlevnadsprincip som anger en godtagbar riksnivå. Om en enhet överstiger den här risken, blir enheten icke-kompatibel. I kombination med villkorlig åtkomst i Azure Active Directory (AD), blockeras användaren åtkomst till företagets resurser.

Den här artikeln visar hur du:

- Aktiverar Intune i ATP och aktivera ATP i Intune. Dessa uppgifter skapar en tjänst-till-tjänst-anslutning mellan Intune och Windows Defender ATP. Den här anslutningen låter Windows Defender ATP skriva risken för dina Intune-enheter.
- Skapa efterlevnadsprincipen i Intune.
- Aktivera villkorlig åtkomst i Azure Active Directory (AD) på enheter baserat på deras hotnivå.

## <a name="prerequisites"></a>Krav

Om du vill använda ATP med Intune måste du ha följande konfigurerat och klart att använda:

- Licensierad klient för Enterprise Mobility + Security E5 och Windows E5 (eller Microsoft 365 Enterprise E5)
- Microsoft Intune-miljö med [Intune-hanterade](windows-enroll.md) Windows 10-enheter som även är Azure AD-anslutna
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) och åtkomst till Windows Defender Security Center (ATP-portal)

## <a name="enable-windows-defender-atp-in-intune"></a>Aktivera Windows Defender ATP i Intune

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetsefterlevnad** > **Windows Defender ATP** > **Öppna administratörskonsolen för Windows Defender Advanced Threat Protection**.

    ![Alternativ text](./media/atp-device-compliance-open-windows-defender.png)

4. I **Windows Defender Säkerhetscenter**:
    1. Välj **Inställningar** > **Avancerade funktioner**.
    2. För **Microsoft Intune-anslutningen**, välj **På**:

        ![Alternativ text](./media/atp-security-center-intune-toggle.png)

    3. Välj **Spara inställningar**.

5. Gå tillbaka till Intune, **Enhetsefterlevnad** > **Windows Defender ATP**. Ange **Ansluta Windows 10.0.15063+-enheter till Windows Defender Advanced Threat Protection** till **På**.
6. Välj **Spara**.

Du gör normalt den här aktiviteten en gång. Så om ATP redan är aktiverat i din Intune-resurs, behöver du inte göra det igen.

## <a name="onboard-devices-using-a-configuration-profile"></a>Publicera enheter med en konfigurerad profil

Windows Defender innehåller ett inbyggt konfigurationspaket som är installerat på enheterna. När det är installera, kommunicerar paketet med [Windows Defender ATP-tjänster](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) för att söka igenom filer, identifiera hot och rapportera risken till Windows Defender ATP. Med Intune kan du skapa du en konfigurationsprofil som använder det här konfigurationspaket. Tilldela sedan den här profilen till enheter som du publicerar för första gången.

När du publicerat en enhet med konfigurationspaketet behöver du inte göra det igen. Detta är vanligtvis en engångsaktivitet.

Du kan också publicera enheter med hjälp av en [Grupprincip eller System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection).

Nästa steg visar hur du använder Intune för att publicera.

#### <a name="download-configuration-package"></a>Hämta konfigurationspaket

1. I [Windows Defender Security Center](https://securitycenter.windows.com) väljer du **Inställningar** > **Integration**.
2. Ange följande inställningar:
  - **Operativsystem**: Windows 10
  - **Publicera en dator** > **Distributionsmetod**: Hantering av mobila enheter/Microsoft Intune
3. Välj **Hämta paket** och spara filen **WindowsDefenderATPOnboardingPackage.zip**. Extrahera filen.

Den här zipfilen innehåller **WindowsDefenderATP.onboarding**, som du behöver i nästa steg.

#### <a name="create-the-atp-configuration-profile"></a>Skapa ATP-konfigurationsprofilen

Den här profilen använder integrationspaketet som du hämtade i föregående steg.

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **Namn** och en **Beskrivning**.
4. För **Plattform** väljer du **Windows 10 och senare**
5. För **Profiltyp** väljer du **Windows Defender ATP (Windows 10 Desktop)**.
6. Konfigurera inställningarna:

  - **Publicera konfigurationspaket**: Bläddra och välj den **WindowsDefenderATP.onboarding**-fil som du hämtat. Den här filen ställer in så att enheterna kan rapportera till tjänsten Windows Defender ATP.
  - **Exempeldelning för alla filer**: Tillåter att exempel kan samlas in och delas med Windows Defender ATP. Till exempel om du ser en misstänkt fil kan du skicka den till Windows Defender ATP för djupgående analys.
  - **Skicka frekvensvärde för telemetrirapportering**: För enheter som har hög risk, aktivera den här inställningen så att den rapporterar telemetri till tjänsten Windows Defender ATP oftare.
  - **Avregistrera konfigurationspaket**: Om du vill ta bort eller ”avlasta” Windows Defender ATP-övervakning, kan du hämta ett paket för avlastning i [Windows Defender Security Center](https://securitycenter.windows.com), och lägger till det. Hoppa annars över den här egenskapen.

    [Publicera Windows 10-datorer med hjälp av System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection) innehåller mer information om dessa Windows Defender ATP-inställningar.

7. Välj **OK** och **Skapa** för att spara ändringarna, vilket skapar profilen.

## <a name="create-the-compliance-policy"></a>Skapa efterlevnadsprincipen
Efterlevnadsprincipen anger en godtagbar risknivå på en enhet.

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
3. Ange ett **Namn** och en **Beskrivning**.
4. I **Plattform** väljer du **Windows 10 och senare**.
5. I inställningen **Enhetens hälsotillstånd** ställ in **Kräv att enheten ligger vid eller under hotnivån för enheten** till din önskade nivå:

  - **Skyddad**: Det här är den säkraste nivån. Enheten får inte ha några existerande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel.
  - **Låg**: Enheten följer standard om det enbart finns hot på låg nivå på enheten. Enheter med medel- eller hög risk är inte kompatibla.
  - **Medel**: Enheten är kompatibel om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
  - **Hög**: Den här nivån är det minst säkra och den tillåter alla hotnivåer. Så enheter med höga, medel eller låga risknivåer anses uppfylla kraven.

6. Välj **OK** och **Skapa** för att spara ändringarna (och skapar profilen).

## <a name="assign-the-policy"></a>Tilldela principen

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetsefterlevnad** > **Principer**> Välj din Windows Defender ATP-princip för efterlevnad.
3. Välj **Tilldelningar**.
4. Inkludera eller exkludera dina Azure AD-grupper för att tilldela dem till principen.
5. Om du vill distribuera principen till grupper, välj **Spara**. Användarenheterna som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="create-an-azure-ad-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst för Azure AD
Principen för villkorlig åtkomst blockerar åtkomsten till resurser *om* enheten inte är kompatibel. Om en enhet överstiger hotnivån, kan du blockera åtkomst till företagets resurser, såsom SharePoint eller Exchange Online.

1. I [Azure Portal](https://portal.azure.com) öppnar du **Azure Active Directory** > **Villkorlig åtkomst** > **Ny princip**.
2. Ange ett **Namn** på principen och välj **Användare och grupper**. Använd inkludera eller exkludera alternativ för att lägga till grupper för principen och välj **Klar**.
3. Välj **Molnappar**, och välj vilka appar som ska skyddas. Välj t.ex. **Välj appar**, och välj **Office 365 SharePoint Online** och **Office 365 Exchange Online**.

    Klicka på **Klar** för att spara ändringarna.

4. Välj **Villkor** > **Klientappar** för att tillämpa principen till appar och webbläsare. Välj exempelvis **Ja** och aktivera sedan **Webbläsare** och **Mobilappar och skrivbordsklienter**.

    Klicka på **Klar** för att spara ändringarna.

5. Välj **Bevilja** för att använda villkorlig åtkomst baserat på enhetsefterlevnad. Välj exempelvis **Bevilja åtkomst** > **Kräv att enheten markerats som kompatibel**.

    Välj **OK** för att spara ändringarna.

6. Välj **Aktiverar principen**, och sedan **Skapa** för att spara ändringarna.

[Vad är villkorlig åtkomst?](conditional-access.md) är en bra resurs.

## <a name="monitor-device-compliance"></a>Övervaka enhetsefterlevnad
Övervaka därefter status för enheter som har Windows Defender ATP-efterlevnadsprincipen.

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetsefterlevnad** > **Principefterlevnad**.
3. Hitta din Windows Defender ATP-princip i listan och se vilka enheter som är kompatibla eller inkompatibla.

## <a name="more-good-stuff"></a>Mer bra innehåll
[Villkorlig åtkomst för Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection)  
[Instrumentpanel för Windows Defender ATP-risk](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)  
[Komma igång med principer för enhetsefterlevnad](device-compliance-get-started.md)  
[Villkorlig åtkomst för Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)