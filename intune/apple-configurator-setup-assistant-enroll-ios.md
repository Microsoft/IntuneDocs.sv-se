---
title: "Registrera iOS-enheter – Apple Configurator – installationsassistent"
titleSuffix: Intune on Azure
description: "Läs hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med installationsassistenten.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Registrera iOS-enheter med Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) på en Mac-dator. Registrering med Apple Configurator kräver att du USB-ansluter varje iOS-enhet till en Mac-dator för att konfigurera företagsregistrering. Du kan registrera enheter i Intune med Apple Configurator på två sätt:
- **Registrering med installationsassistenten** – fabriksåterställer enheten, förbereder den att köra installationsassistenten och installerar företagets principer för enhetens nya användare. De flesta scenarier kräver att principen som tillämpas på iOS-enheten inkluderar användartillhörighet för att aktivera appen Intune-företagsportal.
- **Direkt registrering** – fabriksåterställer inte enheten och registrerar den med en fördefinierad princip. Den här metoden är för enheter **utan användartillhörighet**.

>[!NOTE]
>Den här registreringsmetoden kan inte användas med metoden [hanterare av enhetsregistrering](device-enrollment-manager-enroll.md).

Andra metoder för att registrera iOS-enheter beskrivs i [Välj hur du vill registrera iOS-enheter i Intune](enrollment-method-choose-ios.md).

## <a name="prerequisites"></a>Förutsättningar

Uppfyll följande krav innan du konfigurerar registrering av iOS-enheter:

