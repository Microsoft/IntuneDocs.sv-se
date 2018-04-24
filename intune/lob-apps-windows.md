---
title: Lägga till verksamhetsspecifika Windows-appar i Microsoft Intune
titlesuffix: ''
description: Läs om hur du lägger till verksamhetsspecifika Windows-appar (LOB) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: aa11c29a50006053b6e9b52516a595683d6f4cfd
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Så här lägger du till branschspecifika Windows-appar i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

En verksamhetsspecifik app (LOB) är en app som du lägger till från en appinstallationsfil. Dessa typer av appar är vanligen skrivna internt. I följande steg finns riktlinjer som hjälper dig att lägga till en Windows LOB-app i Microsoft Intune.

## <a name="step-1---specify-the-software-setup-file"></a>Steg 1 – Ange platsen för programinstallationsfilen

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Mobilappar** i **Intune**-fönstret.
4. Välj **Hantera** > **appar** i arbetsbelastningen **Mobilappar**.
5. Välj **Lägg till** ovanför applistan.
6. I fönstret **Lägg till app** väljer du **Verksamhetsspecifik app**.

## <a name="step-2---configure-the-app-package-file"></a>Steg 2 – Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du filen **Appaket**.
2. I fönstret **Appaketfil** väljer du bläddringsknappen och väljer en Windows-installationsfil med filnamnstillägget **.msi**, **.appx** eller **.appxbundle**.
3. Välj **OK** när du är klar.


## <a name="step-3---configure-app-information"></a>Steg 3 – Konfigurera appinformation

1. I fönstret **Lägg till app** väljer du filen **Appaket**.
2. I fönstret **Appinformation** konfigurerar du följande information (vissa värden i det här fönstret kanske har fyllts i automatiskt):
    - **Namn** – Ange namnet på appen så som det visas på företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning** – Ange en beskrivning för appen. Beskrivningen visas för användarna på företagsportalen.
    - **Utgivare** – Ange namnet på appens utgivare.
    - **Ignorera appversion** – Ange **Ja** om appen uppdateras automatiskt av apputvecklaren.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Om du kategoriserar apparna blir det enklare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Visa appen på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Om du vill anger du webbadressen till en webbplats som innehåller information om appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL** – Om du vill anger du webbadressen till en webbplats som innehåller sekretessinformation för appen. Webbadressen visas för användarna på företagsportalen.
    - **Kommandoradsargument** – Om du vill anger du kommandoradsargument som du vill tillämpa på MSI-filen när den körs, t.ex. **/q**.
    - **Utvecklare (valfritt)** – Ange apputvecklarens namn.
    - **Ägare (valfritt)** – Ange ett namn på appägaren, t.ex. **Personalavdelningen**.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp** – Ladda upp en ikon som är associerad med appen. Ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4---finish-up"></a>Steg 4 – Slutför

1. I fönstret **Lägg till app** kontrollerar du att appinformationen är korrekt konfigurerad.
2. Välj **Lägg till** för att överföra appen till Intune.

## <a name="step-5---update-a-line-of-business-app"></a>Steg 5 – Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configuring-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurera att en MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen

Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen. Vissa MSI-appar som baseras på installationsprogram uppdateras automatiskt av apputvecklaren. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignorera appversion** på bladet **Appinformation**. När den här inställningen växlas till **Ja** kommer Microsoft Intune inte använda appversionen som är installerad på Windows-klienten. Den här funktionen är användbar för att undvika konkurrenstillstånd. Den här typen av konkurrenstillstånd kan exempelvis uppstå när appen uppdateras automatiskt av apputvecklaren och även uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket kan skapa en konflikt.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](introduction-device-app-lifecycles.md)
