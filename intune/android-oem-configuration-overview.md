---
title: Använda OEMConfig för Android Enterprise-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd Microsoft Intune för att hantera och använda enheter som kör Android Enterprise med OEMConfig. Se alla steg, inklusive en översikt, se kraven, skapa konfigurations profilen i Intune och se en lista över OEMConfig-appar som stöds.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3108364850641cd85abf6b97a2b981735f59895
ms.sourcegitcommit: 8934b1abec96e18cee15a77107d37551766f7666
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71303915"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I Microsoft Intune kan du använda OEMConfig för att lägga till, skapa och anpassa OEM-/regionsspecifika inställningar för Android Enterprise-enheter. OEMConfig används vanligt vis för att konfigurera inställningar som inte är inbyggda i Intune. Olika OEM-tillverkare (Original Equipment Manufacturer) innehåller olika inställningar. De tillgängliga inställningarna beror på vad OEM-tillverkaren inkluderar i sin OEMConfig-app.

Den här funktionen gäller för:  

- Android enterprise

Den här artikeln beskriver OEMConfig, visar förutsättningarna, visar hur du skapar en konfigurations profil och listar de OEMConfig-appar som stöds i Intune.

## <a name="overview"></a>Översikt

OEMConfig-principer är en särskild typ av enhets konfigurations princip som liknar [konfigurations principen för appar](app-configuration-policies-overview.md). OEMConfig är en standard som definieras av Google och som använder appens konfiguration i Android för att skicka enhets inställningar till appar som skrivits av OEM-tillverkare (Original Equipment Manufacturer). Med den här standarden kan OEM-och EMMs (Enterprise Mobility Management) bygga och stödja OEM-specifika funktioner på ett standardiserat sätt. [Läs mer om OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Tidigare EMMs, till exempel Intune, skapar support manuellt för OEM-specifika funktioner när de har introducerats av OEM-tillverkaren. Den här metoden leder till dubbla insatser och går långsamt.

Med OEMConfig skapar en OEM ett schema som definierar OEM-/regionsspecifika hanterings funktioner. OEM: en bäddar in schemat i en app och placerar sedan appen på Google Play. EMM läser schemat från appen och exponerar schemat i EMM-administratörskonsolen. Med-konsolen kan Intune-administratörer konfigurera inställningarna i schemat.

När OEMConfig-appen installeras på en enhet används inställningarna som kon figurer ATS i EMM-administratörskonsolen för att hantera enheten. Inställningarna på enheten körs av OEMConfig-appen, i stället för en MDM-agent som skapats av EMM.

När OEM-tillverkaren lägger till och förbättrar hanterings funktionerna uppdaterar OEM även appen i Google Play. Som administratör får du de här nya funktionerna och uppdateringarna (inklusive korrigeringar) utan att vänta på att EMMs ska inkludera dessa uppdateringar.

> [!TIP]
> Du kan bara använda OEMConfig med enheter som har stöd för den här funktionen och har en motsvarande OEMConfig-app. Kontakta din OEM för mer information.

## <a name="before-you-begin"></a>Innan du börjar

När du använder OEMConfig bör du vara medveten om följande information:

- Intune visar OEMConfig-appens schema så att du kan konfigurera det. Intune verifierar eller ändrar inte det schema som tillhandahålls av appen. Så om schemat är felaktigt eller har felaktiga data, skickas dessa data fortfarande till enheter. Om du hittar ett problem som kommer från schemat kontaktar du OEM-tillverkaren för vägledning.
- Intune påverkar eller styr inte innehållet i appens schema. Exempelvis har Intune ingen kontroll över strängar, språk, vilka åtgärder som tillåts och så vidare. Vi rekommenderar att du kontaktar OEM för information och metod tips för att hantera sina enheter med OEMConfig.
- OEM-tillverkare kan när som helst uppdatera sina funktioner och scheman och ladda upp en ny app i Google Play. Intune synkroniserar alltid den senaste versionen av OEMConfig-appen från Google Play. Intune behåller inte äldre versioner av schemat eller appen. Om du stöter på versions konflikter rekommenderar vi att du kontaktar OEM för mer information.
- Tilldela en enhet en OEMConfig-profil. Om flera profiler tilldelas till samma enhet kan det hända att du ser inkonsekventa beteenden. OEMConfig-modellen har endast stöd för en enda princip per enhet.

## <a name="prerequisites"></a>Krav

Kontrol lera att du har följande krav för att använda OEMConfig på dina enheter:

- En Android Enterprise-enhet som har registrerats i Intune.
- En OEMConfig-app som skapats av OEM-tillverkaren och laddats upp till Google Play. Kontakta OEM för mer information om det inte finns på Google Play.
- Intune-administratören har behörighet som rollbaserad åtkomst kontroll (RBAC) för **mobilappar** och **DeviceConfigurations**. De här behörigheterna krävs eftersom OEMConfig-profiler använder hanterade AppData för att hantera enhetsspecifika konfigurationer.

## <a name="prepare-the-oemconfig-app"></a>Förbereda OEMConfig-appen

Kontrol lera att enheten har stöd för OEMConfig, att rätt OEMConfig-app läggs till i Intune och att appen installeras på enheten. Kontakta OEM-tillverkaren för att få den här informationen.

> [!TIP] 
> OEMConfig-appar är bara för OEM-tillverkaren. Till exempel gör en Sony OEMConfig-app som är installerad på en zebra Technologies-enhet inte något.

1. Hämta OEMConfig-appen från den hanterade Google Play Butik. [Lägg till hanterade Google Play-appar till Android enterprise-enheter](apps-add-android-for-work.md) har en lista med alla steg.
2. Vissa OEM-tillverkare kan leverera enheter med OEMConfig-appen förinstallerad. Om appen inte är förinstallerad använder du Intune för att [lägga till och distribuera appen till enheter](apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Skapa en OEMConfig-profil

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
    - Välj **Android Enterprise** för **Plattform**.
    - **Profil typ**: Välj **OEMConfig**.

4. Välj **tillhör ande app**, Välj en befintlig OEMConfig-app som du tidigare lade till > **OK**. Se till att välja rätt OEMConfig-app för de enheter som du tilldelar principen till.

    Om du inte ser några appar i listan kan du konfigurera hanterad Google Play och hämta appar från den hanterade Google Play-butiken. [Lägg till hanterade Google Play-appar till Android enterprise-enheter](apps-add-android-for-work.md) har en lista med alla steg.

    > [!IMPORTANT]
    > Om du har lagt till en OEMConfig-app och synkroniserat den med Google Play, men den inte listas som en **kopplad app**, kan du behöva kontakta Intune för att publicera appen. Se [lägga till en ny app](#supported-oemconfig-apps) (i den här artikeln).

5. I **Konfigurera inställningar med**väljer du att använda **Configuration designer** eller **JSON-redigeraren**:

    > [!TIP]
    > Läs OEM-dokumentationen för att kontrol lera att du har konfigurerat egenskaperna korrekt. De här app-egenskaperna ingår i OEM-tillverkaren, inte i Intune. Intune kontrollerar minimal verifiering av egenskaperna eller vad du anger. Om du till exempel anger `abcd` för ett port nummer sparar profilen som-är och distribueras till dina enheter med de värden som du konfigurerar. Se till att du anger rätt information.

    - **Konfigurations design**: när du väljer det här alternativet visas de egenskaper som är tillgängliga i appens schema så att du kan konfigurera.

      - Snabb menyer i Configuration Designer visar att fler alternativ är tillgängliga. Snabb menyn kan till exempel användas för att lägga till, ta bort och ändra ordning på inställningar. De här alternativen ingår i OEM. Se till att läsa dokumentationen för OEM-appen för att lära dig hur dessa alternativ ska användas för att skapa profiler.

      - Många inställningar har standardvärden som tillhandahålls av OEM-tillverkaren. För att se om det finns ett standardvärde, Hovra över informations ikonen bredvid inställningen. En knapp Beskrivning visar standardvärden för den inställningen (om tillämpligt) och mer information från OEM-tillverkaren.

      - Om du klickar på **Rensa** tas en inställning bort från profilen. Om en inställning inte finns i profilen, ändras inte dess värde på enheten när profilen tillämpas.
        
      - Om du skapar ett tomt (avkonfigurerat) paket i Configuration designer tas det bort när du växlar till JSON-redigeraren.

    - **JSON-redigerare**: när du väljer det här alternativet öppnas en JSON-redigerare med en mall för det fullständiga konfigurations schema som är inbäddat i appen. Anpassa mallen med värden för de olika inställningarna i redigeraren. Om du använder **Configuration designer** för att ändra dina värden skriver JSON-redigeraren över mallen med värden från Configuration designer.
    
      - Om du uppdaterar en befintlig profil visar JSON-redigeraren de inställningar som senast sparades med profilen.

      - OEMConfig-scheman kan vara stora och komplexa. Om du vill uppdatera inställningarna med en annan redigerare väljer du knappen **Hämta JSON-mall** . Använd valfritt redigerings program för att lägga till dina konfigurations värden i mallen. Kopiera och klistra sedan in den uppdaterade JSON-filen i till **JSON-redigerarens** egenskap.

      - Du kan använda JSON-redigeraren för att skapa en säkerhets kopia av din konfiguration. När du har konfigurerat inställningarna använder du den här funktionen för att hämta JSON-inställningarna med dina värden. Kopiera och klistra in JSON till en fil och spara den. Nu har du en säkerhets kopierings fil.

    Ändringar som görs i Configuration designer görs också automatiskt i JSON-redigeraren. På samma sätt görs alla ändringar som görs i JSON-redigeraren automatiskt i Configuration designer. Om inaktuella inuppgifter innehåller ogiltiga värden kan du inte växla mellan Configuration designer och JSON-redigeraren förrän du har åtgärdat problemen.

6. Välj **OK** > **Lägg till** för att spara ändringarna. Principen skapas och visas i listan.

Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

 > [!NOTE]
 > Tilldela en profil till varje enhet. OEMConfig-modellen stöder bara en princip per enhet.

Nästa gången enheten söker efter konfigurations uppdateringar tillämpas de OEM-/regionsspecifika inställningar som du har konfigurerat på OEMConfig-appen.

> [!NOTE]
> OEMConfig-standarden omfattar för närvarande inte status rapportering. Därför visar profilerna som standard **väntande** status.

## <a name="supported-oemconfig-apps"></a>OEMConfig-appar som stöds

Jämfört med standard appar expanderar OEMConfig-appar de hanterade konfigurations privilegier som beviljats av Google för att stödja mer komplexa scheman. Intune har för närvarande stöd för följande OEMConfig-appar:

-----------------

| OEM | Samlings-ID | OEM-dokumentation (om tillgänglig) |
| --- | --- | ---|
| Samsung | com. Samsung. Android. Knox. KPU | [Administratörs guide för Knox Service plugin-program](https://docs.samsungknox.com/knox-service-plugin/admin-guide/welcome.htm) |
| Zebra-tekniker | com. Zebra. oemconfig. common | [Översikt över Zebra-OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com. Datalogic. oemconfig | [Användar dokumentation för Datalogic-OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com. Honeywell. oemconfig |  |

-----------------

Om det finns ett OEMConfig-program för din enhet, men inte i tabellen ovan, eller inte visas i Intune-konsolen, måste du skicka ett e-`IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> OEMConfig-appar måste aktive ras av Intune innan de kan konfigureras med OEMConfig-profiler. När en app stöds behöver du inte kontakta Microsoft om hur du konfigurerar den i din klient organisation. Följ bara anvisningarna på den här sidan.

## <a name="next-steps"></a>Nästa steg

- [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
