---
title: Data som Intune skickar till Apple
titleSuffix: Microsoft Intune
description: Lista med data som Intune skickar till Apple.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b204a956-18ec-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2f1be7a2457cca7da62883370c9e273168c6a29
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72502438"
---
# <a name="data-intune-sends-to-apple"></a>Data som Intune skickar till Apple

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Om någon av följande Appletjänster är aktiverade på en enhet, upprättar Microsoft Intune en anslutning med Apple och delar användar- och enhetsinformationen med Apple: 

- [Apples program för enhetsregistrering (DEP)](../enrollment/device-enrollment-program-enroll-ios.md)
- [Apple MDM-pushcertifikat (APNS)](../enrollment/apple-mdm-push-certificate-get.md)
- [Apple School Manager (ASM)](https://docs.microsoft.com/schooldatasync/apple-school-manager-integration-with-intune-for-education-and-school-data-sync)
- [Apples volymköpsprogram (VPP](../apps/vpp-apps-ios.md)

Innan Microsoft Intune kan upprätta en anslutning, måste du skapa ett Apple-konto för varje Apple-tjänst.

I följande tabell visas de data som Microsoft Intune skickar från en enhet till de aktiverade Apple-tjänsterna. 

| Tjänst | Data som skickas till Apple | Används för |
|---|---| ---|
| [APNS](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Token, PushMagic | Om servern accepterar enheten förser enheten servern med sin enhetstoken för push-meddelanden. Servern använder denna token för att skicka push-meddelanden till enheten. Incheckningsmeddelandet innehåller också en PushMagic-sträng. Servern måste komma ihåg denna sträng och inkludera den i alla push-meddelanden som den skickar till enheten. |
| [ASM/DEP](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/MobileDeviceManagementProtocolRef/3-MDM_Protocol/MDM_Protocol.html#//apple_ref/doc/uid/TP40017387-CH3-SW2) | Servertoken | Enhetstoken för push-meddelanden som används för att autentisera till Apple-tjänsten. |
| ASM/DEP | server_name | Ett identifierbart namn på MDM-servern. |
| ASM/DEP | server_uuid | En systemgenererad serveridentifierare. |
| ASM/DEP | admin_id | Apple-ID för den person som genererade de aktuella tokens som används. |
| ASM/DEP | org_name | Organisationens namn. |
| ASM/DEP | org_email | Organisationens e-postadress. |
| ASM/DEP | org_phone | Organisationens telefonnummer. |
| ASM/DEP | org_address | Organisationens adress. |
| ASM/DEP | org_id | DEP-kundens ID. Den här nyckeln är endast tillgänglig i protokollversion 3 och senare. |
| ASM/DEP | serial_number | Enhetens serienummer (sträng). |
| ASM/DEP | modell | Modellnamnet (sträng). |
| ASM/DEP | description | En beskrivning av enheten (sträng). |
| ASM/DEP | asset_tag | Enhetens tillgångstagg (sträng). |
| ASM/DEP | profile_status | Status för profilinstallationen. Möjliga värden: **tom**, **tilldelad**, **push-överförd** eller **borttagen**. |
| ASM/DEP | profile_uuid | Unikt ID för den tilldelade profilen. |
| ASM/DEP | device_assigned_by | E-postadress till den person som tilldelade enheten. |
| ASM/DEP | os | Enhetens operativsystem: iOS, OSX eller tvOS. Den här nyckeln är giltig i X-Server-Protocol-Version 2 eller senare. |
| ASM/DEP | device_family | Enhetens Apple-produktfamilj: iPad, iPhone, iPod, Mac eller AppleTV. Den här nyckeln är giltig i X-Server-Protocol-Version 2 eller senare. |
| ASM/DEP | profile_name | Sträng. Ett läsbart namn för profilen. |
| ASM/DEP | support_phone_number | Valfritt. Sträng. Supportens telefonnummer för organisationen. |
| ASM/DEP | support_email_address | Valfritt. Sträng. Supportens e-postadress för organisationen. Den här nyckeln är giltig i X-Server-Protocol-Version 2 eller senare. |
| ASM/DEP | avdelning | Valfritt. Sträng. Användardefinierad avdelning eller platsens namn. |
| ASM/DEP | devices | Matris med strängar som innehåller enhetens serienummer. (Kan vara tom.) |
| VPP | Intune UserId guid | GUID som genereras av Intune. |
| VPP | Hanterad AppleId UPN | AppleID som angetts av administratören vid konfigurationen av anslutningen för VPP-token med Apple. |
| VPP | Serienummer | Den hanterade enhetens serienummer. |

Om du vill sluta använda Apple-tjänster med Microsoft Intune och ta bort data, måste du både inaktivera din Microsoft Intune Apple-token och även ta bort ditt Apple-konto. Läs mer i Apple-kontot om hur du utför kontohanteringen.


