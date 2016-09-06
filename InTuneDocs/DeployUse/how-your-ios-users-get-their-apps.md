---
title: "Så får dina iOS-användare sina appar | Microsoft Intune"
description: "Metoder för att göra iOS-appar tillgängliga för slutanvändare"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# Så får dina iOS-användare sina appar

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** - Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** - Appar som kan hanteras med principer eller som har blivit "wrappade" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** - Appar som inte kan hanteras med principer eller som inte har wrappats av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, vilket innebär att användarna måste välja olika vyer om de vill hitta alla sina appar. Appar för varje panel som visas på företagsportalsappens appsida är tillgängliga enligt följande:

- Panelen **Företagsappar** pekar på en lista över alla appar på fliken **ALLA** på [företagsportalens webbplats](http://portal.manage.microsoft.com).

- Panelen **Andra appar** pekar för tillfället pekar på en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Detta inkluderar alla appar utom verksamhetsspecifika appar och hanterade App Store-appar.

- Panelen **Kategorier** pekar för tillfället pekar på en vy i företagsportalsappen som listar appkategorier.

    ![ios-hur-man-synkroniserar-enhet-med-intune](./media/ios-sync-comp-portal-apps.png)


###Se även
[Så får dina Android-användare sina appar](how-your-android-users-get-their-apps.md)</br>
[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->


