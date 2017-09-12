---
title: "Anpassade inställningar för Android-enheter i Intune"
titleSuffix: Azure portal
description: "Läs om vilka inställningar du kan använda i en anpassad Android-profil.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 92014eb9fd5564c0527b8cbf68732a51cf83bc96
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Anpassade inställningar för Android-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd **Anpassad** profil för Android i Microsoft Intune för att tilldela OMA-URI-inställningar som kan användas för att styra funktioner på Android-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela Android-inställningar som inte går att konfigurera med Intune-principer.

## <a name="custom-profile-settings-for-android-devices"></a>Anpassade profilinställningar för Android-enheter

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](custom-settings-configure.md).
2. På bladet **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På bladet **Redigera rad** konfigureras följande värden för varje inställning:
    - **Namn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Beskrivning** – Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj mellan **Sträng**, **Sträng (XML)**, **Datum och tid**, **Heltal**, **Flyttal** och **Boolesk**.
    - **OMA-URI** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Värde** – Ange det värde som du vill associera med den OMA-URI som du har angett.
4. Klicka på **OK** när du är klar och fortsätt sedan att lägga till fler inställningar efter behov.

## <a name="next-steps"></a>Nästa steg

När du slutför inställningarna skapas profilen och den visas på bladet med profillistan. Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).

Om du vill ha några exempel på anpassade inställningar som du kan skapa kan du se:

- [Använd en anpassad enhetsprofil för Microsoft Intune för att skapa en Wi-Fi-profil med en i förväg delad nyckel](/intune/wi-fi-profile-shared-key)
- [Använd en anpassad Microsoft Intune-profil för att skapa en VPN-profil per app för Android-enheter](/intune/android-pulse-secure-per-app-vpn)
- [Använd anpassade principer för att tillåta och blockera appar för Samsung KNOX Standard-enheter i Microsoft Intune](/intune/samsung-knox-apps-allow-block)
