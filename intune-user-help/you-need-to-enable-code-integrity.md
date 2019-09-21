---
title: Du måste aktivera kodintegritet | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 84892bbc-f888-417b-bbeb-978cc7e10028
searchScope:
- User help
ROBOTS: ''
ms.reviewer: scottduf
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: c518e0eeb18f51fa17d15a72735e319aef1d647d
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167470"
---
# <a name="enable-code-integrity"></a>Aktivera kodintegritet

Din organisation kan kräva att datorn aktive ras med en hot skydds funktion som kallas *kod integritet*. Kod integritet kontrollerar driv rutiner och systemfiler på enheten för tecken på skador eller skadlig program vara. För att kod integriteten ska fungera på enheten måste även en annan säkerhetsfunktion som kallas [*säker start*](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process#secure-boot) vara aktive rad.

Om din dator inte är kompatibel eftersom kod integriteten är inaktive rad bör du kontakta din organisations IT-avdelning. De hjälper dig att aktivera säker start, vilket kommer att utlösa kod integritet nästa gången du startar enheten.

Om du identifierar dig själv som en avancerad enhets användare och vill prova stegen på egen hand, se återaktivera [säker start](https://docs.microsoft.com/windows-hardware/manufacture/desktop/disabling-secure-boot#re-enable-secure-boot).

## <a name="additional-resources-for-it-administrators"></a>Ytterligare resurser för IT-administratörer

Om du är Intune-administratör och vill lära dig mer om Intunes inställningar för hälsokompatibilitet för enhetens hälso tillstånd läser du [lägga till en efterlevnadsprincip för Windows 10-enheter i Intune](https://docs.microsoft.com/intune/compliance-policy-create-windows.md). En detaljerad titt på de regelefterlevnad som du kan vidta i Intune finns i [HEALTHATTESTATION CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp#step-8-take-appropriate-policy-action-based-on-evaluation-results).  

## <a name="next-steps"></a>Nästa steg

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).
