---
title: Data som Intune skickar till Google
titleSuffix: Microsoft Intune
description: Lista med data som Intune skickar till Google.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a5c3bec4-18ed-11e8-accf-0ed5f89f718b
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: bb205472c4407dab6ff990e33737a8bd8b24a010
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52188661"
---
# <a name="data-intune-sends-to-google"></a>Data som Intune skickar till Google

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Om hantering av Android-företagsenheter är aktiverat på en enhet, upprättar Microsoft Intune en anslutning med Google och delar användar- och enhetsinformation med Google. Du måste skapa ett Google-konto innan Microsoft Intune kan upprätta någon anslutning.

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


Om du vill sluta använda Androids enhetshantering för företag med Microsoft Intune och ta bort data, måste du både inaktivera enhetshanteringen i Microsoft Intune och även ta bort ditt Google-konto. Läs mer i Google-kontot om hur du utför kontohanteringen.


