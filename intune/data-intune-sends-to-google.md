---
title: Data som Intune skickar till Google
titleSuffix: Microsoft Intune
description: Lista med data som Intune skickar till Google.
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 63f1b07d13daad7512dff8e53f9acbafa7bffdd3
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2018
---
# <a name="data-intune-sends-to-google"></a>Data som Intune skickar till Google

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Om hantering av Android-enheter är aktiverat på en enhet, upprättar Microsoft Intune en anslutning med Google och delar användar- och enhetsinformation med Google. Du måste skapa ett Google-konto innan Microsoft Intune kan upprätta någon anslutning.

I följande tabell visas de data som Microsoft Intune skickar till Google när enhetshantering är aktiverat på en enhet:


| Data som skickas till Google | Information | Används för | Exempel |
|:---:|:---:|:---:|:---:|
| EnterpriseId | Har sitt ursprung i Google vid databindning av Gmail-kontot till Intune. | Primär identifierare som används för att kommunicera mellan Intune och Google.  Denna kommunikation innehåller inställningsprinciper, hantering av enheter och användning eller borttagning av databindning i Android för företag med Intune. | Unik identifierare, exempel på format: LC04eik8a6 |
| Principinnehåll | Har sitt ursprung i Intune när du sparar en ny app- eller konfigurationsprincip. | Tillämpa principer på enheter. | Detta är en samling med alla konfigurerade inställningar för en program- eller konfigurationsprincip. Den kan innehålla kundinformation som anges som en del av en princip, till exempel nätverksnamn, programnamn och appspecifika inställningar. |
| Enhetsdata | Enheter för arbetsprofilscenarier börjar med registreringen i Intune. Enheter för hanterade enhetsscenarier börjar med registreringen i Google. | Enhetsdatainformation skickas mellan Intune och Google för olika åtgärder, exempelvis att tillämpa principer, hantera enheten och allmän rapportering. | **Unik identifierare som motsvarar enhetsnamnet.** Exempel: enterprises/LC04ebru7b/devices/3592d971168f9ae4<br>**Unik identifierare som motsvarar användarnamnet.** Exempel: Enterprises/LC04ebru7b/users/116838519924207449711<br>**Enhetstillstånd.** Exempel: Aktiv, inaktiverad, etablering.<br>**Kompatibilitetstillstånd.** Exempel: Inställningen stöds inte, obligatoriska appar saknas<br>**Programvaruinformation.** Exempel: programvaruversioner och korrigeringsnivå.<br>**Nätverksinformation.** Exempel: IMEI, MEID, WifiMacAddress<br>**Enhetsinställningar.** Exempel: Information om krypteringsnivåer och om enheten tillåter okända appar.<br> Nedan visas ett exempel på ett JSON-meddelande. |
| newPassword | Har sitt ursprung i Intune. | Återställning av enhetens lösenord. | Sträng som motsvarar nytt lösenord. |
| Google-användare | Google | Hanterar arbetsprofilen för BYOD-scenarier (Arbetsprofil). | Unik identifierare som motsvarar det länkade Gmail-kontot. Exempel: 114223373813435875042 |
| Programdata | Har sitt ursprung i Intune när programprincipen sparas. |  | Programmets namnsträng. Exempel: app:com.microsoft.windowsintune.companyportal |
| Företagets tjänstkonto | Har sitt ursprung i Google vid en Intune-begäran. | Används vid autentisering mellan Intune och Google för transaktioner som involverar den här kunden. | Det finns flera delar:<br> **Företags-ID**: Beskrevs tidigare.<br>**UPN**: Genererad UPN som används vid autentisering för kunds räkning.<br>Exempel: w49d77900526190e26708c31c9e8a0@pfwp-commicrosoftonedfmdm2.google.com.iam.gserviceaccount.com<br>**Nyckel**: Base64-kodad blob som används i autentiseringsbegäranden och lagras krypterad i tjänsten. Blobben ser ut så här:<br> Unik identifierare som motsvarar kundnyckeln<br>Exempel: a70d4d53eefbd781ce7ad6a6495c65eb15e74f1f |

