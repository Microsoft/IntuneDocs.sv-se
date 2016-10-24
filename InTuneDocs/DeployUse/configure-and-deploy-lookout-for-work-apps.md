---
title: Distribuera Lookout for work-appen | Microsoft Intune
description: "Konfigurera och distribuera Lookout for work-appar för Android."
author: karthikaraman
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4a69be67c3ef9f028c77c738de5f1fcbd59a8d33
ms.openlocfilehash: 2c626cb0a36c38c7b5deeca0ff1e902018540634


---

# Konfigurera och distribuera Lookout for work-appar
Den här artikeln förklarar hur du konfigurerar och distribuerar Lookout for Work-appen till Android- och iOS-enheter.

## Android (Google Play Store-app)

* **Steg ett:** Överför Android-appen Lookout for Work i [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) enligt beskrivningen i avsnittet [Add apps for mobile devices in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune) (Lägg till appar för mobila enheter i Microsoft Intune).
>[!NOTE]
> Klicka inte på rutan för att kräva en hanterad webbläsare.

![Skärmbild av appsidan i Intune-konsolen som visar Lookout for work-apparna i listan](../media/mtp/lookout-app-listed-intune-console.png)

* **Steg två:** Distribuera appen till användare. Välj Lookout for Work-appen som visas på skärmbilden ovan och välj **Hantera distribuering**.

  Du måste markera samma användare som har lagts till i alternativet Registreringshantering i Lookout-konsolen.  Se steg 3 i [avsnittet om att konfigurera prenumerationen med Lookout-skydd mot enhetshot](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) för information om hur du lägger till användargrupper i Lookout MTP.
>[!IMPORTANT]
> Guiden för att distribuera Intune-appen känner inte till Azure AD-användargrupper utan använder Intune-användargrupper istället. Därför måste du skapa en Intune-användargrupp baserat på Azure AD-användargruppen som har registrerats i Lookout-konsolen enligt beskrivningarna i [den här](plan-your-user-and-device-groups.md) artikeln.

Välj alternativet **Nödvändig installation** för att kräva att Lookout-appen installeras på användarens enhet.


## iOS (Företagssignerad version av Lookout-appen)

* **Steg ett:** Kontrollera att **iOS management** (iOS-hantering) är inställt på enheten. Anvisningar om hur du ställer in din enhet för iOS-hantering finns i [Set up iOS and Mac device management](set-up-ios-and-mac-management-with-microsoft-intune.md) (Konfigurera iOS- och Mac-enhetshantering).

* **Steg två:** **Omsignera** iOS-appen Lookout for Work. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. **Before distributing the app** (Innan du distribuerar appen) måste du omsignera appen med din iOS Enterprise Developer-certifikat. Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/en-us/articles/114094038714) på Lookout-platsen.


* **Steg tre:** Aktivera Azure Active Directory-autentisering för iOS-användare genom att göra följande:
  1.  Logga in på [hanteringsportalen för Azure Active Directory](https://manage.windowsazure.com) och gå till programsidan.
  2.  Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.
  ![Skärmbild av dialogrutan Lägg till appar med alternativet för interna klientprogram](../media/mtp/aad-add-app.png)

  3. Ersätt **com.lookout.enterprise.yourcompanyname** med ID:t för kundprogrampaketet som du valde när du registrerade IPA.
  4.  Lägg till ytterligare omdirigerings-URI: **&lt;companyportal://code/ >** följt av en URL-kodad version av din ursprungliga omdirigerings-URI.
  5.  Lägg till **Delegerad behörighet** till din app.

  Mer information finns i [Configure a native client application](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application) (Konfigurera ett internt klientprogram).


* **Steg fyra:** Ladda upp den omsignerade .ipa-filen enligt beskrivningen i artikeln [Lägg till appar för mobila enheter i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune). Ange den lägsta operativsystemsversionen till iOS 8.0 eller senare.

  ![Skärmbild av sidan appar i Intune-administratörskonsolen där Lookout for Work-appen visas i listan över appar](../media/mtp/ios-app-uploaded-intune.png)

* **Steg fem:** Skapa en konfigurationsprincip för hanterade appar enligt beskrivningen i avsnittet [Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

  ![skärmbild av guiden skapa en ny princip med appkonfigurationsprincipen för iOS 8.0 eller senare markerad](../media/mtp/ios-app-config.png)

* **Steg sex:** Välj Lookout for Work-appen och markera **Hantera distribuering** **för att distribuera appen till användare**.

  Du måste markera samma användare som har lagts till i alternativet Registreringshantering i Lookout-konsolen.  Se steg 3 i [avsnittet om att konfigurera prenumerationen med Lookout-skydd mot enhetshot](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) för information om hur du lägger till användargrupper i Lookout MTP.
>[!IMPORTANT]
> Guiden för att distribuera Intune-appen känner inte till Azure AD-användargrupper utan använder Intune-användargrupper istället. Därför måste du skapa en Intune-användargrupp baserat på Azure AD-användargruppen som har registrerats i Lookout-konsolen enligt beskrivningarna i [den här](plan-your-user-and-device-groups.md) artikeln.

Välj alternativet **Nödvändig installation** för att kräva att Lookout-appen installeras på användarens enhet.

## Vad händer när den distribuerade appen öppnas på enheten




När användaren öppnar Lookout for Work på enheten uppmanas de att aktivera appen och att välja alternativet att logga in med Azure Active Directory. En detaljerad genomgång som visar vad slutanvändaren ska göra finns i följande avsnitt:

* [Du uppmanas att installera Lookout for Work på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Du måste åtgärda ett hot som Lookout for Work har hittat på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Nästa steg
* [Aktivera regeln för skydd mot enhetshot i policyn för efterlevnad](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Oct16_HO2-->


