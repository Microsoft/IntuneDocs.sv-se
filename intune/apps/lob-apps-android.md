---
title: Lägg till en verksamhetsspecifik app för Android i Microsoft Intune
description: Läs mer om att lägga till en verksamhetsspecifik Android-app i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 783079786d19c0a65d44af96f9a3be9e2e817fc0
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724795"
---
# <a name="add-an-android-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Android i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

> [!Note]
> Mer information om LOB-appar och Google Play Developer Console finns i [Hanterad privat Google Play-appublicering (LOB) med Google Developer Console](apps-add-android-for-work.md?#managed-google-play-private-lob-app-publishing-using-the-google-developer-console). 

> [!Note]
> Du hittar mer information om Android-enheter för arbete i [Lägg till Google Play för företag-appar till Android enterprise-enheter med Intune](apps-add-android-for-work.md). 

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange programinstallationsfilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Klientappar** i **Intune**-fönstret.
3. Välj **Hantera** > **Appar** i arbetsbelastningen **Klientappar**.
4. Välj **Lägg till** ovanför listan över appar.
5. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en installationsfil för Android med tillägget **.apk**.
3. Välj **OK** när du är klar.

## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** lägger du till information om appen. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange beskrivningen av appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Lägsta operativsystemversion**: Välj den lägsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
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

1. I fönstret **Lägg till app** kontrollerar du att informationen för appen är korrekt.
2. Välj **Lägg till** för att ladda upp appen till Intune.

Den app som du har skapat visas nu i listan över appar. Du kan tilldela appen till grupper som du väljer i listan. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="step-5-update-a-line-of-business-app"></a>Steg 5: Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Om **Kontrollera appar från externa källor** är aktiverad på Android-enheten kommer användaren att frågas innan uppdateringen installeras. Annars installeras uppdateringen automatiskt.

> [!Note]
> För att Intune-tjänsten ska kunna distribuera en ny APK-fil till enheten, måste du öka `android:versionCode` i AndroidManifest.xml-filen i ditt APK-paket.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](../fundamentals/device-lifecycle.md).
