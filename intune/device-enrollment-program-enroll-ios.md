---
title: "Registrera iOS-enheter – Enhetsregistreringsprogrammet"
titleSuffix: Intune on Azure
description: "Läs hur du registrerar företagsägda iOS-enheter med programmet för enhetsregistrering.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/30/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f509f5332b2f8b5f6745816f8795a9a54c10ce2d
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>Konfigurera registrering för iOS-enheter med programmet för enhetsregistrering

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet hjälper IT-administratörer att aktivera registrering av iOS-enheter som köpts via Apples [program för enhetsregistrering (DEP)](https://deploy.apple.com). Microsoft Intune kan även distribuera en registreringsprofil trådlöst till enheter som köpts via DEP. Administratören behöver aldrig röra de olika enheter som ska hanteras. En DEP-profil innehåller hanteringsinställningar som tillämpas på enheter vid registreringen, inklusive alternativ för installationsassistenten.

Om du vill aktivera DEP-registrering kan du använda både Intune och Apples DEP-portal. Du måste även ha en lista eller inköpsordernummer för dina DEP-enheter, så att du kan tilldela dem till Intune för hantering i Apples portal.

>[!NOTE]
>DEP-registreringen kan inte användas med [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

**Steg för att aktivera registreringsprogram från Apple**
1. [Skaffa en Apple DEP-token och tilldela enheter](#get-the-apple-dep-certificate)
2. [Skapa en registreringsprofil](#create-anapple-enrollment-profile)
3. [Synkronisera DEP-hanterade enheter](#sync-dep-managed-devices)
4. [Tilldela enheter en DEP-profil](#assign-a-dep-profile-to-devices)
5. [Distribuera enheter till användare](#distribute-devices-to-users)

## <a name="get-the-apple-dep-token"></a>Hämta Apple DEP-token

Innan du kan registrera företagsägda iOS-enheter med Apples program för enhetsregistrering (DEP) behöver du en DEP-tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till DEP och som ditt företag äger. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

> [!NOTE]
> Om Intune-klienten har migrerats från den klassiska Intune-konsolen till Azure-portalen och du har tagit bort en Apple DEP-token från Intune-administrationskonsolen under migreringsperioden kan DEP-token ha återställts till ditt Intune-konto. Du kan ta bort DEP-token från Azure-portalen igen.

**Krav**
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Registrerad för [Apples program för enhetsregistrering](http://deploy.apple.com)

**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple DEP-token.**<br>
1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering** och **Registreringsprogramtoken**.
![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat.](./media/enrollment-program-token-add.png)
2. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.
![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/enrollment-program-token-download.png)

**Steg 2. Skapa och ladda ned en Apple DEP-token.**<br>
Välj **Skapa en token via Apples enhetsregistreringsprogram (DEP)** så öppnas Apples portal för driftsättningsprogram. Logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.
  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat.](./media/enrollment-program-token-create.png)

  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/enrollment-program-token-sign.png)
   1.  Gå till [Apples portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**.
   ![Skärmbild av någon som väljer Kom igång för Enhetsregistreringsprogram.](./media/enrollment-program-token-started.png)
   2. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.
   3. Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

   ![Skärmbild av hur någon lägger till ett MDM-servernamn för DEP och sedan klickar på Nästa.](./media/enrollment-program-token-add-server.png)
   4.  Dialogrutan **Lägg till &lt;ServerName&gt;**  öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.
   ![Skärmbild av någon som väljer knappen för offentlig nyckelfil och sedan klickar på Nästa.](./media/enrollment-program-token-choose-file.png)
   4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.
   ![Skärmbild av någon som väljer knappen för offentlig nyckelfil och sedan klickar på Nästa.](./media/enrollment-program-token-your-token.png)
   5. Gå till **Distributionsprogram** &gt; **Program för enhetsregistrering** &gt; **Hantera enheter**.
   6. Under **Choose Devices By** (Välj enheter efter) anger du hur enheterna ska identifieras:
    - **Serienummer**
    - **Ordernummer**
    - **Ladda upp CSV-fil**.

   ![Skärmbild av någon som anger enheterna ska visas efter serienummer, väljer åtgärden Assign to Server (Tilldela till server) och sedan servernamnet.](./media/enrollment-program-token-specify-serial.png)

   7. För **Välj åtgärd** väljer du **Assign to Server** (Tilldela till server), väljer det &lt;ServerName&gt; som har angetts för Microsoft Intune och klickar på **OK**. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

**Steg 3. Ange det Apple-ID som användes för att skapa din registreringsprogramtoken.**<br>Ange ditt Apple-ID i Intune-portalen för framtida bruk. Du kan använda detta ID för att förnya din registreringsprogramtoken och slippa behöva registrera alla enheter på nytt.
![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token. ](./media/enrollment-program-token-apple-id.png)
**Steg 4. Bläddra till den registreringsprogramtoken som du vill ladda upp.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter. Intune synkroniseras automatiskt med Apple och visar ditt registreringsprogramkonto.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil

En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Under **Registreringsprogram för Apple** väljer du **Registreringsprogramprofiler** och sedan **Skapa** på bladet **Registreringsprogramprofiler**.
![Skärmbild av någon som väljer länken för att skapa en ny registreringsprogramprofil.](./media/enrollment-program-profile-create.png)
3. Ange ett **namn** och en **beskrivning** för profilen på bladet **Skapa registreringsprofil**. Detta behövs för administrativa syften. Användarna kan inte se den här informationen.
![Skärmbild av någon som anger namn och beskrivning och sedan väljer Registrera med användartillhörighet för en ny registreringsprogramprofil.](./media/enrollment-program-profile-name.png)
Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

 - **Registrera med användartillhörighet** – Användaren registreras med en enhet under konfigurationen och kan sedan beviljas åtkomst till företagets data och e-post. Välj **användartillhörighet** för enheter som tillhör användare och som måste använda företagsportalen för tjänster som installation av appar.

<<<<<<< HEAD
 > [!NOTE]
 > Multifaktorautentisering (MFA) fungerar inte under registreringen av enheter med användartillhörighet som hanteras av registreringsprogram. Efter registreringen fungerar MFA som förväntat på dessa enheter. Nya användare som måste ändra sina lösenord när de loggar in första gången ombeds inte göra detta inte under registreringen av enheter. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. De måste återställa lösenordet från en annan enhet.

 >[!NOTE]
 >Registreringsprogramshantering med användartillhörighet kräver att [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints) aktiveras för att kunna begära användartokens. [Läs mer om WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
=======
    >[!NOTE]
    >DEP med användartillhörighet kräver att [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints) aktiveras för att du ska kunna begära en användartoken. [Läs mer om WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
>>>>>>> 0c3fe0dee88e8ef4d8ad8ad28c0f8957831dd5b3

 - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

4. Välj **Enhetshanteringsinställningar** och konfigurera följande profilinställningar: ![Skärmbild av någon som väljer Hanteringsläge Övervakad, låst registrering, med Tillåt parkoppling inställd på att neka alla och Apple Configurator-certifikat nedtonade för en ny registreringsprogramprofil.](./media/enrollment-program-profile-mode.png)
    - **Övervakad** – Ett hanteringsläge som aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Om du inte markerar kryssrutan begränsas dina hanteringsfunktioner.

    - **Aktivera** – (Kräver Hanteringsläge = Övervakad) Inaktiverar iOS-inställningar som kan möjliggöra borttagning av hanteringsprofilen. Om du lämnar den här kryssrutan omarkerad tillåter du att hanteringsprofilen tas bort från menyn Inställningar. Det här objektet anges under aktiveringen och kan inte ändras utan en fabriksåterställning.

    - **Tillåt parkoppling** – Anger huruvida iOS-enheter ska kunna synkroniseras med datorer eller inte. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

    - **Apple Configurator-certifikat** – Om du väljer **Tillåt Apple Configurator efter certifikat** under **Tillåt parkoppling** måste du ange vilket Apple Configurator-certifikat som ska importeras.

  Välj **Spara**.

5. Välj **Inställningar för inställningsassistenten** och konfigurera följande inställningar: ![Skärmbild av någon som väljer konfigurationsinställningar med tillgängliga inställningar för en ny registreringsprogramprofil.](./media/enrollment-program-profile-settings.png)
    - **Avdelningsnamn** – Visas om användaren knackar på **Om konfiguration** under aktiveringen.

    - **Avdelningens telefonnummer** – Visas om användaren klickar på knappen Behöver du hjälp? under aktiveringen.
    - **Alternativ för Installationsassistenten** – Dessa valfria inställningar kan konfigureras senare på menyn **Inställningar** i iOS.
        - **Lösenordskod** – Fråga efter lösenordskod under aktivering. Kräv alltid ett lösenord om inte enheten är skyddad eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app).
        - **Platstjänster** – Om en här funktionen är aktiverad frågar Installationsassistenten efter under aktivering
        - **Återställ** – Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering
        - **Apple-ID** – Om det här alternativet är aktiverat uppmanar iOS användaren att ange ett Apple-ID när Intune försöker installera en app utan ett ID. Ett Apple-ID krävs för att hämta iOS App Store-appar, inklusive de som har installerats av Intune.
        - **Villkor** – Om det här alternativet är aktiverat uppmanas användarna i installationsassistenten att godkänna Apples villkor under aktiveringen
        - **Touch ID** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Apple Pay** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Zooma** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Siri** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Diagnostikdata** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktiveringen

    Välj **Spara**.
9. Om du vill spara profilinställningarna väljer du **Skapa** på bladet **Skapa registreringsprofil**. Registreringsprofilen visas i listan Registreringsprofiler för Apples registreringsprogram.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter
Nu när Intune har fått behörighet att hantera dina enheter, kan du synkronisera Intune med Apple och se dina hanterade enheter i Intune-portalen.

1. I Intune-portalen väljer du **enhetsregistrering** &gt;  **Apple-registrering** &gt; **Registreringsprogramenheter**.
2. Under **Registreringsprogramenheter** väljer du **Synkronisera**. Bladet **Synkronisera** visas.
![Skärmbild där noden Registreringsprogramenheter har valts och länkvärde håller på att väljas.](./media/enrollment-program-device-sync.png)
3. Välj **Begär synkronisering** på bladet **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.
![Skärmbild av bladet Synkronisera där länken Begär synkronisering håller på att väljas.](./media/enrollment-program-device-request-sync.png)
    För att följa Apples villkor för godkänd registreringsprogramtrafik tillämpar Intune följande begränsningar:
     -  En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer som Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.
4. I arbetsytan Registreringsprogramenheter väljer du **Uppdatera** för att visa dina enheter.

## <a name="assign-an-enrollment-profile-to-devices"></a>Tilldela enheterna en registreringsprofil
Enheter som hanteras av Intune måste tilldelas en registreringsprogramprofil innan de registreras.

>[!NOTE]
>Du kan även tilldela profiler serienummer från bladet **Apple-serienummer**.

1. Välj **Enhetsregistrering** > **Apple-registrering** i Intune-portalen och välj sedan **Registreringsprogramprofiler**.
2. Från listan över **Profiler för registreringsprogram** väljer du den profil du vill tilldela enheter och väljer därefter **Tilldela enheter**.
![Skärmbild av bladet Synkronisera där länken Begär synkronisering håller på att väljas.](./media/enrollment-program-device-assign.png)
3. Välj **Tilldela** och markera sedan de enheter som du vill tilldela den här profilen. Du kan använda filter för att enbart visa tillgängliga enheter:
  - **ej tilldelad**
  - **alla**
  - **&lt;profilnamn&gt;**
4. Markera de enheter som du vill tilldela. Du kan använda kryssrutan ovanför kolumnen för välja upp till 1 000 listade enheter och sedan klicka på **Tilldela**. Om du vill registrera mer än 1 000 enheter måste du upprepa tilldelningen tills alla enheter har tilldelats en registreringsprofil.

  ![Skärmbild av knappen Tilldela som används för att tilldela registreringsprogramprofiler i Intune-portalen](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>Slutanvändarupplevelse med hanterade enheter

Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens. Om enheten har aktiverats och används kan profilen inte användas förrän enheten har fabriksåterställts. När iOS-enheter som hanteras av registreringsprogrammet slås på visas följande för användaren:  

1. **Set Up iOS device** (Konfigurera iOS-enhet) – Användarna kan välja bland följande alternativ:
  - **Set Up as New device** (Konfigurera som ny enhet)
  - **Restore from iCloud Backup** (Återställ från iCloud-säkerhetskopia)
  - **Restore from iTunes Backup** (Återställ från iTunes-säkerhetskopia)
2. Användare informeras **Microsoft konfigurerar din enhet automatiskt.** Följande ytterligare konfigurationsinformation finns också tillgänglig:

  **Konfiguration som gör det möjligt för Microsoft att hantera enheten trådlöst.**

  **En administratör kan hjälpa dig att konfigurera e-post och nätverkskonton, installera och konfigurera appar samt fjärrhantera inställningar.**

  **En administratör kan inaktivera funktioner, installera och avinstallera program, övervaka och begränsa Internet-trafiken samt fjärradera den här enheten.**

  **Konfigurationen tillhandahålls av:<br> MicrosoftIntune iOS Team<br> One Microsoft Way, Redmond, WA 98052 (USA)**

3. Användarna ombeds uppge användarnamn och lösenord till sitt arbets- eller skolkonto.
4. Användarna ombeds uppge sitt Apple-ID. Ett Apple-ID krävs för att installera appen Intune Företagsportal och andra appar. När autentiseringsuppgifterna har angetts installeras en hanteringsprofil på enheten som inte kan tas bort. Intune-hanteringsprofilen visas i **Inställningar** > **Allmänt** > **Enhetshantering** på enheten.

Användarna kan nu slutföra konfigurationen av sina företagsägda enheter via Intune Företagsportal eller Apples Installationsassistenten.
