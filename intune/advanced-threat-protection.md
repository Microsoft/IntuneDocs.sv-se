---
title: Använda Microsoft Defender ATP i Microsoft Intune – Azure | Microsoft Docs
description: Se hur du aktiverar Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) i ett scenario för slutpunkt till slutpunkt, inklusive aktiverar Microsoft Defender ATP i Intune och Microsoft Defender Security Center, publicerar enheter med hjälp av en Microsoft Defender ATP-konfigurationsprofil, skapar en efterlevnadsprincip för en Intune-enhet, skapar en villkorlig åtkomstprincip för Azure AD och övervakar enheternas kompatibilitet.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 069658bdd231be96d7f9fbe23de1b4e38fdc5a9e
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67885152"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Tvinga fram kompatibilitet för Microsoft Defender ATP med villkorlig åtkomst i Intune  

Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) och Microsoft Intune arbetar tillsammans för att förhindra säkerhetsintrång och begränsa effekten av överträdelser inom en organisation.

Den här funktionen gäller för: Windows 10-enheter

Någon skickar till exempel en Word-fil med inbäddad skadlig kod till en användare i din organisation. Användaren öppnar den bifogade filen och aktiverar innehållet. En attack med utökade privilegier startar och en angripare från en fjärrdator har administratörsrättigheter till den drabbade enheten. Angripare har sedan via fjärranslutning tillgång till användarens andra enheter.

Det här säkerhetsintrånget kan påverka hela organisationen.

Microsoft Defender ATP kan lösa säkerhetshändelser som det här scenariot. Microsoft Defender Security Center rapporterar enheterna som ”hög risk” och innehåller en detaljerad rapport om misstänkt aktivitet. I vårt exempel identifierar Microsoft Defender ATP att enheten körde onormal kod, upplevde en processeskalering, infogade skadlig kod och utfärdade ett misstänkt fjärrgränssnitt. Microsoft Defender ATP ger dig sedan alternativ för att minska risken.

Med Intune kan du skapa en efterlevnadsprincip som anger en godtagbar riksnivå. Om en enhet överstiger den här risken, blir enheten icke-kompatibel. I kombination med villkorlig åtkomst i Azure Active Directory (AD), blockeras användaren åtkomst till företagets resurser.

Den här artikeln visar hur du:

- Aktivera Intune i Microsoft Defender Security Center och aktivera Microsoft Defender ATP i Intune. Dessa uppgifter skapar en tjänst-till-tjänst-anslutning mellan Intune och Microsoft Defender ATP. Den här anslutningen låter Microsoft Defender ATP skriva risken för dina Intune-enheter.
- Skapa efterlevnadsprincipen i Intune.
- Aktivera villkorlig åtkomst i Azure Active Directory (AD) på enheter baserat på deras hotnivå.

## <a name="prerequisites"></a>Krav

Om du vill använda Microsoft Defender ATP med Intune måste du ha följande konfigurerat och klart att använda:

- Licensierad klientorganisation för Enterprise Mobility + Security E3 och Windows E5 (eller Microsoft 365 Enterprise E5)
- Microsoft Intune-miljö med [Intune-hanterade](windows-enroll.md) Windows 10-enheter som även är Azure AD-anslutna
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) och åtkomst till Microsoft Defender Security Center (ATP-portal)

