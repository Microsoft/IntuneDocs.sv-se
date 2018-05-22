---
title: Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune
titlesuffix: ''
description: Läs om hur du lägger till en verksamhetsspecifik Windows-app i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f907272f74886612eba9b5b28118f298caa2f36d
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En verksamhetsspecifik app (LOB) är en app som du lägger till från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. I följande steg finns riktlinjer som hjälper dig att lägga till en Windows LOB-app i Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange platsen för programinstallationsfilen

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Enheter** i **Mobilappar**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför listan över appar.
6. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en fil för Windows-installationen med tillägget **.msi**, **.appx** eller **.appxbundle**.
3. Välj **OK** när du är klar.


## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. Konfigurera följande information i fönstret **Appinformation**. Vissa värden i det här fönstret kan fyllas i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Ignorera appversion**: Ange **Ja** om apputvecklaren uppdaterar appen automatiskt.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller information om appen. Webbadressen visas i företagsportalen.
    - **Sekretess-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller sekretessinformation för appen. Webbadressen visas i företagsportalen.
    - **Kommandoradsargument**: Alternativt kan du ange kommandoradsargument som du vill tillämpa på MSI-filen när den körs. Ett exempel är **/q**.
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Anteckningar**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4-finish-up"></a>Steg 4: Slutför

1. I fönstret **Lägg till app** kontrollerar du att appinformationen är rätt konfigurerad.
2. Välj **Lägg till** för att ladda upp appen till Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Steg 5: Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurera att en MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen

Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen. 

Vissa MSI-appar som baseras på installationsprogram uppdateras automatiskt av apputvecklaren. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignorera appversion** i fönstret **Appinformation**. När du växlar den här inställningen till **Ja** kommer Microsoft Intune inte använda appversionen som är installerad på Windows-klienten. 

Den här funktionen är användbar för att undvika konkurrenstillstånd. Exempelvis kan ett konkurrenstillstånd inträffa när appen uppdateras automatiskt av apputvecklare och uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket skapar en konflikt.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md).
