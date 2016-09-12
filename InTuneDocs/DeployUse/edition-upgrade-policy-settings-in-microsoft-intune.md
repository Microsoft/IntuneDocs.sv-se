---
title: "Uppgradera principinställningar för Windows-version | Microsoft Intune"
description: "Läs om hur du uppgraderar Windows 10-enheter automatiskt till den senaste versionen med Intune."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06a9c78300d7ff384299957102114c69c43a1ad5
ms.openlocfilehash: 45130e3e12968d9df579a7a9d0cade0343b7c165


---

# Uppgradera principinställningar för Windows-version i Microsoft Intune
Med Microsoft Intunes **princip för versionsuppgradering** kan du automatiskt uppgradera enheter som körs på en av följande Windows 10-versioner till en senare version:
* Windows 10 Desktop
* Windows 10 Holographic
* Windows 10 Mobil

## Innan du börjar
Innan du börjar uppgradera enheter till den senaste versionen behöver du något av följande:
* En produktnyckel som är giltig för att installera den nya versionen av Windows på alla enheter som du riktar principen mot (för Windows 10 Desktop-versioner). Du kan använda antingen multipla aktiveringsnycklar (MAK) eller nyckelhanteringsserver (KMS).
**eller** En licensfil från Microsoft som innehåller licensinformationen för att installera den nya Windows-versionen på alla enheter som du riktar principen mot (för Windows 10 Mobile- och Windows 10 Holographic-versioner).
* Windows 10-målenheterna måste vara registrerade i Microsoft Intune. Du kan inte använda versionsuppgraderingsprincipen för datorer som kör Intune-klientprogrammet.

## Inställningar för princip för versionsuppgradering

|Inställningsnamn|Information|
|-|-|
|**Namn**|Ange ett namn på principen för versionsuppgradering.|
|**Beskrivning**|Du kan även ange en beskrivning för principen som hjälper dig att identifiera den i Intune-konsolen.
|**Version att uppgradera till**|I listrutan väljer du den version av Windows 10 Desktop, Windows 10 Holographic eller Windows 10 Mobile som du vill uppgradera riktade enheter till.
|**Produktnyckel**|Ange produktnyckeln som du har skaffat från Microsoft som kan användas för att uppgradera alla Windows 10 Desktop-målenheter.<br>När du har skapat en princip som innehåller en produktnyckel kan du inte redigera produktnyckeln senare. Det beror på att nyckeln döljs av säkerhetsskäl. Om du vill ändra produktnyckeln måste du ange hela nyckeln igen.
|**Licensfil**|Klicka på **Bläddra** och välj den licensfil som du har fått från Microsoft och som innehåller licensinformation för den Windows Holographic- eller Windows 10 Mobile-version som du vill uppgradera målenheterna till.

### Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO5-->


