---
title: "Så får dina Android-användare sina appar | Microsoft Intune"
description: "Metoder för att göra Android-appar tillgängliga för slutanvändare"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 90f50d14fac0e335f3b7c5e0825b0bb243b7a532


---


# Så får dina Android-användare sina appar
Läs om hur och var dina Android-slutanvändare får de appar som du distribuerar via Microsoft Intune. Informationen kan vara olika för Android-enheter och Samsung Knox-enheter.

## Android-enheter (inte Samsung KNOX)

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Ett meddelande visas och användarna kan sedan trycka på det för att starta installationen. När installationen har slutförts försvinner meddelandet. | När användarna trycker på appen i företagsportalen dirigeras de till en appsida i Play Store där de kan starta installationen.|
| Required apps      | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. Användarna trycker på meddelandet för att starta installationen. När installationen har slutförts försvinner meddelandet.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store där de kan starta installationen. När installationen har slutförts försvinner meddelandet. |

## Android-enheter (Samsung KNOX)

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Appen installeras utan ytterligare åtgärder från användaren. | När användarna trycker på appen i företagsportalen dirigeras de till en appsida i Play Store där de kan starta installationen.|
| Required apps      | Appen installeras utan ytterligare åtgärder från användaren.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store där de kan starta installationen. När installationen har slutförts försvinner meddelandet. |

Appar kan vara hanterade eller ohanterade (se nedan). Processen för att göra appar hanterade är densamma för alla typer av Android-enheter.

**Hanterade appar** - Appar som kan hanteras med principer eller som har blivit "wrappade" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** - Appar som inte kan hanteras med principer eller som inte har wrappats av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

### Se även
[Lägg till appar med Microsoft Intune](/intune/deploy-use/add-apps)
[Så får dina iOS-användare sina appar](how-your-ios-users-get-their-apps.md)
[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)



<!--HONumber=Jul16_HO4-->


