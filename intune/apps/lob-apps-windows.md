---
title: Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune
titleSuffix: ''
description: Läs om hur du lägger till verksamhetsspecifika Windows-appar (LOB) i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6df77d168bb8be3775c566f63833b46130515b36
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601584"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En verksamhetsspecifik app (LOB) är en app som du lägger till från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. I följande steg finns riktlinjer som hjälper dig att lägga till en Windows LOB-app i Microsoft Intune.

> [!IMPORTANT]
> När du distribuerar Win32-appar med hjälp av en installationsfil med tillägget *.msi* kan du överväga att använda [tillägget Intune-hantering](../apps/intune-management-extension.md). Om du blandar installationen av Win32-appar och verksamhetsspecifika appar under autopilotregistreringen, kan det hända att appen inte kan installeras.  

## <a name="step-1-specify-the-software-setup-file"></a>Steg 1: Ange programinstallationsfilen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Välj **Klientappar** i **Intune**-fönstret.
4. Välj **Hantera** > **Appar** i arbetsbelastningen **Klientappar**.
5. Välj **Lägg till** ovanför listan över appar.
6. I fönstret **Lägg till app** väljer du **Branschspecifik app**.

## <a name="step-2-configure-the-app-package-file"></a>Steg 2: Konfigurera appaketfilen

1. I fönstret **Lägg till app** väljer du **Appaketfilen**.
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en fil för Windows-installationen med tillägget **.msi**, **.appx** eller **.appxbundle**.

    > [!NOTE]
    > Filnamnstillägg för Windows-appar omfattar **.msi**, **.appx**, **.appxbundle**, **.msix** och **.msixbundle**.  

1. Välj **OK** när du är klar.


## <a name="step-3-configure-app-information"></a>Steg 3: Konfigurera appinformation

1. Välj **Appinformation** i fönstret **Lägg till app**.
2. Konfigurera följande information i fönstret **Appinformation**. Vissa värden i det här fönstret kan fyllas i automatiskt.
    - **Namn**: Ange namnet på appen så som det visas i företagsportalen. Kontrollera att alla appnamn du använder är unika. Om samma appnamn förekommer två gånger visas endast en av apparna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Beskrivningen visas i företagsportalen.
    - **Utgivare**: Ange namnet på appens utgivare.
    - **Ignorera appversion**: Ange **Ja** om apputvecklaren uppdaterar appen automatiskt. Det här alternativet gäller endast mobila .msi-appar.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller välj en kategori som du har skapat. Kategorier gör det enklare för användarna att hitta appen när de söker i företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Visa appen tydligt på huvudsidan för företagsportalen när användare söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om appen. Webbadressen visas i företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation om appen. Webbadressen visas i företagsportalen.
    - **Kommandoradsargument**: Alternativt kan du ange kommandoradsargument som du vill tillämpa på MSI-filen när den körs.  Ett exempel är **/q**. Ta inte med msiexec-kommandot eller argument, till exempel **/i** eller **/x**, eftersom de används automatiskt. Mer information finns i [Kommandoradsalternativ](https://docs.microsoft.com/windows/desktop/Msi/command-line-options). Om. MSI-filen behöver ytterligare kommandoradsalternativ kan du använda [Win32-apphantering](app-management.md).
    - **Utvecklare**: Alternativt kan du ange apputvecklarens namn.
    - **Ägare**: Alternativt kan du ange ett namn på appägaren. Ett exempel är **Personalavdelningen**.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Ladda upp en ikon som är associerad med appen. Den här ikonen visas tillsammans med appen när användarna söker på företagsportalen.
3. Välj **OK** när du är klar.

## <a name="step-4-finish-up"></a>Steg 4: Slutför

1. I fönstret **Lägg till app** kontrollerar du att appinformationen är rätt konfigurerad.
2. Välj **Lägg till** för att ladda upp appen till Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Steg 5: Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

   > [!NOTE]
   > För att Intune-tjänsten ska kunna distribuera en ny APPX-fil till enheten, måste du öka `Version` i AppxManifest.xml-filen i ditt APPX-paket.

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Konfigurera att en MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen

Du kan konfigurera att en känd MSI-mobilapp med automatisk uppdatering ignorerar versionskontrollen.

Vissa appar som baseras på MSI-installationsprogram uppdateras automatiskt av apputvecklaren eller någon annan uppdateringsmetod. För dessa automatiskt uppdaterade MSI-appar kan du konfigurera inställningen **Ignorera appversion** i fönstret **Appinformation**. När du växlar den här inställningen till **Ja** kommer Microsoft Intune inte använda appversionen som är installerad på Windows-klienten.

Den här funktionen är användbar för att undvika konkurrenstillstånd. Exempelvis kan ett konkurrenstillstånd inträffa när appen uppdateras automatiskt av apputvecklare och uppdateras av Intune. Båda två kan försöka framtvinga en version av appen på Windows-klienten, vilket skapar en konflikt.

## <a name="next-steps"></a>Nästa steg

- Den app som du har skapat visas i listan över appar. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Se [Övervaka appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Se [Översikt över applivscykeln i Microsoft Intune](app-lifecycle.md).
