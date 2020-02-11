---
title: Lägga till verksamhetsspecifika appar för macOS i Microsoft Intune
titleSuffix: ''
description: Läs mer om att lägga till verksamhetsspecifika appar för macOS i Microsoft Intune.
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755178"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>Lägga till verksamhetsspecifika appar för macOS i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Informationen i den här artikeln visar hur du lägger till verksamhetsspecifika appar för macOS i Microsoft Intune. Du måste hämta ett externt verktyg för att förbearbeta dina *.pkg*-filer innan du kan ladda upp din verksamhetsspecifika fil till Microsoft Intune. Förbearbetningen av dina *.pkg*-filer måste ske på en macOS-enhet.

> [!NOTE]
> Från och med lanseringen av macOS Catalina 10.15 bör du kontrollera att dina LOB-appar för macOS har attesterats innan du lägger till dem i Intune. Om utvecklarna till LOB-apparna inte har attesterat sina appar, kommer apparna inte att kunna köras på användarnas macOS-enheter. Mer information om hur du kontrollerar om en app är attesterad finns [Attestera dina macOS-appar inför lanseringen av macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579).

> [!NOTE]
> Användare av macOS-enheter kan ta bort några av de inbyggda macOS-apparna som Aktier och Kartor, men du kan inte använda Intune för att distribuera dessa appar igen. Om slutanvändarna tar bort dessa appar måste de gå till App Store och installera om dem manuellt.

## <a name="before-your-start"></a>Innan du börjar

Du måste hämta ett externt verktyg, markera det hämtade verktyget som en körbar fil och förbearbeta dina *.pkg*-filer med verktyget innan du kan ladda upp din verksamhetsspecifika fil till Microsoft Intune. Förbearbetningen av dina *.pkg*-filer måste ske på en macOS-enhet. Använd Intune App Wrapping-verktyget för Mac för att aktivera Mac-appar som ska hanteras av Microsoft Intune.

> [!IMPORTANT]
> *.pkg*-filen måste signeras med hjälp av certifikatet "Developer ID Installer" och hämtas från ett Apple Developer-konto. Endast *.pkg*-filer kan användas för att överföra verksamhetsspecifika macOS-appar till Microsoft Intune. Konvertering av andra format, till exempel *.dmg* till *.pkg* stöds inte.
>

1. Hämta [Intunes programhanteringsverktyg för Mac](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac).

    > [!NOTE]
    > **Intunes programhanteringsverktyg för Mac** måste köras på en macOS-dator. 

2. Markera det nedladdade verktyget som en körbar fil:
   - Starta terminalappen.
   - Ändra katalogen till den plats där `IntuneAppUtil` finns.
   - Kör följande kommando för att göra verktygsfilen körbar:<br> 
       `chmod +x IntuneAppUtil`

3. Använd `IntuneAppUtil`-kommandot inom den **Intunes programhanteringsverktyg för Mac** för att omsluta den verksamhetsspecifika *.pkg*-filen från en *.intunemac*-fil.<br>

    Exempelkommandon att använda för Microsoft Intune programhanteringsverktyget för macOS:
    > [!IMPORTANT]
    > Kontrollera att argumentet `<source_file>` inte innehåller blanksteg innan du kör `IntuneAppUtil`-kommandona.

    - `IntuneAppUtil -h`<br>
    Det här kommandot visar användningsinformation för verktyget.
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    Det här kommandot kommer att omsluta den verksamhetsspecifika *.pkg*-filen till en *.intunemac*-fil.
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    Det här kommandot extraherar identifierade parametrar och version för den skapade *.intunemac*-filen.

## <a name="select-the-app-type"></a>Välj typ av app

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I fönstret **Välj apptyp** väljer du **Branschspecifik app** under **Övriga** typer av appar.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.

## <a name="step-1---app-information"></a>Steg 1 – information om app

### <a name="select-the-app-package-file"></a>Välj appaketfilen

1. I fönstret **Lägg till app** klickar du på **Välj appaketfilen**. 
2. I fönstret **Appaketsfil** klickar du på bläddringsknappen. Välj en macOS-installationsfil med tillägget *.intunemac*.
   Appens information visas.
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

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

> [!NOTE]
> Om *.pkg*-filen innehåller flera appar eller appinstallationsprogram kommer Microsoft Intune endast rapportera att *appen* har installerats korrekt när alla installerade appar har upptäckts på enheten.

## <a name="update-a-line-of-business-app"></a>Uppdatera en verksamhetsspecifik app

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> För att Intune-tjänsten ska kunna distribuera en ny *.pkg*-fil till enheten, måste du öka paketet `version` och `CFBundleVersion`-strängen i *packageinfo*-filen i ditt *.pkg*-paket.

## <a name="next-steps"></a>Nästa steg

- Appen som du har skapat visas i applistan. Nu kan du tilldela den till de grupper som du väljer. Mer information finns i [Tilldela appar till grupper](apps-deploy.md).

- Lär dig mer om hur du kan övervaka appens egenskaper och tilldelning. Mer information finns i [Så här övervakar du appinformation och tilldelningar](apps-monitor.md).

- Lär dig mer om kontexten för din app i Intune. Mer information finns i [Översikt över enhets- och applivscykler](../fundamentals/device-lifecycle.md)
