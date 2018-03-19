---
title: "Anpassade inställningar i Microsoft Intune för enheter som kör Windows Phone 8.1"
titleSuffix: 
description: "Läs om inställningarna du kan använda i en anpassad Windows 8.1-profil."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f45b2dd9cab0ccfd912d1f1348d90264bf8906b8
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Anpassade enhetsinställningar i Microsoft Intune för enheter som kör Windows Phone 8.1

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd profilen **Anpassad** för Windows Phone 8.1 i Microsoft Intune för att tilldela OMA-URI-inställningar som kan användas till att styra funktioner på Windows Phone 8.1-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela inställningar som inte går att konfigurera med andra Intune-principer.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Anpassade principinställningar för Windows Phone 8.1-enheter

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. I fönstret **Anpassade OMA-URI-inställningar** väljer du **Lägg till** för att lägga till en eller flera OMA-URI-inställningar.
3. I fönstret **Lägg till rad** konfigureras följande värden för varje inställning:
    - **Namn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning** – Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.
    - **OMA-URI** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj mellan **Sträng**, **Sträng (XML)**, **Datum och tid**, **Heltal**, **Flyttal**, **Boolesk** eller **Base64**.
    - **Värde** – Ange det värde eller den fil som du vill associera med den OMA-URI som du har angett.

4. Klicka på **OK** när du är klar och fortsätt sedan att lägga till fler inställningar efter behov.
