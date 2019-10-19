---
title: Felsök vanliga fel för Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Felsök och lös vanliga fel för den lokala Microsoft Intune Exchange Connector
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: b30a7e843850d6918abc2e76f84397a1f197516f
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508859"
---
# <a name="resolve-common-errors-for-the-intune-exchange-connector"></a>Lösa vanliga fel för Intune Exchange Connector

Den här artikeln kan hjälpa Intune-administratören att lösa vissa fel och meddelanden om driften av Intune Exchange Connector.  

## <a name="configuration-failed-and-returned-error-code-0x0000001"></a>Konfigurationen misslyckades och returnerade felkoden 0x0000001

**Problem**:  
När du försöker konfigurera Microsoft Intune Exchange Connector får du följande fel meddelande:

```
   The Microsoft Intune Exchange Connector cannot connect to the Microsoft Exchange server.  
   The following Microsoft Exchange Server address could not be reached <Exchange server Name FQDN>  
   Verify that the FQDN of the exchange server address and credentials that you entered is correct and the server is running. The Microsoft Intune Exchange Connector does not support Exchange server arrays.  
   Error code: 0x0000001  
```

Det här problemet kan uppstå om proxyinställningarna för Internet är felkonfigurerade.

**Lösning**:  
Konfigurera proxyinställningar:
1. Kontakta den lokala nätverks administratören för att se till att proxyinställningarna är korrekt konfigurerade. 
2. Använd kommandot **netsh WinHTTP** för att konfigurera proxyservern och lägga till den undantags lista som krävs. Exempel:  

   ```
   Netsh winhttp set proxy proxy-server="http=proxy.corp.domain.com" bypass-list"34*.*;134.132.*.*;10.*.*;localhost;*.corp.domain.com;*.staging.domain.com"
   ```

## <a name="configuration-failed-and-returned-error-code-0x000000b"></a>Konfigurationen misslyckades och returnerade felkoden 0x000000b   

**Problem**:  
När du försöker konfigurera Microsoft Intune Exchange Connector får du följande fel meddelande:  

```
   The Microsoft Intune Exchange Connector experienced an error:  
   CertEnroll::CX509PrivateKey::Create: The system cannot find the file specified. 0x80070002 (WIN32: 2  
   ERROR_FILE_NOT_FOUND  
   Error code: 0x000000b  
```
Det här problemet kan uppstå om kontot som du använde för att logga in på Intune inte är ett globalt administratörs konto för Intune.

**Lösning**:  
Logga in på Intune med ett konto som är en global administratör eller Lägg till ditt konto i den globala administratörs gruppen. Mer information finns i [Rollbaserad administrationskontroll (RBAC) med Microsoft Intune](../fundamentals/role-based-access-control.md).

## <a name="configuration-failed-and-returned-error-code-0x0000006"></a>Konfigurationen misslyckades och returnerade felkoden 0x0000006

**Problem**:  
När du försöker konfigurera Microsoft Intune Exchange Connector får du följande fel meddelande:  

```  
   The Microsoft Intune Exchange Connector cannot connect to Microsoft Intune  
   Verify that you are connected to the Internet, check the Microsoft Intune Service Status, and try to connect again.  
   Error code: 0x00000006  
```  
Det här felet kan inträffa om en proxyserver används för att ansluta till Internet och blockerar trafik till Intune-tjänsten. För att avgöra om en proxyserver används, går du till **kontroll panelen**  > **Internet alternativ**, väljer fliken **anslutning** och klickar sedan på **LAN-inställningar**.

**Lösning**:  

- **Alternativ 1** – ta bort proxyinställningarna så att datorn kan ansluta till Internet utan att gå via proxyservern.  

- **Alternativ 2** – Konfigurera proxyservern för att tillåta kommunikation till Intune-tjänsten, enligt beskrivningen i [krav för Intune Exchange Connector](exchange-connector-install.md#intune-exchange-connector-requirements).



## <a name="event-7000-or-7041-microsoft-intune-exchange-connector-service-wont-start"></a>Händelse 7000 eller 7041: Microsoft Intune Exchange Connector tjänsten startar inte

**Problem**:  
En iOS-enhet kan inte registreras i Intune och genererar något av följande fel meddelanden:  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Task Category: None
   Level:               Error
   Keywords:        Classic
   User:                N/A
   Computer:      <computer>
   Description:
   The Microsoft Intune Exchange Connector Service service failed to start because of the following error:  
   The service did not start because of a logon failure.
```  

```  
   Log Name:      System
   Source:            Service Control Manager
   Date:               <time>
   Event ID:          7041
   Task Category: None
   Level:               Error   
   Keywords:        Classic
   User:                N/A
   Computer:       <computer>
   Description:
   The WIEC service was unable to log on as .\WIEC_USER with the currently configured password because of the following error:
   Logon failure: the user has not been granted the requested logon type at this computer.
   Service: WIEC
   Domain and account: .\WIEC_USER
   This service account does not have the required user right "Log on as a service."  
```
Det här problemet kan uppstå om **WIEC_User** -kontot inte har användar rättigheten **Logga in som tjänst** i den lokala principen.

**Lösning**:  
På den dator som kör Intune Exchange Connector tilldelar du kontot **Logga in som en tjänst** användare till **WIEC_User** -tjänstkontot. Om datorn är en nod i ett kluster ser du till att tilldela kontot för att *Logga in som en tjänst* användare till kluster tjänst kontot på alla noder i klustret.  

Följ dessa steg om du vill koppla användar rättigheten **Logga in som en tjänst** till **WIEC_User** -tjänstkontot på datorn:

1. Logga in på datorn som administratör eller som medlem i gruppen Administratörer.
2. Kör **secpol. msc** för att öppna den lokala säkerhets principen.
3. Gå till **säkerhets inställningar**  > **lokala principer**och välj sedan **tilldelning av användar rättigheter**.
4. I den högra rutan dubbelklickar du på **Logga in som en tjänst**.
5. Välj **Lägg till användare eller grupp**, Lägg till **WIEC_USER** i principen och välj sedan **OK** två gånger.

Kontakta domän administratören för att ta reda på om en grupprincips inställning skrivs över om användaren **loggar in som en tjänst** användare rättigheten har tilldelats **WIEC_User** , men senare togs bort.  

## <a name="next-steps"></a>Nästa steg  

Följande artikel kan hjälpa dig att lösa vissa fel:
- [Lös vanliga problem för Intune Exchange Connector](troubleshoot-exchange-connector-common-problems.md). git 

Kontakta hjälp från support eller Intune-communityn.
- Se [få support](../fundamentals/get-support.md) för att felsöka problemet med hjälp av Intune-konsolen eller att öppna ett support ärende med Microsoft. 
- Publicera ditt problem i [Microsoft Intune forum](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
