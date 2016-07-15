---
title: "Konfigurera Microsoft Intune Exchange Connector för värdbaserad Exchange | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# Konfigurera Intune Service-to-Service Connector för Exchange Online

Använd den här informationen för att ansluta Microsoft Intune med en Exchange Online-tjänst som tillhandahålls genom Office 365.

## Krav för Service-to-Service Connector
**Service-to-Service Connector** har endast stöd för värdbaserad Exchange och har inga krav för lokal infrastruktur.

|Krav|Mer information|
|---------------|--------------------|
|Värdbaserad Exchange konfigurerad och körs|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|Utfärdare för hantering av mobila enheter| [Ange Microsoft Intune som utfärdare för hantering av mobila enheter](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange-version|Du måste ha en Office 365-prenumeration med en Exchange Server 2013-klient eller senare. Så länge klienten är Exchange Server 2013 eller senare, stöder anslutningen Exchange Server 2010 i samma miljö.|
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


Service-to-Service Connector konfigureras automatiskt och synkroniseras med den värdbaserade Exchange-miljön.

## Validera Exchange-anslutning

När du har konfigurerat Exchange Connector väljer du arbetsytan **ADMIN** och sedan **Hantering av mobila enheter** > **Microsoft Exchange** och kontrollerar att informationen som du angav visas under **Anslutningsinformation för Exchange**.

Du kan också kontrollera datum och tid för det senaste lyckade synkroniseringsförsöket.



<!--HONumber=Jun16_HO4-->


