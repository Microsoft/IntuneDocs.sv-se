---
title: Vanliga meddelanden för slutpunktsskydd i Microsoft Intune – Azure | Microsoft Docs
description: Se vanliga meddelanden och möjliga lösningar när du använder och felsöker Endpoint Protection och Windows Defender i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5159ee595a6699eb457b194162d21038d4667063
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68353340"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problem med Endpoint Protection och möjliga lösningar i Microsoft Intune

Den här artikeln beskriver artikellistorna och beskriver potentiella orsaker och lösningar för några fel och varningar. Använd informationen för att hjälpa dig lösa problem när du använder Endpoint Protection.

## <a name="windows-defender-error-codes"></a>Windows Defender-felkoder

Granska händelseloggar och felkoder för att [felsöka problem med Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Vanliga Intune-fel och möjliga lösningar

### <a name="endpoint-protection-engine-unavailable"></a>Endpoint Protection-motorn är inte tillgänglig

**Potentiell orsak**: Motorn för Endpoint Protection i Intune är skadad eller borttagen.

**Möjliga lösningar**:

- Om Endpoint Protection är skadat eller inte uppdaterat, uppdatera eller installera om programmet.
- Framtvinga en omedelbar uppdatering. I Endpoint Protection-klientprogrammet (eventuellt i aktivitetsfältet), väljer du **Uppdatera**.
- I Kontrollpanelen > Program, väljer du **Microsoft Intune Endpoint Protection Agent**. Avinstallera programmet.
- Microsoft Online Management Update Manager identifierar programmet som saknas under nästa uppdateringssynkronisering och installerar om det på den schemalagda installationstiden.

### <a name="features-are-disabled"></a>Funktioner är inaktiverade

Du kan få ett meddelande om att vissa funktioner är inaktiverade. Du får de här meddelandena om Intune Endpoint Protection eller Windows Defender har inaktiverats av en administratör med en konfigurationsprofil. Eller inaktiveras av en slutanvändare på enheten. Möjliga meddelanden:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Möjliga lösningar**: aktivera dessa funktioner. Anvisningar finns i:

- [Lägg till Endpoint Protection-inställningar](endpoint-protection-configure.md)
- [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus)
- [Slutanvändare: aktivera realtidsskydd om du vill komma åt företagsresurser](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>Definitionerna för skadlig kod är inaktuella

Den här statusen visas när definitionerna för skadlig kod på enheten är inaktuella med 14 dagar eller mer. Meddelandet kan till exempel indikera om enheten är frånkopplad från Internet eller om definitionerna för skadlig kod är inaktuella.

[Möjliga lösningar](device-restrictions-windows-10.md#windows-defender-antivirus): om definitionerna för skadlig kod är inaktuella, kan du uppdatera definitionerna med **Windows Defender Antivirus**.

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Det är dags för Fullständig sökning eller Snabbsökning

En fullständig sökning eller Snabbsökning har inte slutförts de senaste 14 dagarna. Det här scenariot kan inträffa om enheten startar om under en fullständig genomsökning.

**Möjliga lösningar**: om en genomsökning har förfallit kan du köra en genomsökning en gång, eller schemalägga återkommande genomsökningar. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>Ett annat program för slutpunktsskydd körs

Ett annat program för slutpunktsskydd körs och enheten är felfri.

**Möjliga lösningar**: om ett annat program för slutpunktsskydd är installerat och Intune upptäcker det programmet, kan enheten bli instabil.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
