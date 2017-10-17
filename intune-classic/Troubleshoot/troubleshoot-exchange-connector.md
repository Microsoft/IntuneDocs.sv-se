---
title: "Felsök Exchange Connector"
description: "Felsöka problem med Intune Exchange Connector."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 08a21197fd7c67aff037396e86a1555a8033daac
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="troubleshoot-the-exchange-connector"></a>Felsöka Exchange Connector

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I det här avsnittet beskrivs hur du felsöker problem som kan vara relaterade till Intune Exchange Connector.

## <a name="steps-for-checking-the-connector-configuration"></a>Steg för att kontrollera Connector-konfigurationen 

Kontrollera Exchange Connector-konfigurationen och se sedan om problemet är löst.

- Se till att ange ett meddelandekonto i den inledande installationen av Exchange Connector.
- Exchange Connector-tjänstkontot måste ha behörighet att köra PowerShell-cmdlets som används av Exchange Connector.
- Ange en klientåtkomstserver som är så nära som möjligt den server som är värd för Exchange Connector när du konfigurerar Exchange Connector. Svarstiden för kommunikationen mellan klientåtkomstservern och Exchange Connector kan orsaka fördröjningar i enhetsidentifieringen, särskilt om O365-dedikerad används.
- Tänk på att det finns en tidsfördröjning mellan Exchange Connector-synkroniseringarna med Exchange-klientåtkomstservern. En fullständig synkronisering görs en gång per dag, och en deltasynkronisering (snabbsynkronisering) görs varannan timme. Det är sannolikt att användare med en nyregistrerad enhet upplever en fördröjd åtkomst.
- 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync-enheten identifieras inte från Exchange
Kontrollera att Exchange Connector synkroniserar med Exchange-servern. Det gör du genom att leta reda på loggarna som visar om en fullständig synkronisering eller en deltasynkronisering har utförts. Se Exchange Connector-loggarna. Om en fullständig synkronisering eller en deltasynkronisering har utförts efter att enheten anslutits kan du utesluta att detta är orsaken till problemet. Om ingen synkronisering har gjorts samlar du in synkroniseringsloggarna och bifogar dem i ditt supportärende.

- Om användarna saknar Intune-licens kan Exchange Connector inte identifiera deras enheter.
- Om en användares primära SMTP-adress skiljer sig från användarens UPN i AAD, kan Exchange Connector inte identifiera någon enhet för den Intune/AAD-användaren. Åtgärda den primära SMTP-adressen.
- Om klientåtkomstservern som Exchange Connector kommunicerar med under en identifieringscykel är en Exchange 2010-klientåtkomstserver och du använder både en Exchange 2010-postlådeserver och en Exchange 2013-postlådeserver, kan Exchange Connector inte identifiera Exchange 2013-användarnas enheter. Du kan lösa detta genom att konfigurera Exchange Connector så att den pekar på en Exchange 2013-klientåtkomstserver.  Det här problemet gäller främst O365-dedikerad-topologier, men vi rekommenderar ändå att du pekar på en Exchange 2013-klientåtkomstserver i andra topologier.
- I Exchange-dedikerade miljöer (O365-dedikerad) måste du peka Exchange Connector på en Exchange 2013-klientåtkomstserver (inte 2010) i den dedikerade miljön under den inledande konfigurationen eftersom den endast kommer att kommunicera med den här klientåtkomstservern vid körning av Powershell-cmdlets.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Använda Powershell för att få mer information om problem med Exchange Connector
- Om du vill hämta en lista över alla mobila enheter för en postlåda använder du Get-ActiveSyncDeviceStatistics -mailbox mbx
- Om du vill hämta en lista över SMTP-adresser för en postlåda använder du Get-Mailbox -Identity user | select emailaddresses | fl.
- Om du vill hämta detaljerad information om en enhets åtkomststatus använder du Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).
