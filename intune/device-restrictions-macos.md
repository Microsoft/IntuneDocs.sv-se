---
title: Inställningar av enhetsbegränsningar för macOS i Microsoft Intune
titlesuffix: ''
description: Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på enheter som kör macOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f4cf5a5eb716760034b25b52098b9e65e6540c63
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-macos-device-restriction-settings"></a>Inställningar för enhetsbegränsningar för macOS-enheter i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln visas inställningarna för enhetsbegränsningar i Microsoft Intune som du kan konfigurera för enheter som kör macOS.

## <a name="password"></a>Lösenord
-   **Lösenord** – Kräver att användaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Required password type** – Ange om lösenordet kan vara endast Numeriskt eller om det måste vara Alfanumeriskt (innehålla bokstäver och siffror). Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.
    -   **Antal icke-alfanumeriska tecken i lösenord** – Ange antalet avancerade tecken i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol, t.ex. ”**?**”.
    -   **Minsta längd på lösenord** – Ange den minsta längd på lösenord som en användare måste konfigurera (mellan **4** och **16** tecken).
    -   **Enkla lösenord** – Låt användarna skapa enkla lösenord som **0000** eller **1234**.
    -   **Största antal minuter innan lösenord krävs efter det att skärmen låsts** –Ange hur länge datorn måste vara inaktiv innan ett lösenord krävs för att låsa upp den.
    -   **Maximalt antal minuter av inaktivitet innan skärmen låses** – Anger hur lång tid datorn måste vara i viloläge innan skärmen låses.
    -   **Lösenordets giltighetstid (i dagar)** – Ange efter hur många dagar användaren måste byta lösenord (**1** till **255** dagar).
    -   **Förhindra återanvändning av tidigare lösenord** – Ange antalet tidigare lösenord som inte får återanvändas (**1** till **24**).

## <a name="restricted-apps"></a>Begränsade appar

Du kan konfigurera en av följande listor i listan med begränsade appar:

- Listan **Otillåtna appar** – Ange de appar (som inte hanteras av Intune) som användarna inte får installera och köra. Användarna hindras inte från att installera en förbjuden app, men om de gör det rapporteras det till dig.
- Listan **Godkända appar** – Ange de appar som användare tillåts att installera. Användarna får inte installera appar som inte finns med i listan. Appar som hanteras av Intune tillåts automatiskt. Användare hindras inte från att installera en app som inte finns med på listan över godkända appar, men om de gör det rapporteras detta till dig.

Konfigurera listan genom att klicka på **Lägg till**, ange ett namn, t.ex. appens utgivare, och appens samlings-ID (t.ex. *com.apple.calculator*).

## <a name="domains"></a>Domäner

### <a name="unmarked-email-domains"></a>Avmarkerade e-postdomäner

I fältet **Webbadress till e-postdomän** lägger du till en eller flera webbadresser i listan. När slutanvändarna får ett e-postmeddelande från en annan domän än den du har konfigurerat, markeras e-postmeddelandet som ej betrott i iOS e-postappen.

