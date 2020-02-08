---
title: Använda OEMConfig för Android Enterprise-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd Microsoft Intune för att hantera och använda enheter som kör Android Enterprise med OEMConfig. Se alla steg, inklusive en översikt och kraven, skapa konfigurationsprofilen i Intune och se en lista över OEMConfig-appar som stöds.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cc568cbadb683f632ffd2365ab7023cd796f231
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886703"
---
# <a name="use-and-manage-android-enterprise-devices-with-oemconfig-in-microsoft-intune"></a>Använda och hantera Android Enterprise-enheter med OEMConfig i Microsoft Intune

I Microsoft Intune kan du använda OEMConfig för att lägga till, skapa och anpassa OEM-specifika inställningar för Android Enterprise-enheter. OEMConfig används vanligtvis för att konfigurera inställningar som inte är inbyggda i Intune. Olika OEM-tillverkare (Original Equipment Manufacturer) inkluderar olika inställningar. De tillgängliga inställningarna beror på vad OEM-tillverkaren inkluderar i sin OEMConfig-app.

Den här funktionen gäller för:  

- Android enterprise

Den här artikeln beskriver OEMConfig, beskriver förutsättningarna, visar hur du skapar en konfigurationsprofil och innehåller en lista med de OEMConfig-appar som stöds i Intune.

## <a name="overview"></a>Översikt

