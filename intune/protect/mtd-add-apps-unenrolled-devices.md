---
title: Lägga till Mobile Threat Defense-appar till oregistrerade enheter
titleSuffix: Microsoft Intune
description: Lägg till Mobile Threat Defense-appar till enhetsanvändares oregistrerade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8dd7127594a0e23c85b9f8141ce6d398d9a447a
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794465"
---
# <a name="add-mobile-threat-defense-apps-to-unenrolled-devices"></a>Lägga till Mobile Threat Defense-appar till oregistrerade enheter

Vid användning av Intune-appskyddsprinciper Mobile Threat Defense utför Intune som standard arbetet med att vägleda slutanvändaren på enheten för att installera och logga in på alla appar som krävs för att aktivera anslutningarna till relevanta tjänster.

Slutanvändare behöver Microsoft Authenticator (iOS) för att registrera sin enhet samt Mobile Threat Defense (för både Android och iOS) för att få meddelanden när ett hot identifieras på de mobila enheterna och för att få vägledning om hur hoten kan åtgärdas.

Om du vill kan du använda Intune för att lägga till och distribuera Microsoft Authenticator och även MTD-appar (Mobile Threat Defense).

> [!NOTE] 
> Den här artikeln gäller för alla Mobile Threat Defense-partner som har stöd för appskyddsprinciper: Better Mobile (Android), Zimperium (iOS) samt Lookout for Work (Android/iOS).
> 
> För oregistrerade enheter **behöver du inte någon iOS-appskyddsprincip** som konfigurerar Mobile Threat Defense för iOS-appar som du använder med Intune. Detta är en viktig skillnad jämfört med Intune-registrerade enheter. 

## <a name="configure-microsoft-authenticator-for-ios-via-intune-optional"></a>Konfigurera Microsoft Authenticator för iOS via Intune (valfritt)
Vid användning av Intune-appskyddsprinciper med Mobile Threat Defense vägleder Intune slutanvändaren för att installera, logga in på och registrera sin enhet med Microsoft Authenticator (iOS).

Om du dock vill göra appen tillgänglig för slutanvändare via Intune-företagsportalen kan du läsa anvisningarna för att [lägga till iOS-butiksappar till Microsoft Intune](../apps/store-apps-ios.md). Använd denna [Microsoft Authenticator – iOS App Store-URL](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) när du slutför avsnittet **Konfigurera appinformation**. Glöm inte att [tilldela appar till grupper med Intune](../apps/apps-deploy.md) som sista steg.

> [!NOTE] 
> För iOS-enheter krävs [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) så att användarnas identiteter kan kontrolleras av Azure AD. Intune-företagsportalen fungerar som broker på Android-enheter så att användare kan få sina identiteter kontrollerade av Azure AD.

## <a name="making-mobile-threat-defense-apps-available-via-intune-optional"></a>Göra Mobile Threat Defense-appar tillgängliga via Intune (valfritt)
Vid användning av Intune-appskyddsprinciper med Mobile Threat Defense vägleder Intune slutanvändaren för att installera och logga in på den Mobile Threat Defense-klientapp som krävs. 

Om du dock vill göra appen tillgänglig för slutanvändare via Intune-företagsportalen kan du följa stegen nedan i [Azure-portalen](https://portal.azure.com/). Kontrollera att du vet hur man gör för att:

- [Lägga till en app i Intune](../apps/apps-add.md).
- [Tilldela en app med Intune](../apps/apps-deploy.md).

### <a name="making-lookout-for-work-available-to-end-users"></a>Göra Lookout for Work tillgängligt för slutanvändare
- **Android**  
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](../apps/store-apps-android.md). Använd denna [Lookout for Work – Play Store-URL](https://play.google.com/store/apps/details?id=com.lookout.enterprise) när du slutför avsnittet **Konfigurera appinformation**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](../apps/store-apps-ios.md). Använd denna [Lookout for Work – iOS App Store-URL](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) när du slutför avsnittet **Konfigurera appinformation**.

<!-- ### Making Symantec Endpoint Protection Mobile available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). When completing the **Configure app information** section, use this [SEP Mobile app store URL](https://play.google.com/store/apps/details?id=com.skycure.skycure). For **Minimum operating system**, select **Android 4.0 (Ice Cream Sandwich)**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [SEP Mobile - App Store URL](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) when completing the **Configure app information** section.

### Making Check Point SandBlast Mobile available to end users
- **Android**  
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Check Point SandBlast Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) when completing the **Configure app information** section. 

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Check Point SandBlast Mobile - App Store URL](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) when completing the **Configure app information** section. -->

### <a name="making-zimperium-available-to-end-users"></a>Göra Zimperium tillgängligt för slutanvändare
<!-- - **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Zimperium - Play Store URL](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) when completing the **Configure app information** section. -->
- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](../apps/store-apps-ios.md). Använd denna [Zimperium – App Store-URL](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) när du slutför avsnittet **Konfigurera appinformation**.
 
<!-- ### Making Pradeo available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Pradeo - Play Store URL](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Pradeo - App Store URL](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) when completing the **Configure app information** section. -->

### <a name="making-better-mobile-available-to-end-users"></a>Göra Better Mobile tillgängligt för slutanvändare 
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](../apps/store-apps-android.md). Använd denna [Active Shield – Play Store-URL](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) när du slutför avsnittet **Konfigurera appinformation**.
<!-- - **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) when completing the **Configure app information** section. -->

<!-- ### Making Sophos available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Sophos - Play Store URL](https://play.google.com/store/apps/details?id=com.sophos.smsec) when completing the **Configure app information** section.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [ActiveShield - App Store URL](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) when completing the **Configure app information** section.

### Making Wandera available to end users
- **Android**
  - See the instructions for [adding Android store apps to Microsoft Intune](../apps/store-apps-android.md). Use this [Wandera Mobile - Play Store URL](https://play.google.com/store/apps/details?id=com.wandera.android) when completing the **Configure app information** section. For **Minimum operating system**, select **Android 5.0**.

- **iOS**
  - See the instructions for [adding iOS store apps to Microsoft Intune](../apps/store-apps-ios.md). Use this [Wandera Mobile - - App Store URL](https://itunes.apple.com/app/wandera/id605469330) when completing the **Configure app information** section. -->

## <a name="next-steps"></a>Nästa steg  

- [Aktivera Mobile Threat Defense-anslutningsprogrammet i Intune för oregistrerade enheter](~/protect/mtd-enable-unenrolled-devices.md)

