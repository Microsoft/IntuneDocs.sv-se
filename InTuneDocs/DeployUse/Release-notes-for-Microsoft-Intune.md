---
title: "Viktig information för Microsoft Intune | Microsoft Intune"
description: "Viktig information för Intune"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db9479b2-582d-4a1a-9fbc-fbfc6c680e6f
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7549b5af84e5a1712c2e1649b1afe03718d53dcc
ms.openlocfilehash: ad95830b37d3b83554b64d2f82fa537e603190d6


---

# Viktig information för Microsoft Intune
Microsoft Intune är en integrerad, molnbaserad klienthanteringslösning som tillhandahåller verktyg, rapporter och uppgraderingslicenser för den senaste versionen av Windows, och som hjälper dig att hålla dina datorer uppdaterade och säkra. Med Intune kan du också hantera mobila enheter i nätverket via Exchange ActiveSync eller direkt via Intune. Följande versionsinformation innehåller viktig information och kända problem i Microsoft Intune.


## Android-användare kan inte skicka e-post när villkorlig åtkomst för Exchange Online har implementerats

Användare som kör Samsung Android 5.1.1 och senare på sina enheter kan inte skicka e-post när villkorlig åtkomst för Exchange Online har konfigurerats. Samsung bekräftar att problemet ligger i deras inbyggda e-postklient i Android 5.1.1 och senare, och arbetar för närvarande med att åtgärda felet.

**Lösning 1:** Rekommendera slutanvändare att använda Outlook-appen för Android.

**Lösning 2:** Se till att berörda användare kan skicka e-post genom att följa dessa steg:

1. Lägg till den berörda användaren i en säkerhetsgrupp under Undantagna grupper i principen för villkorlig åtkomst för Exchange Online.
2. Tillåt att användaren tillfälligt synkroniserar e-post i den inbyggda e-postklienten.
3. Ta bort den berörda användaren från den undantagna gruppen och bekräfta att användaren kan skicka e-post.

Microsoft och Samsung arbetar tillsammans med att ta fram en lösning eller fler sätt att komma runt problemet.



## Det kanske inte går att ändra resursåtkomstprofiler mellan grupper för iOS och Android
**Problem:** När du ändrar e-post- eller SCEP-resursåtkomstprofiler (Simple Certificate Enrollment Protocol) mellan grupper kan det uppstå konflikter mellan profilerna som leder till fel. Anta till exempel att du har en befintlig e-postprofil som pekar på den lokala Exchange-servern, som är riktad mot grupp A, och att du sedan skapar en ny e-postprofil som pekar på Exchange Online, som är riktad mot grupp B. När du flyttar användare från grupp A till grupp B behåller enheterna den lokala Exchange-e-postprofilen och försöker installera e-postprofilen för Exchange Online som är riktad mot grupp B.

I den här situationen kan något av följande inträffa: 
* Om e-postprofilerna A och B är identiska avvisar enheten e-postprofil B eftersom den redan innehåller e-postprofil A.
* Om e-postprofil A inte är identisk med e-postprofil B, som i exemplet ovan, resulterar scenariot i två e-postprofiler på enheten.

**Obs!** Värdnamnet och attributet som används för användarnamnet kontrolleras för att skilja mellan e-postprofilerna.

Resursåtkomstprofilen (e-postprofilen) togs inte bort från enheten i något av fallen ovan för att förhindra oavsiktlig borttagning av en användares åtkomst till e-post eller klientens SCEP-certifikat.

**Lösning:** Ingen.

## När du registrerar en Windows 8.1-enhet som måste autentiseras till en proxyserver misslyckas registreringen utan några synliga tecken på vad som kan vara orsaken till problemet
**Problem:** När du registrerar en Windows 8.1-enhet och enheten måste autentiseras mot en proxyserver under registreringsprocessen, så misslyckas registreringen om enheten inte har cachelagrat proxyserverns autentiseringsuppgifter. Om proxyserverns autentiseringsuppgifter inte cachelagras på enheten måste registreringen vänta tills användaren anger autentiseringsuppgifterna. Uppmaningen om att tillhandahålla autentiseringsuppgifter till proxyservern visas dock inte under registreringsprocessen. Resultatet blir att autentiseringen gentemot proxyservern inte kan genomföras under samtidigt som det inte visas någon tydlig indikation på problemet för användaren.

**Lösning:** För Windows 8.1-enheter som måste registreras i ett nätverk som kräver en autentiserad proxyserver måste du konfigurera och spara proxyserverns autentiseringsuppgifter innan du registrerar enheten. Så här konfigurerar du och sparar autentiseringsuppgifter på en Windows 8.1-enhet:

1.  Öppna **Internet Explorer** på Windows 8.1-enheten.

2.  När du uppmanas att ange autentiseringsuppgifter för proxyservern gör du detta och väljer alternativet **Kom ihåg min inloggningsinformation**.

3.  Registrera enheten.

## Det går inte att registrera Windows Phone 8.1-enheter med  Microsoft Intune när enhetsautentisering är aktiverad i AD FS
**Problem:** När du registrerar en Windows Phone 8.1-enhet misslyckas registreringen om den valfria inställningen för autentisering är aktiverad som en del av den globala autentiseringsprincipen i AD FS (Active Directory Federation Services).

**Lösning:** Inaktivera enhetsautentisering på AD FS-servern genom att avmarkera **Aktivera enhetsautentisering** i **Redigera global autentiseringsprincip**. Mer information finns i [Konfigurera autentiseringsprinciper](http://technet.microsoft.com/library/dn486781.aspx)


## Microsoft Intune App Wrapping-verktyget för Android har ingen inbyggd avinstallationsfunktion
**Problem:** **Microsoft Intunes apphanteringsverktyg för Android** har ingen inbyggd funktion för att avinstallera verktyget.

**Lösning:** Bläddra till den palats där du installerade verktyget och ta bort katalogen. Standardinstallationsplatsen är: **C:\Program Files (x86)\Microsoft Intune Mobile Application Management\Android\App Wrapping Tool**. Mer information om apphanteringsverktyget finns i [Förbereda Android-appar för hantering med apphanteringsverktyget](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool).

## Fjärrhjälp är inte tillgänglig på datorer som kör Windows 8 eller Windows 8.1
**Problem:** I den här versionen är fjärrhjälpsfunktionen inte tillgänglig på datorer som kör Windows 8 eller Windows 8.1.

**Lösning:** Ingen.

## Det finns en risk att varningsmeddelanden för mottagare som läggs till automatiskt inte fungerar
**Problem:** Mottagare som läggs till automatiskt till aviseringsmeddelanden får kanske inte alltid meddelanden.

**Lösning:** Om du vill säkerställa att mottagarna får aviseringar om meddelanden bör du lägga till mottagarna manuellt till varningsmeddelanden.

## Språkstöd i Azure Preview Portal
Azure Preview Portal bygger på en ny plattform och stöder följande språk – kinesiska (förenklad), kinesiska (traditionell), tjeckiska, holländska, engelska, tyska, ungerska, italienska, japanska, portugisiska (Brasilien), portugisiska (Portugal), ryska, spanska, engelska, franska, koreanska, polska, svenska och turkiska.

Intune-administrationskonsolen och mobilmiljöerna för slutanvändarna stöder danska, grekiska, finska, norska och rumänska, förutom de språk som stöds av Azure Preview Portal.



<!--HONumber=Sep16_HO2-->


