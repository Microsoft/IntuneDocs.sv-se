---
title: Android-appar med appskyddsprinciper
description: "Det här avsnittet beskriver vad som händer när din app hanteras av appskyddsprinciper."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 030e17a9f28a9476c82e89d4dd26151a2d3cb953
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/13/2017
---
# Vad som händer när din Android-app hanteras av appskyddsprinciper
<a id="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Det här avsnittet beskriver användarupplevelsen för appar med appskyddsprinciper. Appskyddsprinciper tillämpas endast när appar används i arbetssammanhang: Till exempel när användaren har åtkomst till appar med ett arbetskonto eller har åtkomst till filer som lagras i ett företags OneDrive-affärsplats.
##  Åtkomstappar
<a id="access-apps" class="xliff"></a>

Företagsportalappen krävs för alla appar som är kopplade till appskyddsprinciper på Android-enheter.

För enheter som inte har registrerats i Intune måste företagsportalappen installeras på enheten. Användaren behöver dock inte starta eller logga in i företagsportalappen innan de kan använda appar som hanteras av appskyddsprinciper.

Företagsportalappen är ett sätt för Intune att dela data på en säker plats. Därför är företagsportalappen ett krav för alla appar som är associerade med appskyddsprinciper, även om enheten inte har registrerats i Intune.


##  Använda appar med stöd för flera identiteter
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

Appskyddsprinciper tillämpas bara i arbetssammanhang. Därför kan appen fungerar på olika sätt beroende på om sammanhanget är arbete eller personligt.

Användaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata. För **Outlook-appen**, uppmanas användaren att ange en PIN-kod när hen startar appen. För **OneDrive-appen**, uppmanas användaren att ange PIN-koden när hen skriver i arbetskontot. För Microsoft **Word**, **PowerPoint** och **Excel**, uppmanas användaren att ange PIN-koden när hen har åtkomst till dokument som lagras i företagets OneDrive för företag.

##  Hantera användarkonton på enheten
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

Intune stöder distribution av appskyddsprinciper till ett användarkonto per enhet endast.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar appskyddsprincipen.

  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av appskyddsprinciperna.

  * För **OneDrive- och Outlook-appar** och **Outlook-appar** kan du bara använda ett arbetskonto.  Du kan inte lägga till flera arbetskonton för dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.


* Om en enhet har flera befintliga användarkonton innan appskyddsprinciperna distribueras kommer kontot som appskyddsprinciperna distribueras till först att hanteras av Intunes appskyddsprinciper.


Läs följande exempel för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X.
### Lägg till ett andra konto
<a id="add-a-second-account" class="xliff"></a>
####  Android
<a id="android" class="xliff"></a>
Om du använder en Android-enhet kan ett blockeringsmeddelande visas med instruktioner för att ta bort det befintliga kontot och lägga till ett nytt.  Om du vill ta bort det befintliga kontot går du till **Inställningar &gt;Allmänt &gt; Programhanterare &gt;Företagsportal.** Välj sedan **Rensa data**.

![Skärmbild av felmeddelande och anvisningar för att ta bort kontot](./media/Android_SwitchUser.png)

##  Visa mediefiler med Azure Information Protection-appen
<a id="view-media-files-with-the-azure-information-protection-app" class="xliff"></a>
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

## Nästa steg
<a id="next-steps" class="xliff"></a>
[Vad som händer när din iOS-app hanteras av appskyddsprinciper](end-user-mam-apps-ios.md)
