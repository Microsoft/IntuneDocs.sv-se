---
title: Använda StageNow-loggar på Android Zebra-enheter i Microsoft Intune-Azure | Microsoft Docs
description: Se vanliga problem och lösningar när du använder StageNow på Android-enheter med Microsoft Intune. Lär dig också hur du hämtar loggar och se exempel på hur du kan läsa loggarna efter framgång eller fel.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/26/2019
ms.topic: troubleshooting
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
ms.openlocfilehash: e7ed93c86d3fbe7ed7a6ac5d4b1a3494fb55f2bc
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506986"
---
# <a name="troubleshoot-and-see-potential-issues-on-android-zebra-devices-in-microsoft-intune"></a>Felsök och se potentiella problem på Android Zebra-enheter i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I Microsoft Intune kan du använda [Zebra Mobility Extensions (MX) för att hantera Android Zebra-enheter](android-zebra-mx-overview.md). När du använder Zebra-enheter kan du skapa profiler i StageNow för att hantera inställningar och ladda upp dem till Intune. Intune använder StageNow-appen för att tillämpa inställningarna på enheterna. StageNow-appen skapar också en detaljerad loggfil på enheten som används för fel sökning.

Den här funktionen gäller för:

- Android

Du kan till exempel skapa en profil i StageNow för att konfigurera en enhet. När du skapar StageNow-profilen genererar det sista steget en fil för att testa profilen. Du använder den här filen med StageNow-appen på enheten.

I ett annat exempel skapar du en profil i StageNow och testar den. I Intune lägger du till StageNow-profilen och tilldelar den sedan till dina Zebra-enheter. När du kontrollerar status för den tilldelade profilen, visar profilen en hög nivå status.

I båda fallen kan du få mer information från logg filen StageNow, som sparas på enheten varje gång en StageNow-profil tillämpas.

Vissa problem är inte relaterade till innehållet i StageNow-profilen och återspeglas inte i loggarna.

Den här artikeln visar hur du läser StageNow-loggarna och visar en lista över andra potentiella problem med Zebra-enheter som kanske inte återspeglas i loggarna.

[Använd och hantera Zebra-enheter med Zebra Mobility Extensions](android-zebra-mx-overview.md) innehåller mer information om den här funktionen.

## <a name="get-the-logs"></a>Hämta loggarna

### <a name="use-the-stagenow-app-on-the-device"></a>Använd StageNow-appen på enheten
När du testar en profil direkt med StageNow på datorn i, i stället för [att använda Intune för att distribuera profilen](android-zebra-mx-overview.md#step-4-create-a-device-management-profile-in-stagenow), sparar StageNow-appen på enheten loggarna från testet. Om du vill hämta logg filen använder du alternativet **mer (...)** i StageNow-appen på enheten.

### <a name="get-logs-using-android-debug-bridge"></a>Hämta loggar med hjälp av Android Debug Bridge
Om du vill hämta loggar när profilen redan har distribuerats med Intune ansluter du enheten till en dator med [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) (öppnar Android ' s webbplats).

På enheten sparas loggar i `/sdcard/Android/data/com.microsoft.windowsintune.companyportal/files`

### <a name="get-logs-from-email"></a>Hämta loggar från e-post
För att få loggar efter att profilen redan har distribuerats med Intune kan slutanvändare skicka in loggar med en e-postapp på enheten. Öppna appen Företagsportal på Zebra-enheten och [skicka loggarna](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). Med funktionen skicka loggar skapas även ett PowerLift-incident-ID som du kan använda om du kontaktar Microsoft support.

## <a name="read-the-logs"></a>Läs loggarna

När du tittar på loggarna uppstår ett fel när du ser `<characteristic-error>`-taggen. Fel information skrivs till egenskapen `<parm-error>` tag > `desc`.

## <a name="error-types"></a>Fel typer

Zebra-enheter innehåller olika fel rapporterings nivåer:

- CSP: n stöds inte på enheten. Enheten är till exempel inte en mobil enhet och har inte någon mobil hanterare.
- MX-eller OSX-versionen är felaktig. Varje KRYPTOGRAFIPROVIDER har versions hantering. En fullständig support mat ris finns i [Zebra-dokumentationen](http://techdocs.zebra.com/mx/) (öppnar Zebra ' s webbplats).
- Enheten rapporterar ett annat problem eller fel.

## <a name="examples"></a>Exempel

Du har till exempel följande ingångs profil:

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

I loggen är XML-filen identisk med indata. Denna matchande utdata innebär att profilen har tillämpats på enheten utan fel:

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

I ett annat exempel har du följande ingång:

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

Loggen visar ett fel, eftersom det innehåller en `<characteristic-error>`-tagg. I det här scenariot försökte profilen installera ett Android-paket (APK) som inte finns på den angivna sökvägen:

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

## <a name="other-potential-issues-with-zebra-devices"></a>Andra potentiella problem med Zebra-enheter

I det här avsnittet visas andra möjliga problem som kan uppstå när du använder Zebra-enheter med enhets administratör. De här problemen rapporteras inte i StageNow-loggarna.

### <a name="android-system-webview-is-out-of-date"></a>Android System WebView är inaktuellt

När äldre enheter loggar in med Företagsportal-appen kan användarna se ett meddelande om att komponenten för system WebView är inaktuell och behöver uppgraderas. Om Google Play är installerat på enheten ansluter du den till Internet och söker efter uppdateringar. Om enheten inte har Google Play installerat hämtar du den uppdaterade versionen av komponenten och använder den på enheterna. Eller uppdatera till det senaste enhets operativ systemet som utfärdats av Zebra.

### <a name="management-actions-take-a-long-time"></a>Hanterings åtgärder tar lång tid

Om Google Play-tjänsterna inte är tillgängliga tar det upp till åtta timmar att slutföra vissa uppgifter. [Begränsningar i Intune-företagsportal app för Android](https://support.microsoft.com/help/3211588/limitations-of-intune-company-portal-app-for-android-in-china) (öppnar en annan Microsoft-webbplats) kan vara en lämplig resurs.

### <a name="device-spoofing-suspected-shows-in-intune"></a>"Enhets förfalskning misstänkt" visas i Intune

Det här felet innebär att Intune misstänker att en icke-Zebra Android-enhet rapporterar sin modell och tillverkare som en zebra-enhet.

### <a name="company-portal-app-is-older-than-minimum-required-version"></a>Företagsportal-appen är äldre än den minsta version som krävs

Intune kan uppdatera den tidigaste version av Företagsportal-appen som krävs. Om Google Play inte är installerat på enheten kommer Företagsportal-appen inte att uppdateras automatiskt. Om den minsta version som krävs är nyare än den installerade versionen slutar Företagsportal-appen att fungera. Uppdatera till den senaste Företagsportal-appen med hjälp av [separat inläsning på Zebra-enheter](android-zebra-mx-overview.md#sideload-the-company-portal-app).

## <a name="next-steps"></a>Nästa steg

[Zebra diskussions tavlor](https://developer.zebra.com/community/home/discussions) (öppnar Zebra ' s webbplats)

[Använda och hantera Zebra-enheter med Zebra Mobility Extensions i Intune](android-zebra-mx-overview.md)
