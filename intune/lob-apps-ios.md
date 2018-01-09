---
title: "Så här lägger du till branschspecifika iOS-appar i Intune"
titlesuffix: Azure portal
description: "Läs om att lägga till verksamhetsspecifika iOS-appar till Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 20a044ea6b517279a2546f62d05cc79e09dcdc5f
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-ios-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika iOS-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informationen i det här avsnittet hjälper dig att lägga till verksamhetskritiska iOS-appar i Intune.

>[!NOTE]
>Användare av iOS-enheter kan ta bort några av de inbyggda iOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj **Hantera appar** på **Intune**-bladet.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I bladet **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appaket** klickar du på knappen Bläddra och väljer en iOS-installationsfil med filnamnstillägget **.ipa**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. På bladet **Lägg till app** väljer du filen **Appaket**.
2. På bladet **Appinformation** lägger du till information för appen. Beroende på vilken app du har valt kan det hända att några av värdena i det här bladet har fyllts i automatiskt:
    - **Namn** – Ange namnet på appen som ska visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användare i företagsportalen.
    - **Beskrivning** – Ange en beskrivning av appen som ska visas för användare på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Minsta operativsystem** – Välj den minsta operativsystemversion som appen kan installeras på. Om appen tilldelas till en enhet med ett äldre operativsystem installeras den inte.
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

1. På bladet **Lägg till app** kontrollerar du att informationen för appen är korrekt.
2. Välj **Lägg till** för att överföra appen till Intune.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Steg 5 – Uppdatera en verksamhetsspecifik app

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]Obs: För att Intune-tjänsten ska kunna distribuera en ny IPA-fil till enheten, måste du öka CFBundleVersion-strängen i Info.plist-filen i ditt IPA-paket.

## <a name="next-steps"></a>Nästa steg

Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
