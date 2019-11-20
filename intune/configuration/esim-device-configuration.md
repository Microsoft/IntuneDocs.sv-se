---
title: Aktivera eSIM-dataanslutningar i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller använd eSIM för att få Internet- och dataåtkomst med hjälp av olika dataplaner. I Intune lägger du till eller importerar aktiveringskoder och tilldelar sedan dessa aktiveringskoder med hjälp av en konfigurationsprofil. Du kan även övervaka eSIM-profilerna och kontrollera statusen för de eSIM-aktiverade enheterna.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbe2377bfd353dc00ddfdf53a6d091c486644194
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059383"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Konfigurera mobila eSIM-profiler i Intune – offentlig förhandsversion

eSIM är ett inbäddat SIM-kort som du kan använda för att ansluta till Internet via en mobildataanslutning på en eSIM-kompatibel enhet, till exempel [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro). Med ett eSIM behöver du inte skaffa ett SIM-kort från din mobiloperatör. Som global resenär kan du även växla mellan mobiloperatörer och dataabonnemang så att du alltid håller dig uppkopplad.

Låt säga att du till exempel har ett mobildataabonnemang för arbete och ett annat dataabonnemang hos en annan mobiloperatör för personligt bruk. När du reser får du Internetåtkomst genom att hitta mobiloperatörer med dataabonnemang i det området.

I Intune kan du importera engångskoder för aktivering som tillhandahålls av din mobiloperatör. För att konfigurera mobildataabonnemang på eSIM-modulen distribuerar du de här aktiveringskoderna till dina eSIM-kompatibla enheter. När Intune installerar aktiveringskoden använder eSIM-maskinvarumodulen data i aktiveringskoden för att kontakta mobiloperatören. När det är klart laddas eSIM-profilen ned på enheten och konfigureras för mobilaktivering.

Följande krävs för att distribuera eSIM till dina enheter med hjälp av Intune:

