---
title: "Så här lägger du till verksamhetsspecifika appar för Android i Microsoft Intune"
titlesuffix: 
description: "Läs mer om att lägga till verksamhetsspecifika appar för Android i Microsoft Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3f336fb295dba396dad3a399aafc17435edb70b3
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Android-appar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

En verksamhetsspecifik app är en app som du lägger till i Intune från en appinstallationsfil. Dessa typer av appar är vanligen skrivna internt. Intune installerar den verksamhetsspecifika appen på användarens enhet. 

> [!Note]
> Läs mer om verksamhetsspecifika appar från Google Play for Work-butiken i [Arbeta med en verksamhetsspecifik app från Google Play for Work-butiken](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store). 

## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du **Verksamhetsspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfil**.
2. I fönstret **Appaketfil** väljer du knappen Bläddra. Välj sedan en Android-installationsfil med filnamnstillägget **.apk**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. I fönstret **Lägg till app** väljer du filen **Appaket**.
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

1. I fönstret **Lägg till app** kontrollerar du appinformationen.
2. Välj **Lägg till** för att överföra appen till Intune.

Den app som du har skapat visas i listan över appar där du kan välja att tilldela den till olika grupper. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Steg 5 – Uppdatera en verksamhetsspecifik app

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> För att Intune-tjänsten ska kunna distribuera en ny APK-fil till enheten, måste du öka android:versionCode-strängen i AndroidManifest.xml-filen i ditt APK-paket.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
