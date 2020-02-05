---
title: Lägga till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune
titleSuffix: ''
description: Lär dig hur du lägger till Microsoft Edge till macOS-enheter med hjälp av Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
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
ms.openlocfilehash: 6ebcb81cd0f186a3fd23e0701d12ea871eab129a
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912581"
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

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I listan **Apptyp**, under **Microsoft Edge, version 77 och senare**, väljer du **macOS**.

## <a name="configure-app-information"></a>Konfigurera appinformation
I det här steget anger du information om den här appdistributionen. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.

1. Visa fönstret **Appinformation** genom att klicka på **Appinformation**.
2. Ange information om den här appdistributionen i fönstret **Appinformation**. Den här informationen hjälper dig att identifiera appen i Intune och hjälper användarna att hitta appen i företagsportalen.
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

1. Välj **Appinställningar** i fönstret **Lägg till app**.
2. Bestäm vilken Edge-kanal du ska distribuera appen från genom att gå till fönstret **Appinställningar** och välja **Stabil**, **Beta** eller **Dev** i listan **Kanal**.

    - Kanalen **Stabil** är den rekommenderade kanalen för bredare distributioner i företagsmiljöer. Den uppdateras var sjätte vecka, och varje utgåva innehåller förbättringar från betakanalen.
    - Kanalen **Beta** är den mest stabila Microsoft Edge-förhandsupplevelsen och det bästa valet för en fullständig pilotlansering i din organisation. Större uppdateringar sker var sjätte vecka, och i varje ny version ingår lärdomar och förbättringar från Dev-kanalen.
    - **Dev**-kanalen är redo för företagsfeedback för Windows, Windows Server och macOS. Den uppdateras varje vecka och innehåller de senaste förbättringarna och korrigeringarna.

    > [!NOTE]
    > Microsoft Edge-webbläsarens logotyp visas med appen när användare söker på företagsportalen.

3.  Välj **OK**.

## <a name="select-scope-tags-optional"></a>Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Fullständig information om omfångstaggar finns i Använda RBAC och omfångstaggar för distribuerad IT.
1.  Välj **Omfång (taggar)** > **Lägg till**.
2.  Använd rutan **Välj** för att söka efter omfångstaggar.
3.  Markera kryssrutan bredvid de omfångstaggar som du vill tilldela till den här appen.
4.  Klicka på **Välj** > **OK**.

## <a name="add-the-app"></a>Lägg till appen
När du har slutfört konfigurationen väljer du **Lägg till** i fönstret **Lägg till app**. 

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

> [!NOTE]
> Apple tillhandahåller för närvarande inget sätt för Intune att avinstallera Microsoft Edge på macOS-enheter.

## <a name="next-steps"></a>Nästa steg
- Information om hur du konfigurerar Microsoft Edge på macOS-enheter finns i [Konfigurera Microsoft Edge på macOS-enheter](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar från grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](~/apps/apps-inc-exl-assignments.md).
- [Tilldela appar till grupper](~/apps/apps-deploy.md)

