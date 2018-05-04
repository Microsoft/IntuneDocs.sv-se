---
title: Lägg till en verksamhetsspecifik app för Windows Phone i Microsoft Intune
titlesuffix: ''
description: Läs om att lägga till en verksamhetsspecifik Windows Phone-app till Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 25f71122fdcf932f0318923f44f3703700f48558
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Windows Phone i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till en verksamhetsspecifik app för Windows Phone i Microsoft Intune. En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange platsen för programinstallationsfilen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Mobilappar**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför listan över appar.
6. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en fil för installation av Windows Phone med tillägget **.xap**.
3. Välj **OK** när du är klar.


## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** konfigurerar du appinformationen. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Ignorera appversion**: Ange **Ja** om apputvecklaren uppdaterar appen automatiskt.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL**: Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas i företagsportalen.
    - **Sekretess-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas i företagsportalen.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Anteckningar**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4-finish-up"></a>Steg 4: Slutför

1. I fönstret **Lägg till app** kontrollerar du att informationen är rätt konfigurerad.
2. Välj **Lägg till** för att ladda upp appen till Intune.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md).
