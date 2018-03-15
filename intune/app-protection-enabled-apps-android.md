---
title: Android-appar med appskyddsprinciper
titlesuffix: Microsoft Intune
description: "Läs om vad som händer när en Android-app har skyddsprinciper."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: af25dc918907e086441a89f222985a75199bbe95
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/05/2018
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>Vad som händer när din Android-app hanteras av appskyddsprinciper 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Läs om vad som händer när Android-appar har appskyddsprinciper. Appskyddsprinciper används bara när appar används i en arbetskontext. Det kan till exempel vara när du använder en app med ett arbetskonto eller när du använder filer som är lagrade på företagets OneDrive-plats.
##  <a name="accessing-apps"></a>Komma åt appar

Företagsportalappen krävs för alla appar på Android-enheter som har appskyddsprinciper.

Installera Företagsportalen på alla enheter som inte är registrerade i Intune. Användare behöver inte logga in på företagsportalappen för att använda appar som har appskyddsprinciper.
Företagsportalappen låter dig dela data på en säker plats. Därför är den ett krav även för enheter som inte är registrerade.


##  <a name="using-apps-with-multi-identity-support"></a>Använda appar med stöd för flera identiteter

Appskyddsprinciperna gäller endast om en användare försöker komma åt arbetsrelaterade data.  Beteendet kan se annorlunda ut om användaren använder appen för personligt bruk.

Vissa appar stöder flera identiteter. I så fall tillämpar Intune endast appskyddsprinciperna när en användare försöker komma åt arbetsdata.  En användare kan till exempel uppmanas att ange en PIN-kod.  I **Outlook-appen** uppmanas användaren att ange en PIN-kod när han eller hon startar appen. I **OneDrive-appen** uppmanas användaren att ange en PIN-kod när han eller hon anger arbetskontot.  I Microsoft **Word**, **PowerPoint** och **Excel** uppmanas användaren att ange en PIN-kod när han eller hon öppnar företagets OneDrive-dokument.
##  <a name="managing-user-accounts-on-the-device"></a>Hantera användarkonton på enheten

Intune har stöd för distribution av appskyddsprinciper till ett användarkonto per enhet.

* Beroende på den app du använder kan den andra användaren eventuellt vara blockerad på enheten. I samtliga fall påverkas dock endast den första användaren som hämtar appskyddsprincipen.

  * **Microsoft Word**, **Excel** och **PowerPoint** blockerar inte åtkomst till ytterligare ett användarkonto. Användarkontot påverkas dock inte av appskyddsprinciperna.

  * För **OneDrive- och Outlook-appar** kan du bara använda ett arbetskonto.  Det går inte att lägga till flera arbetskonton i dessa appar.  Men du kan ta bort en användare från en enhet, och sedan lägga till en annan användare i enheten.


* En enhet kan ha flera befintliga användarkonton innan appskyddsprinciperna distribueras. I så fall hanteras det första kontot som appskyddsprinciperna distribueras till av Intunes appskyddsprinciper.


Läs följande exempelscenario om du vill veta hur Intune hanterar flera användarkonton.

Användare A arbetar för två företag – **Företag X** och **Företag Y**. Användare A har ett arbetskonto för varje företag och båda använder Intune för att distribuera appskyddsprinciper. **Företag X** distribuerar appskyddsprinciper **före** **Företag Y**. Det konto som är kopplat till **Företag X** får appskyddsprincipen, men inte kontot som är kopplat till Företag Y. Om du vill att användarkontot för Företag Y ska hanteras av appskyddsprinciperna måste Användare A ta bort användarkontot för Företag X.
### <a name="adding-a-second-account"></a>Lägga till ett andra konto
####  <a name="android"></a>Android
Du kan också få en uppmaning om att ta bort det befintliga kontot och lägga till ett nytt.  Om du vill ta bort det befintliga kontot går du till **Inställningar &gt;Allmänt &gt; Programhanterare &gt;Företagsportal. Välj Rensa Data.**

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
|Pfile är ett allmänt adapterformat för skyddade filer. Den kapslar in det krypterade innehållet och Azure Information Protection-licenserna. Det kan användas för att skydda alla filtyper.|Textfiler, till exempel XML och CSV, kan visas i appen även när de skyddas. Filtyper: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## <a name="next-steps"></a>Nästa steg
[Vad som händer när din iOS-app hanteras av appskyddsprinciper](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Se även
[Skapa och distribuera appskyddsprinciper med Microsoft Intune](app-protection-policies.md)
