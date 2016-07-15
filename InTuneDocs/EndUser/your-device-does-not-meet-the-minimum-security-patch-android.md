---
title: "Enheten uppfyller inte minimikraven för säkerhetskorrigering | Microsoft Intune"
description: 
keywords: 
author: staciebarker
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b3e5994c-d215-4c72-8915-349bd0b2504d
ms.sourcegitcommit: b76c04545b9b26a0e2470b95a3f5ac0a81b07817
ms.openlocfilehash: a4788340b36c7d04ff1a62844aea7dba06079a2b


---

# Enheten uppfyller inte minimikraven för säkerhetskorrigering

Om meddelandet ”Lägsta Android-säkerhetskorrigeringsnivå har inte konfigurerats” (eller liknande) visas måste du minst installera den lägsta säkerhetskorrigeringen, eller en senare säkerhetskorrigering. IT-administratören kräver den här installationen för att skydda företagsdata på din Android-enhet.

Den aktuella säkerhetskorrigeringsnivån kan finnas på olika platser, beroende på vilken typ av Android-enhet du har. Du måste ta reda på om du har en Samsung Knox-enhet eller någon annan typ av Android-enhet. Om du vill ta reda på om du har en Samsung Knox-enhet väljer du **Inställningar** > **Om telefonen**. Om du inte ser ordet ”Knox” i listan har du inte en Samsung Knox-enhet.

**Så här hittar du den senaste programvaruversionen på enheten:**

- Ej Samsung Knox-enheter: Välj **Inställningar** > **Om** > **Programvaruinformation** > **Mer** och se **Android-säkerhetskorrigeringsnivå**. Menynamnen och platserna varierar lite mellan olika Android-enheter.

- Samsung Knox-enheter: Välj **Inställningar** > **Om telefonen** > **Säkerhetsprogramvaruversion**.

**Så här installerar du säkerhetskorrigeringen:**

- Ej Samsung Knox-enheter: Välj **Inställningar** > **Om** > **Programvaruuppdateringar**. 

- Samsung Knox-enheter: Välj **Inställningar** > **Systemuppdateringar** > **Sök efter ny systemuppdatering**.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

### Se även
[Med hjälp av en Android-enhet med Intune](using-your-android-device-with-intune.md)



<!--HONumber=Jul16_HO2-->


