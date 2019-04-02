---
title: Använda Zebra Mobility tillägg på Android-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använda Microsoft Intune för att hantera och använda Zebra enheter som kör Android med Zebra Mobility tillägg (MX). Se alla steg, inklusive installera appen företagsportal separat appen, tilldela enhetsadministratörens roll, skapa en profil för StageNow och mycket mer.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
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
ms.openlocfilehash: aa2734247569245794bce7fe1de68c8b20c6091f
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490612"
---
# <a name="use-and-manage-zebra-devices-with-zebra-mobility-extensions-in-microsoft-intune"></a>Använda och hantera Zebra enheter med Zebra Mobility tillägg i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune innehåller en omfattande uppsättning funktioner, inklusive hantering av appar och konfigurera inställningar för enheter. Dessa inbyggda funktioner och inställningar används för att hantera Android-enheter tillverkats av Zebra tekniker, även kallat ”Zebra enheter”.

Om du vill anpassa eller lägga till fler Zebra-specifika inställningar du kan också använda Zebra **Mobility tillägg (MX)** på dessa enheter. 

Den här funktionen gäller för:

- Android

Företaget kan använda Zebra enheter för detaljhandeln på fabriksgolvet med mera. Exempelvis kan du är en återförsäljare och tusentals Zebra mobila enheter som används av försäljningsställen finns i din miljö. Intune kan hjälpa dig att hantera dessa enheter som en del av din lösning för hantering av mobila enheter.

Med Intune kan registrera du Zebra enheter för att distribuera dina line-of-business-appar till enheter. ”Enhet” konfigurationsprofiler kan du skapa MX-profiler för att hantera dina Zebra-specifika inställningar.

Den här artikeln visar hur du använder Zebra Mobility tillägg (MX) på Zebra enheter i Microsoft Intune.

## <a name="before-you-begin"></a>Innan du börjar

