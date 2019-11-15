---
title: Uppdatera Windows BIOS-funktioner med hjälp av MDM-principer i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till en DFCI-profil (Device Firmware Configuration Interface) för att hantera UEFI-inställningar, till exempel CPU, inbyggd maskinvara och startalternativ på Windows 10-enheter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9fe2b2174252aa1081eb311d79b4b5ba37f96f2
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755342"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Använda DFCI-profiler på Windows-enheter i Microsoft Intune (allmänt tillgänglig förhandsversion)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

När du använder Intune för att hantera Autopilot-enheter kan du hantera UEFI-inställningar (BIOS) när enheterna har registrerats med hjälp av DFCI (Device Firmware Configuration Interface). En översikt av fördelar, scenarier och förutsättningar finns i [översikten över DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/).

Med DFCI [kan Windows](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp) skicka hanteringskommandon från Intune till UEFI (Unified Extensible Firmware Interface).

I Intune använder du den här funktionen för att kontrollera BIOS-inställningar. Vanligtvis är inbyggd programvara mer motståndskraftig mot skadliga attacker. Den begränsar slutanvändarnas kontroll över BIOS, vilket är lämpligt i en komprometterad situation.

Anta att du använder Windows 10-enheter i en säker miljö och vill inaktivera kameran. Du kan inaktivera kameran på lagret för inbyggd programvara så att det inte spelar någon roll vad slutanvändaren gör. Kameran aktiveras inte om operativsystemet startas om eller om datorn rensas. Ett annat exempel är att låsa startalternativen för att hindra användare från att starta ett annat operativsystem eller en äldre version av Windows som inte har samma säkerhetsfunktioner.

När du installerar om en äldre Windows-version, installerar ett separat operativsystem eller formaterar hårddisken kan du inte åsidosätta DFCI-hantering. Den här funktionen kan förhindra att skadlig kod kommunicerar med OS-processer, däribland förhöjda OS-processer. Förtroendekedjan i DFCI använder kryptering med offentlig nyckel och är inte beroende av lokal lösenordssäkerhet för UEFI (BIOS). Det här säkerhetslagret hindrar lokala användare från att komma åt hanterade inställningar från enhetens UEFI-menyer (BIOS).

Den här funktionen gäller för:

- Windows 10 RS5 (1809) och senare med UEFI som stöds

## <a name="before-you-begin"></a>Innan du börjar

- Enhetstillverkaren måste ha lagt till DFCI i sin inbyggda UEFI-programvara under tillverkningsprocessen eller som en uppdatering av inbyggd programvara som du installerar. Ta hjälp av dina enhetsleverantörer för att fastställa [vilka tillverkare som stöder DFCI](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) eller vilken version av inbyggd programvara som krävs för användning av DFCI.

