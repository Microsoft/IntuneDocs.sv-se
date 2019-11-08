---
title: Inställningar för säkerhets bas linje i Intune för Microsoft Edge
titleSuffix: Microsoft Intune
description: Inställningar för säkerhets bas linje som stöds av Intune för att hantera Microsoft Edge-webbläsare
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/30/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8f4e56340d871ea5e0bcec7e541a418c32d021d0
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415652"
---
# <a name="microsoft-edge-baseline-settings-for-intune"></a>Microsoft Edges bas linje inställningar för Intune

Visa Microsoft Edge-webbläsarens bas linje inställningar som stöds av Microsoft Intune. Standardinställningarna för Microsoft Edge-standardvärden representerar den rekommenderade konfigurationen för Microsoft Edge-webbläsare och kanske inte matchar standardvärdena för andra säkerhets bas linjer.

> [!NOTE]
> Microsoft Edge-bas linjen är i en offentlig för hands version. 

## <a name="microsoft-edge"></a>Microsoft Edge

- **Förhindra att Microsoft Defender SmartScreen-meddelanden för webbplatser kringgås**  
  **Standard**: Aktiverat  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

  Med den här princip inställningen kan du bestämma om användarna ska kunna åsidosätta Microsoft Defender SmartScreen-varningar om potentiellt skadliga webbplatser. 
  - Om du aktiverar den här inställningen kan användarna inte ignorera Microsoft Defender SmartScreen-varningar och de blockeras från att fortsätta till webbplatsen. 
  - Om du inaktiverar eller inte konfigurerar den här inställningen kan användare Ignorera Microsoft Defender SmartScreen-varningar och fortsätta till platsen.

- **Lägsta SSL-version som är aktive rad**  
  **Standard**: Aktiverat  

  Ange en lägsta version av SSL som stöds. Om du anger att den här principen *inte har kon figurer ATS*använder Microsoft Edge en minimal standard version av *TLS 1,0*. När inställningen *är aktive rad*kan du välja en lägsta version med följande värden:

  - TLS 1.0
  - TLS 1.1
  - TLS 1.2

  - **Lägsta SSL-version som är aktive rad**  
    **Standard**: TLS 1,2

- **Förhindra att SmartScreen-varningar från Microsoft Defender ignoreras om hämtningar**  
  **Standard**: Aktiverat  
  Microsoft Edge CSP: [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)  

  Med den här principen kan du avgöra om användare kan åsidosätta Microsoft Defender SmartScreen-varningar om overifierade hämtningar.
  - Om du aktiverar den här principen kan inte användare i din organisation ignorera SmartScreen-varningar från Microsoft Defender, och de hindras från att slutföra de overifierade hämtningarna.
  - Om du inaktiverar eller inte konfigurerar den här principen kan användare Ignorera Microsoft Defender SmartScreen-varningar och slutföra overifierade hämtningar.

- **Tillåt att användare fortsätter från sidan med SSL-varning**  
  **Standard**: Inaktiverat  
  Microsoft Edge CSP: [Browser/PreventCertErrorOverrides](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventcerterroroverrides)  

  Microsoft Edge visar en varnings sida när användare besöker webbplatser som har SSL-fel. Om du anger att den här principen *är aktive rad* eller *inte konfigurerad*kan användarna klicka på dessa varnings sidor. När den här principen är *inaktive rad*blockeras användarna från att klicka via en varnings sida. 

