---
title: Återställa 10 Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd Börja om på nytt för att ta bort eller avinstallera appar på Windows 10-datorer med Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e48b7dac5064f9daeb62e141a4c1b2a4adf11b7
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782200"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Använda Börja om på nytt för att återställa Windows 10-enheter med Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Enhetsåtgärden **Börja om på nytt** tar bort alla installerade appar från en dator som kör Windows 10 version 1703 eller senare. Med Börja om på nytt kan du ta bort förinstallerade appar (från OEM-tillverkare) som ofta installeras på nya datorer. 

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) och välj **Enheter** > **Alla enheter**.
2. Välj en Windows 10-enhet i listan med de enheter du hanterar.
3. Klicka på **Börja om på nytt**. 
4. Välj **Behåll användardata på den här enheten** om du vill:
   * behålla enhetens Azure AD-koppling
   * Enheten registreras i hanteringen av mobilenheter igen när en Azure Active Directory-aktiverad användare loggar in på enheten.
   * behålla innehållet i användarens arbetsmapp och bara ta bort appar och inställningar.

  > [!IMPORTANT]
 > Om du inte behåller användardata kommer enheten att återställas till slutfört OOBE-läge (Out-of-Box Experience) som bibehåller det inbyggda administratörskontot.
 > BYOD-enheter avregistreras från Azure AD och hanteringen av mobilenheter.
 > Azure AD-anslutna enheter registreras i hantering av mobilenheter igen när en Azure Active Directory-aktiverad användare loggar in på enheten.
 
5. Klicka på **OK**.   
6. Om du vill se status för den här åtgärden går du tillbaka till **Enheter** och klickar på **Enhetsåtgärder**.  
7. Enheten kommer att återställas till den första inloggningsskärmen.