- Enheten måste registreras för Windows Autopilot av en [Microsoft Cloud Solution Provider-partner (CSP)](https://partner.microsoft.com/cloud-solution-provider) eller registreras direkt av OEM-tillverkaren. 

  Enheter som registreras manuellt för Autopilot, till exempel sådana som [importeras från en CSV-fil](../enrollment/enrollment-autopilot.md#add-devices), tillåts inte att använda DFCI. Det är avsiktligt att DFCI-hantering kräver extern attestering av enhetens kommersiella förvärv via en OEM-tillverkare eller en Microsoft CSP-partnerregistrering till Windows Autopilot.

  När enheten har registrerats visas dess serienummer i listan över Windows Autopilot-enheter.

  Mer information om Autopilot samt eventuella krav finns i [Registrera Windows-enheter i Intune med hjälp av Windows Autopilot](../enrollment/enrollment-autopilot.md).

## <a name="create-your-azure-ad-security-groups"></a>Skapa dina Azure AD-säkerhetsgrupper

Autopilot-distributionsprofiler tilldelas till Azure AD-säkerhetsgrupper. Se till att skapa grupper som omfattar dina DFCI-enheter som stöds. För DFCI-enheter kan de flesta organisationer skapa enhetsgrupper i stället för användargrupper. Beakta följande scenarier:

- HR-avdelningen har annorlunda Windows-enheter. Av säkerhetsskäl vill du inte att någon i den här gruppen ska använda kameran på enheterna. I det här scenariot kan du skapa en användargrupp för HR-säkerhet så att principen gäller för användarna i HR-gruppen oavsett enhetstyp.
- På produktionsgolvet har du 10 enheter. Du vill förhindra alla enheter från att startas från en USB-enhet. I det här scenariot kan du skapa en säkerhetsenhetsgrupp och lägga till dessa 10 enheter i gruppen.

Mer information om hur du skapar grupper i Intune finns i [Lägga till grupper för att organisera användare och enheter](../fundamentals/groups-add.md).

## <a name="create-the-profiles"></a>Skapa profilerna

För att använda DFCI skapar du följande profiler och tilldelar dem till din grupp.

### <a name="create-an-autopilot-deployment-profile"></a>Skapa en Autopilot-distributionsprofil

Den här profilen upprättar och förkonfigurerar nya enheter. [Autopilot-distributionsprofil](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile) visar stegen för att skapa profilen.

### <a name="create-an-enrollment-state-page-profile"></a>Skapa en profil för registreringsstatussida

Den här profilen ser till att enheterna verifieras och aktiveras för DFCI under Windows-installationen. Det rekommenderas starkt att du använder den här profilen för att blockera enhetsanvändning tills alla appar och profiler har installerats. [Profil för registreringsstatussida](../enrollment/windows-enrollment-status.md) visar en lista över stegen för att skapa profilen.

### <a name="create-the-dfci-profile"></a>Skapa DFCI-profilen

Den här profilen innehåller de DFCI-inställningar som du konfigurerar.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Konfigurationsprofiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på profilen. Namnge dina principer så att du enkelt kan identifiera dem senare. Ett användbart profilnamn är till exempel **Windows: Konfigurera DFCI-inställningar på Windows-enheter**.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Device Firmware Configuration Interface**.

4. Konfigurera inställningarna:

    - **Tillåt lokal användare att ändra UEFI-inställningar (BIOS)** : Alternativen är:
      - **Endast ej konfigurerade inställningar**: Den lokala användaren kan ändra valfri inställningar *förutom* de inställningar som uttryckligen anges till **Aktivera** eller **Inaktivera** av Intune.
      - **Inga**: Den lokala användaren kan inte ändra UEFI-inställningar (BIOS), däribland inställningar som inte visas i DFCI-profilen.

    - **CPU- och I/O-virtualisering**: Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: BIOS gör plattformens funktioner för CPU- och I/O-virtualisering tillgängliga för användning av operativsystemet. Det aktiverar Windows-tekniker för virtualiseringsbaserad säkerhet och enhetsskydd.
        - **Inaktivera**: BIOS inaktiverar plattformens funktioner för CPU- och I/O-virtualisering och förhindrar att de används.
    - **Kameror**: Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: Alla inbyggda kameror som hanteras direkt av UEFI (BIOS) aktiveras. Kringutrustning, till exempel USB-kameror, påverkas inte.
        - **Inaktiverad**: Alla inbyggda kameror som hanteras direkt av UEFI (BIOS) inaktiveras. Kringutrustning, till exempel USB-kameror, påverkas inte.
    - **Mikrofoner och högtalare**:  Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: Alla inbyggda mikrofoner och högtalare som hanteras direkt av UEFI (BIOS) aktiveras. Kringutrustning, till exempel USB-enheter, påverkas inte.
        - **Inaktiverad**: Alla inbyggda mikrofoner och högtalare som hanteras direkt av UEFI (BIOS) inaktiveras. Kringutrustning, till exempel USB-enheter, påverkas inte.
    - **Radio (Bluetooth, Wi-Fi, NFC osv.)** : Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: Alla inbyggda radior som hanteras direkt av UEFI (BIOS) aktiveras. Kringutrustning, till exempel USB-enheter, påverkas inte.
        - **Inaktiverad**: Alla inbyggda radior som hanteras direkt av UEFI (BIOS) inaktiveras. Kringutrustning, till exempel USB-enheter, påverkas inte.

        > [!WARNING]
        > Om du inaktiverar inställningen **Radio** måste enheten ha en trådbunden nätverksanslutning. Annars kan enheten bli ohanterbar.

    - **Starta från externa media (USB, SD)** : Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: UEFI (BIOS) tillåter start från icke-hårddiskbaserad lagring.
        - **Inaktiverad**: UEFI (BIOS) tillåter inte start från icke-hårddiskbaserad lagring.
    - **Starta från nätverkskort**:  Alternativen är:
        - **Inte konfigurerad**: Intune ändrar inte den här funktionen och låter eventuella inställningar vara kvar som de är.
        - **Aktiverad**: UEFI (BIOS) tillåter start från inbyggda nätverksgränssnitt.
        - **Inaktiverad**: UEFI (BIOS) tillåter inte start från inbyggda nätverksgränssnitt.

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar. Profilen skapas och visas i listan.

## <a name="assign-the-profiles-and-reboot"></a>Tilldela profilerna och starta om

När profilerna har skapats är de [redo att tilldelas](../configuration/device-profile-assign.md). Tilldela profilerna till dina Azure AD-säkerhetsgrupper som omfattar dina DFCI-enheter.

När enheten kör Windows Autopilot kan DFCI framtvinga en omstart på sidan för registreringsstatus. Den första omstarten registrerar UEFI i Intune. 

Om du vill bekräfta att enheten har registrerats kan du starta om enheten igen, men det är inget krav. Följ enhetstillverkarens instruktioner för att öppna UEFI-menyn och bekräfta att UEFI hanteras.

Nästa gången enheten synkroniserar med Intune, tar Windows emot DFCI-inställningarna. Starta om enheten. Den här tredje omstarten krävs för att UEFI ska kunna ta emot DFCI-inställningarna från Windows.

## <a name="update-existing-dfci-settings"></a>Uppdatera befintliga DFCI-inställningar

Om du vill ändra befintliga DFCI-inställningar på enheter som används kan du göra det. I din befintliga DFCI-profil ändrar du inställningarna och sparar ändringarna. Eftersom profilen redan har tilldelats börjar de nya DFCI-inställningarna gälla när:

1. Enheten checkar in med Intune-tjänsten för att granska profiluppdateringar. Incheckningar sker då och då. Mer information finns i [när enheter hämtar uppdateringar av princip, profil eller app](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

2. Om du vill framtvinga de nya inställningarna startar du om enheten [fjärrstyrt](../remote-actions/device-restart.md) eller lokalt.

Du kan även [signalera till enheter att checka in](../remote-actions/device-sync.md). Efter en lyckad synkronisering [signalerar du för omstart](../remote-actions/device-restart.md).

>[!NOTE]
> Om du tar bort DFCI-profilen, eller tar bort en enhet från den grupp som är tilldelad till profilen, innebär det inte att DFCI-inställningarna tas bort eller att UEFI-menyerna (BIOS) återaktiveras. Om du vill sluta använda DFCI uppdaterar du din befintliga DFCI-profil. Mer information om stegen finns i [ta enheten ur bruk](#retire) i den här artikeln.

## <a name="reuse-retire-or-recover-the-device"></a>Återanvända, återställa eller ta enheten ur bruk

### <a name="reuse"></a>Återanvända

Om du planerar att återställa Windows för att ändra syftet med enheten [rensar du enheten](../remote-actions/devices-wipe.md). Ta **inte** bort Autopilot-enhetsposten.

När du har rensat enheten flyttar du enheten till den grupp som tilldelats de nya DFCI- och Autopilot-profilerna. Starta om enheten för att köra Windows-konfigurationen igen.

### <a name="retire"></a>Pensionera

När du är redo att ta enheten ur bruk och frigöra den från hantering uppdaterar du DFCI-profilen till de UEFI-inställningar (BIOS) som du vill ha i utgångstillståndet. Vanligtvis vill du att alla inställningar är aktiverade. Exempel:

1. Öppna din DFCI-profil (**Enheter** > **Konfigurationsprofiler**).
2. Ändra **Tillåt lokal användare att ändra UEFI-inställningar (BIOS)** till **Endast ej konfigurerade inställningar**.
3. Ange alla andra inställningar till **Ej konfigurerat**.
4. Spara inställningarna.

De här stegen låser upp enhetens UEFI-menyer (BIOS). Värdena förblir samma som profilen (**Aktiverade** eller **Inaktiverade**) och återställs inte tillbaka till standardvärden för operativsystemet.

Du är nu redo att rensa enheten. När enheten har rensats tar du bort Autopilot-posten. När du tar bort posten förhindras enheten från att automatiskt registreras på nytt när den startas om.

### <a name="recover"></a>Återställa

Om du rensar en enhet och tar bort Autopilot-posten innan du låser upp UEFI-menyerna (BIOS) förblir menyerna låsta. Intune kan inte skicka profiluppdateringar för att låsa upp dem.

Om du vill låsa upp enheten öppnar du UEFI-menyn (BIOS) och uppdaterar hanteringen från nätverket. Återställningen låser upp menyerna, men lämnar alla UEFI-inställningar (BIOS) som värdena i den tidigare Intune DFCI-profilen.

## <a name="end-user-impact"></a>Påverkan för slutanvändare

När DFCI-principen tillämpas kan lokala användare inte ändra inställningar som konfigurerats av DFCI, även om UEFI-menyn (BIOS) är lösenordsskyddad. Beroende på de inställningar som du konfigurerar kan slutanvändare få felmeddelanden om att maskinvarukomponenter inte hittas eller inte kan diagnostiseras. Ge slutanvändarna dokumentation som förklarar de alternativ som du har inaktiverat.  

## <a name="next-steps"></a>Nästa steg

När profilen har tilldelats [övervakar du dess status](../device-profile-monitor.md).
