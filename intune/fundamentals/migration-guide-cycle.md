---
title: Så här fungerar en normal migreringscykel i Intune
titleSuffix: Microsoft Intune
description: Den här artikeln beskriver hur en Microsoft Intune-migreringscykel fungerar och ger exempel på hur du kan hantera migreringscyklerna.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: e771c7f061d32748898846f9391758c02f7499c9
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72505283"
---
# <a name="typical-migration-cycle"></a>Typisk migreringscykel

Det är vanligt att organisationer startar sin Intune-migrering med ett litet pilotprojekt genom att rikta in sig på en del av sina användare på IT-avdelningen. I syfte att fastställa ett tidsschema för migreringen kan din organisation dessutom behöva diskutera sådana faktorer som gruppens beredvillighet för förändring, antal användare, komplexitet, krav, plats och affärsrisk.

Här följer ett exempel på hur dina målgrupper kan schemaläggas:

  | **Målgrupper för migrering** | **Tidsperiod 1** | **Tidsperiod 2** | **Tidsperiod 3** | **Tidsperiod 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Begränsat pilotprojekt – IT-avdelningen (50 användare) | Presentera planen | Ge anvisningar om registrering | Ge en deadline | Framtvinga villkorlig åtkomst |  |                                                        
| Utvidgat pilotprojekt – IT-avdelningen (200 användare) |  | Presentera planen | Ge anvisningar om registrering | Ge en deadline | Framtvinga villkorlig åtkomst |
| Migreringsfas 1: Tekniksmarta användare (2000) |  |  | Presentera planen | Ge anvisningar om registrering | Ge en deadline |
| Migreringsfas 2: Östra USA |  |  |  | Presentera planen | Ge anvisningar om registrering |
| Alla regioner |  |  |  |  | Presentera planen |

## <a name="customer-migration-case-study"></a>Fallstudie av kundmigrering

### <a name="adatum-corporation"></a>Adatum Corporation

Se [hur Adatum Corporation genomförde migreringsprocessen från en MDM-tredjepartsprovider till Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Övervaka migrering

Du kan övervaka migreringen på flera sätt med Intune:

* Intune-användargruppsvyer

* En uppsättning inbyggda rapporter

* Konsolaviseringar

Kontrollera hur många användare som har registrerat enheter efter varje fas, så att du kan:

- Utvärdera hue effektiv din kommunikationsplan var.

- Beräkna effekten av att tillämpa villkorlig åtkomst.


## <a name="post-migration"></a>Efter migreringen

Inaktivera den tidigare MDM-providern och avsluta prenumerationen på tjänsten när du har migrerat till Intune. Ta även bort eventuella onödiga infrastrukturkrav genom att följa MDM-providerns anvisningar.
