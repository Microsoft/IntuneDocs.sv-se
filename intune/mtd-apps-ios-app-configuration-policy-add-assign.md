---
title: "Lägg till och tilldela MTD-appar i Intune"
titleSuffix: Azure portal
description: "Lägg till MTD-program, Microsoft Authenticator-program och iOS-konfigurationsprincipen med Intune i Azure-portalen"
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7afe03c635b63053ef0cc0f622bc9324f31ec68b
ms.sourcegitcommit: eac89306d1391a6d3ae1179612b0820b19c2baa6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/23/2018
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Lägg till och tilldela MTD-appar med Intune

> [!NOTE] 
> Detta avsnitt gäller alla Mobile Threat Defense-partner.

Du kan använda Intune för att lägga till och distribuera MTD-apparna så att slutanvändarna får ett meddelande när ett hot har identifierats i deras mobila enheter och anvisningar för att åtgärda hoten.

För iOS-enheter krävs [Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) så att användarnas identiteter kan kontrolleras av Azure AD. Dessutom behövs konfigurationsprincipen för iOS-appar som identifierar MTD iOS-appen för användning med Intune.

> [!TIP]
> Intune-företagsportalen fungerar som broker på Android-enheter så att användare kan få sina identiteter kontrollerade av Azure AD.

## <a name="before-you-begin"></a>Innan du börjar

