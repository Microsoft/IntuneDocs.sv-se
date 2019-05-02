---
title: Lägg till en verksamhetsspecifik app för Windows Phone i Microsoft Intune
titleSuffix: ''
description: Läs om hur du lägger till verksamhetsspecifika Windows Phone-appar (LOB) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3458570f617fb24fa2798c843ca4d7c69342472
ms.sourcegitcommit: 617bd653c34c1e6a4e2ad61811c5912f8dab775c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/10/2019
ms.locfileid: "59570656"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Windows Phone i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till en verksamhetsspecifik app för Windows Phone i Microsoft Intune. En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange programinstallationsfilen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. Välj **Hantera** > **Appar** i arbetsbelastningen **Klientappar**.
5. Välj **Lägg till** ovanför listan över appar.
6. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en fil för installation av Windows Phone med tillägget **.xap**.
3. Välj **OK** när du är klar.


## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** konfigurerar du appinformationen. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas i företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas i företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4-finish-up"></a>Steg 4: Slutför

1. I fönstret **Lägg till app** kontrollerar du att informationen är rätt konfigurerad.
2. Välj **Lägg till** för att ladda upp appen till Intune.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md).
