---
title: "Lägga till appar i Microsoft Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: De här procedurerna hjälper dig att få dina appar till Intune, redo att tilldelas till användare och enheter. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 969ce8deae9142944f3481172277dc252baa5779
ms.openlocfilehash: a7838f57b2eb8bd36a875f7b5b001b12eafcbf8d

---

# <a name="how-to-add-an-app"></a>Lägga till en app 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Innan du kan hantera och tilldela appar för dina användare, måste du lägga till dem i Intune. Intune stöder en stor variation av olika apptyper och alternativen kan vara olika för varje typ.

Intune stöder tillägg och tilldelning av följande apptyper:

![Apptyper som stöds av Intune](./media/app-types.png)

Följande plattformar stöds. Klicka på ett av avsnitten för mer information om hur du lägger till varje apptyp.

- [Verksamhetsspecifika appar för Android](/intune-azure/manage-apps/android-lob-app)
- [Android Store-appar](/intune-azure/manage-apps/android-store-app)
- [Verksamhetsspecifika appar för iOS](/intune-azure/manage-apps/ios-lob-app)
- [iOS Store-appar](/intune-azure/manage-apps/ios-store-app)
- [Webbappar (för alla plattformar)](/intune-azure/manage-apps/web-app)
- [Windows Phone 8.1 Store-appar](/intune-azure/manage-apps/windows-phone-8-1-store-app)
- [Windows Store-appar](/intune-azure/manage-apps/windows-store-app)

> [!NOTE]
> När du lägger till och distribuerar en app från en butik måste slutanvändare ha ett konto med den butiken för att kunna installera appen.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Skapa och redigera kategorier för appar 

Appkategorier kan användas för att sortera appar så att slutanvändarna lättare kan hitta dem i företagsportalen. Du kan tilldela en eller flera kategorier till en app, till exempel **Utvecklarprogram** eller **Kommunikationsappar**. När du lägger till en app i Intune ges möjlighet att välja den kategori som du önskar. Använd de plattformsspecifika avsnitten för att lägga till en app och tilldela kategorier. Använd följande procedur för att skapa och redigera dina egna kategorier: 

1. Logga in på Azure-portalen. 
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**. 
3. Välj **Hantera appar** på **Intune**-bladet. 
4. Välj **Installation** > **Appkategorier** i arbetsbelastningen **Mobilappar**. 
5. På bladet **Appkategorier** visas en lista över aktuella kategorier. Välj en av följande åtgärder: 
    - **Skapa en kategori** – Ange ett namn för den nya kategorin på bladet **Skapa kategori**. Namn kan bara anges på ett språk och översätts inte av Intune. Klicka på **Skapa** när du är klar.
    - **Redigera en kategori** – För valfri kategori i listan, välj ”**... **”. På bladet **Egenskaper** kan du ange ett nytt namn för kategorin eller ta bort kategorin. --->






<!--HONumber=Feb17_HO1-->


