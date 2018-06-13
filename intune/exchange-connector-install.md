---
title: Konfigurera Microsoft Intune lokalt med Exchange Connector
titleSuffix: ''
description: Använd din lokala Exchange Connector till att hantera enhetsåtkomst till Exchange-postlådor baserat på Intune-registrering och Exchange Active Sync (EAS).
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7de97ac8a9149d2574bbc97df67408f85b243a11
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744694"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Konfigurera den lokala Exchange-anslutningsappen för Intune i Microsoft Intune Azure

I en lokal Exchange Server-miljö kan du använda villkorsstyrd Intune-åtkomst när du vill tillåta eller blockera åtkomst till lokala Exchange-postlådor. Med lokala Exchange Active Sync-anslutningsappar kan du ansluta Intune till dina Exchange-organisationer och ställa in villkorsstyrd åtkomst till Intune samt efterlevnadsprinciper för enheterna. När en enhet sedan försöker ansluta till Exchange avgör Intune om enheten är registrerad i Intune och är kompatibel. Den lokala Exchange-anslutningsappen fastställer vilka enheter som är registrerade i Intune genom att mappa EAS-posterna (Exchange Active Sync) i Exchange Server till Intune-poster. Du kan läsa mer om hur det här fungerar i [Hur används villkorlig åtkomst vanligtvis med Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune har nu stöd för flera lokala Exchange-anslutningar per prenumeration. Om du har fler än en lokal Exchange-organisation kan du ställa in en separat anslutningsapp för varje Exchange-organisation.

Om du vill konfigurera en anslutning som gör det möjligt för Microsoft Intune att kommunicera med den lokala Exchange-servern ska du följa anvisningarna nedan:

1.  Ladda ned den lokala Exchange-anslutningsappen för Intunes från Azure Portal.
2.  Installera och konfigurera Exchange-anslutningsappen på en dator i den lokala Exchange-organisationen.
3.  Verifiera Exchange-anslutningen.
4. Upprepa dessa steg för varje Exchange-organisation du vill ansluta till Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Krav för den lokala Exchange-anslutningsappen för Intune
Följande tabell innehåller kraven för datorn där du installerar den lokala Exchange-anslutningsappen.


|            Krav             |                                                                                                                                                                                                        Mer information                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Operativsystem          |                                                               Intune har stöd för den lokala Exchange-anslutningsappen på datorer som kör någon utgåva av Windows Server 2008 SP2 64-bitars, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 eller Windows Server 2016.<br /><br />Anslutningen stöds inte i Server Core-installationen.                                                                |
|         Microsoft Exchange         |                                                                           För lokala anslutningar krävs Microsoft Exchange 2010 SP1 eller senare, eller äldre Exchange Online Dedicated. Om du vill ta reda på om Exchange Online Dedicated-miljön har den <strong>nya</strong> eller <strong>äldre</strong> konfigurationen kontaktar du din kontoansvariga.                                                                           |
| Utfärdare för hantering av mobila enheter |                                                                                                                              [Ange utfärdare för hantering av mobila enheter till Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              Maskinvara              |                                                                                                                                                     Datorn där du installerar anslutningen måste ha en 1,6 GHz-processor med 2 GB RAM-minne och 10 GB ledigt diskutrymme.                                                                                                                                                      |
|  Active Directory-synkronisering  |                                                                                      Innan du kan använda anslutningsappen för att ansluta Intune till Exchange Server måste du [konfigurera Active Directory-synkronisering](users-add.md) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans.                                                                                      |
|        Tilläggsprogramvara         |                                                                                                                                           En fullständig installation av Microsoft .NET Framework 4.5 och Windows PowerShell 2.0 måste installeras på den dator som är värd för anslutningen.                                                                                                                                           |
|              Nätverk               | Datorn där du installerar anslutningen måste finnas i en domän som har en förtroenderelation till domänen som är värd för Exchange Server.<br /><br />Datorn kräver konfigurationer för att kunna komma åt Intune-tjänsten genom brandväggar och proxyservrar via portarna 80 och 443. Exempel på domäner som används av Intune är manage.microsoft.com, &#42;manage.microsoft.com och &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Krav för Exchange-cmdlet

Du måste skapa ett Active Directory-användarkonto som används av den lokala Exchange-anslutningsappen. Kontot måste ha behörighet att köra följande obligatoriska Exchange för Windows PowerShell-cmdlets:


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Ladda ner installationspaketet för den lokala Exchange-anslutningsappen

1. I ett Windows Server-operativsystem som stöder den lokala Exchange-anslutningsappen öppnar du [Azure Portal](http://portal.azure.com) och loggar in med ett användarkonto som är administratör på den lokala Exchange-servern och som har licens för att använda Exchange Server.

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune** och sedan **Lokal åtkomst** när Intune-instrumentpanelen öppnas.

4. Under **Installation** väljer du **Exchange ActiveSync-kopplingar** och sedan **alternativet för att ladda ned den lokala anslutningsappen**.

5.  Den lokala Exchange-anslutningsappen finns i en komprimerad mapp (.zip) som kan öppnas eller sparas. I dialogrutan **Filhämtning** klickar du på **Spara** för att spara den komprimerade mappen på en säker plats.

    > [!IMPORTANT]
    > Byt inte namn på eller flytta filerna i mappen för den lokala Exchange-anslutningsappen. Installationen av Exchange-anslutningsappen misslyckas om du flyttar eller byter namn på mappens innehåll.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installera och konfigurera den lokala Exchange-anslutningsappen för Intune
Utför följande steg för att installera den lokala Exchange-anslutningsappen för Intune: Om du har flera Exchange-organisationer ska du upprepa dessa steg för varje ytterligare Exchange-anslutningsapp du vill konfigurera.

1. Använd ett operativsystem med stöd för den lokala Exchange-anslutningsappen och extrahera filerna i **Exchange_Connector_Setup.zip** till en säker plats.

2. När filerna har extraherats öppnar du den extraherade mappen och dubbelklickar på **Exchange_Connector_Setup.exe** för att installera den lokala Exchange-anslutningsappen.

   > [!IMPORTANT]
   > Om målmappen inte är en säker plats bör du ta bort certifikatfilen **MicrosoftIntune.accountcert** när du har installerat de lokala anslutningsapparna.

3. I dialogrutan **Microsoft Intune Exchange Connector** väljer du antingen **On-premises Microsoft Exchange Server** eller **Hosted Microsoft Exchange Server**.

   ![Bild som visar var du väljer Exchange Server-typ](./media/intune-sa-exchange-connector-config.png)

   För en lokal Exchange-server anger du antingen servernamnet eller det fullständigt kvalificerade domännamnet för Exchange-servern som är värd för **klientåtkomstserverrollen**.

   För en värdbaserad Exchange-server anger du adressen till Exchange-servern. Så här hittar du URL-adressen till den värdbaserade Exchange-servern:

   1. Öppna Outlook på webben för Office 365.

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

Under konfigurationen lagrar Exchange-anslutningsappen dina proxyinställningar för att möjliggöra åtkomst till internet. Om proxyinställningarna ändras måste du konfigurera om Exchange-anslutningsappen för att kunna använda de uppdaterade proxyinställningarna i Exchange-anslutningsappen.

När Exchange-anslutningsappen har konfigurerat anslutningen synkroniseras automatiskt mobila enheter som är kopplade till användare som hanteras i Exchange, och läggs till i Exchange-anslutningsappen. Synkroniseringen kan ta lite tid att slutföra.

> [!NOTE]
> Om du har installerat den lokala Exchange-anslutningsappen och du någon gång tar bort Exchange-anslutningen måste du avinstallera den lokala Exchange-anslutningsappen från datorn där den installerades.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installera anslutningsappar för flera Exchange-organisationer
Intune har stöd för flera lokala Exchange-anslutningsappar per prenumeration. För en klientorganisation med flera Exchange-organisationer kan du konfigurera en anslutningsapp för varje Exchange-organisation. Hämta .zip-mappen en gång och följ sedan stegen i föregående avsnitt så att du extraherar och kör installationsprogrammet på en server för varje Exchange-organisation.

Funktionerna för hög tillgänglighet, övervakning och manuell synkronisering som beskrivs i följande avsnitt stöds för varje Exchange-organisation som är ansluten till Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram 
När Exchange-anslutningsappen skapar en anslutning till Exchange med angiven CAS, har anslutningsappen möjlighet att identifiera andra CAS. Om den primära certifikatutfärdaren blir otillgänglig, kommer anslutningsappen att växla till en annan certifikatutfärdare, om tillgänglig, tills den primära certifikatutfärdaren blir tillgänglig. Som standard är den här funktionen aktiverad. Du kan inaktivera funktionen med hjälp av följande procedur:
1. På servern där Exchange Connector är installerad går du till %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Med en textredigerare öppnar du **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Ändra &lt;IsCasFailoverEnabled&gt;**SANT**&lt;/IsCasFailoverEnabled&gt; till &lt;IsCasFailoverEnabled&gt;**false** &lt;/IsCasFailoverEnabled&gt; för att inaktivera funktionen.    


## <a name="monitor-the-exchange-connector-activity"></a>Övervaka Exchange Connector-aktiviteten

När du har konfigurerat dina Exchange-anslutningsappar kan du se status för anslutningarna och det senaste lyckade synkroniseringsförsöket. Så här verifierar du anslutningar via Exchange-anslutningsappar:

1. Välj **Lokal åtkomst** på Intune-instrumentpanelen.
2. Under **Installation** väljer du **Exchange ActiveSync-kopplingar** och verifierar statusen för varje Exchange-anslutningsapp.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.

### <a name="system-center-operations-manager-scom-management-pack"></a>Hanteringspaket för System Center Operations Manager (SCOM)

Från och med versionen Intune 1710 kan du använda [SCOM-hanteringspaketet för Exchange Connector och Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Det ger dig flera olika sätt att övervaka Exchange Connector när du behöver felsöka problem.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Tvinga en snabbsynkronisering eller en fullständig synkronisering manuellt
En lokal Exchange-anslutningsapp synkroniserar automatiskt och regelbundet EAS- och Intune-enhetsposterna. Om kompatibilitetsstatusen för en enhet ändras uppdateras posterna i den automatiska synkroniseringsprocessen så att enheten kan blockeras eller tillåtas.

   - **Snabbsynkroniseringar** görs regelbundet flera gånger om dagen. Vid en snabbsynkronisering hämtas enhetsinformation för Intune-licensierade och lokala, villkorsstyrda Exchange-användare som har ändrats sedan den senaste synkroniseringen.

   - En **fullständig synkronisering** görs en gång per dygn som standard. Vid en fullständig synkronisering hämtas enhetsinformation för alla Intune-licensierade och lokala, villkorsstyrda Exchange-användare. Vid en fullständig synkronisering hämtas även information om Exchange-servern, och dessutom garanteras att bara den konfiguration som angetts av Intune på Azure Portal uppdateras på Exchange-servern. 

Du kan tvinga en synkronisering för en anslutningsapp med alternativen **Snabbsynkronisering** eller **Fullständig synkronisering** Intune-instrumentpanel så här:

   1. Välj **Lokal åtkomst** på Intune-instrumentpanelen.
   2. Under **Installation** väljer du **Exchange Active Sync-kopplingar**.
   3. Välj den anslutningsapp du vill synkronisera och välj sedan **Snabbsynkronisering** eller **Fullständig synkronisering**.

## <a name="next-steps"></a>Nästa steg
[Skapa en princip för villkorlig åtkomst för lokal Exchange](conditional-access-exchange-create.md)
