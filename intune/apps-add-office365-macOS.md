---
title: Installera Office 365 i macOS-enheter med Microsoft Intune
titlesuffix: ''
description: Så här använder du Microsoft Intune för installera Office 365-appar på macOS-enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4aa5cb24bc153839c6aac193f074128dd46a2e5f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185414"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Tilldela Office 365 till macOS-enheter med Microsoft Intune

Den här apptypen gör det enkelt för dig att tilldela macOS-enheter till Office 365 2016-appar. Genom att använda den här apptypen kan du installera Word, Excel, PowerPoint, Outlook och OneNote. För att hålla apparna säkrare och uppdaterade innehåller de här apparna även Microsoft AutoUpdater (MAU). Appar som du vill använda visas som en enda app i listan med appar i Intune-konsolen.


## <a name="before-you-start"></a>Innan du börjar

Innan du börjar lägga till Office 365 till macOS-enheter bör du förstå följande:

- Enheterna som du distribuerar dessa appar på måste köra macOS 10.10 eller senare.
- Intune har stöd för att lägga till Office-appar som ingår i Office 2016 för Mac-paket endast.
- Om alla Office-program är öppna när Intune installerar appen kan användare förlora data från filer som inte sparats.

## <a name="create-and-configure-the-app-suite"></a>Skapa och konfigurera app-paketet

Lägg till Office 365 från fönstret **Appar**.
1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Klientappar** i **Intune**-fönstret.
4. I arbetsbelastningsfönstret **Klientappar** väljer du **Appar** under **Hantera**. 
5. Välj **Lägg till**.
6. I listan **Apptyp** i gruppen **Office 365-paket** väljer du **macOS**.
7. Välj **Information om appsvit** för att få information om appsviten.  
    Den här informationen hjälper dig att identifiera appsviten i Intune och hjälper användarna att hitta appsviten det i företagsportalappen.
8. Ange följande information:
    - **Paketnamn**: Ange namnet på appsviten så som det visas på företagsportalen. Kontrollera att alla svitnamn du använder är unika. Om samma paketnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Svitbeskrivning**: Ange en beskrivning för appsviten.
    - **Utgivare**: Microsoft visas som utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Inställningen gör det enklare för användarna att hitta appaketet när de söker på företagsportalen.
    - **Visa den här som aktuell app på företagsportalen**: Välj det här alternativet för att visa appsviten på en framträdande plats på företagsportalens startsida när användarna söker efter appar.
    - **Informations-URL**: Du kan välja att ange webbadressen till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretess-URL**: Alternativt kan du ange webbadressen till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Microsoft visas som utvecklare.
    - **Ägare**: Microsoft visas som ägare.
    - **Anteckningar**: Alternativt kanske du vill ge kommentarer som du vill koppla till den här appen.
    - **Logo**: Office 365-logotypen visas med appen när användare söker på företagsportalen.
9. Välj **OK**.
10. I fönstret **Lägg till app** väljer du **Lägg till**.  
    Programsviten visas som en enda post i listan över appar.

## <a name="configure-app-assignments"></a>Konfigurera apptilldelningar

Konfigurera tilldelningarna för appaket i det här steget. 

1. I listan över appar, väljer du **Office 365**-appsvit för att visa översiktsfönstret för **Office 365**.
2. I fönstret **Office 365** väljer du **Tilldelningar**.
3. Om du vill lägga till en grupp som ska använda appsviten välj **Lägg till grupp**.  
    Fönstret **Lägg till grupp** visas.
4. Ställ in **Tilldelningstyp** på **Obligatorisk** eller **Tillgänglig**.
5. Tilldela programsviten till de grupper som du har valt. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Du kan inte avinstallera Office 365-appsviten via Intune.

5. I fönstret **Tilldela** väljer du **OK**.
6. I fönstret **Lägg till grupp** väljer du **OK**.
7. Välj **Spara** för att genomföra dina tilldelningar.

## <a name="next-steps"></a>Nästa steg

- Mer information om att lägga till appar för Office 365 i en Windows 10-enhet, finns i [Tilldela Office 365 ProPlus 2016-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar från grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](apps-inc-exl-assignments.md).
