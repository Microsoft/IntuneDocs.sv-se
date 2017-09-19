---
title: "Översikt över applivscykeln"
description: "Läs om livscykeln för Intune-hanterade appar, från de läggs till tills de tas ur bruk."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 01648e20704c9cfc0121ded3b95d99e4661f4f53
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="overview-of-the-app-lifecycle"></a>Översikt över applivscykeln

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Applivscykeln i Intune börjar när en app läggs till och fortsätter genom fler faser tills du tar bort appen.

![Applivscykeln](./media/app-lifecycle.png "Intune-appens livscykel")

## <a name="add"></a>Lägg till

Det första steget i appdistributionen är att lägga till de appar som du vill hantera och tilldela i Intune. Det finns många olika apptyper som du kan arbeta med, men de grundläggande procedurerna är samma. Med Intune kan du lägga till appar för både [registrerade enheter](apps-add.md) ([klassisk portal](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)) och [Windows-datorer som du hanterar med Intunes klientprogramvara](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune).

## <a name="deploy"></a>Distribuera

När du har lagt till appen i Intune kan du sedan [tilldela den till användare och enheter som du hanterar](apps-deploy.md) ([klassisk portal](/intune-classic/deploy-use/deploy-apps)). I Intune är den här processen enkel och när appen har distribuerats kan du [övervaka processen](apps-monitor.md) ([klassisk portal](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)) för distributionen från Intunes administrationskonsol. Dessutom kan du i vissa appbutiker, till exempel appbutikerna för [Apple](vpp-apps-ios.md) ([klassisk portal](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)) och [Windows](windows-store-for-business.md) ([klassisk portal](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)), köpa applicenser gruppvis till företaget. Intune kan synkronisera data med dessa butiker så att du kan distribuera och spåra licensanvändning för dessa typer av appar direkt från Intune-administrationskonsolen.

## <a name="configure"></a>Konfigurera

Som en del av applivscykeln släpps regelbundet nya versioner av appar. Intune innehåller verktyg för att enkelt [uppdatera appar](apps-add.md) ([klassisk portal](/intune-classic/deploy-use/update-apps-using-microsoft-intune)) som du har distribuerat till en nyare version. Dessutom kan du konfigurera ytterligare funktioner för vissa appar, till exempel:
- [Konfigurationsprinciper för iOS-appar](app-configuration-policies-use-ios.md) ([klassisk portal](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)) innehåller inställningar för kompatibla iOS-appar som används när appen körs. En app kan till exempel kräva specifika inställningar för anpassning eller namnet på en server som den ska ansluta till.
- [Hanterade webbläsarprinciper](app-configuration-managed-browser.md) ([klassisk portal](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)) hjälper dig att konfigurera inställningar för den hanterade webbläsaren i Intune. Den ersätter enhetens standardwebbläsare och låter dig begränsa vilka webbplatser som användarna kan besöka.

## <a name="protect"></a>Skydda

Intune ger många sätt att skydda data i dina appar. De viktigaste metoderna är:
- [Villkorlig åtkomst](conditional-access.md) ([klassisk portal](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) styr åtkomsten till e-post och andra tjänster utifrån de villkor som du anger. Villkoren innefattar enhetstyper eller om de följer en [efterlevnadsprincip för enheter](device-compliance.md) ([klassisk portal](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)) som du har distribuerat.
- [Appskyddsprinciperna](app-protection-policy.md) ([klassisk portal](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) används i enskilda appar för att skydda de företagsdata som de använder. Du kan till exempel begränsa kopiering av data mellan ohanterade appar och appar som du hanterar, eller förhindra att appar körs på enheter som har jailbreakats eller rotats.

## <a name="retire"></a>Pensionera

Så småningom är det troligt att appar som du har distribuerat blir inaktuella och måste tas bort. Med Intune är det enkelt att [dra tillbaka appar från tjänsten](device-management.md) ([klassisk portal](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)).
