---
title: "Översikt över MDM-livscykeln"
description: "Läs om hur Intune kan hjälpa dig att hantera enheter genom hela livscykeln, från registrering till konfiguration och slutligen pensionering."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7a2eab6ece5628598a7b5a5f9414aa43abc60d69
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="overview-of-the-mobile-device-management-mdm-lifecycle"></a>Översikt över livscykeln för hantering av mobila enheter (MDM)

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Alla enheter du hanterar har en så kallad *livscykel*. Intune kan hjälpa dig att hantera livscykeln från registrering, konfigurering och skydd till pensionering när enheten inte behövs längre:

![Enhetslivscykeln](./media/device-lifecycle.png "Intune-enhetens livscykel")

## <a name="enroll"></a>Registrera
Dagens strategier för hantering av mobila enheter (MDM) omfattar många olika telefoner, surfplattor och datorer (iOS, Android, Windows och Mac OS X). Om du behöver kunna hantera enheten, vilket ofta är fallet för företagsägda enheter, är det första steget att [konfigurera enhetsregistrering](device-enrollment.md) ([klassisk portal](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)). Du kan även hantera Windows-datorer genom att registrera dem med Intune (MDM) eller genom att [installera Intune-klientprogrammet](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune).

## <a name="configure"></a>Konfigurera
Registrering av enheter är bara det första steget. Om du vill dra nytta av allt som Intune har att erbjuda och se till att enheterna är skyddade och kompatibla med företagets standarder, finns en mängd olika principer att välja bland. Med principer kan du konfigurera nästan alla aspekter av hur hanterade enheter fungerar. Bör användare till exempel ha ett lösenord på enheter som innehåller företagsdata? Du kan kräva det. Har du företags-Wi-Fi? Du kan konfigurera det automatiskt. Dessa konfigurationsalternativ finns tillgängliga:

- [**Enhetskonfiguration**](device-profiles.md) ([klassisk portal](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)). Med de här principerna kan du konfigurera funktioner på enheter som du hanterar. Du kan till exempel kräva ett lösenord på Windows-telefoner eller inaktivera kameran på iPhones.
- [**Åtkomst till företagsresurser**](device-profiles.md) ([klassisk portal](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)). När du ger användarna åtkomst till deras arbete på deras personliga enhet kan det medföra utmaningar. Hur säkerställer du till exempel att alla enheter som behöver åtkomst till företagets e-post är korrekt konfigurerade? Hur kan du säkerställa att användarna har åtkomst till företagets nätverk med en VPN-anslutning utan att behöva känna till avancerade inställningar? Intune kan minska det här problemet genom att automatiskt konfigurera de enheter som du hanterar för åtkomst till gemensamma företagsresurser.
- [**Principer för hantering av Windows-datorer (med Intune-klientprogramvaran)**](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client). Registrering av Windows-datorer med Intune ger flest funktioner för enhetshantering, men Intune fortsätter att stödja hantering av Windows-datorer med Intune-klientprogramvaran. Börja här om du behöver information om några av uppgifterna som du kan utföra med datorer.

## <a name="protect"></a>Skydda
I dagens IT är en av de viktigaste uppgifterna att skydda enheter så att inte obehöriga kan komma åt dem. Förutom punkterna i steget **Konfigurera** i enhetslivscykeln tillhandahåller Intune ytterligare funktioner som skyddar de enheter som du hanterar från obehörig åtkomst eller skadliga attacker:
- [**Multi-factor Authentication**](/intune-classic/deploy-use/protect-your-devices-with-microsoft-intune). Att lägga till ett extra lager av autentisering för användarinloggningar kan göra enheter ännu säkrare. Många enheter stöder Multi-factor Authentication som kräver en andra nivå av autentisering, till exempel ett telefonsamtal eller SMS, innan användarna kan få åtkomst.
- [**Inställningar för Windows Hello för företag**](windows-hello.md) ([klassisk portal](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)). Windows Hello för företag är en alternativ inloggningsmetod där användarna kan använda en *gest*, till exempel ett fingeravtryck eller Windows Hello, för att logga in utan lösenord.
- [**Principer för att skydda Windows-datorer (med Intune-klientprogramvaran)**](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune). När du hanterar Windows-datorer med Intune-klientprogramvaran finns det principer som gör att du kan styra inställningar för Endpoint Protection, programuppdateringar och Windows-brandväggen på de datorer som du hanterar.

## <a name="retire"></a>Pensionera
Om en enhet blir stulen eller tappas bort, när enheten behöver bytas ut eller när användaren får en annan tjänst, är det vanligtvis dags att [dra tillbaka eller rensa](device-management.md) ([klassisk portal](/intune-classic/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)) enheten. Det finns ett antal sätt att göra det, till exempel att återställa enheten, ta bort den från hantering eller rensa företagsdata på den.
