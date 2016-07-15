---
title: "Direktregistrering för iOS-enheter | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1b942c7e09e59de59e3e406b84a21a712c0e973a
ms.openlocfilehash: 8fea0f7f87972bc643bbb20348095e05f701287e


---

# Registrera iOS-enheter som använder Apple Configurator direkt
Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator. Den här processen fabriksåterställer inte enheten och registrerar enheten med en fördefinierad princip. Den här metoden gäller för enheter som **inte har någon användartillhörighet** och kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning. Företagsportalappen stöds inte för direktregistrerade enheter. Den här vägledningen förutsätter att du använder Apple Configurator 2.0 på en Mac-dator.

1.  **Skapa en profil för enheter** En enhets registreringsprofil definierar inställningarna som tillämpas på enheter. Om du inte redan har gjort det, skapar du en registreringsprofil för iOS-enheter som använder Apple Configurator.

    #### Så här skapar du en profil

    1.  I [Microsoft Intunes administrationskonsol](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsägda enheter** och väljer sedan **Lägg till...**.

        ![Skapa sida för mobilenhetsregistrering](../media/pol-sa-corp-enroll.png)

    2.  Ange information om enhetsprofilerna:

        -   **Namn** – Namnet på enhetens registreringsprofil. Inte synligt för användarna.

        -   **Beskrivning** – Beskrivning av enhetens registreringsprofil. Inte synligt för användarna.

        -   **Användaranknytning** – Anger hur enheterna registreras. Om du vill använda direktregistrering väljer du **Ingen användartillhörighet**.

        -   **Förtilldelning av enhetsgrupp** – Alla enheter som har distribuerat den här profilen hör ursprungligen till den här gruppen. Du kan tilldela enheter på nytt efter registreringen.

        >[!Important]
        >Grupptilldelningar flyttas från Intune till Azure Active Directory. [Läs mer](http://go.microsoft.com/fwlink/?LinkID=787064)
    3.  Välj **Spara profil** för att lägga till profilen.

5.  **Exportera en profil som .mobileconfig för att distribuera den till iOS-enheter** Välj den enhetsprofil som du skapat. Välj **Exportera...** i verktygsfältet. Välj **Hämta profil** och spara den nedladdade .mobileconfig-filen.

6.  **Flytta filen** Kopiera den nedladdade .mobileconfig-filen till en Mac-dator.
    > [!NOTE]
    > Registreringsprofilens URL är giltig i två veckor från tidpunkten för exporten. Efter två veckor måste du exportera en ny registreringsprofils-URL för att kunna registrera iOS-enheter med installationsassistenten.
7.  **Förbered enheten med Apple Configurator** iOS-enheter är anslutna till Mac-datorn och registreras för hantering av mobila enheter.

    1.  På en Mac-dator startar du **Apple Configurator 2.0**.

    2.  Anslut iOS-enheten till Mac-datorn med en USB-kabel. Stäng **Foton**, **iTunes** och andra appar som öppnas för enheten när enheten identifieras.

    3.  I Apple Configurator klickar du på den anslutna iOS-enheten och väljer sedan knappen **Lägg till**. Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan. Välj **profiler**.

    4.  Använd filväljaren och välj den .mobileconfig-fil som du exporterade från Intune och välj sedan **Lägg till**. Profilen läggs till för enheten.  Om enheten är **obevakad** kräver installationen godkännande på enheten.

8.  **Installera profilen** Du är redo att installera profilen på iOS-enheten. Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas.  Om registreringen medför appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributioner kräver att du har ett Apple-ID för App Store.

    ###### Slutför profilgodkännande för obevakade iOS-enheter

    1.  Lås upp iOS-enheten.

    2.  Tryck på **Installera** i dialogrutan **Installera profil** för **Hanteringsprofil**.

    3.  Ange **enhetens lösenord** eller **Apple-ID** om det behövs.

    4.  Godkänn **varningen** och tryck på **Installera**.

    5.  Godkänn **fjärrvarningen** och tryck på **Förtroende**.

    6.  När rutan **Profilen har installerats** bekräftar att profilen har **installerats** väljer du **Klar**.

9. **Verifiera profil**
    På iOS-enheten startar du **Inställningar** och går till **Allmänt** &gt; **Enhetshantering** &gt; **Hanteringsprofil** &gt; och bekräftar att profilinstallationen visas, kontrollerar iOS-principbegränsningarna och installerade appar. Det kan ta upp till tio minuter innan principbegränsningar och appar visas på enheten.

10. **Distribuera enheter** Nu är iOS-enheten registrerad med Intune och hanteras.


### Se även
[Dags att registrera enheter](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jul16_HO1-->


