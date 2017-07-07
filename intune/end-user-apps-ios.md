---
title: "Så får dina iOS-användare sina appar"
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
ms.openlocfilehash: 0061d4ecd8d71f8b7363193e36b838741aa56a92
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-ios-users-get-their-apps"></a>Så får dina iOS-användare sina appar

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

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

Information om hur du lägger till appar och placerar dem på dessa paneler finns i [Lägga till appar för registrerade enheter i Intune](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Se även
[Så får dina Android-användare sina appar](end-user-apps-android.md)

[Så får dina Windows-användare sina appar](end-user-apps-windows.md)
