---
title: Registrera iOS-enheter med installationsassistenten | Microsoft Intune
description: "Registrera företagsägda iOS-enheter med hjälp av Apple Configurator-verktyget för att återställa enheten till fabriksinställningarna och förbereda den för Installationsassistenten."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: ea6a4732e747dccf9c42732c06bd1b8cdf20e91f


---

# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>Registrera iOS-enheter med Apple Configurator med hjälp av Installationsassistenten
Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator. Den här processen återställer enheten till fabriksinställningarna och förbereder den för Installationsassistenten genom att installera företagets principer för enhetens nya användare.

## <a name="setup-assistant-enrollment-for-ios-devices-with-microsoft-intune"></a>Registrering med installationsassistenten för iOS-enheter med Microsoft Intune
Med Apple Configurator kan du återställa en iOS-enhet till fabriksinställningarna och förbereda den för konfiguration för enhetens nya användare. Den här metoden kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning och förutsätter att du använder Apple Configurator 2.0. De flesta scenarier kräver att principen som tillämpas på iOS-enheten inkluderar **användartillhörighet** för att aktivera appen Intune-företagsportal.

**Krav**
* [Aktivera iOS-registrering](set-up-ios-and-mac-management-with-microsoft-intune.md) genom att installera ett APN-certifikat
* Fysisk åtkomst till iOS-enheter&mdash; måste återställas till fabriksinställningarna utan lösenordsskydd
* Enhetsserienummer – se [Hämta ett iOS-serienummer](https://support.apple.com/en-us/HT204308)
* USB-anslutningskablar
* En Mac-dator med [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


1.  **Skapa grupper med mobila enheter** (valfritt).
    Om ditt företag kräver mobila enhetsgrupper för att hantera enheter skapar du de grupperna. Mer information finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

2.  **Skapa en profil för enheter**.
    En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter. Följande steg visar hur du skapar en enhetsregistreringsprofil för iOS-enheter som registrerats med hjälp av Apple Configurator.

    1.  I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsägda enheter** och väljer sedan **Lägg till**.
    ![Skapa profil för mobilenhetsregistrering](../media/pol-sa-corp-enroll.png)

    2.  Ange information om enhetsprofilerna:

        -   **Namn**: Namnet på enhetsregistreringsprofilen (visas inte för användarna).

        -   **Beskrivning**: En beskrivning av enhetsregistreringsprofilen (visas inte för användarna).

        -   **Registreringsinformation**: Anger hur enheterna registreras.

            -   **Fråga efter användartillhörighet**: Enheten måste vara kopplad till en användare under den ursprungliga installationen och kan sedan beviljas samma åtkomst till företagets data och e-post. **Användartillhörighet** bör konfigureras för DEP-hanterade enheter som tillhör användare och måste använda företagsportalen för tjänster som appinstallation.

            -   **Ingen användartillhörighet**: Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

        -   **Förhandstilldelning av enhetsgrupp**: Alla enheter som har distribuerats med den här profilen hör ursprungligen till den här gruppen. Du kan tilldela enheter på nytt efter registreringen.

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

        -  **Enhetsregistreringsprogram**: Apples enhetsregistreringsprogram (Device Enrollment Program) kan inte användas med registrering via Installationsassistenten. Se till att växlingsknappen har inställningen **Av**.

    3.  Välj **Spara profil** för att lägga till profilen.

3.  **Lägg till iOS-enheter som ska registreras med installationsassistenten**.
    I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Grupper** &gt; **Alla enheter** &gt; **Alla företagsägda enheter** &gt; **Alla enheter** och väljer **Lägg till enheter**. Du kan lägga till enheter på två sätt:

    ![Dialogrutan Lägg till enheter](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **Överför en CSV-fil som innehåller serienummer**: Skapa en kommaavgränsad lista med två kolumner utan rubrik som är begränsad till 5 000 enheter eller 5 MB per CSV-fil.

        |||
        |-|-|
        |&lt;Serienr 1&gt;|&lt;Information om enhet nr 1&gt;|
        |&lt;Serienr 2&gt;|&lt;Information om enhet nr 2&gt;|
        När den öppnas i en textredigerare visas den här CSV-filen som:

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **Lägg till enhetsinformation manuellt**&mdash;Ange serienummer och enhetsinformation för upp till 15 enheter.

    > [!NOTE]
    > Om du senare måste ta bort företagsägda enheter från Intune-hanteringen kanske du behöver ta bort enhetens serienummer från Intune i enhetsgruppen **Efter iOS-serienummer** under **Företagets förregistrerade enheter** för att kunna inaktivera enhetsregistreringen. Om Intune utför en katastrofåterställning vid eller runt den tidpunkt då du tar bort serienummer måste du kontrollera att endast aktiva enheters serienummer finns i gruppen.

    Välj **Nästa**.

4.  **Välj enheter som ska registreras**.
    Bekräfta vilka enheter som ska registreras. Det går inte att importera serienummer som redan har registrerats eller som registrerats på annat sätt. Fortsätt genom att välja **Nästa** .

5.  **Tilldela profil**.
    Ange profilen som ska tilldelas till enheter som lagts till i listan över tillgängliga profiler, granska **profilregistreringsinformationen** och välj **Slutför**. Manuellt tillagda enheter kan associeras med valfri registreringsprofil.

6.  **Exportera en profil som ska distribueras till iOS-enheter**.
    I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsenhetsregistrering** och väljer den enhetsprofil som ska distribueras till mobilenheter. Välj **Exportera** i Aktivitetsfältet. Kopiera och spara **Profil-URL**. Du kommer att överföra den i Apple Configurator senare för att definiera den Intune-profil som används av iOS-enheter.
    För stöd för Apple Configurator 2 måste 2.0-profilens URL redigeras. Det gör du genom att ersätta den här koden:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Med den här koden:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Du kommer att överföra den här profil-URL:en till Apples enhetsregistreringsprogramtjänst med hjälp av Apple Configurator genom följande procedur för att definiera den Intune-profil som används av iOS-enheter.



7.  **Förbered enheten med Apple Configurator**.
    iOS-enheter är anslutna till Mac-datorn och registreras för hantering av mobila enheter.

    1.  På en Mac-dator öppnar du **Apple Configurator 2**. Välj **Apple Configurator 2** i menyfältet och välj sedan **Inställningar**.

         > [!WARNING]
         > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du ansluter den.

    2. I inställningsrutan väljer du **Servrar** och väljer plustecknet (+) för att starta MDM-serverguiden. Välj **Nästa**.

    3. Ange **namnet** och **registrerings-URL:en** för MDM-servern från steg 6 under Registrering av installationsassistent för iOS-enheter med Microsoft Intune. För registrerings-URL:en anger du URL:en för registreringsprofilen som exporterats från Intune. Välj **Nästa**.  

       Du kan ignorera en varning som anger att server-URL:en inte har verifierats. Fortsätt genom att välja **Nästa** tills guiden har slutförts.

    4.  Anslut iOS-mobilenheterna till Mac-datorn med en USB-adapter.

        > [!WARNING]
        > Enheterna kommer att återställas till fabrikskonfigurationerna vid registreringen. Vi rekommenderar att du återställer enheten och sätter på den. Enheten bör visa **Hello**-skärmen när du startar Installationsassistenten.

    5.  Välj **Förbereda**. I fönstret Förbered iOS-enhet väljer du först **Manuellt** och sedan **Nästa**.

    6. I fönstret Registrera i MDM-server väljer du först servernamnet som du skapat och sedan **Nästa**.

    7. I fönstret Övervaka enheter väljer du först övervakningsnivån och sedan **Nästa**.

    8. I fönstret Skapa en organisation väljer du **Organisation** eller skapar en ny organisation och väljer sedan **Nästa**.

    9. I fönstret Konfigurera installationsassistenten för iOS väljer du stegen som visas för användaren och väljer sedan **Förbered**. Autentisera för att uppdatera förtroendeinställningarna om du uppmanas att göra det.  

    10. När iOS-enheten har slutfört förberedelserna kopplar du från USB-kabeln.  

8.  **Distribuera enheter**.
    Enheterna är nu klara för företagets registrering. Stäng av enheterna och distribuera dem till användarna. När användarna sätter på sina enheter startar Installationsassistenten.



### <a name="see-also"></a>Se även
[Förutsättningar för att registrera enheter](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO2-->


