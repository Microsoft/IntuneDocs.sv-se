---
title: "Registrera iOS-enheter – Apple Configurator – installationsassistent"
titlesuffix: Azure portal
description: "Läs hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med installationsassistenten.”"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 10/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c758519f523bf6b61adc7f779043aa4a944998ea
ms.sourcegitcommit: 9fabf1a8db53842f7b00762374de5b137158ee25
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/22/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Registrera iOS-enheter med Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune stöder registrering av iOS-enheter med hjälp av [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) på en Mac-dator. Registrering med Apple Configurator kräver att du USB-ansluter varje iOS-enhet till en Mac-dator för att konfigurera företagsregistrering. Du kan registrera enheter i Intune med Apple Configurator på två sätt:
- **Registrering av installationsassistenten** – Fabriksåterställer enheten och förbereder den för registrering med installationsassistenten.
- **Direktregistrering** – Fabriksåterställer inte enheten och registrerar enheten via iOS-inställningar. Den här metoden har endast stöd för enheter **utan användartillhörighet**.

Registreringsmetoder med Apple Configurator kan inte användas med [enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Krav

- Fysisk åtkomst till iOS-enheter
- [Ange MDM-utfärdare](mdm-authority-set.md)
- [Ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Enhetsserienummer (endast registrering med installationsassistenten)
- USB-anslutningskablar
- macOS-dator som kör [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Skapa en Apple Configurator-profil för enheter

En enhetsregistreringsprofil definierar inställningarna som tillämpas under registreringen. Dessa inställningar tillämpas bara en gång. Följ dessa steg om du vill skapa en registreringsprofil för att registrera iOS-enheter med Apple Configurator.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetsregistrering** > **Apple-registrering**.
4. Välj **AC-profiler** under **Hantera Apple Configurator-registreringsinställningar**.
5. Välj **Skapa** under **Registreringsprofiler i Apple Configurator**.
6. Ange ett **namn** och en **beskrivning** för profilen. Detta behövs för administrativa syften. Användarna kan inte se den här informationen. Du kan använda fältet Namn för att skapa en dynamisk grupp i Azure Active Directory. Använd profilnamnet för att definiera parametern enrollmentProfileName för att tilldela registreringsprofilen till enheter. Läs mer om dynamiska Azure Active Directory-grupper.

  ![Skärmbild av skärmen skapa profil med Registrera med användartillhörighet valt](./media/apple-configurator-profile-create.png)

7. Ange **Användartillhörighet**:
   - **Registrera med användartillhörighet** – Enheten måste vara kopplad till en användare med installationsassistenten och kan sedan komma åt företagets data och e-post. Användartillhörighet krävs för hanterade enheter som tillhör användare och som måste använda företagsportalen för tjänster som installation av appar. Stöds endast för registrering med installationsassistenten. Mappning mellan användare kräver [WS-Trust 1.3 användarnamn/kombinerad slutpunkt](https://technet.microsoft.com/library/adfs2-help-endpoints). [Läs mer](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

   > [!NOTE]
   > Multifaktorautentisering (MFA) fungerar inte under konfigureringen av registrering med användartillhörighet. Efter registreringen fungerar MFA som förväntat på enheterna. Enheterna kan inte uppmana användare som behöver ändra sina lösenord när de loggar in första gången. Användare vars lösenord har upphört att gälla ombeds inte att återställa sina lösenord under registreringen. Användarna måste återställa lösenordet från en annan enhet.

   - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte. Krävs för direktregistrering.

6. Spara profilen genom att välja **Skapa**.

## <a name="setup-assistant-enrollment"></a>Registrering med installationsassistenten

### <a name="add-apple-configurator-serial-numbers"></a>Lägg till Apple Configurator-serienummer

**Lägga till Apple Configurator-serienummer till Intune**

1. Skapa en fil med kommaseparerade värden (CSV) med två kolumner och ingen rubrik. Lägg till serienumret i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 5 000. I en textredigerare ser CSV-listan ut så här:

    F7TLWCLBX196, enhetsinformation</br>
    DLXQPCWVGHMJ, enhetsinformation

   Lär dig [hitta serienumret för en iOS-enhet](https://support.apple.com/HT204073).
2. I Intune på Azure-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
3. Välj **Apple Configurator-enheter** under **Hantera Apple Configurator-registreringsinställningar**.
4. Välj **Lägg till**.
5. Välj en **Registeringsprofil** som ska tillämpas på de serienummer som du importerar. Om du importerar en fil med ny information som skriver över befintlig information väljer du **Skriv över information om befintliga id:n**.
6. Navigera till CSV-filen med serienummer och välj **Lägg till**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Tilldela om en profil till enhetsserienummer

Du kan tilldela en registreringsprofil när du importerar iOS-serienummer för Apple Configurator-registrering. Med Intune kan du även tilldela profiler från två platser i Azure-portalen:
- **Apple Configurator-enheter**
- **AC-profiler**

#### <a name="assign-from-apple-configurator-devices"></a>Tilldela från Apple Configurator-enheter
1. I Intune på Azure-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
3. Välj de serienummer som du vill tilldela en profil till under **Apple Configurator-enheter** och välj sedan **Tilldela profil**.
4. Välj den **nya profil** som du vill tilldela under **Tilldela profil** och välj sedan **Tilldela**.

#### <a name="assign-from-profiles"></a>Tilldela från profiler
1. I Intune på Azure-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Välj **AC profiler** och välj den profil som du vill tilldela till serienummer.
3. Välj **Tilldelade enheter** i profilen och välj sedan **Tilldela**.
4. Filtrera för att hitta enhetsserienummer som du vill tilldela till profilen, välj enheterna och välj sedan **Tilldela**.

### <a name="export-the-profile"></a>Exportera profilen
När du har skapat profilen och tilldelat serienummer måste du exportera profilen från Intune som en URL. Du kan sedan importera den till Apple Configurator på en Mac för distribution till enheter.

1. Välj **Enhetsregistrering** > **Apple-registrering** > **AC-profiler** på Azure-portalen i Intune och välj sedan den profil som ska exporteras.
2. Välj **Exportera profil** i profilen.

  ![Skärmbild av Exportera profil för alternativet Registrering av installationsassistent där profilens webbadress är markerad](./media/ios-apple-configurator-expor-sat.png)
3. Kopiera profil-URL. Du kan sedan lägga till den i Apple Configurator senare för att definiera den Intune-profil som används av iOS-enheter.

  Därefter importerar du den här profilen till Apple Configurator, genom följande procedur som definierar den Intune-profil som används av iOS-enheter.

### <a name="enroll-devices-with-setup-assistant"></a>Registrera enheter med installationsassistenten

1.  På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.
  > [!WARNING]
  > Enheterna återställs till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.

2. I rutan för **inställningar** väljer du **Servrar** och plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.
3. Ange **värdnamn eller URL** och **registrerings-URL** för MDM-servern under installationsassistentens registrering för iOS-enheter med Microsoft Intune. För registrerings-URL:en anger du URL:en för registreringsprofilen som exporterats från Intune. Välj **Nästa**.  

  Du kan ignorera en varning som anger att server-URL:en inte har verifierats. Fortsätt genom att välja **Nästa** tills guiden har slutförts.
4.  Anslut iOS-mobilenheterna till Mac-datorn med en USB-adapter.
5.  Välj de iOS-enheter som du vill hantera och välj sedan **Förbered**. I fönstret **Förbered iOS-enhet** väljer du först **Manuellt** och sedan **Nästa**.
6. I fönstret **Registrera i MDM-server** väljer du först servernamnet som du skapat och sedan **Nästa**.
7. I fönstret **Övervaka enheter** väljer du först övervakningsnivån och sedan **Nästa**.
8. I fönstret **Skapa en organisation** väljer du **Organisation** eller skapar en ny organisation och väljer sedan **Nästa**.
9. I fönstret **Konfigurera installationsassistenten för iOS** väljer du stegen som visas för användaren och väljer sedan **Förbered**. Autentisera för att uppdatera förtroendeinställningarna om du uppmanas att göra det.  
10. När iOS-enheten har slutfört förberedelserna kopplar du från USB-kabeln.  

### <a name="distribute-devices"></a>Distribuera enheter
Enheterna är nu klara för företagets registrering. Stäng av enheterna och distribuera dem till användarna. Installationsassistenten startar när användarna sätter på sina enheter.

När användarna får sina enheter måste de slutföra installationsassistenten. Enheter som har konfigurerats med användartillhörighet kan installera och köra företagsportalappen för att ladda ned appar och hantera enheter.

## <a name="direct-enrollment"></a>Direktregistrering
När du registrerar iOS-enheter direkt med Apple Configurator så kan du registrera en enhet utan att hämta enhetens serienummer. Du kan också namnge enheten i identifieringssyfte innan Intune samlar in enhetens namn under registreringen. Företagsportalappen stöds inte för direktregistrerade enheter. Den här metoden gör inte någon fabriksåterställning av enheten.

Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, kan inte installeras.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportera profilen som .mobileconfig för iOS-enheter
1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Ladda ned profil** under **Exportera profil** för att ladda ned registreringsprofilen.

  ![Skärmbild av Exportera profil för alternativet Registrering av installationsassistent där profilens webbadress är markerad](./media/ios-apple-configurator-expor-de.png)

4. Överför filen till en Mac-dator som kör [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) för att skicka den direkt som en hanteringsprofil till iOS-enheter.
5. Förbered enheten med Apple Configurator med hjälp av följande steg.
  1. Öppna Apple Configurator 2.0 på en Mac-dator.
  2. Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng Foton, iTunes och andra appar som öppnas för enheten när enheten identifieras.
  3. I Apple Configurator väljer du den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **Profiler**.

    ![Skärmbild av Exportera profil för alternativet Registrering av installationsassistent där profilens webbadress är markerad](./media/ios-apple-configurator-add-profile.png)

  4. Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten. Om enheten är obevakad kräver installationen godkännande på enheten.
6. Installera profilen på iOS-enheten på följande sätt. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas. Om registreringen kräver appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributionen kräver att du har ett Apple-ID för App Store.
   1. Lås upp iOS-enheten.
   2. Välj **Installera** för **Hanteringsprofil** i dialogrutan **Installera profil**.
   3. Ange enhetens lösenord eller Apple-ID om så behövs.
   4. Acceptera **varningen** och välj **Installera**.
   5. Acceptera **fjärrvarningen** och välj **Förtroende**.
   6. När rutan **Profilen har installerats** bekräftar att profilen har installerats väljer du **Klar**.

7. Öppna **Inställningar** på iOS-enheten och gå till **Allmänt** > **Enhetshantering** > **Hanteringsprofil**. Bekräfta att profilinstallationen visas och kontrollera iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

8. Distribuera enheter. Nu är iOS-enheten registrerad i Intune och hanteras.
