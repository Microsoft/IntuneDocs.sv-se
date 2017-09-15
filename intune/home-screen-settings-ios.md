---
title: "Layoutinställningar i Intune för startskärmen för iOS-enheter"
titlesuffix: Azure portal
description: "Lär dig vilka inställningar du kan anpassa på startskärmen och dockan på iOS-enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6aba4491-afb9-43cd-9ccc-14e6a2a5a3b1
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4a3f175337d521c92c909db9972d844ac6997cb0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2017
---
# <a name="intune-home-screen-layout-settings-for-ios-devices"></a>Layoutinställningar i Intune för startskärmen för iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd dessa inställningar för att konfigurera layouten för appar, mappar och webbklipp på dockan och startskärmen på iOS-enheter.

iOS-enheter som du tilldelar profilen till måste vara i övervakat läge och köra iOS 9.3 eller senare.

1. På bladen **Enhetsfunktioner** väljer du **Hemskärmslayout (endast övervakat)**.
2. På bladet **Hemskärmslayout (endast övervakat)** väljer du om du vill konfigurera layouterna **Docka** eller **Sidor**.

## <a name="add-items-to-the-dock"></a>Lägga till objekt i dockan

På bladet **Docka** kan du lägga till upp till sex objekt eller mappar till dockan på iOS-skärmen. Emellertid stöder många enheter färre objekt än detta, t.ex. kan iPhone-enheter bara visa fyra objekt. I det här fallet visas endast de första fyra objekt som du har konfigurerat på enheten.

1. Välj **Lägg till** för att lägga till ett objekt i dockan.
2. På bladet **Lägg till rad** väljer du om du vill lägga till en **App** eller en **Mapp**.
3. Med hjälp av informationen i det här avsnittet kan du ange vilka appar och mappar som ska visas i dockan.
4. Fortsätt att lägga till objekt. När du är klar väljer du **OK** tills du kommer tillbaka till bladet **Skapa profil**. Välj **Skapa**.

>[!TIP]
> Du kan dra och släppa objekt på startskärmen och sidlistor för att sortera om dem. 

### <a name="example"></a>Exempel

I det här exemplet har du konfigurerat dockningsskärmen till att enbart visa Safari, E-post och Aktier. E-postappen är markerad i följande bild, för att visa dess egenskaper:

