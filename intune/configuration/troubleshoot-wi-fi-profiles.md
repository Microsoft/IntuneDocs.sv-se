---
title: Felsöka och granska WiFi-enhetens profilloggar i Microsoft Intune – Azure | Microsoft Docs
description: Förstå och felsöka problem i konfigurationsprofilen för WiFi på Android-, iOS- och Windows-enheter i Microsoft Intune. Granska loggar och se några vanliga problem och möjliga lösningar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: tycast
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77f5787509438ec3280f29be8449d78979806042
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74542669"
---
# <a name="troubleshoot-wi-fi-device-configuration-profiles-in-microsoft-intune"></a>Felsöka WiFi-enhetens konfigurationsprofiler i Microsoft Intune

I Intune kan du skapa enhetskonfigurationsprofiler som innehåller anslutningsinställningar för ditt WiFi-nätverk. Använd de här inställningarna när du ansluter användarnas Android-, iOS- och Windows-enheter till organisationens nätverk.

Den här artikeln visar hur en WiFi-profil ser ut när den tillämpas på enheter. Den innehåller också information om loggar, vanliga problem och mycket annat. Använd artikeln när du felsöker dina WiFi-profiler.

Mer information om WiFi-profiler i Intune finns [Lägga till och använda WiFi-inställningar på dina enheter](wi-fi-settings-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

I exemplen i den här artikeln används SCEP-certifikatautentisering för Intune-profilerna. Det förutsätter också att de betrodda rot- och SCEP-profilerna fungerar korrekt på enheten.

## <a name="android"></a>Android

I det här avsnittet går vi igenom slutanvändarupplevelsen när du installerar konfigurationsprofilerna på en Android-enhet.

### <a name="end-user-experience-example"></a>Exempel på slutanvändarupplevelse

I det här scenariot används en Nokia 6.1-enhet. Innan WiFi-profilen installeras på enheten, installerar du de betrodda rot- och SCEP-profilerna.

1. Slutanvändarna får ett meddelande om att de ska installera den betrodda rotcertifikatprofilen:

    > [!div class="mx-imgBorder"]
    > ![Exempel på företagsportalens appmeddelande i Android om att installera en betrodd rotcertifikatprofil](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-trusted-root.png)

2. I nästa meddelande uppmanas användaren att installera SCEP-certifikatprofilen:

    > [!div class="mx-imgBorder"]
    > ![Exempel på företagsportalens appmeddelande i Android om att installera en SCEP-certifikatprofil](./media/troubleshoot-wi-fi-profiles/android-end-user-company-portal-scep-certificate.png)

    > [!TIP]
    > När du använder en Android-enhet som hanteras av enhetsadministratören, kan det finnas flera certifikat i listan. När en certifikatprofil återkallas eller tas bort, finns certifikatet kvar på enheten. I det här scenariot väljer du det nyaste certifikatet. Det är vanligtvis det sista certifikatet i listan.
    >
    > Den här situationen uppstår inte på Android Enterprise- och Samsung KNOX-enheter. Mer information finns i [Hantera Android-arbetsprofilenheter](../enrollment/android-enterprise-overview.md) och [Ta bort SCEP- och PKCS-certifikat](../protect/remove-certificates.md#android-knox-devices).

3. Därefter får användarna ett meddelande om att installera WiFi-profilen:

    > [!div class="mx-imgBorder"]
    > ![Exempel på företagsportalens appmeddelande i Android om att installera en SCEP-certifikatprofil](./media/troubleshoot-wi-fi-profiles/android-end-user-install-wifi-profile.png)

4. När du är klar visas WiFi-anslutningen som ett sparat nätverk:

    > [!div class="mx-imgBorder"]
    > ![WiFi-anslutningen visas som ett sparat nätverk](./media/troubleshoot-wi-fi-profiles/android-end-user-saved-networks.png)

### <a name="review-company-portal-app-logs"></a>Granska företagsportalens apploggar

På Android innehåller filen **Omadmlog.log** information om aktiviteterna för WiFi-profilen när den installerades på enheten. Du kan ha upp till fem Omadmlog-loggfiler. Du bör hämta tidsstämpeln för den senaste synkroniseringen, eftersom den hjälper dig att hitta de relaterade loggposterna.

I följande exempel använder du [CMTrace](https://docs.microsoft.com/configmgr/core/support/cmtrace) till att läsa loggarna och söka efter ”wifimgr”:

> [!div class="mx-imgBorder"]
> ![WiFi-anslutningen visas som ett sparat nätverk](./media/troubleshoot-wi-fi-profiles/android-cmtrace-filter-wifimgr.png)

Följande logg visar sökresultaten och att WiFi-profilen har tillämpats:

```log
2019-08-01T19:22:46.7340000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.7490000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:46.8100000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:46.8209999    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:46.8240000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected ca certificate with alias: 'user:205xxxxx.0' and thumbprint '<thumbprint>'.
2019-08-01T19:22:47.0990000    VERB    com.microsoft.omadm.platforms.android.certmgr.CertificateChainBuilder    15118    04142    Complete certificate chain built with Complete certs.
2019-08-01T19:22:47.1010000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    1 cert(s) matched criteria: User<ID>[i:<ID>,17CECEA1D337FAA7D167AD83A8CC7A8FCBF9xxxx;eku:1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2]
2019-08-01T19:22:47.1090000    VERB    com.microsoft.omadm.utils.CertUtils    15118    04142    0 cert(s) excluded by criteria:
2019-08-01T19:22:47.1110000    INFO    com.microsoft.omadm.utils.CertificateSelector    15118    04142    Selected client cert with alias 'User<ID>' and requestId 'ModelName=<ModelName>%2FLogicalName_<LogicalName>;Hash=-912418295'.
2019-08-01T19:22:47.4120000    VERB    com.microsoft.omadm.Services    15118    04142    Successfully applied, enabled and saved wifi profile '<profile ID>'
2019-08-01T19:22:47.4240000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.4910000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.4970000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Starting to parse Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5080000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Starting to parse OneX from Wifi XML.
2019-08-01T19:22:47.5820000    VERB    com.microsoft.omadm.platforms.android.wifimgr.OneX    15118    04142    Completed parsing OneX from Wifi XML.
2019-08-01T19:22:47.5900000    VERB    com.microsoft.omadm.platforms.android.wifimgr.WifiProfile    15118    04142    Completed parsing Wifi Profile XML with name '<profile ID>'.
2019-08-01T19:22:47.5910000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04142    Applied profile <profile ID>

```

## <a name="ios"></a>iOS

När WiFi-profilen har installerats på enheten visas den i **Hanteringsprofil**:

> [!div class="mx-imgBorder"]
> ![Hanteringsprofil på iOS-enhet](./media/troubleshoot-wi-fi-profiles/ios-management-profile.png)

> [!div class="mx-imgBorder"]
> ![WiFi-anslutningen visas som ett WiFi-nätverk på iOS-enheten](./media/troubleshoot-wi-fi-profiles/ios-wifi-connection-in-management-profile.png)

### <a name="review-the-ios-console-and-device-logs"></a>Granska iOS-konsolen och enhetsloggarna

På iOS-enheter innehåller företagsportalens applogg inte någon information om WiFi-profiler. Om du vill se installationsinformation för dina WiFi-profiler använder du konsolen eller enhetsloggarna:

1. Anslut iOS-enheten till Mac. Gå till **Program** > **Verktyg** och öppna konsolappen.
2. Under **Åtgärd** väljer du **Inkludera informationsmeddelanden** och **Inkludera felsökningsmeddelanden**:

    > [!div class="mx-imgBorder"]
    > ![Inkludera informationsmeddelanden och inkludera felsökningsmeddelanden i iOS-konsolappen](./media/troubleshoot-wi-fi-profiles/ios-console-app-include-info-messages-debug-messages.png)

3. Återskapa scenariot och spara loggarna i en textfil:

    1. Markera alla meddelanden på den aktuella skärmen: **Redigera** > **Välj alla**.
    2. Kopiera meddelandena: **Redigera** > **Kopiera**.
    3. Klistra in loggdatan i en textredigerare och spara filen.

4. Sök i den sparade loggfilen för att se detaljerad information. När profilen har installerats ser utdatan ut ungefär som i följande logg:

    ```log
    Line 390870: debug    11:19:58.994815 -0400    profiled    Adding dependent www.windowsintune.com.wifi.Contoso to parent Microsoft.Profiles.MDM in domain ManagingProfileToManagedProfile to system\
    Line 390872: debug    11:19:58.995210 -0400    profiled    Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.wifi.Contoso in domain ManagedProfileToManagingProfile to system\
    Line 392346: default    11:19:59.360460 -0400    profiled    Profile \'93www.windowsintune.com.wifi.Contoso\'94 installed.\
    ```

## <a name="windows"></a>Windows

När WiFi-profilen har installerats på enheten, går du till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**. Välj ditt konto > **Information**:

> [!div class="mx-imgBorder"]
> ![Åtkomst till arbete eller skola och välj Information på Windows-enheten](./media/troubleshoot-wi-fi-profiles/windows-access-work-school-info.png)

**WiFi** visas i **Områden som hanteras av Microsoft**:

> [!div class="mx-imgBorder"]
> ![I områden som hanteras av Microsoft kan du se att WiFi visas i Windows](./media/troubleshoot-wi-fi-profiles/windows-wifi-areas-managed-by-microsoft.png)

Om du vill se WiFi-anslutningen går du till **Inställningar** > **Nätverk och Internet**  > **WiFi**:

> [!div class="mx-imgBorder"]
> ![I Windows kan du se WiFi-anslutningen som ett känt nätverk i inställningarna](./media/troubleshoot-wi-fi-profiles/windows-wifi-connection-known-networks.png)

### <a name="review-event-viewer-logs"></a>Granska loggbokens loggar

På Windows-enheter loggas information om WiFi-profiler i Loggboken:

1. Öppna appen **Loggboken**.
2. I **Visa**-menyn väljer du **Visa analytiska loggar och felsökningsloggar**.
3. Expandera **Program- och tjänstloggar** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Administratör**

Dina utdata kan se ut ungefär som följande loggar:

```log
Log Name:      Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
Source:        Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider
Date:          8/7/2019 8:01:41 PM
Event ID:      1506
Task Category: (1)
Level:         Information
Keywords:      (2)
User:          SYSTEM
Computer:      <Computer Name>
Description:
WiFiConfigurationServiceProvider: Node set value, type: (0x4), Result: (The operation completed successfully.).
```

## <a name="common-issues"></a>Vanliga problem

### <a name="issue-1-the-wi-fi-profile-isnt-deployed-to-the-device"></a>Problem 1: WiFi-profilen distribueras inte till enheten

- Kontrollera att WiFi-profilen har tilldelats till rätt grupp:

    1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Konfigurationsprofiler**.
    2. Välj din profil > **Tilldelningar**. Kontrollera att de valda grupperna stämmer.
    3. I Endpoint Manager väljer du **Felsökning och support**. Granska informationen i **Tilldelningar**.

- I Endpoint Manager väljer du **Felsökning och support**. Kontrollera att enheten kan synkroniseras med Intune genom att kontrollera tiden för **Senaste incheckning**.

- Om WiFi-profilen är länkad till betrodda rot- och SCEP-profiler, kontrollerar du att båda profilerna har distribuerats till enheten. WiFi-profilen är beroende av dessa profiler.

- På Windows 10 och nyare enheter granskar du informationsloggen för MDM-diagnostik:

  1. Gå till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**.
  2. Välj ditt arbets- eller skolkonto > **Information**.
  3. Längst ned på sidan **Inställningar** väljer du **Skapa rapport**.
  4. Ett fönster öppnas och visar sökvägen till loggfilerna. Välj **Exportera**.
  5. Gå till sökvägen `\Users\Public\Documents\MDMDiagnostics` och visa rapporten:

      > [!div class="mx-imgBorder"]
      > ![Exempel på diagnostisk MDM-information som visar konfigurationen av en WiFi-profil på Windows 10-enheter](./media/troubleshoot-wi-fi-profiles/windows-mdm-diagnostic-info.png)

  > [!TIP]
  > Mer information finns i [Diagnostisera MDM-fel i Windows 10](https://docs.microsoft.com/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).

- Om de betrodda rot- och SCEP-profilerna inte är installerade på en Android-enhet, visas följande post i företagsportalappens Omadmlog-fil:

  ``` log
  2019-08-01T19:18:13.5120000    INFO    com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager    15118    04105    Skipping Wifi profile <profile ID> because it is pending certificates.
  ```

  - När de betrodda rot- och SCEP-profilerna finns på Android-enheten och är kompatibla, är det inte säkert att WiFi-profilen finns på enheten. Det här problemet uppstår när **CertificateSelector**-providern från företagsportalappen inte hittar något certifikat som matchar det angivna villkoret. Det angivna villkoret kan finnas i certifikatmallen eller i SCEP-profilen.

    Om det matchande certifikatet inte kan hittas, installeras inte certifikaten på enheten. WiFi-profilen används inte eftersom den saknar rätt certifikat. I det här scenariot ser du följande post i företagsportalappens Omadmlog-fil:

    ` Skipping Wifi profile <profile ID> because it is pending certificates.`

    Följande exempellogg visar certifikat som undantas eftersom villkoret **Valfritt ändamål** i Förbättrad nyckelanvändning (EKU) angavs. Men certifikaten som tilldelats enheten har inte denna EKU:

    ```log
    2018-11-27T21:10:37.6390000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID1> and requestId <requestID1> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    Excluding cert with alias User<ID2> and requestId <requestID2> as it does not have any purpose EKU.
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    0 cert(s) matched criteria:
    2018-11-27T21:10:37.6400000    VERB     com.microsoft.omadm.utils.CertUtils      14210    00948    2 cert(s) excluded by criteria:
    2018-11-27T21:10:37.6400000    INFO       com.microsoft.omadm.platforms.android.wifimgr.WifiProfileManager       14210                00948     Skipping Wifi profile <profile ID> because it is pending certificates.
    ```

    I följande exempel visas SCEP-profilen som har angett **Valfritt ändamål** i EKU. Men det har inte angetts i certifikatmallen hos certifikatutfärdaren. Åtgärda problemet genom att lägga till alternativet **Valfritt ändamål** i certifikatmallen. Eller ta bort alternativet **Valfritt ändamål** från SCEP-profilen.

    > [!div class="mx-imgBorder"]
    > ![På Android lägger du till Valfritt ändamål i certifikatmallen hos certifikatutfärdaren](./media/troubleshoot-wi-fi-profiles/android-add-any-purpose-eku.png)

    > [!div class="mx-imgBorder"]
    > ![På Android lägger du till Valfritt ändamål i SCEP-certifikatets konfigurationsprofil i Intune](./media/troubleshoot-wi-fi-profiles/android-any-purpose-scep-device-config-profile.png)

  - Kontrollera att alla certifikat som krävs i den fullständiga certifikatkedjan finns på Android-enheten. Annars kan inte WiFi-profilen installeras på enheten. Mer information finns i [Utfärdare av mellanliggande certifikat saknas](https://developer.android.com/training/articles/security-ssl#MissingCa) (öppnar Androids webbplats).
  - Filtrera Omadmlog med nyckelord för att söka efter information, till exempel vilket certifikat som används i WiFi-profilen och om profilen har tillämpats.

    Använd exempelvis [CMTrace](https://docs.microsoft.com/sccm/core/support/cmtrace) för att läsa loggarna. Använd söksträngen för att filtrera ”wifimgr”:

    > [!div class="mx-imgBorder"]
    > ![Filtrera CMTrace för att söka efter WiFiMgr-konfigurationsprofiler på Android-enheter](./media/troubleshoot-wi-fi-profiles/cmtrace-filter-wifimgr.png)

    Utdatan liknar följande logg:

    > [!div class="mx-imgBorder"]
    > ![Exempel på CMTrace-loggutdata som visar att Intune-konfigurationsfilen för WiFi har tillämpats på enheterna](./media/troubleshoot-wi-fi-profiles/cmtrace-sample-log-output.png)

    Om du ser ett fel i loggen kopierar du tidsstämpeln för felet och avfiltrerar loggen. Använd sedan alternativet ”Sök” med tidsstämpeln för att se vad som hände strax före felet.

### <a name="issue-2-the-wi-fi-profile-is-deployed-to-the-device-but-the-device-cant-connect-to-the-network"></a>Problem 2: WiFi-profilen har distribuerats till enheten, men enheten kan inte ansluta till nätverket

Det här problemet beror vanligtvis på något utanför Intune. Följande uppgifter kan hjälpa dig att förstå och felsöka anslutningsproblem:

- Anslut manuellt till nätverket med ett certifikat som har samma villkor som det som finns i WiFi-profilen.

  Om du kan ansluta, tittar du på certifikategenskaperna i den manuella anslutningen. Uppdatera sedan Intunes WiFi-profil med samma certifikategenskaper.
- Anslutningsfel loggas vanligtvis i Radius-serverloggen. Du bör till exempel kunna se om enheten försökte ansluta till WiFi-profilen.

## <a name="need-more-help"></a>Behöver du mer hjälp?

- Använd [Intunes användarforum](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc) eller [få support från Microsoft](../fundamentals/get-support.md).

- Mer information om WiFi-profiler i Microsoft Intune finns i följande artiklar:

  - Lägga till WiFi-inställningar för enheter som kör [Android](wi-fi-settings-android.md), [iOS](wi-fi-settings-ios.md) samt [Windows 10 och senare](wi-fi-settings-windows.md).
  - [Supporttips – Så här konfigurerar du NDES för SCEP-certifikatdistributioner i Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-How-to-configure-NDES-for-SCEP-certificate/ba-p/455125)
  - Felsök [distribution av SCEP-certifikatprofil](https://support.microsoft.com/help/4526725/troubleshooting-scep-profile-deployment-to-android-devices-in-intune) och [NDES-konfiguration](https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune).

- De senaste nyheterna, informationen och tekniska tipsen finns i de officiella bloggarna:
  - [Microsoft Intune-supportteamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
  - [Bloggen om Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity)

## <a name="next-steps"></a>Nästa steg

[Övervaka dina profiler](device-profile-monitor.md).
