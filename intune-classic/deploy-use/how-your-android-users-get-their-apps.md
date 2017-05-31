---
title: "Så får dina Android-användare sina appar | Microsoft Docs"
description: "Metoder för att göra Android-appar tillgängliga för slutanvändare"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: e76e17adac581efd64a54d90b23ad52a12417593
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---


# <a name="how-your-android-users-get-their-apps"></a>Så får dina Android-användare sina appar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Läs om hur och var dina Android-slutanvändare får de appar som du distribuerar via Microsoft Intune. Informationen kan variera för olika enhetstyper (Android-enheter eller Samsung Knox Standard-enheter).

## <a name="native-non-samsung-knox-standard-android-devices"></a>Interna (ej Samsung Knox Standard) Android-enheter

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Ett meddelande visas och användarna kan sedan trycka på det för att starta installationen. När installationen har slutförts försvinner meddelandet. | När användarna trycker på appen i företagsportalen dirigeras de till en appsida i Play Store där de kan starta installationen.|
| Required apps      | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. Användarna trycker på meddelandet för att starta installationen. När installationen har slutförts försvinner meddelandet.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store där de kan starta installationen. När installationen har slutförts försvinner meddelandet. |

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android-enheter

| Typ av app | Verksamhetsspecifika appar | Play Store-appar  |
| ------------- |-------------| -----|
| Tillgängliga appar      | Användarna trycker på **Installera** i företagsportalen. Appen installeras utan ytterligare åtgärder från användaren. | När användarna trycker på appen i företagsportalen dirigeras de till en appsida i Play Store där de kan starta installationen.|
| Required apps      | Appen installeras utan ytterligare åtgärder från användaren.    | Ett meddelande som inte kan stängas visas för användarna. I meddelandet står det att de måste installera en app. När användarna trycker på meddelandet dirigeras de till en appsida i Play Store där de kan starta installationen. När installationen har slutförts försvinner meddelandet. |

Appar kan vara hanterade eller ohanterade (se nedan). Processen för att göra appar hanterade är densamma för alla typer av Android-enheter.

**Hanterade appar** – Appar som kan hanteras med principer. De har blivit "omslutna" av Intune eller skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** – Appar som inte kan hanteras med principer. De har inte omslutits av Intune eller inkluderar inte Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

### <a name="see-also"></a>Se även
[Lägga till appar med Microsoft Intune](/intune-classic/deploy-use/add-apps)

[Så får dina iOS-användare sina appar](how-your-ios-users-get-their-apps.md)

[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)

