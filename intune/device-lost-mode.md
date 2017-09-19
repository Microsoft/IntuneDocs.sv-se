---
title: "Aktivera borttappat läge i iOS med Intune"
titlesuffix: Azure portal
description: "Lär dig hur du använder Intune för att aktivera borttappat läge på förlorade eller stulna iOS-enheter.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5f16bd212c7a23d847da0929933fbd4b497099d0
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>Aktivera borttappat läge på iOS-enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsåtgärden **Borttappat läge** kan du aktivera borttappat läge på förlorade eller stulna iOS-enheter. Med det här läget kan du ange ett meddelande och ett telefonnummer som visas på enhetens låsskärm.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows – stöds inte
- Windows Phone – stöds inte
- iOS – stöd på iOS 9.3 och senare, övervakad och företagsägd
- macOS – stöds inte
- Android – stöds inte

## <a name="how-to-activate-lost-mode"></a>Aktivera borttappat läge

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en iOS-enhet och sedan fjärråtgärden **Borttappat läge**.
6. Aktivera borttappat läge på bladet **Borttappat läge**. Ange sedan det meddelande som ska visas och eventuellt ett telefonnummer för kontakt.
7. Klicka på **OK**.

När du aktiverar borttappat läge blockerar du all användning av enheten. Slutanvändaren kan inte öppna enheten förrän du inaktiverar borttappat läge. Borttappat läge är aktiverat, men du kan använda åtgärden **Leta upp enheten** om du vill veta var enheten finns.
Enheten måste vara en företagsägd iOS-enhet som är i övervakat läge för att kunna använda borttappat läge.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet skickas enhetens latitud- och longitudkoordinater till Intune och visas i Azure Portal.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- Vi rekommenderar att det meddelande du skriver och som ska visas på låsskärmen innehåller information som hjälper den som hittar enheten att återlämna den.

## <a name="next-steps"></a>Nästa steg

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.

