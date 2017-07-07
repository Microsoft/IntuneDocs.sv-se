---
title: "Så får dina Android-användare sina appar"
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
ms.openlocfilehash: 4f0364750edf2e97e2b621c27fb25bea8e0f537c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Så får dina Android-användare sina appar

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

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
[Lägga till appar med Microsoft Intune](apps-add.md)

[Så får dina iOS-användare sina appar](end-user-apps-ios.md)

[Så får dina Windows-användare sina appar](end-user-apps-windows.md)