![Exempel på iOS-dockningsinställningar](http://i.imgur.com/FfFiUcP.png)

När du tilldelar principen till en iPhone blir resultatet en docka som ser ut ungefär så här:

![Exempel på iOS-dockningslayout i iPhone](http://i.imgur.com/bAgCe8F.png)

## <a name="add-home-screen-pages"></a>Lägga till sidor på startskärmen

Lägg till de sidor som du vill ska visas på startskärmen samt de appar som ska visas på varje sida. Apparna som du lägger till på en sida ordnas från vänster till höger, i samma ordning som de anges i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en efterföljande sida.


1. På bladet **Sidor** väljer du **Lägg till**.
2. På bladet **Lägg till rad** anger du ett **Sidnamn**. Det här namnet används som din referens i Azure-portalen och *visas inte* på iOS-enheten.
3. Välj **Lägg till** och välj sedan om du vill lägga till en **App** eller en **Mapp** på sidan.
4. Med hjälp av informationen i det här avsnittet kan du ange vilka appar och mappar som ska visas på sidan.

### <a name="example"></a>Exempel

I det här exemplet har du konfigurerat en ny sida med namnet **Contoso**. Sidan visar endast apparna Hitta vänner och Inställningar. Appen Inställningar är markerad i följande bild, för att visa dess egenskaper:

![Exempel på inställningar på iOS-startskärmen](http://i.imgur.com/Jc2OxyX.png)

När du tilldelar principen till en iPhone blir resultatet en sida som ser ut ungefär så här:

![iOS-enhet med ändrad startskärm](http://i.imgur.com/Bd37PHa.png)

## <a name="how-to-add-an-app-to-the-list"></a>Så här lägger du till en app i listan

1. Ange **Appnamn**. Det här namnet används som din referens i Azure-portalen och *visas inte* på iOS-enheten.
2. Ange **Appsamlings-ID** för den app som du vill visa. Hjälp finns i **Referens till samlings-ID för inbyggda iOS-appar** senare i det här avsnittet.
3. Klicka på **OK** och fortsätt sedan att lägga till objekt, upp till högst **6** för enhetens docka och **60** för en enhetssida.
4. Klicka på **OK**när du är klar.

## <a name="how-to-add-a-folder-to-the-list"></a>Så här lägger du till en mapp i listan

Apparna som du lägger till på en sida i en mapp ordnas från vänster till höger, i samma ordning som de anges i listan. Om du lägger till flera appar än vad som får plats på en sida, kommer apparna att flyttas till en efterföljande sida.

1. Ange **Mappnamn**. Det här namnet visas för användarna på deras enhet.
2. Välj **Lägg till** för att skapa en sida i mappen. Du kan lägga till upp till 20 sidor.
3. På bladet **Lägg till rad** anger du ett namn för sidan. Det här namnet används som din referens i Azure-portalen och *visas inte* på iOS-enheten.
3. Ange **Appnamn**. Det här namnet används som din referens i Azure-portalen och *visas inte* på iOS-enheten.
2. Ange **Appsamlings-ID** för den app som du vill visa. Se **Så här lägger du till en app i listan** om du behöver hjälp.
3. Välj **Lägg till**. Du kan lägga till upp till 60 objekt.
4. Klicka på **OK**när du är klar.


## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referens till samlings-ID för inbyggda iOS-appar

I listan visas appsamlings-ID:n för några vanliga inbyggda iOS-appar. Kontakta programvaruleverantören för att hitta appsamlings-ID:n för andra appar. 

|||
|-|-|
|Appnamn|Appsamlings-ID|
|Appbutik|com.apple.AppStore|
|Kalkylator|com.apple.calculator|
|Kalender|com.apple.mobilecal|
|Kamera|com.apple.camera|
|Klocka|com.apple.mobiletimer|
|Kompass|com.apple.compass|
|Kontakter|com.apple.MobileAddressBook|
|FaceTime|com.apple.facetime|
|Hitta vänner|com.apple.mobileme.fmf1|
|Hitta iPhone|com.apple.mobileme.fmip1|
|Spelcenter|com.apple.gamecenter|
|GarageBand|com.apple.mobilegarageband|
|Hälsa|com.apple.Health|
|iBooks|com.apple.iBooks|
|iTunes Store|com.apple.MobileStore|
|iTunes U|com.apple.itunesu|
|Keynote|com.apple.Keynote|
|E-post|com.apple.mobilemail|
|Kartor|com.apple.Maps|
|Meddelanden|com.apple.MobileSMS|
|Musik|com.apple.Music|
|Nyheter|com.apple.news|
|Anteckningar|com.apple.mobilenotes|
|Siffror|com.apple.Numbers|
|Sidor|com.apple.Pages|
|Photo Booth|com.apple.Photo-Booth|
|Foton|com.apple.mobileslideshow|
|Poddsändningar|com.apple.podcasts|
|Påminnelser|com.apple.reminders|
|Safari|com.apple.mobilesafari|
|Inställningar|com.apple.Preferences|
|Aktier|com.apple.stocks|
|Tips|com.apple.tips|
|Videor|com.apple.videos|
|VoiceMemos|com.apple.VoiceMemos|
|Plånbok|com.apple.Passbook|
|Titta på|com.apple.Bridge|
|Väder|com.apple.weather|


## <a name="next-steps"></a>Nästa steg

Du kan nu tilldela enhetsprofilen till de grupper som du väljer. Mer information finns i [Hur du tilldelar enhetsprofiler](device-profile-assign.md).