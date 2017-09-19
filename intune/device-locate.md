---
title: "Hitta försvunna iOS-enheter med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du hittar borttappade eller stulna iOS-enheter med Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9d03555e91a9e759e62b829576a0d39f957ab430
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Hitta borttappade eller stulna iOS-enheter med Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Åtgärden **Hitta enhet** visar platsen för en förlorad eller stulen iOS-enhet på en karta. Enheten måste vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge. Innan du använder den här åtgärden måste enheten ha placerats i [Borttappat läge](/intune-azure/manage-devices/lost-mode.md).

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöd på iOS 9.3 och senare (i borttappat läge), övervakad och företagsägd
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-locate-a-lost-or-stolen-device"></a>Hitta en förlorad eller stulen enhet

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


## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.