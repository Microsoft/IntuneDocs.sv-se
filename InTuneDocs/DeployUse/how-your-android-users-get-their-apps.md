---
title: "Så får dina Android-användare sina appar | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Så får dina Android-användare sina appar
Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune. 

**Obligatoriska appar** - Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.
 
- **Samsung Knox-enheter**: Om du distribuerar en obligatorisk app till Samsung Knox-enheter installeras den automatiskt obevakat på enheten.
- **Ursprunglig enhet (inte Samsung Knox-enheter)**: Om du distribuerar en obligatorisk app till andra enheter än Samsung Knox-enheter installeras den inte automatiskt på användarnas enheter. I stället uppmanas användarna att installera appen. När användarna accepterar laddas appen ned. Sedan visas ett meddelande om att de behöver installera appen. 

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** - Appar som kan hanteras med principer eller som har blivit "wrappade" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** - Appar som inte kan hanteras med principer eller som inte har wrappats av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

###Se även
[Lägg till appar med Microsoft Intune](/intune/deploy-use/add-apps)
[Så får dina iOS-användare sina appar](how-your-ios-users-get-their-apps.md)
[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


