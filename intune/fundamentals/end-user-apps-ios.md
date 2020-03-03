---
title: Så får dina iOS/iPadOS-användare sina appar
description: Metoder för att göra iOS/iPadOS-appar tillgängliga för slutanvändare
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 344c2e3f3ed53852aa6b749c9ebf6d451dd313ff
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514395"
---
# <a name="how-your-iosipados-users-get-their-apps"></a>Så får dina iOS/iPadOS-användare sina appar

Använd informationen för att förstå hur och var dina slutanvändare får de appar som du distribuerar via Microsoft Intune.

**Obligatoriska appar** – Appar som krävs av administratören och som installeras på enheten med minimal inblandning av användaren, beroende på plattform.

**Tillgängliga appar** – Appar som finns i företagsportalens applista och som en användare kan välja att installera.

**Hanterade appar** – Appar som kan hanteras med principer och har blivit "omslutna" av Intune eller skapats med Intune App Software Development Kit (SDK). De här apparna kan hanteras av Intune och appskyddsprinciper kan tillämpas på dem.

**Ohanterade appar** – appar som användare kan ladda ned från iOS/iPadOS App Store som inte är integrerade med Intune App SDK. Intune har ingen kontroll över distribution, hantering eller selektiv rensning av dessa appar.  

Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade appbutiks-appar listas i företagsportalsappen. För att undvika problemet visar panelerna i företagsportalsappen för iOS/iPadOS användarna flera vyer på en och samma plats (företagsportalens webbplats) för alla deras appar.

Registrerade användare får sina appar genom att trycka på följande paneler på skärmen Appar i företagsportalappen:

- **Alla appar** pekar på en lista över alla appar på fliken ALLA på [företagsportalens webbplats](https://portal.manage.microsoft.com).

- **Aktuella appar** omdirigerar användarna till fliken AKTUELLA på företagsportalens webbplats.

- **Kategorier** pekar på fliken KATEGORIER på företagsportalens webbplats.

![Skärmen Appar på företagsportalen för iOS](./media/end-user-apps-ios/ios-cp-app-main-apps-screen.png)

Mer information om hur man lägger till appar finns i [Så här lägger du till en app i Microsoft Intune](../apps/apps-add.md).

## <a name="see-also"></a>Se även

[Så får dina Android-användare sina appar](end-user-apps-android.md)

[Så får dina Windows-användare sina appar](end-user-apps-windows.md)
