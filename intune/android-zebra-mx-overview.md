---
title: Använda Zebra Mobility Extensions på Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd Microsoft Intune för att hantera och använda Zebra-enheter som kör Android med Zebra Mobility Extensions (MX). Se alla steg, till exempel hur du installerar appen Företagsportal, utför separat inläsning av appen, tilldelar enhetsadministratörsrollen och skapar en StageNow-profil.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 69814b91978aa3cd74c4dc239b099883ae402af9
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764782"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I Intune finns en omfattande uppsättning funktioner, bland annat för att hantera appar och konfigurera enhetsinställningar. Dessa inbyggda funktioner och inställningar används för att hantera Android-enheter som tillverkats av Zebra Technologies (även kallade ”Zebra-enheter”).

Med **Mobility Extensions (MX)**-profiler kan du anpassa eller lägga till fler Zebra-specifika inställningar på Android-enheter.

Den här artikeln visar hur du använder Zebra Mobility Extensions (MX) på Zebra-enheter i Microsoft Intune.

Den här funktionen gäller för:

- Android

Företag kan använda Zebra-enheter till exempel inom detaljhandel och på fabriksgolvet. Anta att ditt företag är återförsäljare och har tusentals Zebra-mobilenheter som säljarna använder. Då kan Intune hjälpa dig att hantera dessa enheter som en del i din MDM-lösning (hantering av mobilenheter).

Med Intune kan du registrera Zebra-enheter för att distribuera dina verksamhetsspecifika appar till enheterna. Med profiler för enhetskonfiguration kan du skapa MX-profiler för att hantera dina Zebra-specifika inställningar.

## <a name="before-you-begin"></a>Innan du börjar

