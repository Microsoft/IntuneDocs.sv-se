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
ms.sourcegitcommit: 52b9e786fe22b04081441db88a3629062fc85668
ms.openlocfilehash: a215d547507dcc460e83009cc6a04baf3fd8f4a4


---


# Så får dina iOS-användare sina appar

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** - Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** - Appar som kan hanteras med principer eller som har blivit "wrappade" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** - Appar som inte kan hanteras med principer eller som inte har wrappats av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen. För att undvika problemet visar app-panelerna i företagsportalsappen för iOS användarna flera vyer på en och samma plats (företagsportalens webbplats) för alla deras appar enligt följande:

- Panelen **Företagsappar** visade tidigare en lista över alla program under fliken ALLA på [företagsportalens webbplats](http://portal.manage.microsoft.com), och den kommer att fortsätta fungera på samma sätt. Namnet på panelen har ändrats till **Alla appar**.

- Panelen **Andra appar** visade tidigare en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen har ändrats till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.

-  Panelen **Kategorier** visade tidigare en vy i företagsportalsappen som listar appkategorier. Panelens namn har inte ändras, men den nu att pekar nu på fliken KATEGORIER på företagsportalens webbplats.
Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



###Se även
[Så får dina Android-användare sina appar](how-your-android-users-get-their-apps.md)</br>
[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)



<!--HONumber=Sep16_HO3-->


