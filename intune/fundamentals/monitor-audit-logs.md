---
title: Granskningsändringar och händelser i Microsoft Intune – Azure | Microsoft Docs
description: Lär dig att gå igenom granskningsloggar som registrerar Microsoft Intune-aktiviteter.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d999603abc539fda4d152d15dd1ab965c465f39e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736305"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Använd granskningsloggar för att spåra och övervaka händelser i Microsoft Intune

Granskningsloggar innehåller en post med aktiviteter som genererar en ändring i Microsoft Intune. Åtgärder för att skapa, uppdatera (redigera), ta bort och tilldela samt fjärråtgärder skapar granskningshändelser som administratörer kan granska för de flesta Intune-arbetsbelastningar. Som standard är granskning aktiverat för alla kunder. Det kan inte inaktiveras.

> [!NOTE]
> Granskningshändelser började registreras i lanseringen från december 2017. Tidigare händelser är inte tillgängliga.

## <a name="who-can-access-the-data"></a>Vem som kan komma åt data?

Användare med följande behörigheter kan gå igenom granskningsloggar:

- Global administratör
- Intune Service-administratör
- Administratörer som har tilldelats en roll för Intune med behörighet **Granska data** - **Läs**

## <a name="audit-logs-for-intune-workloads"></a>Granskningsloggar för arbetsbelastningar för Intune

Du kan gå igenom granskningsloggar i övervakningsgruppen för varje arbetsbelastning i Intune:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj den arbetsbelastning som du vill granska granskningsloggar för. Välj exempelvis **Enheter**.
3. Under **Övervakning** väljer du **Granskningsloggar**.

## <a name="route-logs-to-azure-monitor"></a>Dirigera loggar till Azure Monitor

Granskningsloggar och arbetsloggar kan även dirigeras till Azure Monitor. I **Granskningsloggar** väljer du **Exportera datainställningar**:

![Exportera loggdata till Azure Monitor genom att Exportera datainställningar i Intune](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

Mer information om den här funktionen finns i [Skicka loggdata till lagring, händelsehubbar eller logganalys](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Gå igenom granskningshändelser

![Välj granskningsloggar i Intune för att se åtgärder och datum när händelser inträffade](./media/monitor-audit-logs/monitor-audit-logs.png "Granskningsloggar")

En granskningslogg har en standardlistvy som visar följande objekt:

- Datum och tid för händelsen
- Initierad av (aktör)
- Programnamn
- Aktivitet
- Mål
- Kategori
- Status

Om du vill se mer specifik information om en händelse väljer du ett objekt i listan:

![Få mer specifik information om vem som gjorde vad i granskningsloggar i Intune](./media/monitor-audit-logs/monitor-audit-log-detail.png "Information om granskningslogg")

> [!NOTE]
> **Initierad av (aktör)** innehåller information om vem som körde uppgiften och var den kördes. Om du t.ex. utför aktiviteten i Intune i Azure Portal, visar **Program** alltid **Microsoft Intune-portaltillägg** och **Program-ID** använder alltid samma GUID.
> 
> Avsnittet **Mål** anger flera mål och de egenskaper som har ändrats.  

## <a name="filter-audit-events"></a>Filtrera granskningshändelser

Varje arbetsbelastning har ett menyalternativ som i förväg filtrerar kategorin för granskningshändelser som är associerade med detta fönster. Med ett separat filteralternativ kan du ändra till olika kategorier och information om händelseåtgärd inom denna kategori. Du kan söka med UPN, till exempel den användare som utförde åtgärden. Ett filter för datumintervall ger alternativ för 24 timmar, 7 dagar eller 30 dagar. Som standard visas de senaste 30 dagarna av granskningshändelserna.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Använd Graph API för att hämta granskningshändelser

Mer information om hur du använder Graph API för att hämta upp till ett års granskningshändelser finns i [Lista över auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Nästa steg

[Skicka data till lagring, händelsehubbar eller logganalys](review-logs-using-azure-monitor.md).

[Granska loggarna för klientappskydd](../apps/app-protection-policy-settings-log.md).
