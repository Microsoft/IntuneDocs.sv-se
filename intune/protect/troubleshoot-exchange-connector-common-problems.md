---
title: Felsök vanliga problem med Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Felsök och lös vanliga problem för den lokala Microsoft Intune Exchange Connector.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547679"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Lösa vanliga problem med Intune Exchange Connector
 
Den här artikeln kan hjälpa Intune-administratören att lösa vanliga problem med driften av Intune Exchange Connector.

Innan du börjar felsöka kan du läsa mer [i Felsöka Intune on-premises Exchange Connector](troubleshoot-exchange-connector.md) för grundläggande information om anslutningen. Granska även vanliga problem för anslutnings konfigurationen.

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>En Exchange ActiveSync-enheten identifieras inte från Exchange

När en Exchange ActiveSync-enhet inte identifieras från Exchange [övervakar du aktiviteten Exchange Connector](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) för att se om Exchange Connector synkroniseras med Exchange-servern. Om ingen synkronisering har skett sedan enheten anslöt samlar du in de synkroniserade loggarna och kopplar dem till en support förfrågan. Om en fullständig synkronisering eller snabb synkronisering har slutförts sedan enheten anslöt, söker du efter följande problem:

- Se till att användarna har en Intune-licens. Annars identifierar inte Exchange Connector sina enheter.

- Om användarens primära SMTP-adress skiljer sig från användarhuvudnamnet (UPN) i Azure Active Directory (Azure AD) kan Exchange-anslutningen inte identifiera någon enhet för den användaren. Åtgärda den primära SMTP-adressen för att lösa problemet.

- Om du har både Exchange 2010- och Exchange 2013-postlådeservrar i din miljö rekommenderar vi att du pekar Exchange-anslutningen på en Exchange 2013-klientåtkomstserver (CAS). Om Exchange-anslutningen har konfigurerats för att kommunicera med en Exchange 2010-CAS upptäcker den inga användarenheter på Exchange 2013.

- För Exchange Online-dedikerade miljöer måste du peka Exchange Connector på en Exchange 2013-certifikatutfärdare (inte en Exchange 2010-certifikatutfärdare) i den dedikerade miljön under den första installationen. Anslutningen kommunicerar bara med en Exchange 2013-CAS när den kör PowerShell-cmdletar.

## <a name="problems-with-the-notification-email-message"></a>Problem med e-postmeddelandet

Om du vill ha stöd för villkorlig åtkomst för lokala post lådor på enheter som inte kör Android Knox kontrollerar du att Intune-registreringen startar från e-postmeddelandet "kom igång nu" som Intune Exchange Connector skickar. När du startar registreringen från meddelandet ser du till att enheten tar emot en unik ActiveSyncID på alla plattformar (Exchange, Azure AD, Intune).

En användare kanske inte får e-postmeddelandet eftersom:

- Aviserings kontot har kon figurer ATS felaktigt.
- Det gick inte att identifiera automatiskt för aviserings kontot.
- Begäran om Exchange Web Services (EWS) för att skicka e-postmeddelandet misslyckades.

Läs följande avsnitt för att felsöka problem med e-postavisering.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Kontrol lera det aviserings konto som hämtar inställningarna för automatisk identifiering

1. Kontrollera att tjänsten för automatisk upptäckt och EWS har konfigurerats på Exchange-klientåtkomstservern. Mer information finns i [Client Access Services](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) och [tjänsten för automatisk upptäckt i Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).

2. Kontrol lera att ditt meddelande konto uppfyller följande krav:

   - Kontot har en aktiv post låda som finns på den lokala Exchange-servern.

   - Kontots UPN matchar SMTP-adressen.

3. För automatisk identifiering krävs en DNS-server som har en DNS-post för **Autodiscover.SMTPdomain.com** (till exempel Autodiscover.contoso.com) som pekar på Exchange-klientens åtkomst Server. Om du vill kontrol lera posten anger du FQDN i stället för *Autodiscover.SMTPdomain.com* och följer de här stegen:

   1. Skriv *nslookup*i kommando tolken.

   2. Ange *Autodiscover.SMTPdomain.com*. Utdata bör likna följande bild: ![nslookup-resultat](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   Du kan också testa tjänsten för automatisk upptäckt från Internet på https://testconnectivity.microsoft.com. Eller testa den från en lokal domän med hjälp av Microsoft Connectivity Analyzer-verktyget. Mer information finns i [Microsoft Connectivity Analyzer-verktyget](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)).


### <a name="check-autodiscovery"></a>Kontrol lera automatisk identifiering

Om automatisk identifiering Miss lyckas kan du prova följande steg:

1. [Konfigurera en giltig DNS-post för automatisk identifiering](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)).

2. Hårdkoda webb adressen i konfigurations filen för Intune Exchange Connector:

   1. Bestäm EWS-URL: en. Standard-EWS-URL: en för Exchange är `https://<mailServerFQDN>/ews/exchange.asmx`, men URL: en kan vara annorlunda. Kontakta Exchange-administratören för att kontrol lera rätt URL för din miljö.

   2. Redigera filen *OnPremisesExchangeConnectorServiceConfiguration.xml*. Som standard finns filen i *%programdata%\Microsoft\Windows Intune Exchange Connector* på den dator som kör Exchange-anslutaren. Öppna filen i en text redigerare och ändra sedan följande rad så att den återspeglar EWS-URL: en för din miljö: `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. Spara filen och starta om datorn eller Microsoft Intune Exchange Connector-tjänsten.

>[!NOTE]
> I den här konfigurationen slutar Intune Exchange Connector att använda automatisk identifiering och ansluter istället direkt till EWS-URL: en.

## <a name="next-steps"></a>Nästa steg

Om du behöver hjälp med vissa fel kan [du försöka lösa vanliga fel för Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

För att få support, eller för att få hjälp från Intune-communityn:

- Se [få support](../fundamentals/get-support.md) för att använda Intune-konsolen för att felsöka problemet eller för att öppna ett support ärende med Microsoft.
- Publicera ditt problem i [Microsoft Intune forum](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod).