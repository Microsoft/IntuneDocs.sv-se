---
title: "Installera Microsoft Intune Exchange Connector för on-premises Exchange | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 41ff4212-a6f5-4374-8731-631f7560cff1
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 8c1f4f209c5ec704290882b8f6f71e0b1b01d21c
ms.openlocfilehash: 45f815ea379007b75316552d34f5bd8669b2ccef


---

# Installera Intune on-premises Exchange Connector


Om du vill skapa en anslutning som gör det möjligt för Microsoft Intune att kommunicera med Exchange-servern som är värd för mobila enheters postlådor måste du ladda ned och konfigurera verktyget för lokal anslutning från Intunes administratörskonsol.

## Krav för den lokala anslutningen
I följande tabell visas kraven på datorn där du installerar on-premises Exchange Connector.

|Krav|Mer information|
|---------------|--------------------|
|Operativsystem|Intune stöder on-premises Exchange Connector på datorer som kör någon utgåva av Windows Server 2008 SP2 64-bitars, Windows Server 2008 R2, Windows Server 2012 eller Windows Server 2012 R2.<br /><br />Anslutningen stöds inte i Server Core-installationen.|
|Microsoft Exchange-version|On-premises Connector kräver Microsoft Exchange 2010 SP1 eller senare.|
|Utfärdare för hantering av mobila enheter| [Ange utfärdare för hantering av mobila enheter till Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority).|
|Maskinvara|Datorn där du installerar anslutningen kräver en 1,6 GHz-processor med 2 GB RAM-minne och 10 GB ledigt diskutrymme.|
|Active Directory-synkronisering|Innan du kan använda endera Connector för att ansluta Intune till Exchange Server måste du [konfigurera Active Directory-synkronisering](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans.|
|Tilläggsprogramvara|En fullständig installation av Microsoft .NET Framework 4 och Windows PowerShell 2.0 måste installeras på den dator som är värd för anslutningen.|
|Nätverk|Datorn där du installerar anslutningen måste finnas i en domän som har en förtroenderelation till domänen som är värd för Exchange Server.<br /><br />Datorn kräver konfigurationer för att kunna komma åt Intune-tjänsten genom brandväggar och proxyservrar via portarna 80 och 443. Exempel på domäner som används av Intune är manage.microsoft.com, &#42;manage.microsoft.com och &#42;.manage.microsoft.com.|
|Värdbaserad Exchange konfigurerad och körs|Se [Exchange Server 2016](https://technet.microsoft.com/library/mt170645.aspx) för mer information. |
|Ange utfärdare för hantering av mobila enheter till Intune|[Ange utfärdare för mobila enheter till Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|

### Krav för Exchange-cmdlet

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

## Ladda ner programinstallationspaketet för on-premises Exchange Connector

1. På ett operativsystem med stöd för on-premises Exchange Connector, öppna [administrationskonsolen för Microsoft Intunes](http://manage.microsoft.com) (http://manage.microsoft.com) med ett användarkonto som är en administratör i Exchange-klienten med en licens för att använda Exchange Server.
![Öppna Konfigurera Exchange Connection](../media/ExchangeConnector.gif)

2.  I fönstret med genvägar för arbetsytan väljer du **ADMIN**.

3.  Under **Hantering av mobila enheter** i navigeringsfönstret expanderar du **Microsoft Exchange** och klickar sedan på **Konfigurera Exchange Connection**.

4.  På sidan **Konfigurera Exchange-anslutning** väljer du **Hämta lokal anslutning**.

5.  On-premises Exchange Connector finns i en komprimerad mapp (.zip) som kan öppnas eller sparas. I dialogrutan **Filhämtning** klickar du på **Spara** för att spara den komprimerade mappen på en säker plats.

> [!IMPORTANT]
> Byt inte namn på eller flytta filerna i on-premises Exchange Connector-mappen. Om du flyttar eller byter namn på innehållet i mappen kommer installationen inte fungera korrekt.

## Installera och konfigurera Intune on-premises Exchange Connector
Utför följande steg för att installera Intune on-premises Exchange Connector. On-premises Exchange Connector kan bara installeras en gång per Intune-prenumeration och bara på en dator. Om du försöker konfigurera ytterligare en on-premises Exchange Connector ersätts den ursprungliga anslutningen med den nya.

1.  På ett operativsystem med stöd för On-Premises Connector, extrahera filerna i **Exchange_Connector_Setup.zip** till en säker plats.

2.  När filerna har extraherats öppnar du den extraherade mappen och dubbelklickar på **Exchange_Connector_Setup.exe** för att installera on-premises Exchange Connector.

    > [!IMPORTANT]
    > Om målmappen inte är en säker plats bör du ta bort certifikatfilen **WindowsIntune.accountcert** när du har installerat den lokala anslutningen.

3.  I fältet **Exchange-server** väljer du typen av Exchange-servermiljö, antingen **On-premises Microsoft Exchange Server** eller **Värdbaserad Microsoft Exchange Server**.

  ![Välj din Exchange Server-typ](../media/IntuneSA1dconfigureExchConnector.png)

  För en on-premises Exchange-server anger du antingen servernamnet eller det fullständigt kvalificerade domännamnet för Exchange-servern som är värd för **klientåtkomstserverrollen**.

  För en värdbaserad Exchange-server anger du adressen till Exchange-servern. Så här hittar du URL-adressen till den värdbaserade Exchange-servern:

      1.  Öppna Outlook Web App för Office 365.

      2.  Välj ikonen ”?” längst upp till vänster och välj **Om**.

      3.  Leta upp värdet för **POP extern server** .

      4.  Välj **Proxyserver** om du vill ange proxyserverinställningar för den värdbaserade Exchange-servern.
        1.  Välj **Använd en proxyserver vid synkronisering av information om mobila enheter**.

        2.  Ange **proxyserverns namn** och **portnummer** som används för att logga in på servern.

        3.  Om det är nödvändigt att ange autentiseringsuppgifter för att få åtkomst till proxyservern väljer du Använd autentiseringsuppgifter för att ansluta till proxyservern och anger **domän\användare** och **lösenordet**.

        4.  Välj **OK**.

5.  Ange autentiseringsuppgifterna, **Användare (Domän\användare)** och **Lösenord** som krävs för att ansluta till Exchange-servern.

6.  Ange autentiseringsuppgifterna som krävs för att skicka aviseringar till en användares Exchange-postlåda. Dessa aviseringar kan konfigureras via principer för villkorlig åtkomst med Intune.

    Kontrollera att tjänsten för automatisk upptäckt och Exchange Web Services har konfigurerats på Exchange-klientåtkomstservern. Mer information om detta finns i [Klientåtkomstserver](https://technet.microsoft.com/library/dd298114.aspx).

7.  I fältet **Lösenord** anger du lösenordet för detta konto för att möjliggöra för Intune att ansluta till Exchange-servern.

8. Välj **Anslut**.

    Det kan ta några minuter innan anslutningen har konfigurerats.

Under konfigurationen lagrar Exchange Connector dina proxyinställningar för att möjliggöra åtkomst till Internet. Om proxyinställningarna ändras måste du konfigurera om Exchange Connector för att kunna tillämpa de uppdaterade proxyinställningarna på Exchange Connector.

När Exchange Connector har konfigurerat anslutningen synkroniseras automatiskt mobila enheter som är kopplade till användare som hanteras i Exchange Connector och läggs till i Exchange Connector. Synkroniseringen kan ta lite tid att slutföra.

> [!NOTE]
> Om du har installerat on-premises Exchange Connector och du någon gång tar bort Exchange-anslutningen måste du avinstallera den lokala anslutningen från datorn där programmet installerades.

## Validera Exchange-anslutning

När du har konfigurerat Exchange Connector kan du se status för anslutningen och det senaste lyckade synkroniseringsförsöket. I [administrationskonsolen för Microsoft Intune](http://manage.microsoft.com) väljer du arbetsytan **ADMIN** och sedan väljer du **Microsoft Exchange** under **Hantering av mobila enheter** samt kontrollerar att informationen som du angav visas under **Anslutningsinformation för Exchange**.


Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.



<!--HONumber=Jul16_HO2-->


