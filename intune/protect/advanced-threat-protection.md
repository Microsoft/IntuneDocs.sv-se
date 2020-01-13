---
title: Använda Microsoft Defender ATP i Microsoft Intune – Azure | Microsoft Docs
description: Använd Microsoft Defender Advanced Threat Protection (Microsoft Defender ATP) med Intune, inklusive installation och konfiguration, publicering av dina Intune-enheter med ATP och använd en ATP-riskutvärdering för enheter med dina Intune-principer för enhetsefterlevnad och villkorsstyrd åtkomst för att skydda nätverksresurserna.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fa80697f24167e2a9634bd506e9548ca654129f
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547085"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>Tvinga fram kompatibilitet för Microsoft Defender ATP med villkorlig åtkomst i Intune

Du kan integrera Microsoft Defender Avancerat skydd (Microsoft Defender ATP) med Microsoft Intune som en Skydd mot mobilhot-lösning. Integrationen kan hjälpa dig att förhindra säkerhetsöverträdelser och begränsa effekten av överträdelser inom en organisation. Microsoft Defender ATP fungerar med enheter som kör Windows 10 eller senare.

För att lyckas, använder du följande konfigurationer tillsammans:

- **Etablera en tjänst-till-tjänst-anslutning mellan Intune och Microsoft Defender ATP**. Med den här anslutningen kan Microsoft Defender ATP samla in data om datorrisker från Windows 10-enheter som du hanterar med Intune.
- **Använd en enhetskonfigurationsprofil för att publicera enheter med Microsoft Defender ATP**. Du registrerar enheter för att konfigurera som så att de kommunicerar med Microsoft Defender ATP och för att tillhandahålla data som hjälper dem att utvärdera sin risknivå.
- **Använd en efterlevnadsprincip för enheter för att ange den risknivå som du vill tillåta**. Risknivåer rapporteras av Microsoft Defender ATP. Enheter som överskrider den tillåtna risknivån identifieras som icke-kompatibla.
- **Använd en princip** för villkorlig åtkomst för att blockera användare från att komma åt företagsresurser från enheter som inte är kompatibla.

När du integrerar Intune med Microsoft Defender ATP kan du dra nytta av ATP:s Threat & Vulnerability Management (TVM) och [använda Intune för att åtgärda sårbarheter i slutpunkterna som har upptäckts av TVM](atp-manage-vulnerabilities.md).

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>Exempel på användning av Microsoft Defender ATP med Intune

I följande exempel får du hjälp att förklara hur dessa lösningar fungerar tillsammans för att skydda din organisation. I det här exemplet är Microsoft Defender ATP och Intune redan integrerade.

Föreställ dig en händelse där någon skickar en Word-fil med inbäddad skadlig kod till en användare i din organisation.

- Användaren öppnar den bifogade filen och aktiverar innehållet.
- En attack med utökade privilegier startar och en angripare från en fjärrdator har administratörsrättigheter till den drabbade enheten.
- Angripare har sedan via fjärranslutning tillgång till användarens andra enheter. Det här säkerhetsintrånget kan påverka hela organisationen.

Microsoft Defender ATP kan lösa säkerhetshändelser som det här scenariot.

- I vårt exempel identifierar Microsoft Defender ATP att enheten körde onormal kod, upplevde en processeskalering, infogade skadlig kod och utfärdade ett misstänkt fjärrgränssnitt.
- Baserat på dessa åtgärder från enheten klassificerar Microsoft Defender ATP [enheten som associerad med hög risk](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity) och inkluderar en detaljerad rapport om misstänkt aktivitet på Microsoft Defender Security Center-portalen.

Eftersom du har en efterlevnadsprincip för Intune-enheter för att klassificera enheter *med* medelhög *eller* hög risknivå som icke-kompatibla klassificeras den komprometterade enheten som icke-kompatibel. Den här klassificeringen gör att din princip för villkorlig åtkomst kan aktiveras och blockera åtkomst från enheten till företagets resurser.

## <a name="prerequisites"></a>Krav

Om du vill använda Microsoft Defender ATP med Intune måste du ha följande konfigurerat och klart att använda:

- Licensierad klientorganisation för Enterprise Mobility + Security E3 och Windows E5 (eller Microsoft 365 Enterprise E5)
- Microsoft Intune-miljö med [Intune-hanterade](../enrollment/windows-enroll.md) Windows 10-enheter som även är Azure AD-anslutna
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) och åtkomst till Microsoft Defender Security Center (ATP-portal)

> [!NOTE]
> Microsoft Defender ATP stöds inte med Intune-appskyddsprinciper för iOS och Android.

## <a name="enable-microsoft-defender-atp-in-intune"></a>Aktivera Microsoft Defender ATP i Intune

Det första steget är att skapa en tjänst-till-tjänst-anslutning mellan Intune och Microsoft Defender ATP. Detta kräver administrativ åtkomst till både Microsoft Defender Security Center och Intune.

### <a name="to-enable-defender-atp"></a>Så här aktiverar du Defender ATP

