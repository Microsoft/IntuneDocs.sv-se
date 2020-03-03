---
title: Lägga till Microsoft Defender Avancerat skydd på macOS-enheter med Microsoft Intune
titleSuffix: ''
description: Läs om hur du lägger till Microsoft Defender Avancerat skydd på macOS-enheter med Microsoft Intune.
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
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569566"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Lägga till Microsoft Defender Avancerat skydd på macOS-enheter med Microsoft Intune

Innan du kan distribuera, konfigurera, övervaka eller skydda appar måste du lägga till dem till Intune. En av de tillgängliga [apptyperna](~/apps/apps-add.md#app-types-in-microsoft-intune) är Microsoft Defender Avancerat skydd (ATP). Genom att välja den här apptypen i Intune kan du tilldela och installera Microsoft Defender ATP till enheter som du hanterar och som kör macOS. Den här apptypen gör det enkelt för dig att tilldela Microsoft Defender ATP till macOS-enheter utan att du behöver använda macOS-verktyget för appomslutning. För att hålla apparna säkrare och uppdaterade levereras den här appen med Microsoft AutoUpdater (MAU).

## <a name="prerequisites"></a>Krav
- MacOS-enheten måste köra macOS 10.13 eller senare.
- MacOS-enheten måste ha minst 650 MB ledigt diskutrymme.
- Distribuera kerneltillägg i Intune. Mer information finns i [Lägg till macOS kernel-tillägg i Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> Kerneltillägget kan bara godkännas automatiskt om det finns på enheten innan appen Microsoft Defender ATP installeras. Annars visas ett meddelande om att "systemtillägg blockeras" på Mac-datorn och användarna måste godkänna tillägget genom att gå till **Säkerhetsinställningar** eller **Systeminställningar** > **Säkerhet och integritet** och sedan välja **Tillåt**. Mer information finns i [Felsöka problem med kerneltillägg i Microsoft Defender ATP för Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Lägga till Microsoft Defender ATP i Intune
Du kan lägga till Microsoft Defender ATP och senare i Intune med hjälp av följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I listan **Apptyp**, under **Microsoft Defender ATP**, väljer du **macOS**.

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

## <a name="select-scope-tags-optional"></a>Välj omfångstaggar (valfritt)
Du kan använda omfångstaggar för att bestämma vem som kan se klientappsinformation i Intune. Fullständig information om omfångstaggar finns i Använda RBAC och omfångstaggar för distribuerad IT.
1.  Välj **Omfång (taggar)**  > **Lägg till**.
2.  Använd rutan **Välj** för att söka efter omfångstaggar.
3.  Markera kryssrutan bredvid de omfångstaggar som du vill tilldela till den här appen.
4.  Klicka på **Välj** > **OK**.

## <a name="add-the-app"></a>Lägg till appen
När du har slutfört konfigurationen väljer du **Lägg till** i fönstret **Lägg till app**. 

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

> [!NOTE]
> Apple tillhandahåller för närvarande inget sätt för Intune att avinstallera Microsoft Defender ATP på macOS-enheter.

## <a name="next-steps"></a>Nästa steg
- Information om hur du konfigurerar Microsoft Defender ATP på macOS-enheter finns i [Konfigurera Microsoft Defender ATP på macOS-enheter](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Om du vill veta mer om att inkludera och exkludera apptilldelningar från grupper med användare kan du läsa [Inkludera och exkludera apptilldelningar](~/apps/apps-inc-exl-assignments.md).
- [Tilldela appar till grupper](~/apps/apps-deploy.md)

