---
title: Granskningsloggar för Microsoft Intune-aktiviteter
description: Lär dig att gå igenom granskningsloggar som registrerar Microsoft Intune-aktiviteter.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98540af0f0b7d259973d1a7e873c68fc64f488d1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460690"
---
# <a name="audit-logs-for-intune-activities"></a>Granskningsloggar för Intune-aktiviteter
Granskningsloggar ger dig en post med aktiviteter som genererar en ändring i Microsoft Intune. Skapa, uppdatera (redigera), ta bort, och tilldela åtgärder eller uppgifter för fjärrhantering, generera granskningshändelser som du kan granska. Du kan gå igenom granskningsloggar för de flesta arbetsbelastningar i Intune. Granskning är aktiverat som standard för alla kunder och kan inte inaktiveras. Granskningshändelserna började registreras i funktionen i december 2017 och tidigare händelser är inte tillgängliga.

## <a name="who-can-access-the-data"></a>Vem som kan komma åt data?
Användare med följande behörigheter kan gå igenom granskningsloggar:
- Global administratör
- Intune Service-administratör
- Administratörer som har tilldelats en roll för Intune med behörighet **Granska data** - **Läs**

## <a name="audit-logs-for-intune-workloads"></a>Granskningsloggar för arbetsbelastningar för Intune
Du kan gå igenom granskningsloggar i övervakningsgruppen för varje arbetsbelastning i Intune.  
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. I fönstret **Intune** väljer du den arbetsbelastning som du vill ska gå igenom granskningsloggar, till exempel **Enheter**.
4. I gruppen **Övervakning** för arbetsbelastningen, väljer du **Granskningsloggar**.

## <a name="review-audit-events"></a>Gå igenom granskningshändelser
![Granskningsloggar](./media/monitor-audit-logs.png "Granskningsloggar")

En granskningslogg har en standardlistvy som visar följande objekt:    

- datum och tid för händelsen
- Initierad av (aktör)
- Programnamn
- Aktivitet
- Mål
- Kategori
- Status

Genom att välja ett objekt i listvyn kan hämta du alla information om det.

![Granskningsloggar](./media/monitor-audit-log-detail.png "Granskningsloggar")

> [!Note]    
> Avsnittet **Initierat av (aktör)** i informationen om granskningsloggen innehåller information om vem som utförde aktiviteten och varifrån den utfördes. Om du utför aktiviteten i Intune i Azure-portalen, visar t.ex. **Program** alltid **Microsoft Intune-portaltillägg** och **Program-ID** använder alltid samma GUID. 
>    
> Avsnittet **Mål** kan ange flera mål och de egenskaper som har ändrats.  


## <a name="filter-audit-events"></a>Filtrera granskningshändelser
Varje arbetsbelastning har ett menyalternativ som i förväg filtrerar kategorin för granskningshändelser som är associerade med detta fönster. Med ett separat filteralternativ kan du ändra till olika kategorier och information om händelseåtgärd inom denna kategori. Du kan söka med UPN (till exempel den användare som utförde åtgärden). Ett filter för datumintervall ger alternativ för 24 timmar, 7 dagar eller 30 dagar. Som standard visas de senaste 30 dagarna av granskningshändelserna.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Använd Graph API för att hämta granskningshändelser
Mer information om hur du använder Graph API för att hämta upp till ett års granskningshändelser finns i [Lista över auditEvents](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list).
