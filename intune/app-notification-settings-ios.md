---
title: Skapa appmeddelanden för iOS-enheter – Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa appmeddelanden för iOS-enheter i Microsoft Intune. Välj vilka appar som ska kunna skicka meddelanden, konfigurera inställningar för meddelanden på låsskärmen, aktivera ljud, välj typ av avisering och lägg till en aktivitetsikon.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bda26d1d-2a3b-4669-adf8-a5aa7f994916
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 43068163c15c0588a8a6ef745d5b191f4547a94d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025713"
---
# <a name="configure-app-notifications-settings-on-ios-devices-in-intune"></a>Konfigurera inställningar för appmeddelanden på iOS-enheter i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Konfigurera hur installerade appar på en iOS-enhet skickar meddelanden. Inställningarna har stöd för övervakade enheter som kör iOS 9.3 och senare.

## <a name="add-the-app-notification"></a>Lägg till appmeddelandet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. I din profil för iOS eller macOS väljer du **Enhetsfunktioner**. I listan [iOS- eller macOS-enhetsfunktioner](device-features-configure.md) visas stegen för att skapa en profil.
3. Välj **Appmeddelanden (endast övervakat)** och sedan **Lägg till**: ![Lägg till appmeddelande i iOS- eller macOS-profil i Intune](./media/ios-macos-app-notifications.png)
4. Ange följande egenskaper:

   - **Appsamlings-ID** – Ange **Appsamlings-ID** för den app som du vill konfigurera. Hjälp finns i **Referens till samlings-ID för inbyggda iOS-appar** (i den här artikeln).
   - **Appnamn**: Ange namnet på den app som du vill konfigurera. Det här namnet visas inte på enheten och används för att identifiera appen i listan.
   - **Utgivare**: Ange utgivaren av den app som du vill konfigurera. Utgivarens namn visas inte på enheten och används endast för att identifiera appen i listan.
   - **Meddelanden**: Aktivera eller inaktivera att appen kan skicka meddelanden till enheten. Om du inaktiverar den här inställningen inaktiveras även följande inställningar.
     - **Visa i Notiscenter** – Aktivera den här inställningen för att appen ska visa aviseringar i enhetens meddelandecenter.
     - **Visa på låsskärm** – Aktivera den här inställningen för att visa aviseringar från appen på enhetens låsskärm.
     - **Aviseringstyp** – Välj vilken typ av avisering som du vill se när enheten är upplåst från:
       - **Ingen** – Ingen avisering visas.
       - **Banderoll** – En banderoll visas en kort stund med aviseringen.
       - **Modal** – Aviseringen visas och användarna måste manuellt ta bort den innan de kan fortsätta att använda enheten.
     - **Bricka på appikon** – Aktivera den här inställningen för att lägga till en symbol på appikonen som visar att appen skickat en avisering.
     - **Ljud** – Aktivera den här inställningen när en avisering tas emot.

5. Fortsätt lägga till så många appar som du behöver. När du är klar med att lägga till appar väljer du **OK**.
6. Spara profilen genom att välja **Skapa**.

## <a name="bundle-id-reference-for-built-in-ios-apps"></a>Referens till samlings-ID för inbyggda iOS-appar

I följande lista visas appsamlings-ID:n för några vanliga inbyggda iOS-appar. Kontakta programvaruleverantören om du behöver appsamlings-ID:n för andra appar.

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
|Obs!|com.apple.mobilenotes|
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

Tilldela enhetsprofilen till de grupper som du väljer. Anvisningar finns i [Tilldela enhetsprofiler](device-profile-assign.md).