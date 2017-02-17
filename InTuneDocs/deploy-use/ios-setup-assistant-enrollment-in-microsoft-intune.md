---
title: Registrera iOS-enheter med installationsassistenten | Microsoft Docs
description: "Registrera företagsägda iOS-enheter med hjälp av Apple Configurator-verktyget för att återställa enheten till fabriksinställningarna och förbereda den för Installationsassistenten."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a2e840797c06322b9efc59438e0675e57b7cdb24
ms.openlocfilehash: facae5f49b52760dcea0653bd261e16e13e11bbf


---

# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>Registrera iOS-enheter med Apple Configurator med hjälp av Installationsassistenten

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune stöder registrering av företagsägda iOS-enheter med hjälp av [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) på en Mac-dator. Den här processen återställer enheten till fabriksinställningarna och förbereder den för Installationsassistenten genom att installera företagets principer för enhetens nya användare.

>[!NOTE]
>Den här registreringsmetoden kan inte användas med metoden [hanterare av enhetsregistrering](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

Med Apple Configurator kan du återställa en iOS-enhet till fabriksinställningarna och förbereda den för konfiguration för enhetens nya användare. Den här metoden kräver att du utför företagsregistreringen genom att ansluta iOS-enheten till en Mac-dator via en USB-anslutning och förutsätter att du använder Apple Configurator 2.0. De flesta scenarier kräver att principen som tillämpas på iOS-enheten inkluderar **användartillhörighet** för att aktivera appen Intune-företagsportal.

## <a name="prerequisites-for-enrolling-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Förutsättningar för att registrera iOS-enheter med Apple Configurator med installationsassistenten

- [Installera ett APNs-certifikat](set-up-ios-and-mac-management-with-microsoft-intune.md)

- Se till att du har fysisk åtkomst till iOS-enheter&mdash;enheter måste återställas till fabriksinställningarna utan lösenordsskydd

- Hämta enhetsserienummer&mdash; – se [Hämta ett iOS-serienummer](https://support.apple.com/en-us/HT204308)

- Ha USB-anslutningskablar tillgängligt

- Ha en Mac-dator med [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)


## <a name="steps-to-enroll-ios-devices-by-using-apple-configurator-with-setup-assistant"></a>Anvisningar för att registrera iOS-enheter med Apple Configurator med hjälp av installationsassistenten

Följande steg beskriver hur du kan registrera iOS-enheter från den första dagen med hjälp av Apple Configurator med installationsassistenten. När enheter läggs till och tas bort från din organisation kommer du troligen att upprepa några av de här stegen, som att lägga till eller ta bort serienummer enligt beskrivningen nedan.

### <a name="create-mobile-device-groups-optional"></a>Skapa grupper med mobila enheter (valfritt)

Om ditt företag kräver mobila enhetsgrupper för att hantera enheter kan du välja att skapa de grupperna. Mer information finns i [Använda grupper för att hantera användare och enheter med Microsoft Intune](use-groups-to-manage-users-and-devices-with-microsoft-intune.md).

### <a name="create-a-profile-for-devices"></a>Skapa en profil för enheter

En enhets registreringsprofil definierar inställningarna som tillämpas på en grupp av enheter.

1. I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsägda enheter** och väljer sedan **Lägg till**.

  ![Skapa profil för mobilenhetsregistrering](../media/pol-sa-corp-enroll.png)

2. Ange information om enhetsprofilerna:

   -   **Namn**: Namnet på enhetsregistreringsprofilen (visas inte för användarna).

   -   **Beskrivning**: En beskrivning av enhetsregistreringsprofilen (visas inte för användarna).

   -   **Registreringsinformation**: Anger hur enheterna registreras.

       -   **Fråga efter användartillhörighet**: Enheten måste vara kopplad till en användare under den ursprungliga installationen och kan sedan beviljas samma åtkomst till företagets data och e-post. **Användartillhörighet** bör konfigureras för DEP-hanterade enheter som tillhör användare och måste använda företagsportalen för tjänster som appinstallation.

       -   **Ingen användartillhörighet**: Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

   -   **Förhandstilldelning av enhetsgrupp**: Alla enheter som har distribuerats med den här profilen hör ursprungligen till den här gruppen. Du kan tilldela enheter på nytt efter registreringen.

   > [!Important]
   > Grupptilldelningar flyttas från Intune till Azure Active Directory. När ditt Intune-konto får den tillämpliga uppdateringen kan du inte se alternativet **Tilldela enheter till följande grupp**. [Läs mer](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune#changes-to-intune-group-assignments).

   -  **Enhetsregistreringsprogram**: Apples enhetsregistreringsprogram (Device Enrollment Program) kan inte användas med registrering via Installationsassistenten. Se till att växlingsknappen har inställningen **Av**.

3.  Välj **Spara profil** för att lägga till profilen.

### <a name="add-ios-devices-to-enroll-with-setup-assistant"></a>Lägg till iOS-enheter som ska registreras med installationsassistenten

1. I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Grupper** &gt; **Alla enheter** &gt; **Alla företagsägda enheter** &gt; **Alla enheter** och väljer **Lägg till enheter**. 

   Du kan lägga till enheter på två sätt:

   ![Dialogrutan Lägg till enheter](../media/pol-SA-enroll-iOS-SetupAssistant.png)

   -  **Överför en CSV-fil som innehåller serienummer**: Skapa en kommaavgränsad lista med två kolumner utan rubrik som är begränsad till 5 000 enheter eller 5 MB per CSV-fil.

    |||
    |-|-|
    |&lt;Serienr 1&gt;|&lt;Information om enhet nr 1&gt;|
    |&lt;Serienr&2;&gt;|&lt;Information om enhet nr 2&gt;|

  När den öppnas i en textredigerare visas den här CSV-filen som:

    ```
    0000000,PO 1234
    111111111,PO 1234
    ```

  -  **Lägg till enhetsinformation manuellt**&mdash;Ange serienummer och anteckningar eller information för upp till 15 enheter.

  I rutan **Granska enheter** kan du bekräfta serienumren. Du kan också bestämma om du vill skriva över **informationen** för serienummer som importeras igen, eller så kan du avmarkera rutan **Skriv över** och behålla den nuvarande informationen. 

> [!NOTE] 
> I den befintliga Intune-administratörskonsolen kan administratörer godkänna tillhörande information från en överförd CSV och skriva över befintlig information för enskilda serienummer. I den nya Azure-portalen kan du endast skriva över information för alla serienummer eller ignorera ny information för alla serienummer.

  > [!NOTE]
  > Om du vill ta bort företagsägda enheter från Intune-hanteringen senare kanske du behöver gå till enhetsgruppen **Efter iOS-serienummer** under **Företagets förregistrerade enheter** och ta bort enhetens serienummer från Intune för att kunna inaktivera enhetsregistreringen. Om Intune utför en katastrofåterställning vid eller runt den tidpunkt då du tar bort serienummer måste du kontrollera att endast aktiva enheters serienummer finns i gruppen.

2. Välj **Nästa**.

3. Välj vilka enheter som ska registreras. Det går inte att importera serienummer som redan har registrerats eller som registrerats på annat sätt. Fortsätt genom att välja **Nästa** .

### <a name="assign-a-profile"></a>Tilldela en profil

Ange profilen som ska tilldelas till enheter som lagts till i listan över tillgängliga profiler, granska **profilregistreringsinformationen** och välj **Slutför**. Manuellt tillagda enheter kan associeras med valfri registreringsprofil.

> [!Important]
> I Intune kan du för närvarande utse en ”standardprofil för enhetsregistrering." Det innebär att nya serienummer automatiskt tilldelas den standardprofilen när du synkroniserar nya serienummer med Apple DEP-tjänsten. När din klient migreras till den nya Azure-portalen inom en snar framtid kommer du inte längre att kunna ange en standardprofil och tilldela serienummer automatiskt till den profilen. Du måste istället tilldela serienummer till en profil. [Läs mer](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-ios-devices-using-device-enrollment-program)

### <a name="export-a-profile-to-deploy-to-ios-devices"></a>Exportera en profil som ska distribueras till iOS-enheter

1. I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsenhetsregistrering** och väljer den enhetsprofil som ska distribueras till mobilenheter. 

2. Välj **Exportera** i Aktivitetsfältet. Kopiera och spara **Profil-URL**. Du kommer att överföra den i Apple Configurator senare för att definiera den Intune-profil som används av iOS-enheter.

  För stöd för Apple Configurator 2 måste 2.0-profilens URL redigeras. Det gör du genom att ersätta den här koden:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Med den här koden:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   Du kommer att överföra den här profil-URL:en till Apples enhetsregistreringsprogramtjänst med hjälp av Apple Configurator genom följande procedur för att definiera den Intune-profil som används av iOS-enheter.



### <a name="prepare-the-device-with-apple-configurator"></a>Förbered enheten med Apple Configurator

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

### <a name="distribute-devices"></a>Distribuera enheter

Enheterna är nu klara för företagets registrering. 

Stäng av enheterna och distribuera dem till användarna. När användarna sätter på sina enheter startar Installationsassistenten.


### <a name="see-also"></a>Se även
[Förutsättningar för att registrera enheter](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO2-->


