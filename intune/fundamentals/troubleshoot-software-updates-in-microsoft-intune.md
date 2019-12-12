---
title: Felsöka programuppdateringar i Microsoft Intune – Azure | Microsoft Docs
description: Lös problem med programuppdateringar i Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7da927754971fb66a5d8442d0cdf18e0ebfbcd4a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059081"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Felsökning av programuppdateringar i Microsoft Intune

Lös problem med programuppdateringar i Microsoft Intune. Om du vill se en lista över felkoder och beskrivningar, gå till [Felkoder för programuppdateringsagenten i Microsoft Intune](../protect/software-update-agent-error-codes.md).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>Windows 7-enheter med många ersatta uppdateringar slutar rapportera till Intune

Microsoft Intune-klienter kan uppleva ett eller fler av följande symptom:

- Enheter slutar plötsligt rapportera till Intune.  
- Enheter uppvisar hög processoranvändning.
- Programmen installeras långsamt när de installeras via Intune.
- Microsoft Intune Center visar följande fel: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- Intune-administratörskonsolen > Grupper > Alla enheter > status visar: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Det här problemet kan uppstå om ersatta programuppdateringar (uppdateringar ersätts av en annan uppdatering) inte har avfärdats under en längre tid. Under vissa processer, till exempel installationen av ett program, kontrollerar Windows alla ersatta uppdateringar i följd så att uppdateringarna och deras efterträdare har mappats korrekt. Om listan över ersatta programuppdateringar blir för stor kan den här kontrollåtgärden leda till hög processoranvändning på grund av den bearbetningsbelastning och tid som krävs. Det här problemet påverkar främst Windows 7-enheter på grund av det stora antalet ersatta programuppdateringar som finns tillgängliga för Windows 7. Senare operativsystem har inte lika många ersatta uppdateringar och kanske inte är mottagliga för det här problemet.

**Lösning**

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Programuppdateringar**.
3. Avfärda alla ersatta uppdateringar som gäller Windows 7 eller program som Microsoft Office som har installerats på de berörda klienterna.
4. Starta om de berörda klienterna.

Om du kör Windows 7 kontrollerar du dessutom att följande uppdatering är installerad:[3050265 Windows Update-klienten för Windows 7: juni 2015](https://support.microsoft.com/kb/3050265).

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).