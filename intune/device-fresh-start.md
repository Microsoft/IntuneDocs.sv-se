---
title: "Återställa Windows 10-enheter med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du använder Börja om på nytt för att återställa Windows 10-datorer med Intune.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 590472c0ab9f0103d72730b8ab01dc324c852a7a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Använda Börja om på nytt för att återställa Windows 10-enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Börja om på nytt** tar bort alla appar som har installerats på en Windows 10-dator som kör Creators Update och uppdaterar sedan automatiskt datorn till den senaste versionen av Windows.
Detta kan användas för att ta bort förinstallerade OEM-appar som ofta levereras med en ny dator. Du kan konfigurera om användardata ska behållas när den här enhetsåtgärden utförs. I det här fallet tas appar och inställningar bort, men innehållet i användarens startmapp bevaras.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en Windows 10-skrivbordsenhet och sedan fjärråtgärden **Börja om på nytt** för enheten.

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.

