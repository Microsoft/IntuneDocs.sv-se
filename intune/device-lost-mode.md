---
title: "Aktivera borttappat läge i iOS med Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du använder Intune för att aktivera borttappat läge på förlorade eller stulna iOS-enheter.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a34d008ae76355578c6f24a932c9e1e501d5b46b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="activate-lost-mode-on-ios-devices"></a>Aktivera borttappat läge på iOS-enheter


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Med enhetsåtgärden **Borttappat läge** kan du aktivera borttappat läge på förlorade eller stulna iOS-enheter. Med läget kan du ange ett meddelande och ett telefonnummer som visas på enhetens låsskärm

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en iOS-enhet och sedan fjärråtgärden **Borttappat läge**.
6. Aktivera borttappat läge på bladet **Borttappat läge** och ange det meddelandet som ska visas och, vilket är valfritt, ett telefonnummer.
7. Klicka på **OK**.

När du aktiverar borttappat läge blockerar du all användning av enheten. Slutanvändaren kan inte öppna enheten förrän du inaktiverar borttappat läge. Borttappat läge är aktiverat, men du kan använda åtgärden **Leta upp enheten** om du vill veta var enheten finns.
För att kunna använda Borttappat läge måste enheten vara en företagsägd iOS-enhet, registrerad med DEP, som är i övervakat läge.

Om du vill se status för den åtgärd som du vidtog, går du till bladet **Enheter och grupper** och väljer **Enhetsåtgärder**.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Information om säkerhet och sekretess för åtgärderna för borttappat läge och hitta enhet
- Ingen platsinformation för enheten skickas till Intune förrän du har aktiverat den här åtgärden.
- När du använder åtgärden Hitta enhet skickas enhetens latitud- och longitudkoordinater till Intune och visas i Azure Portal.
- Data lagras i 24 timmar och tas sedan bort. Du kan inte ta bort platsdata manuellt.
- Platsinformationen krypteras både under lagring och vid överföring.
- När du konfigurerar borttappat läge rekommenderar vi att det meddelande du skriver och som ska visas på låsskärmen innehåller information som hjälper den som hittar enheten att återlämna den.

