---
title: Lägga till verksamhetsspecifika appar för iOS i Microsoft Intune
titlesuffix: ''
description: Läs mer om att lägga till verksamhetsspecifika appar för iOS i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7de6c995108bff3b1571b281df2745629c7f9741
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika iOS-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till verksamhetsspecifika appar för iOS i Microsoft Intune.

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du **Verksamhetsspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfil**.
2. I fönstret **Appaketfil** klickar du på knappen Bläddra och väljer en iOS-installationsfil med filnamnstillägget **.ipa**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. I fönstret **Appinformation** lägger du till information om appen. Beroende på vilken app du har valt kan det hända att några av värdena i det här fönstret har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen som ska visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
    - **Ignorera appversion** – Ange **Ja** om appen uppdateras automatiskt av apputvecklaren.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det gör det lättare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp** – Ladda upp en ikon som är associerad med appen. Den här ikonen visas med appen när användare söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4---finish-up"></a>Steg 4 – Slutför

1. I fönstret **Lägg till app** kontrollerar du att informationen för appen är korrekt.
2. Välj **Lägg till** för att överföra appen till Intune.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Steg 5 – Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]  

> [!NOTE]
> För att Intune-tjänsten ska kunna distribuera en ny IPA-fil till enheten, måste du öka *CFBundleVersion*-strängen i *Info.plist*-filen i ditt IPA-paket.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
