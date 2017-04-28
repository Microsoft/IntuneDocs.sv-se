---
title: "Exchange Connector för Exchange Online | Microsoft Docs"
description: "Anslut Intune till Office 365 Exchange-tjänsten för att stödja Exchange ActiveSync MDM (mobil enhetshantering)."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: dce7050a7439a7e24e34be3c79473d6ec3159c83
ms.lasthandoff: 04/24/2017


---

# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>Konfigurera Intune Service to Service Connector för Exchange Online

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd den här informationen för att ansluta Microsoft Intune och Exchange Online eller den nya Exchange Online Dedicated-tjänsten. Om du vill ta reda på om Exchange Online Dedicated-miljön är den **nya** eller **äldre** versionen kontaktar du din kontoansvariga. Intune har endast stöd för en Exchange Connector-anslutning av valfri typ per prenumeration.

## <a name="service-to-service-connector-requirements"></a>Krav för Service to Service Connector
**Service to Service Connector** har endast stöd för Exchange Online eller Exchange Online Dedicated och har inga krav för lokal infrastruktur.

|Krav|Mer information|
|---------------|--------------------|
|Exchange Online konfigurerad och körs|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Utfärdare för hantering av mobila enheter| [Ange Microsoft Intune som utfärdare för hantering av mobila enheter](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Microsoft Exchange-version|Exchange Online eller den nya Exchange Online Dedicated-tjänsten|
|Active Directory-synkronisering|Innan du kan använda Intune Connector måste du [konfigurera Active Directory-synkronisering](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans.|

### <a name="exchange-cmdlet-requirements"></a>Krav för Exchange-cmdlet

Du måste även skapa ett Exchange Online-användarkonto som används av Intune Exchange Connector. Kontot måste ha behörighet att använda administrationskonsolen i Intune och köra följande nödvändiga Windows PowerShell Exchange-cmdlets:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>Konfigurera tjänst till tjänstanslutning

1. Öppna [administrationskonsolen för Microsoft Intune](https://manage.microsoft.com) med ett användarkonto som har administratörsrättigheter för Exchange och behörigheter för cmdlets som [beskrevs tidigare](#exchange-cmdlet-requirements). Microsoft Intune använder den inloggade användarens e-postadress för att upprätta anslutningen.

2.  I fönstret med genvägar på arbetsytan väljer du **ADMIN**>**Hantering av mobila enheter** > **Microsoft Exchange** > **Installera Exchange Connection**.
![Sidan Konfigurera Service to Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  På sidan **Konfigurera Exchange-anslutning** väljer du **Konfigurera Service to Service Connector**.


Service to Service Connector konfigureras automatiskt och synkroniseras med Exchange Online eller den nya Exchange Online Dedicated-miljön.

## <a name="validate-your-exchange-connection"></a>Validera Exchange-anslutning

När du har konfigurerat Exchange Connector går du till [administrationskonsolen för Microsoft Intune](https://manage.microsoft.com). Välj **Admin**> **Hantering av mobila enheter** > **Microsoft Exchange**. Kontrollera sedan att informationen du har angivit visas under **Anslutningsinformation för Exchange**.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.

