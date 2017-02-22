---
title: "Registrera iOS-enheter med Apple Configurator och direktregistrering | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om hur du använder Apple Configurator för att registrera företagsägda iOS-enheter med direktregistrering."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 521a37044d6721fe905db7740329688ba2c24b35
ms.openlocfilehash: f6770556e6ee4e6a6fa1173c8c65c7e54d159016


---

# <a name="enroll-ios-devices-with-apple-configurator-and-direct-enrollment"></a>Registrera iOS-enheter med Apple Configurator och direktregistrering 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) på en Mac-dator. Den här processen fabriksåterställer inte enheten och registrerar enheten med en fördefinierad princip. Den här metoden gäller för enheter som **inte har någon användartillhörighet** och kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning.

>[!NOTE]
>Den här registreringsmetoden kan inte användas med metoden [hanterare av enhetsregistrering](enroll-devices-using-device-enrollment-manager.md).

När du registrerar iOS-enheter direkt kan du registrera dem utan att hämta enhetens serienummer. Du kan också namnge enheten i identifieringssyfte innan Intune samlar in enhetens namn under registreringen. Företagsportalappen stöds inte för direktregistrerade enheter. Den här vägledningen förutsätter att du använder Apple Configurator 2.0 på en Mac-dator.

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

## <a name="create-an-apple-configurator-profile-for-devices"></a>Skapa en Apple Configurator-profil för enheter

En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter. Följande steg visar hur du skapar en enhetsregistreringsprofil för iOS-enheter som registrerats med hjälp av Apple Configurator.

1. Välj **Fler tjänster** i Azure-portalen, skriv **Intune** i textrutan och välj sedan **Övrigt** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Apple-registrering**.

3. Välj **AC-profiler** under **Hantera Apple Configurator-registreringsinställningar**.

4. Välj **Skapa** på bladet **Apple Configurator-registreringsprofiler**.

5. Ange ett namn och en beskrivning för profilen på bladet **Skapa registreringsprofil**.

6. Se till att enheten inte är kopplad till någon användare genom att välja **Registrera utan användartillhörighet** för **Användartillhörighet**. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

7. Spara profilen genom att välja **Skapa**.

## <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Exportera profilen som .mobileconfig för iOS-enheter

1. Ladda ned registreringsprofilen till [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) på bladet **Exportera profil** så att den skickas direkt som push-meddelande till en ansluten iOS-enhet. Den här metoden gör inte någon fabriksåterställning av enheten.

2. Förbered enheten med Apple Configurator med hjälp av följande steg.

   a. Öppna Apple Configurator 2.0 på en Mac-dator.

   b. Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng Foton, iTunes och andra appar som öppnas för enheten när enheten identifieras.

   c. I Apple Configurator väljer du den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **Profiler**.

   d. Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten. Om enheten är obevakad kräver installationen godkännande på enheten.

3. Installera profilen på iOS-enheten på följande sätt. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas. Om registreringen medför appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributioner kräver att du har ett Apple-ID för App Store.

   a. Lås upp iOS-enheten.

   b. Välj **Installera** för **Hanteringsprofil** i dialogrutan **Installera profil**.

   c. Ange enhetens lösenord eller Apple-ID om så behövs.

   d. Acceptera **varningen** och välj **Installera**.

   e. Acceptera **fjärrvarningen** och välj **Förtroende**.

   f. När rutan **Profilen har installerats** bekräftar att profilen har installerats väljer du **Klar**.

4. Öppna **Inställningar** på iOS-enheten och gå till **Allmänt** > **Enhetshantering** > **Hanteringsprofil**. Bekräfta att profilinstallationen visas och kontrollera iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

5. Distribuera enheter. Nu är iOS-enheten registrerad med Intune och hanteras.



<!--HONumber=Feb17_HO1-->

