---
title: Lägga till och tilldela MTD-appar i Microsoft Intune
titleSuffix: Microsoft Intune
description: Använda Intune för att lägga till MTD-program, Microsoft Authenticator-app och iOS-konfigurationsprincip i Azure-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: davera
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6065fda71688909dd7fcbc6ef1909e3d3ab36b8
ms.sourcegitcommit: 6bba9f2ef4d1ec699f5713a4da4f960e7317f1cd
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67407119"
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Lägg till och tilldela MTD-appar med Intune  

> [!NOTE] 
> Den här artikeln gäller alla Mobile Threat Defense-partner.

Du kan använda Intune för att lägga till och distribuera MTD-apparna (Mobile Threat Defense) så att slutanvändarna får ett meddelande när ett hot har identifierats i deras mobila enheter och anvisningar för att åtgärda hoten.

## <a name="before-you-begin"></a>Innan du börjar    
Följande steg måste utföras i [Azure-portalen](https://portal.azure.com/). Kontrollera att du vet hur man gör för att:

-   [Lägga till en app i Intune](apps-add.md).
-   [Lägga till en konfigurationsprincip för iOS-appar i Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).
-   [Tilldela en app med Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

> [!TIP]
> Intune-företagsportalen fungerar som broker på Android-enheter så att användare kan få sina identiteter kontrollerade av Azure AD.

## <a name="configure-microsoft-authenticator-for-ios"></a>Konfigurera Microsoft Authenticator för iOS  
För iOS-enheter krävs [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) så att användarnas identiteter kan kontrolleras av Azure AD. Dessutom behövs en konfigurationsprincip för iOS-appar som konfigurerar MTD iOS-appen för användning med Intune.

Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Microsoft Authenticator-appbutiken](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) i **steg 12** under avsnittet **Konfigurera appinformation**.

## <a name="configure-mtd-applications"></a>Konfigurera MTD-program  
Välj det avsnitt som motsvarar din MTD-provider:

- [Lookout for Work](#configure-lookout-for-work-apps)
- [Symantec Endpoint Protection Mobile (SEP Mobile)](#configure-symantec-endpoint-protection-mobile-apps)
- [Check Point SandBlast Mobile](#configure-check-point-sandblast-mobile-apps)
- [Zimperium](#configure-zimperium-apps)
- [Pradeo](#configure-pradeo-apps)
- [Better Mobile](#configure-better-mobile-apps)
- [Sophos Mobile](#configure-sophos-apps)
- [Wandera](#configure-wandera-apps)

### <a name="configure-lookout-for-work-apps"></a>Konfigurera Lookout for Work-appar  
- **Android**  
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [Lookout for work-webbadress till Googles appbutik](https://play.google.com/store/apps/details?id=com.lookout.enterprise) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [Lookout for Work-webbadressen för iOS-appbutiken](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) i **steg 11** som **appbutiksadress**.

- **Lookout for Work-app utanför Apple Store**  
  - Du måste signera iOS-appen Lookout for Work på nytt. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. Innan du distribuerar appen måste du signera den på nytt med ditt iOS Enterprise Developer-certifikat.  
  - Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/articles/114094038714) på Lookout-webbplatsen.

  - **Aktivera Azure AD-autentisering för användare av Lookout for Work iOS-appen.**

    1. Gå till [Azure-portalen](https://portal.azure.com), logga in med dina autentiseringsuppgifter och gå sedan till appsidan.

    2. Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.

    3. Ersätt **com.lookout.enterprise.yourcompanyname** med ID:t för kundprogrampaketet som du valde när du registrerade IPA.

    4. Lägg till ytterligare omdirigerings-URI: **&lt;companyportal://code/>** följt av en URL-kodad version av din ursprungliga omdirigerings-URI.

    5. Lägg till **Delegerad behörighet** till din app.

    > [!NOTE] 
    > Mer information finns i [configure a native client application with Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) (konfigurera ett Native Client-program med Azure AD).

  - **Lägg till IPA-filen för Lookout for Work.**

    - Ladda upp den omsignerade IPA-filen enligt beskrivningen i artikeln [Add iOS LOB apps with Intune](lob-apps-ios.md) (Lägg till iOS LOB-appar med Intune). Du måste också ange den lägsta versionen av operativsystemet till iOS 8.0 eller senare.

### <a name="configure-symantec-endpoint-protection-mobile-apps"></a>Konfigurera Symantec Endpoint Protection Mobile-appar  
- **Android**
   - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). I **steg 7**, använd den här [webbadressen för SEP Mobile-appbutik](https://play.google.com/store/apps/details?id=com.skycure.skycure).  Som **Lägsta operativsystem** väljer du **Android 4.0 (Ice Cream Sandwich)** .

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [SEP-webbadressen för mobilappbutiken](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) i **steg 11** som **appbutiksadress**.

### <a name="configure-check-point-sandblast-mobile-apps"></a>Konfigurera Check Point SandBlast Mobile-appar  
- **Android**  
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Check Point SandBlast Mobile-appbutiken](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [Check Point SandBlast-webbadressen för mobilappbutiken](https://apps.apple.com/us/app/sandblast-mobile-protect/id1006390797) i **steg 11** som **appbutiksadress**.  

### <a name="configure-zimperium-apps"></a>Konfigurera Zimperium-appar  
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Zimperium-appbutiken](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [Zimperium-webbadressen för appbutiken](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) i **steg 11** som **appbutiksadress**.  
 
### <a name="configure-pradeo-apps"></a>Konfigurera Pradeo-appar  
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Pradeo-appbutiken](https://play.google.com/store/apps/details?id=net.pradeo.service&hl=en_US) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [Pradeo-webbadressen för appbutiken](https://itunes.apple.com/us/app/pradeo-agent/id547979360?mt=8) i **steg 11** som **appbutiksadress**.

### <a name="configure-better-mobile-apps"></a>Konfigurera Better Mobile-appar  
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till App Store för Active Shield](https://play.google.com/store/apps/details?id=com.better.active.shield.enterprise) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här [ActiveShield-webbadressen för appbutiken](https://itunes.apple.com/us/app/activeshield/id980234260?mt=8&uo=4) i **steg 11** som **appbutiksadress**.

### <a name="configure-sophos-apps"></a>Konfigurera Sophos-appar  
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Sophos-appbutiken](https://play.google.com/store/apps/details?id=com.sophos.smsec) i **steg 7**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd den här för [ActiveShield-webbadressen för appbutiken](https://itunes.apple.com/us/app/sophos-mobile-security/id1086924662?mt=8) i **steg 11** som **appbutiksadress**.

### <a name="configure-wandera-apps"></a>Konfigurera Wandera-appar  
 
- **Android**
  - Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd den här [webbadressen för Wandera mobilappbutiken](https://play.google.com/store/apps/details?id=com.wandera.android) i **steg 7**. Som **Lägsta operativsystem** väljer du **Android 5.0**.

- **iOS**
  - Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](https://docs.microsoft.com/intune/store-apps-ios). Använd den här [webbadressen för Wandera-mobilappbutiken](https://itunes.apple.com/app/wandera/id605469330) i **steg 11** som **appbutiksadress**.

## <a name="configure-your-mtd-apps-with-an-ios-app-configuration-policy"></a>Konfigurera dina MTD-appar med en konfigurationsprincip för iOS-appar  

### <a name="lookout-for-work-app-configuration-policy"></a>Konfigurationsprincip för Lookout for Work-app  
- Skapa konfigurationsprincipen för iOS-appar enligt beskrivningen i artikeln om att [använda konfigurationsprincipen för iOS-appar](app-configuration-policies-use-ios.md).

### <a name="sep-mobile-app-configuration-policy"></a>Konfigurationsprincip för SEP Mobile-app  
- Använd samma Azure AD-konto som tidigare konfigurerades i [Symantec Endpoint Protection-hanteringskonsolen](https://aad.skycure.com), vilket ska vara samma konto som användes för att logga in på den klassiska Intune-portalen.

- **Ladda ned** konfigurationsprincipsfilen för iOS-appen: 
  - Gå till [Symantec Endpoint Protection-hanteringskonsol](https://aad.skycure.com) och logga in med dina administratörsautentiseringsuppgifter.

  - Gå till **Inställningar** och under **Integreringar** väljer du **Intune**. Välj **Val av EMM-integrering**. Välj **Microsoft** och spara sedan ditt val.

  - Klicka på länken **Integrering av installationsfiler** och spara den genererade \*-ZIP-filen. ZIP-filen innehåller filen * **.plist** som används för att skapa iOS-appens konfigurationsprincip i Intune.

  - Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till SEP Mobile-konfigurationsprincipen för iOS-appar.

  - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet från filen * **.plist** och klistrar in det i konfigurationsprincipen.

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

### <a name="pradeo-app-configuration-policy"></a>Konfigurationsprincip för Pradeo-appar  
Pradeo stöder inte programkonfigurationsprincipen på iOS.  För att istället få en konfigurerad app kan du arbeta med Pradeo för att implementera anpassade IPA- eller APK-filer som är förkonfigurerade med de inställningar som du önskar.

### <a name="better-mobile-app-configuration-policy"></a>Konfigurationsprincip för Better Mobile-appen  
- Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) när du ska lägga till en konfigurationsprincip för Better Mobile iOS-appen.
  - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet nedan och klistrar in det i konfigurationsprincipen. Ersätt webbadressen `https://client.bmobi.net` med rätt konsoladress.

```
<dict>
<key>better_server_url</key>
<string>https://client.bmobi.net</string>
<key>better_udid</key>
<string>{{aaddeviceid}}</string>
<key>better_user</key>
<string>{{userprincipalname}}</string>
</dict>
```

### <a name="sophos-mobile-app-configuration-policy"></a>Konfigurationsprincip för Sophos Mobile-appen  
Skapa konfigurationsprincipen för iOS-appar enligt beskrivningen i artikeln om att [använda konfigurationsprincipen för iOS-appar](app-configuration-policies-use-ios.md).

### <a name="wandera-app-configuration-policy"></a>Konfigurationsprincip för Wandera-appar  
Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Wandera-konfigurationsprincipen för iOS-appar.
- På **steg 8** använder du alternativet **Ange XML-data**. Logga in på din RADAR Wandera-portal och bläddra till **Inställningar** > **EMM-integrering** > **App Push**. Välj **Intune** och kopiera innehållet nedan och klistra in det i konfigurationsprincipen.  

  ```
  <dict><key>secretKey</key>
  <string>SeeRADAR</string>
  <key>apiKey</key>
  <string> SeeRADAR </string>
  <key>customerId</key>
  <string> SeeRADAR </string>
  <key>email</key>
  <string>{{mail}}</string>
  <key>firstName</key>
  <string>{{username}}</string>
  <key>lastName</key>
  <string></string>
  <key>activationType</key>
  <string>PROVISION_THEN_AWP</string></dict>  
  ```

## <a name="assign-apps-to-groups"></a>Tilldela appar till grupper  
- Det här steget gäller för alla MTD-partner. Se anvisningarna för [tilldelning av appar till grupper med Intune](apps-deploy.md).

## <a name="next-steps"></a>Nästa steg  
- [Konfigurera enhetsefterlevnadsprincipen för MTD](mtd-device-compliance-policy-create.md)
