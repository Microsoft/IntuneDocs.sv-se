---
title: Felsöka Exchange Connector | Microsoft Intune
description: Felsöka problem med lokal Intune Exchange-anslutning.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fecdda5467c83ab12ca921e86259884171e07819
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816556"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Felsöka lokal Intune Exchange-anslutning

I den här artikeln beskrivs hur du felsöker problem med lokal Intune Exchange-anslutning.

## <a name="steps-for-checking-the-connector-configuration"></a>Steg för att kontrollera anslutningskonfigurationen 

Kontrollera [konfigurationen av lokal Intune Exchange-anslutning](exchange-connector-install.md) och se till att anslutningen har konfigurerats korrekt. Nedan visas några vanliga problem. Se om problemet är löst när du har gjort korrigeringar.

 - I dialogrutan för Microsoft Intune Exchange Connector ser du till att du har angett ett användarkonto som har nödvändiga behörigheter för att köra [Windows PowerShell Exchange-cmdlets](exchange-connector-install.md#exchange-cmdlet-requirements).
- Aktivera meddelanden och ange ett meddelandekonto.
 - När du konfigurerar Exchange Connector anger du en klientåtkomstserver (CAS) som är så nära som möjligt den server som är värd för Exchange-anslutningen. Svarstiden för kommunikationen mellan klientåtkomstservern och Exchange-anslutningen kan orsaka fördröjningar i enhetsidentifieringen, särskilt om Dedikerad Exchange Online används.
 - Åtkomst för en användare med en nyligen registrerad enhet kan fördröjas tills Exchange-anslutningen synkroniserar med Exchange-CAS. En fullständig synkronisering görs en gång per dag, och en deltasynkronisering (snabbsynkronisering) görs flera gånger per dag.  Du kan [manuellt framtvinga en snabbsynkronisering eller en fullständig synkronisering](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) för att minimera fördröjningar.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync-enheten identifieras inte från Exchange
[Övervaka Exchange-anslutningens aktivitet](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) för att se om Exchange-anslutningen synkroniserar med Exchange-servern. Om en fullständig synkronisering eller en snabbsynkronisering har slutförts efter att enheten anslöts kan du söka efter andra möjliga problem som anges nedan. Om ingen synkronisering har gjorts samlar du in synkroniseringsloggarna och bifogar dem i en supportbegäran.

 - Se till att användarna har en Intune-licens; annars kan Exchange-anslutningen inte identifiera deras enheter.
 - Om en användares primära SMTP-adress skiljer sig från användarens UPN i Azure Active Directory (Azure AD) kan Exchange-anslutningen inte identifiera någon enhet för den användaren. Åtgärda den primära SMTP-adressen för att lösa problemet.
 - Om du har både Exchange 2010- och Exchange 2013-postlådeservrar i din miljö rekommenderar vi att du pekar Exchange-anslutningen på en Exchange 2013-CAS. Annars kommer Exchange-anslutningen inte att identifiera några 2013-användares enheter om Exchange-anslutningen har konfigurerats för att kommunicera med en Exchange 2010-CAS. 
- I Dedikerad Exchange Online-miljöer måste du peka Exchange-anslutningen på en Exchange 2013-CAS (inte en Exchange 2010-CAS) i den dedikerade miljön under den inledande konfigurationen eftersom anslutningen endast kommer att kommunicera med den här CAS:en vid körning av Powershell-cmdlets.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Använda Powershell för att få mer information om problem med Exchange Connector
- Om du vill hämta en lista över alla mobila enheter för en postlåda använder du Get-ActiveSyncDeviceStatistics -mailbox mbx
- Om du vill hämta en lista över SMTP-adresser för en postlåda använder du Get-Mailbox -Identity user | select emailaddresses | fl
- Om du vill hämta detaljerad information om en enhets åtkomststatus använder du Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>Nästa steg
Om den här informationen inte är till hjälp kan du även [få support för Microsoft Intune](get-support.md).
