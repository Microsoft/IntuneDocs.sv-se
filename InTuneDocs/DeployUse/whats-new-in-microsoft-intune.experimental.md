---
# required metadata

experiment_id: lindavr-abtest-20160527
title: Vad är nytt | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Nyheter i Microsoft Intune

## Maj 2016


Med undantag för TeamViewer-integrering stöds alla dessa funktioner även för hybriddistributioner (Configuration Manager med Intune). Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Dokumentation

Välkommen till förhandsversionen av [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Det här är en helt ny modern innehållsplattform som har tagits fram för att göra det enklare för våra kunder att förstå och använda Intune.
Mer information om alla de nya funktionerna finns i [Introduktion till docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu hittar du den här informationen under **Tjänstens hälsa** i [Office 365-hanteringsportalen](https://portal.office.com/Admin/Default.aspx).
Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Apphantering

- **MAM SDK: Stöd för konfiguration av PIN-kodens längd.** Du kan ange längden på PIN-koden för MAM-appar på samma sätt som PIN-koden för en enhet. Detta innebär att slutanvändaren måste uppfylla de nya begränsningar som du anger. Användaren ser en lite annorlunda PIN-skärm som är anpassad till den längre inmatningen. Mer information finns i [MAM-principinställningar för Android](/intune/deploy-use/android-mam-policy-settings) och [MAM-principinställningar för iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype för företag för iOS och Android.** Du kan nu välja att rikta in Skype för företag med [MAM utan registreringsprinciper](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). När användarna loggar in tillämpas MAM-principerna.

- **Nya appar tillgängliga för hantering med MAM-principer.** Microsoft Word-, Excel- och PowerPoint-appar för Android kan nu associeras med MAM-principer på enheter som inte har registrerats med Intune. Om du vill se en fullständig lista över appar som stöds kan du gå till Microsoft Intune-galleriet för mobilprogram på sidan för [Microsoft Intune-programpartner](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

### Enhetshantering

- **Fjärrhjälpsessioner för Windows-datorer.** Med TeamViewer-integrering för Windows-datorer som hanteras av Intune-klientprogrammet kan du etablera fjärrhjälpssessioner från Windows-datorer vilket underlättar supportavdelningens arbete. Datorer som stöds är bland annat Windows 7, 8, 8.1 och Windows 10.
Mer information finns i [Vanliga hanteringsuppgifter för Windows-datorer med Microsoft Intune-datorklienten](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#respond-to-a-remote-assistance-request)

### Uppdateringar av företagsportalen

#### Företagsportalappen för Android

- **Popup-meddelanden för slutanvändare**: Slutanvändarna ser nu popup-meddelandena från Android-företagsportalappen när de registrerar eller tar bort enheter från företagsportalen.

- **Ändringar i kontona för Enhetsregistreringshanterare i Android-företagsportalappen.** I syfte att förbättra prestanda och skalning visar Intune inte längre alla enheter i enhetsregistreringshanteraren i fönstret Mina enheter Android-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.
-
#### Företagsportalens webbplats

**Webbplatsen för företagsportalen: En banderoll för enhetsidentifikation visar mer information för slutanvändaren.** Slutanvändarna kan nu enkelt identifiera den enhet de har valt när de använder företagsportalens webbplats. Om fel enhet har valts kan de välja rätt enhet genom att trycka på länken **Tryck här** på banderollen på startsidan.


## Kommande nyheter

- **Introduktion till gränssnittet i Meddelandecenter**. Som en del av migreringen av Intune till [hanteringsportalen för Office 365](https://portal.office.com/) kommer vi att börja utnyttja Meddelandecenter för att informera om nya funktioner och annan kommunikation. Genom att installera den medföljande mobilappen för Office 365-administratör kan du också ta emot meddelanden på din mobiltelefon och enkelt vidarebefordra meddelanden till användare eller ett distributionsalias.
Från och med majutgåvan kommer vi att börja använda Meddelandecenter för att meddela dig när uppdateringar är färdiga och för att publicera information om nya och förbättrade Intune-funktioner. Ta en titt på Meddelandecentret redan nu genom att logga in till [hanteringsportalen för Office 365](https://portal.office.com/) och välja alternativet MEDDELANDECENTER i det vänstra navigeringsfönstret.

- **Ändringar av konton för enhetsregistreringshanterare**. I syfte att förbättra prestanda och skalning visar Intune inte längre **alla** enheter i enhetsregistreringshanteraren i fönstret **Mina enheter** i iOS-företagsportalappen. Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen. DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen. Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP-program för enhetsregistrering (Device Enrollment Program) eller verktyget Apple Configurator. Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter. Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.

### Moln-översikt
Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Tjänstens utfasning
- **Intune Viewer-appar.** Med versionen av den nya RMS-delningsappen tar vi bort följande Intune Viewer-appar, med början från augusti 2016:
    - Intune AV Viewer
    - Intune PDF Viewer
    - Intune Image Viewer för Android från Google Play

  I stället för att använda Intune Viewer-appar bör du använda den nya Rights Management-appen (RMS-delning) för Android, där du kan distribuera en app i stället för tre separata appar för att på ett säkert sätt visa företagets filer på Android-enheter. Läs mer om RMS-delningsappen (med länk till dokumentationen).

- **Borttagning av anpassade meddelanderegler för specifika grupper.**
Intune-meddelanderegler används för att definiera vem en e-postavisering ska skickas till från Intune. För närvarande kan du konfigurera meddelanderegler för att skicka e-post till alla användare av enheter i en Intune-enhetsgrupp som du har skapat. Från och med den 1 juni 2016 eller däromkring kommer det inte längre att finnas stöd för att rikta sig till användarskapade grupper.

    Om du vill rikta en meddelanderegel till en grupp som du har skapat via Microsoft Intune-administrationskonsolen skulle du i dag utföra följande steg:

    Gå till **Admin**-arbetsytan och klicka på **Meddelanderegler** > **Skapa ny regel**

    Välj de enhetsgrupper som regeln ska gälla för i steg två i guiden Skapa meddelanderegel. Det här steget, Välj enhetsgrupper, håller på att fasas ut från Intune-konsolen.

    Den preliminära tidslinjen för den här ändringen ser ut som följer:
    - Från och med juni 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
    - Runt augusti 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
    - Runt oktober 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.


- **Ändringar i stödet för iOS-företagsportalappen**. Under de kommande månaderna kommer det en uppdatering för Microsoft Intune-företagsportalappen för iOS som bara har stöd för enheter som kör iOS 8.0 eller senare. Användarna kan inte registrera nya enheter som kör versioner under iOS 8.0. Registrerade enheter som kör versioner under iOS 8.0 fortsätter att hanteras och kommer under en begränsad tid att kunna fortsätta använda företagsportalappen. Enheterna måste dock har version iOS 8.0 eller senare installerad för att få åtkomst till den senaste versionen av företagsportalappen. Vi rekommenderar att du att meddelar användarna om att de bör uppdatera till iOS 8.0 eller senare för att kunna dra full nytta av nya funktioner i Intune.



## Tidigare versioner av Intune
Information om det senaste halvårets nyheter i Intune finns i artikeln [Tidigare Intune-versioner](previous-intune-releases.md).
> [!div class="op_single_selector"]
- [April 2016](previous-intune-releases.md)
- [Mars 2016](previous-intune-releases.md)
- [Februari 2016](previous-intune-releases.md)
- [Januari 2016](previous-intune-releases.md)
- [December 2015](previous-intune-releases.md)
- [November 2015](previous-intune-releases.md)




### Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO1-->


