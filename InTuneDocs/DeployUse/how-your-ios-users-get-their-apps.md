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
ms.sourcegitcommit: 37841027c7ae040163440a19f9e163fb4eb87233
ms.openlocfilehash: ad780fb3403f6caaee1218d785a5cad326c18df5


---


# Så får dina iOS-användare sina appar

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** – Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** – Appar som kan hanteras med principer eller som har blivit "omslutna" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** – Appar som inte kan hanteras med principer eller som inte har omslutits av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade appbutiks-appar listas i företagsportalsappen. För att undvika problemet visar panelerna i företagsportalsappen för iOS användarna flera vyer på en och samma plats (företagsportalens webbplats) för alla deras appar.

- **Företagsappar** visade tidigare en lista över alla program under fliken ALLA på [företagsportalens webbplats](http://portal.manage.microsoft.com), och den kommer att fortsätta fungera på samma sätt. Namnet på panelen har ändrats till **Alla appar**.

- **Andra appar** visade tidigare en vy i företagsportalsappen som visade alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen har ändrats till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.

-  **Kategorier** visade tidigare en vy i företagsportalsappen som listade appkategorier. Panelens namn har inte ändrats, men den pekar nu på fliken KATEGORIER på företagsportalens webbplats.
Du hittar uppdaterade skärmbilder i [Förbättringar i hur iOS-slutanvändare får sina appar](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).



### Se även
[Så får dina Android-användare sina appar](how-your-android-users-get-their-apps.md)

[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)



<!--HONumber=Oct16_HO2-->


