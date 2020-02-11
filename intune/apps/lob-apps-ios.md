---
title: Lägg till en verksamhetsspecifik app för iOS i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till en verksamhetsspecifik iOS-app i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b7c0a7dfa4337983c12ada2d0f415c771bd0548
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755195"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för iOS i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till en verksamhetsspecifik app för iOS i Microsoft Intune. En verksamhetsspecifik app är en app som du lägger till i Intune från en IPA-appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. Du måste först gå med i iOS Developer Enterprise-programmet. Mer information om hur du gör detta finns på [Apples webbplats](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna såsom Stocks och Maps. Du kan inte använda Intune för att distribuera om dessa appar. Om användarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.
>
>iOS LOB-appar har en maximal storleksgräns på 4 GB per app.

## <a name="select-the-app-type"></a>Välj apptyp

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **Branschspecifik app** under **Övriga** apptyper i fönstret **Välj apptyp**.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.

## <a name="step-1---app-information"></a>Steg 1 – Appinformation

### <a name="select-the-app-package-file"></a>Välj appaketfilen

1. Klicka på **Välj appaketfil** fönstret **Lägg till app**. 
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en installationsfil för iOS med tillägget **.ipa**.
   Appinformationen visas.
3. När du är klar väljer du **OK** i fönstret **Appaketfil** för att lägga till appen.

### <a name="set-app-information"></a>Konfigurera appinformation

1. Lägg till information om appen i fönstret **Appinformation**. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
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
2. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.

## <a name="step-2---select-scope-tags-optional"></a>Steg 2 – Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

1. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. 
2. Klicka på **Nästa** för att visa sidan **Tilldelningar**.

## <a name="step-3---assignments"></a>Steg 3 – Tilldelningar

1. Välj **Obligatorisk**, **Tillgängligt för registrerade enheter** eller **Avinstallera** som grupptilldelning för appen. Mer information finns i [Lägg till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md) och [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).
2. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. 

## <a name="step-4---review--create"></a>Steg 4 – Granska och skapa

1. Granska värdena och inställningarna som du har angett för appen.
2. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

    Bladet **Översikt** för den branschspecifika appen visas.

Den app som du har skapat visas nu i listan över appar. Du kan tilldela appar till grupper som du väljer i listan. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

> [!NOTE]
> Etableringsprofiler för iOS LOB-appar visar ett meddelande 30 dagar innan de upphör att gälla.

## <a name="step-5-update-a-line-of-business-app"></a>Steg 5: Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

Uppdateringen av verksamhetsspecifika appar kommer att installeras automatiskt.

> [!NOTE]
> För att Intune-tjänsten ska kunna distribuera en ny IPA-fil till enheten, måste du öka `CFBundleVersion`-strängen i Info.plist-filen i ditt IPA-paket.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](../fundamentals/device-lifecycle.md).
