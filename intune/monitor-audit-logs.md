---
title: Granska ändringar och händelser i Microsoft Intune – Azure | Microsoft Docs
description: Lär dig att gå igenom granskningsloggar som registrerar Microsoft Intune-aktiviteter.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394909"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>Använd granskningsloggar för att spåra och övervaka händelser i Microsoft Intune

Granskningsloggar innehåller en post med aktiviteter som genererar en ändring i Microsoft Intune. Skapa, uppdatera (redigera), ta bort, tilldela och åtgärder för fjärransluten skapa granskningshändelser som administratörer kan granska för de flesta arbetsbelastningar för Intune. Granskning är aktiverat som standard för alla kunder. Det kan inte inaktiveras.

> [!NOTE]
> Granskningshändelser igång inspelning på funktionsutgåva December 2017. Tidigare händelser är inte tillgängliga.

## <a name="who-can-access-the-data"></a>Vem som kan komma åt data?

Användare med följande behörigheter kan gå igenom granskningsloggar:

- Global administratör
- Intune Service-administratör
- Administratörer som har tilldelats en roll för Intune med behörighet **Granska data** - **Läs**

## <a name="audit-logs-for-intune-workloads"></a>Granskningsloggar för arbetsbelastningar för Intune

Du kan gå igenom granskningsloggar i övervakningsgruppen för varje arbetsbelastning i Intune:

1. I [Azure-portalen](https://portal.azure.com/) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Väljer du den arbetsbelastning som du vill gå igenom granskningsloggar. Välj exempelvis **enheter**.
3. Under **övervakning**, Välj **granskningsloggar**.

## <a name="route-logs-to-azure-monitor"></a>Dirigera loggar till Azure Monitor

Gransknings- och driftloggar kan också dirigeras till Azure Monitor. I **granskningsloggar**väljer **Exportera inställningar**:

![Exportera loggdata till Azure monitor genom att välja inställningar för Export i Intune](./media/audit-logs-export-data-settings.png)

Mer information om den här funktionen finns i [Skicka loggdata till lagring, händelsehubbar eller logganalys](review-logs-using-azure-monitor.md).

## <a name="review-audit-events"></a>Gå igenom granskningshändelser

![Välj granskningsloggar i Intune för att se åtgärder och datum när händelserna inträffade](./media/monitor-audit-logs.png "granskningsloggar")

En granskningslogg har en standardlistvy som visar följande objekt:

- Datum och tid för händelsen
- Initierad av (aktör)
- Programnamn
- Aktivitet
- Mål
- Kategori
- Status

Markera ett objekt i listan om du vill se mer detaljerad information om en händelse:

![Få mer specifik information om vem gjorde vad i audit loggar i Intune](./media/monitor-audit-log-detail.png "granskningsloggen")

> [!NOTE]
> **Initierad av (aktör)** innehåller information om vem som körde aktiviteten och där den kördes. Om du t.ex. utför aktiviteten i Intune i Azure Portal, visar **Program** alltid **Microsoft Intune-portaltillägg** och **Program-ID** använder alltid samma GUID.
> 
> Avsnittet **Mål** anger flera mål och de egenskaper som har ändrats.  

## <a name="filter-audit-events"></a>Filtrera granskningshändelser

Varje arbetsbelastning har ett menyalternativ som i förväg filtrerar kategorin för granskningshändelser som är associerade med detta fönster. Med ett separat filteralternativ kan du ändra till olika kategorier och information om händelseåtgärd inom denna kategori. Du kan söka efter UPN, till exempel att användaren som utförde åtgärden. Ett filter för datumintervall ger alternativ för 24 timmar, 7 dagar eller 30 dagar. Som standard visas de senaste 30 dagarna av granskningshändelserna.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Använd Graph API för att hämta granskningshändelser

Mer information om hur du använder graph API för att få upp till ett års granskningshändelser finns i [lista över auditEvents](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0).

## <a name="next-steps"></a>Nästa steg

[Skicka data till lagring, event hubs eller logganalys](review-logs-using-azure-monitor.md).

[Granska loggarna för klientappskydd](app-protection-policy-settings-log.md).
