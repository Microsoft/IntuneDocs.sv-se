---
title: Visa och åtgärda personliga data
description: Lär dig hur du visar och korrigerar personliga data.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b9efb60d169ba6f88b4765d3fc651f3a0596b230
ms.sourcegitcommit: 378474debffbc85010c54e20151d81b59b7a7828
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028587"
---
# <a name="view-and-correct-personal-data"></a>Visa och åtgärda personliga data

Intune-administratörer kan visa vissa personliga data baserat på deras åtkomstbehörigheter, men endast slutanvändare kan ändra sin enhets personliga data.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>Visa personliga data

Administratörer kan se slutanvändarnas personliga information i olika blad i Intune-gränssnittet. Följande artiklar förklarar vilken information administratörer har och inte har åtkomst till:
- [Visa enhetsinformation](device-inventory.md) i Intune förklarar hur du kan granska information om en slutanvändares enhet.
- [Övervaka appinformation och tilldelningar](apps-monitor.md) förklarar hur du kan se information om appar som installerats på en slutanvändarens enhet.
- I artikeln [Vilken information kan företaget se när jag registrerar min enhet?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) får slutanvändarna en lista över data som deras företag kan och inte kan se. Det rekommenderas att du tydligt informerar användarna om vilka typer av data du samlar in och varför du samlar in dem. Den här artikeln kan bli det första steget för att skapa en sådan transparens.

### <a name="who-can-view-the-data"></a>Vem kan visa data?

Microsoft använder noggranna kontroller för att styra åtkomst till kunddata, beviljar den lägsta åtkomstnivå som krävs för att slutföra nyckeluppgifter och återkallar åtkomst när den inte längre behövs. 

Du kan skydda och styra åtkomsten till slutanvändarens personliga data med hjälp av rollbaserad administrationskontroll (RBAC). Mer information finns i [RBAC med Microsoft Intune](role-based-access-control.md).

Du kan lära dig mer om Microsofts datapraxis genom att läsa Villkor för Online Services och [Sekretesspolicy för Microsoft Online Services](http://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409). 

## <a name="correct-end-user-personal-data"></a>Korrigera slutanvändares personliga data

Administratörer kan inte uppdatera enhets- eller appspecifik information. Om en slutanvändare vill korrigera personliga data (till exempel enhetsnamnet) måste användaren göra det direkt på sin enhet. Sådana ändringar synkroniseras nästa gång användaren ansluter till Intune.


## <a name="next-steps"></a>Nästa steg

Lär dig hur du [granskar, exporterar och tar bort](privacy-data-audit-export-delete.md) personliga data i Intune.