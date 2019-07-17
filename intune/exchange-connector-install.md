---
title: Konfigurera Microsoft Intune lokalt med Exchange Connector
titleSuffix: Microsoft Intune
description: Använd din lokala Exchange Connector till att hantera enhetsåtkomst till Exchange-postlådor baserat på Intune-registrering och Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7663009c7d45171ab6469f7f6e96b4c8f979b744
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883286"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Konfigurera den lokala Exchange-anslutningsappen för Intune i Microsoft Intune
Informationen i den här artikeln hjälper dig att installera och sedan övervaka den lokala Exchange Active Sync-anslutningsappen för Intune.  Du använder den lokala Exchange-anslutningsappen för Intune med dina [principer för villkorlig åtkomst för att tillåta eller blockera åtkomst till Exchange On-Premises-postlådor](conditional-access-exchange-create.md). 

När en enhet försöker ansluta till ditt lokala Exchange mappar Exchange-anslutningsappen EAS-poster (Exchange Active Sync) i Exchange Server till Intune-poster för att söka efter enhetsregistrering med Intune och efterlevnad med dina principer för enhetsefterlevnad. Beroende på dina principer för villkorlig åtkomst, kan enheten tillåtas åtkomst eller blockeras. Mer information finns i [Hur används villkorlig åtkomst vanligtvis med Intune?](conditional-access-intune-common-ways-use.md)

Intune har stöd för installation av flera lokala Exchange-anslutningsappar per prenumeration. Om du har fler än en lokal Exchange-organisation kan du konfigurera en separat anslutningsapp för varje sådan. Dock kan bara en anslutning installeras för varje enskild Exchange-organisation. 

Följande är de allmänna stegen för att konfigurera en anslutning som gör att Intune kan kommunicera med den lokala Exchange-servern:

1. Ladda ned den lokala Exchange-anslutningsappen från Intune-portalen.
2. Installera och konfigurera Exchange-anslutningsappen på en dator i den lokala Exchange-organisationen.
3. Verifiera Exchange-anslutningen.
4. Upprepa dessa steg för varje ytterligare Exchange-organisation som du vill ansluta till Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Krav för den lokala Exchange-anslutningsappen för Intune
Du behöver ett konto med en Intune-licens som kan användas av anslutningsappen för att ansluta till Exchange. Kontot anges när du installerar anslutningsappen.  

Följande tabell innehåller kraven för datorn där du installerar den lokala Exchange-anslutningsappen.  

|  Krav  |   Mer information     |
|---------------|------------------------|
|  Operativsystem        | Intune har stöd för den lokala Exchange-anslutningsappen på datorer som kör någon utgåva av Windows Server 2008 SP2 64-bitars, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 eller Windows Server 2016.<br /><br />Anslutningsappen stöds inte i Server Core-installationer.  |
| Microsoft Exchange          | För lokala anslutningar krävs Microsoft Exchange 2010 SP3 eller senare, eller äldre Exchange Online Dedicated. Om du vill ta reda på om Exchange Online Dedicated-miljön har den <strong>nya</strong> eller <strong>äldre</strong> konfigurationen kontaktar du din kontoansvariga. |
| Utfärdare för hantering av mobila enheter           | [Ange utfärdare för hantering av mobila enheter till Intune](mdm-authority-set.md). |
| Maskinvara              | Datorn där du installerar anslutningen måste ha en 1,6 GHz-processor med 2 GB RAM-minne och 10 GB ledigt diskutrymme. |
|  Active Directory-synkronisering             | Innan du kan använda anslutningsappen för att ansluta Intune till Exchange Server måste du [konfigurera Active Directory-synkronisering](users-add.md) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans. |
| Tilläggsprogramvara         | En fullständig installation av Microsoft .NET Framework 4.5 och Windows PowerShell 2.0 måste installeras på den dator som är värd för anslutningen. |
| Nätverk               | Datorn där du installerar anslutningen måste finnas i en domän som har en förtroenderelation till domänen som är värd för Exchange Server.<br /><br />Datorn kräver konfigurationer för att kunna komma åt Intune-tjänsten genom brandväggar och proxyservrar via portarna 80 och 443. Exempel på domäner som används av Intune är manage.microsoft.com, &#42;manage.microsoft.com och &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Krav för Exchange-cmdlet

Skapa ett Active Directory-användarkonto som ska användas av den lokala Exchange-anslutningsappen. Kontot måste ha behörighet att köra följande obligatoriska Exchange för Windows PowerShell-cmdlets:


- Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
- Get-CasMailbox, Set-CasMailbox
- Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
- Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
- Get-ActiveSyncDeviceStatistics
- Get-ActiveSyncDevice
- Get-ExchangeServer
- Get-ActiveSyncDeviceClass
- Get-Recipient
- Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
- Set-ADServerSettings
- Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Ladda ner installationspaketet för den lokala Exchange-anslutningsappen

