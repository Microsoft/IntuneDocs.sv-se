---
title: Felsöka slutpunktsskydd i Intune – Azure | Microsoft Docs
description: Lösa problem när du använder Microsoft Intune Endpoint Protection.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1de1722aa635367dac4b586e1333aed163156a83
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836684"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Felsöka Endpoint Protection i Intune

Använd informationen för att lösa problem som kan uppstå när du använder slutpunktsskydd. Du kan också [granska händelseloggar och felkoder för att felsöka problem med Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).

### <a name="error-messages"></a>Felmeddelanden
I det här avsnittet beskrivs möjliga orsaker och lösningar vid följande fel och varningar.

|Statusobjekt|Möjliga orsaker|Möjliga lösningar|
|---------------|--------------------|-----------------------|
|**Endpoint Protection-motorn är inte tillgänglig**|Motorn för Endpoint Protection i Intune är skadad eller har tagits bort.|Om motorn för Endpoint Protection i Intune är skadad kan du prova att uppdatera eller installera om programvaran.<br /><br />Om du vill framtvinga en omedelbar uppdatering klickar du på **Uppdatera** i Endpoint Protection-klientprogrammet (i verktygsfältet på hanterade datorer).<br /><br />Om motorn inte kan uppdateras måste du installera om Endpoint Protection-motorn.<br /><br />Leta upp **Microsoft Intune Endpoint Protection Agent** i listan över installerade program på Kontrollpanelen på den hanterade datorn och avinstallera programmet.<br /><br />Microsoft Online Management Update Manager identifierar programmet som saknas under nästa uppdateringssynkronisering och installerar om det på den schemalagda installationstiden.|
|**Endpoint Protection är inaktiverat**|Intunes slutpunktsskydd har inaktiverats av en administratör med hjälp av en konfigurationsprofil, eller av en användare på en hanterad dator.|Aktivera slutpunktsskyddet. Läs mer om att [lägga till inställningar för slutpunktsskydd](endpoint-protection-configure.md) i Intune, eller [starta Windows Defender för att komma åt företagets resurser](/intune-user-help/turn-on-defender-windows).|
|**Realtidsskydd är inaktiverat**|Realtidsskydd har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera slutpunktsskyddet. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Genomsökning av hämtningar är inaktiverat**|Genomsökningen av hämtningar har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera genomsökningen. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Fil- och programaktivitetsövervakning inaktiverad**|Övervakningen av fil- och programaktiviteter har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera fil- och programaktiviteter. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Beteendeövervakning är inaktiverat**|Beteendeövervakning har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera beteendeövervakningen. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Genomsökning av skript är inaktiverat**|Genomsökning av skript har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera genomsökningen av skript. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Kontrollsystem för nätverk är inaktiverat**|Kontrollsystemet för nätverk har inaktiverats av en administratör med hjälp av en profil, eller av en användare på en hanterad dator.|Aktivera NIS (Network Inspection Service). Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) i Intune, eller [starta realtidsskyddet för att få åtkomst till företagets resurser](/intune-user-help/turn-on-defender-windows). |
|**Definitionerna för skadlig kod är inaktuella**|Datorn kanske har varit frånkopplad från Internet under en längre tid och definitionerna för skadlig kod kanske inte har uppdaterats än. Den här statusen visas när definitionerna för skadlig kod på datorn är inaktuella i 14 dagar eller mer.|Om definitionerna för skadlig kod är inaktuella, kan du uppdatera definitionerna med [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**En fullständig genomsökning är försenad**|En fullständig genomsökning har inte utförts på 14 dagar. Detta kan bero på en omstart av datorn under en fullständig genomsökning.|Om en fullständig genomsökning har förfallit kan du köra en fullständig genomsökning en gång, eller schemalägga återkommande fullständiga genomsökningar. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**En snabbgenomsökning är försenad**|En snabbgenomsökning har inte utförts på 14 dagar. Detta kan bero på en omstart av datorn under en snabbgenomsökning.|Om en snabbgenomsökning har förfallit kan du köra en snabbgenomsökning en gång, eller schemalägga återkommande snabbgenomsökningar. Se [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Ett annat program för slutpunktsskydd körs**|Ett annat program för slutpunktsskydd körs och datorn är felfri.|Om ett annat program för slutpunktsskydd är installerat och Intune upptäcker det programmet, kan enheten bli instabil.|

### <a name="next-steps"></a>Nästa steg
Om den här informationen inte är till någon hjälp, kan du även [få support för Microsoft Intune](get-support.md).
