---
title: "Registrera iOS-enheter – Enhetsregistreringsprogrammet"
titlesuffix: Azure portal
description: "Läs hur du registrerar företagsägda iOS-enheter med programmet för enhetsregistrering.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c14903d227164089f52c9bd3288a99f29a9141b8
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Registrera iOS-enheter automatiskt med Apples DEP (Device Enrollment Program)

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet hjälper dig att aktivera registrering av iOS-enheter som köpts via Apples [program för enhetsregistrering (DEP)](https://deploy.apple.com). Du kan aktivera DEP-registrering för ett stort antal enheter utan att behöva röra dem. Du kan leverera enheter som iPhone och iPad direkt till användare. När användaren sätter på enheten körs installationsassistenten med de konfigurerade inställningarna och enheten registreras i hanteringen.

Om du vill aktivera DEP-registrering kan du använda både Intune och Apples DEP-portal. En lista med serienummer eller inköpsordernummer krävs så att du kan tilldela enheter till Intune för hantering. Du kan skapa DEP-registreringsprofiler som innehåller inställningar som verkställs på enheterna under registreringen.

DEP-registreringen fungerar dock inte med [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Krav
- Enheter som köpts i [Apples enhetsregistreringsprogram](http://deploy.apple.com)
- [MDM-utfärdare](mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

> [!NOTE]
> Multifaktorautentisering (MFA) fungerar inte under inställning av DEP-enheter för användartillhörighet. Efter registreringen fungerar MFA som förväntat på enheterna. Enheterna kan inte uppmana användare som behöver ändra sina lösenord när de loggar in första gången. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. Användarna måste återställa lösenordet från en annan enhet.

## <a name="get-the-apple-dep-token"></a>Hämta Apple DEP-token

Innan du kan registrera iOS-enheter med DEP behöver du en DEP-tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om DEP-enheter som ditt företag äger. Intune kan även överföra registreringsprofiler till Apple och tilldela enheter till dessa profiler.

Du kan använda Apples DEP-portal för att skapa en DEP-token. Du kan också använda DEP-portalen för att tilldela enheter till Intune för hantering.

> [!NOTE]
> Om du tar bort denna token från den klassiska Intune-portalen innan du migrerar till Azure, kan Intune återställa en borttagen Apple DEP-token. Du kan ta bort DEP-token från Azure-portalen igen. Du kan ta bort DEP-token från Azure-portalen igen.

**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple DEP-token.**<br>

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat.](./media/enrollment-program-token-add.png)

2. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

  ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/enrollment-program-token-download.png)

**Steg 2. Skapa och ladda ned en Apple DEP-token.**<br>
1. Välj **Skapa en token via Apples enhetsregistreringsprogram (DEP)** så öppnas Apples portal för driftsättningsprogram. Logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.
2.  Gå till Apples [portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**.

3. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.
4. Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

   ![Skärmbild av hur någon lägger till ett MDM-servernamn för DEP och sedan klickar på Nästa.](./media/enrollment-program-token-add-server.png)

5. Dialogrutan **Lägg till &lt;ServerName&gt; ** öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.

6.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.

7. Gå till **Distributionsprogram** &gt; **Program för enhetsregistrering** &gt; **Hantera enheter**.
8. Under **Choose Devices By** (Välj enheter efter) anger du hur enheterna ska identifieras:
    - **Serienummer**
    - **Ordernummer**
    - **Ladda upp CSV-fil**.

   ![Skärmbild av någon som anger enheterna ska visas efter serienummer, väljer åtgärden Assign to Server (Tilldela till server) och sedan servernamnet.](./media/enrollment-program-token-specify-serial.png)

9. Välj **Assign to Server** (Tilldela till server) för **Välj åtgärd** och välj **servernamnet** som angetts för Microsoft Intune och sedan &lt;OK&gt;. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

**Steg 3. Ange det Apple-ID som användes för att skapa din registreringsprogramtoken.**<br>I Intune på Azure-portalen anger du ditt Apple-ID för framtida bruk. Du kan använda detta ID för att förnya din registreringsprogramtoken i framtiden och slippa behöva registrera alla enheter på nytt.

![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/enrollment-program-token-apple-id.png)

**Steg 4. Bläddra till den registreringsprogramtoken som du vill ladda upp.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter. Intune synkroniseras automatiskt med Apple och visar ditt registreringsprogramkonto.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil

Nu när du har installerat din token kan skapa du en registreringsprofil för DEP-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering**.
2. Under **Registreringsprogram för Apple** väljer du **Profiler för registreringsprogram** > **Skapa**.
3. Ange ett **namn** och en **beskrivning** för profilen på bladet **Skapa registreringsprofil**. Detta behövs för administrativa syften. Användarna kan inte se den här informationen. Du kan använda fältet **Namn** för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om [dynamiska Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

  Ange om enheter med den här profilen ska registreras med eller utan en tilldelad användare under **Användartillhörighet**.

 - Välj **Registrera med användartillhörighet** – Välj detta för enheter som tillhör användare och som måste använda företagsportalen för tjänster som installation av appar.

 - **Registrera utan användartillhörighet** – Välj detta för enheter som inte är kopplade till en enda användare. Använd detta för enheter som utför uppgifter utan att öppna lokala användardata. Appar som företagsportalappen fungerar inte.

4. Välj **Enhetshanteringsinställningar** för att konfigurera följande profilinställningar:

  ![Skärmbild av val av hanteringsläge. Enheten har följande inställningar: Kontrollerad, Låst registrering samt Tillåt parkoppling inställd på Neka alla. Apple Configurator-certifikat är nedtonat för en ny registreringsprogramprofil.](./media/enrollment-program-profile-mode.png)
    - **Övervakad** – Ett hanteringsläge som aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Om du inte markerar kryssrutan begränsas dina hanteringsfunktioner.

    - **Aktivera** – (Kräver Hanteringsläge = Övervakad) Inaktiverar iOS-inställningar som kan möjliggöra borttagning av hanteringsprofilen. Om du lämnar den här kryssrutan omarkerad tillåter du att hanteringsprofilen tas bort från menyn Inställningar. När enhetsregistreringen är klar går det inte att ändra inställningen utan att göra en fabriksåterställning av enheten.

    - **Tillåt parkoppling** – Anger huruvida iOS-enheter ska kunna synkroniseras med datorer eller inte. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

    - **Apple Configurator-certifikat** – Om du väljer **Tillåt Apple Configurator efter certifikat** under **Tillåt parkoppling** måste du ange vilket Apple Configurator-certifikat som ska importeras.

  Välj **Spara**.

5. Välj **Inställningar för inställningsassistenten** och konfigurera följande profilinställningar:

  ![Skärmbild av någon som väljer konfigurationsinställningar för en ny registreringsprogramprofil.](./media/enrollment-program-profile-settings.png)
    - **Avdelningsnamn** – Visas om användaren knackar på **Om konfiguration** under aktiveringen.

    - **Avdelningens telefonnummer** – Visas om användaren klickar på knappen **Behöver du hjälp?** under aktiveringen.
    - **Alternativ för Installationsassistenten** – Dessa valfria inställningar kan konfigureras senare på menyn **Inställningar** i iOS.
        - **Lösenord**
        - **Platstjänster**
        - **Återställa**
        - **Apple-ID**
        - **Villkor**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **Diagnostikdata**

    Välj **Spara**.
9. Om du vill spara profilinställningarna väljer du **Skapa** på bladet **Skapa registreringsprofil**. Registreringsprofilen visas i listan Registreringsprofiler för Apples registreringsprogram.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter
Nu när Intune har fått behörighet att hantera dina enheter, kan du synkronisera Intune med Apple och se dina hanterade enheter i Intune på Azure-portalen.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** >  **Apple-registrering** > **Registreringsprogramenheter**.
2. Under **Registreringsprogramenheter** väljer du **Synkronisera**.

  ![Skärmbild där noden Registreringsprogramenheter har valts och länkvärde håller på att väljas.](./media/enrollment-program-device-sync.png)
3. Välj **Begär synkronisering** på bladet **Synkronisera**. Förloppsindikatorn visar hur lång tid som du måste vänta innan du begär synkronisering igen.

  ![Skärmbild av bladet Synkronisera där länken Begär synkronisering håller på att väljas.](./media/enrollment-program-device-request-sync.png)

  För att följa Apples villkor för godkänd registreringsprogramtrafik tillämpar Intune följande begränsningar:
     -  En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Vid en fullständig synkronisering uppdateras Intune med alla Apple-serienummer som tilldelats till Intune. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran har 15 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.
     - Intune synkroniserar nya och borttagna enheter med Apple var 24:e timme.

4. I arbetsytan Registreringsprogramenheter väljer du **Uppdatera** för att visa dina enheter.

## <a name="assign-an-enrollment-profile-to-devices"></a>Tilldela enheterna en registreringsprofil
Du måste tilldela en registreringsprogramprofil till enheterna innan de kan registreras.

>[!NOTE]
>Du kan även tilldela profiler serienummer från bladet **Apple-serienummer**.

1. I Intune på Azure-portalen väljer du **Enhetsregistrering** > **Apple-registrering** och väljer sedan **Registreringsprogramprofiler**.
2. Från listan över **Registreringsprogramprofiler** väljer du den profil du vill tilldela till enheter och väljer därefter **Tilldela enheter**.

 ![Skärmbild av enhetstilldelningar med Tilldela markerat.](./media/enrollment-program-device-assign.png)

3. Välj **Tilldela** och markera sedan de enheter som du vill tilldela den här profilen. Du kan använda filter för att enbart visa tillgängliga enheter:
  - **ej tilldelad**
  - **alla**
  - **&lt;profilnamn&gt;**
4. Markera de enheter som du vill tilldela. Du kan använda kryssrutan ovanför kolumnen för välja upp till 1 000 listade enheter och sedan klicka på **Tilldela**. Om du vill registrera mer än 1 000 enheter måste du upprepa tilldelningen tills alla enheter har tilldelats en registreringsprofil.

  ![Skärmbild av knappen Tilldela som används för att tilldela registreringsprogramprofiler i Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>Distribuera enheter
Du har aktiverat hantering och synkronisering mellan Apple och Intune, och har tilldelat en profil så att DEP-enheterna kan registreras. Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens. Enheter utan användartillhörighet kräver en enhetslicens. En aktiverad enhet kan inte använda en registreringsprofil förrän enheten har återställts till fabriksinställningarna.

Se [Registrera din iOS-enhet i Intune med enhetsregistreringsprogrammet](/intune-user-help/enroll-your-device-dep-ios).
