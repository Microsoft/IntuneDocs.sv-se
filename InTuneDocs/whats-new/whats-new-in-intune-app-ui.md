---
title: "UI-uppdateringar för Intune-appar för slutanvändare | Microsoft Docs"
description: "Ta reda på vad som har ändrats i gränssnittet för appar som fungerar på slutanvändarenheter med Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 62dcb40ad5a7921c514a9d41da14b991e39f3bcd
ms.openlocfilehash: f4a48b889702147abe20fd513fdb0f774020a54a
ms.lasthandoff: 04/20/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>UI-uppdateringar för Intune-appar för slutanvändare
Lär dig mer om de senaste uppdateringarna i användargränssnittet för appar som dina slutanvändare ser i den här versionen av Microsoft Intune. Detta kan hjälpa dig med användarkommunikation och att uppdatera anpassad dokumentation som du har skapat för att stödja distributionen. Det underlättar också felsökningen av eventuella problem som användarna har om de kontaktar supportavdelningen för att få hjälp med att använda företagsportalen.

> [!Note]
> Observera att bilderna nedan är förhandsgranskningar och att den presenterade produkten kan skilja sig från presenterade versioner.

## <a name="april-2017"></a>April 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Förbättrad inloggning i företagsportalens appar för alla plattformar <!--User Story 1132123-->

Vi förbättrar inloggningen för appar i Intunes företagsportal för Android, iOS och Windows.  Det nya användargränssnittet visas automatiskt på alla plattformar för företagsportalappen när Azure AD genomför ändringen. Dessutom kan användarna nu logga in på företagsportalen från en annan enhet med en engångskod som genereras. Detta är särskilt användbart när användarna måste logga in utan autentiseringsuppgifter.  

Nedan kan du se föregående inloggning, den nya inloggningen med autentiseringsuppgifter och den nya inloggningen från en annan enhet.

__Föregående inloggning__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_before_1704_001.png)

![Användarna anger sina autentiseringsuppgifter på den här sidan när de har tryckt på Logga in, vilken begär användarens e-post och lösenord, tillsammans med förslag på att lösa lösenordsfel.](./media/cp_ios_aad_signin_before_1704_002.png)

![När de har angett sina lösenord loggas de in på företagsportalappen, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_before_1704_003.png)

__Ny inloggning__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_after_1704_001.png)

![Användaren ombeds endast att ange sin e-postadress, i stället för sin e-post och lösenord på samma skärm.](./media/cp_ios_aad_signin_after_1704_002.png)

![Användaren uppmanas att ange lösenordet när e-postadressen har accepterats.](./media/cp_ios_aad_signin_after_1704_003.png)

__Ny inloggning vid inloggning från en annan enhet__

![Företagsportalens inloggningssida med en ikon för en person framför en grafisk representation av en webbplats. Nedanför finns knappen ”Logga in”. En länk längst ner leder till Microsofts information om sekretess och cookies.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Tryck på länken __Logga in från en annan enhet__.

![Användaren ombeds endast att ange sin e-postadress, i stället för sin e-post och lösenord på samma skärm. Länken under e-postfältet visar ”Logga in från en annan enhet”.](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![Instruktioner visas för att gå till sidan aka.ms/devicelogin med ett unikt lösenord från din arbetsdator. Därefter använder du koden för att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Starta en webbläsare och gå till [http://aka.ms/devicelogin](https://aka.ms/devicelogin).

![En bild av användarens webbläsare på arbetsdatorn, i stället för företagsportalappen. Sidan ”Inloggning på enhet” visas och uppmanar användarna ange koden de fick i företagsportalsappen.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Ange koden som du såg i företagsportalsappen. När du väljer __Fortsätt__, kommer du att kunna autentisera med någon av metoderna som stöds av ditt företag, till exempel ett smartkort.

![Användaren har matat in sin unika kod i fältet och webbplatsen ”Inloggning på enhet” har begärt en bekräftelse på att Intunes företagsportal är rätt app för att få behörighet att logga in.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![En bekräftelsesida som anger att användaren har loggat in i företagsportalsappen på sin enhet visas nu, och den här sidan kan stängas.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

Företagsportalappen börjar logga in.

![Efter att genomgått autentiseringsprocessen loggas företagsportalappen in, vilket visas med en förloppsindikator.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nya ikoner för Managed Browser och företagsportalen <!--918433, 918431-->

Managed Browser har fått uppdaterade ikoner för både Android- och iOS-versionerna av appen. Den nya ikonen innehåller det uppdaterade Intune-märket så att det överensstämmer med andra appar i Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

Företagsportalen har också fått uppdaterade ikoner för Android-, iOS- och Windows-versionerna av appen, för att förbättra enhetligheten med andra appar i EM+S. Dessa ikoner släpps gradvis till plattformarna från april till slutet av maj.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Förloppsindikator för inloggning i Android-företagsportalen <!--953374-->

En uppdatering av Android-företagsportalsappen visar en förloppsindikator för inloggning när användaren startar eller återupptar appen. Indikatorn visar nya statusmeddelanden, med början på ”Ansluter...”, sedan ”Loggar in...”, följt av ”Kontrollerar säkerhetskrav...” innan användaren får åtkomst till appen.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="february-2017"></a>Februari 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Ny användarupplevelse för företagsportalappen för Android <!--621622, announced 1702-->
Från och med mars följer företagsportalsappen för Android [riktlinjer för materialdesign](https://material.io/guidelines/material-design/introduction.html) för att skapa en modernare känsla och ett modernare utseende. Den här förbättrade användarupplevelsen innehåller:

* __Färger__: Flikrubriken kan färgas enligt din anpassade färgpalett.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Enheter som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Gränssnitt__: Knapparna __Aktuella appar__ och __Alla appar__ har uppdaterats på fliken __Appar__. __Sökknappen__ är nu flytande.

![Till vänster finns en avbildning av företagsportalappen för Android före uppdateringen. Till höger finns en avbildning av företagsportalappen för Android efter uppdateringen. Båda bilderna visar fliken Appar som den valda fliken från de tre tillgängliga flikarna Appar, Enheter och Kontakta IT.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigering__: Alla appar visar en flikvy över __Aktuella__, __Alla__ och __Kategorier__ för att underlätta navigeringen. __Kontakta IT__ har effektiviserats för bättre läsbarhet.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Januari 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernisera företagsportalswebbplatsen <!--753980, announced 1701-->
Från och med februari kommer företagsportalens webbplats att ha stöd för appar som är avsedda för användare som inte har några hanterade enheter. Webbplatsen anpassas med andra Microsoft-produkter och tjänster med hjälp av ett nytt kontrasterande färgschema, dynamiska bilder och en "hamburgarmeny", ![En liten bild på hamburgarmenyn som nu är tillagd i det övre vänstra hörnet på företagsportalens webbplats](./media/CP_hamburger_menu.png) som innehåller kontaktinformation till supportavdelningen och information om befintliga hanterade enheter. Landningssidan ordnas om för att betona appar som är tillgängliga för användare med karuseller för aktuella och nyligen uppdaterade appar.

![Till vänster visas en bild av den aktuella versionen av webbplatsen för företagsportalen med dess tidigare version av Appar, Mina enheter och vyerna Aktuellt och Kategorier. Till höger visas en bild av den uppdaterade versionen av webbplatsen för företagsportalen med en uppdaterad appkarusell, lista över nyligen publicerade appar och uppdaterad kategorivy.](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>Se även
* [Microsoft Intune-blogg](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Översikt över molnplattformen](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Vad är nytt i förhandsversionen av Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Nyhetsarkiv](whats-new-archive.md)

