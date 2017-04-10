---
title: "Uppgradera principinställningar för Windows-version | Microsoft Docs"
description: "Läs om hur du uppgraderar Windows 10-enheter automatiskt till den senaste versionen med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ae6477866991cec4091ff2790b925b0e464375f9


---

# <a name="windows-edition-upgrade-policy-settings-in-microsoft-intune"></a>Uppgradera principinställningar för Windows-version i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intunes **princip för versionsuppgradering** kan du automatiskt uppgradera enheter som körs på en av följande Windows 10-versioner till en senare version:
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobil

Följande uppgraderingsvägar stöds:
- Från Windows 10 Pro till Windows 10 Enterprise
- Från Windows 10 Home till Windows 10 Education
- Från Windows 10 Mobile till Windows 10 Mobile Enterprise
- Från Windows 10 Holographic Pro till Windows 10 Holographic Enterprise

## <a name="before-you-start"></a>Innan du börjar
Innan du börjar uppgradera enheter till den senaste versionen behöver du något av följande:
* En produktnyckel som är giltig för att installera den nya versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner). Du kan använda antingen multipla aktiveringsnycklar (MAK) eller nyckelhanteringsserver (KMS).
**eller** En licensfil från Microsoft som innehåller licensinformationen för att installera den nya Windows-versionen på alla enheter som du riktar principen mot (för Windows 10 Mobile- och Windows 10 Holographic-versioner).
* Windows 10-målenheterna måste vara registrerade i Microsoft Intune. Du kan inte använda versionsuppgraderingsprincipen för datorer som kör Intune-klientprogrammet.

## <a name="edition-upgrade-policy-settings"></a>Inställningar för princip för versionsuppgradering

|Inställningsnamn|Information|
|-|-|
|**Namn**|Ange ett namn på principen för versionsuppgradering.|
|**Beskrivning**|Du kan även ange en beskrivning för principen som hjälper dig att identifiera den i Intune-konsolen.
|**Version att uppgradera till**|I listrutan väljer du den version av Windows 10 Desktop, Windows 10 Holographic eller Windows 10 Mobile som du vill uppgradera riktade enheter till.
|**Produktnyckel**|Ange produktnyckeln som du har skaffat från Microsoft som kan användas för att uppgradera alla Windows 10 Desktop-målenheter.<br>När du har skapat en princip som innehåller en produktnyckel kan du inte redigera produktnyckeln senare. Det beror på att nyckeln döljs av säkerhetsskäl. Om du vill ändra produktnyckeln måste du ange hela nyckeln igen.
|**Licensfil**|Klicka på **Bläddra** och välj den licensfil som du har fått från Microsoft och som innehåller licensinformation för den Windows Holographic- eller Windows 10 Mobile-version som du vill uppgradera målenheterna till.

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO2-->