- Se till att du har den senaste versionen av skrivbordsappen StageNow från Zebra Technologies.
- Se [Zebras fullständiga MX-funktionstabell](http://techdocs.zebra.com/mx/compatibility) (öppnar Zebras webbplats) för att kontrollera att de profiler du skapar är kompatibla med enhetens MX-version, operativsystemversion och modell.
- Vissa enheter, till exempel TC20/25-enheter, stöder inte alla tillgängliga MX-funktioner i StageNow. Gå till [Zebras funktionstabell](http://techdocs.zebra.com/mx/tc2x/) (öppnar Zebras webbplats) om du vill se den senaste supportinformationen.

## <a name="step-1-install-the-latest-company-portal-app"></a>Steg 1: Hämta den senaste versionen av appen Företagsportal

Gå till Google Play på enheten och hämta och installera appen Företagsportal från Microsoft. När du har installerat appen Företagsportal från Google Play hämtas uppdateringar och korrigeringar automatiskt.

Om Google Play inte är tillgängligt hämtar du [Microsoft Intune Företagsportal för Android](https://www.microsoft.com/download/details.aspx?id=49140) (öppnar en annan Microsoft-webbplats) och [läs in den separat](#sideload-the-company-portal-app) (i den här artikeln). När appen installeras på det här sättet får appen inte uppdateringar eller korrigeringar automatiskt. Du bör uppdatera och korrigera appen manuellt med jämna mellanrum.

### <a name="sideload-the-company-portal-app"></a>Läsa in appen Företagsportal separat

”Separat inläsning” innebär att du inte installerar appen via Google Play. Använd StageNow om du vill läsa in appen Företagsportal separat. 

Följande steg ger en översikt. Specifik information finns i Zebras dokumentation. [Enroll in an MDM using StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (Registrera dig i en MDM med StageNow) (öppnar Zebras-webbplats) kan vara en bra resurs.

1. Skapa en profil för **Enroll in an MDM** (Registrera dig i en MDM) i StageNow.
2. I **Deployment** (Distribution) väljer du att ladda ned MDM-agentfilen.
3. Ange **No** (Nej) för stegen **Support App** (Supportapp) och **Download Configuration** (Hämta konfiguration).
4. I **Download MDM** (Ladda ned MDM) väljer du **Transfer/Copy File** (Överför/kopiera fil). Lägg till källa och mål för Android-paketet (APK) för Företagsportal.
5. Lämna standardvärdena som de är i **Launch MDM** (Starta MDM). Lägg till följande information:

    - **Paketnamn**: `com.microsoft.windowsintune.companyportal`
    - **Klassnamn**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Fortsätt att publicera profilen och använd den med appen StageNow på enheten. Appen Företagsportal installeras och öppnas på enheten.

> [!TIP]
> Om du vill ha mer information om StageNow och vad den gör, kan du se [StageNow Android device staging](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (Förberedelse av Android-enheter med StageNow) (öppnar Zebras webbplats).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Steg 2: Kontrollera att appen Företagsportal har enhetsadministratörsrollen

Appen Företagsportal måste ha enhetsadministratörsrollen för att hantera Android-enheter. I vissa Zebra-enheter finns ett användargränssnitt för att aktivera enhetsadministratörsrollen. Om enheten innehåller användargränssnittet uppmanas slutanvändaren i appen Företagsportal att bevilja enhetsadministratörsrollen under [registreringen](#step-3-enroll-the-device-in-to-intune) (i den här artikeln).

Om den inte innehåller användargränssnittet använder du **DevAdmin Manager** i StageNow för att skapa en profil som manuellt beviljar enhetsadministratörsrollen till appen Företagsportal.

Följande steg ger en översikt. Specifik information finns i Zebras dokumentation. 
[Set battery swap mode as device administrator](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (Ange batteriväxlingsläge som enhetsadministratör) (öppnar Zebras webbplats) kan vara en bra resurs.

1. Skapa en profil i StageNow och välj **Xpert Mode**.
2. Lägg till **DevAdmin Manager** i profilen.
3. Ange **Turn On as Device Administrator** (Aktivera som enhetsadministratör) för **Device Administration Action** (Åtgärd för enhetsadministration).
4. Ange `com.microsoft.windowsintune.companyportal` som **Device Admin Package Name** (Administratörspaketnamn för enheten).
5. Ange `com.microsoft.omadm.client.PolicyManagerReceiver` som **Device Admin Class Name** (Administratörsklassnamn för enheten).

Fortsätt att publicera profilen och använd den med appen StageNow på enheten. Appen Företagsportal beviljas enhetsadministratörsrollen.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Steg 3: Registrera enheten i Intune

När du har slutfört de två första stegen installeras appen Företagsportal på enheten. Enheten är klar att registreras i Intune.

Anvisningar finns i [Enroll Android devices](android-enroll.md) (Registrera Android-enheter). Om du har många Zebra-enheter kanske du vill använda ett [DEM-konto (enhetsregistreringshanterare)](device-enrollment-manager-enroll.md). Om du använder ett DEM-konto tas även alternativet att avregistrera från appen Företagsportal bort så att det blir svårare för användarna att avregistrera enheten.

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Steg 4: Skapa en enhetshanteringsprofil i StageNow

Använd StageNow för att skapa en profil som konfigurerar inställningar som du vill hantera på enheten. Specifik information finns i Zebras dokumentation. [Profiles](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (Profiler) (öppnar Zebras webbplats) kan vara en bra resurs.

När du skapar profilen i StageNow i det sista steget väljer du **Export to MDM** (Exportera till MDM). Detta genererar en XML-fil. Spara den här filen. Du behöver den i ett senare steg.

> [!TIP]
> Vi rekommenderar att du testar profilen innan du distribuerar den till enheter i din organisation. I det sista steget när du skapar profiler med StageNow på datorn kan du testa profilen med **testalternativen**. Sedan använder du den StageNow-genererade filen med appen StageNow på enheten. 
> 
> I appen StageNow på enheten visas loggar som skapades när du testade profilen. I [Use StageNow logs on Zebra devices running Android in Intune](android-zebra-mx-logs-troubleshoot.md) (Använda StageNow-loggar på Zebra-enheter som kör Android i Intune) finns information om hur du använder StageNow-loggar för att få information om varför fel uppstår.

> [!NOTE]
> Om du refererar till appar, uppdaterar paket eller uppdaterar andra filer i din StageNow-profil vill du att enheten ska få dessa uppdateringar. För att kunna få uppdateringarna måste enheten ansluta till StageNow-distributionsservern när profilen används. 
> 
> Eller så kan du använda de inbyggda funktionerna i Intune för att hämta dessa ändringar, till exempel: 
> - Apphanteringsfunktioner för att [lägga till](apps-add.md), [distribuera](apps-deploy.md), uppdatera och [övervaka](apps-monitor.md) appar.
> - Hantera [system- och appuppdateringar](device-restrictions-android-for-work.md#device-owner-only) på enheter som kör Android Enterprise

När du har testat filen är nästa steg att distribuera profilen till enheter med Intune.

> [!NOTE]
> Distribuera en profil till varje enhet. Om det finns flera StageNow-profiler som du vill distribuera till enheterna exporterar du StageNow-profilerna och kombinerar inställningarna till en enda XML-fil innan du lägger till den i Intune. 
> 
> Du vill inte ha två inställningar som konfigurerar samma egenskap i samma XML-fil. Målet är att undvika konflikter mellan inställningar på enheten.

## <a name="step-5-create-a-profile-in-intune"></a>Steg 5: Skapa en profil i Intune

Skapa en enhetskonfigurationsprofil i Intune:

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Android**.
    - **Profiltyp**: Välj **MX-profilen (endast Zebra)**.

4. I **MX-profil i .xml-format**  lägger du till XML-profilfilen [som du exporterade från StageNow](#step-4-create-a-device-management-profile-in-stagenow) (i den här artikeln).
5. Välj **OK** > **Skapa** för att spara ändringarna. Principen skapas och visas i listan.

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Nästa gång enheten söker efter konfigurationsuppdateringar distribueras MX-profilen till enheten. Enheterna synkroniseras med Intune när de registreras och därefter ungefär var åttonde timme. Du kan också [framtvinga en synkronisering i Intune](device-sync.md). Eller öppna **appen Företagsportal** > **Inställningar** > **Synkronisera** på enheten. 

> [!TIP]
> - Av säkerhetsskäl visas inte XML-profilens text när du har sparat den. Texten är krypterad och du ser bara asterisker (`****`). Vi rekommenderar att du sparar kopior av MX-profiler för egen referens innan du lägger till dem i Intune.
> 
> - Om du vill uppdatera en profil efter att den har tilldelats till Zebra-enheter skapar du en uppdaterad StageNow XML-fil, redigerar den befintliga Intune-profilen och lägger till den nya StageNow XML-filen. Den nya filen skriver över den tidigare StageNow-principen i profilen.

## <a name="next-steps"></a>Nästa steg

- [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
- [Använd StageNow-loggar för att felsöka Zebra-enheter](android-zebra-mx-logs-troubleshoot.md).
