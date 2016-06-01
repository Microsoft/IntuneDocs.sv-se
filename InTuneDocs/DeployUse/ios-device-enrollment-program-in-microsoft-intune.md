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
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera företagsägda iOS-enheter i Enhetsregistreringsprogrammet
Microsoft Intune kan distribuera en registreringsprofil som registrerar iOS-enheter som köpts via Enhetsregistreringsprogrammet (DEP) "over-the-air". Registreringspaketet kan innehålla installationsassistentalternativ för enheten. Enheter som har registrerats via DEP kan inte avregistreras av användarna.

## Hantering med Apples DEP för iOS-enheter med Microsoft Intune
Ett företag som vill hantera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) måste gå med i Apples program och få enheter genom det. Information om den här processen finns på:  [https://deploy.apple.com](https://deploy.apple.com). Exempel på fördelar med programmet är bland annat obevakade konfigurationer utan USB-anslutning från varje enhet till en dator.

Innan du kan registrera företagsägda iOS-enheter med DEP måste du ha en DEP-token från Apple. Med denna token kan Intune synkronisera information om DEP-deltagande enheter som ägs av ditt företag. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

1.  **Börja hantera iOS-enheter med Microsoft Intune**
    Du måste aktivera iOS-hantering för Intune innan du kan registrera DEP-enheter (Device Enrollment Program) för iOS.

2.  **Skaffa en krypteringsnyckel**
    Som administratör öppnar du [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com), går till **Administratör** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram** och klickar på **Hämta krypteringsnyckel**. Spara filen med krypteringsnyckeln (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

      ![Uppdatera en token för enhetsregistreringsprogrammet](../media/dev-sa-ios-dep.png)

3.  **Skaffa en token för enhetsregistreringsprogrammet**
    Gå till [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med företagets Apple-ID. Detta Apple-ID måste användas i framtiden för att förnya din DEP-token.

    1.  I [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) går du till **Enhetsregistreringsprogram** &gt; ** Hantera servrar** och klickar på **Lägg till MDM-server**.

    2.  Ange **MDM-servernamn** och klicka sedan på **Nästa**. Servernamnet är för din referens för att identifiera MDM-servern. Det är inte namn eller URL-adressen till Microsoft Intune Server.

    3.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Klicka på **Välj fil** för att överföra PEM-filen och klicka sedan på **Nästa**.

    4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din server-token**. Hämta filen server-token (.p7m) till datorn och klickar sedan på **Klar**.

    Den här certifikatfilen (.p7m) används för att upprätta en förtroenderelation mellan Intune och Apples DEP-servrar.

4.  **Lägg till DEP-token i Intune**
    I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com), går du till **Admin** &gt; **hantering av mobila enheter** &gt; **iOS** &gt; **enhetsregistreringsprogram**, och klickar på **Överför DEP-Token**. **Bläddra** till certifikatfilen (.p7m), ange ditt **Apple-ID**, och klicka på **Överför**.

5.  **Lägg till principen för registrering av företagsenheter**
    I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com), gå till **Princip** &gt; ** Företagsenhetsregistrering** och klicka sedan på **Lägg till**. Ange **Allmän** information, inklusive **Namn** och **Beskrivning**. Ange om enheter som är tilldelade till profilen har användartillhörighet eller tillhör en grupp och aktivera sedan inställningar för **Konfigurera enhetsregistreringsprogram för denna princip** för att ge stöd för DEP. I **Installationsassistentsfönstren** definieras de iOS-enhetsinställningar som konfigurerades vid installationen.

      ![Installationsassistentfönstret](../media/pol-sa-corp-enroll.png)

6.  **Tilldela DEP-enheter för hantering**
    Gå till [DEP-portalen (Device Enrollment Program)](https://deploy.apple.com) (https://deploy.apple.com) och logga in med företagets Apple-ID. Gå till **Distribution av program** &gt; **Enhetsregistreringsprogram** &gt; **Hantera enheter**. Ange hur du ska **Välja enheter**, ange information om enheten och ange information om enhetens **serienummer**, **ordningsnummer**eller **Överför CSV-fil**. Välj därefter **Tilldela till server**, välj det &lt;ServerName&gt; som angetts för Microsoft Intune och klicka sedan på **OK**.

7.  **Synkronisera DEP-hanterade enheter**
    Som administratör öppnar du [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com), går till **Administratör** &gt; **Hantering av mobila enheter** &gt; **iOS** &gt; **Enhetsregistreringsprogram** och klickar på **Synkronisera nu**. En synkroniseringsbegäran skickas till Apple. För att se DEP-hanterade enheter efter synkroniseringen går du till [administrationskonsolen för Microsoft Intunes](http://manage.microsoft.com), **Grupper** &gt; **Alla företagsägda enheter**. På arbetsytan **Företagsägda enheter** visas ”Ej ansluten” för **Tillstånd** för en hanterad enhet tills enheten har startats och kör installationsassistenten för registrering.

    Om du vill följa Apples villkor för godkänd DEP-trafik tillämpar Intune följande begränsningar:
     -  En fullständig DEP-synkronisering kan endast köras var 7: e dag. Under en fullständig synkronisering uppdaterar Intune varje serienummer Apple har tilldelat Intune vare sig serien tidigare har synkroniserats eller inte. Om en fullständig synkronisering prövas inom 7 dagar efter den föregående fullständiga synkroniseringen, uppdaterar Intune endast serienummer som inte redan visas i Intune.
     -  Varje synkroniseringsbegäran ges 10 minuter att slutföras. Under denna tid, eller tills begäran slutförs, är knappen Synkronisera inaktiverad.

8.  **Distribuera enheter till användare**
    Nu kan dina företagsägda enheter distribueras till användarna. När en iOS-enhet aktiveras, kommer den att registreras för hantering av Intune.



### Se även
[Dags att registrera enheter](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


