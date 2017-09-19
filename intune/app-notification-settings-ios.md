---
title: "Appaviseringsinställningar i Intune för iOS-enheter"
titlesuffix: Azure portal
description: "Läs om de inställningar du kan använda för att styra aviseringar från appar i iOS-enheter.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 46b31be3cd05c0a5252589d2b25eb92b86a42733
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2017
---
# <a name="intune-app-notifications-settings-for-ios-devices"></a>Appaviseringsinställningar i Intune för iOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Låter dig konfigurera hur appar som installerats på en enhet skickar aviseringar. Inställningarna har stöd för övervakade enheter som kör iOS 9.3 och senare.

## <a name="configure-settings"></a>Konfigurera inställningar

1. På bladet Enhetsfunktioner väljer du **Appaviseringar (endast övervakat)**.
2. På bladet **Appaviseringar** väljer du **Lägg till** och sedan konfigurerar du följande värden:
    - **Appsamlings-ID** – Ange **Appsamlings-ID** för den app som du vill konfigurera. Hjälp finns i **Referens till samlings-ID för inbyggda iOS-appar** senare i det här avsnittet.
    - **Appnamn** – Ange namnet på den app som du vill konfigurera. Det här namnet visas inte på enheten och används för att identifiera appen i listan.
    - **Utgivare** – Ange utgivaren av den app som du vill konfigurera. Utgivarens namn visas inte på enheten och används endast för att identifiera appen i listan.
    - **Aviseringar** – Aktivera eller inaktivera appen från att skicka aviseringar till enheten. Om du inaktiverar den här inställningen inaktiveras även följande inställningar.
        - **Visa i Notiscenter** – Aktivera den här inställningen för att appen ska visa aviseringar i enhetens meddelandecenter.
        - **Visa på låsskärm** – Aktivera den här inställningen för att visa aviseringar från appen på enhetens låsskärm.
        - **Aviseringstyp** – Välj vilken typ av avisering som du vill se när enheten är upplåst från:
            - **Ingen** – Ingen avisering visas.
            - **Banderoll** – En banderoll visas en kort stund med aviseringen.
            - **Modal** – Aviseringen visas och användarna måste manuellt ta bort den innan de kan fortsätta att använda enheten.
        - **Bricka på appikon** – Aktivera den här inställningen för att lägga till en symbol på appikonen som visar att appen skickat en avisering.
        - **Ljud** – Aktivera den här inställningen när en avisering tas emot.
3. Fortsätt lägga till så många appar som du behöver. Välj **OK** när du är klar.
4. Välj **OK** tills du kommer tillbaka till bladet **Skapa profil**. Välj sedan **Skapa**. 


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
