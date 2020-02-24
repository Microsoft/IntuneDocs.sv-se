---
title: Lägg till inbyggda appar på mobila enheter med Microsoft Intune
titleSuffix: ''
description: Så här använder du Intune för att underlätta installation av inbyggda appar på mobila enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96cd4997029c15396db91e9866bbb387c20f1044
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414437"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Lägg till inbyggda appar i Microsoft Intune

Den *inbyggda* apptypen gör det enkelt att tilldela granskade och hanterade appar som till exempel Office 365-appar till iOS/iPadOS- och Android-enheter. Du kan tilldela specifika appar för den här apptypen, till exempel Excel, OneDrive, Outlook, Skype med mera. När du lagt till en app visas apptypen antingen som *Inbyggd iOS-app* eller *Inbyggd Android-app*. Du kan välja vilken av dessa appar du vill publicera till enhetsanvändare genom att använda den inbyggda apptypen.

I tidigare versioner av Intune-konsolen tillhandahöll Intune flera hanterade Office 365-appar som standard, till exempel Outlook och OneDrive. Apptyperna för dessa hanterade appar har taggats som *Hanterad iOS Store-app* eller *Hanterad Android-app*. Istället för att använda dessa apptyper, rekommenderar vi att du använder den inbyggda apptypen. Genom att använda den inbyggda apptypen får du extra flexibilitet för att redigera och ta bort Office 365-appar.

>[!NOTE]
>Standard-Office 365-appar som taggats som *Hanterad iOS Store* och *Hanterad Android-app* tas bort från listan över appar när alla tilldelningar har tagits bort.

## <a name="add-a-built-in-app"></a>Lägg till en inbyggd app

För att lägga till en inbyggd app till dina tillgängliga appar i Microsoft Intune, gör följande:
1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I rutan **Välj typ av app** väljer du **Inbyggd app** bland tillgängliga **typer av appar i Store**.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.
5. På sidan **Välj inbyggda appar** klickar du på **Välj app** för att välja de appar som du vill inkludera.
6. Välj de inbyggda appar som du vill inkludera. 
7. När du har valt apparna klickar du på **Välj** i fönstret **Välj inbyggda appar**.
8. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.
9. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).
10. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
11. Välj grupptilldelningar för appen. Mer information finns i [Lägga till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md). 
12. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. Granska värdena och inställningarna som du har angett för appen.
13. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

    **Översiktsbladet** för appen som du har skapat visas i applistan.

## <a name="configure-app-information"></a>Konfigurera appinformation

Du kan modifiera informationen om den inbyggda appen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.
1. Välj **Appar** > **Alla appar** och välj den inbyggda app som du vill ändra.  
   Ett fönster för den inbyggda appen visas.
2. Välj **Egenskaper**.
3. Välj **Redigera** bredvid **Appinformation**.
4. I fönstret **Appinformation** kan du ändra följande information:
    - **Namn**: Ange namnet på den inbyggda appen så som det visas i företagsportalen. Kontrollera att alla namn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. 
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Kategori**: Valfritt – välj en eller fler av de inbyggda appkategorierna. Om du konfigurerar det här alternativet blir det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appens ägare (till exempel *HR-avdelningen*).
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon**: Ladda upp en ikon som visas med appen när användare söker i företagsportalen.
5. Visa sidan **Granska och skapa** genom att klicka på **Granska och skapa**. Granska värdena och inställningarna som du har angett för appen.
13. När du är klar klickar du på **Spara** för att uppdatera appen i Intune.

    **Översiktsbladet** för appen som du har skapat visas i applistan.

## <a name="next-steps"></a>Nästa steg

- Nu kan du tilldela apparna till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).
