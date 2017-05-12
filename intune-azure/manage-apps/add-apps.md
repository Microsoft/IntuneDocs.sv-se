---
title: "Så här lägger du till appar i Microsoft Intune | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: De här procedurerna hjälper dig att få dina appar till Intune, redo att tilldelas till användare och enheter. "
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 529a3e91e1f86129de77df0529f48a42f86a6521
ms.openlocfilehash: 69ae0926631edc00cc2dc12be559d366e1623140
ms.contentlocale: sv-se
ms.lasthandoff: 05/11/2017

---

# <a name="how-to-add-an-app-to-microsoft-intune"></a>Så här lägger du till appar i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Innan du kan hantera och tilldela appar för dina användare, måste du lägga till dem i Intune. Intune stöder en stor variation av olika apptyper och alternativen kan vara olika för varje typ.

I Intune kan du lägga till och tilldela följande apptyper:

![Apptyper som stöds av Intune](./media/app-types.png)

Följande plattformar stöds.

- Android Store-appar
- Verksamhetsspecifika appar för Android
- iOS Store-appar
- Verksamhetsspecifika appar för iOS
- Webbappar
- Windows Phone 8.1 Store-appar
- Verksamhetsspecifika appar för Windows Phone (.xap-filer)
- Windows Store-appar
- Verksamhetsspecifika appar för Windows (endast .xap-filer)

>[!TIP]
> Verksamhetsspecifika appar (eller LOB) är sådana som du inte installerar från en appbutik utan installerar från appens installationsfil. Till exempel om du vill installera en LOB-app för iOS lägger du till en arkivfil för appen (med filnamnstillägget .ipa). Detta är vanligen appar som du har skrivit internt.

## <a name="before-you-start"></a>Innan du börjar

Tänk på följande innan du börjar lägga till och tilldela appar.

- När du lägger till och tilldelar en app från en butik måste slutanvändare ha ett konto med den butiken för att kunna installera appen.
- Vissa appar eller objekt som du tilldelar kan vara beroende av inbyggda iOS-appar. Om du till exempel tilldelar en bok från iOS Store måste appen iBooks finnas på enheten. Om du har tagit bort den inbyggda iBooks-appen, kan du inte använda Intune för att återinföra den.

## <a name="cloud-storage-space"></a>Molnlagringsutrymme
Alla appar som du skapar med installationstypen Programinstallation (till exempel en verksamhetsspecifik app) måste paketeras och överföras till Microsoft Intunes molnlagring. En utvärderingsprenumeration på Intune inkluderar 2 GB molnbaserad lagring som används för att lagra hanterade appar och uppdateringar. 20 GB lagringsutrymme ingår i den fullständiga prenumerationen.

Du kan köpa ytterligare lagringsutrymme för Intune med din ursprungliga köpmetod.  Om du betalade via faktura eller med kreditkort besöker du [prenumerationshanteringsportalen](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Annars kontaktar du din partner eller säljrepresentant.

Krav för lagringsutrymme i molnet:

-   Alla appinstallationsfiler måste finnas i samma mapp.
-   Den maximala filstorleken för en fil som du överför är 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Skapa och redigera kategorier för appar

Appkategorier kan användas för att sortera appar så att slutanvändarna lättare kan hitta dem i företagsportalen. Du kan tilldela en eller flera kategorier till en app, till exempel **Utvecklarprogram** eller **Kommunikationsappar**.
När du lägger till en app i Intune ges möjlighet att välja den kategori som du önskar. Använd de plattformsspecifika avsnitten för att lägga till en app och tilldela kategorier. Använd följande procedur för att skapa och redigera dina egna kategorier:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Installation** > **Appkategorier** i arbetsbelastningen **Mobilappar**.
5. På bladet **Appkategorier** visas en lista över aktuella kategorier. Välj en av följande åtgärder:
    - **Skapa en kategori** – Ange ett namn för den nya kategorin på bladet **Skapa kategori**. Namn kan bara anges på ett språk och översätts inte av Intune. Klicka på **Skapa** när du är klar.
    - **Redigera en kategori** – För valfri kategori i listan, välj ”**...** ”. På bladet **Egenskaper** kan du ange ett nytt namn för kategorin eller ta bort kategorin.


## <a name="apps-added-automatically-by-intune"></a>Appar som läggs till automatiskt av Intune

Följande appar, som publicerats av Microsoft, är inbyggda i Intune och klara att tilldela:

|||
|-|-|
|Namn|Plattform|Typ av app|
|Azure Information Protection|Android|Hanterad Google Play-app|
|Dynamics CRM för telefoner|Android|Hanterad Google Play-app|
|Dynamics CRM för surfplattor|Android|Hanterad Google Play-app|
|Excel|iOS|Hanterad iOS Store-app|
|Excel|Android|Hanterad Google Play-app|
|Hanterad webbläsare|Android|Hanterad Google Play-app|
|Hanterad webbläsare|iOS|Hanterad iOS Store-app|
|Microsoft Dynamics CRM för telefoner|iOS|Hanterad iOS Store-app|
|Microsoft Dynamics CRM för surfplattor|iOS|Hanterad iOS Store-app|
|Microsoft Power BI|iOS|Hanterad iOS Store-app|
|Microsoft Power BI|Android|Hanterad Google Play-app|
|Microsoft SharePoint|iOS|Hanterad iOS Store-app|
|Microsoft SharePoint|Android|Hanterad Google Play-app|
|Microsoft Teams|Android|Hanterad Google Play-app|
|Microsoft Teams|iOS|Hanterad iOS Store-app|
|OneDrive|iOS|Hanterad iOS Store-app|
|OneDrive|Android|Hanterad Google Play-app|
|OneNote|iOS|Hanterad iOS Store-app|
|Outlook|Android|Hanterad Google Play-app|
|Outlook|iOS|Hanterad iOS Store-app|
|Outlook Groups|Android|Hanterad Google Play-app|
|Outlook Groups|iOS|Hanterad iOS Store-app|
|PowerPoint|iOS|Hanterad iOS Store-app|

## <a name="next-steps"></a>Nästa steg

Välj något av följande avsnitt för att ta reda på hur du lägger till appar för varje Intune-plattform:

- [Android Store-appar](android-store-app.md)
- [Android LOB-appar](android-lob-app.md)
- [iOS Store-appar](ios-store-app.md)
- [iOS LOB-appar](ios-lob-app.md)
- [Webbappar (för alla plattformar)](web-app.md)
- [Windows Phone 8.1 Store-appar](windows-phone-8-1-store-app.md)
- [Windows Phone LOB-appar](windows-phone-line-of-business-app.md)
- [Windows Store-appar](windows-store-app.md)
- [Windows LOB-appar](windows-line-of-business-app.md)

