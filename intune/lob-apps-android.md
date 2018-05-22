---
title: Lägg till en verksamhetsspecifik app för Android i Microsoft Intune
titlesuffix: ''
description: Läs mer om att lägga till en verksamhetsspecifik app för Android i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 22470356c921eea17e4d2b3d57f796fe51568ee1
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Android i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

> [!Note]
> Läs mer om verksamhetsspecifika appar från Google Play for Work-butiken i [Arbeta med en verksamhetsspecifik app från Google Play for Work-butiken](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store). 

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange platsen för programinstallationsfilen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Mobilappar**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför listan över appar.
6. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en installationsfil för Android med tillägget **.apk**.
3. Välj **OK** när du är klar.


## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** lägger du till information om appen. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange beskrivningen av appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Lägsta operativsystemversion**: Välj den lägsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
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

1. I fönstret **Lägg till app** kontrollerar du att informationen för appen är korrekt.
2. Välj **Lägg till** för att ladda upp appen till Intune.

Den app som du har skapat visas nu i listan över appar. Du kan tilldela appen till grupper som du väljer i listan. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Steg 5: Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> För att Intune-tjänsten ska kunna distribuera en ny APK-fil till enheten, måste du öka `android:versionCode` i AndroidManifest.xml-filen i ditt APK-paket.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md).
