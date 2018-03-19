---
title: Installera Office 365 i macOS-enheter med Microsoft Intune
titlesuffix: 
description: "Så här använder du Microsoft Intune för installera Office 365-appar på macOS-enheter."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Tilldela Office 365 till macOS-enheter med Microsoft Intune

Den här **Store-appen** gör det enkelt för dig att tilldela macOS-enheter till Office 365-appar. Den här apptypen låter dig installera Word, Excel, PowerPoint, Outlook och OneNote. De här apparna inkluderar även Microsoft AutoUpdater (MAU), för att hålla apparna säkrare och uppdaterade. Appar som du vill använda visas som en enda app i listan med appar i Intune-konsolen.


## <a name="before-you-start"></a>Innan du börjar

Innan du börjar lägga till Office 365 till macOS-enheter måste du förstå följande:

- Enheterna som du distribuerar dessa appar på måste köra macOS 10.10 eller senare.
- Intune har endast stöd för att lägga till Office-appar som ingår i Office 2016 för Mac-paket.
- Om några Office-program öppnas när Intune installerar appen kan slutanvändare förlora data från filer som inte sparats.

## <a name="create-and-configure-the-app-suite"></a>Skapa och konfigurera app-paketet

Lägg till Office 365 med hjälp av bladet **Appar**.
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
4. Välj **Appar** i avsnittet **Hantera** i arbetsbelastningen **Mobilappar**. 
5. Välj **Lägg till** för att visa bladet **Lägg till app**.
6. I listan **Apptyp** väljer du **macOS** i gruppen **Office 365-paket**.
7. Välj **Information om appsvit** för att ge information om appaketet. Den här informationen hjälper dig att identifiera appaketet i Intune och hjälper även användarna att hitta det i företagsportalappen.
8.  Ange följande information:
    - **Paketnamn** – Ange namnet på appaketet så som det visas på företagsportalen. Kontrollera att alla paketnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Paketbeskrivning** – Ange en beskrivning för appaketet.
    - **Utgivare** – Microsoft visas som utgivare.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Inställningen gör det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Den här inställningen visar appaketet på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** (valfritt) – Ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL** (valfritt) – Ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare** – Microsoft visas som utvecklare.
    - **Ägare** – Microsoft visas som ägare.
    - **Anteckningar** (valfritt) – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Logo** – Office 365-logotypen visas med appen när användare söker på företagsportalen.
9.  Klicka på **OK** på bladet **Appinformation**.
10. Klicka på **Lägg till** på bladet **Lägg till app**.
    Programsviten visas som en enda post i listan över appar.

## <a name="configure-app-assignments"></a>Konfigurera apptilldelningar

Konfigurera tilldelningarna för appaket i det här steget. 

1. Välj **Office 365**-appaketet i listan med appar för att visa översiktsbladet för **Office 365**.
2. Klicka på **Tilldelningar** på **Office 365**-bladet.
3. Klicka på **Lägg till grupp** för att lägga till en grupp när du vill använda appaketet. Bladet **Lägg till grupp** visas.
3. Ställ in **Tilldelningstyp** på **Obligatorisk**.
4. Tilldela programsvit till de grupper du väljer. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

    >[!Note]
    > För eventuella grupper som kräver Office 365-appaketet kan du inte avinstallera det via Microsoft Intune.

5. Välj **OK** på bladet **Tilldela**.
6. Välj **OK** på bladet **Lägg till grupp**.
7. Välj **Spara** för att genomföra dina tilldelningar.

## <a name="next-steps"></a>Nästa steg

- Mer information om att lägga till appar för Office 365 i en Windows 10-enhet, finns i [Tilldela Office 365 ProPlus 2016-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar till grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](apps-inc-exl-assignments.md).
