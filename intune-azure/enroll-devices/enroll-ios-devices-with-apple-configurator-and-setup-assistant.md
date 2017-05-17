---
title: "Registrera iOS-enheter – Apple Configurator – installationsassistent"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med installationsassistenten."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 90222b10832fd8251ad897348eeebed5b3d1e552
ms.openlocfilehash: ababc7f8238079ce02a587e1829e8eedfb117937
ms.contentlocale: sv-se
ms.lasthandoff: 05/11/2017


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

   - **Registrera med användartillhörighet** – Enheten måste registreras med en användare under den ursprungliga installationen och kan sedan beviljas åtkomst till företagets data och e-post. Användartillhörighet ska konfigureras för hanterade enheter som tillhör användare och som måste använda företagsportalen för tjänster som t.ex. appinstallation.

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

  Du kommer att överföra den här profil-URL:en till Apple-tjänsten med hjälp av Apple Configurator, genom följande procedur som definierar den Intune-profil som används av iOS-enheter.

5. Överför den här profil-URL:en till Apple-tjänsten med Apple Configurator för att definiera den Intune-profil som används av iOS-enheter.
 1.  På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.
  > [!WARNING]
  > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.

  2. I rutan för **inställningar** väljer du **Servrar** och plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.

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

    Se [Informera dina slutanvändare om Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune). Du kan också dirigera dina slutanvändare till [Använda din iOS- eller macOS-enhet med Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) 

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>Hur användare installerar och använder företagsportalen på sina enheter

Enheter som har konfigurerats med mappning mellan användare kan installera och köra företagsportalsappen och ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ytterligare några steg, vilka beskrivs nedan, för att kunna slutföra installationen och installera företagsportalappen.

