---
title: "Lägg till och tilldela MTD-appar i Intune"
titleSuffix: Intune on Azure
description: "Lägg till MTD-appar, Microsoft Authenticator-appen och iOS-konfigurationsprincipen i Intune på Azure"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00356258-76a8-4a84-9cf5-64ceedb58e72
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7b3fb86648a86b161eadfc071bdacbfd4ea0222f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="add-and-assign-mobile-threat-defense-mtd-apps-with-intune"></a>Lägg till och tilldela MTD-appar med Intune

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

### <a name="skycure-app-for-android"></a>Skycure-app för Android

- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [webbadress till Skycure-appbutiken](https://play.google.com/store/apps/details?id=com.skycure.skycure) i **steg 7**.

### <a name="skycure-app-for-ios"></a>Skycure-app för iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Skycure-appbutiken](https://itunes.apple.com/us/app/skycure/id695620821?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

### <a name="microsoft-authenticator-app-for-ios"></a>Microsoft Authenticator-appen för iOS

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [webbadress till Microsoft Authenticator-appbutiken](https://itunes.apple.com/us/app/microsoft-authenticator/id983156458?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

### <a name="lookout-for-work-android-app"></a>Android-appen Lookout for work

- Se anvisningarna för att [lägga till Android Store-appar i Microsoft Intune](store-apps-android.md). Använd denna [Lookout for work-webbadress till Googles appbutik](https://play.google.com/store/apps/details?id=com.lookout.enterprise) i **steg 7**.

### <a name="lookout-for-work-ios-app"></a>iOS-appen Lookout for Work

- Läs anvisningarna för att [lägga till iOS Store-appar i Microsoft Intune](store-apps-ios.md). Använd denna [Lookout for Work-webbadress till iOS-appbutiken](https://itunes.apple.com/us/app/lookout-for-work/id997193468?mt=8) i **steg 5** under avsnittet **Configure app information** (konfigurera appinformation).

### <a name="lookout-for-work-app-outside-the-apple-store"></a>Lookout for Work-app utanför Apples appbutik

Du måste signera iOS-appen Lookout for Work på nytt. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. Innan du distribuerar appen måste du signera den på nytt med ditt iOS Enterprise Developer-certifikat.

Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/articles/114094038714) på Lookout-webbplatsen.

#### <a name="enable-azure-ad-authentication-for-lookout-for-work-ios-app"></a>Aktivera Azure AD-autentisering för Lookout for Work iOS-appen

Aktivera Azure Active Directory-autentisering för iOS-användare genom att göra följande:

1. Gå till [Azure-portalen](https://portal.sazure.com), logga in med dina autentiseringsuppgifter och gå sedan till appsidan.
  
2. Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.

3. Ersätt **com.lookout.enterprise.yourcompanyname** med ID:t för kundprogrampaketet som du valde när du registrerade IPA.

4.  Lägg till ytterligare omdirigerings-URI: **&lt;companyportal://code/>** följt av en URL-kodad version av din ursprungliga omdirigerings-URI.

5.  Lägg till **Delegerad behörighet** till din app.

    > [!NOTE] 
    > Mer information finns i [configure a native client application with Azure AD](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) (konfigurera ett Native Client-program med Azure AD).

#### <a name="add-the-lookout-for-work-ipa-file"></a>Lägg till IPA-filen för Lookout for Work

- Ladda upp den omsignerade IPA-filen enligt beskrivningen i avsnittet [Add iOS LOB apps with Intune](lob-apps-ios.md) (lägg till iOS LOB-appar med Intune). Du måste också ange den lägsta versionen av operativsystemet till iOS 8.0 eller senare.

## <a name="to-associate-the-mtd-app-with-an-ios-app-configuration-policy"></a>Associera MTD-appen med en konfigurationsprincip för iOS-appar

### <a name="for-skycure"></a>För Skycure

-   Använd samma Azure AD-konto som tidigare konfigurerades i Skycure Management Console, vilket ska vara samma konto som används för att logga in på den klassiska Intune-konsolen.

-   Skycure-integreringsfilen måste vara klar att använda. Detta är ZIP-filen som tidigare hämtades från Skycure Management Console. Den innehåller filen **skycure\_configuration.plist** med iOS-appens parametrar för konfigurationsprincipen.

- Se anvisningarna för [användning av Microsoft Intune-appkonfigurationsprinciper för iOS](app-configuration-policies-use-ios.md) för att lägga till Skycure-konfigurationsprincipen för iOS-appar.
    - I steg 8 använder du alternativet **Ange XML-data**, kopierar innehållet från filen **skycure_configuration.plist** och klistrar in det i konfigurationsprincipen.

Du kan också kopiera innehållet i **skycure_configuration.plist** härifrån:

```
<dict>
    <key>MdmType</key>
    <string>Intune</string>
    <key>UserEmail</key>
    <string>{{userprincipalname}}</string>
</dict>

```
### <a name="for-lookout"></a>För Lookout

- Skapa konfigurationsprincipen för iOS-appar enligt beskrivningen i avsnittet om att [använda konfigurationsprincipen för iOS-appar](app-configuration-policies-use-ios.md).

## <a name="to-assign-mtd-apps"></a>Tilldela MTD appar

- Se anvisningarna för [tilldelning av appar till grupper med Intune](apps-deploy.md).

## <a name="next-steps"></a>Nästa steg

[Ställ in Skycure-integrering med Intune](skycure-mtd-connector-integration.md)
[Ställ in Lookout-integrering med Intune](lookout-mtd-connector-integration.md)