-   Följande steg måste utföras i [Azure-portalen](https://portal.azure.com/).

-   Kontrollera att du vet hur man gör för att:

    -   [Lägga till en app i Intune](apps-add.md).

    -   [Lägga till en konfigurationsprincip för iOS-appar i Intune](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

    -   [Tilldela en app med Intune](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune).

    -   [ Lägga till en konfigurationsprincip för iOS-appar](https://docs.microsoft.com/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

## <a name="to-add-apps"></a>Så här lägger du till appar

### <a name="all-mtd-partners"></a>Alla MTD-partner

#### <a name="microsoft-authenticator-app-for-ios"></a>Microsoft Authenticator-appen för iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Microsoft Authenticator-appbutiken](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

### <a name="lookout"></a>Lookout

#### <a name="android"></a>Android
- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [Lookout for work-webbadress till Googles appbutik](https://play.google.com/store/apps/details?id=com.lookout.enterprise) i **steg 7**.

#### <a name="ios"></a>iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [Lookout for Work-webbadress till iOS-appbutiken](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

#### <a name="lookout-for-work-app-outside-the-apple-store"></a>Lookout for Work-app utanför Apples appbutik

Du måste signera iOS-appen Lookout for Work på nytt. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. Innan du distribuerar appen måste du signera den på nytt med ditt iOS Enterprise Developer-certifikat.

Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/articles/114094038714) på Lookout-webbplatsen.

##### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Aktivera Azure AD-autentisering för Lookout for Work iOS-appen

Aktivera Azure Active Directory-autentisering för iOS-användare genom att göra följande:

1. Gå till [Azure-portalen](https://portal.azure.com), logga in med dina autentiseringsuppgifter och gå sedan till appsidan.
  
2. Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.

3. Ersätt **com.lookout.enterprise.yourcompanyname** med ID:t för kundprogrampaketet som du valde när du registrerade IPA.

4.  Lägg till ytterligare omdirigerings-URI: **&lt;companyportal://code/>** följt av en URL-kodad version av din ursprungliga omdirigerings-URI.

5.  Lägg till **Delegerad behörighet** till din app.

    > [!NOTE] 
    > Mer information finns i [configure a native client application with Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) (konfigurera ett Native Client-program med Azure AD).

##### <a name="add-the-lookout-for-work-ipa-file"></a>Lägg till IPA-filen för Lookout for Work

- Ladda upp den omsignerade IPA-filen enligt beskrivningen i avsnittet [Add iOS LOB apps with Intune](lob-apps-ios.md) (lägg till iOS LOB-appar med Intune). Du måste också ange den lägsta versionen av operativsystemet till iOS 8.0 eller senare.

### <a name="skycure"></a>Skycure

#### <a name="android"></a>Android

- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Skycure-appbutiken](https://play.google.com/store/apps/details?id=com.skycure.skycure) i **steg 7**.

#### <a name="ios"></a>iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Skycure-appbutiken](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

### <a name="check-point-sandblast-mobile"></a>Check Point SandBlast Mobile

#### <a name="android"></a>Android

- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Check Point SandBlast Mobile-appbutiken](https://play.google.com/store/apps/details?id=com.lacoon.security.fox) i **steg 7**.

#### <a name="ios"></a>iOS

- Kontakta [Check Point SandBlast Mobile](https://www.checkpoint.com/products/sandblast-mobile/) för att hämta iOS-appen. Läs anvisningarna om [hur man lägger till appar från iOS-butiken i Microsoft Intune](store-apps-ios.md) och använd sedan webbadressen till Apple-butiken i **steg 5** i avsnittet **Configure app information** (Konfigurera appinformation).

### <a name="zimperium"></a>Zimperium

#### <a name="android"></a>Android

- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Zimperium-appbutiken](https://play.google.com/store/apps/details?id=com.zimperium.zips&hl=en) i **steg 7**.

#### <a name="ios"></a>iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Zimperium-appbutiken](https://itunes.apple.com/us/app/zimperium-zips/id1030924459?mt=8) i **steg 5** under avsnittet **Konfigurera appinformation**.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Associera MTD-appen med en konfigurationsprincip för iOS-appar

### <a name="for-lookout"></a>För Lookout

- Skapa konfigurationsprincipen för iOS-appar enligt beskrivningen i avsnittet om att [använda konfigurationsprincipen för iOS-appar](app-configuration-policies-use-ios.md).

### <a name="for-skycure"></a>För Skycure

-   Använd samma Azure AD-konto som tidigare konfigurerades i [Skycure Management Console](https://aad.skycure.com), vilket ska vara samma konto som användes för att logga in på den klassiska Intune-portalen.

-   Så här **laddar du ned** konfigurationsprincipen för iOS-appen: 
    -   Gå till [Skycures hanteringskonsol](https://aad.skycure.com) och logga in med dina administratörsautentiseringsuppgifter.
    
    -   Gå till **Inställningar** &gt; **Integrering med enhetshantering** &gt; **Val av EMM-integrering**, välj **Microsoft Intune** och spara sedan ditt val.
    
    -   Klicka på länken **Integrering av installationsfiler** och spara den genererade \*ZIP-filen. ZIP-filen innehåller filen **skycure\_configuration.plist**, som används för att skapa iOS-appens konfigurationsprincip i Intune.
    
    -   Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Skycure-konfigurationsprincipen för iOS-appar.
    
    - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet från filen **skycure_configuration.plist** och klistrar in det i konfigurationsprincipen.

Du kan också kopiera innehållet i **skycure_configuration.plist** härifrån:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-check-point-sandblast-mobile"></a>För Check Point SandBlast Mobile

- Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Check Point SandBlast Mobile-konfigurationsprincipen för iOS-appar.
    - I **steg 8** använder du alternativet **Ange XML-data**, kopierar innehållet nedan och klistrar in det i konfigurationsprincipen.

```
<dict><key>MDM</key><string>INTUNE</string></dict>

```

### <a name="for-zimperium"></a>För Zimperium

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

## <a name="to-assign-apps-all-mtd-partners"></a>Så här tilldelar du appar (alla MTD partner)

- Se anvisningarna för [tilldelning av appar till grupper med Intune](apps-deploy.md).

## <a name="next-steps"></a>Nästa steg

- [Lägg till enhetsefterlevnadsprincip för MTD](mtd-device-compliance-policy-create.md)
