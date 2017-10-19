---
title: "Funktioner för hantering av registrerade enheter"
description: "Läs om hur Intune hjälper dig att hantera de enheter som du registrerar."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/12/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f543996bf573aef9dd606ae403185da65a3599d2
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="enrolled-device-management-capabilities-of-microsoft-intune"></a>Funktioner för hantering av registrerade enheter i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Med Microsoft Intune kan du hantera ett antal enheter genom att *registrera* dem i tjänsten. Du kan registrera vissa typer av enheter själv, eller så kan användare registrera sig via *företagsportalappen*. Användarna kan även utföra åtgärder som att söka efter och installera appar, vilket säkerställer att deras enheter är kompatibla med företagets principer. Och de kan kontakta IT-support.

Det här avsnittet innehåller en fullständig lista över de funktioner du får när du registrerar enheten.

Hantering, inventering, appdistribution, etablering och tillbakadragning hanteras via administrationskonsolen för Intune. Användare får tillgång till företagsportalen där de kan installera appar, registrera och avregistrera enheter och kontakta IT-avdelningen eller supportavdelningen.



## <a name="device-security-and-configuration"></a>Enheternas säkerhet och konfiguration

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Konfigurationsprinciper<br><br>Anpassade principer| Gör att du kan hantera många inställningar och funktioner på mobila enheter i organisationen. Du kan till exempel kräva ett lösenord, begränsa antalet lösenordsförsök, begränsa tiden tills skärmen låser sig, ställa in ett utgångsdatum för lösenord och förhindra återanvändningen av gamla lösenord. Du kan också styra användningen av maskin- och programvarufunktioner, till exempel kameran på enheten eller webbläsaren.<br><br>Använd anpassade principer när konfigurationsprinciper inte innehåller inställningen du behöver. För iOS-enheter kan du importera inställningar som du har exporterat från verktyget Apple Configurator. För andra enheter kan du använda OMA-URI-inställningarna (Open Mobile Alliance Uniform Resource Identifier) för att konfigurera inställningarna och funktioner på enheten.|[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)|
|Fjärrensning, fjärrlåsning och återställning av lösenord|Raderar känsliga data när en enhet tappas bort eller blir stulen. Exempel: du kan fjärrlåsa enheten, återställa den till fabriksinställningarna eller endast rensa företagsdata.<br><br>Du kan nollställa lösenord om användare förlorar åtkomst till sina enheter, låsa försvunna eller stulna enheter, eller till och med radera data från försvunna eller stulna enheter.|[Skydda dina enheter med fjärrlåsning och lösenordsåterställning](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)|
|Helskärmsläge|Gör att du kan låsa vissa funktioner i mobila enheter, till exempel skärmbild och strömbrytarens funktion. Du kan även begränsa enheterna till att kunna köra en enda app som du anger.|[Inställningar för iOS-konfigurationsprinciper i Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|

## <a name="app-management"></a>Apphantering

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Appdistribution och -hantering|Tillhandahåller verktyg som hjälper dig att hantera mobila appar genom hela deras livscykel, inklusive appdistribution från installationsfiler och appbutiker, detaljerad övervakning av appstatus och borttagning av appar.|[Distribuera appar i Microsoft Intune](/intune-classic/deploy-use/deploy-apps)|
|Kompatibla och icke-kompatibla appar|Gör att du kan ange listor med kompatibla appar (som användarna får installera) och icke-kompatibla appar (som användarna inte får installera).|[Principinställningar för iOS i Microsoft Intune](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Hantering av mobila program|Konfigurerar begränsningar för appar med hjälp av hantering av mobilprogram för alla enheter (både enheter som hanteras med Intune och enheter som inte hanteras med Intune). Med hjälp av dessa principer kan du öka säkerheten för företagets data genom att begränsa åtgärder, exempelvis kopiera och klistra in, extern säkerhetskopiering av data och överföring av data mellan appar.|[Konfigurera och distribuera hanteringsprinciper för mobilprogram i konsolen för Microsoft Intune](/intune/app-wrapper-prepare-android)|
|Konfiguration av iOS-mobilapp|Använder konfigurationsprinciper för mobilappar om du vill definiera inställningar för iOS-appar som kan krävas när användaren kör appen. En app kan till exempel kräva att användaren anger ett portnummer eller inloggningsinformation. Det kan effektivisera appkonfigurationen och minska antalet supportsamtal.|[Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Etableringsprofiler för iOS-mobilappar|Hjälper dig att distribuera etableringsprofiler till iOS-appar som snart upphör att gälla. |[Använd etableringsprofilprinciper för iOS för att förhindra att dina appar upphör att gälla](/intune-classic/deploy-use/ios-mobile-app-provisioning-profiles)|
|Hanterad webbläsare|Konfigurerar principer för hanterade webbläsare för att styra vilka webbplatser som enhetsanvändarna ska kunna besöka. Du kan dessutom använda principer för hantering av mobila appar på den hanterade webbläsaren.|[Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Windows Hello för företag|Gör att du kan integrera med Microsoft Hello för företag, som är en alternativ inloggningsmetod för Windows 10 som använder Active Directory lokalt eller Azure Active Directory för att ersätta ett lösenord, smartkort eller virtuella smartkort.|[Kontrollera Windows Hello för företag-inställningar på enheter med Microsoft Intune](/intune-classic/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|
|Volyminköpsappar|Hjälper dig att hantera appar som du har köpt via ett volyminköpsprogram genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger.|[Hantera volyminköpta appar med Microsoft Intune](/intune-classic/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)|

## <a name="company-resource-access"></a>Åtkomst till företagsresurser

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Certifikatprofiler|Skapar och distribuerar betrodda certifikatprofiler och SCEP-certifikat (Simple Certificate Enrollment Protocol) som används för att skydda och autentisera Wi-Fi-, VPN-, och e-profiler.|[Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi-profiler|Distribuerar trådlösa nätverksinställningar till användarna. Genom att distribuera de här inställningarna gör du det enklare för användaren att ansluta till företagets nätverk.|[Wi-Fi-anslutningar i Microsoft Intune](/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)|
|E-postprofiler|Skapar och distribuerar e-postinställningar till enheter. Detta innebär att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.|[Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN-profiler|Distribuerar VPN-inställningar till användare och enheter i din organisation. Genom att distribuera inställningarna gör du det enklare för användarna att ansluta till resurser i företagets nätverk.|[VPN-anslutningar i Microsoft Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune)|
|Villkorliga åtkomstprinciper|Hanterar åtkomst till Microsoft Exchange-e-post och SharePoint Online från enheter som inte hanteras av Intune.|[Begränsa åtkomst till e-post och SharePoint med Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## <a name="inventory-and-reporting"></a>Inventering och rapporter

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Inventering och rapporter|Hittar information om de enheter som du hanterar och den programvara som används i enheterna.|[Förstå dina enheter med inventering i Microsoft Intune](/intune-classic/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|
