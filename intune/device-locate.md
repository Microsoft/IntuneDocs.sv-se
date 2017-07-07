---
title: "Hitta försvunna iOS-enheter med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du hittar borttappade eller stulna iOS-enheter med Intune.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80aa0e5afd1f8862b181d455ff6b545e462f90c9
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Hitta borttappade eller stulna iOS-enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Hitta enhet** visar platsen för en förlorad eller stulen iOS-enhet på en karta. Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge. Innan du använder den här åtgärden måste enheten ha placerats i [Borttappat läge](/intune-azure/manage-devices/lost-mode.md).

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en iOS-enhet och sedan fjärråtgärden **Hitta enhet**.
6. När enheten har hittats visas dess plats visas på bladet **Hitta enhet**.
    ![Hitta enhetsblad](./media/locate-device.png)

>[!NOTE]
>Av sekretesskäl är avståndet du kan zooma på kartan begränsat.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet skickas enhetens latitud- och longitudkoordinater till Intune och visas i Azure Portal.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- När du konfigurerar borttappat läge rekommenderar vi att det meddelande du skriver och som ska visas på låsskärmen innehåller information som hjälper den som hittar enheten att återlämna den.
