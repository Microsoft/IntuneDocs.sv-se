---
title: Visa enhetsinformation med Microsoft Intune – Azure | Microsoft Docs
description: Visa information om din enhet, till exempel operativsystem, lagringsutrymme, tillverkare och modell. Hämta en lista över installerade appar, kontrollera efterlevnadsprinciper och konfigurera TeamViewer med Microsoft Intune i Azure. Det fungerar ungefär som när du visar en inventering av de enheter som du hanterar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a658182800f480f27097e078f28adc95c35aa3ea
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313186"
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
   - **Identifierade appar** visar alla installerade appar på enheten som Intune hittat och deras versioner. Du kan också **Exportera** applistan till en .csv-fil.
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

## <a name="hardware-device-details"></a>Information om maskinvaruenheten

### <a name="windows-and-ios-device-details"></a>Windows- och iOS-enhetsinformation:
|Detalj|Description|  
|--------------|----------------------|  
|Namn|Namnet på enheten.|
|Hanteringsnamn|Enhetsnamnet används endast i konsolen. Även om du ändrar det här namnet ändras inte namnet på enheten.|
|UDID|Enhetens unika enhets-ID.|
|ID för Intune-enhet|Ett GUID som unikt identifierar den här enheten.|
|Serienummer|Enhetens serienummer från tillverkaren.|
|Delad enhet|Enheten delas av flera användare om inställningen är **Ja**.|
|Användargodkänd registrering|Enheten har användargodkänd registrering som gör att administratörer kan hantera vissa säkerhetsinställningar på enheten om inställningen är **Ja**.|
|Operativsystem|Vilken typ av operativsystem som används på enheten.|
|Operativsystemversion|Enhetens operativsystemversion.|
|Operativsystemets språk|Språket som är inställt på enhetens operativsystem.|
|Totalt lagringsutrymme|Det totala lagringsutrymmet på enheten (i gigabyte).|
|Ledigt lagringsutrymme|Det oanvända lagringsutrymmet på enheten (i gigabyte).|


### <a name="windows-ios-and-macos-device-details"></a>Windows, iOS och macOS-enhetsinformation
|Detalj|Description|  
|--------------|----------------------|  
|IMEI|Enhetens IMEI (International Mobile Equipment Identity).|
|MEID|Enhetens mobilutrustningsnummer.|
|Tillverkare|Enhetstillverkaren.|
|Modell|Enhetsmodellen.|
|Telefonnummer|Telefonnumret som har tilldelats enheten.|
|Abonnentens operatör|Enhetens mobiloperatör.|
|Mobilteknik|Radiosystem som används av enheten.|
|Wi-Fi MAC|Enhetens MAC-adress.|
|ICCID|Det integrerade kretskort-ID:t som är ett unikt ID-nummer för ett SIM-kort.|
|Registreringsdatum|Datum och tid då enheten registrerades i Intune.|
|Senaste kontakt|Datum och tid då enheten senast var i kontakt med Intune.|
|Kod för att kringgå aktiveringslås|Koden som kan användas för att förbikoppla aktiveringslåset.|
|Azure AD-registrerad|Om inställningen är **Ja** är enheten registrerad i Azure Directory.|
|Efterlevnad|Enhetens kompatibilitetstillstånd.|
|EAS-aktiverad|Om inställningen är **Ja** så är enheten synkroniserad med en Exchange-postlåda.|
|Aktiverings-ID för EAS|Enhetens identifierare för Exchange ActiveSync.|
|Övervakas|Om inställningen är **Ja** så har administratörer utökad kontroll över enheten.|
|Krypterad|Om inställningen är **Ja** så krypteras de data som lagras på enheten.|



## <a name="next-steps"></a>Nästa steg
Se vad mer du kan göra för att [hantera dina enheter](device-management.md) med Intune.