- [Ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md)
- Fysisk åtkomst till iOS-enheter
- Enheternas serienummer (se [så här hämtar du ett iOS-serienummer](https://support.apple.com//HT204308))
- USB-anslutningskablar
- Mac-dator med [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Lägg till Apple Configurator-serienummer](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>Registrering med installationsassistenten

### <a name="create-an-apple-configurator-profile-for-devices"></a>Skapa en Apple Configurator-profil för enheter

En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter. Följande steg visar hur du skapar en enhetsregistreringsprofil för iOS-enheter som registrerats med hjälp av Apple Configurator.

1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Välj **AC-profiler** under **Hantera Apple Configurator-registreringsinställningar**.
3. Välj **Skapa** på bladet **Apple Configurator-registreringsprofiler**.
4. Ange ett namn och en beskrivning för profilen på bladet **Skapa registreringsprofil**.
5. Ange om enheter med den här profilen ska registreras med eller utan användartillhörighet under **Användartillhörighet**.

   - **Registrera med användartillhörighet** – Enheten måste registreras med en användare under den ursprungliga installationen och kan sedan beviljas åtkomst till företagets data och e-post. Användartillhörighet ska konfigureras för hanterade enheter som tillhör användare och som måste använda företagsportalen för tjänster som t.ex. appinstallation.
   - **Registrera utan användartillhörighet** – Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

6. Spara profilen genom att välja **Skapa**.

### <a name="add-apple-configurator-serial-numbers"></a>Lägg till Apple Configurator-serienummer

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Följ de här stegen när du ska lägga till serienummer till Intune när du vill [registrera företagsägda iOS-enheter med hjälp av Apple Configurator med installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md). Du kan lägga till serienumren ett i taget eller ladda upp en fil med kommateckenavgränsade fält (CSV) med serienummer. När du har lagt till serienumren tilldelar du dem en profil. Profilen innehåller specifika hanteringsinställningar som du tillämpar på enheter.

Andra metoder för att registrera iOS-enheter beskrivs i [Välj hur du vill registrera iOS-enheter i Intune](enrollment-method-choose-ios.md).

**Lägga till Apple Configurator-serienummer till Intune**

1. Skapa en fil med kommaseparerade värden (CSV) med två kolumner och ingen rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 500. Om du öppnar CSV-listan i en textredigerare ser den ut ungefär så här:

    F7TLWCLBX196, enhetsinformation</br>
    DLXQPCWVGHMJ, enhetsinformation

2. I Azure-portalen, väljer du **registrera enheter** och därefter **Apple-registrering**.
3. Välj **Apple Configurator-serienummer** under **Hantera Apple Configurator-registreringsinställningar**.
4. Välj **Lägg till** på bladet **Apple Configurator-serienummer**.
5. Välj den profil som ska tillämpas på de serienummer som du importerar på bladet **Lägg till serienummer**. Om du importerar en fil med ny information som kommer att skriva över befintlig information, så välj Skriv över information för befintliga identifierare. Då ersätts den befintliga informationen av den nya.
6. Navigera till CSV-filen med serienummer och välj **Lägg till**.

### <a name="assign-a-profile-to-specific-serial-numbers"></a>Tilldela specifika serienummer en profil

Med Intune kan du tilldela profiler från två olika platser i Azure-portalen. Du kan tilldela efter Apple Configurator-profiler eller efter enheter.

#### <a name="assign-by-devices"></a>Tilldela efter enheter
1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
3. I bladet **Apple Configurator-enheter**, väljer du de serienummer som du vill tilldela en profil till och därefter väljer du **Tilldela profil**.
4. Välj den profil som du vill tilldela på bladet **Tilldela profil** och välj sedan **Tilldela**.

#### <a name="assign-by-profiles"></a>Tilldela efter profiler
1. I Intune-portalen väljer du **Enhetsregistrering** och därefter **Apple-registrering**.
2. Välj **AC profiler** och välj den profil som du vill tilldela serienummer.
3. I bladet som uppkallats med profilens namn väljer du **Serienummer** > **Tilldela**.
4. Välj de serienummer som du vill tilldela profilen och sedan knappen **Tilldela**.

### <a name="export-the-profile-to-ios-devices"></a>Exportera profilen till iOS-enheter
När du har skapat profilen och tilldelat serienummer måste du exportera profilen från Intune, antingen som en URL eller som en fil i det format som beskrivs nedan. Sedan importerar du profilen manuellt till Apple Configurator-programmet på en Mac, och Apple Configurator-programmet distribuerar den därefter till enheterna.

1. I Intune-portalen, väljer du bladet **Apple Configurator-registreringsprofiler** och därefter den profil du vill exportera.
2. Välj **Exportera profil** på bladet för profilen.
3. Kopiera profilens webbadress till [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) med iOS-enheten ansluten. Du kommer att överföra den i Apple Configurator senare för att definiera den Intune-profil som används av iOS-enheter.

  Du kommer att överföra den här profil-URL:en till Apple-tjänsten med hjälp av Apple Configurator, genom följande procedur som definierar den Intune-profil som används av iOS-enheter.
4. Överför den här profil-URL:en till Apple-tjänsten med Apple Configurator för att definiera den Intune-profil som används av iOS-enheter.
 1.  På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.
  > [!WARNING]
  > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.
  2. I rutan för **inställningar** väljer du **Servrar** och plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.
  3. Ange **värdnamn eller URL** och **registrerings-URL** för MDM-servern under installationsassistentens registrering för iOS-enheter med Microsoft Intune. För registrerings-URL:en anger du URL:en för registreringsprofilen som exporterats från Intune. Välj **Nästa**.  

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

## <a name="direct-enrollment"></a>Direktregistrering
När du registrerar iOS-enheter direkt med Apple Configurator så kan du registrera en enhet utan att hämta enhetens serienummer. Du kan också namnge enheten i identifieringssyfte innan Intune samlar in enhetens namn under registreringen. Företagsportalappen stöds inte för direktregistrerade enheter. Den här vägledningen förutsätter att du använder Apple Configurator 2.0 på en Mac-dator.

1. I Intune-portalen, väljer du **enhetsregistrering**, **Apple-registrering** och därefter **AC-profiler**.
2. Välj **Skapa** på bladet **Apple Configurator-registreringsprofiler**.
3. Ange ett namn och en beskrivning för profilen på bladet **Skapa registreringsprofil**.
4. Se till att enheten inte är kopplad till någon användare genom att välja **Registrera utan användartillhörighet** för **Användartillhörighet**. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.
5. Spara profilen genom att välja **Skapa**.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportera profilen som .mobileconfig för iOS-enheter

1. Ladda ned registreringsprofilen till [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) på bladet **Exportera profil** så att den skickas direkt som push-meddelande till en ansluten iOS-enhet. Den här metoden gör inte någon fabriksåterställning av enheten.
2. Förbered enheten med Apple Configurator med hjälp av följande steg.
  1. Öppna Apple Configurator 2.0 på en Mac-dator.
  2. Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng Foton, iTunes och andra appar som öppnas för enheten när enheten identifieras.
  3. I Apple Configurator väljer du den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **Profiler**.
  4. Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten. Om enheten är obevakad kräver installationen godkännande på enheten.
3. Installera profilen på iOS-enheten på följande sätt. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas. Om registreringen medför appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributioner kräver att du har ett Apple-ID för App Store.
   1. Lås upp iOS-enheten.
   2. Välj **Installera** för **Hanteringsprofil** i dialogrutan **Installera profil**.
   3. Ange enhetens lösenord eller Apple-ID om så behövs.
   4. Acceptera **varningen** och välj **Installera**.
   5. Acceptera **fjärrvarningen** och välj **Förtroende**.
   6. När rutan **Profilen har installerats** bekräftar att profilen har installerats väljer du **Klar**.

    4. Öppna **Inställningar** på iOS-enheten och gå till **Allmänt** > **Enhetshantering** > **Hanteringsprofil**. Bekräfta att profilinstallationen visas och kontrollera iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

    5. Distribuera enheter. Nu är iOS-enheten registrerad med Intune och hanteras.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Hur användare installerar och använder företagsportalen på sina enheter

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ytterligare några steg, vilka beskrivs nedan, för att kunna slutföra installationen och installera företagsportalappen.