OEMConfig-principer är en särskild typ av enhetskonfigurationsprincip som liknar [konfigurationsprincipen för appar](../apps/app-configuration-policies-overview.md). OEMConfig är en standard definierad av Google och som använder appkonfiguration i Android för att skicka enhetsinställningar till appar som skrivits av OEM-tillverkare (Original Equipment Manufacturer). Med den här standarden kan OEM- och EMM-tillverkare (Enterprise Mobility Management) bygga och stödja OEM-specifika funktioner på ett standardiserat sätt. [Mer information om OEMConfig](https://blog.google/products/android-enterprise/oemconfig-supports-enterprise-device-features/).

Tidigare har EMM-tillverkare, till exempel Intune, manuellt skapat stöd för OEM-specifika funktioner efter att de har introducerats av OEM-tillverkaren. Den här metoden leder till dubblerad arbetsinsats och långsamt införande.

Med OEMConfig skapar en OEM-tillverkare ett schema som definierar OEM-specifika hanteringsfunktioner. OEM-tillverkaren bäddar in schemat i en app och placerar sedan appen på Google Play. EMM läser schemat från appen och exponerar schemat i EMM-administratörskonsolen. Med konsolen kan Intune-administratörer konfigurera inställningarna i schemat.

När OEMConfig-appen installeras på en enhet använder den inställningarna som konfigurerats på EMM-administratörskonsolen för att hantera enheten. Enhetsinställningarna körs av OEMConfig-appen, i stället för en MDM-agent som skapats av EMM.

När OEM-tillverkaren lägger till och förbättrar hanteringsfunktionerna uppdaterar OEM även appen i Google Play. Som administratör får du de här nya funktionerna och uppdateringarna (inklusive korrigeringar) utan att behöva vänta på att EMM-tillverkaren ska inkludera dessa uppdateringar.

> [!TIP]
> Du kan bara använda OEMConfig med enheter som har stöd för den här funktionen och har en motsvarande OEMConfig-app. Kontakta din OEM-tillverkare för mer information.

## <a name="before-you-begin"></a>Innan du börjar

När du använder OEMConfig bör du vara medveten om följande:

- Intune visar OEMConfig-appens schema så att du kan konfigurera det. Intune verifierar eller ändrar inte det schema som tillhandahålls av appen. Så om schemat är felaktigt eller har felaktiga data, skickas dessa data fortfarande till enheter. Om du hittar ett problem som kommer från schemat kontaktar du OEM-tillverkaren för vägledning.
- Intune påverkar eller styr inte innehållet i appens schema. Exempelvis har Intune ingen kontroll över strängar, språk, vilka åtgärder som tillåts och så vidare. Vi rekommenderar att du kontaktar OEM-tillverkaren för mer information om hur du hanterar deras enheter med OEMConfig.
- OEM-tillverkare kan när som helst uppdatera sina funktioner och scheman som stöds och ladda upp en ny app i Google Play. Intune synkroniserar alltid den senaste versionen av OEMConfig-appen från Google Play. Intune behåller inte äldre versioner av schemat eller appen. Om du stöter på versionskonflikter rekommenderar vi att du kontaktar OEM-tillverkaren för mer information.
- Tilldela en OEMConfig-profil till en enhet. Om flera profiler tilldelas till samma enhet kan det hända att du ser ett inkonsekvent beteende. OEMConfig-modellen har endast stöd för en enda princip per enhet.

## <a name="prerequisites"></a>Krav

För att kunna använda OEMConfig på dina enheter ska du kontrollera att följande krav är uppfyllda:

- En Android Enterprise-enhet som har registrerats i Intune.
- En OEMConfig-app som har skapats av OEM-tillverkaren och laddats upp till Google Play. Kontakta OEM-tillverkaren för mer information om den inte finns på Google Play.
- Intune-administratören har behörighet enligt rollbaserad åtkomstkontroll (RBAC) för **mobilappar**, **enhetskonfigurationer** och läsbehörighet under **Android for Work**. De här behörigheterna krävs eftersom OEMConfig-profiler använder hanterade appkonfigurationer för att hantera enhetskonfigurationer.

## <a name="prepare-the-oemconfig-app"></a>Förbereda OEMConfig-appen

Kontrollera att enheten har stöd för OEMConfig, att rätt OEMConfig-app läggs till i Intune och att appen installeras på enheten. Kontakta OEM-tillverkaren för att få den här informationen.

> [!TIP] 
> OEMConfig-appar är specifika för OEM-tillverkaren. Till exempel fungerar inte en Sony OEMConfig-app som är installerad på en Zebra Technologies-enhet.

1. Hämta OEMConfig-appen från den hanterade Google Play-butiken. [Lägg till hanterade Google Play-appar till Android enterprise-enheter](../apps/apps-add-android-for-work.md) har en lista med alla steg.
2. Vissa OEM-tillverkare kan leverera enheter med OEMConfig-appen förinstallerad. Om appen inte är förinstallerad använder du Intune för att [lägga till och distribuera appen till enheterna](../apps/apps-deploy.md).

## <a name="create-an-oemconfig-profile"></a>Skapa en OEMConfig-profil

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Plattform**: Välj **Android Enterprise**.
    - **Profiltyp**: Välj **OEMConfig**.

4. Välj **Skapa**.
5. Ange följande egenskaper i **Grundinställningar**:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **OEMConfig-app**: Välj **Välj en OEMConfig-app**.

6. Under **Tillhörande app** väljer du en befintlig OEMConfig-app som tidigare har lagts till > **Välj**. Se till att du väljer rätt OEMConfig-app för de enheter som du tilldelar principen till.

    Om du inte ser några appar i listan kan du konfigurera hanterad Google Play och hämta appar från den hanterade Google Play-butiken. I [Lägg till hanterade Google Play-appar till Android Enterprise-enheter](../apps/apps-add-android-for-work.md) finns en lista med alla steg.

    > [!IMPORTANT]
    > Om du har lagt till en OEMConfig-app och synkroniserat den med Google Play, men den inte visas som en **Tillhörande app**, kan du behöva kontakta Intune för att registrera appen. Se [lägga till en ny app](#supported-oemconfig-apps) (i den här artikeln).

7. Välj **Nästa**.
8. Under **Konfigurera inställningar** väljer du **Configuration Designer** eller **JSON-redigerare**:

    > [!TIP]
    > Läs OEM-dokumentationen för att se till att du har konfigurerat egenskaperna korrekt. De här appegenskaperna inkluderas av OEM-tillverkaren, inte Intune. Intune utför minimal verifiering av egenskaperna eller det du anger. Om du till exempel anger `abcd` för ett portnummer sparas profilen som den är och distribueras till dina enheter med de värden som du konfigurerar. Se till att du anger rätt information.

    - **Configuration Designer**: När du väljer det här alternativet visas de egenskaper som är tillgängliga i appens schema så att du kan konfigurera dem.

      - Snabbmenyer i Configuration Designer visar att fler alternativ är tillgängliga. Med snabbmenyn kanske du till exempel kan lägga till, ta bort och ändra ordning på inställningar. De här alternativen inkluderas av OEM. Se till att läsa dokumentationen för OEM-appen för att lära dig hur dessa alternativ ska användas för att skapa profiler.

      - Många inställningar har standardvärden som tillhandahålls av OEM-tillverkaren. För att se om det finns ett standardvärde kan du hovra över informationsikonen bredvid inställningen. En knappbeskrivning visar standardvärdena för den inställningen (om tillämpligt) och mer information från OEM-tillverkaren.

      - Om du klickar på **Rensa** tas den inställningen bort från profilen. Om en inställning inte finns i profilen ändras inte dess värde på enheten när profilen tillämpas.

      - Om du skapar ett tomt (okonfigurerat) paket i Configuration Designer tas det bort när du växlar till JSON-redigeraren.

    - **JSON-redigerare**: När du väljer det här alternativet öppnas en JSON-redigerare med en mall för det fullständiga konfigurationsschemat som är inbäddat i appen. Anpassa mallen med värden för de olika inställningarna i redigeraren. Om du använder **Configuration Designer** för att ändra dina värden skriver JSON-redigeraren över mallen med värden från Configuration Designer.

      - Om du uppdaterar en befintlig profil visar JSON-redigeraren de inställningar som senast sparades med profilen.

      - OEMConfig-scheman kan vara stora och komplexa. Om du vill uppdatera inställningarna med en annan redigerare väljer du knappen **Ladda ned JSON-mall**. Använd valfri redigerare för att lägga till dina konfigurationsvärden i mallen. Kopiera och klistra sedan in den uppdaterade JSON-filen i egenskapen **JSON-redigerare**.

      - Du kan använda JSON-redigeraren för att skapa en säkerhetskopia av din konfiguration. När du har konfigurerat inställningarna använder du den här funktionen för att hämta JSON-inställningarna med dina värden. Kopiera och klistra in JSON till en fil och spara den. Nu har du en säkerhetskopia.

    Ändringar som görs i Configuration Designer görs också automatiskt i JSON-redigeraren. På samma sätt görs även alla ändringar som görs i JSON-redigeraren automatiskt i Configuration Designer. Om dina indata innehåller ogiltiga värden kan du inte växla mellan Configuration Designer och JSON-redigeraren förrän du har åtgärdat problemen.

9. Välj **Nästa**.
10. Under **Omfångstaggar** (valfritt), tilldelar du en tagg för att filtrera profilen till specifika IT-grupper, till exempel `US-NC IT Team` eller `JohnGlenn_ITDepartment`. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

    Välj **Nästa**.

11. Under **Tilldelningar**väljer du de användare eller grupper som ska ta emot din profil. Tilldela en profil till varje enhet. OEMConfig-modellen har bara stöd för en princip per enhet.

    Mer information om hur du tilldelar profiler finns i [Tilldela användar- och enhetsprofiler](device-profile-assign.md).

    Välj **Nästa**.

12. Granska inställningarna under **Granska + skapa**. När du väljer **Skapa** sparas dina ändringar och profilen tilldelas. Principen visas också i profillistan.

Nästa gången enheten söker efter konfigurationsuppdateringar tillämpas de OEM-specifika inställningar som du har konfigurerat i OEMConfig-appen.

> [!NOTE]
> OEMConfig-standarden omfattar för närvarande inte statusrapportering. Därför visar profilerna som standard **väntande** status.

## <a name="supported-oemconfig-apps"></a>OEMConfig-appar som stöds

Jämfört med standardappar expanderar OEMConfig-appar de hanterade konfigurationsprivilegier som beviljats av Google för att stödja mer komplexa scheman. Intune har för närvarande stöd för följande OEMConfig-appar:

-----------------

| OEM | Samlings-ID | OEM-dokumentation (om tillgänglig) |
| --- | --- | ---|
| Samsung | com.samsung.android.knox.kpu | [Administratörsguide för Knox Service plugin-program](https://docs.samsungknox.com/knox-service-plugin/admin-guide/index.htm) |
| Zebra Technologies | com.zebra.oemconfig.common | [Översikt över Zebra OEMConfig](http://techdocs.zebra.com/oemconfig ) |
| Datalogic | com.datalogic.oemconfig | [Användardokumentation för Datalogic OEMConfig](https://datalogic.github.io/oemconfig/) |
| Honeywell | com.honeywell.oemconfig |  |
| Kyocera | jp.kyocera.enterprisedeviceconfig |  |
| Spectralink – streckkoder | com.spectralink.barcode.service |  |
| Spectralink – knappar | com.spectralink.buttons |  |
| Spectralink – enhet | com.spectralink.slnkdevicesettings  |  |
| Spectralink – loggning | com.spectralink.slnklogger |  |
| Spectralink – VQO | com.spectralink.slnkvqo |  |
| HMD Global | com.hmdglobal.app.oemconfig.ironman |  |

-----------------

Om det finns ett OEMConfig-program för din enhet, men det inte visas i tabellen ovan, eller inte visas på Intune-konsolen, ber vi dig skicka e-post till `IntuneOEMConfig@microsoft.com`.

> [!NOTE]
> OEMConfig-appar måste aktiveras av Intune innan de kan konfigureras med OEMConfig-profiler. När en app stöds behöver du inte kontakta Microsoft om hur du konfigurerar den i din klientorganisation. Följ bara anvisningarna på den här sidan.

## <a name="next-steps"></a>Nästa steg

[Övervaka profilstatus](device-profile-monitor.md).
