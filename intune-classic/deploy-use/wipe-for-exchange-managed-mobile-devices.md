---
title: Rensning för mobila enheter hanterade med Exchange
description: Med Microsoft Intune kan du rensa eller återställa mobila enheter som hanteras med hjälp av Exchange ActiveSync (EAS) med Intune Exchange Connector
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 753e5e9dac7199dff18d110808524f05aa669036
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016092"
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Wipe for Hantering av mobila enheter-managed mobile devices

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan du rensa eller återställa mobila enheter som hanteras med hjälp av Exchange ActiveSync (EAS) med Intune Exchange Connector. I följande tabell beskrivs rensningsfunktionerna som är tillgängliga via Exchange ActiveSync:


|      Typ av rensning       |              Windows 8.1 och Windows RT 8.1              |                            iOS                             |                          Android                          |
|-------------------------|----------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|        Fullständig rensning        |          Tar bort e-postkonto och cachelagrad e-post.           |                      XFabriksåterställning.                       |                      Fabriksåterställning.                       |
|  Selektiv rensning/e-post   |                  Tar bort e-postkonto.                  |                       Stöds inte.                       |                      Stöds inte.                       |
| Selektiv rensning/principer | Tvingande principer tas bort, men inställningar ändras inte | XTvingande principer tas bort, men inställningar ändras inte. | Tvingande principer tas bort, men inställningar ändras inte. |

