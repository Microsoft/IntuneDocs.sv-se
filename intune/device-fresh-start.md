---
title: Återställa 10 Windows-enheter med Microsoft Intune – Azure | Microsoft Docs
description: Använd Börja om på nytt för att ta bort eller avinstallera appar på Windows 10-datorer med Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5658bf2e1ee250ef9fd405b3f7ec1772b166f338
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021004"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Använda Börja om på nytt för att återställa Windows 10-enheter med Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Börja om på nytt** tar bort alla appar som är installerade på en Windows 10-dator som kör Creators Update. Sedan uppdateras datorn automatiskt till den senaste versionen av Windows.

Den här åtgärden tar bort förinstallerade appar (från OEM-tillverkare) som vanligtvis installeras med en ny dator. Om du vill behålla innehållet i användarens arbetsmapp och bara ta bort appar och inställningar använder du inställningen `if user data is retained`.

> [!IMPORTANT]
> Åtgärden Börja om på nytt avregistrerar enheten från Intune, men enheten är fortfarande ansluten i Azure Active Directory.

## <a name="use-fresh-start"></a>Använda Börja om på nytt

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. I listan med enheter som du hanterar väljer du en Windows 10-skrivbordsenhet och sedan **Börja om på nytt**.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den här åtgärden väljer du **Enhetsåtgärder** (**Microsoft Intune** > **Enheter**).