---
title: "Exchange Connector för Exchange Online | Microsoft Intune"
description: "Anslut Intune till Office 365 Exchange-tjänsten för att stödja Exchange ActiveSync MDM (mobil enhetshantering)."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: a6438bb3ca21e5c46dca5ebe69266fd9bce9a4b8


---

# Konfigurera Intune Service-to-Service Connector för Exchange Online

Använd den här informationen för att ansluta Microsoft Intune och Exchange Online eller ny Exchange Online Dedicated-tjänst. Om du vill ta reda på om Exchange Online Dedicated-miljön är **ny** eller **äldre** kontaktar du din kontoansvariga. Intune har endast stöd för en Exchange Connector-anslutning av valfri typ per prenumeration.

## Krav för Service-to-Service Connector
**Service-to-Service Connector** har endast stöd för Exchange Online eller ny Exchange Online Dedicated och har inga krav för lokal infrastruktur.

|Krav|Mer information|
|---------------|--------------------|
|Exchange Online konfigurerad och körs|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Utfärdare för hantering av mobila enheter| [Ange Microsoft Intune som utfärdare för hantering av mobila enheter](prerequisites-for-enrollment.md#set-mobile-device-management-authority)|
|Microsoft Exchange-version|Exchange Online eller ny Exchange Online Dedicated-tjänst|
|Active Directory-synkronisering|Innan du kan använda Intune Connector måste du [konfigurera Active Directory-synkronisering](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3) så att dina lokala användare och säkerhetsgrupper synkroniseras med din Azure Active Directory-instans.|

### Krav för Exchange-cmdlet

Du måste även skapa ett Exchange Online-användarkonto som används av Intune Exchange Connector. Kontot måste ha behörighet att använda administratörskonsolen i Intune och köra de här nödvändiga Windows PowerShell Exchange-cmdlets:

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## Konfigurera Service-to-Service Connector

1. Öppna [administratörskonsolen för Microsoft Intune](http://manage.microsoft.com) med ett användarkonto med administratörsrättigheter för Exchange och behörigheter för cmdlets som nämns [ovan](#exchange-cmdlet-requirements). Microsoft Intune använder den inloggade användarens e-postadress för att upprätta anslutningen.

2.  Välj **ADMIN** i fönstret med genvägar på arbetsytan och gå till **hantering av mobila enheter** > **Microsoft Exchange** > **Installera Exchange Connection**.
![Sidan Konfigurera Service-to-Service Connector](../media/intunesa5cservicetoserviceconnector.png)

3.  På sidan **Konfigurera Exchange-anslutning** väljer du **Konfigurera Service to Service Connector**.


Service-to-Service Connector konfigureras automatiskt och synkroniseras med Exchange Online eller den nya Exchange Online Dedicated-miljön.

## Validera Exchange-anslutning

När du har konfigurerat Exchange Connector går du till [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com), väljer **Admin**, väljer **Hantering av mobila enheter** > **Microsoft Exchange** och verifierar att informationen du angett visas under **Anslutningsinformation för Exchange**.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.



<!--HONumber=Sep16_HO4-->


