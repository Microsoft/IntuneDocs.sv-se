---
# required metadata

title: Uppgradera principinställningar för Windows-version i Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Uppgradera principinställningar för Windows-version i Microsoft Intune
Med Microsoft Intunes **princip för versionsuppgradering** kan du automatiskt uppgradera enheter som körs på en av följande Windows 10-versioner till en senare version:
* Windows 10 Desktop
* Windows 10 Holographic

## Innan du börjar
Innan du börjar uppgradera enheter till den senaste versionen behöver du något av följande:
* En produktnyckel som är giltig för att installera den nya versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner).
* En licensfil från Microsoft som innehåller licensinformationen för att installera den nya versionen på alla enheter som du riktar principen mot (för Windows 10 Mobile- och Windows 10 Holographic-versioner).
* Windows 10-enheter som du riktar in dig på måste vara registrerade i Microsoft Intune.

## Inställningar för princip för versionsuppgradering

|Inställningsnamn|Information|
|-|-|
|**Namn**|Ange ett namn på principen för versionsuppgradering.|
|**Beskrivning**|Du kan även ange en beskrivning för principen som hjälper dig att identifiera den i Intune-konsolen.
|**Version att uppgradera till**|I listrutan väljer du den version av Windows 10 Desktop, Windows 10 Holographic eller Windows 10 Mobile som du vill uppgradera riktade enheter till.
|**Produktnyckel**|Ange produktnyckeln som du har skaffat från Microsoft som kan användas för att uppgradera alla inriktade Windows 10 Desktop-enheter.<br>När du har skapat en princip som innehåller en produktnyckel kan du inte redigera produktnyckeln senare. Det beror på att nyckeln döljs av säkerhetsskäl. Om du vill ändra produktnyckeln måste du ange hela nyckeln igen.
|**Licensfil**|Klicka på **Bläddra** för att välja den licensfil som du har skaffat från Microsoft som innehåller licensinformation för den Windows Holographic-version som du vill uppgradera riktade enheter till.

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

<!--HONumber=May16_HO1-->


