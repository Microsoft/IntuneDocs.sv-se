---
title: Lägga till slutpunktsskydd i macOS i Microsoft Intune – Azure | Microsoft Docs
description: På macOS-enheter använder du gatekeepern för att avgöra var appar kan installeras, inklusive Mac App Store. Genom att aktivera eller konfigurera en brandvägg kan man också tillåta eller blockera specifika appar, använda Stealthläge och även blockera vissa typer av inkommande anslutningar med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4aa0c47f0aa099ff469eb31b212f387836ad69b
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68756514"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Inställningar av slutpunktsskydd för macOS i Intune  

I den här artikeln visas inställningarna för slutpunktsskydd som du kan konfigurera för enheter som kör macOS. Du konfigurerar dessa inställningar genom att använda en macOS-enhets konfigurations profil för [Endpoint Protection](endpoint-protection-configure.md) i Intune.  

## <a name="gatekeeper"></a>Gatekeeper  

- **Tillåt appar som hämtats från dessa platser**  
  Begränsa vilka appar en enhet kan starta, beroende på var apparna hämtades från. Avsikten är att skydda enheter mot skadlig kod och tillåta appar endast från källor som du litar på.  

  - **Inte konfigurerat**  
  - **Mac App Store**  
  - **Mac App Store och identifierade utvecklare**  
  - **Överallt**  

  **Standard**: Inte konfigurerat  

- **Användaren kan åsidosätta gatekeeper**  
  Förhindrar användare från att åsidosätta denna inställning och från att installera en app genom att Ctrl-klicka. När den är aktiverad kan användare installera appar med Ctrl+klick.  
 
  - **Inte konfigurerad** – användare kan Ctrl-klicka för att installera appar.  
  - **Blockera** – förhindrar att användare använder Ctrl-klicka för att installera appar.  

  **Standard**: Inte konfigurerat  

## <a name="firewall"></a>Brandvägg  

Använd brandväggen för att styra anslutningar per program i stället för per port. Med programspecifika inställningar är det lättare att använda brandväggsskyddet. Du också förhindra att oönskade appar tar kontroll över nätverksportar som är öppna för legitima appar.  

**Allmänt**
- **Brandvägg**  
  Aktivera brandväggen om du vill konfigurera hur inkommande anslutningar ska hanteras i din miljö.  
  - **Inte konfigurerat**  
  - **Aktivera**  

  **Standard**: Inte konfigurerat  

- **Inkommande anslutningar**  
  Blockera alla inkommande anslutningar utom de anslutningar som krävs för grundläggande Internet-tjänster, till exempel DHCP, Bonjour och IPSec. Funktionen blockerar också alla delade tjänster, till exempel fildelning och skärmdelning. Om du använder delningstjänster behåller du inställningen som *Inte konfigurerad*.  
  - **Inte konfigurerat**  
  - **Blockera**  

  **Standard**: Inte konfigurerat  

**Tillåta eller blockera inkommande anslutningar för specifika appar.**  

  - **Tillåtna appar**  
    Välj de appar som uttryckligen ska tillåtas ta emot inkommande anslutningar.  

  - **Blockerade appar**  
    Välj de appar som ska blockera inkommande anslutningar.  

  - **Dolt läge**  
    Aktivera detta om du vill förhindra att datorn svarar på avsökningsförfrågningar. Enheten fortsätter att besvara inkommande begäranden för godkända appar. Oväntade begäranden, till exempel ICMP (ping) ignoreras.  
    - **Inte konfigurerat**  
    - **Aktivera**  

    **Standard**: Inte konfigurerat  

## <a name="filevault"></a>FileVault  
Mer information om Apple FileVault-inställningar finns i [FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) i Apple Developer-innehåll. 

- **FileVault**  
  Du kan *Aktivera* fullständig disk kryptering med XTS-AES 128 med FileVault på enheter som kör MacOS 10,13 och senare.  
  - **Inte konfigurerat**  
  - **Aktivera**  

  **Standard**: Inte konfigurerat  

  - **Typ av återställnings nyckel**  
    *Personliga nyckel* återställnings nycklar skapas för enheter. Konfigurera följande inställningar för den personliga nyckeln.  

    - **Plats för personlig återställnings nyckel** – ange ett kort meddelande till användaren som förklarar hur och var de kan hämta sin personliga återställnings nyckel. Den här texten infogas i meddelandet användaren ser på deras inloggnings skärm när du uppmanas att ange deras personliga återställnings nyckel om ett lösen ord är bortglömt.  
      
    - **Rotation av personlig återställnings nyckel** – ange hur ofta den personliga återställnings nyckeln för en enhet ska roteras. Du kan välja standardvärdet **inte konfigurerad**eller värdet **1** till **12** månader.  

  - **Inaktivera prompt vid utloggning**  
    Förhindra att användaren uppmanas att aktivera FileVault när de loggar ut.  När inställningen är aktive rad är uppmaningen vid utloggning inaktive rad och användaren tillfrågas när de loggar in.  
    - **Inte konfigurerat**  
    - **Aktivera** – inaktivera prompten vid utloggning.

    **Standard**: Inte konfigurerat  

     > [!IMPORTANT]  
     > Det finns ett känt problem när inställningen **inaktivera fråga vid utloggning** är inställd på *Aktivera*. När inställningen är *aktive*rad måste inställningen för **antal gånger som ska kringgås** anges till ett värde och får inte anges som *ej konfigurerad*. Om inställningen är *inte konfigurerad*, Miss lyckas profilen på enheten. I det här scenariot rapporterar enheten att det är en **Sammanfattning av profil tillstånd** som **fel** utan ytterligare information.
     > 
     > När **inaktivera prompt vid utloggning** är inställt på *inte konfigurerad*, kan **antalet tillåtna gånger att kringgå** *inte konfigureras* eller ha ett värde.  
     > 
     > Problemet kommer att åtgärdas i en kommande uppdatering. 

  - **Antal gånger som tillåts kringgås**  
  Ange antalet gånger som en användare kan ignorera prompter för att aktivera FileVault innan FileVault krävs för att användaren ska kunna logga in.  

    - **Inte konfigurerad** – kryptering på enheten krävs innan nästa inloggning tillåts.  
    - **1** till **10** – Tillåt att en användare ignorerar uppvarningen från 1 till 10 gånger innan den kräver kryptering på enheten.  
    - **Ingen gräns, fråga alltid** – användaren uppmanas att aktivera FileVault men kryptering krävs aldrig.  
 
    **Standard**: Inte konfigurerat  


