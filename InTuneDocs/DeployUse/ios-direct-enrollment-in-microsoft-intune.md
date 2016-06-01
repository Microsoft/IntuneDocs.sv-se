---
# required metadata

title: Direktregistrering för iOS-enheter med Microsoft Intune | Microsoft Intune
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

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera iOS-enheter som använder Apple Configurator direkt
Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator. Den här processen fabriksåterställer inte enheten och registrerar enheten med en fördefinierad princip. Den här metoden gäller för enheter som **inte har någon användartillhörighet** och kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning. Företagsportalappen stöds inte för direktregistrerade enheter. Den här vägledningen förutsätter att du använder Apple Configurator 2.0 på en Mac-dator.

1.  Skapa en profil för enheter En enhets registreringsprofil definierar inställningarna som tillämpas på enheter.

    #### Om du inte redan har gjort det, skapar du en registreringsprofil för iOS-enheter som använder Apple Configurator.

    1.  Så här skapar du en profil

        ![I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsenhetsregistrering** och klickar sedan på **Lägg till...**](../media/pol-sa-corp-enroll.png)

    2.  Skapa sida för mobilenhetsregistrering

        -   Ange information om enhetsprofilerna: **Namn** – Namnet på enhetens registreringsprofil.

        -   Inte synligt för användarna. **Beskrivning** – Beskrivning av enhetens registreringsprofil.

        -   Inte synligt för användarna. **Användaranknytning** – Anger hur enheterna registreras.

        -   Om du vill använda direktregistrering väljer du **Ingen användartillhörighet** **Förtilldelning av enhetsgrupp** – Alla enheter som har distribuerat den här profilen hör ursprungligen till den här gruppen.

    3.  Du kan tilldela enheter på nytt efter registreringen.

2.  Klicka på **Spara profil** för att lägga till profilen.

    ![Lägg till iOS-enheter som ska registreras med Apple Configurator](../media/pol-SA-enroll-iOS-SetupAssistant.png)

      I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com) går du till **Grupper** &gt; **Alla enheter** &gt; **Förregistrerade företagsenheter** &gt; **Med iOS-serienummer** och klickar sedan på **Lägg till enheter...**

    -   iOS installationsassistent

        |||
        |-|-|
        |&lt;Du kan lägga till enheter på två sätt:&gt;|&lt;**Överför en CSV-fil som innehåller serienummer** – Skapa en kommaavgränsad lista med två kolumner utan rubrik som är begränsad till 5 000 enheter eller 5 MB per CSV-fil.&gt;|
        |&lt;Serienr 1&gt;|&lt;Information om enhet nr 1&gt;|
        Serienr 2

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   Information om enhet nr 2

    > [!NOTE]
    > CSV-filen när den visas i en textredigerare:  **Information om manuellt tillagd enhet** – Ange serienummer och enhetsinformation för upp till fem enheter och klicka på **Nästa**

3.  Om du senare måste ta bort företagsägda enheter från Intune-hanteringen måste du ta bort enhetens serienummer från Intune i gruppen **Företagsägda enheter** för att kunna inaktivera enhetsregistreringen. Om Intune utför en katastrofåterställning på eller runt den tid då serienumren togs bort, måste du kontrollera att endast aktiva enheters serienummer finns kvar i gruppen. Välj enheter som ska registreras

4.  Bekräfta vilka enheter som ska registreras. Det går inte att importera serienummer som redan har registrerats eller som registrerats på annat sätt.

5.  Fortsätt genom att klicka på **Nästa** . Tilldela profil Ange profilen som ska tilldelas till enheter som lagts till i listan över tillgängliga profiler, granska **Profilregistreringsinformation**och klickar på **Slutför**. Manuellt tillagda enheter kan tilldelas en registreringsprofil. Välj en profil som ska distribueras till iOS-enheter

6.  I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com) gå till **Princip** &gt; **Företagsenhetsregistrering**. Välj sedan den enhetsprofil som ska distribueras till mobila enheter.
    > [!NOTE]
    > Den här profilen bör vara samma profil som du tilldelade för distribution i föregående steg. Klicka på **Exportera**
7.  i verktygsfältet.

    1.  Klicka på **Hämta profil** och spara den hämtade MOBILECONFIG-filen.

    2.  Överför filen Kopiera den nedladdade MOBILECONFIG-filen till en Mac-dator.

    3.  Registreringsprofilens URL är giltig i två veckor från tidpunkten för exporten. Efter två veckor måste du exportera en ny registreringsprofils-URL för att kunna registrera iOS-enheter med installationsassistenten. Förbered enheten med Apple Configurator

    4.  iOS-enheter är anslutna till Mac-datorn och registreras för hantering av mobila enheter. På en Mac-dator startar du **Apple Configurator 2.0**  Anslut iOS-enheten till Mac-datorn med en USB-kabel.

8.  Stäng **Foton**, **iTunes** och andra appar som öppnas för enheten när enheten identifieras. I Apple Configurator klickar du på den anslutna iOS-enheten och klickar sedan på knappen **Lägg till**.  Alternativ som kan läggas till för enheten visas i den nedrullningsbara listan.

    ###### Klicka på **Profiler**

    1.  Använd filväljaren och välj den MOBILECONFIG-fil som du exporterade från Intune och klicka sedan på **Lägg till**.

    2.  Profilen läggs till för enheten.

    3.  Om enheten är **obevakad** kräver installationen godkännande på enheten.

    4.  Installera profilen

    5.  Du är redo att installera profilen på iOS-enheten.

    6.  Installationsassistenten måste ha slutförts på enheten och enheten måste vara redo att användas.

9. Om registreringen medför appdistributioner måste enheten ha ett konfigurerat Apple-ID eftersom appdistributioner kräver att du har ett Apple-ID för App Store. Slutför profilgodkännande för obevakade iOS-enheter

10. Lås upp iOS-enheten.


### Tryck på **Installera** i dialogrutan **Installera profil** för **Hanteringsprofil**
[Ange **enhetens lösenord** eller **Apple-ID** om det behövs.](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


