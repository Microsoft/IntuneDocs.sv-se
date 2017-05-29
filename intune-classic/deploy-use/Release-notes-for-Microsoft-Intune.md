---
title: "Viktig information för Microsoft Intune | Microsoft Docs"
description: "Viktig information för Intune"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2c7563ba79819a59740ba81c078c5540d0792ee5
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="release-notes-for-microsoft-intune"></a>Viktig information för Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune är en integrerad, molnbaserad klienthanteringslösning som tillhandahåller verktyg, rapporter och uppgraderingslicenser för den senaste versionen av Windows. Lösningen hjälper dig även att hålla dina datorer uppdaterade och säkra. Med Intune kan du också hantera mobila enheter i nätverket via Exchange ActiveSync eller direkt via Intune. Följande versionsinformation innehåller viktig information och kända problem i Microsoft Intune.

<!-- 3-6-17: customer asked if this is still current; Stacie asked Chris Baldwin about it. Chris said it's a Samsung issue, but that he hasn't heard any reports about it for months, so he suggested that I share that with the customer and remove this item from the release notes. I'm only going to comment it out in case it resurfaces.
## Android users can’t send email when conditional access for Exchange Online is implemented

**Issue:** Users running Samsung Android 5.1.1 and later on their devices can't send email when conditional access for Exchange Online has been set up. Samsung acknowledges that the issue is in its built-in email client in Android 5.1.1 and later, and is investigating a fix.

**Workaround 1:** Advise users to use the Outlook app for Android.

**Workaround 2:** To let affected users send email, you can follow these steps:

1. Put each affected user in a security group in the “exempted groups” section of the conditional access policy for Exchange Online.
2. Let the user temporarily sync email on the built-in email client.
3. Remove the affected user from the exempted group, and confirm that the user can now send email.

Microsoft will continue to work closely with Samsung on a fix or additional workarounds.
-->


## <a name="changing-resource-access-profiles-between-groups-for-ios-and-android-might-fail"></a>Det kanske inte går att ändra resursåtkomstprofiler mellan grupper för iOS och Android
**Problem:** När du ändrar e-post- eller SCEP-resursåtkomstprofiler (Simple Certificate Enrollment Protocol) mellan grupper kan det uppstå konflikter mellan profilerna som leder till fel. Anta till exempel att du har en befintlig e-postprofil som pekar på en lokal Exchange-server, som är riktad mot grupp A. Sedan skapar du en ny e-postprofil som pekar på Exchange Online, som är riktad mot grupp B. När du flyttar användare från grupp A till grupp B behåller enheterna den lokala Exchange-e-postprofilen och försöker installera e-postprofilen för Exchange Online som är riktad mot grupp B.

I den här situationen kan något av följande inträffa: 
* Om e-postprofilerna A och B är identiska avvisar enheten e-postprofil B eftersom den redan innehåller e-postprofil A.
* Om e-postprofil A inte är identisk med e-postprofil B, som i exemplet, resulterar scenariot i två e-postprofiler på enheten.

> [!NOTE]
> Värdnamnet och attributet som används för användarnamnet kontrolleras för att skilja mellan e-postprofilerna.

Resursåtkomstprofilen (e-postprofilen) togs inte bort från enheten i något av fallen för att förhindra oavsiktlig borttagning av en användares åtkomst till e-post eller klientens SCEP-certifikat.

**Lösning:** Ingen.

## <a name="when-you-enroll-a-windows-81-device-that-must-authenticate-to-a-proxy-server-the-enrollment-process-fails-with-no-visible-cause"></a>När du registrerar en Windows 8.1-enhet som måste autentiseras till en proxyserver misslyckas registreringen utan några synliga tecken på varför
**Problem:** När du registrerar en Windows 8.1-enhet och enheten måste autentiseras mot en proxyserver under registreringsprocessen, så misslyckas registreringen om enheten inte har cachelagrat proxyserverns autentiseringsuppgifter. Om proxyserverns autentiseringsuppgifter inte cachelagras på enheten måste registreringen vänta tills användaren anger autentiseringsuppgifterna. Uppmaningen om att tillhandahålla autentiseringsuppgifter till proxyservern visas dock inte under registreringsprocessen. Resultatet blir att registreringsprocessen inte kan autentiseras gentemot proxyservern. Ingen synlig indikation för det här felet visas för användaren.

**Lösning:** För Windows 8.1-enheter som måste registreras i ett nätverk som kräver en autentiserad proxyserver måste du konfigurera och spara proxyserverns autentiseringsuppgifter innan du registrerar enheten. Så här konfigurerar du och sparar autentiseringsuppgifter på en Windows 8.1-enhet:

1.  Öppna Internet Explorer på Windows 8.1-enheten.
2.  När du uppmanas att ange autentiseringsuppgifter för proxyservern gör du detta och väljer alternativet **Kom ihåg min inloggningsinformation**.
3.  Registrera enheten.

## <a name="windows-phone-81-devices-fail-to-enroll-with-microsoft-intune-when-device-authentication-is-enabled-in-ad-fs"></a>Det går inte att registrera Windows Phone 8.1-enheter med  Microsoft Intune när enhetsautentisering är aktiverad i AD FS
**Problem:** När du registrerar en Windows Phone 8.1-enhet misslyckas registreringen om den valfria inställningen för autentisering är aktiverad som en del av den globala autentiseringsprincipen i AD FS (Active Directory Federation Services).

**Lösning:** Inaktivera enhetsautentisering på AD FS-servern genom att avmarkera **Aktivera enhetsautentisering** i **Redigera global autentiseringsprincip**. Mer information finns i [Konfigurera autentiseringsprinciper](http://technet.microsoft.com/library/dn486781.aspx).


## <a name="microsoft-intune-app-wrapping-tool-for-android-has-no-built-in-uninstall-capability"></a>Microsoft Intune App Wrapping-verktyget för Android har ingen inbyggd avinstallationsfunktion
**Problem:** **Microsoft Intunes apphanteringsverktyg för Android** har ingen inbyggd funktion för att avinstallera verktyget.

**Lösning:** Bläddra till den palats där du installerade verktyget och ta bort katalogen. Standardplatsen för installationen är: **C:\Program Files /intune-classic/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## <a name="remote-assistance-is-not-available-on-computers-that-run-windows-8-or-windows-81"></a>Fjärrhjälp är inte tillgänglig på datorer som kör Windows 8 eller Windows 8.1
**Problem:** I den här versionen är fjärrhjälpsfunktionen inte tillgänglig på datorer som kör Windows 8 eller Windows 8.1.

**Lösning:** Ingen.

## <a name="alert-notifications-for-recipients-that-are-automatically-added-might-not-work"></a>Det finns en risk att varningsmeddelanden för mottagare som läggs till automatiskt inte fungerar
**Problem:** Mottagare som läggs till automatiskt till aviseringsmeddelanden får kanske inte alltid meddelanden.

**Lösning:** Om du vill säkerställa att mottagarna får aviseringar om meddelanden bör du lägga till mottagarna manuellt till varningsmeddelanden.

## <a name="language-support-in-the-azure-portal"></a>Språkstöd i Azure Portal
Azure Portal stöder dessa språk: kinesiska (förenklad), kinesiska (traditionell), tjeckiska, holländska, engelska, tyska, ungerska, italienska, japanska, portugisiska (Brasilien), portugisiska (Portugal), ryska, spanska, engelska, franska, koreanska, polska, svenska och turkiska.

Intune-administrationskonsolen och mobilmiljöerna för användarna stöder danska, grekiska, finska, norska och rumänska, samt alla de språk som stöds av Azure Portal.

