---
title: "Krav för registreringen av mobila enheter | Microsoft Docs"
description: "Ange krav för hantering av mobila enheter (MDM) och kom igång med att registrera olika operativsystem."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7beff3bf4579d9fb79f0c3f2fb8fbf9bb1ea160
ms.openlocfilehash: fc97e1266c2e859104b21f3bf4ff24f33123f66a
ms.lasthandoff: 02/22/2017


---

# <a name="prerequisites-for-mobile-device-management-in-intune"></a>Krav för hantering av mobila enheter i Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan göra det möjligt för anställda att registrera sina mobila enheter i Intune med följande steg. Samma steg krävs för att hantera företagsägda enheter.

|Steg|Information|  
|-----------|-------------|  
|**Steg 1:** [Aktivera anslutningar](#step-1-enable-connections)|Se till att det anpassade domännamnet är konfigurerat och att nätverkskommunikation är redo|  
|**Steg 2:** [Ange MDM-auktoritet](#step-2-set-mdm-authority)|Utfärdaren för hantering av mobila enheter definierar den tjänst som har tilldelats enheterna|
|**Steg 3:** [Skapa grupper](#step-3-create-groups)|Konfigurera användarinriktade inställningar för företagsportalappen|  
|**Steg 4:** [Konfigurera företagsportalen](#step-4-configure-company-portal)|Konfigurera användarinriktade inställningar för företagsportalappen|  
|**Steg 5:** [Tilldela användarlicenser](#step-5-assign-user-licenses)|Tilldela Intune-licenser till användare så att de kan registrera enheter|
|**Steg 6:** [Aktivera registrering](#step-6-enable-enrollment)|Aktivera plattformsspecifika inställningar för iOS- och Windows-hantering. Android-enheter behöver ingen ytterligare konfigurering.|
|**Steg 7:** [Nästa steg](#step-7-next-steps)|Aktivera plattformsspecifika inställningar för iOS- och Windows-hantering. Android-enheter behöver ingen ytterligare konfigurering.|

Letar du efter Intune med Configuration Manager?
> [!div class="button"]
[Se SCCM-dokument >](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm)

## <a name="step-1-enable-connections"></a>Steg 1: Aktivera anslutningar

Innan du aktiverar registrering av mobila enheter ser du till att du har gjort följande:
- [Granska webbadresser och portar som krävs i nätverket](../get-started/network-infrastructure-requirements-for-microsoft-intune.md)
- [Lägga till och verifiera en egen domän](../get-started/domain-names-for-microsoft-intune.md)

## <a name="step-2-set-mdm-authority"></a>Steg 2: Ange MDM-auktoritet
Utfärdaren för hantering av mobila enheter definierar den hanteringstjänst som har behörighet att hantera en uppsättning enheter. Alternativen för MDM-utfärdare innefattar själva Intune och Configuration Manager med Intune. Om Configuration Manager anges som utfärdare för hanteringen kan inga andra tjänster användas för hantering av mobila enheter.

>[!IMPORTANT]
> Överväg noggrant om du vill hantera mobila enheter endast med hjälp av Intune (onlinetjänst) eller System Center Configuration Manager med Intune (lokal programvarulösning i samband med onlinetjänsten). När du har angett auktoritet för hantering av mobila enheter kan du inte ändra detta utan hjälp från Microsoft Support. Instruktioner finns i [Vad ska jag göra om jag väljer fel inställning för MDM-auktoritet?](#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).


1.  Gå till [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) och välj **Admin** &gt; **Hantering av mobila enheter**.

2.  Klicka på **Ange auktoritet för hantering av mobila enheter** i **Uppgiftslistan**. Dialogrutan **Ange MDM-auktoritet** öppnas.

    ![Dialogrutan Ange MDM-auktoritet](../media/intune-mdm-authority.png)

3.  Intune begär bekräftelse på att du vill ha Intune som MDM-utfärdare. Markera kryssrutan och välj sedan **Ja** om du vill hantera mobila enheter med Microsoft Intune.

## <a name="step-3-create-groups"></a>Step 3: Skapa grupper

Du kan skapa användare och enhetsgrupper för att förenkla hanteringen och bättre rikta åtgärder mot distribuerade appar, principer och företagsresurser. [Lär dig hur du skapar grupper](use-groups-to-manage-users-and-devices-with-microsoft-intune.md#create-groups).

## <a name="step-4-configure-company-portal"></a>Steg 4: Konfigurera företagsportalen

Intune-företagsportalen är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.

> [!TIP]
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Om du vill göra det loggar du bara in på [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) som klient eller tjänstadministratör, väljer **Admin** &gt; **Företagsportal** och konfigurerar inställningarna för företagsportalen.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

### <a name="company-contact-information-and-privacy-statement"></a>Företagets kontaktinformation och sekretesspolicy

Företagsnamnet visas som företagsportalens rubrik. Kontaktuppgifterna och informationen visas för användarna på skärmen Kontakta IT på företagsportalen. Sekretesspolicyn visas när användaren klickar på sekretesslänken.

|Fältnamn|Högsta längd|Mer information|
    |----------|------------------------|----------------|
    |Företag|40|Det här namnet visas som företagsportalens rubrik. **Obs**! Använd endast alfanumeriska tecken. Specialtecken kan inte användas i fältet.|
    |IT-avdelningens kontaktperson|40|Det här namnet visas på sidan **Kontakta IT-avdelningen**.|
    |IT-avdelningens telefonnummer|20|Det här numret visas på sidan **Kontakta IT-avdelningen**.|
    |IT-avdelningens e-postadress|40|Den här adressen visas på sidan **Kontakta IT-avdelningen**. Du måste ange en giltig e-postadress i formatet **alias@domainname.com**.|
    |Ytterligare information|120|Den här informationen visas på sidan **Kontakta IT-avdelningen**.|
    |URL till företagets sekretesspolicy|79|Du kan ange en egen sekretesspolicy för ditt företag som visas när användaren klickar på en länk på företagsportalen. Du måste ange en giltig URL i formatet https://www.contoso.com.|

### <a name="support-contacts"></a>Supportkontakter
Supportwebbplatsen visas för användarna på företagsportalen så att de kan få tillgång till onlinesupport.

|Fältnamn|Högsta längd|Mer information|
    |----------|------------------------|----------------|
    |URL till supportwebbplatsen|150|Om du har en supportwebbplats som du vill att slutanvändarna ska använda, anger du webbadressen här. URL:en måste ha formatet https://www.contoso.com. Om du inte anger någon webbadress kommer inget att visas på sidan **Kontakta IT** på företagsportalen.|
    |Namn på webbplats|40|Det här är det egna namnet som visas för supportwebbplatsens URL. Om du bara anger URL:en till en supportwebbplats utan något eget namn visas **Gå till IT-webbplatsen** på sidan **Kontakta IT** på företagsportalen.|


### <a name="company-branding-customization"></a>Varumärkesanpassning

Du kan anpassa företagsportalen med företagets logotyp, företagets namn, temafärg och bakgrund.

|Fältnamn|Mer information|
    |----------|----------------|
    |Temafärg|Välj en temafärg som ska användas på företagsportalen.|
    |Infoga företagslogotyp|Om du aktiverar det här alternativet kan du ladda upp företagets logotyp så att den visas på företagsportalen. Du kan ladda upp två logotyper: en logotyp som visas när företagsportalens bakgrund är vit och en logotyp som visas när företagsportalens bakgrund har din valda temafärg. En logotyp måste vara en PNG- eller JPG-fil med en högsta upplösning på 400 × 100 bildpunkter och en största storlek på 750 kB.|
    |Välj en bakgrund för företagsportalappen|Den här inställningen påverkar bara bakgrunden i företagsportalappen.|


När du har sparat ändringarna kan du använda länkarna längst ned på sidan **Företagsportal** i administratörskonsolen för att gå till företagsportalen. Dessa länkar kan inte ändras. När en användare loggar in visar dessa länkar dina prenumerationer på företagsportalen.

## <a name="step-5-assign-user-licenses"></a>Steg 5: Tilldela användarlicenser

Du använder **hanteringsportalen för Office 365** för att manuellt lägga till molnbaserade användare och tilldela licenser till både molnbaserade användarkonton och konton som synkroniseras från din lokala Active Directory till Azure Active Directory (Azure AD). Du kan [synkronisera lokala användare med Azure AD](../get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3.md#how-to-sync-on-premises-users-with-azure-ad).

1.  Logga in på [hanteringsportalen för Office 365](https://portal.office.com/Admin/Default.aspx) med dina klientadministratörsuppgifter.

2.  Välj det användarkonto som du vill tilldela Intune-användarlicensen till och markera kryssrutan **Microsoft Intune** i egenskaperna för användarkontot.

3.  Nu läggs användarkontot till i Microsoft Intune-användargruppen, vilket beviljar användaren behörighet att använda tjänsten och registrera sina enheter för hantering.

### <a name="to-synchronize-on-premises-users-with-azure-ad"></a>Så här synkroniserar du lokala användare med Azure AD

1. [Lägg till UPN-suffixet](https://technet.microsoft.com/en-us/library/cc772007.aspx) för din egna domän i din lokala Active Directory.
2. Ange det nya UPN-suffixet för de lokala användare som du tänker importera.
3. Kör [Azure AD Connect-synkronisering](https://azure.microsoft.com/en-us/documentation/articles/active-directory-aadconnect/) för att integrera dina lokala användare med Azure AD.
4. När informationen om användarkontot har synkroniserats kan du tilldela Microsoft Intune-licenser med [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).

## <a name="step-6-enable-enrollment"></a>Steg 6: Aktivera registrering
När du har konfigurerat MDM-utfärdare måste du konfigurera enhetshantering för de operativsystem som organisationen vill ha stöd för. Stegen för att konfigurera enhetshantering varierar beroende på operativsystem. I Android OS krävs till exempel inte att du gör någonting i Intune-administratörskonsolen. Å andra sidan kräver Windows och iOS en förtroenderelation mellan enheter och Intune för att tillåta hantering.

Ställ in hantering för följande plattformar:
- [iOS och Mac](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [Android](set-up-android-management-with-microsoft-intune.md)
- [Android for Work](set-up-android-for-work.md)
- [Windows-datorer och bärbara datorer](set-up-windows-device-management-with-microsoft-intune.md)
- [Windows 10 Mobile och Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)

Du kan också aktivera [registrering av företagsägda enheter](manage-corporate-owned-devices.md).

## <a name="step-7-next-steps"></a>Steg 7: Nästa steg

Nu när registreringen har aktiverats bör du konfigurera hanteringen så att den uppfyller dina affärsbehov. Här är några hanteringsalternativ:

- [Distribuera principer som hanterar inställningar och funktioner på enheter](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
- [Aktivera åtkomst till företagsresurser som e-post, Wi-Fi och VPN](enable-access-to-company-resources-with-microsoft-intune.md)
- [Lägg till appar](add-apps.md) och [distribuera appar](deploy-apps.md) till hanterade enheter
- [Skapa efterlevnadsprinciper för enheter](introduction-to-device-compliance-policies-in-microsoft-intune.md) och [begränsa åtkomsten baserat på efterlevnad](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)

## <a name="what-to-do-if-you-choose-the-wrong-mdm-authority-setting"></a>Vad ska jag göra om jag väljer fel inställning för MDM-auktoritet?

Om du har valt fel inställning för MDM-auktoritet och vill ändra inställningen måste du kontakta Microsoft Support. Du kan inte ändra den här inställningen själv. Läs följande information innan du kontaktar Microsoft Support. Den beskriver vilken information Microsoft Support behöver från dig för att kunna göra ändringen.

MDM-auktoriteten kan återställas på tre sätt. I supportbegäran väljer du det sätt som passar bäst för ditt fall. Om inget alternativ motsvarar ditt fall meddelar du Microsoft Support om detta.

Microsoft Support ber dig bekräfta följande information:

- Klient-ID: den domän som används för att logga in på tjänsten (till exempel intune.onmicrosoft.com)
- Den MDM-auktoritet som du vill ändra till
- Bekräftelse av att nödvändiga steg har slutförts, enligt listan nedan

Om du använder samexistens måste du kontrollera checklistan för både Intune och Office 365.

### <a name="reset-mdm-authority-from-intune-to-configuration-manager"></a>Återställa MDM-auktoritet från Intune till Configuration Manager

Gör följande innan du kontaktar Microsoft Support för att återställa din MDM-auktoritet.

- Dra tillbaka alla enheter från Intune-administratörskonsolen. Försök inte att dra tillbaka en enhet från själva enheten. 
- Ta bort Service To Service Connector (under **Administration** > **Hantering av mobila enheter** > **Microsoft Exchange**) eller inaktivera Exchange Connector, om du har konfigurerat det. 
- Ta bort rollen Hanterare av enhetsregistrering från **Administratör** > **Hanterare av enhetsregistrering**.
- Inaktivera Mappning av enhetsgrupp i **Administratör** > **Hanterings av mobila enheter** > **Mappning av enhetsgrupp**.
- Ta bort nycklar för separat inläsning from **Administratör** > **Hantering av mobila enheter** > **Windows** > **Nycklar för separat inläsning**.
- Ta bort APNs-certifikatet för iOS på sidan **Administratör** > **Hantering av mobila enheter** > **iOS**.
- Ta bort DEP-token för iOS på sidan **Administratör** > **Hantering av mobila enheter** > **iOS**.
- Ta bort alla principer för dina MDM-enheter under **Princip** > **Konfigurationsprinciper**.
- Ta bort alla publicerade program för dina MDM-enheter i **Appar** > **Hanterad programvara**.

### <a name="reset-mdm-authority-from-configuration-manager-to-intune"></a>Återställa MDM-auktoritet från Configuration Manager till Intune

Gör följande innan du kontaktar Microsoft Support för att återställa din MDM-auktoritet.

- Dra tillbaka alla enheter (som hanteras som mobila enheter) från Configuration Manager-konsolen. Försök inte att dra tillbaka en enhet från själva enheten. 
- Ta bort alla användare från Intune-användargruppen. Peka Intune-prenumerationen till en tom användarsamling eller ta bort alla användare från målsamlingen.  Kontrollera att användarna har tagits bort i CloudUserSync.log. 
- Avmarkera iOS-plattformen för att rensa APNs-certifikatet.
- Ta bort alla publicerade program för MDM-enheter.
- Ta bort alla principer för MDM-enheter. 
- Ta bort Windows Intune Connector från Configuration Manager-konsolen (gäller endast för R2 SP1 eller lägre).
Ta bort Intune-prenumerationen genom att högerklicka på prenumerationen och välja **Ta bort**.
- Starta om SMS Executive-tjänsten.
- Ge oss några exempelanvändare så att vi, när processen är klar, kan kontrollera att Configuration Manager-licenserna har tagits bort.

### <a name="reset-mdm-authority-from-office-365-to-configuration-manager"></a>Återställa MDM-auktoritet från Office 365 till Configuration Manager

1. Gå till [https://protection.office.com](https://protection.office.com).
2. Välj fliken **Säkerhetsprinciper** och välj **Enhetshantering**. 
3. Dra tillbaka alla enheter genom att välja **Selektiv rensning**. Försök inte att dra tillbaka en enhet från själva enheten. Om selektiv rensning har inaktiverats krävs ingen ytterligare åtgärd.
4. Välj fliken **Säkerhetsprinciper** och välj **Säkerhetsprinciper för enhet**. 
5. Välj **Ta bort** för alla befintliga principer. Om principerna är i väntande tillstånd krävs ingen ytterligare åtgärd.

>[!NOTE]
>Det går inte att ta bort APNs-certifikatet för iOS. Det fortsätter att vara kopplat till kontot. 

### <a name="next-steps-for-mdm-authority-resets"></a>Nästa steg för återställning av MDM-auktoritet

När Microsoft Support har verifierat punkterna i checklistan kan det ta upp till tre arbetsdagar att återställa MDM-auktoritet, men vanligtvis sker det inom en dag. 

>[!IMPORTANT]
>Konfigurera inte prenumerationen förrän Microsoft Support har bekräftat att återställningen har slutförts! För tidig konfiguration kan leda till skador och kan påverka din möjlighet att använda Intune-tjänsten. 

