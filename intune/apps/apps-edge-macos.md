---
title: Lägga till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune
titleSuffix: ''
description: Lär dig hur du lägger till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6726f731fba5bc41893f999ac627bff9a8aca1e
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754838"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Lägga till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune

Innan du kan distribuera, konfigurera, övervaka eller skydda appar måste du lägga till dem till Intune. En av de tillgängliga [apptyperna](~/apps/apps-add.md#app-types-in-microsoft-intune) är Microsoft Edge *version 77 och senare*. Genom att välja den här apptypen i Intune kan du tilldela och installera Microsoft Edge *version 77 och senare* till enheter som du hanterar och som kör macOS. Den här apptypen gör det enkelt för dig att tilldela Microsoft Edge till macOS-enheter utan att du behöver använda macOS-verktyget för appomslutning. För att hålla apparna säkrare och uppdaterade levereras den här appen med Microsoft AutoUpdater (MAU).

> [!IMPORTANT]
> Den här apptypen är i **offentlig förhandsversion** och erbjuder utvecklar- och betakanaler för macOS. Distributionen är bara på engelska (EN), men slutanvändarna kan ändra visningsspråket i webbläsaren under **Inställningar** > **Språk**. 

> [!NOTE]
> Microsoft Edge *version 77 och senare* är även tillgängligt för Windows 10.

## <a name="prerequisites"></a>Krav
- macOS-enheten måste köra macOS 10.12 eller senare innan Microsoft Edge installeras.

## <a name="add-microsoft-edge-to-intune"></a>Lägga till Microsoft Edge till Intune
Du kan lägga till Microsoft Edge version 77 och senare till Intune med hjälp av följande steg:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I fönstret **Intune** väljer du **Klientappar** > **Appar** > **Lägg till**.
3. I listan **Apptyp**, under **Microsoft Edge, version 77 och senare**, väljer du **macOS**.

## <a name="configure-app-information"></a>Konfigurera appinformation
I det här steget anger du information om den här appdistributionen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.

1. Klicka på **Appinformation** för att visa bladet **Appinformation**.
2. På bladet **Appinformation** anger du information om den här appdistributionen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.
    - **Namn**: Ange namnet på appen så som det ska visas i företagsportalen. Kontrollera att alla namn är unika. Om samma appnamn förekommer två gånger visas endast en av apparna för användarna på företagsportalen.
    - **Beskrivning**: Ange en beskrivning för appen. Du kan till exempel ange målanvändarna i beskrivningen.
    - **Utgivare**: Microsoft visas som utgivare.
    - **Kategori**: Välj en eller flera av de inbyggda appkategorierna, eller en kategori som du har skapat. Inställningen gör det enklare för användarna att hitta appen när de söker på företagsportalen.
    - **Visa denna som en aktuell app i företagsportalen**: Välj det här alternativet för att tydligt visa appen på företagsportalens huvudsida när användarna söker efter appar.
    - **Webbadress till information**: Du kan välja att ange en webbadress till en webbplats som innehåller information om den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Sekretesswebbadress**: Du kan välja att ange en webbadress till en webbplats som innehåller sekretessinformation för den här appen. Webbadressen visas för användarna på företagsportalen.
    - **Utvecklare**: Microsoft visas som utvecklare.
    - **Ägare**: Microsoft visas som ägare.
    - **Kommentarer**: Alternativt kanske du vill ange kommentarer till appen.
3. Välj **OK**.

## <a name="configure-microsoft-edge-settings"></a>Konfigurera Microsoft Edge-inställningar
I det här steget konfigurerar du installationsalternativ för appen.

1. På bladet **Lägg till app** väljer du **Appinställningar**.
2. På bladet **Appinställningar** är kanalen **Beta** automatiskt vald och kan inte ändras.
    - Kanalen **Beta** är den mest stabila Microsoft Edge-förhandsupplevelsen och det bästa valet för en fullständig pilotlansering i din organisation. Det sker större uppdateringar var sjätte vecka.

    > [!NOTE]
    > Microsoft Edge-webbläsarens logotyp visas med appen när användare söker på företagsportalen.
3.  Välj **OK**.

## <a name="select-scope-tags-optional"></a>Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Fullständig information om omfångstaggar finns i Använda RBAC och omfångstaggar för distribuerad IT.
1.  Välj **Omfång (taggar)**  > **Lägg till**.
2.  Använd rutan **Välj** för att söka efter omfångstaggar.
3.  Markera kryssrutan bredvid de omfångstaggar som du vill tilldela till den här appen.
4.  Klicka på **Välj** > **OK**.

## <a name="add-the-app"></a>Lägg till appen
När du har slutfört konfigurationen väljer du **Lägg till** från bladet **Lägg till app**. 

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

> [!NOTE]
> Apple tillhandahåller för närvarande inget sätt för Intune att avinstallera Microsoft Edge på macOS-enheter.

## <a name="next-steps"></a>Nästa steg
- Information om hur du konfigurerar Microsoft Edge på macOS-enheter finns i [Konfigurera Microsoft Edge på macOS-enheter](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar från grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](~/apps/apps-inc-exl-assignments.md).
- [Tilldela appar till grupper](~/apps/apps-deploy.md)

