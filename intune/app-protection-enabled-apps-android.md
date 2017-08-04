---
title: Android-appar med appskyddsprinciper
titleSuffix: Intune on Azure
description: "Det här ämnet beskriver vad som händer när din Android-app hanteras av appskyddsprinciper.”"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97a7a2d2727d823c24e720b61531dce78f6935d1
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Vad som händer när din Android-app hanteras av appskyddsprinciper 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Det här avsnittet beskriver användarupplevelsen för appar med appskyddsprinciper. Appskyddsprinciper används bara när appar används i arbetskontext, t.ex. åtkomst till appar med ditt arbetskonto eller åtkomst till filer som lagras på platsen för ditt företags OneDrive för företag.
##  <a name="accessing-apps"></a>Komma åt appar

Företagsportalappen krävs för alla appar som är kopplade till appskyddsprinciper på Android-enheter.

För enheter som inte har registrerats i Intune måste företagsportalappen installeras på enheten. Användaren behöver dock inte starta eller logga in i företagsportalappen innan de kan använda appar som hanteras av appskyddsprinciper.
Företagsportalappen är ett sätt för Intune att dela data på en säker plats, och därför är detta ett krav även om enheten inte har registrerats i Intune.


##  <a name="using-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Appskyddsprinciper tillämpas bara i arbetskontexten när du använder appen, och appens beteende kan skilja sig beroende på kontexten: arbete eller personligt.

För appar som stöder flera identiteter tillämpar Intune endast appskyddsprinciperna när slutanvändaren använder appen i arbetskontexten.  Slutanvändaren uppmanas till exempel att ange en PIN-kod för att kunna komma åt arbetsdata.  För **Outlook-appen** uppmanas slutanvändaren att ange en PIN-kod när appen startas. För **OneDrive-appen** sker detta när slutanvändaren anger arbetskontot.  För Microsoft **Word**, **PowerPoint* och **Excel** sker detta när slutanvändaren kommer åt dokument som lagras på platsen för företagets OneDrive för företag-plats.
##  <a name="managing-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune har endast stöd för distribution av appskyddsprinciper till ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar appskyddsprincipen.

  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte ett andra användarkonto, men det andra användarkontot påverkas inte av appskyddsprinciperna.

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Däremot kan du ta bort en användare och lägga till en annan användare på enheten.


* Om en enhet har flera befintliga användarkonton innan appskyddsprinciperna distribueras kommer kontot som appskyddsprinciperna distribueras till först att hanteras av Intunes appskyddsprinciper.


Läsa exemplet nedan för att få en bättre förståelse för hur flera användarkonton behandlas.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot som är kopplat till Företag Y ska hanteras av appskyddsprinciperna måste du ta bort användarkontot som är kopplat till Företag X.
### <a name="adding-a-second-account"></a>Lägga till ett andra konto
####  <a name="android"></a>Android
Om du använder en Android-enhet kan ett blockeringsmeddelande visas med instruktioner för att ta bort det befintliga kontot och lägga till ett nytt.  Om du vill ta bort det befintliga kontot går du till **Inställningar &gt;Allmänt &gt; Programhanterare &gt;Företagsportal och väljer ”Rensa data”**.

![Skärmbild av felmeddelande och anvisningar för att ta bort kontot](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Visa mediefiler med Azure Information Protection-appen (tidigare delningsapplikationen för Rights Management)
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
## <a name="next-steps"></a>Nästa steg
[Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Se även
[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)
