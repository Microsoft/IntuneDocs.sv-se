---
title: "Registrera iOS-enheter – Enhetsregistreringsprogrammet"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig hur du registrerar företagsägda iOS-enheter med programmet för enhetsregistrering."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 61fbc2af9a7c43d01c20f86ff26012f63ee0a3c2
ms.openlocfilehash: c56bea46c8b505e0d357cfe90678ab149559b896
ms.lasthandoff: 04/07/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Registrera iOS-enheter med programmet för enhetsregistrering

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Det här avsnittet hjälper IT-administratörer att registrera företagsägda iOS-enheter som köpts via [Apples enhetsregistreringsprogram (DEP)](https://deploy.apple.com). Microsoft Intune kan distribuera en registreringsprofil som registrerar DEP "i luften" så att administratören inte behöver ha fysisk kontakt med varje hanterad enhet. En DEP-profil innehåller hanteringsinställningar som du vill tillämpa på enheter vid registreringen. Registreringspaketet kan innehålla installationsassistentalternativ för enheten.

>[!NOTE]
>DEP-registreringen kan inte användas med [enhetsregistreringshanteraren](enroll-devices-using-device-enrollment-manager.md).
>Om användare dessutom registrerar sina iOS-enheter med företagsportalappen och dessa enheters serienummer sedan importeras och tilldelas en DEP-profil, så måste enheten avregistreras från Intune.

**DEP-registreringssteg**
1. [Hämta en Apple DEP-token](#get-the-apple-dep-certificate)
2. [Skapa en DEP-profil](#create-anapple-dep-profile)
3. [Tilldela Intune-servern Apple DEP-serienummer](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [Synkronisera DEP-hanterade enheter](#synchronize-dep-managed-devices)
5. Distribuera enheter till användare



## <a name="get-the-apple-dep-certificate"></a>Hämta Apple DEP-certifikatet
Innan du kan registrera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) behöver du en DEP-certifikatfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till DEP och som ditt företag äger. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

Ett företag som vill hantera företagsägda iOS-enheter med DEP måste gå med i Apples program och skaffa enheter genom det. Information om den här processen finns på https://deploy.apple.com. Exempel på fördelar med programmet är obevakade enhetsinstallationer utan användning av en USB-kabel för att ansluta varje enhet till en dator.

> [!NOTE]
> Om Intune-klienten har migrerats från den klassiska Intune-konsolen till Azure-portalen och du har tagit bort en Apple DEP-token från Intune-administrationskonsolen under migreringsperioden kan DEP-token ha återställts till ditt Intune-konto. Du kan ta bort DEP-token från Azure-portalen igen.




**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple DEP-token.**<br>
1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. På bladet Intune väljer du **Enhetsregistrering** > **Apple DEP-Token**.
2. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

**Steg 2. Ladda ned en Apple DEP-token från en lämplig Apple-webbplats.**<br>
Välj [Skapa en DEP-token via Apples distributionsprogram](https://deploy.apple.com) (https://deploy.apple.com) och logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.

   1.  I Apples [DEP-portal (Device Enrollment Program)](https://deploy.apple.com) går du till **Enhetsregistreringsprogram** &gt; **Hantera servrar** och väljer **Lägg till MDM-server**.
   2.  Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.
   3.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.
   4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.

**Steg 3. Ange det Apple-ID som användes för att skapa din Apple DEP-token. Detta ID kan du använda för att förnya din Apple DEP-token.**

**Steg 4. Bläddra till din Apple DEP-token och ladda upp. Intune synkroniseras automatiskt med ditt DEP-konto.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

## <a name="create-an-apple-dep-profile"></a>Skapa en Apple DEP-profil

En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter. Följande steg visar hur du skapar en enhetsregistreringsprofil för iOS-enheter som registrerats med hjälp av DEP.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Apple-registrering**.
3. Välj **DEP-profiler** under **Hantera inställningar för Apples program för enhetsregistrering (DEP)**.
4. Välj **skapa** på bladet **Apple DEP-profiler**.
5. Ange ett namn och en beskrivning för profilen på bladet **Skapa registreringsprofil**.
6. Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

 - **Registrera med användartillhörighet** – Enheten måste registreras med en användare under den ursprungliga installationen och kan sedan beviljas åtkomst till företagets data och e-post. Välj användartillhörighet för DEP-hanterade enheter som tillhör användare och som måste använda företagsportalen för tjänster som installation av appar. Observera att multifaktorautentisering (MFA) inte fungerar under registreringen på DEP-enheter med användartillhörighet. Efter registreringen fungerar MFA som förväntat på dessa enheter. Nya användare som måste ändra sina lösenord när de loggar in första gången uppmanas inte under registreringen på DEP-enheter. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under DEP-registreringen. De måste återställa lösenordet från en annan enhet.

    >[!NOTE]
    >DEP med användartillhörighet kräver att [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints) aktiveras för att du ska kunna begära en användartoken. [Läs mer om WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

7. Välj **Enhetshanteringsinställningar**, konfigurera följande profilinställningar och välj sedan **Spara**:

    - **Övervakad** – Ett hanteringsläge som aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Om du inte markerar kryssrutan begränsas dina hanteringsfunktioner.

    - **Aktivera** – (Kräver Hanteringsläge = Övervakad) Inaktiverar iOS-inställningar som kan möjliggöra borttagning av hanteringsprofilen. Om du lämnar den här kryssrutan omarkerad tillåter du att hanteringsprofilen tas bort från menyn Inställningar. Det här objektet anges under aktiveringen och kan inte ändras utan en fabriksåterställning.

    - **Tillåt parkoppling** – Anger huruvida iOS-enheter ska kunna synkroniseras med datorer eller inte. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

    - **Apple Configurator-certifikat** – Om du väljer **Tillåt Apple Configurator efter certifikat** under **Tillåt parkoppling** måste du ange vilket Apple Configurator-certifikat som ska importeras.

8. Välj **Inställningar för inställningsassistenten**, konfigurera följande profilinställningar och välj sedan **Spara**:

    - **Avdelningsnamn** – Visas om användaren knackar på **Om konfiguration** under aktiveringen.

    - **Avdelningens telefonnummer** – Visas om användaren klickar på knappen Behöver du hjälp? under aktiveringen.
    - **Alternativ för Installationsassistenten** – Dessa valfria inställningar kan konfigureras senare på menyn **Inställningar** i iOS.
        - **Lösenordskod** – Fråga efter lösenordskod under aktivering. Kräv alltid en lösenordskod om inte enheten ska skyddas eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app).
        - **Platstjänster** – Om en här funktionen är aktiverad frågar Installationsassistenten efter under aktivering
        - **Återställ** – Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering
        - **Apple-ID** – Om det här alternativet är aktiverat uppmanas användaren i iOS att uppge ett Apple-ID när Intune försöker installera en app utan ett ID. Ett Apple-ID krävs för att hämta iOS App Store-appar, inklusive de som har installerats av Intune.
        - **Villkor** – Om det här alternativet är aktiverat uppmanas användarna i installationsassistenten att godkänna Apples villkor under aktiveringen
        - **Touch ID** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Apple Pay** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Zooma** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Siri** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Diagnostikdata** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktiveringen

9. Om du vill spara profilinställningarna väljer du **Skapa** på bladet **Skapa registreringsprofil**.

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>Tilldela din MDM-server Apple DEP-serienummer

1. Gå till [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med företagets Apple-ID.

2. Gå till **Distributionsprogram** &gt; **Enhetsregistreringsprogram (DEP)** &gt; **Hantera enheter**.

3. Ange hur du avser att **välja enheter** och tillhandahåll sedan information om enheten och specifikationer genom **serienummer**, **ordningsnummer** eller genom att välja **Överför CSV-fil**.

4. Välj **Tilldela till server** och välj &lt;servernamnet&gt; som angetts för Microsoft Intune och sedan **OK**.

## <a name="synchronize-dep-managed-devices"></a>Synkronisera DEP-hanterade enheter

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet i Azure-portalen och välj sedan **Apple-registrering**.

3. Välj **DEP-serienummer** under **Hantera inställningar för Apples program för enhetsregistrering (DEP)**.

4. Välj **Synkronisera** på bladet **Apple DEP-serienummer**.

5. Välj **Begär synkronisering** på bladet **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.

    Om du vill följa Apples villkor för godkänd DEP-trafik tillämpar Intune följande begränsningar:
     -    En fullständig DEP-synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer som Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -    Varje synkroniseringsbegäran har 10 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.

>[!NOTE]
>Du kan även tilldela profiler DEP-serienummer från bladet **Apple DEP-serienummer**.

## <a name="distribute-devices-to-users"></a>Distribuera enheter till användare

Nu kan du distribuera företagsägda enheter till användare. När en iOS-enhet aktiveras registreras den för hantering av Intune.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Hur användare installerar och använder företagsportalen på sina enheter

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ytterligare några steg, vilka beskrivs nedan, för att kunna slutföra installationen och installera företagsportalappen.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Hur en användare registrerar företagsägda iOS-enheter med användartillhörighet

1. När användaren startar enheten uppmanas han eller hon att slutföra arbetet med installationsassistenten. Under installationen uppmanas användarna att ange sina autentiseringsuppgifter. Användaren måste använda de autentiseringsuppgifter (unikt namn eller UPN) som är associerade med prenumerationen i Intune.

2. Under installationen uppmanas användarna att ange ett Apple-ID. Användaren måste ange ett Apple-ID för att företagsportalen ska få installeras på enheten. Användaren kan även ange ID från iOS-inställningsmenyn när installationen har slutförts.

3. När installationen har slutförts måste användaren installera företagsportalappen från App Store.

4. Användaren kan nu logga in på företagsportalen med det UPN som angavs när enheten konfigurerades.

5. Efter inloggningen uppmanas användaren att registrera enheten. Det första steget är att identifiera enheten. I appen visas en lista över iOS-enheter som redan är företagsregistrerade och har tilldelats till användarens Intune-konto. Användaren ska välja motsvarande enhet. Om enheten inte är företagsregistrerad måste användaren välja ny enhet och fortsätta med standardregistreringsflödet.

6. På nästa skärm måste användaren bekräfta den nya enhetens serienummer. Användaren gör detta genom att välja den länk som visas. Länken öppnar appen Inställningar, med vars hjälp användaren kan verifiera sitt serienummer. Sedan måste användaren ange de fyra sista tecknen i serienumret i företagsportalappen.

   I det här steget verifieras att enheten är den företagsenhet som har registrerats i Intune. Om serienumret på enheten inte stämmer, så innebär det att användaren har valt fel enhet. Användaren måste gå tillbaka till föregående sida och välja en annan enhet.

7. När serienumret har verifierats omdirigeras användaren från företagsportalappen till företagsportalens webbplats för att slutföra registreringen. På webbplatsen uppmanas sedan användaren att återgå till appen.

Registreringen är klar, och användaren kan nu använda den här enheten med fullständiga funktioner.

