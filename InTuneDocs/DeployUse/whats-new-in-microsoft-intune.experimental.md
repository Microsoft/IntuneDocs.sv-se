---
experiment_id: lindavr-abtest-20160527
title: "Vad är nytt | Microsoft Intune"
description: "Ta reda på vad är nytt den här månaden och i tidigare versioner av Microsoft Intune"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
ms.sourcegitcommit: d1fb04dbb8746637bf72c1e227f36fe589594ca0
ms.openlocfilehash: ae524a989e236e84a6ce9d8266fc648dd683a825


---

# Nyheter i Microsoft Intune
Läs mer om nyheterna i den här versionen av Microsoft Intune. Du kan också läsa mer om kommande ändringar som du borde planera för, och om tidigare versioner.

Följande är nytt i den här versionen. Med undantag för uppdateringen av Windows Defender-principinställningen har alla dessa funktioner också stöd för hybriddistributioner (Configuration Manager med Intune). Mer information om nya hybridfunktioner finns på [sidan med nyheter om hybridfunktioner](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Juni 2016
### Hälsotillstånd för Intune-tjänsten
Information om Intune-tjänstens hälsotillstånd har nu flyttats till en central plats med andra Microsoft-tjänster. Nu finns den här informationen i under Tjänstens hälsa i Office 365-hanteringsportalen. Mer information finns i [det här blogginlägget](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

## Apphantering
- **Förbättrad konfigurationsupplevelse för Windows 10-företagsdatapolicy.** Vi har gjort förbättringar i konfigurationsupplevelsen för Windows 10- företagsdatapolicyn vad gäller att skapa regler för program, specificera nätverksgränsdefinitioner och andra inställningar för företagsdataskydd. Läs mer i [Skapa en princip för företagsdataskydd (EDP) med Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


## Enhetshantering
- **Windows Defender-principinställning för att skydda mot potentiellt oönskade appar.** En ny Windows Defender-inställning som kallas **identifiering av potentiellt oönskade program** har lagts till i den allmänna konfigurationsprincipen för Windows 10 Desktop och Mobile. Du kan använda den här inställningen för att skydda registrerade stationära Windows-datorer från att köra program som Windows Defender har klassificerat som potentiellt oönskade. Du kan skydda dig mot att dessa program körs eller använda granskningsläget för att rapportera att ett potentiellt oönskat program har installerats. Mer information finns i [Principinställningar för Windows 10 i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

## Villkorlig åtkomst
- **Cisco ISE-kontrollprinciper för nätverksåtkomst för Intune.**  Kunder som använder Cisco Identity Service Engine (ISE) 2.1 och även använder Microsoft Intune kan ange en princip för nätverksåtkomst i ISE.

    Med den här principen måste enheter som ansluter till nätverket med hjälp av Wi-Fi eller VPN uppfylla följande villkor innan de tillåts åtkomst:

    * Måste hanteras av Intune
    * Måste vara kompatibla med alla distribuerade efterlevnadsprinciper för Intune

 Användare med icke kompatibla enheter uppmanas att registrera sig och åtgärda eventuella efterlevnadsproblem för att få åtkomst.
- **Villkorlig åtkomst för webbläsare.** Du kan skapa en princip för villkorlig åtkomst för [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) och [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) så att programmen bara kan användas från webbläsare som stöds i hanterade och godkända iOS- och Android-enheter. Användare som försöker logga in till Outlook Web Access (OWA) och SharePoint-webbplatser med iOS- och Android-enheter uppmanas att registrera sina enheter med Intune samt att åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS 1175844--->

- **Dynamics CRM Online stöder villkorlig åtkomst.** Du kan skapa en princip för villkorlig åtkomst för [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) så att det bara kan användas av hanterade och kompatibla iOS- och Android-enheter. Slutanvändare som försöker logga in i mobilappen för Dynamics CRM på iOS och Android uppmanas att registrera sig i Intune samt åtgärda eventuella efterlevnadsproblem innan de kan logga in.
<!---TFS1295358--->


## Uppdateringar av företagsportalen

### Android-företagsportalsapp

- När IT-administratörer använder den nya principen ”Kräv att enheter förhindrar installation av appar från okända källor (Android 4.0+)” visas meddelandet ”Installation från okända källor måste inaktiveras” i enheter med Android 4.0 eller senare. Användare måste välja **Inställningar** > **Säkerhet**, och inaktivera **Okända källor**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att ”Genomsök enhet efter säkerhetshot" (Android 4.0+) är aktiverat på enheter” visas meddelandet ”Genomsök enhet efter säkerhetshot” i enheter med Android 4.0 eller senare. Användarna måste välja **Inställningar** > **Google** > **Säkerhet** och aktivera **Genomsök enhet efter säkerhetshot**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om meddelandet och varför användaren måste aktivera inställningen.

- När IT-administratörer använder den nya principen ”Kräv att USB-felsökning är inaktiverat (Android 4.2+)” visas meddelandet ”USB-felsökning måste inaktiveras” i enheter med Android 4.2 eller senare. Användarna måste välja **Inställningar** > **Utvecklaralternativ** och inaktivera **USB-felsökning**. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) om meddelandet och varför användaren måste inaktivera inställningen.

- När IT-administratörer använda nya principen ”Lägsta Android-säkerhetskorrigeringsnivå (Android 6.0+)” visas meddelandet ”Den här enheten motsvarar inte miniminivån för Android-säkerhetskorrigering” i enheter med Android 6.0 eller senare. Användarna måste installera den nödvändiga säkerhetskorrigeringen. Det finns en länk i efterlevnadsmeddelandet som visar mer [information](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) om hur den nödvändiga säkerhetskorrigeringen installeras och vilken säkerhetskorrigering som redan finns installerad.

### iOS-företagsportalappen

- Appinstallationen har förbättrats för slutanvändare som installerar affärsspecifika appar. Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera din iOS-enhet manuellt](/Intune/EndUser/sync-your-device-manually-ios.md).

- Microsoft Intunes-företagsportalappen för iOS har uppdaterats med stöd till iOS version 8.0 och senare. Uppdateringen innebär att slutanvändare bara kan installera företagsportalappen och registrera nya enheter i Intune om enheten kör iOS version 8.0 eller senare. Användare som redan har registrerat enheter som körs på en iOS-version som inte stöds, kan fortsätta använda den företagsportalapp som finns på enheten.


## Kommande nyheter

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
    - Från och med augusti 2016 kan nya klienter inte se steg två i guiden Skapa meddelanderegel. Befintliga klienter påverkas inte.
    - Omkring september 2016 kommer vissa befintliga klienter inte att se kommandot för att välja enhetsgrupper i guiden.
    - Omkring november 2016 planerar vi för att samtliga klienter inte kommer att se kommandot för att välja enhetsgrupper i guiden.


- **Ändringar i stödet för iOS-företagsportalappen**. I juli krävs det av alla användare att de använder den senaste versionen av Microsoft Intune-företagsportalappen för iOS . Nya användare kommer bara att kunna hämta den senaste versionen och aktuella användare kommer att behöva uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.





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



<!--HONumber=Jun16_HO4-->


