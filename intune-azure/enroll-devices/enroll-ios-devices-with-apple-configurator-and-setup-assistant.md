---
title: "Registrera iOS-enheter –Apple Configurator– installationsassistent | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med installationsassistenten."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 888e7b7af7dcca4154f67a1de781eb7908d9a187
ms.lasthandoff: 02/15/2017


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Registrera iOS-enheter med Apple Configurator och installationsassistenten 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) på en Mac-dator. Den här processen återställer enheten till fabriksinställningarna, förbereder den för att köra installationsassistenten och installerar företagets principer för enhetens nya användare.

>[!NOTE]
>Den här registreringsmetoden kan inte användas med metoden [hanterare av enhetsregistrering](enroll-devices-using-device-enrollment-manager.md).

Med Apple Configurator kan du återställa en iOS-enhet till fabriksinställningarna och förbereda den för konfiguration för enhetens nya användare. Den här metoden kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning och förutsätter att du använder Apple Configurator 2.0. De flesta scenarier kräver att principen som tillämpas på iOS-enheten inkluderar användartillhörighet för att aktivera appen Intune-företagsportal.

Andra metoder för att registrera iOS-enheter beskrivs i [Välj hur du vill registrera iOS-enheter i Intune](choose-ios-enrollment-method.md).

## <a name="prerequisites"></a>Förutsättningar

Uppfyll följande krav innan du konfigurerar registrering av iOS-enheter:

