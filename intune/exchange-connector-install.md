---
title: Konfigurera Microsoft Intune lokalt med Exchange Connector
titleSuffix: 
description: "Använd din lokala Exchange Connector till att hantera enhetsåtkomst till Exchange-postlådor baserat på Intune-registrering och Exchange Active Sync (EAS)."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0caea2e8b7704fe2dfcbec937b59000ac2a12ae5
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Konfigurera Intune On-Premises Connector för lokal Exchange i Microsoft Intune Azure

En lokal Exchange Server-miljö kan använda Intunes lokala Exchange Connector till att hantera enhetsåtkomst till lokala Exchange-postlådor, baserat på om enheterna har registrerats i Intune och om de är kompatibla med Intunes principer för enhetsefterlevnad. Lokala Exchange Connector har även i uppgift att identifiera mobila enheter som ansluter till lokala Exchange-servrar genom att synkronisera den befintliga EAS-posten (Exchange Active Sync) med Intune.

> [!IMPORTANT]
> Intune har endast stöd för en lokal Exchange Connector-anslutning av valfri typ per prenumeration.

Om du vill konfigurera en anslutning som gör det möjligt för Microsoft Intune att kommunicera med den lokala Exchange-servern måste du följa anvisningarna nedan:

1.  Hämta Intunes lokala Exchange Connector från Azure-portalen.
2.  Installera och konfigurera Intune Exchange Connector lokalt.
3.  Verifiera Exchange-anslutningen.

## <a name="on-premises-exchange-connector-requirements"></a>Krav för den lokala Exchange Connector
Följande tabell innehåller kraven för datorn där du installerar den lokala Exchange Connector.

|Krav|Mer information|
|---------------|--------------------|
|Operativsystem|Intune stöder lokal Exchange Connector på datorer som kör någon utgåva av Windows Server 2008 SP2 64-bitars, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 eller Windows Server 2016.<br /><br />Connector stöds inte i Server Core-installationer.|
|Microsoft Exchange|Lokala anslutningar kräver Microsoft Exchange 2010 SP1 eller senare, eller äldre Exchange Online Dedicated. Om du vill ta reda på om Exchange Online Dedicated-miljön har den **nya** eller **äldre** konfigurationen kontaktar du din kontoansvariga.|
|Utfärdare för hantering av mobila enheter| [Ange utfärdare för hantering av mobila enheter till Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).|
|Maskinvara|Datorn där du installerar anslutningen måste ha en 1,6 GHz-processor med 2 GB RAM-minne och 10 GB ledigt diskutrymme.|users-add.md
|Active Directory-synkronisering|Innan du kan använda Connector-anslutningen för att ansluta Intune till Exchange Server måste du [konfigurera Active Directory-synkronisering](users-add.md) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans.|
|Tilläggsprogramvara|En fullständig installation av Microsoft .NET Framework 4.5 och Windows PowerShell 2.0 måste installeras på den dator som är värd för anslutningen.|
|Nätverk|Datorn där du installerar anslutningen måste finnas i en domän som har en förtroenderelation till domänen som är värd för Exchange Server.<br /><br />Datorn kräver konfigurationer för att kunna komma åt Intune-tjänsten genom brandväggar och proxyservrar via portarna 80 och 443. Exempel på domäner som används av Intune är manage.microsoft.com, &#42;manage.microsoft.com och &#42;.manage.microsoft.com.|


### <a name="exchange-cmdlet-requirements"></a>Krav för Exchange-cmdlet

Du måste skapa ett Active Directory-användarkonto som används av Intune Exchange Connector. Kontot måste ha behörighet att köra följande obligatoriska Exchange för Windows PowerShell-cmdlets:


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Ladda ner programinstallationspaketet för den lokala Exchange Connector

