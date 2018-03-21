---
title: "Aktivera borttappat läge för iOS med Microsoft Intune – Azure | Microsoft Docs"
description: "Aktivera eller starta borttappat läge för att anpassa ett meddelande som visas på låsskärmen på en borttappad eller stulen iOS-enhet med hjälp av Microsoft Intune. Och få information om säkerhet och sekretess när du använder åtgärden för borttappat läge."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47d6314dfaed546e5b4cff7f93a5540ba512bde9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Aktivera borttappat läge på iOS-enheter med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsåtgärden **Borttappat läge** kan du aktivera borttappat läge på förlorade eller stulna iOS-enheter. Med det här läget kan du ange ett meddelande och ett telefonnummer som visas på enhetens låsskärm. Enheten måste vara en företagsägd iOS-enhet som är i övervakat läge för att kunna använda borttappat läge.

## <a name="supported-platforms"></a>Plattformar som stöds

- iOS 9.3 och senare

Den här funktionen stöds **inte** för: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Aktivera borttappat läge

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enheter** och sedan **Alla enheter**.
4. I listan med enheter som du hanterar väljer du en iOS-enhet, **...Mer** och sedan fjärråtgärden **Borttappat läge**.
5. Aktivera funktionen i **borttappat läge**. Ange sedan det meddelande som ska visas och ett telefonnummer för kontakt.
6. Klicka på **OK** för att spara ändringarna.

När du aktiverar borttappat läge blockeras all användning av enheten. Slutanvändaren kan inte öppna enheten förrän du inaktiverar borttappat läge. När borttappat läge är aktiverat kan du hitta enheten med hjälp av åtgärden [Hitta enhet](device-locate.md).

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet skickas enhetens latitud- och longitudkoordinater till Intune och visas i Azure Portal.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- Se till att ta med information för att återlämna den borttappade enheten i det meddelande som ska visas på låsskärmen.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för aktivering av borttappat läge öppnar du **Enheter** och väljer **Enhetsåtgärder**.