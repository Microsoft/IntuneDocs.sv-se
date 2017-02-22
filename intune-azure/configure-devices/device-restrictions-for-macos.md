---
title: "Inställning av begränsningar i Intune-enheter för macOS | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på macOS-enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3129cbaf-96c2-4837-8907-ca87a605a496
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1e9c97d66e80de635ad43a1339d092b7987f738b
ms.openlocfilehash: 6856303581f5275c88d5d4efe07088de8f7ab713


---

# <a name="macos-device-restriction-settings-in-intune-azure-preview"></a>Inställning av enhetsbegränsningar för macOS-enheter i förhandsversionen av Intune Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="password"></a>Lösenord
-   **Lösenord krävs** – Slutanvändaren måste ange ett lösenord för att få åtkomst till enheten.
    -   **Required password type** – Ange om lösenordet kan vara endast Numeriskt eller om det måste vara Alfanumeriskt (innehålla bokstäver och siffror). Den här inställningen stöds endast i Mac OS X version 10.10.3 och senare.
    -   **Antal icke-alfanumeriska tecken i lösenord** – Ange antalet avancerade tecken i lösenordet (**0** till **4**).<br>Ett avancerat tecken är en symbol som **?**.
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





<!--HONumber=Feb17_HO1-->


