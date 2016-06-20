---
# required metadata

title: Hantering med Apples DEP för iOS-enheter med Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: dagerrit
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet
Microsoft Intune kan distribuera en registreringsprofil som registrerar iOS-enheter som köpts via Enhetsregistreringsprogrammet (DEP) "over-the-air". Registreringspaketet kan innehålla installationsassistentalternativ för enheten. Enheter som har registrerats via DEP kan inte avregistreras av användarna.

## Hantering med Apples DEP för iOS-enheter med Microsoft Intune
Ett företag som vill hantera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) måste gå med i Apples program och få enheter genom det. Information om den här processen finns på:  [https://deploy.apple.com](https://deploy.apple.com). Exempel på fördelar med programmet är bland annat obevakade konfigurationer utan USB-anslutning från varje enhet till en dator.

Innan du kan registrera företagsägda iOS-enheter med DEP måste du ha en DEP-token från Apple. Med denna token kan Intune synkronisera information om DEP-deltagande enheter som ägs av ditt företag. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

1.  **Börja hantera iOS-enheter med Microsoft Intune** Innan du kan registrera iOS DEP-enheter (Device Enrollment Program) måste du slutföra aktiveringen av iOS-hantering för Intune.

2.  **Skaffa en krypteringsnyckel** Öppna [Microsoft Intune -administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Admin** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Program för enhetsregistrering** och klicka på **Hämta krypteringsnyckel**. Spara filen med krypteringsnyckeln (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

      ![Uppdatera en token för enhetsregistreringsprogrammet](../media/dev-sa-ios-dep.png)

3.  **Hämta en token för enhetsregistreringsprogrammet** Gå till [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med företagets Apple-ID. Detta Apple-ID måste användas i framtiden för att förnya din DEP-token.

    1.  Öppna [DEP-portalen](https://deploy.apple.com) och gå till **Enhetsregistreringsprogram** &gt; **Hantera servrars** och klickar sedan på **Lägg till MDM-server**.

    2.  Ange **MDM-servernamn** och klicka sedan på **Nästa**. Servernamnet är för din referens för att identifiera MDM-servern. Det är inte namn eller URL-adressen till Microsoft Intune Server.

    3.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Klicka på **Välj fil** för att överföra PEM-filen och klicka sedan på **Nästa**.

    4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din server-token**. Hämta filen server-token (.p7m) till datorn och klickar sedan på **Klar**.

    Den här certifikatfilen (.p7m) används för att upprätta en förtroenderelation mellan Intune och Apples DEP-servrar.

4.  **Lägg till DEP-token i Intune** Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) och gå till **Admin** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Program för enhetsregistrering** och klicka på **Överför DEP-token**. **Bläddra** till certifikatfilen (.p7m), ange ditt **Apple ID**och klicka på **Överför**.

5.  **Lägg till princip för att registrera företagsenheter** I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsenhetsregistrering** och klickar sedan på **Lägg till**.

    Ange **Allmän** information, inklusive **Namn** och **Beskrivning**. Ange om enheter som är tilldelade till profilen har användartillhörighet eller tillhör en grupp.
      - **Fråga efter användartillhörighet**: Enheten måste vara kopplad till en användare under den ursprungliga installationen och kan sedan beviljas samma åtkomst till företagets data och e-post som användaren.  **Användartillhörighet** ska konfigureras för de DEP-hanterade enheter som tillhör användare och som behöver använda företagsportalen (d.v.s. för att installera appar).
      - **Ingen användartillhörighet**: Enheten är inte kopplad till någon användare. Använd den här anknytningen för enheter som utför uppgifter utan att öppna lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för installation av branschspecifika appar, fungerar inte.

    Aktivera sedan **Konfigurera DEP-inställningar för den här profilen** för att ge stöd åt DEP.

      ![Installationsassistentfönstret](../media/pol-sa-corp-enroll.png)

     Följande inställningar är tillgängliga för DEP-hanterade enheter:

     - **Avdelning** – Visas när användarna knackar på "Om Configuration" under aktivering
     - **Telefonnummer till support** – Visas när användaren klickar på **Behöver hjälp** under aktivering
     - **Förberedelseläge** – Det här tillståndet anges under aktiveringen och kan inte ändras utan att enhetens fabriksinställningar återställs:
        - **Oövervakad** – Begränsade hanteringsfunktioner
        - **Övervakad** – Aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard
     - **Lås registreringsprofil till enhet** – Det här tillståndet anges under aktiveringen och kan inte ändras utan en fabriksåterställning
        - **Inaktivera** – Tillåter att hanteringsprofilen tas bort från menyn **Inställningar**
        - **Aktivera** – (Kräver **Förberedelseläge** = **Övervakad**) Inaktiverar iOS-inställningar som möjliggör borttagning av hanteringsprofilen.
     - **Alternativ för installationsassistenten** – De här inställningarna är valfria och kan konfigureras senare på iOS-menyn **Inställningar**
        - **Lösenordskod** – Fråga efter lösenordskod under aktivering. Kräv alltid en lösenordskod om inte enheten ska skyddas eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app).
        - **Platstjänster** – Om en här funktionen är aktiverad frågar Installationsassistenten efter under aktivering
        - **Återställ** – Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering
        - **Apple-ID** – Ett Apple-ID krävs för att hämta iOS App Store-appar, inklusive de som har installerats av Intune. Om det här alternativet är aktiverat uppmanas användaren i iOS att uppge ett Apple-ID när Intune försöker installera en app utan ett ID.
        - **Villkor** – Om alternativet är aktiverat uppmanar Installationsassistenten användarna att acceptera Apples villkor under aktivering - **Touch ID** – Om alternativet är aktiverat frågar Installationsassistenten efter den här tjänsten under aktivering - **Apple Pay** – Om alternativet är aktiverat frågar Installationsassistenten efter den här tjänsten under aktivering - **Zooma** – Om alternativet är aktiverat frågar Installationsassistenten efter den här tjänsten under aktivering - **Siri** – Om alternativet är aktiverat frågar Installationsassistenten efter den här tjänsten under aktivering - **Skicka diagnostikdata till Apple** – Om alternativet är aktiverat frågar Installationsassistenten efter den här tjänsten under aktivering -  **Aktivera ytterligare hantering av Apple Configurator** – Ställ in på **Tillåt inte** att förhindra synkronisering av filer med iTunes eller hantering via Apple Configurator. Microsoft rekommenderar att du anger **Tillåt inte**, exporterar eventuell ytterligare konfiguration från Apple Configurator och sedan distribuerar som en anpassad iOS-konfigurationsprofil via Intune i stället för att använda den här inställningen för att tillåta manuell distribution med eller utan ett certifikat.
        - **Tillåt inte** – Hindrar enheten från att kommunicera via USB (inaktiverar sammankoppling) - **Tillåt** – Tillåter enheten att kommunicera via USB-anslutning för PC eller Mac - **Kräv certifikat** – Tillåter sammankoppling med en Mac-dator med ett certifikat som importerats till registreringsprofilen

6.  **Tilldela DEP-enheter för hantering** Gå till [DEP-portalen (Device Enrollment Program Portal)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med ditt företags Apple-ID. Gå till **Distribution av program** &gt; **Enhetsregistreringsprogram** &gt; **Hantera enheter**. Ange hur du ska **Välja enheter**, ange information om enheten och ange information om enhetens **serienummer**, **ordningsnummer**eller **Överför CSV-fil**. Välj därefter **Tilldela till server**, välj det &lt;ServerName&gt; som har angetts för Microsoft Intune och klicka sedan på **OK**.

7.  **Synkronisera DEP-hanterade enheter** Öppna [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram** och klicka på **Synkronisera nu**. En synkroniseringsbegäran skickas till Apple. Om du vill se DEP-hanterade enheter efter synkroniseringen går du till [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) och sedan till **Grupper** &gt; **Alla företagsägda enheter**. På arbetsytan **Företagsägda enheter** visas ”Ej ansluten” för **Tillstånd** för en hanterad enhet tills enheten har startats och kör installationsassistenten för registrering.

    Om du vill följa Apples villkor för godkänd DEP-trafik tillämpar Intune följande begränsningar:
     -  En fullständig DEP-synkronisering kan endast köras var 7: e dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om en fullständig synkronisering prövas inom 7 dagar efter den föregående fullständiga synkroniseringen, uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran ges 10 minuter att slutföras. Under denna tid, eller tills begäran slutförs, är knappen Synkronisera inaktiverad.

8.  **Distribuera enheter till användare** Dina företagsägda enheter kan nu distribueras till användarna. När en iOS-enhet aktiveras, kommer den att registreras för hantering av Intune.



### Se även
[Dags att registrera enheter](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


