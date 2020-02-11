---
title: Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune
titleSuffix: ''
description: Läs om hur du lägger till verksamhetsspecifika Windows-appar (LOB) i Microsoft Intune.
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
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3deb9f3c96a4c2c2de72b7016aca855f679bbd7
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755143"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Lägg till en verksamhetsspecifik app för Windows i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

En verksamhetsspecifik app (LOB) är en app som du lägger till från en appinstallationsfil. Den här typen av app skrivs vanligtvis inom företaget. I följande steg finns riktlinjer som hjälper dig att lägga till en Windows LOB-app i Microsoft Intune.

> [!IMPORTANT]
> När du distribuerar Win32-appar med hjälp av en installationsfil med tillägget *.msi* kan du överväga att använda [tillägget Intune-hantering](../apps/intune-management-extension.md). Om du blandar installationen av Win32-appar och verksamhetsspecifika appar under autopilotregistreringen, kan det hända att appen inte kan installeras.  

## <a name="select-the-app-type"></a>Välj typ av app

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I fönstret **Välj apptyp** väljer du **Branschspecifik app** under **Övriga** typer av appar.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.

## <a name="step-1---app-information"></a>Steg 1 – information om app

### <a name="select-the-app-package-file"></a>Välj appaketfilen

1. I fönstret **Lägg till app** klickar du på **Välj appaketfilen**. 
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en fil för Windows-installationen med tillägget **.msi**, **.appx** eller **.appxbundle**.
   Appens information visas.

    > [!NOTE]
    > Filnamnstillägg för Windows-appar omfattar **.msi**, **.appx**, **.appxbundle**, **.msix** och **.msixbundle**.  

3. När du är klar väljer du **OK** i fönstret **Appaketfil** för att lägga till appen.

### <a name="set-app-information"></a>Konfigurera appinformation

1. I fönstret **Appinformation** lägger du till information om appen. Beroende på vilken app väljer kan det hända att några av värdena i det här fönstret fylls i automatiskt.
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

## <a name="update-a-line-of-business-app"></a>Uppdatera en verksamhetsspecifik app

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

- Läs mer om Win32-appar. Se [Win32-apphantering](~/apps/apps-win32-app-management.md).
