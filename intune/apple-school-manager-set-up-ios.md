---
title: "Konfigurera registrering av Apple School Manager-programmet för iOS-enheter"
titlesuffix: Azure portal
description: "Lär dig hur du konfigurerar Apple School Manager-programmets registrering av företagsägda iOS-enheter med Intune\""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 666ce43e3bd87db5a8245694d22401819c369951
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Aktivera registrering av iOS-enheter med Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet hjälper dig att aktivera registrering av iOS-enheter som köpts via [Apple School Manager](https://school.apple.com/)-programmet. Med hjälp av Intune med Apple School Manager kan du registrera många iOS-enheter utan att ens behöva röra dem. När en student eller en lärare sätter på enheten körs installationsassistenten med de konfigurerade inställningarna och enheten registreras i hanteringen.

Om du vill aktivera Apple School Manager-registrering använder du både Intune-portalen och Apple School Manager-portalen. En lista med serienummer eller inköpsordernummer krävs så att du kan tilldela enheter till Intune för hantering. Du kan skapa DEP-registreringsprofiler som innehåller inställningar som verkställs på enheterna under registreringen.

Apple School Manager-registrering kan inte användas med [Apples program för enhetsregistrering](device-enrollment-program-enroll-ios.md) eller [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

**Förutsättningar**
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- [MDM-utfärdare](mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Enheter som köpts från programmet [Apple School Management](http://school.apple.com)

>[!NOTE]
>Multifaktorautentisering (MFA) fungerar inte vid registrering på Apple School Manager-enheter med användartillhörighet. Efter registreringen fungerar MFA som förväntat på dessa enheter. Efter registreringen fungerar MFA som förväntat på enheterna. Enheterna kan inte uppmana användare som behöver ändra sina lösenord när de loggar in första gången. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. Användarna måste återställa lösenordet från en annan enhet.

## <a name="get-the-apple-token-and-assign-devices"></a>Skaffa Apple-token och tilldela enheter

Innan du kan registrera företagsägda iOS-enheter med Apple School Manager behöver du en tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till Apple School Manager. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler. I Apples portal kan du också tilldela de enhetsserienummer som ska hanteras.

**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple-token.**<br>
1. I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** och sedan väljer du **Token för registreringsprogram**.

  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/enrollment-program-token-download.png)

2. På bladet **Token för registreringsprogram** väljer du **Ladda ned din offentliga nyckel** för att ladda ned och spara krypteringsnyckelfilen (.pem) lokalt. .pem-filen används för att begära ett förtroendecertifikat från Apple School Manager-portalen.

**Steg 2. Ladda ned en token och tilldela enheter.**<br>
1. Välj **Skapa en token via Apple School Manager** och logga in med ditt företags Apple-ID. Du kan använda detta Apple-ID när du behöver förnya din Apple School Manager-token.
2.  I [Apple School Manager-portalen](https://school.apple.com) går du till **MDM-servrar** och väljer sedan **Lägg till MDM-server** (längst upp till höger).
3.  Ange **MDM-serverns namn**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.
   ![Skärmbild av Apple School Manager-portalen med serienummeralternativet markerat](./media/asm-server-assignment.png)

4.  Välj **Ladda upp fil...**  i Apples portal, bläddra till .pem-filen och välj **Spara MDM-server** (längst ned till höger).
5.  Välj **Hämta token** och ladda ned servertokenfilen (.p7m) till datorn.
6. Gå till **Enhetstilldelningar** och **Välj enhet** med manuell inmatning av **Serienummer**, **Ordernummer** eller **Överför CSV-fil**.
     ![Skärmbild av Apple School Manager-portalen med serienummeralternativet markerat](./media/asm-device-assignment.png)
7.  Välj åtgärden **Tilldela till server** och välj den **MDM-server** som du skapade.
8. Ange alternativ för **Välj enheter** och ange sedan enhetsinformation.
9. Välj **Tilldela till server** och välj &lt;servernamnet&gt; som angetts för Microsoft Intune och sedan **OK**.

**Steg 3. Ange det Apple-ID som användes för att skapa Apple School Manager-token.**<br>Detta ID ska användas när du förnyar din Apple School Manager-token och lagras för framtida användning.

![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/enrollment-program-token-apple-id.png)

**Steg 4. Leta reda på och ladda upp din token.**<br>
Gå till certifikatfilen (.p7m), välj **Öppna** och sedan **Ladda upp**. Intune synkroniserar automatiskt Apple School Manager-enheterna från Apple.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil
En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Under **Registreringsprogram** väljer du **Registreringsprogramprofiler**.
3. På bladet **Registreringsprogramprofiler** väljer du **Skapa**.
4. På bladet **Skapa registreringsprofil** anger du ett **Namn** och en **Beskrivning** för profilen som visas i Intune.
5. Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

 - **Registrera med användartillhörighet** – Kopplar enheten till en användare under installationen.

  Det delade iPad-läget i Apple School Manager innebär att användarna måste registrera sig utan användartillhörighet.

 - **Registrera utan användartillhörighet** – Välj detta för enheter som inte är kopplade till en enda användare, som delade enheter. Använd detta för enheter som utför uppgifter utan att öppna lokala användardata. Appar som företagsportalappen fungerar inte.

6. Välj **Enhetshanteringsinställningar**. Dessa objekt anges under aktiveringen och kräver en fabriksåterställning om du vill ändra dem. konfigurera följande profilinställningar och välj sedan **Spara**:

  ![Skärmbild av val av hanteringsläge. Enheten har följande inställningar: Övervakad, Låst registrering samt Tillåt parkoppling inställd på Neka alla. Apple Configurator-certifikat är nedtonat för en ny registreringsprogramprofil.](./media/enrollment-program-profile-mode.png)

    - **Övervakad** – Ett hanteringsläge som aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Om du inte markerar kryssrutan begränsas dina hanteringsfunktioner.

     - **Låst registrering** – (Kräver Hanteringsläge = Övervakad) Inaktiverar iOS-inställningar som kan möjliggöra borttagning av hanteringsprofilen. Om du lämnar den här kryssrutan omarkerad tillåter du att hanteringsprofilen tas bort från menyn Inställningar.
   - **Delad iPad** – (kräver **Registrera utan användartillhörighet** och Övervakat läge.) Flera användare kan logga in på iPad-enheter som har registrerats med hjälp av ett hanterat Apple-ID. Hanterade Apple-ID:n skapas i Apple School Manager-portalen. Mer information om [delad iPad](education-settings-configure-ios-shared.md). Du bör också granska [Apples krav för delad iPad](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

   >[!NOTE]
   >Om **Användartillhörighet** är inställt på **Med användartillhörighet** eller **Övervakat** läge är inställt på **Av**, är det delade iPad-läget inaktiverat för registreringsprofilen.

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

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
(Valfritt) Apple School Manager stöder synkronisering av klasslistdata till Azure Active Directory (AD) med hjälp av Microsoft SDS (School Data Sync). Utför följande steg om du vill använda SDS till att synkronisera skolans data.

1. På bladet **Token för registreringsprogram** väljer du antingen den blå informationsbanderollen eller **Anslut School Data Sync**.
2. Välj **Tillåt** för inställningen **Tillåt Microsoft School Data Sync att använda den här token**. Den här inställningen innebär att Intune kan ansluta till SDS i Office 365.
3. För att aktivera en anslutning mellan Apple School Manager och Azure AD väljer du **Ställ in Microsoft School Data Sync**. Lär dig mer om [hur du ställer in School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Klicka på **OK** för att spara och fortsätta.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter
Nu när Intune har tilldelats behörighet att hantera Apple School Manager-enheterna kan du synkronisera Intune med Apple-tjänsten och se dina hanterade enheter i Intune.

1. I Intune på Azure Portal väljer du **Enhetsregistrering** > **Apple-registrering** > **Registreringsprogramenheter** > **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.

  ![Skärmbild där noden Registreringsprogramenheter har valts och länkvärde håller på att väljas.](./media/enrollment-program-device-sync.png)
2. Välj **Begär synkronisering** på bladet **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.

  ![Skärmbild av bladet Synkronisera där länken Begär synkronisering håller på att väljas.](./media/enrollment-program-device-request-sync.png)

  Om du vill följa Apples villkor för godkänd trafik tillämpar Intune följande begränsningar:
   -    En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer som Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
   -    Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.

>[!NOTE]
>Du kan också tilldela Apple School Manager-serienummer till profiler från bladet **Registreringsprogramenheter**.

## <a name="assign-a-profile-to-devices"></a>Tilldela en profil till enheter
Apple School Manager-enheter som hanteras av Intune måste tilldelas en registreringsprogramprofil innan de registreras.

1. I Intune på Azure Portal väljer du **Enhetsregistrering** > **Apple-registrering** och väljer sedan **Registreringsprogramprofiler**.
2. Från listan över **Registreringsprogramprofiler** väljer du den profil som du vill tilldela till enheter och därefter **Enhetstilldelningar**

 ![Skärmbild av enhetstilldelningar med Tilldela markerat.](./media/enrollment-program-device-assign.png)

3. Välj **Tilldela** och markera sedan de Apple School Manager-enheter som du vill tilldela den här profilen. Du kan använda filter för att enbart visa tillgängliga enheter:
  - **ej tilldelad**
  - **alla**
  - **&lt;profilnamn&gt;**
4. Markera de enheter som du vill tilldela. Kryssrutan ovanför kolumnen markerar upp till 1 000 enheter från listan. Klicka på **Tilldela**. Om du vill registrera mer än 1 000 enheter måste du upprepa tilldelningen tills alla enheter har tilldelats en registreringsprofil.

  ![Skärmbild av knappen Tilldela som används för att tilldela registreringsprogramprofiler i Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Nu kan du distribuera företagsägda enheter till användare. När en Apple School Manager-enhet i iOS aktiveras kommer den att registreras för hantering av Intune. Om enheten har aktiverats och används kan profilen inte användas förrän enheten har fabriksåterställts.
