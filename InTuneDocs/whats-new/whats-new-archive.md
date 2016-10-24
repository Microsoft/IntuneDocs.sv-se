---
title: Nyhetsarkiv | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ec77bc20bf429c804cb502bb46fc549d080a94ac
ms.openlocfilehash: 14698e5f40e76e370e178aeb6187d89fbc5cb2bd


---
## September 2016
## Nya funktioner, meddelanden och information
* [Villkorlig åtkomst till Windows](#windows-conditional-access)
* [Stöd för iOS 10](#ios-10-support)
* [Programhanteringsverktyget stöder MAM utan enhetsregistrering för Android och iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [Intune-grupper påbörjar övergången till Azure Active Directory i september](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Lookout-integrering för att skydda Android-enheter](#lookout-integration-to-protect-android-devices)
* [Uppdateringar av företagsportalen för Android, iOS och Windows](#company-portal-updates)
* [Intune-ordlista](#intune-glossary)
* [Kommande nyheter](#whats-coming)

## Villkorlig åtkomst till Windows
Nu kan du skapa principer för villkorlig åtkomst via Intune-administratörskonsolen om du vill blockera Windows-datorer från att få åtkomst till Exchange Online och SharePoint Online. Du kan även skapa principer för villkorlig åtkomst för att blockera åtkomst till stationära och universella Office-program.

## Stöd för iOS 10
Befintliga Intune MDM- och MAM-scenarier är kompatibla med iOS 10. Om du vill få tips kan du läsa [Intune-supportteamets blogg](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## Programhanteringsverktyget stöder MAM utan enhetsregistrering för Android och iOS
Intunes programhanteringsverktyg är ett kommandoradsverktyg som används för att aktivera Intune MAM på verksamhetsspecifika appar för iOS och Android. Det är det enklaste sättet att införliva SDK:n för Intune MAM i appen, så att appen kan verkställa MAM-principer som distribueras genom Intune. Med MAM-principer kan du:

1. Kryptera appens data.
2. Kräva att informationsanställda anger en PIN-kod när appen startas.
3. Tillåta att appen överför data endast till andra hanterade appar.
4. Förhindra att appen säkerhetskopierar data till Android, iTunes och iCloud.
5. Endast tillåta åtgärderna att klippa ut, kopiera och klistra in för andra hanterade appar.

Förhandsversion av den uppdaterade versionen av Intunes programhanteringsverktyg stöder nu MAM utan enhetsregistrering på interna verksamhetsspecifika appar för iOS och Android. Det innebär att slutanvändarna inte behöver registrera sina enheter med Intune för att kunna använda MAM-aktiverade verksamhetsspecifika appar.

Alla kan testa den allmänna förhandsversionen av programvaran och läsa användbar dokumentation som finns i GitHub för msintuneappsdk:

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Innan du installerar och använder förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS måste du:

* Granska Microsofts licensvillkor för förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android och iOS
* Skriv ut och behåll en kopia av licensvillkoren för framtida referens. Genom att ladda ned och använda förhandsversionen av Microsoft Intune-programhanteringsverktyget för Android godkänner du licensvillkoren. Om du inte accepterar villkoren har du inte rätt att använda programvaran.
<!---TFS 1235607--->

## Intune-grupper påbörjar övergången till Azure Active Directory i september
Vissa nya Intune-konton kommer att använda Azure Active Directory-säkerhetsgrupper i stället för Intune-användargrupper. Du kommer att veta att du arbetar med säkerhetsgrupper, eftersom sidan för Intune-portalgrupper har en länk som dirigerar dig till Azure-hanteringsportalen.

## Lookout-integrering för att skydda Android-enheter
Microsoft integrerar med Lookouts lösning för mobilhotsskydd för att skydda mobila Android-enheter genom att identifiera skadlig kod, riskfyllda appar med mera, på enheter. Lookouts lösning hjälper dig att bestämma hotnivån, vilken kan konfigureras. Du kan skapa en regel för policy för efterlevnad i Intune för att fastställa enhetens efterlevnad baserat på riskbedömningen av Lookout. Genom att använda åtkomstprinciper kan du tillåta eller blockera åtkomst till företagsresurser utifrån enhetens efterlevnadsstatus.

Slutanvändare med icke-kompatibla enheter kommer att uppmanas att registrera och måste installera Lookout for Work-appen på Android-enheter, aktivera appen och åtgärda hot som rapporteras i Lookout for Work-appen för att få åtkomst. Mer information finns i [Begränsa åtkomsten baserat på enhet, nätverk och programrisk](restrict-access-based-on-device-network-app-risk.md).


## Uppdateringar av företagsportalen

### Android

**Tillägg av "Meddelanden" på företagsportalen för Android**<br/>
En ny ikon för meddelanden har lagts till på företagsportalen för Android på startsidan. När användaren trycker på ikonen visas sidan Meddelanden. På sidan visas alla objekt som kräver åtgärder i företagsportalappen, till exempel inkompatibla enheter, registreringsuppdatering och aktivering av registreringar. Om du använder företagsportalappen för iOS kan du redan se dessa meddelanden. Den nya sidan Meddelanden innebär att användarna inte kommer att se sidan Konfiguration av företagsåtkomst varje gång de startar eller återupptar företagsportalen, förutsatt att enheten redan är registrerad. Om du skapar din egen vägledning för slutanvändare kanske du vill uppdatera din dokumentation för den här ändringen. Sök efter uppdaterade skärmbilder [här](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->

**Skicka feedback från företagsportalen för Android**</br>
En ny artikel har lagts till i menyn i företagsportalen för Android. Om du trycker på **Hjälp och feedback** visas tre åtgärder:
* Använd **Få hjälp** för att rapportera ett problem med företagsportalen till din IT-avdelning. IT-avdelningen kommer att skapa ett e-postmeddelande med din e-postklient och bifoga företagsportal-loggarna till det. **Få hjälp** ersätter funktionen **Skicka data** på sidan **Inställningar**.
* Använd **Lämna feedback** för att skicka feedback till företagsportal-teamet.
* Använd **Betygsätt vår app** för att lämna ett betyg eller en recension för företagsportalappen på Google Play.

### iOS
**Ändringar i stödet för iOS-företagsportalappen**<br/>
Alla användare av Microsoft Intune-företagsportalappen för iOS måste nu använda den senaste versionen. Nya användare kan endast ladda ned den senaste versionen och aktuella användare måste uppdatera till den. Den senaste versionen kräver iOS 8.0 eller senare, så enheter som använder äldre iOS-versioner kan inte använda företagsportalen eller registrera sig förrän de uppdaterar sin enhet till iOS 8.0 eller senare och sedan uppdaterar företagsportalsappen till den senaste versionen. Registrerade enheter med tidigare versioner än iOS 8.0 fortsätter att hanteras och visas i Intune-administratörskonsolen.
<!---TFS 1283165--->

**Förbättringar i hur iOS-slutanvändare får sina appar**<br/>
Följande ändringar har gjorts av appanelerna i företagsportalsappen för iOS så att användarna ska kunna få flera vyer på en och samma plats, nämligen företagsportalens webbplats för alla deras appar. Apples begränsningar förhindrar att verksamhetsspecifika appar och hanterade App Store-appar listas i företagsportalsappen, och kräver att användarna besöker olika vyer om de vill hitta alla sina appar.

- Panelen **Företagsappar** visade tidigare en lista över alla program under fliken ALLA på företagsportalens webbplats, och den kommer att fortsätta fungera på samma sätt. Namnet på panelen har ändrats till **Alla appar**.
- Panelen **Andra appar** visade tidigare en vy i företagsportalsappen som visar alla appar som Apple tillåter att företagsportalsappen visar. Namnet på panelen har ändrats till **Aktuella appar**, och om du trycker på panelen öppnas fliken AKTUELLT på företagsportalens webbplats.
-  Panelen **Kategorier** visade tidigare en vy i företagsportalsappen som listar appkategorier. Panelens namn har inte ändrats, men den pekar nu på fliken KATEGORIER på företagsportalens webbplats.
Du kan söka efter uppdaterade skärmbilder [här](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

**Uppmanar till installation av appen iOS Managed Browser om IT Pro anger detta krav för en app**<br/>
Enhetens företagsportalsapp uppmanar dig till att installera den hanterade webbläsaren innan ett webbklipp kan installeras, om du har konfigurerat detta webbklipp så att det bara kan öppnas i den hanterade webbläsaren och om du ännu inte har installerat den hanterade webbläsaren.
<!---TFS 1228570--->

### Windows
**En feedback-knapp har lagts till i Windows Phone 8.1-företagsportalappen**<br/>
I företagsportalappen för Windows Phone 8.1 kan slutanvändarna skicka feedback om appen med hjälp av en ny "skicka feedback"-knapp. För att hitta knappen trycker användare på "trepunkts"-menyn längst ned till höger på skärmen Företagsportalapp och sedan på **skicka feedback**. Den insamlade, avidentifierade feedbacken hjälper Microsoft att förbättra företagsportalappen för användare.
<!---TFS 1317806--->

## Intune-ordlista</br>
Vi har lagt till ett nytt [ordlisteavsnitt](https://docs.microsoft.com/intune/understand-explore/intune-glossary) i biblioteket som hjälper dig att förstå några av de termer som används i Intune-produkten.



<!--HONumber=Oct16_HO2-->


