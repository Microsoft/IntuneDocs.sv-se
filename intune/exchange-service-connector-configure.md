---
title: Intune Exchange Connector för Exchange Online
titleSuffix: ''
description: Anslut Intune till Office 365 Exchange-tjänsten för att stödja Exchange ActiveSync MDM (mobil enhetshantering).
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 640d1a5cbd785248cb309bc250c95631295955b3
ms.sourcegitcommit: 71497f0215fc8bed454ac318b0548b1281a8fe0f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/08/2018
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Konfigurera Exchange-tjänstens anslutningsprogram för Intune och Exchange Online

Den här artikeln visar hur du ansluter Microsoft Intune-tjänsten till Exchange Online eller den nya Exchange Online Dedicated-tjänsten. Om du vill ta reda på om Exchange Online Dedicated-miljön är den **nya** eller **äldre** versionen kontaktar du din kontoansvariga.

## <a name="service-to-service-connector-requirements"></a>Krav för Service to Service Connector
**Service to Service Connector** har endast stöd för Exchange Online eller Exchange Online Dedicated och har inga krav för lokal infrastruktur.


|              Krav               |                                                                                                            Mer information                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Online konfigurerad och körs |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   Utfärdare för hantering av mobila enheter   |                                                       [Ange Microsoft Intune som utfärdare för hantering av mobila enheter](mdm-authority-set.md)                                                       |
|       Microsoft Exchange-version       |                                                                                      Exchange Online eller den nya Exchange Online Dedicated-tjänsten                                                                                      |
|    Active Directory-synkronisering    | Innan du kan använda Intune Connector måste du [konfigurera Active Directory-synkronisering](/intune/users-add) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans. |

### <a name="exchange-cmdlet-requirements"></a>Krav för Exchange-cmdlet

Du måste även skapa ett Exchange Online-användarkonto som används av Intune Exchange-tjänstens anslutningsapp. Kontot måste ha behörighet att köra följande obligatoriska Exchange för Windows PowerShell-cmdlets:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Konfigurera tjänst till tjänstanslutning

1. Logga in på [Azure Portal](http://portal.azure.com) med ett konto som har administratörsrättigheter för Exchange och behörigheter för cmdlets såsom [beskrivs ovan](#exchange-cmdlet-requirements). Microsoft Intune använder den inloggade användarens e-postadress för att upprätta anslutningen.

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune** för att öppna Microsoft Intune-instrumentpanelen. Välj **Villkorlig åtkomst** och sedan under **Installation**, välj **Exchange-tjänstanslutning**.

4.  På sidan **Villkorlig åtkomst – Exchange-tjänstanslutning** väljer du **Konfigurera Service to Service Connector**. 
   
     ![Bild som visar hur du väljer länken Konfigurera Service to Service Connector](media/exchange_service_connector.png)

Service to Service Connector konfigureras automatiskt och synkroniseras med Exchange Online eller den nya Exchange Online Dedicated-miljön.

## <a name="validate-your-exchange-connection"></a>Validera Exchange-anslutning

När du har konfigurerat Exchange Service to Service Connector, verifiera informationen i Exchange Connector Server på sidan **Villkorlig åtkomst – Exchange-tjänstanslutning**.

Du kan också kontrollera **Anslutningsstatus** och datum och tid för det senaste lyckade synkroniseringsförsöket.

## <a name="next-steps"></a>Nästa steg
[Övervaka villkorlig åtkomst i Exchange i Microsoft Intune](conditional-access-exchange-monitor.md)