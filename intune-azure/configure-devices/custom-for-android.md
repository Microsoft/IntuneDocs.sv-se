---
title: "Intunes anpassade inställningar för Android-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Lär dig mer om vilka inställningar du kan använda i en anpassad Android-profil."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab494a3dd1e1bdea9703ab314574b192c5208ee
ms.openlocfilehash: 3a80a69a27b540b66fb96e098c0b0f66a0854297


---

# <a name="custom-settings-for-android-devices-in-intune-azure-preview"></a>Anpassade inställningar för Android-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd **Anpassad** profil för Android i Microsoft Intune för att distribuera OMA-URI-inställningar som kan användas för att styra funktioner på Android-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna distribuera Android-inställningar som inte går att konfigurera med Intune-principer.

## <a name="custom-profile-settings-for-android-devices"></a>Anpassade profilinställningar för Android-enheter

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](how-to-configure-custom-settings.md).
2. På bladet **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På bladet **Redigera rad** konfigureras följande värden för varje inställning:
    - **Namn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning** – Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj mellan **Sträng**, **Sträng (XML)**, **Datum och tid**, **Heltal**, **Flyttal** och **Boolesk**.
    - **OMA-URI** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Värde** – Ange det värde som du vill associera med den OMA-URI som du har angett.
4. Klicka på **OK** när du är klar och fortsätt sedan att lägga till fler inställningar efter behov.



<!--HONumber=Feb17_HO1-->


