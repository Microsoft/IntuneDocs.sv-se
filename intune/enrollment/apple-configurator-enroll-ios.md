---
title: Registrera iOS-enheter – Apple Configurator – Installationsassistent
titleSuffix: Microsoft Intune
description: Läs hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med installationsassistenten.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d50fdbb766068e643604cdf729e62cdd07d22b62
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723521"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Konfigurera registrering av iOS-enheter med Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune stöder registrering av iOS-enheter med hjälp av [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) på en Mac-dator. Registrering med Apple Configurator kräver att du USB-ansluter varje iOS-enhet till en Mac-dator för att konfigurera företagsregistrering. Du kan registrera enheter i Intune med Apple Configurator på två sätt:
- **Registrering av installationsassistenten** – Rensar enheten och förbereder den för registrering med installationsassistenten.
- **Direktregistrering** – Rensar inte enheten och registrerar enheten via iOS-inställningar. Den här metoden har endast stöd för enheter **utan användartillhörighet**.

Registreringsmetoder med Apple Configurator kan inte användas med [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Krav

- Fysisk åtkomst till iOS-enheter
- [Ange MDM-utfärdare](../fundamentals/mdm-authority-set.md)
- [Ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Enhetsserienummer (endast registrering med installationsassistenten)
- USB-anslutningskablar
- macOS-dator som kör [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Skapa en Apple Configurator-profil för enheter

En enhetsregistreringsprofil definierar inställningarna som tillämpas under registreringen. Dessa inställningar tillämpas bara en gång. Följ dessa steg om du vill skapa en registreringsprofil för att registrera iOS-enheter med Apple Configurator.

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator**  >  **Profiler** > **Skapa**.

    ![Skapa en profil för Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. Under **Skapa registreringsprofil**, skriver du in ett **Namn** och en **Beskrivning** av profilen för administrativa ändamål. Användarna kan inte se den här informationen. Du kan använda fältet Namn för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om dynamiska Azure Active Directory-grupper.

    ![Skärmbild av skärmen skapa profil med Registrera med användartillhörighet valt](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. Ange om enheter med den här profilen måste registreras med eller utan en tilldelad användare under **Användartillhörighet**.

    - **Registrera med användartillhörighet** – välj det här alternativet för enheter som tillhör användare och som vill använda företagsportalen för tjänster som installation av appar. Enheten måste vara kopplad till en användare med Installationsassistenten och kan sedan komma åt företagsdata och e-post. Stöds endast för registrering med installationsassistenten. Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registrera utan användartillhörighet** – välj det här alternativet för enheter som inte är kopplade till en enda användare. Använd det här för enheter som utför uppgifter utan att komma åt lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte. Krävs för direktregistrering.

4. Om du väljer **Registrera med användartillhörighet**, får du alternativet att låta användare autentisera sig med Företagsportalen istället för Apple Installationsassistenten.

    > [!NOTE]
    > Om du vill göra något av följande, ställer du in **Autentisera med Intune-företagsportalen istället för Apple Installationsassistenten** till **Ja**:
    >    - använda multifaktorautentisering
    >    - ge en uppmaning till användare som behöver ändra sina lösenord när de loggar in första gången
    >    - be användarna att återställa sina utgångna lösenord under registreringen.
    >
    > Dessa stöds inte vid autentisering med Apples installationsassistent.


6. Spara profilen genom att välja **Skapa**.

## <a name="setup-assistant-enrollment"></a>Registrering med installationsassistenten

### <a name="add-apple-configurator-serial-numbers"></a>Lägg till Apple Configurator-serienummer

1. Skapa en fil med kommaseparerade värden (CSV) med två kolumner och ingen rubrik. Lägg till serienumret i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 5 000. I en textredigerare ser CSV-listan ut så här:

    F7TLWCLBX196, enhetsinformation</br>
    DLXQPCWVGHMJ, enhetsinformation

   Lär dig [hitta serienumret för en iOS-enhet](https://support.apple.com/HT204073).
2. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator**  >  **Enheter** > **Lägg till**.

5. Välj en **Registeringsprofil** som ska tillämpas på de serienummer som du importerar. Om du vill att den nya serienummersinformationen ska skriva över befintlig information, väljer du **Skriv över information för befintliga identifierare**.
6. Under **Importera enheter**, bläddrar du till csv-filen med serienummer och väljer **Lägg till**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Tilldela om en profil till enhetsserienummer

Du kan tilldela en registreringsprofil när du importerar iOS-serienummer för Apple Configurator-registrering. Du kan även tilldela profiler från två platser i Azure-portalen:
- **Apple Configurator-enheter**
- **AC-profiler**

#### <a name="assign-from-apple-configurator-devices"></a>Tilldela från Apple Configurator-enheter
1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator** > **Enheter** > välj serienumren > **Tilldela profil**.
2. Under **Tilldela profil**, väljer du den **Nya profil** som du vill tilldela och väljer därefter **Tilldela**.

#### <a name="assign-from-profiles"></a>Tilldela från profiler
1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator** > **Profiler** > välj en profil.
2. I profilen väljer du **Tilldelade enheter** och väljer sedan **Tilldela**.
3. Filtrera för att hitta enhetsserienummer som du vill tilldela till profilen, välj enheterna och välj sedan **Tilldela**.

### <a name="export-the-profile"></a>Exportera profilen
När du har skapat profilen och tilldelat serienummer måste du exportera profilen från Intune som en URL. Du kan sedan importera den till Apple Configurator på en Mac för distribution till enheter.

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator** > **Profiler** >  välj profilen att exportera.
2. Välj **Exportera profil** i profilen.
3. Kopiera **Profilens URL**. Du kan sedan lägga till den i Apple Configurator för att definiera den Intune-profil som används av iOS-enheter.

   Därefter importerar du den här profilen till Apple Configurator, genom följande procedur som definierar den Intune-profil som används av iOS-enheter.

### <a name="enroll-devices-with-setup-assistant"></a>Registrera enheter med installationsassistenten

1. På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.
    > [!WARNING]
    > Enheterna återställs till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.
    > Om enheten redan har registrerats med Apple ID-kontot måste enheten tas bort från Apple iCloud innan registreringsprocessen startas. Meddelandet "Det gick inte att aktivera [enhetens namn]" visas.

2. I rutan för **inställningar** väljer du **Servrar** och plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.
3. Ange **värdnamn eller URL** och **registrerings-URL** för MDM-servern under installationsassistentens registrering för iOS-enheter med Microsoft Intune. För registrerings-URL:en anger du URL:en för registreringsprofilen som exporterats från Intune. Välj **Nästa**.  
    Du kan ignorera en varning som anger att server-URL:en inte har verifierats. Fortsätt genom att välja **Nästa** tills guiden har slutförts.
4. Anslut iOS-mobilenheterna till Mac-datorn med en USB-adapter.
5. Välj de iOS-enheter som du vill hantera och välj sedan **Förbered**. I fönstret **Förbered iOS-enhet**, väljer du **Manuellt** och sedan **Nästa**.
6. I fönstret **Registrera i MDM-server** väljer du först servernamnet som du skapat och sedan **Nästa**.
7. I fönstret **Övervaka enheter** väljer du först övervakningsnivån och sedan **Nästa**.
8. I fönstret **Skapa en organisation** väljer du **Organisation** eller skapar en ny organisation och väljer sedan **Nästa**.
9. I fönstret **Konfigurera installationsassistenten för iOS** väljer du stegen som visas för användaren och väljer sedan **Förbered**. Autentisera för att uppdatera förtroendeinställningarna om du uppmanas att göra det.  
10. När iOS-enheten har slutfört förberedelserna kopplar du från USB-kabeln.  

### <a name="distribute-devices"></a>Distribuera enheter
Enheterna är nu klara för företagets registrering. Stäng av enheterna och distribuera dem till användarna. Installationsassistenten startar när användarna sätter på sina enheter.

När användarna får sina enheter måste de slutföra installationsassistenten. Enheter som har konfigurerats med användartillhörighet kan installera och köra företagsportalappen för att ladda ned appar och hantera enheter.

## <a name="direct-enrollment"></a>Direktregistrering
När du registrerar iOS-enheter direkt med Apple Configurator så kan du registrera en enhet utan att hämta enhetens serienummer. Du kan också namnge enheten i identifieringssyfte innan Intune samlar in enhetens namn under registreringen. Företagsportalappen stöds inte för direktregistrerade enheter. Den här metoden rensar inte enheten.

Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, kan inte installeras.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportera profilen som .mobileconfig för iOS-enheter

1. I [Intune](https://aka.ms/intuneportal), väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple Configurator** > **Profiler** >  välj profilen att exportera > **Exportera profil**.
2. Under **Direktregistrering**, väljer du **Hämta profil** och sparar filen. En fil för registreringsprofiler är endast giltig i två veckor, efter det måste du återskapa den.
3. Överför filen till en Mac-dator som kör [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) för att skicka den direkt som en hanteringsprofil till iOS-enheter.
4. Förbered enheten med Apple Configurator med följande steg:
    1. Öppna Apple Configurator 2.0 på en Mac-dator.
    2. Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng Foton, iTunes och andra appar som öppnas för enheten när enheten identifieras.
    3. I Apple Configurator väljer du den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **Profiler**.

        ![Skärmbild av Exportera profil för alternativet Registrering av installationsassistent där profilens webbadress är markerad](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten. Om enheten är obevakad kräver installationen godkännande på enheten.
5. Installera profilen på iOS-enheten på följande sätt. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas. Om registreringen kräver appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributionen kräver att du har ett Apple-ID för App Store.
    1. Lås upp iOS-enheten.
    2. Välj **Installera** för **Hanteringsprofil** i dialogrutan **Installera profil**.
    3. Ange enhetens lösenord eller Apple-ID om så behövs.
    4. Acceptera **varningen** och välj **Installera**.
    5. Acceptera **fjärrvarningen** och välj **Förtroende**.
    6. När rutan **Profilen har installerats** bekräftar att profilen har installerats väljer du **Klar**.

6. Öppna **Inställningar** på iOS-enheten och gå till **Allmänt** > **Enhetshantering** > **Hanteringsprofil**. Bekräfta att profilinstallationen visas och kontrollera iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

7. Distribuera enheter. Nu är iOS-enheten registrerad i Intune och hanteras.





