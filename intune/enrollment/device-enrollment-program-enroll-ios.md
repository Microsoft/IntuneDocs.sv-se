---
title: Registrera iOS/iPadOS-enheter – Enhetsregistreringsprogrammet
titleSuffix: Microsoft Intune
description: Läs hur du registrerar företagsägda iOS/iPadOS-enheter med programmet för enhetsregistrering.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a1eca1f8911e9c6aae3b3725cf15f04d954c5f48
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260324"
---
# <a name="automatically-enroll-iosipados-devices-with-apples-device-enrollment-program"></a>Registrera iOS/iPadOS-enheter automatiskt med Apples DEP (Device Enrollment Program)

Du kan konfigurera Intune till att registrera iOS/iPadOS-enheter som köpts via Apples [program för enhetsregistrering (DEP)](https://deploy.apple.com). Med DEP kan du konfigurera ett stort antal enheter utan att behöva röra dem. Enheter som iPhones, iPads och MacBooks kan levereras direkt till användarna. När användaren sätter på enheten körs installationsassistenten, som innehåller vanliga funktioner för Apple-produkter, med de förkonfigurerade inställningarna och enheten registreras i hanteringen.

Om du vill aktivera DEP-registrering använder du både Intune-portalen samt Apple Business Manager (ABM)- eller Apple School Manager (ASM)-portalen. En lista med serienummer eller inköpsordernummer krävs för att du ska kunna tilldela enheter till Intune för hantering i ABM/ASM. Du kan skapa DEP-registreringsprofiler i Intune med inställningar som tillämpas på enheterna under registreringen. Observera DEP-registreringen kan inte användas med [enhetsregistreringshanterarens](device-enrollment-manager-enroll.md) konto.

> [!NOTE]
> DEP ställer in enhetskonfigurationer som inte alltid kan tas bort av slutanvändaren. Innan [migreringen till DEP](../fundamentals/migration-guide-considerations.md) måste enheten därför rensas så att den återställs till dess ursprungliga tillstånd (fabriksinställningarna).

## <a name="dep-and-the-company-portal"></a>DEP och företagsportalen

DEP-registreringar är inte kompatibla med App Store-versionen av företagsportalappen. Du kan ge användarna åtkomst till företagsportalappen på en DEP-enhet. Du kanske vill ange åtkomsten så att användarna kan välja vilka företagsappar de vill använda på sin enhet, eller använda modern autentisering för att slutföra registreringsprocessen. 

Om du vill aktivera modern autentisering vid registreringen, skickar du appen till enheten med **Installera företagsportalen med VPP** (volyminköpsprogram) i DEP-profilen. Mer information finns i [Registrera iOS/-enheter automatiskt med Apples program för enhetsregistrering](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

Om du vill att företagsportalen ska uppdateras automatiskt och erbjuda företagsportalappen på enheter som redan har registrerats med DEP, distribuerar du företagsportalappen via Intune som ett obligatoriskt volyminköpsprogram (VPP) med en [programkonfigurationsprincip](../apps/app-configuration-policies-use-ios.md).

Obs! Vid automatisk enhetsregistrering, när Företagsportal körs i enstaka appläge, visas ett felmeddelande när du klickar på länken ”Läs mer” på grund av läget. När registreringen är färdig kan du visa mer information i Företagsportal när enheten inte längre är i enstaka appläge. 

## <a name="what-is-supervised-mode"></a>Vad är övervakat läge?

Apple införde övervakat läge i iOS/iPadOS 5. En iOS/iPadOS-enhet i övervakat läge kan hanteras med fler kontroller, exempelvis kontroller som blockerar skärmdumpar eller installation av appar från App Store. Det är därför användbart för företagsägda enheter. Intune har stöd för konfigurering av enheter för övervakat läge som en del av Apples program för enhetsregistrering (DEP).

Stöd för ej kontrollerade DEP-enheter upphörde i iOS/iPadOS 11. I iOS/iPadOS 11 och senare bör DEP-konfigurerade enheter alltid övervakas. Flaggan DEP is_supervised ignoreras i en framtida iOS/iPadOS-version.

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
- [Utfärdare för hantering av mobil enhet (MDM)](../fundamentals/mdm-authority-set.md)
- [Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Hämta en Apple DEP-token

Innan du kan registrera iOS/iPadOS-enheter med DEP behöver du en DEP-tokenfil (.p7m) från Apple. Med denna token kan Intune synkronisera information om DEP-enheter som ditt företag äger. Intune kan även överföra registreringsprofiler till Apple och tilldela enheter till dessa profiler.

Du kan använda Apple Business Manager- eller Apple School Manager-portalen till att skapa en token. Du kan också använda ABM/ASM-portalen för att tilldela enheter till Intune för hantering.

> [!NOTE]
> Om du tar bort denna token från den klassiska Intune-portalen innan du migrerar till Azure, kan Intune återställa en borttagen Apple DEP-token. Du kan ta bort DEP-token från Azure-portalen igen.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckeln som krävs för att skapa token.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram** > **Lägg till**.

    ![Hämta en registreringsprogramtoken.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Välj **Jag godkänner** för att ge Microsoft behörighet att skicka information om användare och enhet till Apple.

> [!NOTE]
> När du kommit förbi steg 2 och ska ladda ned certifikatet för den offentliga Intune-nyckeln, ska du inte stänga guiden eller navigera från sidan. Om du gör det ogiltigförklaras certifikatet du har laddat ned. I så fall måste du utföra den här processen på nytt. Då blir också knappen Skapa och fliken Granska + skapa nedtonad, och du kan inte slutföra processen.

   ![Skärmbild av rutan Registreringsprogramtoken i arbetsytan för Apple-certifikat. Nedladdning av offentlig nyckel.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Steg 2. Använd din nyckel för att hämta en token från Apple.

1. Välj **Skapa en token för Apples enhetsregistreringsprogram** för att öppna Apples portal för distributionsprogram och logga in med ditt företags Apple-ID. Du måste använda detta Apple-ID för att kunna förnya DEP-token.
2. Gå till Apples [portal för driftsättningsprogram](https://deploy.apple.com) och välj **Kom igång** för **Enhetsregistreringsprogram**.

3. På sidan **Hantera servrar** väljer du **Lägg till MDM-server**.
4. Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

5. Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas med meddelandet **Upload Your Public Key** (Överför din offentliga nyckel). Markera **Välj fil...** för att överföra PEM-filen och välj sedan **Nästa**.

6. Gå till **Distributionsprogram** &gt; **Programmet för enhetsregistrering** &gt; **Hantera enheter**.
7. Under **Choose Devices By** (Välj enheter efter) anger du hur enheterna ska identifieras:
    - **Serienummer**
    - **Ordernummer**
    - **Ladda upp CSV-fil**.

   ![Skärmbild av någon som anger enheterna ska visas efter serienummer, väljer åtgärden Assign to Server (Tilldela till server) och sedan servernamnet.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. Välj **Assign to Server** (Tilldela till server) för **Välj åtgärd** och välj **servernamnet** som angetts för Microsoft Intune och sedan &lt;OK&gt;. Apples portal tilldelar de angivna enheterna till Intune-servern för hantering och visar sedan meddelandet **Assignment Complete** (Tilldelningen är klar).

   Gå till Apple-portalen och **Driftsättningsprogram** &gt; **Enhetsregistreringsprogram** &gt; **View Assignment History (Visa historik för tilldelning)** för att se en lista över enheter och deras MDM-servertilldelning.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Steg 3. Spara det Apple-ID som användes för att skapa den här token.

I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) anger du Apple-ID:t för framtida referens.

![Skärmbild av någon som anger det Apple-ID som användes för att skapa registreringsprogramtoken och bläddrat till denna token.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Steg 4. Ladda upp din token och välj omfångstaggar.

1. I rutan **Apple-token** bläddrar du till certifikatfilen (.pem) och väljer **Öppna**.
2. Om du vill tillämpa [omfångstaggar](../fundamentals/scope-tags.md) på denna DEP-token, väljer du **Omfång (taggar)** och de omfångstaggar som du vill använda. Omfångstaggar som tillämpas på en token ärvs av profiler och enheter som läggs till i den.
3. Välj **Skapa**.

Med pushcertifikatet kan Intune registrera och hantera iOS/iPadOS-enheter genom push-överföring av principer till registrerade mobila enheter. Intune synkroniseras automatiskt med Apple och visar ditt registreringsprogramkonto.

## <a name="create-an-apple-enrollment-profile"></a>Skapa en Apple-registreringsprofil

Nu när du har installerat din token kan skapa du en registreringsprofil för DEP-enheter. En enhetsregistreringsprofil definierar inställningarna som tillämpas på en grupp av enheter vid registreringen. Det finns en gräns på 100 registreringsprofiler per DEP-token.

> [!NOTE]
> Enheterna kommer att blockeras om det inte finns tillräckligt med licenser i företagsportalen för en VPP-token, eller om token har upphört att gälla. Intune visar en varning när en token snart upphör att gälla, eller om licenserna börjar ta slut.
 

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram**.
2. Välj en token, välj **Profiler** > **Skapa profil** > **iOS**.

    ![Skärmbild av Skapa en profil.](./media/device-enrollment-program-enroll-ios/image04.png)

3. På sidan **Grundinställningar**, anger du ett **Namn** och **Beskrivning** för profilen för administrationssyfte. Användarna kan inte se den här informationen. Du kan använda fältet **Namn** för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om [dynamiska Azure Active Directory-grupper](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Profilnamn och beskrivning.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Välj **Nästa: Enhetshanteringsinställningar**.

5. Ange om enheter med den här profilen måste registreras med eller utan en tilldelad användare under **Användartillhörighet**.
    - **Registrera med användartillhörighet** – välj det här alternativet för enheter som tillhör användare och som vill använda Intune-företagsportalappen för tjänster som installation av appar. Om du använder ADFS och registreringsprofilen har **Autentisera med företagsportalen i stället för installationsassistenten** inställt på **Nej**, krävs [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints) [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registrera utan användartillhörighet** – välj det här alternativet för enheter som inte är kopplade till en enda användare. Använd det här alternativet för enheter som inte kommer åt lokala användardata. Appar som Företagsportal fungerar inte.

5. Om du väljer **Registrera med användartillhörighet**, kan du låta användare autentisera sig med företagsportalen istället för Apple Installationsassistenten.

    ![Autentisera med Företagsportalen.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Om du vill göra något av följande anger du **Välj var användarna måste autentiseras** till **Företagsportal**.
    >    - använda multifaktorautentisering
    >    - ge en uppmaning till användare som behöver ändra sina lösenord när de loggar in första gången
    >    - be användarna att återställa sina utgångna lösenord under registreringen.
    >
    > Dessa stöds inte vid autentisering med Apples installationsassistent.

6. Om du väljer **Företagsportal** för **Välj var användarna måste autentiseras**, kan du använda en VPP-token för att automatiskt installera företagsportalen på enheten. I det här fallet behöver användaren inte ange ett Apple-ID. Om du vill installera Företagsportalen med en VPP-token väljer du en token under **Installera Företagsportalen med VPP**. Kräver att företagsportalen redan har lagts till i VPP-token. Kontrollera att du har konfigurerat appdistribution i Intune (Intune>Klientappar) för att säkerställa att företagsportalappen uppdateras även efter registreringen. Om du vill undvika användarinteraktion bör du skaffa Företagsportal som en iOS/iPadOS VPP-app, göra den till en obligatorisk app och använda enhetslicenser för tilldelningen. Se till att den token du väljer inte upphör att gälla och att du har tillräckligt många enhetslicenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune installera företagsportalen från App Store istället, och då krävs ett Apple-ID. 

    > [!NOTE]
    > När **Välj var användarna måste autentiseras** är inställt till **Företagsportal**, se till att enhetsregistreringsprocessen utförs inom de närmsta 24 timmarna efter att företagsportalen laddats ned till DEP-enheten. Annars kan registreringen misslyckas och en fabriksåterställning krävs för att registrera enheten.
    
    ![Skärmbild av installation av Företagsportalen med VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Om du väljer **Installationsassistent** för **Välj var användarna måste autentiseras**, men du även vill använda villkorlig åtkomst eller distribuera företagsprogram på enheterna, måste du installera företagsportalen på enheterna. Välj **Ja** för att **Installera Företagsportalen**.  Om du vill att användarna ska kunna ta emot företagsportalen utan att behöva autentisera till App Store väljer du **Installera företagsportalen med VPP** och väljer en VPP-token. Se till att den token du väljer inte upphör att gälla och att du har tillräckligt många enhetslicenser för företagsportalappen för att distribuera den korrekt.

8. Om du väljer en token för **Installera företagsportalen med VPP** kan du låsa enheten i enkelt appläge (specifikt företagsportalappen) direkt efter att installationsassistenten har slutförts. Välj **Ja** för **Run Company Portal in Single App Mode until authentication** (Kör företagsportalappen i enkelt appläge till autentisering) för att ange detta alternativ. För att kunna använda enheten måste användaren först autentisera genom att logga in med företagsportalen.

    Multifaktorautentisering stöds inte på en enskild enhet som är låst i ett enkelt appläge. Den här begränsningen finns eftersom enheten inte kan växla till en annan app för att slutföra den andra faktorn för autentisering. Därför måste den andra faktorn vara på en annan enhet om du vill ha multifaktorautentisering på en enhet med enkelt appläge.

    Den här funktionen fungerar bara för iOS/iPadOS 11.3.1 och senare.

   ![Skärmbild av läget för enskilda appar.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Om du vill att enheter som använder den här profilen ska övervakas väljer du **Ja** för **Övervakade**.

    ![Skärmbild för Enhetshanteringsinställningar.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    **Övervakade** enheter ger dig fler hanteringsalternativ och inaktiverar aktiveringslåset som standard. Microsoft rekommenderar att du använder DEP som mekanism för att aktivera övervakat läge, särskilt om du distribuerar större antal iOS/iPadOS-enheter.

    Användare meddelas att deras enheter är övervakade på två sätt:

   - Låsskärmen säger: ”Denna iPhone hanteras av Contoso.”
   - Skärmen **Inställningar** > **Allmänt** > **Om** säger: ”Denna iPhone är övervakad. Contoso can monitor your Internet traffic and locate this device." (Denna iPhone är övervakad. Contoso kan övervaka din Internettrafik och hitta denna enhet.)

     > [!NOTE]
     > En enhet som registrerats utan övervakning kan bara återställas genom att använda Apple Configurator. Om du återställer enheten på det här sättet, måste du ansluta en iOS/iPadOS-enhet till en Mac-dator med en USB-kabel. Läs mer om detta i [dokumentation för Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Välj om du vill ha låst registrering för enheter som använder den här profilen. **Låst registrering** inaktiverar iOS/iPadOS-inställningarna som tillåter att hanteringsprofilen tas bort från menyn **Inställningar**. När enhetsregistreringen är klar går det inte att ändra inställningen utan att göra en rensning av enheten. Sådana enheter måste ha hanteringsläget **Övervakad** inställt på *Ja*. 

11. Välj om du vill att enheter som använder den här profilen ska kunna **Synkronisera med datorer**. Om du väljer **Tillåt Apple Configurator efter certifikat** måste du välja ett certifikat under **Apple Configurator-certifikat**.

12. Om du väljer **Tillåt Apple Configurator efter certifikat** i föregående steg, väljer du ett Apple Configurator-certifikat att importera.

13. Du kan ange ett namngivningsformat för enheter som tillämpas automatiskt när de registreras och vid varje incheckning. Om du vill skapa en namngivningsmall väljer du **Ja** under **Använd mall för enhetsnamn**. I rutan **Mall för enhetsnamn** anger du sedan den mall som ska användas för de namn som använder den här profilen. Du kan ange ett mallformat som innehåller enhetstyp och serienummer. 

14. Välj **Nästa: Anpassning av installationsassistenten**.

15. På sidan **Anpassning av installationsassistenten** konfigurerar du följande profilinställningar: ![Anpassning av installationsassistenten.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Avdelningsinställningar | Beskrivning |
    |---|---|
    | <strong>Avdelningsnamn</strong> | Visas när användare trycker på <strong>Om konfiguration</strong> vid aktiveringen. |
    |    <strong>Avdelningens telefonnummer</strong>     | Visas när användaren klickar på knappen <strong>Behöver hjälp</strong> vid aktiveringen. |

    Du kan välja att dölja installationsassistentens skärmar på enheten under användarinstallationen.
    - Om du väljer **Dölj** visas inte skärmen under installationen. När enheten har konfigurerats kan användaren fortfarande använda menyn **Inställningar** för att ställa in funktionen.
    - Om du väljer **Visa** så visas skärmen under installationen. Användaren kan ibland hoppa över skärmen utan att vidta några åtgärder. Det går dock att öppna menyn **Inställningar** på enheten för att ställa in funktionen. 


    | Inställningar på skärm i Installationsassistenten | Om du väljer **Visa** kommer enheten under installationen att ... |
    |------------------------------------------|------------------------------------------|
    | <strong>Lösenord</strong> | Fråga användaren om ett lösenord. Kräv alltid ett lösenord för osäkrade enheter om inte åtkomsten kontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app). |
    | <strong>Platstjänster</strong> | Fråga användaren om deras plats. |
    | <strong>Återställa</strong> | Visa skärmen Appar och data. På den här skärmen kan användaren återställa eller överföra data från säkerhetskopieringen i iCloud när enheten konfigureras. |
    | <strong>iCloud och Apple-ID</strong> | Ge användaren möjlighet att logga in med sitt Apple-ID och använda iCloud.                         |
    | <strong>Villkor</strong> | Kräva att användaren godkänner Apples användarvillkor. |
    | <strong>Touch ID</strong> | Ge användaren möjlighet att ställa in identifiering med fingeravtryck för enheten. |
    | <strong>Apple Pay</strong> | Ge användaren möjlighet att konfigurera Apple Pay på enheten. |
    | <strong>Zoom</strong> | Ge användaren möjlighet att zooma in på skärmen under konfigurationen. |
    | <strong>Siri</strong> | Ge användaren möjlighet att ställa in Siri. |
    | <strong>Diagnostikdata</strong> | Visa skärmen Diagnostik för användaren. På den här skärmen kan användaren välja att skicka diagnostikdata till Apple. |
    | <strong>Visningston</strong> | Ge användaren möjlighet att aktivera Visningston. |
    | <strong>Sekretess</strong> | Visa sekretesskärmen för användaren. |
    | <strong>Android-migrering</strong> | Ge användaren möjlighet att migrera data från en Android-enhet. |
    | <strong>iMessage och FaceTime</strong> | Ge användaren möjlighet att konfigurera iMessage och FaceTime. |
    | <strong>Registrering</strong> | Visa informationsskärmar för registrering för användarutbildning, som försättsblad och multitasking och kontrollcenter. |
    | <strong>Klockmigrering</strong> | Ge användaren möjlighet att migrera data från en klockenhet. |
    | <strong>Skärmtid</strong> | Visa skärmen Skärmtid. |
    | <strong>Programuppdatering</strong> | Visa skärmen för obligatorisk programuppdatering. |
    | <strong>SIM-installation</strong> | Ge användaren möjlighet att lägga till ett mobilabonnemang. |
    | <strong>Utseende</strong> | Visa skärmen Utseende för användaren. |
    | <strong>Express-språk</strong>| Visa skärmen Express-språk för användaren. |
    | <strong>Önskat språk</strong> | Ge användaren möjlighet att välja **Önskat språk**. |
    | <strong>Migrering av enhet till enhet</strong> | Ge användaren möjlighet att migrera data från sin gamla enhet till den här enheten.|
    

16. Välj **Nästa** för att gå till sidan **Granska + skapa**.

17. Spara profilen genom att välja **Skapa**.

## <a name="sync-managed-devices"></a>Synkronisera hanterade enheter
Nu när Intune har fått behörighet att hantera dina enheter, kan du synkronisera Intune med Apple och se dina hanterade enheter i Intune på Azure-portalen.

1. Gå till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), välj **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram** > välj en token i listan > **Enheter** > **Synkronisera**. ![Skärmbild på noden Registreringsprogramenheter och länken Synkronisera.](./media/device-enrollment-program-enroll-ios/image06.png)

   För att följa Apples villkor för godkänd registreringsprogramtrafik tillämpar Intune följande begränsningar:
   - En fullständig synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering, hämtar Intune den fullständigt uppdaterade listan med serienummer som tilldelats den Apple MDM-server som är ansluten till Intune. Om en DEP-enhet tas bort från Intune-portalen ska den inte vara tilldelad från Apple MDM-servern i DEP-portalen. Om den ej är tilldelad, importeras den inte om till Intune förrän den fullständiga synkroniseringen har körts.   
   - En synkronisering körs automatiskt var 24:e timme. Du kan också synkronisera genom att klicka på **Synkronisera**-knappen (högst en gång var 15:e minut). Alla synkroniseringsbegäranden ges 15 minuter att slutföras. **Synkronisera**-knappen är inaktiverad tills att en synkronisering har slutförts. Synkroniseringen kommer att uppdatera status för befintliga enheter och importera nya enheter som tilldelats Apple MDM-servern.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Tilldela enheterna en registreringsprofil
Du måste tilldela en registreringsprogramprofil till enheterna innan de kan registreras.

>[!NOTE]
>Du kan även tilldela profiler serienummer från bladet **Apple-serienummer**.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram** > välj en token i listan.
2. Välj **Enheter** > välj enheter i listan > **Tilldela profil**.
3. Välj en profil för enheterna under **Tilldela profil** och välj sedan **Tilldela**.

### <a name="assign-a-default-profile"></a>Ange som standardprofil

Du kan välja en standardprofil som ska tillämpas för alla enheter som registreras med en specifik token.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram** > välj en token i listan.
2. Välj **Ange standardprofil**, välj en profil i listmenyn och välj sedan **Spara**. Den här profilen kommer att tillämpas på alla enheter som registreras med token.

## <a name="distribute-devices"></a>Distribuera enheter
Du har aktiverat hantering och synkronisering mellan Apple och Intune, och har tilldelat en profil så att DEP-enheterna kan registreras. Du kan nu distribuera enheter till användare. Enheter med användartillhörighet kräver att varje användare tilldelas en Intune-licens. Enheter utan användartillhörighet kräver en enhetslicens. En aktiverad enhet kan inte använda en registreringsprofil förrän enheten har rensats.

Mer information finns i [Registrera din iOS/iPadOS-enhet i Intune med enhetsregistreringsprogrammet](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Ladda upp en DEP-token  
1. Gå till deploy.apple.com.  
2. Under **Hantera servrar**, väljer du din MDM-server som är associerad med den tokenfil som du vill förnya.
3. Välj **Skapa ny Token**.

    ![Skärmbild av Skapa ny token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Välj **Din servertoken**.  
5. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **iOS** > **iOS-registrering** > **Token för registreringsprogram** > välj token.
    ![Skärmbild av registreringsprogramtoken.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Välj **Förnya token** och ange det Apple-ID som användes för att skapa den ursprungliga token.  
    ![Skärmbild av Skapa ny token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Överför den nyligen hämtade token.  
9. Välj **Förnya token**. Du får se en bekräftelse att token har förnyats.   
    ![Skärmbild av bekräftelse.](./media/device-enrollment-program-enroll-ios/confirmation.png)