- [Konfigurera domäner](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Ange MDM-utfärdare](set-mdm-authority.md)
- [Skapa grupper](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Konfigurera företagsportalen](/intune-azure/manage-apps/company-portal-app.md)
- Tilldela användarlicenser i [Office 365-portalen](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Hämta ett Apple MDM-pushcertifikat](get-an-apple-mdm-push-certificate.md)
- Kontrollera att du har fysisk åtkomst till iOS-enheter
- Ta reda på enhetens serienummer (se [Hämta ett iOS-serienummer](https://support.apple.com//HT204308))
- Ha USB-anslutningskablar tillgängligt
- Kontrollera att du har en Mac-dator med [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) installerat
- [Lägg till Apple Configurator-serienummer](add-apple-configurator-serial-numbers.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>Skapa en Apple Configurator-profil för enheter

En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter. Följande steg visar hur du skapar en enhetsregistreringsprofil för iOS-enheter som registrerats med hjälp av Apple Configurator.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Apple-registrering**.

3. Välj **AC-profiler** under **Hantera Apple Configurator-registreringsinställningar**.

4. Välj **Skapa** på bladet **Apple Configurator-registreringsprofiler**.

5. Ange ett namn och en beskrivning för profilen på bladet **Skapa registreringsprofil**.

6. Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

   - **Registrera med användartillhörighet** – Enheten måste registreras med en användare under den ursprungliga installationen och kan sedan beviljas åtkomst till företagets data och e-post. Användartillhörighet ska konfigureras för DEP-hanterade enheter som tillhör användare och som måste använda företagsportalen för tjänster som appinstallation.

   - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

7. Spara profilen genom att välja **Skapa**.

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Tilldela serienummer till en Apple Configurator-profil

När du har skapat Apple Configurator-profiler kan du tilldela enhetsserienummer till profilerna. Om du vill kunna tilldela serienummer måste du först lägga till dem i Intune genom att följa stegen i [Lägg till Apple Configurator-serienummer](add-apple-configurator-serial-numbers.md).

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>Tilldela serienummer till Apple Configurator-profiler

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Från bladet **Apple Configurator-registreringsprofiler** väljer du den profil som du vill tilldela serienummer till.

3. I bladet som uppkallats med profilens namn väljer du **Serienummer** > **Tilldela**.

4. Välj de serienummer som du vill tilldela profilen och sedan knappen **Tilldela**.

## <a name="export-the-profile-to-ios-devices"></a>Exportera profilen till iOS-enheter

När du har skapat profilen och tilldelat serienummer måste du exportera profilen från Intune, antingen som en URL eller som en fil i det format som beskrivs nedan. Sedan importerar du profilen manuellt till Apple Configurator-programmet på en Mac, och Apple Configurator-programmet distribuerar den därefter till enheterna.

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>Exportera en profil med hjälp av registrering med installationsassistenten

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj profilen som ska exporteras på bladet **Apple Configurator-registreringsprofiler**.

3. Välj **Exportera profil** på bladet för profilen.

4. Kopiera profilens webbadress till [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) med iOS-enheten ansluten. Du kommer att överföra den i Apple Configurator senare för att definiera den Intune-profil som används av iOS-enheter.

  För stöd för Apple Configurator 2 måste 2.0-profilens URL redigeras. Det gör du genom att ersätta den här koden:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Med den här koden:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Du kommer att överföra den här profil-URL:en till Apples enhetsregistreringsprogramtjänst med hjälp av Apple Configurator genom följande procedur för att definiera den Intune-profil som används av iOS-enheter.

5. Överför den här profil-URL:en till Apples enhetsregistreringsprogramtjänst för att definiera den Intune-profil som används av iOS-enheter.


    1.  På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.

         > [!WARNING]
         > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.

    2. I fönstret **inställningar** väljer du **Servrar** och väljer plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.

    3. Ange **namnet** och **registrerings-URL:en** för MDM-servern från steg 6 under Registrering av installationsassistent för iOS-enheter med Microsoft Intune. För registrerings-URL:en anger du URL:en för registreringsprofilen som exporterats från Intune. Välj **Nästa**.  

       Du kan ignorera en varning som anger att server-URL:en inte har verifierats. Fortsätt genom att välja **Nästa** tills guiden har slutförts.

    4.  Anslut iOS-mobilenheterna till Mac-datorn med en USB-adapter.

        > [!WARNING]
        > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du startar Installationsassistenten.

    5.  Välj **Förbereda**. I fönstret **Förbered iOS-enhet** väljer du först **Manuellt** och sedan **Nästa**.

    6. I fönstret **Registrera i MDM-server** väljer du först servernamnet som du skapat och sedan **Nästa**.

    7. I fönstret **Övervaka enheter** väljer du först övervakningsnivån och sedan **Nästa**.

    8. I fönstret **Skapa en organisation** väljer du **Organisation** eller skapar en ny organisation och väljer sedan **Nästa**.

    9. I fönstret **Konfigurera installationsassistenten för iOS** väljer du stegen som visas för användaren och väljer sedan **Förbered**. Autentisera för att uppdatera förtroendeinställningarna om du uppmanas att göra det.  

    10. När iOS-enheten har slutfört förberedelserna kopplar du från USB-kabeln.  

6.  **Distribuera enheter**.
    Enheterna är nu klara för företagets registrering. Stäng av enheterna och distribuera dem till användarna. När användarna sätter på sina enheter startar Installationsassistenten.

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Hur användare installerar och använder företagsportalen på sina enheter

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ytterligare några steg, vilka beskrivs nedan, för att kunna slutföra installationen och installera företagsportalappen.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Hur en användare registrerar företagsägda iOS-enheter med användartillhörighet

1. När användaren startar enheten uppmanas han eller hon att slutföra arbetet med installationsassistenten. Under installationen uppmanas användarna att ange sina autentiseringsuppgifter. Användaren måste använda de autentiseringsuppgifter (unikt namn eller UPN) som är associerade med prenumerationen i Intune.

2. Under installationen uppmanas användarna att ange ett Apple-ID. Användaren måste ange ett Apple-ID för att företagsportalen ska få installeras på enheten. Användaren kan även ange ID från iOS-inställningsmenyn när installationen har slutförts.

3. När installationen har slutförts måste företagsportalappen installeras på iOS-enheten från App Store.

4. Användaren kan nu logga in på företagsportalen med det UPN som angavs när enheten konfigurerades.

5. Efter inloggningen uppmanas användaren att registrera enheten. Det första steget är att identifiera enheten. I appen visas en lista över iOS-enheter som redan är företagsregistrerade och har tilldelats till användarens Intune-konto. Användaren ska välja motsvarande enhet. Om enheten inte är företagsregistrerad måste användaren välja ny enhet och fortsätta med standardregistreringsflödet.

6. På nästa skärm måste användaren bekräfta den nya enhetens serienummer. Användare kan trycka på länken Bekräfta serienumret och starta inställningsappen för att verifiera serienumret. Sedan måste användaren ange de fyra sista tecknen i serienumret i företagsportalappen.

    I det här steget verifieras att enheten är den företagsenhet som har registrerats i Intune. Om serienumret på enheten inte matchar har fel enhet valts. Användaren bör gå tillbaka till föregående sida och välja en annan enhet.

7. När serienumret har verifierats omdirigeras användaren från företagsportalappen till företagsportalens webbplats för att slutföra registreringen. På webbplatsen uppmanas sedan användaren att återgå till appen.

Registreringen är klar, och användaren kan nu använda den här enheten med fullständiga funktioner.

