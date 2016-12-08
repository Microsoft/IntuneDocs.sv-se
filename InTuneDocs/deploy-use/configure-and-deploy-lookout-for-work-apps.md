---
title: Distribuera Lookout for work-appen | Microsoft Intune
description: "Konfigurera och distribuera Lookout for work-appar för Android."
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: 646bd62dcf95b37ce9154e4852612b17ab71f954


---

# <a name="configure-and-deploy-lookout-for-work-apps"></a>Konfigurera och distribuera Lookout for work-appar
Den här artikeln förklarar hur du konfigurerar och distribuerar Lookout for Work-appen till Android- och iOS-enheter.

## <a name="android-google-play-store-app"></a>Android (Google Play Store-app)

* **Steg 1**: I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) går du till **Appar** och väljer **Lägg till appar**.   
* **Steg 2**: På sidan  **Programvaruinstallation** för utgivaren väljer du **Extern länk** och anger följande URL: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Klicka inte på rutan för att kräva en hanterad webbläsare.

* **Steg 3**: Fyll i följande på sidan **Programvarubeskrivning**:
  * **Utgivare:** Lookout Mobile Security
  * **Namn:** Lookout for Work
  * **Beskrivning:** Lookout tillhandahåller det bästa skyddet mot mobila hot för att skydda din enhet. När appen Lookout är installerad på enheten skyddar den din enhet från hot och varnar dig och din företagsadministratör om några hittas.
  * **Kategori:** Datorhantering
* **Steg 4**: När åtgärden har slutförts visas meddelandet **Dataöverföringen till Microsoft Intune har slutförts**.

När du klickar på **Appar** i Intune-konsolen så kommer du nu att se Lookout for Work-appen i listan ![skärmbild på Intune-administratörskonsolens appsida som visar Lookout for Work-appar i listan](../media/mtp/lookout-app-listed-intune-console.png)

* **Steg 5**: Distribuera appar till användare genom att välja Lookout for Work-appen och välja  **Hantera distribution**.

  Du måste markera samma användare som har lagts till i alternativet Registreringshantering i Lookout MTP-konsolen.  Se steg tre i [configure your subscription with Lookout MTP section](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) (avsnittet konfigurera din prenumeration med Lookout MTP) för information om att lägga till användargrupper i Lookout MTP.
  >[!IMPORTANT]
  > Appdistributionsguiden för Intune kan inte använda Azure AD-användargrupper utan använder istället Intune-användargrupper. Därför måste du skapa en Intune-användargrupp baserat på Azure AD-användargruppen som har registrerats i Lookout MTP-konsolen enligt beskrivningarna i [den här](plan-your-user-and-device-groups.md)artikeln.

* **Steg 6**: Välj alternativet **Nödvändig installation** för att kräva att Lookout-appen installeras på användarens enhet.


## <a name="ios-enterprisesigned-version-of-lookout-app"></a>iOS (Företagssignerad version av Lookout-appen)

* **Steg ett:** Kontrollera att **iOS management** (iOS-hantering) är inställt på enheten. Anvisningar om hur du ställer in din enhet för iOS-hantering finns i [Set up iOS and Mac device management](set-up-ios-and-mac-management-with-microsoft-intune.md) (Konfigurera iOS- och Mac-enhetshantering).

* **Steg två:** **Omsignera** iOS-appen Lookout for Work. Lookout distribuerar iOS-appen Lookout for Work utanför iOS App Store. **Before distributing the app** (Innan du distribuerar appen) måste du omsignera appen med din iOS Enterprise Developer-certifikat. Detaljerade anvisningar om hur du omsignerar iOS-apparna Lookout for Work finns i [Omsigneringsprocessen för iOS-appen Lookout for Work](https://personal.support.lookout.com/hc/en-us/articles/114094038714) på Lookout-platsen.


* **Steg tre:** Aktivera Azure Active Directory-autentisering för iOS-användare genom att göra följande:
  1.  Logga in på [hanteringsportalen för Azure Active Directory](https://manage.windowsazure.com) och gå till programsidan.
  2.  Lägg till **Lookout for Work iOS app** (iOS-appen Lookout for Work) som ett **internt klientprogram**.
  ![skärmbild på dialogrutan lägg till appar som visar det inbyggda klientapps-alternativet](../media/mtp/aad-add-app.png)

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

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Vad händer när den distribuerade appen öppnas på enheten




När användaren öppnar Lookout for Work på enheten uppmanas de att aktivera appen och att välja alternativet att logga in med Azure Active Directory. En detaljerad genomgång som visar vad slutanvändaren ska göra finns i följande avsnitt:

* [Du uppmanas att installera Lookout for Work på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Du måste åtgärda ett hot som Lookout for Work har hittat på din Android-enhet](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Nästa steg
* [Aktivera regeln för skydd mot hot på enhet i kompatibilitetsprincipen](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Nov16_HO2-->

