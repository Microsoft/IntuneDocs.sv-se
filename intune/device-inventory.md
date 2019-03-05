---
title: Visa enhetsinformation med Microsoft Intune – Azure | Microsoft Docs
description: Visa information om din enhet, till exempel operativsystem, lagringsutrymme, tillverkare och modell. Hämta en lista över installerade appar, kontrollera efterlevnadsprinciper och konfigurera TeamViewer med Microsoft Intune i Azure. Det fungerar ungefär som när du visar en inventering av de enheter som du hanterar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76b125c216cd3767df0cb6a374d0fcbeeade794a
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232598"
---
# <a name="see-device-details-in-intune"></a>Visa enhetsinformation i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Funktionen **Enheter** tillhandahåller ytterligare information om de enheter som du hanterar, inklusive deras maskinvara och installerade appar.

Den här artikeln beskriver hur du visar alla dina enheter och deras egenskaper i Azure Portal.

## <a name="view-the-device-details"></a>Visa enhetsinformation

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter** > välj en av enheterna i listan för att öppna informationen:

   - I **Översikt** visas namnet på enheten och några viktiga egenskaper, bland annat om det är en BYOD-enhet (Bring Your Own Device), när den checkades in och mycket mer. Du kan utföra följande åtgärder på enheten:
      - [Pensionera](devices-wipe.md#retire)
        - [Rensning](devices-wipe.md#wipe)
        - [Fjärrlåsning](device-remote-lock.md)
        - [Synkronisera enhet](device-sync.md)
        - [Återställ lösenord](device-passcode-reset.md)
        - [Starta om](device-restart.md) (Endast Windows)
        - [Börja om på nytt](device-fresh-start.md) (Endast Windows)
     - Starta en fjärrhjälpssession
   - Använd **Egenskaper** för att tilldela en [enhetskategori som du skapar](device-group-mapping.md), samt för att ändra ägarskap för enheten till en personlig enhet eller företagets enhet.
   - **Maskinvara** innehåller information om enheten, bland annat enhets-ID, operativsystem och version, lagringsutrymme, modell och tillverkare, inställningar för villkorlig åtkomst.
   - **Identifierade appar** visar alla installerade appar på enheten som Intune hittat och deras versioner. Du kan också **Exportera** applistan till en .csv-fil. Den här listan uppdateras var sjunde dag.
   - **Enhetsefterlevnad** visar alla tilldelade efterlevnadsprinciper, samt om enheten är kompatibel eller inkompatibel.
   - **Enhetskonfiguration** visar alla enhetskonfigurationsprinciper som är tilldelade till enheten, samt om principen har lyckats eller misslyckats.

Intune samlar endast in en applista från företagsägda enheter. Appar på personliga enheter kontrolleras inte. För datorer med Windows 10 visas bara moderna appar för företagsägda enheter. Intune samlar inte in information om Win32-appar på enheten. Alla appar kan inte samlas in, beroende på vilken operatör som används för enheterna.

|Plattform|För privatägda enheter|För företagsägda enheter|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (utan Configuration Manager-klienten)|Endast hanterade appar|Endast hanterade appar|
|Windows 8.1 (utan Configuration Manager-klienten)|Endast hanterade appar|Endast hanterade appar|  
|Windows Phone 8|Endast hanterade appar|Endast hanterade appar|  
|Windows RT|Endast hanterade appar|Endast hanterade appar|  
|iOS|Endast hanterade appar|Alla appar som är installerade på enheten|
|macOS|Alla appar som är installerade på enheten|Alla appar som är installerade på enheten|  
|Android|Endast hanterade appar|Alla appar som är installerade på enheten|  
|Android enterprise|Endast hanterade appar|Endast appar som har installerats i arbetsprofilen|  

## <a name="hardware-device-details"></a>Information om maskinvaruenheten
Eventuellt samlas inte all information in, beroende på vilken operatör enheterna använder

|Information|Beskrivning|Plattform| 
|--------------|----------------------|----|  
|Namn|Namnet på enheten.|Windows, iOS|
|Hanteringsnamn|Enhetsnamnet används endast i konsolen. Även om du ändrar det här namnet ändras inte namnet på enheten.|Windows, iOS|
|UDID|Enhetens unika enhets-ID.|Windows, iOS|
|ID för Intune-enhet|Ett GUID som unikt identifierar den här enheten.|Windows, iOS|
|Serienummer|Enhetens serienummer från tillverkaren.|Windows, iOS|
|Delad enhet|Enheten delas av flera användare om inställningen är **Ja**.|Windows, iOS|
|Användargodkänd registrering|Enheten har användargodkänd registrering som gör att administratörer kan hantera vissa säkerhetsinställningar på enheten om inställningen är **Ja**.|Windows, iOS|
|Operativsystem|Vilken typ av operativsystem som används på enheten.|Windows, iOS|
|Operativsystemversion|Enhetens operativsystemversion.|Windows, iOS|
|Operativsystemets språk|Språket som är inställt på enhetens operativsystem.|Windows, iOS|
|Totalt lagringsutrymme|Det totala lagringsutrymmet på enheten (i gigabyte).|Windows, iOS|
|Ledigt lagringsutrymme|Det oanvända lagringsutrymmet på enheten (i gigabyte).|Windows, iOS|
|IMEI|Enhetens IMEI (International Mobile Equipment Identity).|Windows, iOS, Android|
|MEID|Enhetens mobilutrustningsnummer.|Windows, iOS, Android|
|Tillverkare|Enhetstillverkaren.|Windows, iOS, Android|
|Modell|Enhetsmodellen.|Windows, iOS, Android|
|Telefonnummer|Telefonnumret som har tilldelats enheten.|Windows, iOS, Android|
|Abonnentens operatör|Enhetens mobiloperatör.|Windows, iOS, Android|
|Mobilteknik|Radiosystem som används av enheten.|Windows, iOS, Android|
|Wi-Fi MAC|Enhetens MAC-adress.|Windows, iOS, Android|
|ICCID|Det integrerade kretskort-ID:t som är ett unikt ID-nummer för ett SIM-kort.|Windows, iOS, Android|
|Registreringsdatum|Datum och tid då enheten registrerades i Intune.|Windows, iOS, Android|
|Senaste kontakt|Datum och tid då enheten senast var i kontakt med Intune.|Windows, iOS, Android|
|Kod för att kringgå aktiveringslås|Koden som kan användas för att förbikoppla aktiveringslåset.|Windows, iOS, Android|
|Azure AD-registrerad|Om inställningen är **Ja** är enheten registrerad i Azure Directory.|Windows, iOS, Android|
|Efterlevnad|Enhetens kompatibilitetstillstånd.|Windows, iOS, Android|
|EAS-aktiverad|Om inställningen är **Ja** så är enheten synkroniserad med en Exchange-postlåda.|Windows, iOS, Android|
|Aktiverings-ID för EAS|Enhetens identifierare för Exchange ActiveSync.|Windows, iOS, Android|
|Övervakas|Om inställningen är **Ja** så har administratörer utökad kontroll över enheten.|Windows, iOS, Android|
|Krypterad|Om inställningen är **Ja** så krypteras de data som lagras på enheten.|Windows, iOS, Android|



## <a name="next-steps"></a>Nästa steg
Se vad mer du kan göra för att [hantera dina enheter](device-management.md) med Intune.
