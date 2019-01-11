---
title: Intune Exchange Connector för Exchange Online | Microsoft Intune
description: Anslut Intune till Office 365 Exchange-tjänsten för att stödja Exchange ActiveSync MDM (mobil enhetshantering).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9845ed1b809b611975c07c6c8335acd237d845c0
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816709"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Konfigurera Exchange-tjänstens anslutningsprogram för Intune och Exchange Online
Den här artikeln visar hur du ansluter Microsoft Intune-tjänsten till Exchange Online eller den nya Exchange Online Dedicated-tjänsten. Om du vill ta reda på om Exchange Online Dedicated-miljön är den **nya** eller **äldre** versionen kontaktar du din kontoansvariga.

Med **Service to Service Connector** kan du hantera både Exchange ActiveSync (EAS) och Intune-hanterade enheter från en enda administrativ konsol.  Det krävs inte något anslutningsprogram till att aktivera villkorsstyrd åtkomst för Exchange Online.

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

1. Logga in på [Azure Portal](https://portal.azure.com) med ett konto som har administratörsrättigheter för Exchange och behörigheter för cmdletarna som [beskrivs ovan](#exchange-cmdlet-requirements), en giltig Intune-licens och rollen Global administratör. Microsoft Intune använder den inloggade användarens e-postadress för att upprätta anslutningen.

2. Välj **Alla tjänster** i den vänstra menyn och skriv sedan **Intune** i textrutans filter.

3. Välj **Intune** för att öppna Microsoft Intune-instrumentpanelen. Välj **Villkorlig åtkomst** och sedan under **Installation**, välj **Exchange-tjänstanslutning**.

4.  På sidan **Villkorlig åtkomst – Exchange-tjänstanslutning** väljer du **Konfigurera Service to Service Connector**. 
   
     ![Bild som visar hur du väljer länken Konfigurera Service to Service Connector](media/exchange_service_connector.png)

Service to Service Connector konfigureras automatiskt och synkroniseras med Exchange Online eller den nya Exchange Online Dedicated-miljön.

## <a name="validate-your-exchange-connection"></a>Validera Exchange-anslutning

När du har konfigurerat Exchange Service to Service Connector, verifiera informationen i Exchange Connector Server på sidan **Villkorlig åtkomst – Exchange-tjänstanslutning**.

Du kan också kontrollera **Anslutningsstatus** och datum och tid för det senaste lyckade synkroniseringsförsöket.

 