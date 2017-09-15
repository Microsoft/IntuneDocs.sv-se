---
title: "Så här lägger du till appar i Microsoft Intune"
titlesuffix: Azure portal
description: "De här procedurerna hjälper dig att få in dina appar i Intune så att de är redo att tilldelas till användare och enheter. \""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 108f789f16304498cf54387326d112353bf70aa2
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Så här lägger du till appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

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

Appkategorier kan användas för att sortera appar så att användarna lättare kan hitta dem i företagsportalen. Du kan tilldela en eller flera kategorier till en app, till exempel **Utvecklarprogram** eller **Kommunikationsappar**.
När du lägger till en app i Intune ges möjlighet att välja den kategori som du önskar. Använd de plattformsspecifika avsnitten för att lägga till en app och tilldela kategorier. Använd följande procedur för att skapa och redigera dina egna kategorier:

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Installation** > **Appkategorier** i arbetsbelastningen **Mobilappar**.
5. På bladet **Appkategorier** visas en lista över aktuella kategorier. Välj en av följande åtgärder:
    - **Skapa en kategori** – Ange ett namn för den nya kategorin på bladet **Skapa kategori**. Namn kan bara anges på ett språk och översätts inte av Intune. Klicka på **Skapa** när du är klar.
    - **Redigera en kategori** – För valfri kategori i listan, välj ”**... **”. På bladet **Egenskaper** kan du ange ett nytt namn för kategorin eller ta bort kategorin.


## <a name="apps-added-automatically-by-intune"></a>Appar som läggs till automatiskt av Intune

Tidigare innehöll Intune ett antal inbyggda appar för snabb tilldelning. Efter feedback från användarna har vi beslutat oss för att ta bort listan och dess inbyggda appar visas inte längre.
Om du har redan har tilldelat några inbyggda appar kommer dessa även i fortsättningen att finnas kvar i listan över appar. Du kan fortsätta att tilldela dessa appar vid behov.
I en senare version planerar vi att lägga till en enklare metod för att välja och tilldela inbyggda appar från Azure-portalen.

## <a name="next-steps"></a>Nästa steg

Välj något av följande avsnitt för att ta reda på hur du lägger till appar för varje Intune-plattform:

- [Android Store-appar](store-apps-android.md)
- [Android LOB-appar](lob-apps-android.md)
- [iOS Store-appar](store-apps-ios.md)
- [iOS LOB-appar](lob-apps-ios.md)
- [Webbappar (för alla plattformar)](web-app.md)
- [Windows Phone 8.1 Store-appar](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB-appar](lob-apps-windows-phone.md)
- [Windows Store-appar](store-apps-windows.md)
- [Windows LOB-appar](lob-apps-windows.md)
- [Office 365-appar för Windows 10](apps-add-office365.md)