**Exempel på enhetsdata**

Här är ett exempel på ett JSON-enhetsmeddelande från Google:



```
'{
  "name": "enterprises/LC02dhxx1r/devices/3195483be017acdc",
  "userId": "114223373813435875042",
  "adminType": "DEVICE_OWNER",
  "state": "ACTIVE",
  "appliedState": "ACTIVE",
  "policyCompliant": true,
  "enrollmentTime": "2017-10-06T15:17:41.702Z",
  "lastStatusReportTime": "2017-10-06T15:18:10.325Z",
  "lastPolicyComplianceReportTime": "2017-10-06T15:18:11.665Z",
  "lastPolicySyncTime": "2017-10-06T15:18:07.852Z",
  "appliedPolicyVersion": "2",
  "apiLevel": 26,
  "enrollmentTokenData": "brew 30 day token",
  "enrollmentTokenId": "yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs",
  "softwareInfo": {
    "androidVersion": "8.0.0",
    "cloudDpcVersionCode": 55314,
    "cloudDpcVersionName": "bv00553-rc14",
    "androidBuildNumber": "OPR4.170623.009",
    "deviceKernelVersion": "3.10.73-ga51b1600b7f8",
    "bootloaderVersion": "BHZ21c",
    "androidBuildTime": "2017-08-28T18:57:48Z",
    "securityPatchLevel": "2017-10-05",
    "androidBuildType": "user",
    "buildUser": "android-build"
  },
  "hardwareInfo": {
    "brand": "google",
    "hardware": "bullhead",
    "deviceBasebandVersion": "M8994F-2.6.39.3.03",
    "manufacturer": "LGE",
    "serialNumber": "01ed07873b3c20cd",
    "model": "Nexus 5X",
    "batteryShutdownTemperatures": [60.0],
    "batteryThrottlingTemperatures": [-3.4028235E38],
    "cpuShutdownTemperatures": [115.0, 115.0, 115.0, 115.0, 115.0, 115.0],
    "cpuThrottlingTemperatures": [60.0, 60.0, 60.0, 60.0, 60.0, 60.0],
    "gpuShutdownTemperatures": [-3.4028235E38],
    "gpuThrottlingTemperatures": [-3.4028235E38],
    "skinShutdownTemperatures": [-3.4028235E38],
    "skinThrottlingTemperatures": [37.0]
  },
  "displays": [{
    "name": "Built-in Screen",
    "refreshRate": 60,
    "state": "ON",
    "width": 1080,
    "height": 1920,
    "density": 420
  }],
  "appliedPolicyName": "enterprises/LC02dhxx1r/policies/default",
  "networkInfo": {
    "imei": "353626070676775",
    "wifiMacAddress": "02:00:00:00:00:00"
  },
  "memoryInfo": {
    "totalRam": "1902936064",
    "totalInternalStorage": "3169611776"
  },
  "memoryEvents": [{
    "eventType": "EXTERNAL_STORAGE_DETECTED",
    "createTime": "2017-10-06T15:18:09.959Z",
    "byteCount": "26720919552"
  }],
  "powerManagementEvents": [{
    "eventType": "BATTERY_LEVEL_COLLECTED",
    "createTime": "2017-10-06T15:18:09.939Z",
    "batteryLevel": 95.0
  }],
  "userName": "enterprises/LC02dhxx1r/users/114223373813435875042",
  "enrollmentTokenName": "enterprises/LC02dhxx1r/enrollmentTokens/yXdtW0_0L7c7Yo9DtRhEfPi3PcMqTorF3V1bTAw_eRs"
}'
```

Om du vill sluta använda Androids enhetshantering med Microsoft Intune och ta bort data, måste du både inaktivera enhetshanteringen i Microsoft Intune och även ta bort ditt Google-konto. Läs mer i Google-kontot om hur du utför kontohanteringen.


