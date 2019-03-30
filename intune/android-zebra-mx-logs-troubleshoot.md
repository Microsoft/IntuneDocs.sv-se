---
title: Använd StageNow loggar in på Android Zebra enheter i Microsoft Intune – Azure | Microsoft Docs
description: Se vanliga problem och lösningar när du använder StageNow på Android-enheter med Microsoft Intune. Lär dig också att hämta loggarna och se exempel på hur du läser loggarna för slutförande- eller fel.
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
ms.openlocfilehash: 36476820805c00cefafcd9f64dd2f08a014762c0
ms.sourcegitcommit: 44095bbd1502b02201a01604531f4105401fbb92
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58490549"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Felsöka och se eventuella problem på Android Zebra enheter i Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda i Microsoft Intune, [Zebra Mobility tillägg (MX) att hantera enheter med Android Zebra](android-zebra-mx-overview.md). När du använder Zebra enheter kan du skapa profiler i StageNow att hantera inställningar och överför dem till Intune. Intune använder StageNow appen för att tillämpa inställningarna på enheterna. Appen StageNow skapar även en detaljerad loggfil på den enhet som används för att felsöka.

Den här funktionen gäller för:

- Android

Exempelvis kan skapa du en profil i StageNow att konfigurera en enhet. När du skapar profilen StageNow genererar en fil i det sista steget för du testa profilen. Du kan använda den här filen med StageNow appen på enheten.

Ett annat exempel är du skapar en profil i StageNow och testa den. I Intune, lägga till StageNow profilen och tilldela den till dina Zebra-enheter. När du kontrollerar status för den tillhörande profilen visar profilen statusen på hög nivå.

I båda dessa fall kan du få mer information från loggfil StageNow som sparas på enheten varje gång en StageNow profilen används.

Vissa problem inte är relaterade till innehållet i StageNow profilen och syns inte i loggarna.

Den här artikeln visar hur du läsa StageNow loggar och visar en lista över andra potentiella problem med Zebra enheter som inte kanske återspeglas i loggarna.

[Använda och hantera Zebra enheter med Zebra Mobility tillägg](android-zebra-mx-overview.md) innehåller mer information om den här funktionen.

## <a name="get-the-logs"></a>Hämta loggarna

### <a name="use-the-stagenow-app-on-the-device"></a>Använd StageNow appen på enheten
När du testar en profil som direkt med hjälp av StageNow i på datorn, istället för att använda [Intune för att distribuera profilen](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), StageNow-appen på enheten sparar loggar testet. Hämta filen med den **mer (...)**  alternativet i StageNow appen på enheten.

### <a name="get-logs-using-android-debug-bridge"></a>Hämta loggar med Android Debug-bryggan
Om du vill hämta loggar när profilen har redan distribuerats med Intune, ansluter du enheten till en dator med [Android Debug-bryggan (GDB)](https://developer.android.com/studio/command-line/adb) (öppnas Androids-webbplats).

På enheten sparas loggar i `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Hämta loggar från e-post
Om du vill hämta loggar när profilen har redan distribuerats med Intune, slutanvändare kan e-du loggarna via en e postapp på enheten. Öppna appen företagsportal på Zebra-enheten och [skicka loggarna](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Med funktionen Skicka loggar skapar även en PowerLift incident-ID som du kan referera till om du kontaktar Microsoft support.

## <a name="read-the-logs"></a>Läsa loggarna

När du tittar på loggarna, det finns ett fel när du ser den `<characteristic-error>` tagg. Information om fel skrivs till den `<parm-error>` tagg > `desc` egenskapen.

## <a name="error-types"></a>Feltyper

Zebra enheter är olika nivåer för felrapportering:

- CSP: N stöds inte på enheten. Enheten är inte en mobil enhet och har inte ett mobilt manager.
- MX eller OSX-versionen matchar inte. Varje CSP är en ny version. En matris med fullständig support, se [Zebras dokumentation](http://techdocs.zebra.com/mx/) (öppnas Zebras-webbplats).
- Enheten rapporterar ett annat problem eller fel.

## <a name="examples"></a>Exempel

Till exempel ha följande indata profil:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

I loggen är XML identisk med indata. Den här matchande utdata innebär att profilen har tillämpats på enheten utan fel:

```xml
<wap-provisioningdoc>
    <characteristic type="Clock" version="6.0">
        <parm name="AutoTime" value="false"/>
        <parm name="TimeZone" value="GMT-5"/>
        <parm name="Date" value="2014-12-03"/>
        <parm name="Time" value="11:11:11"/>
    </characteristic>
</wap-provisioningdoc>
```

Ett annat exempel är innehåller följande indata:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2" >
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic type="AppMgr" version="4.2" >
        <parm name="Action" value="Install"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic>
</wap-provisioningdoc>
```

Loggen visar ett fel, eftersom den innehåller en `<characteristic-error>` tagg. I det här scenariot profilen som försökte installera ett Android-paket (APK) som inte finns i den angivna sökvägen:

```xml
<wap-provisioningdoc>
    <characteristic type="XmlMgr" version="4.2">
        <parm name="ProcessingMode" value="1"/>
    </characteristic>
    <characteristic-error type="AppMgr" version="5.1" desc="missing">
        <parm-error name="Action" value="Install" desc="apk doesnot exist in the path"/>
        <parm name="APK" value="/sdcard/test.apk"/>
    </characteristic-error>
</wap-provisioningdoc>
```

## <a name="other-potential-issues-with-zebra-devices"></a>Andra potentiella problem med Zebra enheter

Det här avsnittet innehåller andra möjliga problem uppstå när du använder Zebra enheter med Enhetsadministratör. De här problemen rapporteras inte i StageNow loggarna.

### <a name="android-system-webview-is-out-of-date"></a>Android-systemets webbvy är inaktuell

När äldre enheter loggar in med hjälp av företagsportalappen kan kan användare se ett meddelande att komponenten-systemets webbvy är inaktuell och måste uppgraderas. Om enheten inte har installerat Google Play, ansluter den till internet och Sök efter uppdateringar. Om enheten inte har installerat Google Play, hämta den uppdaterade versionen av komponenten och tillämpa den på enheterna. Eller uppdatera till den senaste enheten operativsystem som utfärdats av Zebra.

### <a name="management-actions-take-a-long-time"></a>Hanteringsåtgärder ta lång tid

Om Google Play-tjänster inte är tillgänglig kan ta upp till 8 timmar att slutföra vissa uppgifter. [Begränsningar för Intune företagsportal-appen för Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (öppnas ett annat Microsoft-webbplats) kan vara en bra resurs.

### <a name="device-spoofing-suspected-shows-in-intune"></a>”Enhet-förfalskning misstänkt” visas i Intune

Detta fel innebär att Intune misstänker att en icke - Zebra Android-enhet rapporterar dess modell och tillverkare som en Zebra-enhet.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Företagsportalappen är äldre än version som krävs

Intune kan uppdatera versionen som krävs av appen företagsportal. Om Google Play inte är installerad på enheten, uppdateras inte företagsportalappen automatiskt. Om den lägsta versionen är nyare än den installerade versionen, slutar företagsportalappen fungerar. Uppdatering av den senaste Företagsportalen med [separat inläsning på Zebra enheter](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Nästa steg

[Zebra diskussionstavlor](https://developer.zebra.com/community/home/discussions) (öppnas Zebras-webbplats)

[Använda och hantera Zebra enheter med Zebra Mobility tillägg i Intune](android-zebra-mx-overview.md)
