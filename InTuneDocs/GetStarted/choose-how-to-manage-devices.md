---
title: "Välj hur du vill hantera enheter | Microsoft Intune"
description: "Läs om de olika sätten att registrera och hantera enheter."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/31/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e3f27837195e5fdf58b9c13f38b0e5c0ad90d971
ms.openlocfilehash: 86b33ff528a2922e62c4c726bc8ce5f6bdbcfa38


---

# Välj hur du vill hantera enheter

För att du ska kunna utnyttja flera av funktionerna i Intune, till exempel appdistribution och kontroll av enhetsinställningar, måste enheterna vara *hanterade*. Hur du hanterar enheter beror på vilka Intune-funktioner som du vill använda.
Det här avsnittet hjälper dig att välja den metod som passar dina behov.

Om du vill hantera enheter som kör iOS, Mac OS X, Android eller Windows Phone, måste du *registrera* dem.

Om du vill hantera Windows-datorer har du två alternativ:

1. Registrera enheten **eller**
2. Installera *Intune-klientprogrammet*.

## Bestämma vilken metod du ska använda
Använd det här beslutsflödet för att avgöra hur du ska få enheterna hanterade.

![Beslutsflöde för hur du får enheterna hanterade.](./media/choose-manage-method.png)

Du får mest funktioner om du registrerar Windows-datorerna. Intune-klientprogrammet kan dock passa bättre om:

- Datorn kör Windows 7
- Du vill hantera Windows-programvaruuppdateringar och licensanvändning
- Du vill hantera skadlig kod med Endpoint Protection och Windows-brandväggen
- Du vill tillhandahålla fjärrhjälp till användare med programmet TeamViewer


En detaljerad lista över de hanteringsfunktioner som du får med varje metod finns i [Funktioner för hantering av mobilenheter](mobile-device-management-capabilities-in-microsoft-intune.md) och [Funktioner för Intune PC-klientprogrammet](windows-pc-management-capabilities-in-microsoft-intune.md).
Information om vilka enheter och datorer som Intune stöder finns i [Mobila enheter och datorer som stöds](/intune/get-started/supported-mobile-devices-and-computers)


## Exchange ActiveSync-hantering
Utöver att registrera en enhet eller installera Intune-klientprogrammet kan du även hantera enheter med [Exchange ActiveSync](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune). Den här metoden kräver att du installerar den lokala anslutningen eller använder den inbyggda tjänst-till-tjänst-anslutningen för att ansluta till Exchange Server.
Det här är dock ett tredje alternativ för att hantera enheter som erbjuder en begränsad uppsättning funktioner jämfört med de andra metoderna.


## Nästa steg

- [Välj hur du vill registrera mobila enheter](/intune/get-started/choose-how-to-enroll-devices1)
- [Hantera Windows-datorer med Intune-klientprogramvara](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)



- [Exchange ActiveSync-hantering av mobila enheter med Microsoft Intune](/intune/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune).




<!--HONumber=Aug16_HO5-->


