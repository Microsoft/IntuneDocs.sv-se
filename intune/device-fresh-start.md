---
title: Återställa 10 Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd Börja om på nytt för att ta bort eller avinstallera appar på Windows 10-datorer med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b66cd00f734cab3ca85f6d87f056f8c482a377d
ms.sourcegitcommit: 2811df0f851ca6b08f6ae8c926fb2e6971c41690
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2018
ms.locfileid: "40251739"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Använda Börja om på nytt för att återställa Windows 10-enheter med Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Börja om på nytt** tar bort alla installerade appar från en dator som kör Windows 10 version 1703 eller senare. Med Börja om på nytt kan du ta bort förinstallerade appar (från OEM-tillverkare) som ofta installeras på nya datorer.  

1. Logga in på den [Azure Portal](https://portal.azure.com) och gå till **Microsoft Intune** > **Enheter** > **Alla enheter**.
2. Välj en Windows 10-enhet i listan med de enheter du hanterar.
3. Klicka på **Börja om på nytt**. 
4. Välj **Behåll användardata på den här enheten** om du vill:
   * behålla enhetens Azure AD-koppling
    * behålla enhetens registrering i hanteringen av mobila enheter 
    * behålla innehållet i användarens arbetsmapp och bara ta bort appar och inställningar.  
  > [!IMPORTANT]
 > Om du inte behåller användardata återställs enheten till fabrikstillståndet. Den avregistreras från Azure AD och hanteringen av mobila enheter. 
 
5. Klicka på **OK**.   
6. Om du vill se status för den här åtgärden går du tillbaka till **Enheter** och klickar på **Enhetsåtgärder**.  
