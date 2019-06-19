---
title: Jämför hanteringsalternativ för Windows-datorer
titleSuffix: Microsoft Intune
description: Registrera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) eller Apple Configurator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3665a785391d2bff707bf5b8fe0a7e4f6e8a43d
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044521"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Jämför hanteringen av Windows-datorer som datorer respektive mobila enheter

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Organisationer kan använda Microsoft Intune för att hantera Windows-datorer som mobila enheter med hantering av mobila enheter (MDM) eller som datorer med Intune-programvaruklienten.  Microsoft rekommenderar att kunderna använder MDM-hanteringslösningen närhelst det är möjligt. Men för att du bättre ska förstå skillnaderna mellan dessa alternativ, så har vi tagit fram följande diagram där du kan jämföra de två hanteringsalternativen.

|**Funktionen/scenario** |**Windows som dator**<br>Intune-klientprogrammet | **Windows som mobil enhet**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Operativsystem** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Intune Portal-support** |[Silverlight-konsolen](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**Villkorsstyrd åtkomst**|Saknas|Tillgänglig <br>[Vad är Villkorsstyrd åtkomst?](conditional-access.md)|
|**Massregistrering**|Saknas|Tillgänglig <br>[Massregistrering för Windows-enheter](windows-bulk-enroll.md)|
|**Enhetsprofiler**|Saknas|Tillgänglig <br>[Vad är enhetsprofiler i Microsoft Intune?](device-profiles.md)|
|**Registrering utan agent**|Saknas |Tillgänglig<br>[Registrera Windows-enheter](windows-enroll.md)|
|**Hantering av programvaruuppdateringar**| Windows-uppdateringar och appuppdateringar för Microsoft<br>[Hålla Windows-datorerna uppdaterade med programvaruuppdateringar](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Microsoft Store för företag för både Windows 10- och Microsoft-appar<br> [Konfigurera inställningar för Windows Update för företag](windows-update-for-business-configure.md) |
|**Hantering av programlicenser**|Tillgänglig <br>[Hantera licensavtal för Windows-datorprogram](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Microsoft Store för företag (endast .appx-appar)<br>[Hantera appar som du har köpt från Microsoft Store för företag](windows-store-for-business.md)|
|**Inventering**|Tillgänglig <br>[Visa maskin- och programvaruinventering för Windows-datorer](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Tillgänglig <br>[Så här övervakar du appinformation](apps-monitor.md)<br>[Vad är enhetshantering](device-management.md)|
|**Princip för Windows-brandväggen**|Tillgänglig <br>[Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Tillgänglig <br>[Windows Defender-brandvägg](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Skydd mot skadlig kod**|Slutpunktsskydd<br>[Skydda Windows-datorer med Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows försvarare<br>[Aktivera Windows Defender](advanced-threat-protection.md)|
|**Fjärrhjälp** |TeamViewer<br>[Begära och tillhandahålla hjälp för Windows-datorer](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Fjärradministrera Intune-enheter med TeamViewer](teamviewer-support.md) |
|**Appdistribution** | Inte tillgängligt för Microsoft Store för företag,<br>enbart .exe, .appx och multi-file .msi<br>[Lägg till program för Windows-datorer som kör Intune-klientprogramvaran](add-apps-for-windows-pcs-in-microsoft-intune.md)|Tillgängliga för Microsoft Store-appar och branschspecifika appar<br>[Så här lägger du till Windows Store-appar](store-apps-windows.md)<br>[Så här lägger du till Windows branschspecifika appar (LOB-appar)](lob-apps-windows.md)|
|**Appskydd**|Saknas|Tillgänglig <br>[Vad är appskyddsprinciper?](app-protection-policy.md)|
|**Hälsoattestering**|Saknas|Tillgänglig|


### <a name="advantages-of-mdm-windows-pc-management"></a>Fördelarna med MDM-hantering för Windows-datorer
Hantering av Windows-datorer med modern hantering av mobila enheter har följande fördelar:
- **Skalbarhet** – MDM-hanteringen skalas med Intunes molnhantering. Intune-programvaruklienten är begränsad till 7000 datorer.
- **Enkelhet** – Använder de moderna hanteringsfunktioner som ingår i operativsystemet utan att behöva hämta någon programvaruklient
- **Konsekvens** – Dina Windows-datorer hanteras precis som alla andra enheter i din organisation
<!-- - **Cloud optimization** - -->
