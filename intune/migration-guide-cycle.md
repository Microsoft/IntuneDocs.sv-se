---
title: "Så här fungerar en normal migreringscykel i Intune"
description: "Den här artikeln beskriver hur en Intune-migreringscykel fungerar och ger exempel på hur du kan hantera migreringscyklerna."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 34e748e16449a99bad4c1f3e96c22dda6d8f3018
ms.sourcegitcommit: 388c5f59bc992375ac63968fd7330af5d84a1348
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/12/2017
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

-   Utvärdera hue effektiv din kommunikationsplan var.

-   Beräkna effekten av att tillämpa villkorlig åtkomst.


## <a name="post-migration"></a>Efter migreringen

Inaktivera den tidigare MDM-providern och avsluta prenumerationen på tjänsten när du har migrerat till Intune. Ta även bort eventuella onödiga infrastrukturkrav genom att följa MDM-providerns anvisningar.
