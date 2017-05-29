---
title: "Översikt över livscykeln för hantering av mobila enheter (MDM) | Microsoft Docs"
description: "Läs om hur Intune kan hjälpa dig att hantera enheter genom hela livscykeln, från registrering till konfiguration och slutligen pensionering."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f6051fa7-133f-4712-86a5-e5f5bc5ab3c7
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3311ba5081c4b04d72fdeb1f9a558ffc2e1b02fc
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="overview-of-the-mobile-device-management-mdm-lifecycle"></a>Översikt över livscykeln för hantering av mobila enheter (MDM)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Alla enheter du hanterar har en så kallad *livscykel*. Intune kan hjälpa dig att hantera livscykeln från registrering, konfigurering och skydd till pensionering när enheten inte behövs längre:

![Enhetslivscykeln](./media/device-lifecycle.png "Intune-enhetens livscykel")

## <a name="enroll"></a>Registrera
Dagens strategier för hantering av mobila enheter (MDM) omfattar många olika telefoner, surfplattor och datorer (iOS, Android, Windows och Mac OS X). Om du behöver kunna hantera enheten, vilket ofta är fallet för företagsägda enheter, är det första steget att [konfigurera registrering av enheter](enroll-devices-in-microsoft-intune.md). Du kan även hantera Windows-datorer genom att registrera dem med Intune (MDM) eller genom att [installera Intune-klientprogrammet](manage-windows-pcs-with-microsoft-intune.md).

## <a name="configure"></a>Konfigurera
Registrering av enheter är bara det första steget. Om du vill dra nytta av allt som Intune har att erbjuda och se till att enheterna är skyddade och kompatibla med företagets standarder, finns en mängd olika principer att välja bland. Med principer kan du konfigurera nästan alla aspekter av hur hanterade enheter fungerar. Bör användare till exempel ha ett lösenord på enheter som innehåller företagsdata? Du kan kräva det. Har du företags-Wi-Fi? Du kan konfigurera det automatiskt. Dessa konfigurationsalternativ finns tillgängliga:

- [**Konfigurationsprinciper**](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md). Med de här principerna kan du konfigurera funktioner på enheter som du hanterar. Du kan till exempel kräva ett lösenord på Windows-telefoner eller inaktivera kameran på iPhones.
- [**Principer för åtkomst till företagsresurser**](enable-access-to-company-resources-with-microsoft-intune.md). När du ger användarna åtkomst till deras arbete på deras personliga enhet kan det medföra utmaningar. Hur säkerställer du till exempel att alla enheter som behöver åtkomst till företagets e-post är korrekt konfigurerade? Hur kan du säkerställa att användarna har åtkomst till företagets nätverk med en VPN-anslutning utan att behöva känna till avancerade inställningar? Intune kan minska det här problemet genom att automatiskt konfigurera de enheter som du hanterar för åtkomst till gemensamma företagsresurser.
- [**Principer för hantering av Windows-datorer (med Intune-klientprogramvaran)**](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md). Registrering av Windows-datorer med Intune ger flest funktioner för enhetshantering, men Intune fortsätter att stödja hantering av Windows-datorer med Intune-klientprogramvaran. Börja här om du behöver information om några av uppgifterna som du kan utföra med datorer.

## <a name="protect"></a>Skydda
I dagens IT är en av de viktigaste uppgifterna att skydda enheter så att inte obehöriga kan komma åt dem. Förutom punkterna i steget **Konfigurera** i enhetslivscykeln tillhandahåller Intune ytterligare funktioner som skyddar de enheter som du hanterar från obehörig åtkomst eller skadliga attacker:
- [**Multi-factor Authentication**](protect-your-devices-with-microsoft-intune.md). Att lägga till ett extra lager av autentisering för användarinloggningar kan göra enheter ännu säkrare. Många enheter stöder Multi-factor Authentication som kräver en andra nivå av autentisering, till exempel ett telefonsamtal eller SMS, innan användarna kan få åtkomst.
- [**Microsoft Passport-inställningar**](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md). Microsoft Passport är en alternativ inloggningsmetod som gör att användarna kan använda en *gest*, till exempel ett fingeravtryck, eller Windows Hello för att logga in utan lösenord.
- [**Principer för att skydda Windows-datorer (med Intune-klientprogramvaran)**](policies-to-protect-windows-pcs-in-microsoft-intune.md). När du hanterar Windows-datorer med Intune-klientprogramvaran finns det principer som gör att du kan styra inställningar för Endpoint Protection, programuppdateringar och Windows-brandväggen på de datorer som du hanterar.

## <a name="retire"></a>Pensionera
När en enhet blir stulen eller tappas bort, när enheten behöver bytas ut eller när användarna flyttar till en annan tjänst är det vanligtvis dags att [dra tillbaka eller rensa](use-remote-wipe-to-help-protect-data-using-microsoft-intune.md) enheten. Det finns ett antal sätt att göra det, till exempel att återställa enheten, ta bort den från hantering eller rensa företagsdata på den.

