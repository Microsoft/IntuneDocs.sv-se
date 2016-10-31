---
title: "Hantering med Apples DEP för iOS-enheter | Microsoft Intune"
description: "Distribuera en registreringsprofil som registrerar iOS-enheter som har köpts via enhetsregistreringsprogrammet (DEP) ”over the air” (trådlöst) för att hantera Apple-enheter."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 021c02c9a148746a76309efc819b9e28a2748c4f
ms.openlocfilehash: b608d6353db2f37eed03d34c9216726fa7cd1cb2


---

# Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet
Microsoft Intune kan distribuera en registreringsprofil som registrerar iOS-enheter som köpts via enhetsregistreringsprogrammet (DEP) ”over the air” (trådlöst). Registreringspaketet kan innehålla installationsassistentalternativ för enheten. Enheter som har registrerats via DEP kan inte avregistreras av användarna.

## Hantering med Apples DEP för iOS-enheter med Microsoft Intune
Ett företag som vill hantera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) måste gå med i Apples program och skaffa enheter genom det. Information om den här processen finns på:  [https://deploy.apple.com](https://deploy.apple.com). Exempel på fördelar med programmet är obevakade enhetsinstallationer utan användning av en USB-kabel för att ansluta varje enhet till en dator.

Innan du kan registrera företagsägda iOS-enheter med DEP behöver du en DEP-token från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till DEP och som ditt företag äger. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

1.  **Börja hantera iOS-enheter med Microsoft Intune**</br>
    Du måste aktivera iOS-hantering för Intune innan du kan registrera DEP-enheter (Device Enrollment Program) för iOS.

2.  **Skaffa en krypteringsnyckel**</br>
    Som en administratörsanvändare öppnar du [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com), går till **Admin** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram (DEP)** och väljer **Hämta krypteringsnyckel**. Spara filen med krypteringsnyckeln (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

      ![Uppdatera en token för enhetsregistreringsprogrammet](../media/dev-sa-ios-dep.png)

3.  **Skaffa en token för enhetsregistreringsprogrammet**</br>
    Gå till [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med företagets Apple-ID. Detta Apple-ID måste användas senare för att förnya din DEP-token.

    1.  På [DEP-portalen (Device Enrollment Program Portal)](https://deploy.apple.com) går du till **Enhetsregistreringsprogram (DEP)** &gt; **Hantera servrar** och väljer **Lägg till MDM-server**.

    2.  Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

    3.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.

    4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.

    Den här certifikatfilen (.p7m) används för att upprätta en förtroenderelation mellan Intune och Apples DEP-servrar.

4.  **Lägg till DEP-token i Intune**</br>
    I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Admin** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram (DEP)** och väljer sedan **Ladda upp en DEP-token**. **Bläddra** till certifikatfilen (.p7m), ange ditt **Apple-ID** och välj sedan **Överför**.

5.  **Lägg till principen för registrering av företagsenheter**</br>
    I [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) går du till **Princip** &gt; **Företagsägda enheter** och väljer sedan **Lägg till**.

    Ange **Allmän** information, inklusive **Namn** och **Beskrivning**, och ange om enheter som är tilldelade till profilen har användartillhörighet eller tillhör en grupp.
      - **Fråga efter användartillhörighet**: Enheten måste kopplas till en användare under den ursprungliga installationen innan den kan beviljas samma åtkomst till företagets data och e-post som användaren. **Användartillhörighet** bör konfigureras för de DEP-hanterade enheter som tillhör användare och som behöver använda företagsportalen (dvs. för att installera appar).</br> **Obs:** DEP-enheter med användartillhörigheter har inte stöd för multifaktorautentisering.

      > [!NOTE]
      > DEP med användartillhörighet kräver att WS-Trust 1.3 användarnamn/kombinerad slutpunkt aktiveras för att du ska kunna begära en användartoken.

      - **Ingen användartillhörighet**: Enheten är inte kopplad till någon användare. Använd den här tillhörighetstypen för enheter som utför uppgifter utan att komma åt lokala användardata. Appar som kräver användartillhörighet, inklusive företagsportalappen som används för att installera affärsappar, kommer inte att fungera.

    Du kan också **Tilldela enheter till följande grupp**. Välj **Välj** för att välja en grupp.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Aktivera sedan **Konfigurera DEP-inställningar för den här profilen** för att ge stöd åt DEP.

      ![Installationsassistentfönstret](../media/pol-sa-corp-enroll.png)

     Följande inställningar är tillgängliga för DEP-hanterade enheter:

     - **Avdelning** – Visas om användaren trycker på **Om konfiguration** under aktiveringen
     - **Telefonnummer till support** – Visas om användaren klickar på **Behöver hjälp** under aktiveringen
     - **Förberedelseläge** – Anges under aktiveringen och kan inte ändras utan att enhetens fabriksinställningar återställs:
        - **Oövervakad** – Begränsade hanteringsfunktioner
        - **Övervakad** – Aktiverar fler hanteringsalternativ och inaktiverar aktiveringslåset som standard
     - **Lås registreringsprofil till enhet** – Anges under aktiveringen och kan inte ändras utan en fabriksåterställning
        - **Inaktivera** – Tillåter att hanteringsprofilen tas bort från menyn **Inställningar**
        - **Aktivera** – (Kräver **Förberedelseläge** = **Övervakad**) Inaktiverar iOS-inställningar som möjliggör borttagning av hanteringsprofilen.
     - **Alternativ för Installationsassistenten** – Dessa valfria inställningar kan konfigureras senare på menyn **Inställningar** i iOS.
        - **Lösenordskod** – Fråga efter lösenordskod under aktivering. Kräv alltid en lösenordskod om inte enheten ska skyddas eller åtkomstkontrolleras på något annat sätt (t.ex. helskärmsläge som begränsar enheten till en app).
        - **Platstjänster** – Om en här funktionen är aktiverad frågar Installationsassistenten efter under aktivering
        - **Återställ** – Om den här funktionen är aktiverad frågar Installationsassistenten om iCloud-säkerhetskopiering vid aktivering
        - **Apple-ID** – Om det här alternativet är aktiverat uppmanas användaren i iOS att uppge ett Apple-ID när Intune försöker installera en app utan ett ID. Ett Apple-ID krävs för att hämta iOS App Store-appar, inklusive de som har installerats av Intune.
        - **Villkor** – Om det här alternativet är aktiverat uppmanas användarna i installationsassistenten att godkänna Apples villkor under aktiveringen
        - **Touch ID** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Apple Pay** – Om det här alternativet är aktiverat frågar installationsassistenten efter den här tjänsten under aktivering
        - **Zooma** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Siri** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
        - **Skicka diagnostikdata till Apple** – Om den här funktionen är aktiverad frågar installationsassistenten efter den här tjänsten under aktivering
     -  **Aktivera ytterligare hantering av Apple Configurator** – Ange till **Tillåt inte** om du vill förhindra synkronisering av filer med iTunes eller hantering via Apple Configurator. Det är en bra idé att välja **Tillåt inte**, exportera ytterligare konfigurationer från Apple Configurator och sedan distribuera som en anpassad iOS-konfigurationsprofil via Intune i stället för att använda den här inställningen för att tillåta manuell distribution med eller utan ett certifikat.
        - **Tillåt inte** – Hindrar enheten från att kommunicera via USB (inaktiverar sammankoppling)
        - **Tillåt** – Tillåter att enheten kommunicerar via USB-anslutning för PC- eller Mac-dator
        - **Kräv certifikat** – Möjliggör sammankoppling med en Mac-dator med ett certifikat som har importerats till registreringsprofilen

6.  **Tilldela DEP-enheter för hantering** Gå till [DEP-portalen (Device Enrollment Program Portal)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med ditt företags Apple-ID. Gå till **Distributionsprogram** &gt; **Enhetsregistreringsprogram (DEP)** &gt; **Hantera enheter**. Ange hur du ska **Välja enheter**, ange information om enheten och ange information om enhetens **serienummer**, **ordningsnummer**eller **Överför CSV-fil**. Välj **Assign to Server** (Tilldela till server) och välj &lt;servernamnet&gt; som angetts för Microsoft Intune och sedan **OK**.

7.  **Synkronisera DEP-hanterade enheter** Öppna [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram (DEP)** och välj sedan **Synkronisera nu**. En synkroniseringsbegäran skickas till Apple. Om du vill se DEP-hanterade enheter efter synkroniseringen går du till [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com), går till **Grupper** &gt; **Alla enheter**&gt;**Företagets förregistrerade enheter**&gt;**Efter iOS-serienummer**. På arbetsytan **Efter iOS-serienummer** visas ”Ej ansluten” för **Tillstånd** för en hanterad enhet tills enheten har startats och kör installationsassistenten för registrering.

    Om du vill följa Apples villkor för godkänd DEP-trafik tillämpar Intune följande begränsningar:
     -  En fullständig DEP-synkronisering kan inte köras oftare än en gång var sjunde dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer som Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om du försöker köra en fullständig synkronisering inom sju dagar efter den föregående fullständiga synkroniseringen uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran har 10 minuter på sig att slutföras. Under den här tiden, eller tills begäran slutförts, är knappen **Synkronisera** inaktiverad.

8.  **Distribuera enheter till användare** Dina företagsägda enheter kan nu distribueras till användarna. När en iOS-enhet aktiveras, kommer den att registreras för hantering av Intune.

## Ändringar i Intune-grupptilldelningar

Från och med november flyttas grupphantering för enheter till Azure Active Directory. Efter övergången till Azure Active Directory-grupper visas grupptilldelning inte i alternativen för **Företagets registreringsprofil**. Eftersom ändringen görs över ett antal månader kan du kanske inte se ändringen direkt. Efter flytten till den nya portalen kan dynamiska enhetsgruppstilldelningar definieras baserat på namnet på företagets registreringsprofil. Den här processen ser till att enheter som redan har tilldelats till en enhetsgrupp registreras automatiskt i gruppen med principer och appar distribuerade. [Läs mer om Azure Active Directory-grupper](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### Se även
[Förutsättningar för att registrera enheter](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->


