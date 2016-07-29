---
title: "Felsöka e-postprofiler | Microsoft Intune"
description: "Problem relaterade till e-postprofiler och hur du felsöker och löser dem."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 05/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9915b275101e287498217c4f35e1c0e56d2425c2
ms.openlocfilehash: 9b699229489be2f09ea4c7a80e1e80f6ec7b106e


---

# Felsöka e-postprofiler i Microsoft Intune
Det här avsnittet innehåller information om problem relaterade till e-postprofiler och hur du felsöker och löser dem.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.


## Det går inte att skicka bilder från e-postkontot
Användare med automatiskt konfigurerade e-postkonton kan inte skicka bilder från sina enheter.
Detta inträffar när alternativet **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

### Intune-lösning

1.  Öppna Microsoft Intune-administrationskonsolen och välj arbetsbelastningen **Princip** &gt;**Konfigurationsprincip**.

2.  Välj e-postprofilen och klicka på **Redigera**.

3.  Välj **Tillåt att e-post skickas från tredjepartsprogram.**

### Configuration Manager integrerat med Intune

1.  Öppna Configuration Manager-konsolen &gt;**Tillgångar och efterlevnad**.

2.  Expandera **Översikt** -&gt;**Efterlevnadsinställningar** -&gt;**Åtkomst till företagsresurser** och välj **E-postprofiler**.

3.  Högerklicka på e-postprofilen och öppna **Egenskaper**.

4.  Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**.

## Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft-supporten. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jul16_HO4-->


