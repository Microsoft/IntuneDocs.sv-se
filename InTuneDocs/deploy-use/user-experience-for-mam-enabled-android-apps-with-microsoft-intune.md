---
title: Android-appar med MAM-principer | Microsoft Intune
description: "I det här avsnittet beskrivs vad som händer när din app hanteras av hanteringsprinciper för mobilappar (MAM)."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 945c9f48846fc37358c44b83990feed1f3694966


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-mam-policies"></a>Vad som händer när din Android-app hanteras med MAM-principer
Det här avsnittet beskriver användargränssnittet för appar med principer för mobil programhantering (MAM). MAM-principer tillämpas endast när appar används i arbetssammanhang: Till exempel när användaren har åtkomst till appar med ett arbetskonto eller har åtkomst till filer som lagras i ett företags OneDrive-affärsplats.
##  <a name="access-apps"></a>Åtkomstappar

Företagsportalappen krävs för alla appar som är kopplade till MAM-principer på Android-enheter.

För enheter som inte har registrerats i Intune måste företagsportalappen installeras på enheten. Användaren behöver dock inte starta eller logga in i företagsportalappen innan de kan använda appar som hanteras av MAM-principer.

Företagsportalappen är ett sätt för Intune att dela data på en säker plats. Därför är företagsportalappen ett krav för alla appar som är associerade med MAM-principer, även om enheten inte har registrerats i Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

MAM-principer tillämpas bara i arbetssammanhang. Därför kan appen fungerar på olika sätt beroende på om sammanhanget är arbete eller personligt.

Användaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata. För **Outlook-appen**, uppmanas användaren att ange en PIN-kod när hen startar appen. För **OneDrive-appen**, uppmanas användaren att ange PIN-koden när hen skriver i arbetskontot. För Microsoft **Word**, **PowerPoint** och **Excel**, uppmanas användaren att ange PIN-koden när hen har åtkomst till dokument som lagras i företagets OneDrive för företag.

##  <a name="manage-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune stöder distribution av MAM-principer till ett användarkonto per enhet endast.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar MAM-principerna av principen.

  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av MAM-principerna.

  * För **OneDrive- och Outlook-appar** och **Outlook-appar** kan du bara använda ett arbetskonto.  Du kan inte lägga till flera arbetskonton för dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.


* Om en enhet har flera befintliga användarkonton innan MAM-principerna distribueras kommer kontot som MAM-principerna distribueras till först att hanteras av Intune MAM-principer.


Läs följande exempel för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera MAM-principer. **Företag X** distribuerar MAM-principer **före** **Företag Y**. Det konto som är kopplat till **Företag X** får MAM-principen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av MAM-principerna måste du ta bort användarkontot som är kopplat till Företag X.
### <a name="add-a-second-account"></a>Lägg till ett andra konto
####  <a name="android"></a>Android
Om du använder en Android-enhet kan ett blockeringsmeddelande visas med instruktioner för att ta bort det befintliga kontot och lägga till ett nytt.  Om du vill ta bort det befintliga kontot går du till **Inställningar &gt;Allmänt &gt; Programhanterare &gt;Företagsportal.** Välj sedan **Rensa data**.

![Skärmbild av felmeddelande och anvisningar för att ta bort kontot](../media/AppManagement/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Visa mediefiler med Azure Information Protection-appen
Du kan visa företagets AV-, PDF- och bildfiler på Android-enheter i [Azure Information Protection-app](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (tidigare kallad Rights Management Sharing-app).

Hämta den här appen från Google Play Store.  

Följande filtyper stöds:

* **Ljud:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (förbättrad AAC+), AAC ELD (Enhanced Low Delay AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Bild:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Dokument:** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Pfile är ett allmänt “wrapper”-format för skyddade filer som kapslar in det krypterade innehållet och Azure Information Protection-licenserna. Det kan användas för att skydda alla filtyper.|Textfiler, till exempel XML och CSV och så vare, kan visas i appen även när de skyddas. Filtyper: .txt, .ptxt, .csv, .pcsv, .log, .plog, .xml, .pxml.|

## <a name="next-steps"></a>Nästa steg
[Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### <a name="see-also"></a>Se även
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