- **eSIM-kompatibla enheter**, till exempel Surface LTE: Se [om din enhet stöder eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). Eller så kan du se en lista över [några av de kända eSIM-kompatibla enheterna](#esim-capable-devices) (i den här artikeln).
- **Windows 10 Fall Creators Update PC** (1709 eller senare) som registreras och MDM-hanteras av Intune
- **Aktiveringskoder** tillhandahålls av mobiloperatören. De här engångskoderna för aktivering läggs till i Intune och distribueras till dina eSIM-kompatibla enheter. Kontakta mobiloperatören om du vill skaffa eSIM-aktiveringskoder.

## <a name="deploy-esim-to-devices---overview"></a>Distribuera eSIM till enheter – översikt

För att distribuera eSIM till enheter utför en administratör följande uppgifter:

1. Importera aktiveringskoder som tillhandahålls av mobiloperatören
2. Skapa en Azure Active Directory-enhetsgrupp (Azure AD) som innehåller dina eSIM-kompatibla enheter
3. Tilldela Azure AD-gruppen till din importerade prenumerationspool
4. Övervaka distributionen

Den här artikeln vägleder dig genom stegen.

## <a name="esim-capable-devices"></a>eSIM-kompatibla enheter

Följande enheter har tillkännagivits som eSIM-kompatibla eller finns på marknaden i dag. Kontrollera även om [din enhet stöder eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- ASUS NovoGo TP370QL
- ASUS TP401
- ASUS omvandlare Mini T103
- HP Elitebook G5
- HP känner avundsjuka x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630

## <a name="step-1-add-cellular-activation-codes"></a>Steg 1: Lägga till mobilaktiveringskoder

Mobilaktiveringskoder tillhandahålls av mobiloperatören i en kommaavgränsad fil (csv). När du har den här filen lägger du till den i Intune med följande steg:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **eSIM-mobilprofiler** > **Lägg till**.
3. Välj den CSV-fil som har dina aktiveringskoder.
4. Klicka på **OK** för att spara ändringarna.

### <a name="csv-file-requirements"></a>Krav för CSV-fil

När du arbetar med csv-filen med aktiveringskoderna ser du till att du eller din mobiloperatör följer kraven:

- Filen måste vara i csv-format (filnamn.csv).
- Filstrukturen måste följa ett strikt format. Annars misslyckas importen. Intune kontrollerar filen vid import och misslyckas om fel hittas.
- Aktiveringskoder används en gång. Det rekommenderas inte att du importerar aktiveringskoder som du tidigare importerat eftersom det kan orsaka problem när du distribuerar till samma enhet eller en annan enhet.
- Varje fil ska vara specifik för en enskild mobiloperatör, och alla aktiveringskoder ska vara specifika för samma prenumerationsavtal. Intune distribuerar slumpmässigt aktiveringskoder till målenheter. Det finns inte någon garanti gällande vilken enhet som får en specifik aktiveringskod.
- Högst 1000 aktiveringskoder kan importeras i en csv-filen.

### <a name="csv-file-example"></a>Exempel på en CSV-fil

1. Den första raden och den första cellen i CSV-filen är URL:en till mobiloperatörens eSIM-aktiveringstjänst, som kallas SM-DP + (Subscription Manager Data Preparation-servern). URL:en ska vara ett fullständigt kvalificerat domännamn (FQDN) utan kommatecken.
2. Den andra raden och alla följande rader är unika engångskoder för aktivering som innehåller två värden:

    1. Den första kolumnen är unikt ICCID (identifierare för SIM-kortet)
    2. Den andra kolumnen är matchande ID med endast ett kommatecken som avgränsare (inget kommatecken i slutet). Se följande exempel:

        ![Exempel på CSV-fil med mobiloperatörens aktiveringskod](./media/esim-device-configuration/url-activation-code-examples.png)

3. CSV-filnamnet blir namnet på mobilabonnemangspoolen i Azure-portalen. I föregående bild är filnamnet `UnlimitedDataSkynet.csv`. Därför ger Intune abonnemangspoolen namnet `UnlimitedDataSkynet.csv`:

    ![Mobilabonnemangspoolen namnges efter CSV-exempelfilens aktiveringskod](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Steg 2: Skapa en Azure AD-enhetsgrupp

Skapa en enhetsgrupp som innehåller de eSIM-kompatibla enheterna. [Lägg till grupper](../fundamentals/groups-add.md) innehåller stegen.

> [!NOTE]
> - Endast enheter omfattas; användare omfattas inte.
> - Vi rekommenderar att du skapar en statisk Azure AD-enhetsgrupp som innehåller eSIM-enheterna. Användning av en grupp bekräftar att du endast avser eSIM-enheter.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Steg 3: Tilldela eSIM-aktiveringskoder till enheter

Tilldela profilen till den Azure AD-grupp som innehåller eSIM-enheterna.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **eSIM-mobilprofiler**.
3. I listan med profiler väljer du den eSIM-mobilabonnemangspool som du vill tilldela och väljer sedan **Tilldelningar**.
4. Välj om du vill **inkludera** eller **exkludera** grupper och välj sedan grupperna.

    ![Inkludera enhetsgruppen för att tilldela profilen](./media/esim-device-configuration/include-exclude-groups.png)

5. När du väljer dina grupper väljer du en Azure AD-grupp. Om du vill välja flera grupper använder du **Ctrl**-tangenten och väljer grupperna.
6. **Spara** ändringarna när du är klar.

eSIM-Aktiveringskoder används en gång. När Intune har installerat en aktiveringskod på en enhet kontaktar eSIM-modulen mobiloperatör för att ladda ned mobilprofilen. Den här kontakten slutför registreringen av enheten med mobiloperatörens nätverk.

## <a name="step-4-monitor-deployment"></a>Steg 4: Övervaka distributionen

### <a name="review-the-deployment-status"></a>Granska distributionsstatusen

När du har tilldelat profilen kan du övervaka distributionsstatus för en abonnemangspool.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **eSIM-mobilprofiler**. Alla dina befintliga eSIM-mobilabonnemangspooler visas.
3. Välj ett abonnemang och granska **Distributionsstatus**.

### <a name="check-the-profile-status"></a>Kontrollera profilstatus

När du har skapat din enhetsprofil tillhandahåller Intune grafiska diagram. Dessa diagram visar status för en profil, som t.ex. om den har tilldelats till enheter korrekt eller om profilen visar en konflikt.

1. Välj **Enheter** > **eSIM-mobilprofiler** > Välj en befintlig prenumeration.
2. I fliken **Översikt** visar det översta grafiska diagrammet det antal enheter som är tilldelade till den specifika distributionen av eSIM-mobilabonnemangspool.

    Det visar även antalet enheter för andra plattformar som tilldelats samma enhetsprofil.

    Intune visar leverans och installationsstatus för den aktiveringskod som riktas till enheter.

    - **Enheten är inte synkroniserad**: Den avsedda enheten har inte kontaktat Intune sedan eSIM-distributionsprincipen skapades
    - **Aktivering väntar**: Ett tillfälligt tillstånd när Intune aktivt installerar aktiveringskoden på enheten
    - **Aktiv**: Aktiveringskoden har installerats
    - **Aktiveringen misslyckades**: Installationen av aktiveringskoden misslyckades – se felsökningsguiden.

#### <a name="view-the-detailed-device-status"></a>Visa detaljerad enhetsstatus

Du kan övervaka och visa en detaljerad lista över enheter i Enhetsstatus.**

1. Välj **Enheter** > **eSIM-mobilprofiler** > Välj en befintlig prenumeration.
2. Välj **Enhetsstatus**. Intune visar ytterligare information om enheten:

    - **Enhetsnamn**: Namnet på den enhet som avses
    - **Användare**: Användare av den registrerade enheten
    - **ICCID**: Unik kod som tillhandahålls av mobiloperatören inom den aktiveringskod som är installerad på enheten
    - **Aktiveringsstatus**: Status för Intune-leverans -installation för aktiveringskoden på enheten
    - **Mobilstatus**: Tillstånd som tillhandahålls av mobiloperatören. Kontakta mobiloperatören för att felsöka.
    - **Senaste incheckning**: Datum då enheten senast kommunicerade med Intune

### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Övervaka eSIM-profilinformation på den faktiska enheten

1. På enheten öppnar du **Inställningar** > gå till **Nätverk och Internet**.
2. Välj **Mobilt** > **Hantera eSIM-profiler**
3. eSIM-profilerna visas i listan:

    ![Visa eSIM-profiler i enhetsinställningarna](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Ta bort eSIM-profilen från enheten

När du tar bort enheten från Azure AD-gruppen tas även eSIM-profilen bort. Se till att:

1. Bekräfta att du använder Azure AD-gruppen för eSIM-enheter.
2. Gå till Azure AD-gruppen och ta bort enheten från gruppen.
3. När den borttagna enheten kontaktar Intune utvärderas den uppdaterade principen, och eSIM-profilen tas bort.

eSIM-profilen tas även bort när enheten [dras tillbaka](../remote-actions/devices-wipe.md#retire) eller avregistreras av användaren eller när åtgärden [ta bort företagsdata](../remote-actions/devices-wipe.md#wipe) körs på enheten.

> [!NOTE]
> Det är inte säkert att faktureringen avbryts om du tar bort profilen. Kontakta mobiloperatören för att kontrollera faktureringsstatusen för din enhet.

## <a name="best-practices--troubleshooting"></a>Metodtips och felsökning

- Se till att CSV-filen är korrekt formaterad. Bekräfta att filen inte innehåller duplicerade koder, flera mobiloperatörer eller olika dataplaner. Kom ihåg att varje fil måste vara unik för en mobiloperatör och ett mobildataabonnemang.
- Skapa en statisk Azure AD-enhetsgrupp som endast innehåller eSIM-enheter som är mål.
- Om det finns ett problem med distributionsstatusen kontrollerar du följande:
  - **Filformatet är inte korrekt**: Se **Steg 1: Lägg till mobilaktiveringskoder** (i den här artikeln) om hur du formaterar filen korrekt.
  - **Mobilaktiveringen fungerar inte, kontakta mobiloperatören**: Aktiveringskoden kan kanske inte aktiveras inom deras nätverk. Eller så misslyckades nedladdningen av profilen och mobilaktiveringen.

## <a name="next-steps"></a>Nästa steg
[Konfigurera enhetsprofiler](../device-profiles.md)
