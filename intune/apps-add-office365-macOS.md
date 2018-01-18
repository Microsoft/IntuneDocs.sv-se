---
title: Installera Office 365 i macOS-enheter med Intune
titlesuffix: Azure portal
description: "Så här använder du Intune för att underlätta installation av Office 365-appar på macOS-enheter."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e0ad0b99a2c8a602b5e542530a1d437065461b2
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Tilldela Office 365 till macOS-enheter med Microsoft Intune

Den här apptypen gör det enkelt för dig att tilldela macOS-enheter till Office 365-appar. Den här nya apptypen låter dig installera Word, Excel, PowerPoint, Outlook och OneNote. De här apparna inkluderar även Microsoft AutoUpdater (MAU), för att hålla apparna säkrare och uppdaterade. Appar som du vill använda visas som en enda app i listan med appar i Intune-konsolen.


## <a name="before-you-start"></a>Innan du börjar

- Enheterna som du distribuerar dessa appar på måste köra macOS 10.10 eller senare.
- Intune har endast stöd för att lägga till Office-appar som ingår i Office 2016 för Mac-paket.
- Om några Office-program öppnas när Intune installerar appen kan slutanvändare förlora data från filer som inte sparats.


## <a name="get-started"></a>Kom igång
Lägg till Office 365 med hjälp av bladet **Appar**.
1.  Logga in på Azure-portalen.
2.  Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3.  Välj **Mobilappar** på **Intune**-bladet.
4.  Välj **Appar** i gruppen **Hantera** i arbetsbelastningen **Mobilappar**. Välj **Lägg till**.
5.  På bladet **Lägg till app** väljer du **Office 365** > **macOS**.
6.  Välj **Lägg till**.

## <a name="configure-the-app-suite"></a>Konfigurera app-paketet

Ange information om appaketet. Den här informationen hjälper dig att identifiera det i Intune och hjälper även användarna att hitta det i företagsportalappen.

1.  Välj **Appinformation** på bladet **Lägg till app**.
2.  Ange följande information:
    - **Paketnamn** – Ange namnet på appaketet så som det visas på företagsportalen. Kontrollera att alla paketnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Paketbeskrivning** – Ange en beskrivning för appaketet.
    - **Utgivare** – Microsoft visas som utgivare.
    - **Kategori** – Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Det blir det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen** – Det här visar appaketet på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL** – Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL (valfritt)** – Ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare** – Microsoft visas som utvecklare.
    - **Ägare** – Microsoft visas som ägare.
    - **Anteckningar** – Ge eventuella kommentarer som du vill koppla till den här appen.
    - **Ladda upp ikon** - Ladda upp en ikon som visas med appen när användare söker i företagsportalen.
3.  Välj **OK**. Programsviten visas som en enda post i listan över appar.

## <a name="configure-app-assignments"></a>Konfigurera apptilldelningar

Konfigurera tilldelningarna för appaket i det här steget. Observera att tillgänglig apptyp kommer snart.

1.  Välj appaket i listan över appar och välj **Tilldelningar**.
2.  Välj **Välj grupper**.
3.  Tilldela programsvit till de grupper du väljer. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](/intune/apps-deploy).
4.  För varje grupp, välj **Kräv installera**.
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. Välj **Spara** för att genomföra dina tilldelningar.

## <a name="next-steps"></a>Nästa steg

Mer information om att lägga till appar för Office 365 i en Windows 10-enhet, finns i [Tilldela Office 365 ProPlus 2016-appar till Windows 10-enheter med Microsoft Intune](/intune/apps-add-office365).