1. I ett Windows Server-operativsystem som stöder den lokala Exchange Connector öppnar du [Azure Portal](http://portal.azure.com) och loggar in med ett användarkonto som är administratör på den lokala Exchange-servern och som har licens för att använda Exchange Server.

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune**. Intune- instrumentpanelen öppnas. Välj **Lokal åtkomst**.

4. Välj **Exchange ActiveSync Connector** och sedan alternativet för att **ladda ned det lokala anslutningsprogrammet**.

5.  Den lokala Exchange Connector finns i en komprimerad mapp (.zip) som kan öppnas eller sparas. I dialogrutan **Filhämtning** klickar du på **Spara** för att spara den komprimerade mappen på en säker plats.

    > [!IMPORTANT]
    > Byt inte namn på eller flytta filerna i mappen för den lokala Exchange Connector. Installationen av Exchange Connector misslyckas om du flyttar eller byter namn på mappens innehåll.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installera och konfigurera den lokala Intune Exchange Connector
Utför följande steg för att installera den lokala Intune Exchange Connector. Den lokala Exchange Connector kan bara installeras en gång per Intune-prenumeration och bara på en dator. Om du försöker konfigurera ytterligare en lokal Exchange Connector ersätts den ursprungliga anslutningen med den nya.

1.  På ett operativsystem med stöd för den lokala Exchange Connector extraherar du filerna i **Exchange_Connector_Setup.zip** till en säker plats.

2.  När filerna har extraherats öppnar du den extraherade mappen och dubbelklickar på **Exchange_Connector_Setup.exe** för att installera den lokala Exchange Connector.

    > [!IMPORTANT]
    > Om målmappen inte är en säker plats bör du ta bort certifikatfilen **WindowsIntune.accountcert** när du har installerat den lokala anslutningen.

3.  I dialogrutan **Microsoft Intune Exchange Connector** väljer du antingen **On-premises Microsoft Exchange Server** eller **Hosted Microsoft Exchange Server**.

  ![Bild som visar var du väljer Exchange Server-typ](./media/intune-sa-exchange-connector-config.png)

  För en lokal Exchange-server anger du antingen servernamnet eller det fullständigt kvalificerade domännamnet för Exchange-servern som är värd för **klientåtkomstserverrollen**.

  För en värdbaserad Exchange-server anger du adressen till Exchange-servern. Så här hittar du URL-adressen till den värdbaserade Exchange-servern:

    1. Öppna Outlook Web App för Office 365.

    2. Välj ikonen **?** längst upp till vänster och välj sedan **Om**.

    3. Leta upp värdet för **POP extern server** .

    4. Välj **Proxyserver** om du vill ange proxyserverinställningar för den värdbaserade Exchange-servern.
        1. Välj **Använd en proxyserver vid synkronisering av information om mobila enheter**.

        2. Ange **proxyserverns namn** och **portnummer** som används för att logga in på servern.

        3. Om det är nödvändigt att ange autentiseringsuppgifter för att ansluta till proxyservern väljer du **Använd autentiseringsuppgifter för att ansluta till proxyservern**. Ange **domän\användare** och **lösenordet**.

        4. Välj **OK**.

    5. I fälten **Användare (domän\användare)** och **Lösenord** anger du autentiseringsuppgifterna som krävs för att ansluta till Exchange-servern.

    6.  Ange de autentiseringsuppgifter som krävs för att skicka meddelanden till en användares Exchange Server-postlåda. Den här användaren kan vara dedikerad till enbart meddelanden. Meddelandeanvändaren behöver en Exchange-postlåda för att kunna skicka meddelanden via e-post. Du kan konfigurera dessa meddelanden med villkorliga åtkomstprinciper i Intune.  

        Kontrollera att tjänsten för automatisk upptäckt och Exchange Web Services har konfigurerats på Exchange-klientåtkomstservern. Mer information finns i avsnittet om [klientåtkomstservern](https://technet.microsoft.com/library/dd298114.aspx).

    7.  I fältet **Lösenord** anger du lösenordet för detta konto för att möjliggöra för Intune att ansluta till Exchange-servern.

    8. Välj **Anslut**.

    > [!NOTE]
    > Det kan ta några minuter innan anslutningen har konfigurerats.

Under konfigurationen lagrar Exchange Connector dina proxyinställningar för att möjliggöra åtkomst till Internet. Om proxyinställningarna ändras måste du konfigurera om Exchange Connector för att kunna tillämpa de uppdaterade proxyinställningarna på Exchange Connector.

När Exchange Connector har konfigurerat anslutningen synkroniseras automatiskt mobila enheter som är kopplade till användare som hanteras i Exchange Connector och läggs till i Exchange Connector. Synkroniseringen kan ta lite tid att slutföra.

> [!NOTE]
> Om du har installerat den lokala Exchange Connector och du någon gång tar bort Exchange-anslutningen måste du avinstallera den lokala anslutningen från datorn där programmet installerades.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram 
När Exchange-anslutningsappen skapar en anslutning till Exchange med angiven CAS, har anslutningsappen möjlighet att identifiera andra CAS. Om den primära certifikatutfärdaren blir otillgänglig, kommer anslutningsappen att växla till en annan certifikatutfärdare, om tillgänglig, tills den primära certifikatutfärdaren blir tillgänglig. Som standard är den här funktionen aktiverad. Du kan inaktivera funktionen med hjälp av följande procedur:
1. På servern där Exchange Connector är installerad går du till %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Med en textredigerare öppnar du **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Ändra &lt;IsCasFailoverEnabled&gt;**SANT**&lt;/IsCasFailoverEnabled&gt; till &lt;IsCasFailoverEnabled&gt;**false** &lt;/IsCasFailoverEnabled&gt; för att inaktivera funktionen.    


## <a name="monitor-the-exchange-connector-activity"></a>Övervaka Exchange Connector-aktiviteten

När du har konfigurerat Exchange Connector kan du se status för anslutningen och det senaste lyckade synkroniseringsförsöket. Verifiera Exchange Connector-anslutningen:

1. Välj **Lokal åtkomst** på Intune-instrumentpanelen.
2. Verifiera anslutningsstatusen genom att välja **Lokal Exchange-åtkomst** under **Hantera**.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.

### <a name="system-center-operations-manager-scom-management-pack"></a>Hanteringspaket för System Center Operations Manager (SCOM)

Från och med versionen Intune 1710 kan du använda [SCOM-hanteringspaketet för Exchange Connector och Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Det ger dig flera olika sätt att övervaka Exchange Connector när du behöver felsöka problem.

## <a name="next-steps"></a>Nästa steg
[Skapa en princip för villkorlig åtkomst för lokal Exchange](conditional-access-exchange-create.md)
