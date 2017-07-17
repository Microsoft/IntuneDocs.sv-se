---
title: "Jämför hanteringsalternativ för Windows-datorer"
description: "Registrera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) eller Apple Configurator"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 560ce922fa58e759157358c6b7348fe0388ce408
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# Jämför hanteringen av Windows-datorer som datorer respektive mobila enheter
<a id="compare-managing-windows-pcs-as-computers-or-mobile-devices" class="xliff"></a>

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Organisationer kan använda Microsoft Intune för att hantera Windows-datorer som mobila enheter med hantering av mobila enheter (MDM) eller som datorer med Intune-programvaruklienten.  Microsoft rekommenderar att kunderna använder MDM-hanteringslösningen närhelst det är möjligt. Men för att du bättre ska förstå skillnaderna mellan dessa alternativ, så har vi tagit fram följande diagram där du kan jämföra de två hanteringsalternativen.

|**Funktionen/scenario** |**Windows som dator**<br>Intune-klientprogrammet | **Windows som mobil enhet**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Operativsystem** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Intune Portal-support** |[Silverlight-konsolen](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**Villkorlig åtkomst**|Saknas|Tillgänglig <br>[Vad är villkorlig åtkomst?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**Massregistrering**|Saknas|Tillgänglig <br>[Massregistrering för Windows-enheter](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**Enhetsprofiler**|Saknas|Tillgänglig <br>[Vad är enhetsprofiler i Microsoft Intune?](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**Registrering utan agent**|Saknas |Tillgänglig<br>[Registrera Windows-enheter](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**Hantering av programvaruuppdateringar**| Windows-uppdateringar och appuppdateringar för Microsoft<br>[Hålla Windows-datorerna uppdaterade med programvaruuppdateringar](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Microsoft Store för företag för både Windows 10- och Microsoft-appar<br> [Konfigurera inställningar för Windows Update för företag](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**Hantering av programlicenser**|Tillgänglig <br>[Hantera licensavtal för Windows-datorprogram](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|Microsoft Store för företag (endast .appx-appar)<br>[Hantera appar som du har köpt från Windows Store för företag](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**Inventering**|Tillgänglig <br>[Visa maskin- och programvaruinventering för Windows-datorer](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|Tillgänglig <br>[Så här övervakar du appinformation](https://docs.microsoft.com/intune/apps-monitor)<br>[Vad är enhetshantering](https://docs.microsoft.com/intune/device-management)|
|**Princip för Windows-brandväggen**|Tillgänglig <br>[Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |Saknas|
|**Skydd mot skadlig kod**|Slutpunktsskydd<br>[Skydda Windows-datorer med Endpoint Protection](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows försvarare<br>[Inställningar för Windows Defender](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**Fjärrhjälp** |TeamViewer<br>[Begära och tillhandahålla hjälp för Windows-datorer](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|Saknas |
|**Appdistribution** | Inte tillgängligt för Microsoft Store för företag,<br>enbart .exe, .appx och multi-file .msi<br>[Lägg till program för Windows-datorer som kör Intune-klientprogramvaran](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Tillgängliga för Microsoft Store-appar och branschspecifika appar<br>[Så här lägger du till Windows Store-appar](https://docs.microsoft.com/intune-azure/manage-apps/windows-store-app)<br>Microsofts appdistribution och Win32-appar kommer snart |
|**Appskydd**|Saknas|Tillgänglig <br>[Vad är appskyddsprinciper?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|


### Fördelarna med MDM-hantering för Windows-datorer
<a id="advantages-of-mdm-windows-pc-management" class="xliff"></a>
Hantering av Windows-datorer med modern hantering av mobila enheter har följande fördelar:
- **Skalbarhet** – MDM-hanteringen skalas med Intunes molnhantering. Intune-programvaruklienten är begränsad till 7000 datorer.
- **Enkelhet** – Använder de moderna hanteringsfunktioner som ingår i operativsystemet utan att behöva hämta någon programvaruklient
- **Konsekvens** – Dina Windows-datorer hanteras precis som alla andra enheter i din organisation
<!-- - **Cloud optimization** - -->
