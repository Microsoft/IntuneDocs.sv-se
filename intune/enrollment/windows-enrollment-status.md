---
title: Konfigurera en sida för registreringsstatus
titleSuffix: Microsoft Intune
description: Konfigurera en hälsningssida för användare som registrerar Windows 10-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a470c9a92f7792af2b371acf873807ad344afb
ms.sourcegitcommit: b752acefec077c719e169e665c955adb944e85c6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781115"
---
# <a name="set-up-an-enrollment-status-page"></a>Konfigurera en sida för registreringsstatus
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
På sidan för registreringsstatus (ESP) visas installationsinformation om Windows 10-enheter (version 1803 och senare) under den inledande enhetsregistreringen. Exempel:
- när du använder [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 
- eller närhelst en hanterad enhet startas för första gången efter att en princip för registreringsstatus har tillämpats. 

Statussidan för registreringen kan hjälpa användaren att förstå statusen för sina enheter under enhetskonfigurationen. Du kan skapa flera profiler för sidan för registreringsstatus och tillämpa dem på olika grupper som innehåller användare. Profiler kan ställas in att:
- Visa installationsförloppet.
- Blockera användningen tills installationen är klar.
- Ange vad en användare kan göra om enhetskonfigurationen misslyckas.

Du kan också ange en prioritetsordning för varje profil om det skulle uppstå konflikter mellan profiltilldelningar för samma användare.

> [!NOTE]
> Sidan för registreringsstatus kan bara vara riktad mot en användare som tillhör en tilldelad grupp och principen ställs in på enheten vid tidpunkten för registreringen för alla användare som använder enheten.  

## <a name="available-settings"></a>Tillgängliga inställningar

 Följande inställningar kan konfigureras för att anpassa beteendet för sidan registreringsstatus:

<table>
<th align="left">Inställningen<th align="left">Ja<th align="left">Nej
<tr><td>Visa installationsförlopp för appar och profiler<td>Registreringsstatussidan visas.<td>Registreringsstatussidan visas inte.
<tr><td>Blockera enhetsanvändning tills alla appar och profiler är installerade<td>Inställningarna i den här tabellen görs tillgängliga för att anpassa beteendet för sidan registreringsstatus, så att användaren kan åtgärda eventuella installationsproblem.
<td>Sidan registreringsstatus visas utan ytterligare alternativ för att lösa installationsproblem.
<tr><td>Tillåt användare att återställa enheten om installationsfel uppstår<td>Knappen <b>Återställ enheten</b> visas om installationsfel uppstår.<td>Knappen <b>Återställ enheten</b> visas inte om installationsfel uppstår.
<tr><td>Tillåt användare att återställa enheten om installationsfel uppstår<td>Knappen <b>Fortsätt ändå</b> visas om ett installationsfel uppstår.<td>Knappen <b>Fortsätt ändå</b> visas inte om ett installationsfel uppstår.
<tr><td>Visa tidsgränsfel när installationen tar längre tid än det angivna antalet minuter<td colspan="2">Ange antalet minuter som ska förflyta innan installationen slutförs. Ett standardvärde på 60 minuter har angetts.
<tr><td>Visa anpassat meddelande när ett fel uppstår<td>En textruta finns där du kan ange ett anpassat meddelande som ska visas om ett installationsfel inträffar.<td>Standardmeddelandet visas: <br><b>Installationen överskred den angivna tidsgränsen för din organisation. Försök igen eller kontakta din IT-support om du behöver hjälp.<b>
<tr><td>Tillåt användare att samla in loggar om installationsfel<td>Om det finns ett installationsfel visas knappen <b>Samla in loggar</b>. <br>Om användaren klickar på den här knappen uppmanas de att välja en plats där loggfilen ska sparas <b>MDMDiagReport.cab</b><td>Knappen <b>Samla in loggar</b> visas inte om installationsfel uppstår.
<tr><td>Blockera enhetsanvändning tills följande obligatoriska appar har installerats, om de är tilldelade till användaren/enheten<td colspan="2">Välj <b>Alla</b> eller <b>Valda</b>. <br><br>Om <b>Selected</b> väljs visas en knappen <b>Välj appar</b> som låter dig välja vilka appar som måste installeras innan enheten aktiveras.
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivera standardsidan för registreringsstatus för alla användare

Följ stegen nedan om du vill aktivera sidan för registreringsstatus.
 
1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Windows** > **Windows-registrering** > **Sidan för registreringsstatus**.
2. På bladet **Statussidan för registrering**  väljer du **Standard** > **Inställningar**.
3. Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4. Välj övriga inställningar som du vill aktivera och välj sedan **Spara**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Skapa en profil för registreringsstatussidan och tilldela den till en grupp

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Windows** > **Windows-registrering** > **Sidan för registreringsstatus** > **Skapa profil**.
2. Ange ett **namn** och en **beskrivning**.
3. Välj **Skapa**.
4. Välj den nya profilen i listan **Statussidan för registrering**.
5. Välj **Tilldelningar** > **Välj grupper** > välj de grupper som ska använda den här profilen > **Välj** > **Spara**.
6. Välj **Inställningar** > välj de inställningar som du vill använda för den här profilen > **Spara**.

## <a name="set-the-enrollment-status-page-priority"></a>Ange prioritet för registreringsstatussidan

En användare kan finnas i flera grupper och ha många profiler för registreringsstatussidan. För att lösa dessa konflikter kan du ange prioriteten för varje profil. Om någon har mer än en profil för registreringsstatussidan, tillämpas endast profilen med högst prioritet vid registreringen.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Windows** > **Windows-registrering** > **Sidan för registreringsstatus**.
2. Hovra över profilen i listan.
3. Använd de tre lodräta punkterna och dra profilen till önskad plats i listan.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Blockera åtkomst till en enhet tills ett visst program har installerats

Du kan ange vilka appar som måste installeras innan användaren kan komma åt skrivbordet.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Windows** > **Windows-registrering** > **Sidan för registreringsstatus**.
2. Välj en profil > **Inställningar**.
3. Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4. Välj **Ja** för **Block device use until all apps and profiles are installed** (Blockera enhetsanvändning tills alla appar och profiler är installerade).
5. Välj **Valda** för **Blockera enhetsanvändning tills följande obligatoriska appar har installerats, om de är tilldelade till användaren/enheten**.
6. Välj **Välj appar** > välj apparna > **Välj** > **Spara**.

## <a name="enrollment-status-page-tracking-information"></a>Spårningsinformation på statussidan för registrering

Det finns tre faser där statussidan spårar information: enhetsförberedelse, enhetskonfiguration och kontokonfiguration.

### <a name="device-preparation"></a>Förberedelse av enheten

När det gäller enhetsförberedelse spårar registreringsstatussidan:
- Trusted Platform Module-nyckelattesteringar (TPM) (i förekommande fall)
- förlopp vid anslutning till Azure Active Directory
- registrera i Intune
- installera Intune-hanteringstillägg

### <a name="device-setup"></a>Enhetskonfiguration

Registreringsstatussidan spårar följande enhetsinställningsobjekt (om de är tilldelade till alla enheter eller en enhetsgrupp där den registrerade enheten är medlem):
- Säkerhetsprinciper
  - En konfigurationstjänstprovider (CSP) för alla registreringar.
  - De faktiska konfigurationstjänstprovidrar som har konfigurerats av Intune spåras inte här.
- Program
  - Verksamhetskritiska (LoB) MSI-appar per dator.
  - LoB-lagringsappar med installationskontext = Enhet.
  - Offlinelagrings- och LoB-lagringsappar med installationskontext = Enhet.
  - Win32-program (endast Windows 10 version 1903 och senare) 
- Anslutningsprofiler
  - VPN- eller Wi-Fi-profiler som har tilldelats **Alla enheter** eller en enhetsgrupp som enheten som registreras är medlem i, men endast för Autopilot-enheter
- Certifikatprofiler som har tilldelats **Alla enheter** eller en enhetsgrupp som enheten som registreras är medlem i, men endast för Autopilot-enheter

### <a name="account-setup"></a>Kontokonfiguration
För kontokonfiguration spårar statussidan för registrering följande objekt om de har tilldelats till den aktuella användaren:
- Säkerhetsprinciper
  - En konfigurationstjänstprovider (CSP) för alla registreringar.
  - De faktiska konfigurationstjänstprovidrar som har konfigurerats av Intune spåras inte här.
- Program
  - Verksamhetsspecifika MSI-appar per användare som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
  - Verksamhetsspecifika MSI-appar per dator som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
  - Verksamhetsspecifika butiksappar, appar i onlinebutiken och appar i offlinebutiken som tilldelas något av följande objekt:
    - Alla enheter
    - Alla användare
    - En användargrupp där användaren som registrerar enheten är en medlem med installationskontexten Användare.
  - Win32-program (endast Windows 10 version 1903 och senare) 
- Anslutningsprofiler
  - VPN- eller Wi-Fi-profiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
- Certifikat
  - Certifikatprofiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.

### <a name="troubleshooting"></a>Felsökning
Vanliga frågor om felsökning.

- Varför installerades inte mina program under enhetsinstallationsfasen under autopilotdistributionen som använder registreringsstatussidan?
  - För att garantera att program installeras under en installation av en autopilotenhet, se till att 
        1. Programmet väljs för att blockera åtkomst i listan över valda appar
        2. Programmen riktas mot samma Azure AD-enhetsgrupp som din autopilotprofil är tilldelad till. 

- Varför visas sidan registreringsstatus för distributioner som inte gäller autopilot, till exempel när en användare loggar in för första gången på en registrerad enhet för Configuration Manager-medhantering?  
  - Registreringsstatussidan visar installationsstatus för alla registreringsmetoder, inklusive
      - Autopilot
      - Medhantering med Configuration Manager
      - När en ny användare loggar in på enheten som har tillämpat principen för registreringsstatussidan för första gången

- Hur kan jag inaktivera registreringsstatussidan om den har konfigurerats på enheten?
  - Registreringsstatussidans princip konfigureras på en enhet när den registreras. Om du vill inaktivera registreringsstatussidan måste du inaktivera områdena användare och status på registreringsstatussidan. Du inaktiverar avsnitten genom att skapa anpassade OMA-URI-inställningar med följande konfigurationer.

      Avaktivera användarregistreringsstatussidan:

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      Avaktivera enhetsregistreringsstatussidan:

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- Hur kan jag samla in loggfiler?
  - Det finns två sätt som loggfiler för registreringsstatussidan kan samlas in på:
      - Ge användarna möjlighet att samla in loggar i ESP-principen. När ett avbrott sker på registreringsstatussidan kan slutanvändaren välja alternativet att **Samla in loggar**. Genom att sätta in en USB-enhet kan loggfilerna kopieras till enheten
      - Öppna en kommandotolk genom att trycka på shift-F10 och ange följande kommandorad för att generera loggfilerna: 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>Kända problem
Nedan visas kända problem. 
- Om du inaktiverar ESP-profilen tas inte ESP-principen bort från enheterna och användarna får fortfarande ESP när de loggar in på enheten för första gången. Principen tas inte bort när ESP-profilen är inaktiverad. Du måste distribuera OMA-URI för att inaktivera ESP. Se ovan för instruktioner om hur du inaktiverar ESP med OMA-URI. 
- En väntande omstart kommer alltid att orsaka ett avbrott. Avbrottet beror på att enheten måste startas om. Enheten måste starta om för att ge tillräckligt med tid för att objektet som spåras i registreringsstatussidan ska slutföras. En omstart kommer att leda till att registreringsstatussidan avslutas. Efter omstart kommer enheten inte att starta kontokonfigurationen.  Överväg att inte kräva omstart när programmet installeras. 
- En omstart under enhetsinstallationen tvingar användaren att ange sina autentiseringsuppgifter innan de övergår till installationsfasen för kontot. Användarautentiseringsuppgifter bevaras inte under omstarten. Låt användaren ange sina autentiseringsuppgifter. Därefter kan registreringsstatussidan fortsätta. 
- Registreringsstatussidan kommer alltid att göra ett avbrott under en registrering av arbets- eller skolkonto på enheter med versioner av Windows 10 som är äldre än 1903. Registreringsstatussidan väntar på att Azure AD-registreringen ska slutföras. Problemet åtgärdas i Windows 10-version 1903 och senare.  
- Hybrid Azure AD-autopilotdistribution med ESP tar längre tid än det avbrott som har definierats i ESP-profilen. I hybriddistributioner av Azure AD-autopilot tar ESP 40 minuter längre än värdet som anges i ESP-profilen. Den här fördröjningen låter det lokala AD-anslutningsprogrammet skapa den nya enhetsposten i Azure AD. 
- Inloggningssidan för Windows är inte ifylld med användarnamnet i användardrivet Autopilot-läge. Om en omstart sker under enhetskonfigurationsfasen i ESP:
    - bevaras inte användarautentiseringsuppgifterna
    - måste användaren ange autentiseringsuppgifterna igen innan de fortsätter från enhetsinstallationsfasen till kontoinstallationsfasen
- ESP har fastnat under en längre tid eller så slutförs aldrig fasen "Identifierar". Intune beräknar ESP-principerna under identifieringsfasen. En enhet kan kanske inte slutföra beräkningen av ESP-principerna om den aktuella användaren inte har en tilldelad Intune-licens.  
- Om du konfigurerar Windows Defender-programreglering kan du bli ombedd att starta om under Autopilot. Konfigurering av Microsoft Defender-programmet (AppLocker CSP) kräver en omstart. När den här principen har konfigurerats kan det leda till att en enhet startas om under autopilot. För närvarande finns det inget sätt att utelämna eller skjuta upp omstarten.
- När DeviceLock-principen (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) är aktiverad som en del av en ESP-profil kan fel på automatisk inloggning med användarskrivbord eller OOBE uppstå oväntat av två orsaker.
  - Om enheten inte har startats om innan du avbröt installationsfasen för ESP-enheten kan användaren uppmanas att ange sina autentiseringsuppgifter för Azure AD. Det här meddelandet visas i stället för en lyckad automatisk inloggning där användaren ser en animation för första inloggningen på Windows.
  - Automatisk inloggning kommer att misslyckas om enheten startades om efter att användaren angav sina inloggningsuppgifter för Azure AD men innan ESP-enhetens konfigurationsfas avslutades. Felet uppstår eftersom ESP-konfigurationsfasen inte slutfördes. Lösningen är att återställa enheten.

## <a name="next-steps"></a>Nästa steg
När du har konfigurerat Windows-registreringssidor kan du gå vidare och lära dig hur du hanterar Windows-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](../remote-actions/device-management.md)
