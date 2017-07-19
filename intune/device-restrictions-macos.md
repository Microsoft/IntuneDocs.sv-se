---
title: "Inställningar för enhetsbegränsning för macOS i Intune"
titleSuffix: Intune on Azure
description: "Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på macOS-enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 716ca0a2041bdd2ecfadd180999a09f80373cb2a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="macos-device-restriction-settings-in-microsoft-intune"></a>Inställningar för enhetsbegränsningar för macOS-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd de här inställningarna för att hantera macOS-enheter i en profil för begränsning av enheter.

## <a name="password"></a>Lösenord
-   **Lösenord krävs** – Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Required password type** – Ange om lösenordet kan vara endast Numeriskt eller om det måste vara Alfanumeriskt (innehålla bokstäver och siffror). Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.
    -   **Antal icke-alfanumeriska tecken i lösenord** – Ange antalet avancerade tecken i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol, t.ex. **?**
    -   **Minsta längd på lösenord** – Ange den minsta längd på lösenord som en användare måste konfigurera (mellan **4** och **16** tecken).
    -   **Enkla lösenord** – Låt användarna skapa enkla lösenord som **0000** eller **1234**.
    -   **Största antal minuter innan lösenord krävs efter det att skärmen låsts** –Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid datorn måste vara i viloläge innan skärmen låses.
    -   **Lösenordets giltighetstid (i dagar)** – Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).
    -   **Förhindra återanvändning av tidigare lösenord** – Ange antalet tidigare lösenord som inte får återanvändas (**1** till **24**).

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra.
Listan **Godkända appar** – Ange de appar som användare tillåts att installera. För att fortsätta vara kompatibla får användarna inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare, och appens samlings-ID (t.ex. *com.apple.calculator*).

## <a name="domains"></a>Domains

### <a name="unmarked-email-domains"></a>Avmarkerade e-postdomäner

I fältet **Webbadress till e-postdomän** lägger du till en eller flera webbadresser i listan. När användarna får ett e-postmeddelande från en annan domän än den du har konfigurerat, markeras e-postmeddelandet som ej betrott i iOS e-postappen.

