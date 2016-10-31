---
title: Android-appar med MAM-principer | Microsoft Intune
description: "I det här avsnittet beskrivs vad som händer när din app hanteras av hanteringsprinciper för mobilappar (MAM)."
keywords: 
author: karthikaraman
ms.author: karaman
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
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 546b909737b4ea34bd747880fe8ed2d366c6b18a


---

# Vad som händer när din Android-app hanteras med MAM-principer
Det här avsnittet beskriver användargränssnittet för appar med MAM-principer. MAM-principer för hantering av mobila program används bara om appar används i arbetskontexten, t.ex. åtkomst till appar med ditt arbetskonto eller åtkomst till filer som lagras på platsen för ditt företags OneDrive för företag.
##  Komma åt appar

Företagsportalappen krävs för alla appar som är kopplade till MAM-principer på Android-enheter.

För enheter som inte har registrerats i Intune måste företagsportalappen installeras på enheten. Användaren behöver dock inte starta eller logga in i företagsportalappen innan de kan använda appar som hanteras av MAM-principer.
Företagsportalappen är ett sätt för Intune att dela data på en säker plats, och därför är detta ett krav även om enheten inte har registrerats i Intune.


##  Använda appar med stöd för flera identiteter

MAM-principer tillämpas bara i arbetskontexten när du använder appen, och appens beteende kan skilja sig beroende på kontexten: arbete eller personligt.

För appar som stöder flera identiteter tillämpar Intune endast MAM-principerna när slutanvändaren använder appen i arbetskontexten.  Slutanvändaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata.  För **Outlook-appen** uppmanas slutanvändaren att ange en PIN-kod när appen startas. För **OneDrive-appen** sker detta när slutanvändaren anger arbetskontot.  För Microsoft **Word**, **PowerPoint* och **Excel** sker detta när användaren kommer åt dokument som lagras på platsen för företagets OneDrive för företag.
##  Hantera användarkonton på enheten

Intune har endast stöd för distribution av MAM-principer till endast ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar MAM-principerna av principen.

  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av MAM-principerna.

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.


* Om en enhet har flera befintliga användarkonton innan MAM-principerna distribueras kommer kontot som MAM-principerna distribueras till först att hanteras av Intune MAM-principer.


Läsa exemplet nedan för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera MAM-principer. **Företag X** distribuerar MAM-principer **före** **Företag Y**. Det konto som är kopplat till **Företag X** får MAM-principen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av MAM-principerna måste du ta bort användarkontot som är kopplat till Företag X.
### Lägga till ett andra konto
####  Android
Om du använder en Android-enhet kan ett blockeringsmeddelande visas med instruktioner för att ta bort det befintliga kontot och lägga till ett nytt.  Om du vill ta bort det befintliga kontot går du till **Inställningar &gt;Allmänt &gt; Programhanterare &gt;Företagsportal och väljer ”Rensa data”**.

![Skärmbild av felmeddelande och anvisningar för att ta bort kontot](../media/AppManagement/Android_SwitchUser.png)

##  Visa mediefiler med Azure Information Protection-appen (tidigare delningsapplikationen för Rights Management)
Om du vill visa företagets AV-, PDF- och bildfiler på Android-enheter använder du [Azure Information Protection-appen](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Hämta den här appen från Google Play Store.  

Följande filtyper stöds:

* **Ljud:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (förbättrad AAC+), AAC ELD (Enhanced Low Delay AAC), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Video:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Bild:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **Dokument:** PDF, PPDF

------------
|**pfile**|**text**|
|----|----|
|Pfile är ett allmänt “wrapper”-format för skyddade filer som kapslar in det krypterade innehållet och Azure Information Protection-licenserna. Det kan användas för att skydda alla filtyper.|Textfiler, till exempel XML och CSV, kan visas i appen även när de skyddas. Filtyper: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## Nästa steg
[Vad som händer när din iOS-app hanteras med MAM-principer](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### Se även
[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


