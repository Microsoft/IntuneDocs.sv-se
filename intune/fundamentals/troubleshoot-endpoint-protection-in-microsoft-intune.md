---
title: Vanliga meddelanden för slutpunktsskydd i Microsoft Intune – Azure | Microsoft Docs
description: Se vanliga meddelanden och möjliga lösningar när du använder och felsöker Endpoint Protection och Microsoft Defender i Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 819586a923f5c0f3a81a6d59c4a3895898182f6b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059163"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problem med Endpoint Protection och möjliga lösningar i Microsoft Intune

Den här artikeln beskriver artikellistorna och beskriver potentiella orsaker och lösningar för några fel och varningar. Använd informationen för att hjälpa dig lösa problem när du använder Endpoint Protection.

## <a name="microsoft-defender-error-codes"></a>Fel koder för Microsoft Defender

Granska händelseloggar och felkoder för att [felsöka problem med Microsoft Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Vanliga Intune-fel och möjliga lösningar

### <a name="endpoint-protection-engine-unavailable"></a>Endpoint Protection-motorn är inte tillgänglig

**Potentiell orsak**: Motorn för Endpoint Protection i Intune är skadad eller borttagen.

**Möjliga lösningar**:

- Om Endpoint Protection är skadat eller inte uppdaterat, uppdatera eller installera om programmet.
- Framtvinga en omedelbar uppdatering. I Endpoint Protection-klientprogrammet (eventuellt i aktivitetsfältet), väljer du **Uppdatera**.
- I Kontrollpanelen > Program, väljer du **Microsoft Intune Endpoint Protection Agent**. Avinstallera programmet.
- Microsoft Online Management Update Manager identifierar programmet som saknas under nästa uppdateringssynkronisering och installerar om det på den schemalagda installationstiden.

### <a name="features-are-disabled"></a>Funktioner är inaktiverade

Du kan få ett meddelande om att vissa funktioner är inaktiverade. Du får de här meddelandena om Intune Endpoint Protection eller Microsoft Defender har inaktiverats av en administratör med en konfigurationsprofil. Eller inaktiveras av en slutanvändare på enheten. Möjliga meddelanden:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Möjliga lösningar**: aktivera dessa funktioner. Anvisningar finns i:

- [Lägg till Endpoint Protection-inställningar](../protect/endpoint-protection-configure.md)
- [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [Slutanvändare: aktivera realtidsskydd om du vill komma åt företagsresurser](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>Definitionerna för skadlig kod är inaktuella

Den här statusen visas när definitionerna för skadlig kod på enheten är inaktuella med 14 dagar eller mer. Meddelandet kan till exempel indikera om enheten är frånkopplad från Internet eller om definitionerna för skadlig kod är inaktuella.

[Möjliga lösningar](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus): om definitionerna för skadlig kod är inaktuella, kan du uppdatera definitionerna med **Microsoft Defender Antivirus**.

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Det är dags för Fullständig sökning eller Snabbsökning

En fullständig sökning eller Snabbsökning har inte slutförts de senaste 14 dagarna. Det här scenariot kan inträffa om enheten startar om under en fullständig genomsökning.

**Möjliga lösningar**: om en genomsökning har förfallit kan du köra en genomsökning en gång, eller schemalägga återkommande genomsökningar. Se [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Ett annat program för slutpunktsskydd körs

Ett annat program för slutpunktsskydd körs och enheten är felfri.

**Möjliga lösningar**: om ett annat program för slutpunktsskydd är installerat och Intune upptäcker det programmet, kan enheten bli instabil.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