- Måste du ha den senaste versionen av StageNow skrivbordsappen från Zebra tekniker.
- Bör du kontrollera [Zebras fullständig MX funktionen matrisen](http://techdocs.zebra.com/mx/compatibility) (öppnas Zebras-webbplats) att bekräfta de profiler som skapas är kompatibla med enhetens MX-version, OS-version och modellen.
- Vissa enheter, till exempel TC20/25 enheter stöder inte alla tillgängliga MX-funktioner i StageNow. Se till att kontrollera [Zebras funktionen matrisen](http://techdocs.zebra.com/mx/tc2x/) (öppnas Zebras-webbplats) för uppdaterade supportinformation.

## <a name="step-1-install-the-latest-company-portal-app"></a>Steg 1: Installera den senaste företagsportalappen

Gå till Google Play store på enheten, och hämta och installera Intunes företagsportalapp från Microsoft. När du har installerat från Google Play, företagsportalappen hämtar uppdateringar och korrigeringar automatiskt.

Om Google Play inte är tillgängligt, ladda ned den [Microsoft Intunes företagsportal för Android](https://www.microsoft.com/download/details.aspx?id=49140) (öppnas en annan Microsoft-webbplats), och [läsa den](#sideload-the-company-portal-app) (i den här artikeln). När du installerat på så sätt kan appen ta emot inte uppdateringar eller åtgärdas automatiskt. Du bör regelbundet uppdaterar och korrigera appen manuellt.

### <a name="sideload-the-company-portal-app"></a>Separat inläsning av företagsportalappen

”Separat inläsning” är när du inte använder Google Play för att installera en app. Använd StageNow läsa appen företagsportal. 

Följande steg ger en översikt. Specifik information finns i dokumentationen för Zebra's. [Registrera dig i en MDM med StageNow](http://techdocs.zebra.com/stagenow/3-1/Profiles/enrollmdm/) (öppnas Zebras-webbplats) kan vara en bra resurs.

1. I StageNow, skapar du en profil för **registrera i en MDM**.
2. I **distribution**, välja att hämta filen MDM-agenten.
3. Ange den **Support App** och **ladda ned Configuration** steg för att **nr**.
4. I **hämta MDM**väljer **överföring/kopiera filen**. Lägg till källa och mål för företagets Portal Android-paketet (APK).
5. I **starta MDM**, lämna standardinställningarna efter-är. Lägg till följande information:

    - **Paketnamn**: `com.microsoft.windowsintune.companyportal`
    - **Klassnamn**: `com.microsoft.windowsintune.companyportal.views.SplashActivity`

Fortsätta att publicera profilen och använda den med StageNow appen på enheten. Företagsportalappen är installerad och öppnas på enheten.

> [!TIP]
> Mer information om StageNow, så att den inte finns i [StageNow Android-enhet mellanlagring](https://www.zebra.com/us/en/products/software/mobile-computers/mobile-app-utilities/stagenow.html) (öppnas Zebras-webbplats).

## <a name="step-2-confirm-the-company-portal-app-has-device-administrator-role"></a>Steg 2: Kontrollera att företagsportalappen har enhetsadministratörens roll

Företagsportalappen krävs enhet-administratören hantera Android-enheter. Om du vill aktivera rollen Enhetsadministratör är vissa enheter som Zebra ett användargränssnitt (UI) på enheten. Om enheten innehåller ett användargränssnitt, företagsportalappen uppmanas användaren att bevilja Enhetsadministratör under [registrering](#step-3-enroll-the-device-in-to-intune) (i den här artikeln).

Om ett gränssnitt är inte tillgängligt, använder du den **DevAdmin Manager** i StageNow att skapa en profil som ger manuellt Enhetsadministratör att appen företagsportal.

Följande steg ger en översikt. Specifik information finns i dokumentationen för Zebra's. 
[Inställning batteri växlingsutrymme som enhetsadministratör](https://zebratechnologies.force.com/s/article/Set-Battery-Swap-Mode-as-Device-Administrator-using-StageNow-Tool) (öppnas Zebras webbplats) kan vara en bra resurs.

1. Skapa en profil i StageNow, och välj **Xpert läge**.
2. Lägg till **DevAdmin Manager** till profilen.
3. Ange **Administration Enhetsåtgärd** till **aktivera som Enhetsadministratör**.
4. Ange **Admin paket enhetsnamn** till `com.microsoft.windowsintune.companyportal`.
5. Ange **enheten Admin klassnamn** till `com.microsoft.omadm.client.PolicyManagerReceiver`.

Fortsätta att publicera profilen och använda den med StageNow appen på enheten. Företagsportalappen beviljas rollen Administratör för enheten.

## <a name="step-3-enroll-the-device-in-to-intune"></a>Steg 3: Registrera enheten i Intune

När du har slutfört de två första stegen, installeras företagsportalappen på enheten. Enheten är redo att vara registrerade i Intune.

[Registrera Android-enheter](android-enroll.md) innehåller stegen. Om du har många Zebra enheter kanske du vill använda en [konto för enhetsregistreringshantering](device-enrollment-manager-enroll.md).

## <a name="step-4-create-a-device-management-profile-in-stagenow"></a>Steg 4: Skapa en profil för hantering i StageNow

Använd StageNow för att skapa en profil som konfigurerar inställningar som du vill hantera på enheten. Specifik information finns i dokumentationen för Zebra's. [Profiler](http://techdocs.zebra.com/stagenow/3-2/stagingprofiles/) (öppnas Zebras webbplats) kan vara en bra resurs.

När du skapar profilen i StageNow, på det sista steget, Välj **exportera till MDM**. Detta genererar en XML-fil. Spara filen. Du behöver det i ett senare steg.

> [!TIP]
> Vi rekommenderar för att testa profilen innan du distribuerar den till enheter i din organisation. I det sista steget när du skapar profiler med StageNow på datorn testa, att använda den **testa** alternativ. Sedan kan använda StageNow genererade filen med StageNow appen på enheten. 
> 
> StageNow appen på enheten visar loggar som genereras när du testar profilen. [Använd StageNow loggar in på Zebra enheter som kör Android i Intune](android-zebra-mx-logs-troubleshoot.md) innehåller information om hur du använder StageNow loggar för att förstå fel.

> [!NOTE]
> Om du refererar till appar, uppdateringspaket eller uppdatera andra filer i din StageNow-profil som du vill att enheten att få dessa uppdateringar. För att få uppdateringar kan ansluta enheten till distributionsservern StageNow när profilen tillämpas. 
> 
> Eller du kan använda de inbyggda funktionerna i Intune för att få dessa ändringar, inklusive: 
> - Funktioner i apphantering [lägga till](apps-add.md), [distribuera](apps-deploy.md), uppdatera, och [övervakaren](apps-monitor.md) appar.
> - Hantera [system-och app](device-restrictions-android-for-work.md#device-owner-only) på enheter som kör Android Enterprise

När du har testat filen är nästa steg att distribuera profilen till enheter med Intune.

> [!NOTE]
> Distribuera en profil till varje enhet. Om det finns flera StageNow profiler som du vill distribuera på enheter kan exportera StageNow profiler och kombinera inställningarna i en XML-fil innan du lägger till den i Intune. 
> 
> Vill du inte två inställningar som konfigurerar samma egenskap i samma XML-filen. Målet är att undvika konflikter mellan inställningar på enheten.

## <a name="step-5-create-a-profile-in-intune"></a>Steg 5: Skapa en profil i Intune

Skapa en enhetskonfigurationsprofil i Intune:

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på den nya profilen.
    - **Beskrivning:** Ange en beskrivning för profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Android**.
    - **Profiltyp**: Välj **MX-profilen (endast Zebra)**.

4. I **MX-profil i XML-format**, lägga till XML-profilfil [du har exporterat från StageNow](#step-4-create-a-device-management-profile-in-stagenow) (i den här artikeln).
5. Välj **OK** > **Skapa** för att spara ändringarna. Principen skapas och visas i listan.

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Nästa gång enheten söker efter konfigurationsuppdateringar, har MX-profil distribuerats till enheten. Enheter som synkroniseras med Intune när enheter registreras och sedan cirka var åttonde timme. Du kan också [kan du framtvinga synkronisering i Intune](device-sync.md). Eller på enheten, öppna den **företagsportalappen** > **inställningar** > **synkronisering**. 

> [!TIP]
> - Av säkerhetsskäl visas inte profilen XML-text när du har sparat. Texten är krypterad och du kan bara se asterisker (`****`). Referens rekommenderar vi för att spara kopior av MX-profiler innan du lägger till dem i Intune.
> 
> - Om du vill uppdatera en profil när den är tilldelad till Zebra enheter kan skapa en uppdaterad StageNow XML-fil, redigera den befintliga Intune-profilen och lägga till den nya StageNow XML-filen. Den nya filen skriver över den föregående StageNow principen i profilen.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

[Använda StageNow loggar för felsökning av Zebra enheter](android-zebra-mx-logs-troubleshoot.md).
