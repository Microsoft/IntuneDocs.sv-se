---
title: Felsöka Android Enterprise-enheter i Microsoft Intune
description: Förslag på felsökning av några av de vanligaste problemen när du registrerar Android-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652376"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Felsöka problem med Android Enterprise-enheter i Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem när de registrerar Android Enterprise-enheter i Intune.

## <a name="apps-on-android-enterprise-devices"></a>Appar på Android Enterprise-enheter

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Hanterade Google Play-appar som inte distribueras via Intune visas i arbetsprofilen
Systemappar kan aktiveras i arbetsprofilen av enhets-OEM när arbetsprofilen skapas. Detta styrs inte av MDM-leverantören.

Felsök med hjälp av följande steg:

  1. Samla in Företagsportalloggar.
  2. Anteckna de appar som visas i arbetsprofilen oväntat.
  3. Avregistrera enheten från Intune och avinstallera Företagsportal.
  4. Installera appen [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc), som gör att du kan skapa en arbetsprofil utan en EMM för testning.
  5. Följ instruktionerna i [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) för att skapa en arbetsprofil på enheten.
  6. Granska appar som visas i arbetsprofilen. 
  7. Om samma program visas i appen Test DPC förväntas apparna av OEM för den enheten.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Ej godkända hanterade Google Play for Work-butiksappar tas inte bort från sidan Klientappar i Intune
Det här beteendet är förväntat.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>Hanterade Google Play-appar rapporteras inte på bladet Identifierade appar i Intune-portalen
Det här beteendet är förväntat. Endast systemappar som är installerade i arbetsprofilen inventeras på bladet Identifierade appar. Om du vill se hanterade Google Play-program använder du bladet **Hanterade appar**.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>Stöds webbappar för arbetsprofilsregistrerade enheter?
Ja. Mer information finns i [hanterade Google Play-webblänkar](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>Enhetshantering

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Filsökvägen Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files saknas på arbetsprofilsregistrerade enheter

  **Svar**: Det här beteendet är förväntat. Den här sökvägen skapas endast för scenariot med enhetsadministratör (äldre Android-registrering).

  Samla in Företagsportalloggar med hjälp av följande steg:

  1. I Företagsportalappen med brickan trycker du på **Meny** > **Hjälp** > **E-postsupport** och trycker sedan på **Skicka e-post och ladda upp loggar**. 
  2. När du uppmanas att **Skicka begäran om hjälp med** väljer du en av e-postapparna.
  3. Ett e-postmeddelande genereras av IT-administratören med ett incident-ID som kan anges till Microsofts produktsupport.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>Senaste synkroniseringstid för hanterad Google Play har inte uppdaterats på flera dagar
Det här beteendet är förväntat. Synkroniseringen utlöses endast när du utför den manuellt.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>Kryptering krävs när en enhet registreras. Går det att stänga av den?
Nej, Google kräver att enheten krypteras för att en arbetsprofil ska skapas. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>Samsung-enheter blockerar användningen av tangentbord från tredje part såsom SwiftKey
Samsung började framtvinga denna begränsning på enheter med Android 8.0+. Microsoft arbetar för närvarande med Samsung angående det här problemet och publicerar ny information när sådan blir tillgänglig.

## <a name="remote-actions"></a>Fjärråtgärder

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>Alternativet Rensa (fabriksåterställning) är inte tillgängligt för arbetsprofilsregistrerad enhet
Det här beteendet är förväntat. I scenariot för arbetsprofil har MDM-leverantören inte full kontroll över enheten. Det enda tillgängliga alternativet är Dra tillbaka (ta bort företagsdata), som tar bort hela arbetsprofilen och allt dess innehåll.

### <a name="is-device-passcode-reset-supported"></a>Stöds återställning av enhetens lösenord?
För arbetsprofilsregistrerade enheter kan du endast återställa arbetsprofilens lösenord på enheter med Android 8.0 eller senare när:
- arbetsprofilens lösenord är hanterat
- slutanvändaren tillåter att du återställer det.

För dedikerade enheter (COSU) och fullständigt hanterade enheter stöds återställning av enhetens lösenord.


## <a name="next-steps"></a>Nästa steg

- [Felsöka enhetsregistrering i Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Ställ en fråga i Intunes forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Läs Microsoft Intune-supportteamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Läs bloggen om Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)