Du behöver bara aktivera Defender ATP en gång per klientorganisation.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Slutpunktssäkerhet** > **Microsoft Defender ATP** och välj sedan **Öppna Microsoft Defender Säkerhetscenter**.

   ![Välj att öppna Microsoft Defender Security Center](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. I **Microsoft Defender Security Center**:
    1. Välj **Inställningar** > **Avancerade funktioner**.
    2. För **Microsoft Intune-anslutningen**, välj **På**:

        ![Aktivera anslutningen till Intune](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. Välj **Spara inställningar**.

4. Gå tillbaka till **Microsoft Defender ATP** i administrationscentret för Microsoft Endpoint Manager. Under **MDM-inställningar för efterlevnadsprinciper** väljer du **På** för **Anslut Windows-enheter i version 10.0.15063 och högre till Microsoft Defender ATP**.

5. Välj **Spara**.

> [!TIP]
> När du När du integrerar ett nytt program för Skydd mot mobilhot (MTD) i Intune och aktiverar anslutningen till Intune, skapar Intune en klassisk princip för villkorlig åtkomst i Azure Active Directory. Alla MTD-appar som du integrerar, inklusive [Defender ATP](advanced-threat-protection.md) eller något annat [MTD-partnerprogram](mobile-threat-defense.md#mobile-threat-defense-partners), skapar en ny klassisk princip för villkorlig åtkomst. Dessa principer kan ignoreras, men de bör inte redigeras, tas bort eller inaktiveras.
>
> Om den klassiska principen tas bort måste du ta bort anslutningen till Intune som var ansvarig för skapandet och sedan konfigurera den igen. Detta återskapar den klassiska principen. Den har inte stöd för att migrera klassiska principer för MTD-appar till den nya principtypen för villkorlig åtkomst.
>
> Klassiska principer för villkorlig åtkomst för MTD-appar:
>
> - Används av Intune MTD för att kräva att enheter registreras i Azure AD så att de har ett enhets-ID innan de kommunicerar med MTD-partners. ID:t krävs så att enheterna kan rapportera deras status till Intune.
> - Har ingen påverkan på andra molnappar eller resurser.
> - Är skilda från principer för villkorlig åtkomst som du kan skapa för att hantera MTD.
> - Samverkar inte som standard med andra principer för villkorlig åtkomst som du använder för utvärdering.
>
> Du kan visa klassiska principer för villkorlig åtkomst genom att gå till **Azure Active Directory** > **Villkorlig åtkomst** > **Klassiska principer** i [Azure](https://portal.azure.com/#home).

## <a name="onboard-devices-by-using-a-configuration-profile"></a>Publicera enheter med en konfigurationsprofil

När du har upprättat tjänst-till-tjänst-anslutningen mellan Intune och Microsoft Defender ATP kan du publicera dina Intune-hanterade enheter till ATP så att data om deras risknivå kan samlas in och användas. Använd en enhetskonfigurationsprofil för att publicera enheter med Microsoft Defender ATP.

När du upprättar anslutningen till Microsoft Defender ATP fick Intune ett konfigurationspaket för Microsoft Defender ATP-registrering från Microsoft Defender ATP. Det här paketet distribueras till enheter med enhetskonfigurationsprofilen. Konfigurationspaketet konfigurerar enheter för att kommunicera med [Microsoft Defender ATP-tjänster](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) för att söka igenom filer, identifiera hot och rapportera risken till Microsoft Defender ATP. När du publicerat en enhet med konfigurationspaketet behöver du inte göra det igen. Du kan också publicera enheter med hjälp av en [grupprincip eller Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="create-the-device-configuration-profile"></a>Skapa en enhetskonfigurationsprofil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange ett **Namn** och en **Beskrivning**.
4. För **Plattform** väljer du **Windows 10 och senare**
5. För **Profiltyp** väljer du **Microsoft Defender ATP (Windows 10 Desktop)** .
6. Konfigurera inställningarna:

   - **Pakettyp för konfiguration av Microsoft Defender ATP-klient**: Välj **Publicera** för att lägga till konfigurationspaketet i profilen. Välj **Avregistrera** för att ta bort konfigurationspaketet från profilen.
  
     > [!NOTE]
     > Om du har upprättat en anslutning på rätt sätt med Microsoft Defender ATP, kommer Intune automatiskt **publicera** konfigurationsprofilen åt dig, och inställningen **Pakettyp för konfiguration av Microsoft Defender ATP-klient** kommer inte vara tillgänglig.
  
   - **Exempeldelning för alla filer**: **Aktivera** tillåter att exempel samlas in och delas med Microsoft Defender ATP. Till exempel om du ser en misstänkt fil kan du skicka den till Microsoft Defender ATP för djupgående analys. **Inte konfigurerad** delar inte några exempel med Microsoft Defender ATP.
   - **Skicka frekvensvärde för telemetrirapportering**: För enheter med hög risk kan du **Aktivera** den här inställningen så att den rapporterar telemetri till tjänsten Microsoft Defender ATP oftare.

     [Registrera Windows 10-datorer med hjälp av Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) innehåller mer information om dessa Microsoft Defender ATP-inställningar.

7. Välj **OK** och **Skapa** för att spara ändringarna, vilket skapar profilen.
8. [Tilldela en enhetskonfigurationsprofil](../configuration/device-profile-assign.md) till enheter som du vill utvärdera med Microsoft Defender ATP.

## <a name="create-and-assign-the-compliance-policy"></a>Skapa och tilldela en efterlevnadsprincip

Efterlevnadsprincipen bestämmer risknivån som du bedömer som lämplig för en enhet.

### <a name="create-the-compliance-policy"></a>Skapa efterlevnadsprincipen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Efterlevnadsprinciper** > **Skapa princip**.
3. Ange ett **Namn** och en **Beskrivning**.
4. I **Plattform** väljer du **Windows 10 och senare**.
5. Under **Inställningar** väljer du **Windows Defender ATP**.
6. Ange **Kräv att enheten ska hållas vid eller under riskpoängen** till önskad nivå.

   Klassificeringar för hotnivå [bestäms av Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue).

   - **Rensa**: Den här nivån är säkrast. Enheten får inte ha några existerande hot och ska ha tillgång till företagsresurser. Om något hot identifieras på enheten kommer den att utvärderas som icke-kompatibel. (Microsoft Defender ATP använder värdet *Säkert*.)
   - **Låg**: Enheten följer standard om det enbart finns hot på låg nivå på enheten. Enheter med medel- eller hög risk är inte kompatibla.
   - **Medel**: Enheten följer standard om hoten som hittas på enheten är låga eller medelhöga. Om hot på en högre nivå identifieras på enheten får den statusen icke-kompatibel.
   - **Hög**: Den här nivån är den minst säkra och tillåter alla hotnivåer. Så enheter med höga, medel eller låga risknivåer anses uppfylla kraven.

7. Välj **OK** och **Skapa** för att spara ändringarna (och skapar profilen).
8. [Tilldela enhetens efterlevnadsprincip](create-compliance-policy.md#assign-the-policy) till tillämpliga grupper.

## <a name="create-a-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst

Principen för villkorlig åtkomst blockerar åtkomsten till resurser för enheter som överskrider den hotnivå som du har angett i efterlevnadsprincipen. Du kan blockera enhetens åtkomst till företagets resurser, såsom SharePoint eller Exchange Online.

> [!TIP]
> Villkorsstyrd åtkomst är en Azure Active Directory-teknik (Azure AD). Noden för villkorlig åtkomst som du kommer åt från administrationscentret för Microsoft Endpoint Manager är samma nod som du kommer åt från *Azure AD*.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Slutpunktssäkerhet** > **Villkorlig åtkomst** > **Ny princip**.

3. Ange ett **Namn** på principen och välj **Användare och grupper**. Använd inkludera eller exkludera alternativ för att lägga till grupper för principen och välj **Klar**.

4. Välj **Molnappar**, och välj vilka appar som ska skyddas. Välj t.ex. **Välj appar**, och välj **Office 365 SharePoint Online** och **Office 365 Exchange Online**.

   Klicka på **Klar** för att spara ändringarna.

5. Välj **Villkor** > **Klientappar** för att tillämpa principen till appar och webbläsare. Välj exempelvis **Ja** och aktivera sedan **Webbläsare** och **Mobilappar och skrivbordsklienter**.

   Klicka på **Klar** för att spara ändringarna.

6. Välj **Bevilja** för att använda villkorlig åtkomst baserat på enhetsefterlevnad. Välj exempelvis **Bevilja åtkomst** > **Kräv att enheten markerats som kompatibel**.

    Välj **OK** för att spara ändringarna.

7. Välj **Aktiverar principen**, och sedan **Skapa** för att spara ändringarna.

## <a name="monitor-device-compliance"></a>Övervaka enhetsefterlevnad

Övervaka därefter status för enheter som har Microsoft Defender ATP-efterlevnadsprincipen.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Övervaka** > **Principefterlevnad**.

3. Hitta din Microsoft Defender ATP-princip i listan och se vilka enheter som är kompatibla eller inkompatibla.

Du kan också använda den *operativa* rapporten för icke-kompatibla enheter från samma plats:

1. Välj **Enheter** > **Övervaka** > **icke-kompatibla enheter**.

Mer information om rapporter finns i [Intune-rapporter](../fundamentals/reports.md).

## <a name="view-onboarding-status"></a>Visa registreringsstatus

Om du vill se registreringsstatus för alla Intune-hanterade Windows 10-enheter, kan du gå till **Enhetsefterlevnad** > **Microsoft Defender ATP**. Från den här sidan kan du också börja skapa en enhetskonfigurationsprofil som kan registrera fler enheter till Microsoft Defender ATP.

## <a name="next-steps"></a>Nästa steg

[Villkorlig åtkomst för Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access)

[Instrumentpanel för Microsoft Defender ATP-risk](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)

[Använd säkerhetsaktiviteter med ATP:s sårbarhetshantering för att åtgärda problem på enheterna](atp-manage-vulnerabilities.md).

[Komma igång med principer för enhetsefterlevnad](device-compliance-get-started.md)
