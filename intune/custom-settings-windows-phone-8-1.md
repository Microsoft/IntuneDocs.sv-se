---
title: "Anpassade inställningar i Intune för Windows Phone 8.1-enheter"
titleSuffix: Intune on Azure
description: "Läs om inställningarna du kan använda i en anpassad Windows 8.1-profil.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b3dcad95b85d967e48c8b05d655a5e679daa0aee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Anpassade inställningar för Windows Phone 8.1-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd profilen **Anpassad** för Windows Phone 8.1 i Microsoft Intune för att tilldela OMA-URI-inställningar som kan användas till att styra funktioner på Windows Phone 8.1-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela inställningar som inte går att konfigurera med andra Intune-principer.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Anpassade principinställningar för Windows Phone 8.1-enheter

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. På bladet **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På bladet **Lägg till rad** konfigureras följande värden för varje inställning:
    - **Namn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning** – Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.
    - **OMA-URI** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj **Sträng**, **Datum och tid**, **Heltal**, **Flyttal** eller **Booleskt**.
    - **Värde** – Ange det värde som du vill associera med den OMA-URI som du har angett.

4. Klicka på **OK** när du är klar och fortsätt sedan att lägga till fler inställningar efter behov.
