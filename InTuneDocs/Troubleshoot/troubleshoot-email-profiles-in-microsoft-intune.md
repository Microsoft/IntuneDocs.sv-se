---
# required metadata

title: Felsöka e-postprofiler | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Felsöka e-postprofiler i Microsoft Intune
Det här avsnittet innehåller information om problem relaterade till e-postprofiler och hur du felsöker och löser dem.

Om du inte lyckas lösa problemet med hjälp av den här informationen läser du [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md), som beskriver hur du kan få hjälp på fler sätt.


## Det går inte att skicka bilder från e-postkontot
Användare med automatiskt konfigurerade e-postkonton kan inte skicka bilder från sina enheter.
Detta inträffar när alternativet **Tillåt att e-post skickas från tredjepartsprogram** inte är aktiverat.

### Intune-lösning

1.  Öppna Microsoft Intune-administrationskonsolen och välj arbetsbelastningen **Princip** &gt; **Konfigurationsprincip**

2.  Välj e-postprofilen och klicka på **Redigera**

3.  Välj **Tillåt att e-post skickas från tredjepartsprogram.**

### Configuration Manager integrerat med Intune

1.  Öppna Configuration Manager-konsolen &gt; **Tillgångar och efterlevnad**.

2.  Expandera **Översikt** -&gt; **Kompatibilitetsinställningar** -&gt; **Åtkomst till företagsresurs** och välj **E-postprofiler**

3.  Högerklicka på e-postprofilen och öppna **Egenskaper**

4.  Välj **Tillåt att e-post skickas från tredjepartsprogram** på fliken **Synkroniseringsinställningar**

## Nästa steg
Om du inte lyckas lösa problemet med hjälp av den här felsökningsinformationen kontaktar du Microsoft Support. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](how-to-get-support-for-microsoft-intune.md)


<!--HONumber=May16_HO2-->

