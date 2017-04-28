---
title: "Så får dina iOS-användare sina appar | Microsoft Docs"
description: "Metoder för att göra iOS-appar tillgängliga för slutanvändare"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 02e54d4ae2ffa860fb95725c74fdff913e88365b
ms.lasthandoff: 04/24/2017


---


# <a name="how-your-ios-users-get-their-apps"></a>Så får dina iOS-användare sina appar

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** – Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** – Appar som kan hanteras med principer eller som har blivit "omslutna" av Intune eller som har skapats med Intune Mobile Application Management (MAM) Software Development Kit (SDK). De här apparna kan hanteras av Intune och applikations-policys kan tillämpas på dem.

**Ohanterade appar** – Appar som inte kan hanteras med principer eller som inte har omslutits av Intune eller som inte inkluderar Intunes MAM SDK. Applikations-policys kan inte tillämpas på de här apparna.

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade appbutiks-appar listas i företagsportalsappen. För att undvika problemet visar panelerna i företagsportalsappen för iOS användarna flera vyer på en och samma plats (företagsportalens webbplats) för alla deras appar.

Registrerade användare får sina appar genom att trycka på följande paneler på skärmen Appar i företagsportalappen:

- **Alla appar** pekar på en lista över alla appar på fliken ALLA på [företagsportalens webbplats](https://portal.manage.microsoft.com).

- **Aktuella appar** omdirigerar användarna till fliken AKTUELLA på företagsportalens webbplats.

- **Kategorier** pekar på fliken KATEGORIER på företagsportalens webbplats.


![Skärmen Appar på företagsportalen för iOS](./media/ios-cp-app-main-apps-screen.png)

Information om hur du lägger till appar och placerar dem på dessa paneler finns i [Lägga till appar för registrerade enheter i Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Se även
[Så får dina Android-användare sina appar](how-your-android-users-get-their-apps.md)

[Så får dina Windows-användare sina appar](how-your-windows-users-get-their-apps.md)

