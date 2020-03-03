---
title: Översikt över livscykeln för hantering av mobila enheter (MDM) i Microsoft Intune
description: Läs om hur Intune kan hjälpa dig att hantera enheter genom hela livscykeln – från registrering till konfiguration och slutligen pensionering.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57a1e1c9c8a03fae67f2a4a25b6b4f16a20a8ec7
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514463"
---
# <a name="overview-of-the-microsoft-intune-mobile-device-management-mdm-lifecycle"></a>Översikt över livscykeln för hantering av mobila enheter (MDM) i Microsoft Intune

Alla enheter du hanterar har en *livscykel*. Intune kan hjälpa dig att hantera livscykeln: från registrering, konfigurering och skydd till pensionering när enheten inte behövs längre.

![Enhetslivscykeln](./media/device-lifecycle/device-lifecycle.png "Intune-enhetslivscykeln")

## <a name="enroll"></a>Registrera

Dagens strategier för hantering av mobila enheter (MDM) omfattar många olika telefoner, surfplattor och datorer (iOS/iPadOS, Android, Windows och Mac OS X). Om du behöver kunna hantera enheten, vilket ofta är fallet för företagsägda enheter, är det första steget att [konfigurera registrering av enheter](../enrollment/device-enrollment.md). Du kan även hantera Windows-datorer genom att registrera dem med Intune (MDM) eller genom att [installera Intune-klientprogrammet](../manage-windows-pcs-with-microsoft-intune.md).

## <a name="configure"></a>Konfigurera

Registrering av enheter är bara det första steget. Om du vill dra nytta av allt som Intune har att erbjuda och se till att enheterna är skyddade och kompatibla med företagets standarder, finns en mängd olika principer att välja bland. Med principer kan du konfigurera nästan alla aspekter av hur hanterade enheter fungerar. Bör användare till exempel ha ett lösenord på enheter som innehåller företagsdata? Du kan kräva det. Har du företags-Wi-Fi? Du kan konfigurera det automatiskt. Dessa konfigurationsalternativ finns tillgängliga:

- [**Enhetskonfiguration**](../configuration/device-profiles.md). Med de här principerna kan du konfigurera funktioner på enheter som du hanterar. Du kan till exempel kräva ett lösenord på Windows-telefoner eller inaktivera kameran på iPhones.
- [**Åtkomst till företagsresurs**](../configuration/device-profiles.md). När du ger användarna åtkomst till deras arbete på deras personliga enhet kan det medföra utmaningar. Hur säkerställer du till exempel att alla enheter som behöver åtkomst till företagets e-post är korrekt konfigurerade? Hur kan du säkerställa att användarna har åtkomst till företagets nätverk med en VPN-anslutning utan att behöva känna till avancerade inställningar? Intune kan minska det här problemet genom att automatiskt konfigurera de enheter som du hanterar för åtkomst till gemensamma företagsresurser.
- [**Principer för hantering av Windows-datorer (med Intune-klientprogramvaran)** ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Registrering av Windows-datorer med Intune ger flest funktioner för enhetshantering, men Intune fortsätter att stödja hantering av Windows-datorer med Intune-klientprogramvaran. Börja här om du behöver information om några av uppgifterna som du kan utföra med datorer.

## <a name="protect"></a>Skydda

I dagens IT är en av de viktigaste uppgifterna att skydda enheter så att inte obehöriga kan komma åt dem. Förutom punkterna i steget **Konfigurera** i enhetslivscykeln tillhandahåller Intune ytterligare funktioner som skyddar de enheter som du hanterar från obehörig åtkomst eller skadliga attacker:

- [**Multi-factor Authentication**](../enrollment/multi-factor-authentication.md). Att lägga till ett extra lager av autentisering för användarinloggningar kan göra enheter ännu säkrare. Många enheter stöder Multi-factor Authentication som kräver en andra nivå av autentisering, till exempel ett telefonsamtal eller SMS, innan användarna kan få åtkomst.
- [**Windows Hello för företag-inställningar**](../protect/windows-hello.md). Windows Hello för företag är en alternativ inloggningsmetod där användarna kan använda en *gest*, till exempel ett fingeravtryck eller Windows Hello, för att logga in utan lösenord.
- [**Principer för att skydda Windows-datorer (med Intune-klientprogramvaran)** ](../policies-to-protect-windows-pcs-in-microsoft-intune.md). När du hanterar Windows-datorer med Intune-klientprogramvaran finns det principer som gör att du kan styra inställningar för Endpoint Protection, programuppdateringar och Windows-brandväggen på de datorer som du hanterar.

## <a name="retire"></a>Pensionera

När en enhet blir stulen eller tappas bort, när enheten behöver bytas ut eller när användarna flyttar till en annan tjänst är det vanligtvis dags att [dra tillbaka eller rensa](../remote-actions/device-management.md) enheten. Det finns ett antal sätt att göra det, till exempel att återställa enheten, ta bort den från hantering eller rensa företagsdata på den.

## <a name="next-steps"></a>Nästa steg

- Läs mer om [enhetshantering i Microsoft Intune](../remote-actions/device-management.md)
