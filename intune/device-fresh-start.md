---
title: Återställa 10 Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd Börja om på nytt för att ta bort eller avinstallera appar på Windows 10-datorer med Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1eb1e671cc16196974cb15cdc785ba7d99fa8f46
ms.sourcegitcommit: 4bd992da609b8bcc85edc2d64fe8128546aa4617
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2019
ms.locfileid: "55303420"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Använda Börja om på nytt för att återställa Windows 10-enheter med Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Börja om på nytt** tar bort alla installerade appar från en dator som kör Windows 10 version 1703 eller senare. Med Börja om på nytt kan du ta bort förinstallerade appar (från OEM-tillverkare) som ofta installeras på nya datorer.  

1. Logga in på den [Azure Portal](https://portal.azure.com) och gå till **Microsoft Intune** > **Enheter** > **Alla enheter**.
2. Välj en Windows 10-enhet i listan med de enheter du hanterar.
3. Klicka på **Börja om på nytt**. 
4. Välj **Behåll användardata på den här enheten** om du vill:
   * behålla enhetens Azure AD-koppling
    * Enheten registreras i hantering av mobilenheter igen när en Azure Active Directory-aktiverad användare loggar in på enheten.
    * behålla innehållet i användarens arbetsmapp och bara ta bort appar och inställningar.  
  > [!IMPORTANT]
 > Om du inte behåller användardata återställs enheten till fabrikstillståndet. BYOD-enheter avregistreras från Azure AD och hanteringen av mobilenheter.
 > Azure AD-anslutna enheter registreras i hantering av mobilenheter igen när en Azure Active Directory-aktiverad användare loggar in på enheten.
 
5. Klicka på **OK**.   
6. Om du vill se status för den här åtgärden går du tillbaka till **Enheter** och klickar på **Enhetsåtgärder**.  
