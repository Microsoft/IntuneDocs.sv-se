---
title: Data som JAMF Pro skickar till Intune
titleSuffix: Microsoft Intune
description: Granska listan med data som Jamf Pro skickar till Microsoft Intune när du integrerar Jamf Pro för att hantera Mac med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 449e799dfc0531958c1578179cf07440d348ecf8
ms.sourcegitcommit: f04e21ec459998922ba9c7091ab5f8efafd8a01c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71813939"
---
# <a name="data-jamf-pro-sends-to-intune"></a>Data Jamf Pro skickar till Intune

När du använder [Jamf Pro](https://www.jamf.com) för att hantera dina slutanvändares Mac-datorer med Intune, samlar Jamf Pro in inventeringsuppgifter om hanterade macOS-enheter. 

## <a name="data"></a>Data  
En lista med data som Jamf Pro delar med Intune finns i [Bilaga: Inventeringsinformation som delas med Microsoft Intune](https://docs.jamf.com/technical-papers/jamf-pro/microsoft-intune/10.9.0/Appendix__Inventory_Information_Shared_with_Microsoft_Intune.html) i den tekniska dokumentationen för Jamf Pro. 

<!--  
Jamf Pro reports the following information to Intune:  

* Device Azure AD ID
* JAMF Inventory State (inventory state of a computer checked in with Jamf Pro within the last 24 hours)
* OS Version
* User Azure AD ID
* Encrypted (FileVault 2)
* Gatekeeper Status
* Password: minimum number of character sets
* Password expiration (days)
* Password Type - simple, alphanumeric, or unknown
* Prevent Auto Login
* Required Passcode Length
* Password: number of previous passwords to prevent reuse
* System Integrity Protection
* Last Check-In Time
* Architecture Type
* Available RAM Slots
* Battery Capacity
* Boot ROM
* Bus Speed
* Cache Size
* Device Name
* Domain Join
* Jamf ID
* MAC address
* Make
* Model
* Model Identifier
* NIC Speed
* Number of Cores
* Number of Processors
* OS
* Platform
* Processor Speed
* Processor Type
* Secondary MAC Address
* Serial Number
* SMC Version
* Total RAM
* UDID
* User Email
--> 

<!-- 
You can remove a Jamf-managed device from the Intune console by selecting **Delete** in the **All devices** view. Bulk device deletion can be enabled by selecting multiple devices and clicking **Delete**.
-->

## <a name="next-steps"></a>Nästa steg
Få information om hur du [tar bort en Jamf-hanterad enhet i Jamf Pro-dokumenten](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Du kan även skicka in ett supportärende med [Jamf-support](https://www.jamf.com/support/) för ytterligare hjälp. 