- **Standard inställning för Adobe Flash**  
  **Standard**: Aktiverat  
  Microsoft Edge CSP: [Browser/AllowFlash](https://docs.microsoft.coms/windows/client-management/mdm/policy-csp-browser#browser-allowflash)och [Browser/AllowFlashClickToRun](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowflashclicktorun)  

  Avgör om webbplatser som inte omfattas av "PluginsAllowedForUrls" eller "PluginsBlockedForUrls" kan köra Adobe Flash-plugin-programmet automatiskt. 

  - Välj "BlockPlugins" om du vill blockera Adobe Flash på alla webbplatser
  - Välj "ClickToPlay" om du vill låta Adobe Flash köras, men användaren måste klicka på plats hållaren för att starta den.
  
   I alla fall prioriteras principerna "PluginsAllowedForUrls" och "PluginsBlockedForUrls" DefaultPluginsSetting ". Automatisk uppspelning tillåts endast för domäner som uttryckligen anges i "PluginsAllowedForUrls"-principen. 
   Om du vill aktivera automatisk uppspelning för alla platser bör du överväga att lägga till http://* och https://* i den här listan. 
   
   - Om du anger att den här principen *inte är konfigurerad*, kan användaren ändra den här inställningen manuellt. * 2 = blockera Adobe Flash-plugin-programmet * 3 = Klicka för att spela upp det tidigare alternativet "1" Tillåt-alla, men den här funktionen hanteras nu bara av "PluginsAllowedForUrls"-principen. Befintliga principer som använder ' 1 ' kommer att köras i Klicka-till-uppspelning-läge.  
 
  - **Standard inställning för Adobe Flash**  
    **Standard**: blockera Adobe Flash-plugin-programmet

- **Aktivera webbplats isolering för varje plats**  
  **Standard**: Aktiverat  

  SitePerProcess-principen kan användas för att hindra användare från att väljer av standard beteendet att isolera alla platser. Du kan också använda IsolateOrigins-principen för att isolera ytterligare, mer detaljerade ursprung.

  - När den här principen är *aktive rad*kan användarna inte välja standard beteendet där varje plats körs i en egen process. 
  - Om du använder *inaktiverat* eller *inte konfigurerat*kan en användare välja att isolera plats. (Till exempel med hjälp av posten "inaktivera plats isolering" i edge://flags.) Om principen inaktive ras eller om du inte konfigurerar principen stängs inte plats isolering.

- **Autentiseringsscheman som stöds**  
  **Standard**: Aktiverat  

  Anger vilka HTTP-autentiseringsscheman som stöds. Du kan konfigurera principen med hjälp av följande värden: Basic, Digest, NTLM och Negotiate. Separera flera värden med kommatecken. Om du inte konfigurerar den här principen används alla fyra scheman.
 
  - **Autentiseringsscheman som stöds**  
    Välj bland följande alternativ: 
    - Grundläggande
    - Sammandrag
    - NTLM *(markerat som standard)*
    - Förhandla *(markerad som standard)*

- **Aktivera att spara lösen ord i lösen ords hanteraren**  
  **Standard**: Inaktiverat  
  Microsoft Edge CSP: [Browser/AllowPasswordManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)  

  Aktivera Microsoft Edge för att spara användar lösen ord. 
  - Om du aktiverar den här principen kan användarna spara sina lösen ord i Microsoft Edge. Nästa gång de besöker webbplatsen kommer Microsoft Edge att ange lösen ordet automatiskt. 
  - Om du inaktiverar den här principen kan användarna inte spara nya lösen ord, men de kan fortfarande använda tidigare sparade lösen ord. 
  
  När du ställer in den här principen på antingen *aktive rad* eller *inaktive*rad kan användarna inte ändra eller åsidosätta den här principen i Microsoft Edge. 
  
  Om du väljer att *inte konfigurera*kan användarna spara lösen ord, samt inaktivera den här funktionen.

- **Styra vilka tillägg som inte kan installeras**  
  **Standard**: Aktiverat  

  Lista de speciella tillägg som användarna inte kan installera i Microsoft Edge. När du distribuerar den här principen inaktive ras alla tillägg i den här listan som tidigare har installerats och användaren kan inte aktivera dem. Om du tar bort ett objekt från listan över blockerade tillägg, aktive ras tillägget automatiskt på nytt var det har installerats.
  
  Använd **\*** för att blockera alla tillägg som inte uttryckligen anges i listan över tillåtna. Om den här principen är inställd på *inte konfigurerad*kan användarna installera alla tillägg i Microsoft Edge. 
  
  Exempel värde: extension_id1 extension_id2.  
  <br>
  - **Tilläggs-ID: n användaren bör förhindras från att installeras (eller * för alla)**  
    Välj **Lägg till** och ange ytterligare tillägg. **\*** är valt som standard.

- **Konfigurera Microsoft Defender SmartScreen**  
  **Standard**: Aktiverat  
  Microsoft Edge CSP: [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)  
  
  Med den här princip inställningen kan du konfigurera om du vill aktivera Microsoft Defender SmartScreen. Microsoft Defender SmartScreen tillhandahåller varnings meddelanden som hjälper dig att skydda dina användare från potentiella phishing-bedrägerier och skadlig program vara. 
  
  - Som standard är Microsoft Defender SmartScreen aktiverat. Om du aktiverar den här inställningen aktive ras Microsoft Defender SmartScreen och användarna kan inte inaktivera det.
  - Om du inaktiverar den här inställningen inaktive ras Microsoft Defender SmartScreen och användarna kan inte aktivera den. 
  - När inställningen *inte är konfigurerad*kan användarna välja om de vill använda Microsoft Defender SmartScreen. 
  
  Den här principen är endast tillgänglig på Windows-instanser som är anslutna till en Microsoft Active Director-domän, eller på Windows 10 Pro-eller Enterprise-instanser som har registrerats för enhets hantering.

- **Tillåt interna meddelande värdar på användar nivå (installeras utan administratörs behörighet)**  
  **Standard**: Inaktiverat  

  Aktiverar installation på användar nivå av interna meddelande värdar. 
  - Om du inaktiverar den här principen används endast interna meddelande värdar som är installerade på system nivå i Microsoft Edge. Om du inte konfigurerar den här principen kommer Microsoft Edge att tillåta användning av interna meddelande värdar på användar nivå.

## <a name="next-steps"></a>Nästa steg

[Använda säkerhets bas linjer i Intune](security-baselines.md)
