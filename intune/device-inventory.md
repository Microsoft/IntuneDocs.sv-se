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
ms.openlocfilehash: f66c0695c7e3d1f4bb7a5ca3abceeb13f6af41f2
ms.sourcegitcommit: 3c4ea8d6809a63042705b5ed4f25ba80f522070e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/11/2018
ms.locfileid: "34051614"
---
# <a name="see-device-details-in-intune"></a>Visa enhetsinformation i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Funktionen **Enheter** tillhandahåller ytterligare information om de enheter som du hanterar, inklusive deras maskinvara och installerade appar.

Den här artikeln beskriver hur du visar alla dina enheter och deras egenskaper i Azure Portal.

## <a name="view-the-device-details"></a>Visa enhetsinformation

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** > **Alla enheter** > välj en av enheterna i listan för att öppna informationen:

   - I **Översikt** visas namnet på enheten och några viktiga egenskaper, bland annat om det är en BYOD-enhet (Bring Your Own Device), när den checkades in och mycket mer. Välj **Mer** för att också:
     - Ta bort företagsdata
     - Ta bort enheten
     - Fjärrlåsa enheten
     - Radera
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

## <a name="next-steps"></a>Nästa steg
Se vad mer du kan göra för att [hantera dina enheter](device-management.md) med Intune.