---
title: Funktioner för hantering av enheter i Microsoft Intune
description: Läs om hur Intune hjälper dig att hantera de enheter som du registrerar.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 415005ee58367a189986e9d7bd0ef693f14bc5c9
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048358"
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funktioner för hantering av registrerade enheter i Microsoft Intune

Med Microsoft Intune kan du hantera ett antal enheter genom att *registrera* dem i tjänsten. Du kan registrera vissa typer av enheter själv, eller så kan användare registrera sig via *företagsportalappen*. Med registreringen kan de bläddra och installera appar, se till att deras enheter är kompatibla med företagets principer och kontakta sin IT-support.

Den här artikeln innehåller en fullständig lista över de funktioner du får när du registrerar enheter.

Hantering, inventering, appdistribution, etablering och tillbakadragning hanteras via Intune i Azure-portalen.

Användare får tillgång till företagsportalen där de kan installera appar, registrera och avregistrera enheter och kontakta IT-avdelningen eller supportavdelningen.



## <a name="device-security-and-configuration"></a>Enheternas säkerhet och konfiguration

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Konfigurationsprinciper<br><br>Anpassade principer| Gör att du kan hantera många inställningar och funktioner på mobila enheter i organisationen. Du kan till exempel kräva ett lösenord, begränsa antalet lösenordsförsök, begränsa tiden tills skärmen låser sig, ställa in ett utgångsdatum för lösenord och förhindra återanvändningen av gamla lösenord. Du kan också styra användningen av maskin- och programvarufunktioner, till exempel kameran på enheten eller webbläsaren.<br><br>Använd anpassade principer när konfigurationsprinciperna saknar den inställning som du behöver. För iOS-enheter kan du importera inställningar som du har exporterat från verktyget Apple Configurator. För andra enheter kan du använda OMA-URI-inställningarna (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera inställningarna och funktioner på enheten.|[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](device-compliance-get-started.md)|
|Fjärrensning, fjärrlåsning och återställning av lösenord|Raderar känsliga data när en enhet tappas bort eller blir stulen. Exempel: du kan fjärrlåsa enheten, återställa den till fabriksinställningarna eller endast rensa företagsdata.<br><br>Du kan nollställa lösenord om användare förlorar åtkomst till sina enheter, låsa försvunna eller stulna enheter, eller till och med radera data från försvunna eller stulna enheter.|Skydda dina enheter med [fjärrlåsning](device-remote-lock.md) och [lösenordsåterställning](device-passcode-reset.md)|
|Helskärmsläge|Gör att du kan låsa vissa funktioner i mobila enheter, till exempel skärmbild och strömbrytarens funktion. Du kan även begränsa enheterna till att kunna köra en enda app som du anger. |[Inställningar för iOS-konfigurationsprinciper i Microsoft Intune](device-restrictions-ios.md)|

## <a name="app-management"></a>Apphantering

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Appdistribution och -hantering|Tillhandahåller verktyg som hjälper dig att hantera mobila appar genom hela deras livscykel, inklusive appdistribution från installationsfiler och appbutiker, detaljerad övervakning av appstatus och borttagning av appar.|[Distribuera appar i Microsoft Intune](apps-deploy.md)|
|Kompatibla och icke-kompatibla appar|Gör att du kan ange listor med kompatibla appar (som användarna får installera) och icke-kompatibla appar (som användarna inte får installera).|[Principinställningar för iOS i Microsoft Intune](device-restrictions-ios.md)|
|Hantering av mobila program|Konfigurerar begränsningar för appar med hjälp av hantering av mobilprogram för alla enheter (både enheter som hanteras med Intune och enheter som inte hanteras med Intune). Du kan öka säkerheten för företagets data genom att begränsa åtgärder, som exempelvis kopiera och klistra in, extern säkerhetskopiering av data och överföring av data mellan appar.|[Konfigurera och distribuera hanteringsprinciper för mobilprogram i konsolen för Microsoft Intune](app-wrapper-prepare-android.md)|
|Konfiguration av iOS-mobilapp|Använder konfigurationsprinciper för mobilappar om du vill definiera inställningar för iOS-appar som kan krävas när användaren kör appen. En app kan till exempel kräva att användaren anger ett portnummer eller inloggningsinformation. Du kan effektivisera appkonfigurationen och minska antalet supportsamtal.|[Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](app-configuration-policies-use-ios.md)|
|Etableringsprofiler för iOS-mobilappar|Hjälper dig att distribuera etableringsprofiler till iOS-appar som snart upphör att gälla. |[Använd etableringsprofilprinciper för iOS för att förhindra att dina appar upphör att gälla](app-provisioning-profile-ios.md)|
|Hanterad webbläsare|Konfigurerar principer för hanterade webbläsare för att styra vilka webbplatser som enhetsanvändarna ska kunna besöka. Du kan dessutom använda principer för hantering av mobila appar på den hanterade webbläsaren.|[Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](app-configuration-managed-browser.md)|
|Windows Hello för företag|Gör att du kan integrera med Microsoft Hello för företag, som är en alternativ inloggningsmetod för Windows 10 som använder Active Directory lokalt eller Azure Active Directory för att ersätta ett lösenord, smartkort eller virtuella smartkort.|[Kontrollera Windows Hello för företag-inställningar på enheter med Microsoft Intune](windows-hello.md)|
|Volyminköpsappar|Hjälper dig att hantera appar som du har köpt via ett volyminköpsprogram genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger.|[Hantera volyminköpta appar med Microsoft Intune](vpp-apps.md)|

## <a name="company-resource-access"></a>Åtkomst till företagsresurser

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Certifikatprofiler|Skapar och distribuerar betrodda certifikatprofiler och SCEP-certifikat (Simple Certificate Enrollment Protocol) som används för att skydda och autentisera Wi-Fi-, VPN-, och e-profiler.|[Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](certificates-configure.md)|
|Wi-Fi-profiler|Distribuerar trådlösa nätverksinställningar till användarna. Genom att distribuera de här inställningarna gör du det enklare för användaren att ansluta till företagets nätverk.|[Wi-Fi-anslutningar i Microsoft Intune](wi-fi-settings-configure.md)|
|E-postprofiler|Skapar och distribuerar e-postinställningar till enheter så att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.|[Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](email-settings-configure.md)|
|VPN-profiler|Distribuerar VPN-inställningar till användare och enheter i din organisation. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till resurser i företagets nätverk.|[VPN-anslutningar i Microsoft Intune](device-profiles.md#vpn)|
|Villkorliga åtkomstprinciper|Hanterar åtkomst till Microsoft Exchange-e-post och SharePoint Online från enheter som inte hanteras av Intune.|[Begränsa åtkomst till e-post och SharePoint med Microsoft Intune](app-based-conditional-access-intune.md)|

## <a name="next-steps"></a>Nästa steg

[Visa en lista över enheter som du kan hantera](device-management.md).
