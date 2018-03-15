---
title: "Komma igång med appar i Microsoft Intune"
titlesuffix: 
description: "Hitta och lägg till appar på enheter så att personalen kan arbeta effektivt."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Komma igång med att lägga till appar i Microsoft Intune

Innan du kan tilldela, övervaka, konfigurera eller skydda appar måste du lägga till dem till Intune. Intune stöder flera olika apptyper. De tillgängliga alternativen skiljer sig åt för varje apptyp.

I Intune kan du lägga till och tilldela följande apptyper i företagsenheter:
- **Appar från Store**: För enheter i vilka ytterligare mobilapphantering ska tillämpas på appar som är tillgängliga i App Store.
- **Appar som skrivits internt (verksamhetsspecifika)**: För att ladda upp en fil som sedan laddas ned till användarnas enheter.
- **Inbyggda appar**: För att tilldela granskade och hanterade appar som till exempel Office 365-appar till iOS- och Android-enheter. 
- **Appar på webben**: Intune skapar en genväg till webbappen på enhetens startskärm.

## <a name="how-do-i-assign-a-public-store-app"></a>Hur gör jag för att tilldela en offentlig butiksapp?

I följande exempel visas hur du lägger till en iOS-app i Microsoft Intune.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning + hantering**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Appar** under avsnittet **Hantera** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** till höger i fönstret **Appar**.
6. I listan **Apptyp** väljer du **iOS** under tillgängliga **Store-apptyper**.
6. Välj **Search the App Store** (Sök i App Store).
7. Välj först nationella inställningar på bladet **Search the App Store** (Sök i App Store).
8. Ange namn (eller en del av namnet) i sökrutan. Intune söker i butiken och returnerar en lista över relevanta resultat.
9. Välj önskad app i listan och klicka sedan på **Välj**.
10. Välj **Appinformation** om du vill konfigurera appinformationen.
11. (Valfritt) Lägg till ytterligare information som hjälp vid organisation av den här appen, t.ex. **Ägare**, **Anteckningar**, **Utvecklare** och en **sekretesswebbadress** (till företagets sekretesspolicy).
12. Markera **Ja** för att **visa appen som en aktuell app i företagsportalen**. 
13. Klicka på **OK** när du har lagt till all appinformation som behövs.
14. Klicka på **Lägg till** på bladet **Lägg till app**. Därmed dirigeras du till appens **översikt**. 

## <a name="next-steps"></a>Nästa steg

Nu när du har lagt till en app i Intune kan du ange vilka grupper av medarbetare som ska kunna lägga till appen på sina enheter.

- [Så här tilldelar du appar till grupper](apps-deploy.md)
- 
## <a name="learn-more"></a>Läs mer

* [Vad är apphantering med Intune?](app-management.md)
* [Översikt över appens livscykel](app-lifecycle.md)
* [Vad är appskyddsprinciper?](app-protection-policy.md)
