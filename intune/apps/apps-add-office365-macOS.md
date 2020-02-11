---
title: Installera Office 365 i macOS-enheter med Microsoft Intune
titleSuffix: ''
description: Så här använder du Microsoft Intune för installera Office 365-appar på macOS-enheter.
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
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755365"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Tilldela Office 365 till macOS-enheter med Microsoft Intune

Den här apptypen gör det enkelt för dig att tilldela macOS-enheter till Office 365 2016-appar. Genom att använda den här apptypen kan du installera Word, Excel, PowerPoint, Outlook och OneNote. För att hålla apparna säkrare och uppdaterade innehåller de här apparna även Microsoft AutoUpdater (MAU). Appar som du vill använda visas som en enda app i listan med appar i Intune-konsolen.


## <a name="before-you-start"></a>Innan du börjar

Innan du börjar lägga till Office 365 till macOS-enheter bör du förstå följande:

- Enheterna som du distribuerar dessa appar på måste köra macOS 10.10 eller senare.
- Intune har stöd för att lägga till Office-appar som ingår i Office 2016 för Mac-paket endast.
- Om alla Office-program är öppna när Intune installerar appen kan användare förlora data från filer som inte sparats.

## <a name="select-the-office-365-suite-app-type"></a>Välj en app av Office 365-pakettyp

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. Välj **macOS** i avsnittet **Office 365-paket** i fönstret **Välj apptyp**.
4. Klicka på **Välj**. Stegen **Lägga till Office 365-paket** visas.

## <a name="step-1---app-suite-information"></a>Steg 1 – Information om appsvit

I det här steget anger du information om appaketet. Den här informationen hjälper dig att identifiera appsviten i Intune och hjälper användarna att hitta appsviten det i företagsportalappen.

1. På sidan **Information om appsvit** kan du bekräfta eller ändra standardvärdena:
    - **Namn på programsvit**: Ange namnet på appsviten så som det visas i företagsportalen. Kontrollera att alla svitnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning av programsvit**: Ange en beskrivning av appsviten. Exempelvis kan du visa de appar som ingår.
    - **Utgivare**: Microsoft visas som utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Inställningen gör det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appsviten på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Microsoft visas som utvecklare.
    - **Ägare**: Microsoft visas som ägare.
    - **Kommentarer**: Ange eventuella kommentarer som du vill koppla till den här appen.
    - **Logotyp**: Office 365-logotypen visas med appen när användarna söker på företagsportalen.
2. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.

## <a name="step-2---select-scope-tags-optional"></a>Steg 2 – Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

1. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appsviten. 
2. Klicka på **Nästa** för att visa sidan **Tilldelningar**.

## <a name="step-3---assignments"></a>Steg 3 – Tilldelningar

1. Välj **Obligatorisk**, **Tillgängligt för registrerade enheter**som grupptilldelning för appsviten. Mer information finns i [Lägg till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md) och [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Du kan inte avinstallera Office 365 för macOS-appsviten via Intune.

2. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. 

## <a name="step-4---review--create"></a>Steg 4 – Granska och skapa

1. Granska värdena och inställningarna som du har angett för appsviten.
2. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

    **Översiktsbladet** för Office 365 Windows 10-appsviten som du har skapat visas i applistan. Programsviten visas som en enda post i listan över appar.

## <a name="next-steps"></a>Nästa steg

- Mer information om att lägga till appar för Office 365 i en Windows 10-enhet, finns i [Tilldela Office 365 ProPlus 2016-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar från grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](apps-inc-exl-assignments.md).
