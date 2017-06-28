---
title: "Använd principer för att förenkla hanteringen av Windows-datorer"
description: "Beskriver principerna för hantering av Windows-datorer och inställningarna för Microsoft Intune Center."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f0afda7e-f4c3-4bcd-b4bf-4304103cf73e
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: e14b5c56356812fdc3ea775cddde0f668b344177
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="use-policies-to-simplify-windows-pc-management"></a>Använd principer för att förenkla hanteringen av Windows-datorer

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Om du vill hantera stationära Windows-datorer som datorer genom att köra Intune-programvaruklienten på dem kan du endast använda de principer som ligger under principerna för **Datorhantering** i Intune-administratörskonsolen. Alla andra principer som visas i administrationskonsolen gäller endast för mobila enheter. Genom att använda principer för **datorhantering** kan du konfigurera inställningarna i Microsoft Intune Center, hantera datoruppdateringar och konfigurera Windows-brandväggen för datorer.

![Principmall för Windows-datorer](../media/pc_policy_template.png)

### <a name="manage-the-microsoft-intune-center"></a>Hantera Microsoft Intune Center
Användarna ser Intune-klientprogrammet som **Microsoft Intune Center**. Med Microsoft Intune Center kan användarna:

-   Hämta program från företagsportalen.

-   Söka efter uppdateringar.

-   Hantera Microsoft Intune Endpoint Protection.

-  Begära fjärrhjälp.

Microsoft Intune Center är installerat på alla hanterade datorer. Du kan konfigurera följande inställningar i en Intune-princip och dessa visas för användaren i Microsoft Intune Center:

|Principinställningar|Information|
|------------------|--------------------|
|**Namn**|Namnet på den administratör som hanterar datorn.<br />Maxlängd: 40 tecken|
|**Telefonnummer**|Telefonnumret till den administratör som hanterar datorn.<br />Maxlängd: 20 tecken|
|**E-postadress**|E-postadressen till den administratör som hanterar datorn.<br />Maxlängd: 40 tecken|
|**Webbplatsnamn**|Namnet på användarnas supportwebbplats.<br />Maxlängd: 40 tecken|
|**Webbadress**|Webbadressen till supportwebbplatsen.<br />Maxlängd: 150 tecken|
|**Anmärkningar**|En kommentar som visas för användarna.<br />Maxlängd: 120 tecken|

Information om principer och inställningar som du kan konfigurera för Windows-datorer finns i följande resurser:

- [Hålla Windows-datorer uppdaterade med programuppdateringar i Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) – Dessa principer kör kontroller av hanterade datorer för, och laddar ned programvaruuppdateringar från, Microsoft och tredje parter. Dessa uppdateringar innehåller inte OS-uppgraderingar (t.ex. uppgradering från Windows 7 till Windows 10, eller uppgradering från en version av Windows 10 till en senare version).

- [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md) – Dessa inställningar omfattar genomsökningsscheman och åtgärder som ska vidtas om skadlig kod upptäcks.

- [Skydda Windows-datorer med Windows-brandväggsprinciper i Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) – Dessa principer förenklar administrationen av inställningar för Windows-brandväggen på hanterade datorer.


### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)

