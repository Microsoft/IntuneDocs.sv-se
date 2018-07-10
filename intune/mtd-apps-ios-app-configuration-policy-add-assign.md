---
title: Lägga till och tilldela MTD-appar i Microsoft Intune
titleSuffix: ''
description: Använda Intune för att lägga till MTD-program, Microsoft Authenticator-app och iOS-konfigurationsprincip i Azure-portalen.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 06/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6c7f3229c2cb4c5f3f57d84d348053f25eeeb9c9
ms.sourcegitcommit: f70d6aaea59b52cd0d7bd3008afd243868967fd6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/28/2018
ms.locfileid: "37066223"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Lägg till och tilldela MTD-appar med Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Du kan använda Intune för att lägga till och distribuera MTD-apparna så att slutanvändarna får ett meddelande när ett hot har identifierats i deras mobila enheter och anvisningar för att åtgärda hoten.


## <a name="before-you-begin"></a>Innan du börjar

Följande steg måste utföras i [Azure-portalen](https://portal.azure.com/). Kontrollera att du vet hur man gör för att:

  -   [Lägga till en app i Intune](apps-add.md).
  -   [Lägga till en konfigurationsprincip för iOS-appar i Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
  -   [Tilldela en app med Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).
  -   [ Lägga till en konfigurationsprincip för iOS-appar](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

> [!TIP]
> Intune-företagsportalen fungerar som broker på Android-enheter så att användare kan få sina identiteter kontrollerade av Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Konfigurera Microsoft Authenticator för iOS
För iOS-enheter krävs [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) så att användarnas identiteter kan kontrolleras av Azure AD. Dessutom behövs konfigurationsprincipen för iOS-appar som identifierar MTD iOS-appen för användning med Intune.

Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Microsoft Authenticator-appbutiken](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) i **steg 12** under avsnittet **Konfigurera appinformation**.

## <a name="configure-mtd-applications"></a>Konfigurera MTD-program

Välj det avsnitt som motsvarar din MTD-provider:

  - [Lookout for Work](#configure-lookout-for-work-apps)
  - [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
  - [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
  - [Zimperium](#configure-zimperium-apps)
  - [Pradeo](#configure-pradeo-apps)

### <a name="configure-lookout-for-work-apps"></a>Konfigurera Lookout for Work-appar

- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [Lookout for work-webbadress till Googles appbutik](https://play.google.com/store/apps/details?id=com.lookout.enterprise) i **steg 7**.

- **iOS**

  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [Lookout for Work-webbadress till iOS-appbutiken](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) i **steg 12** under avsnittet **Konfigurera appinformation**.

-   **Lookout for Work-app utanför Apple Store**
    - Du måste signera iOS-appen Lookout for Work på nytt. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. Innan du distribuerar appen måste du signera den på nytt med ditt iOS Enterprise Developer-certifikat.
    - Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/articles/114094038714) på Lookout-webbplatsen.

    - **Aktivera Azure AD-autentisering för användare av Lookout for Work iOS-appen.**

        1. Gå till [Azure-portalen](https://portal.azure.com), logga in med dina autentiseringsuppgifter och gå sedan till appsidan.

        2. Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.

        3. Ersätt **com.lookout.enterprise.yourcompanyname** med ID:t för kundprogrampaketet som du valde när du registrerade IPA.

        4.  Lägg till ytterligare omdirigerings-URI: **&lt;companyportal://code/>** följt av en URL-kodad version av din ursprungliga omdirigerings-URI.

        5.  Lägg till **Delegerad behörighet** till din app.

        > [!NOTE] 
        > Mer information finns i [configure a native client application with Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) (konfigurera ett Native Client-program med Azure AD).

     - **Lägg till IPA-filen för Lookout for Work.**

        - Ladda upp den omsignerade IPA-filen enligt beskrivningen i avsnittet [Add iOS LOB apps with Intune](lob-apps-ios.md) (lägg till iOS LOB-appar med Intune). Du måste också ange den lägsta versionen av operativsystemet till iOS 8.0 eller senare.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Konfigurera Symantec Endpoint Protection Mobile-appar

 - **Android**

    - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). I **steg 7**, använd den här [webbadressen för SEP Mobile-appbutik](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Som **Lägsta operativsystem** väljer du **Android 4.0 (Ice Cream Sandwich)**.

 - **iOS**

    - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). I **steg 12** använd denna [webbadress för SEP Mobile-appbutik](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) under avsnittet **Konfigurera appinformation**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Konfigurera Check Point SandBlast Mobile-appar

 - **Android**

    - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Check Point SandBlast Mobile-appbutiken](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) i **steg 7**.

 - **iOS**

    - Kontakta [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) för att hämta iOS-appen. Läs anvisningarna om [hur man lägger till appar från iOS-butiken i Microsoft Intune](store-apps-ios.md) och använd sedan webbadressen till Apple-butiken i **steg 12** i avsnittet **Konfigurera appinformation**.

### <a name="configure-zimperium-apps"></a>Konfigurera Zimperium-appar

 - **Android**

    - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Zimperium-appbutiken](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) i **steg 7**.

 - **iOS**

    - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Zimperium-appbutiken](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) i **steg 12** under avsnittet **Konfigurera appinformation**.

### <a name="configure-pradeo-apps"></a>Konfigurera Pradeo-appar

 - **Android**

    - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Pradeo-appbutiken](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) i **steg 7**.

 - **iOS**

    - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Pradeo-appbutiken](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) i **steg 12** under avsnittet **Konfigurera appinformation**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Konfigurera dina MTD-appar med en konfigurationsprincip för iOS-appar

### <a name="lookout-for-work-app-configuration-policy"></a>Konfigurationsprincip för Lookout for Work-app

- Skapa konfigurationsprincipen för iOS-appar enligt beskrivningen i avsnittet om att [använda konfigurationsprincipen för iOS-appar](app-configuration-policies-use-ios.md).

### <a name="sep-mobile-app-configuration-policy"></a>Konfigurationsprincip för SEP Mobile-app

-   Använd samma Azure AD-konto som tidigare konfigurerades i [Symantec Endpoint Protection-hanteringskosolen](https://aad.skycure.com), vilket ska vara samma konto som användes för att logga in på den klassiska Intune-portalen.

-   Så här **laddar du ned** konfigurationsprincipen för iOS-appen: 
    -   Gå till [Symantec Endpoint Protection-hanteringskonsol](https://aad.skycure.com) och logga in med dina administratörsautentiseringsuppgifter.

    -   Gå till **Inställningar** och under **Integreringar** väljer du **Intune**. Välj **Val av EMM-integrering**. Välj **Microsoft** och spara sedan ditt val.

    -   Klicka på länken **Integrering av installationsfiler** och spara den genererade \*-ZIP-filen. ZIP-filen innehåller filen ***.plist** som används för att skapa iOS-appens konfigurationsprincip i Intune.

    -   Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till SEP Mobile-konfigurationsprincipen för iOS-appar.

    - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet från filen ***.plist** och klistrar in det i konfigurationsprincipen.

> [!NOTE]
> Om det inte går att hämta filerna, kontakta [Symantec Endpoint Protection Mobile Enterprise Support](https://support.symantec.com/en_US/contact-support.html).

### <a name="check-point-sandblast-mobile-app-configuration-policy"></a>Konfigurationsprincip för Check Point SandBlast Mobile-app

- Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Check Point SandBlast Mobile-konfigurationsprincipen för iOS-appar.
    - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet nedan och klistrar in det i konfigurationsprincipen.

```
<dict><key>MDM</key><string>INTUNE</string></dict>
```

### <a name="zimperium-app-configuration-policy"></a>Konfigurationsprincip för Zimperium-app

- Se anvisningarna för att [använda Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Zimperium-konfigurationsprincipen för iOS-appar.
    - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet nedan och klistrar in det i konfigurationsprincipen.

```
<dict>
<key>provider</key><string>Intune</string>
<key>userprincipalname</key><string>{{userprincipalname}}</string>
<key>deviceid</key>
<string>{{deviceid}}</string>
<key>serialnumber</key>
<string>{{serialnumber}}</string>
<key>udidlast4digits</key>
<string>{{udidlast4digits}}</string>
</dict>
```

## <a name="assign-apps-to-groups"></a>Tilldela appar till grupper

- Det här steget gäller för alla MTD-partner. Se anvisningarna för [tilldelning av appar till grupper med Intune](apps-deploy.md).

## <a name="next-steps"></a>Nästa steg

- [Konfigurera enhetsefterlevnadsprincipen för MTD](mtd-device-compliance-policy-create.md)
