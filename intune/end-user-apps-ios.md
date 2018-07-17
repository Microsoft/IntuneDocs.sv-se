---
title: Så får dina iOS-användare sina appar
description: Metoder för att göra iOS-appar tillgängliga för slutanvändare
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/28/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7744d8422e774242e0883c8d77814c42fd71895f
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38224833"
---
# <a name="how-your-ios-users-get-their-apps"></a>Så får dina iOS-användare sina appar

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** – Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** – Appar som kan hanteras med principer och har blivit "omslutna" av Intune eller skapats med Intune App Software Development Kit (SDK). De här apparna kan hanteras av Intune och appskyddsprinciper kan tillämpas på dem.

**Ohanterade appar** – Appar som inte kan hanteras med principer eller som inte har omslutits av Intune eller som inte inkluderar Intunes App SDK. Applikations-policys kan inte tillämpas på de här apparna.

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade appbutiks-appar listas i företagsportalsappen. För att undvika problemet visar panelerna i företagsportalsappen för iOS användarna flera vyer på en och samma plats (företagsportalens webbplats) för alla deras appar.

Registrerade användare får sina appar genom att trycka på följande paneler på skärmen Appar i företagsportalappen:

- **Alla appar** pekar på en lista över alla appar på fliken ALLA på [företagsportalens webbplats](https://portal.manage.microsoft.com).

- **Aktuella appar** omdirigerar användarna till fliken AKTUELLA på företagsportalens webbplats.

- **Kategorier** pekar på fliken KATEGORIER på företagsportalens webbplats.


![Skärmen Appar på företagsportalen för iOS](./media/ios-cp-app-main-apps-screen.png)

Mer information om hur man lägger till appar finns i [Så här lägger du till en app i Microsoft Intune](apps-add.md).

### <a name="see-also"></a>Se även
[Så får dina Android-användare sina appar](end-user-apps-android.md)

[Så får dina Windows-användare sina appar](end-user-apps-windows.md)