## <a name="enable-microsoft-defender-atp-in-intune"></a>Aktivera Microsoft Defender ATP i Intune

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetsefterlevnad** > **Microsoft Defender ATP** och under *inställningar för anslutningsprogram* väljer du därefter **Öppna Microsoft Defender Security Center**.

    ![Välj att öppna Microsoft Defender Security Center](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. I **Microsoft Defender Security Center**:
    1. Välj **Inställningar** > **Avancerade funktioner**.
    2. För **Microsoft Intune-anslutningen**, välj **På**:

        ![Aktivera anslutningen till Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Välj **Spara inställningar**.

4. Gå tillbaka till Intune, **Enhetsefterlevnad** > **Microsoft Defender ATP**. Ställ in **Anslut Windows-enheter version 10.0.15063 och senare till Microsoft Defender ATP** till **På**.
5. Välj **Spara**.

Du gör normalt den här aktiviteten en gång. Så om Microsoft Defender ATP redan är aktiverat i din Intune-resurs, behöver du inte göra det igen.

## <a name="onboard-devices-using-a-configuration-profile"></a>Publicera enheter med en konfigurerad profil

När en slutanvändare registreras i Intune kan du skicka olika inställningar till enheten med en konfigurationsprofil. Detta gäller även för Microsoft Defender ATP.

Microsoft Defender ATP omfattar ett konfigurationspaket för registrering som kommunicerar med [Microsoft Defender ATP-tjänster](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) för att söka igenom filer, identifiera hot och rapportera risken till Microsoft Defender ATP.

När du registrerar får Intune ett automatiskt genererat konfigurationspaket från Microsoft Defender ATP. Intune push-överför konfigurationspaketet till enheten när den skickar konfigurationsprofilen till enheten, vilket gör att Microsoft Defender ATP kan hotövervaka enheten.

När du publicerat en enhet med konfigurationspaketet behöver du inte göra det igen. Du kan också publicera enheter med hjälp av en [Grupprincip eller System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-configuration-profile"></a>Skapa konfigurationsprofilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange ett **Namn** och en **Beskrivning**.
4. För **Plattform** väljer du **Windows 10 och senare**
5. För **Profiltyp** väljer du **Microsoft Defender ATP (Windows 10 Desktop)** .
6. Konfigurera inställningarna:

    - **Pakettyp för konfiguration av Microsoft Defender ATP-klient**: Välj **Publicera** för att lägga till konfigurationspaketet i profilen. Välj **Avregistrera** för att ta bort konfigurationspaketet från profilen.
  
    > [!NOTE]  
    > Om du har upprättat en anslutning på rätt sätt med Microsoft Defender ATP, kommer Intune automatiskt **publicera** konfigurationsprofilen åt dig, och inställningen **Pakettyp för konfiguration av Microsoft Defender ATP-klient** kommer inte vara tillgänglig.
  
    - **Exempeldelning för alla filer**: **Aktivera** tillåter att exempel samlas in och delas med Microsoft Defender ATP. Till exempel om du ser en misstänkt fil kan du skicka den till Microsoft Defender ATP för djupgående analys. **Inte konfigurerad** delar inte några exempel med Microsoft Defender ATP.
    - **Skicka frekvensvärde för telemetrirapportering**: För enheter med hög risk kan du **Aktivera** den här inställningen så att den rapporterar telemetri till tjänsten Microsoft Defender ATP oftare.

    [Registrera Windows 10-datorer med hjälp av System Center Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) innehåller mer information om dessa Microsoft Defender ATP-inställningar.

7. Välj **OK** och **Skapa** för att spara ändringarna, vilket skapar profilen.

## <a name="create-the-compliance-policy"></a>Skapa efterlevnadsprincipen
Efterlevnadsprincipen anger en godtagbar risknivå på en enhet.

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
3. Ange ett **Namn** och en **Beskrivning**.
4. I **Plattform** väljer du **Windows 10 och senare**.
5. I inställningarna för **Microsoft Defender ATP** anger du **Kräv att enheten ska hållas vid eller under riskpoängen** till önskad nivå. Klassificeringar för hotnivå [bestäms av Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Rensa**: Den här nivån är säkrast. Enheten får inte ha några existerande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel. (Microsoft Defender ATP använder värdet *Säkert*.)
   - **Låg**: Enheten följer standard om det enbart finns hot på låg nivå på enheten. Enheter med medel- eller hög risk är inte kompatibla.
   - **Medel**: Enheten följer standard om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
   - **Hög**: Den här nivån är den minst säkra och tillåter alla hotnivåer. Så enheter med höga, medel eller låga risknivåer anses uppfylla kraven.

6. Välj **OK** och **Skapa** för att spara ändringarna (och skapar profilen).

## <a name="assign-the-policy"></a>Tilldela principen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetsefterlevnad** > **Principer**> Välj din Microsoft Defender ATP-princip för efterlevnad.
3. Välj **Tilldelningar**.
4. Inkludera eller exkludera dina Azure AD-grupper för att tilldela dem till principen.
5. Om du vill distribuera principen till grupper, välj **Spara**. Användarenheterna som principen är inriktad på kommer att utvärderas för att se om de följer standard.

## <a name="create-a-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst
Principen för villkorlig åtkomst blockerar åtkomsten till resurser *om* enheten inte är kompatibel. Om en enhet överstiger hotnivån, kan du blockera åtkomst till företagets resurser, såsom SharePoint eller Exchange Online.  

> [!TIP]  
> Villkorsstyrd åtkomst är en Azure Active Directory-teknik (Azure AD). Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*.  

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Villkorlig åtkomst** > **Ny princip**.
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
Övervaka därefter status för enheter som har Microsoft Defender ATP-efterlevnadsprincipen.

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetsefterlevnad** > **Principefterlevnad**.
3. Hitta din Microsoft Defender ATP-princip i listan och se vilka enheter som är kompatibla eller inkompatibla.

## <a name="more-good-stuff"></a>Mer bra innehåll
[Villkorlig åtkomst för Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)  
[Instrumentpanel för Microsoft Defender ATP-risk](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)  

[Komma igång med principer för enhetsefterlevnad](device-compliance-get-started.md)  
[Villkorlig åtkomst för Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)