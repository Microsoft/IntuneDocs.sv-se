---
title: "Konfigurera registrering av Apple School Manager-programmet för iOS-enheter"
titleSuffix: Intune on Azure
description: "Lär dig hur du konfigurerar Apple School Manager-programmets registrering av företagsägda iOS-enheter med Intune\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73556209c88759ffe0747d9927cbcbb49600e0c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Aktivera registrering av iOS-enheter med Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet hjälper IT-administratörer att aktivera registrering av iOS-enheter som köpts via [Apple School Manager](https://school.apple.com/)-programmet (ASM). Microsoft Intune kan trådlöst distribuera en registreringsprofil som registrerar ASM-enheter för hantering. Administratören behöver aldrig röra de olika enheter som ska hanteras. En ASM-profil innehåller hanteringsinställningar som tillämpas på enheter vid registreringen, inklusive alternativ för installationsassistenten.

**ASM-registreringssteg**
1. [Skaffa en ASM-token och tilldela enheter](#get-the-asm-token-and-assign-devices)
2. [Skapa en registreringsprofil](#create-an-apple-enrollment-profile)
3. [Ansluta School Data Sync](#connect-school-data-sync) (valfritt)
4. [Synkronisera ASM-hanterade enheter](#sync-asm-managed-devices)
5. [Tilldela en ASM-profil till enheter](#assign-an-asm-profile-to-devices)
6. [Distribuera enheter till användare](#distribute-devices-to-users)

>[!NOTE]
>ASM-registrering kan inte användas med Apples [program för enhetsregistrering (DEP)](device-enrollment-program-enroll-ios.md) eller Intunes konto för [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

## <a name="get-the-apple-asm-token-and-assign-devices"></a>Skaffa Apples ASM-token och tilldela enheter

Innan du kan registrera företagsägda iOS-enheter med Apple School Manager (ASM) behöver du en ASM-tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till ASM. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler. I Apples portal kan du också tilldela de enhetsserienummer som ska hanteras.

**Krav**
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Registrerat för [Apple School Manager](http://school.apple.com)

**Steg 1. Ladda ned det offentliga nyckelcertifikat för Intune som krävs för att skapa en Apple ASM-token.**<br>
1. På Azure [Intune-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** och sedan **Token för registreringsprogram**.
2. På bladet **Token för registreringsprogram** väljer du **Ladda ned din offentliga nyckel** för att ladda ned och spara krypteringsnyckelfilen (.pem) lokalt. .pem-filen används för att begära ett förtroendecertifikat från Apple School Manager-portalen.

**Steg 2. Ladda ned en ASM-token och tilldela enheter.**<br>
Välj **Skapa en token via Apple School Manager** och logga in med ditt företags Apple-ID. Du kan använda detta Apple-ID när du behöver förnya din ASM-token.

   1.  I [Apple School Manager-portalen](https://school.apple.com) går du till **MDM-servrar** och väljer sedan **Lägg till MDM-server** (längst upp till höger).
   2.  Ange **MDM-serverns namn**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.
   3.  Välj **Ladda upp fil...**  i Apples portal, bläddra till .pem-filen och välj **Spara MDM-server** (längst ned till höger).
   4.  Välj **Hämta token** och ladda ned servertokenfilen (.p7m) till datorn.
   5. Gå till **Enhetstilldelningar** och **Välj enhet** med manuell inmatning av **Serienummer**, **Ordernummer** eller **Överför CSV-fil**.
   6.   Välj åtgärden **Tilldela till server** och välj den **MDM-server** som du skapade.
   7. Ange hur du avser att **välja enheter** och tillhandahåll sedan information om enheten och specifikationer genom **serienummer**, **ordningsnummer** eller genom att välja **Överför CSV-fil**.
   8. Välj **Tilldela till server** och välj &lt;servernamnet&gt; som angetts för Microsoft Intune och sedan **OK**.

**Steg 3. Ange det Apple-ID som användes för att skapa din ASM-token.**<br>Detta ID ska användas när du förnyar din Apple ASM-token och lagras för framtida användning.

**Steg 4. Leta reda på och ladda upp din token.**<br>
Gå till certifikatfilen (.p7m), välj **Öppna** och sedan **Ladda upp**. Intune synkroniserar automatiskt ASM-enheterna från Apple.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil
En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Under **Registreringsprogram** väljer du **Profiler för registreringsprogram**.
3. På bladet **Profiler för registreringsprogram** väljer du **Skapa**.
4. På bladet **Skapa registreringsprofil** anger du ett **Namn** och en **Beskrivning** för profilen som visas i Intune-portalen.
5. Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

 - **Registrera med användartillhörighet** – Enheten måste registreras med en användare under den ursprungliga installationen och kan sedan beviljas åtkomst till företagets data och e-post. Välj användartillhörighet för de ASM-hanterade enheter som användarna loggar in på med sina hanterade Apple-ID:n.

 >[!NOTE]
 >Multifaktorautentisering (MFA) fungerar inte vid registrering på ASM-enheter med användartillhörighet. Efter registreringen fungerar MFA som förväntat på dessa enheter.

  Det delade iPad-läget i Apple School Manager innebär att användarna måste registrera sig med användartillhörighet.

 >[!NOTE]
    >ASM med användartillhörighet kräver att [användarnamn/kombinerad slutpunkt för WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) aktiveras för att du ska kunna begära en användartoken. [Läs mer om WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet (inklusive företagsportalappen som används vid installation av branschspecifika appar) fungerar inte.

6. Välj **Enhetshanteringsinställningar**. Dessa objekt anges under aktiveringen och kräver en fabriksåterställning om du vill ändra dem. konfigurera följande profilinställningar och välj sedan **Spara**:

    - **Övervakad** – Ett hanteringsläge som aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Om du inte markerar kryssrutan begränsas dina hanteringsfunktioner.

    - **Aktivera** – (Kräver Hanteringsläge = Övervakad) Inaktiverar iOS-inställningar som kan möjliggöra borttagning av hanteringsprofilen. Om du lämnar den här kryssrutan omarkerad tillåter du att hanteringsprofilen tas bort från menyn Inställningar.

  - **Delad iPad** – (kräver **Registrera med användartillhörighet** och **Övervakat** läge.) Flera användare kan logga in på iPad-enheter som har registrerats med hjälp av ett hanterat Apple-ID. Hanterade Apple-ID:n skapas i Apple School Manager-portalen.

  >[!NOTE]
  >Om läget **Delad iPad** är aktiverat i en profil och antingen **Användartillhörighet** eller **Övervakat** läge är inställt på **Av**, är det delade iPad-läget inaktiverat för registreringsprofilen.

  - **Maximalt antal cacheanvändare** – (kräver **Delad iPad** = **Ja**) Skapar en partition på enheten för varje användare. Det rekommenderade värdet är antalet studenter som troligen kommer att använda enheten under en viss tidsperiod. Om exempelvis sex studenter använder enheten regelbundet under veckan, anges numret till sex.  

    - **Tillåt parkoppling** – Anger huruvida iOS-enheter ska kunna synkroniseras med datorer eller inte. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

    - **Apple Configurator-certifikat** – Om du väljer **Tillåt Apple Configurator efter certifikat** under **Tillåt parkoppling** måste du ange vilket Apple Configurator-certifikat som ska importeras.

7. Välj **Inställningar för inställningsassistenten**, konfigurera följande profilinställningar och välj sedan **Spara**:

    - **Avdelningsnamn** – Visas om användaren knackar på **Om konfiguration** under aktiveringen.

    - **Avdelningens telefonnummer** – Visas om användaren klickar på knappen Behöver du hjälp? under aktiveringen.
    - **Alternativ för Installationsassistenten** – Om dessa alternativ undantas från Installationsassistenten kan de anges senare på menyn **Inställningar** i iOS.
        - **Lösenordskod** – Fråga efter lösenordskod under aktivering. Kräv alltid ett lösenord om inte enheten är skyddad eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app).
        - **Platstjänster** – Om en här funktionen är aktiverad frågar Installationsassistenten efter under aktivering
        - **Återställ** – Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering
        - **Apple-ID** – Om det här alternativet är aktiverat uppmanar iOS användaren att ange ett Apple-ID när Intune försöker installera en app utan ett ID. Ett Apple-ID krävs för att kunna ladda ned iOS App Store-appar, inklusive de appar som har installerats av Intune.
        - **Villkor** – Om det här alternativet är aktiverat uppmanas användarna i installationsassistenten att godkänna Apples villkor under aktiveringen
        - **Touch ID** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Apple Pay** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Zooma** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Siri** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Diagnostikdata** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktiveringen

8. Om du vill spara profilinställningarna väljer du **Skapa** på bladet **Skapa registreringsprofil**.

## <a name="connect-school-data-sync"></a>Ansluta School Data Sync
(Valfritt) ASM stöder synkronisering av klasslistdata till Azure Active Directory (AD) med hjälp av Microsoft SDS (School Data Sync). Utför följande steg om du vill använda SDS till att synkronisera skolans data.

1. På bladet **Token för registreringsprogram** väljer du antingen den blå informationsbanderollen eller **Anslut School Data Sync**.
2. Välj **Tillåt** för inställningen **Tillåt Microsoft School Data Sync att använda den här token**. Den här inställningen innebär att Intune kan ansluta till SDS i Office 365.
3. För att aktivera en anslutning mellan ASM och Azure AD väljer du **Ställ in Microsoft School Data Sync**. Lär dig mer om [hur du ställer in School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Klicka på **OK** för att spara och fortsätta.

## <a name="sync-asm-managed-devices"></a>Synkronisera ASM-hanterade enheter
Nu när Intune har tilldelats behörighet att hantera dina ASM-enheter, kan du synkronisera Intune med ASM-tjänsten och se dina hanterade enheter i Intune-portalen.

1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Under **Registreringsprogramenheter** väljer du **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.

    För att följa Apples villkor för godkänd ASM-trafik tillämpar Intune följande begränsningar:
     -  En fullständig ASM-synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer som Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.

>[!NOTE]
>Du kan också tilldela ASM-serienummer till profiler från bladet **Registreringsprogramenheter**.

## <a name="assign-an-asm-profile-to-devices"></a>Tilldela en ASM-profil till enheter
ASM-enheter som hanteras av Intune måste tilldelas en ASM-profil innan de registreras.

1. Välj **Enhetsregistrering** > **Apple-registrering** i Intune-portalen och välj sedan **Registreringsprogramprofiler**.
2. Från listan över **Profiler för registreringsprogram** väljer du den profil du vill tilldela enheter och väljer därefter **Enhetstilldelningar**
3. Välj **Tilldela** och markera sedan de ASM-enheter som du vill tilldela den här profilen. Du kan använda filter för att enbart se tillgängliga ASM-enheter:
  - **ej tilldelad**
  - **alla**
  - **&lt;ASM-profilnamn&gt;**
4. Markera de enheter som du vill tilldela. Kryssrutan ovanför kolumnen markerar upp till 1 000 enheter från listan. Klicka på **Tilldela**. Om du vill registrera mer än 1 000 enheter måste du upprepa tilldelningen tills alla enheter har tilldelats en ASM-profil.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Nu kan du distribuera företagsägda enheter till användare. När en ASM-enhet i iOS aktiveras kommer den att registreras för hantering av Intune. Om enheten har aktiverats och används kan profilen inte användas förrän enheten har fabriksåterställts.

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Hur användare installerar och använder företagsportalen på sina enheter

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. När användarna fått sina enheter måste de köra Installationsassistenten och installera företagsportalappen.