1. I ett Windows Server-operativsystem som stöder den lokala Exchange-anslutningsappen öppnar du [Azure Portal](https://portal.azure.com) och loggar in med ett användarkonto som är administratör på den lokala Exchange-servern och som har licens för att använda Exchange Server.

2. Gå till **Intune** > **Exchange-åtkomst**  

3. Under **Installation** väljer du **Lokal Exchange ActiveSync-anslutningsapp** och sedan **Lägg till**.

4. På sidan **Lägg till anslutningsapp** väljer du **Ladda ned den lokala anslutningsappen**. Den lokala Exchange-anslutningsappen finns i en komprimerad mapp (.zip) som kan öppnas eller sparas. I dialogrutan **Filhämtning** klickar du på **Spara** för att spara den komprimerade mappen på en säker plats.

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

   För en on-premises Exchange-server anger du antingen servernamnet eller det fullständigt kvalificerade domännamnet för Exchange-servern som är värd för **klientåtkomstserverrollen**.

   För en värdbaserad Exchange-server anger du adressen till Exchange-servern. Så här hittar du URL-adressen till den värdbaserade Exchange-servern:

   1. Öppna Outlook på webben för Office 365.

   2. Välj ikonen **?** längst upp till vänster och välj sedan **Om**.

   3. Leta upp värdet för **POP extern server** .

   4. Välj **Proxyserver** om du vill ange proxyserverinställningar för den värdbaserade Exchange-servern.
       1. Välj **Använd en proxyserver vid synkronisering av information om mobila enheter**.

       2. Ange **proxyserverns namn** och **portnummer** som används för att logga in på servern.

       3. Om det är nödvändigt att ange autentiseringsuppgifter för att ansluta till proxyservern väljer du **Använd autentiseringsuppgifter för att ansluta till proxyservern**. Ange **domän\användare** och **lösenordet**.

       4. Välj **OK**.

4. I fälten **Användare (domän\användare)** och **Lösenord** anger du autentiseringsuppgifterna som krävs för att ansluta till Exchange-servern. Det konto som du anger måste ha en licens för att använda Intune. 

5. Ange de autentiseringsuppgifter som krävs för att skicka meddelanden till en användares Exchange Server-postlåda. Den här användaren kan vara dedikerad till enbart meddelanden. Meddelandeanvändaren behöver en Exchange-postlåda för att skicka meddelanden via e-post. Du kan konfigurera dessa meddelanden med principer för villkorlig åtkomst i Intune.  

       Ensure that the Autodiscover service and Exchange Web Services are configured on the Exchange Client Access Server. For more information, see [Client Access server](https://technet.microsoft.com/library/dd298114.aspx).

6. I fältet **Lösenord** anger du lösenordet för detta konto för att möjliggöra för Intune att ansluta till Exchange-servern.

7. Välj **Anslut**.

   > [!NOTE]
   > Det kan ta några minuter innan anslutningen har konfigurerats.

Under konfigurationen lagrar Exchange-anslutningsappen dina proxyinställningar för att möjliggöra åtkomst till internet. Om proxyinställningarna ändras måste du konfigurera om Exchange-anslutningsappen för att kunna använda de uppdaterade proxyinställningarna i Exchange-anslutningsappen.

När Exchange-anslutningsappen har konfigurerat anslutningen synkroniseras automatiskt mobila enheter som är kopplade till användare som hanteras i Exchange, och läggs till i Exchange-anslutningsappen. Synkroniseringen kan ta lite tid att slutföra.

> [!NOTE]
> Om du har installerat den lokala Exchange-anslutningsappen och du någon gång tar bort Exchange-anslutningen måste du avinstallera den lokala Exchange-anslutningsappen från datorn där den installerades.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installera anslutningsappar för flera Exchange-organisationer
Intune har stöd för flera lokala Exchange-anslutningsappar per prenumeration. För en klientorganisation med flera Exchange-organisationer kan du konfigurera en anslutningsapp för varje Exchange-organisation, men endast en enda anslutningsapp för en enskild organisation. 

Om du kommer att installera anslutningsappar för att ansluta till flera Exchange-organisationer laddar du ned .zip-mappen en gång och återanvänder sedan samma nedladdning för varje anslutningsapp som du installerar. För varje ytterligare anslutningsapp följer du stegen i föregående avsnitt för att extrahera och köra installationsprogrammet på en server i Exchange-organisationen.

De funktioner för hög tillgänglighet, övervakning och manuell synkronisering som beskrivs i följande avsnitt stöds för varje Exchange-organisation som ansluter till Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Support med hög tillgänglighet för lokalt Exchange-anslutningsprogram 
Hög tillgänglighet för den lokala Exchange-anslutningsappen innebär att om den Exchange-CAS (Client Access Server) som anslutningsappen använder slutar vara tillgänglig så kan anslutningsappen växla över till en annan CAS för den Exchange-organisationen. Exchange-anslutningsappen i sig har inte stöd för hög tillgänglighet. Om anslutningsappen slutar fungera finns det ingen automatisk redundans, och du måste då byta ut den anslutningsappen genom att [installera en ny anslutningsapp](#reinstall-the-on-premises-exchange-connector). 

För att utföra redundans upptäcker anslutningsappen ytterligare CAS för den Exchange-organisationen efter att anslutningsappen har skapat en lyckad anslutning till Exchange via angiven CAS. Vetskap om ytterligare CAS gör att anslutningsappen kan redundansväxla till en annan CAS om en sådan finns tills den primära CAS blir tillgänglig. Som standard är identifiering av ytterligare CAS aktiverad. Du kan inaktivera redundans med hjälp av följande procedur:  
1. På den server där Exchange-anslutningsappen är installerad går du till %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Med en textredigerare öppnar du **OnPremisesExchangeConnectorServiceConfiguration.xml**.
3. Ändra &lt;IsCasFailoverEnabled&gt;**SANT**&lt;/IsCasFailoverEnabled&gt; till &lt;IsCasFailoverEnabled&gt;**false** &lt;/IsCasFailoverEnabled&gt; för att inaktivera funktionen.    
 

## <a name="reinstall-the-on-premises-exchange-connector"></a>Installera om den lokala Exchange-anslutningsappen
Du kan behöva installera om en Exchange-anslutningsapp. Eftersom en enda anslutningsapp stöds för anslutning till varje Exchange-organisation gäller att om du installerar en andra anslutningsapp för en organisation så ersätter den nya anslutningsapp som du installerar den ursprungliga anslutningsappen.

1. Använd stegen från [Installera och konfigurera den lokala Exchange-anslutningsappen för Intune](#install-and-configure-the-intune-on-premises-exchange-connector) för att starta installationen av den nya anslutningsappen. 
2. När du uppmanas väljer du **Ersätt** för att installera den nya anslutningsappen.  
   ![Konfigurationsuppmaning om att ersätta en anslutningsapp](./media/exchange-connector-install/prompt-to-replace.png)

3. Fortsätt med hjälp av stegen från föregående procedur och logga in på Intune.
4. När den sista skärmen visas väljer du **Stäng** för att slutföra installationen.  
   ![Slutföra installationen](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Övervaka Exchange Connector-aktiviteten

När du har konfigurerat Exchange-anslutningsappen kan du se status för anslutningarna och det senaste lyckade synkroniseringsförsöket. Så här verifierar du anslutningen för Exchange-anslutningsappen:

1. På Intune-instrumentpanelen väljer du **Exchange-åtkomst**.
2. Verifiera **Lokal Exchange-åtkomst** för att verifiera anslutningsstatusen för varje Exchange-anslutningsapp.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.
--> 

### <a name="system-center-operations-manager-management-pack"></a>Hanteringspaket för System Center Operations Manager

Från och med versionen Intune 1710 kan du använda [Operations Manager-hanteringspaketet för Exchange Connector och Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True). Genom att använda hanteringspaketet får du flera olika sätt att övervaka Exchange-anslutningsappen när du behöver felsöka problem.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Tvinga en snabbsynkronisering eller en fullständig synkronisering manuellt
En lokal Exchange Connector synkroniserar automatiskt och regelbundet EAS- och Intune-enhetsposterna. Om efterlevnadsstatusen för en enhet ändras uppdaterar den automatiska synkroniseringsprocessen posterna regelbundet så att enhetsåtkomst kan blockeras eller tillåtas.

- **Snabbsynkroniseringar** görs regelbundet flera gånger om dagen. Vid en snabbsynkronisering hämtas enhetsinformation för Intune-licensierade och lokala Exchange-användare med villkorlig åtkomst.

- En **fullständig synkronisering** görs en gång per dygn som standard. Vid en fullständig synkronisering hämtas enhetsinformation för alla Intune-licensierade och lokala Exchange-användare med villkorlig åtkomst. Vid en fullständig synkronisering hämtas även information om Exchange-servern, och dessutom garanteras att bara den konfiguration som angetts av Intune på Azure Portal uppdateras på Exchange-servern. 


Du kan tvinga en synkronisering för en anslutningsapp med alternativen **Snabbsynkronisering** eller **Fullständig synkronisering** Intune-instrumentpanel så här:

   1. På Intune-instrumentpanelen väljer du **Exchange-åtkomst**.
   2. Välj **Lokal Exchange-åtkomst**.
   3. Välj den anslutningsapp du vill synkronisera och välj sedan **Snabbsynkronisering** eller **Fullständig synkronisering**.

## <a name="next-steps"></a>Nästa steg
[Skapa en princip för villkorlig åtkomst för Exchange On-Premises](conditional-access-exchange-create.md)
