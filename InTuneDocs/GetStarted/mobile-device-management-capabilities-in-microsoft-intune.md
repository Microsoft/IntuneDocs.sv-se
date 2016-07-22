---
title: "Funktioner för hantering av mobila enheter | Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f23b3ee7-78da-4e53-9fc2-78e58401bcf9
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 0f460165f251acf95f4af36afa39409d3eb21162


---
# Funktioner för hantering av mobila enheter i Microsoft Intune

Med Microsoft Intune kan du hantera ett antal enheter genom att *registrera* dem i tjänsten. Användarna kan sedan använda en *företagsportal* för att utföra ett antal åtgärder, till exempel registrera sin enhet, bläddra bland och installera appar, se till att enheten är kompatibel med företagets principer och kontakta IT-supporten.
Det här avsnittet innehåller en fullständig lista över de funktioner som registrering av enheter erbjuder.

Hantering, inventering, appdistribution, etablering och tillbakadragning hanteras via administrationskonsolen för Intune. Användare får tillgång till företagsportalen vilken låter dem installera appar, registrera och avregistrera enheter och för att få hjälp att kontakta IT-avdelningen eller supportavdelningen.



## Enheternas säkerhet och konfiguration

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Konfigurationsprinciper<br><br>Anpassade principer|Med konfigurationsprinciper för mobila enheter kan du hantera många inställningar och funktioner på mobila enheter i organisationen. Du kan till exempel kräva ett lösenord, begränsa antalet lösenordsförsök, begränsa tiden tills skärmen låser sig, ställa in ett utgångsdatum för lösenord och förhindra återanvändningen av gamla lösenord. Du kan också styra användningen av maskin- och programvarufunktioner, till exempel kameran på enheten eller webbläsaren<br><br>Använd anpassade principer när konfigurationsprinciper inte innehåller inställningen du behöver. För iOS-enheter kan du importera inställningar som du har exporterat från verktyget Apple Configurator. För andra enheter kan du använda OMA-URI-inställningarna för att konfigurera inställningarna och funktioner på enheten.|[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)<br />|
|Fjärrensning, fjärrlåsning och återställning av lösenord|Radera känsliga data när en enhet tappas bort eller blir stulen. Exempel: du kan fjärrlåsa enheten, återställa den till fabriksinställningarna eller endast rensa företagsdata.<br>Du kan nollställa lösenord om användare förlorar åtkomst till sina enheter, låsa försvunna eller stulna enheter, eller till och med radera data från försvunna eller stulna enheter.|[Skydda dina enheter med fjärrlåsning och lösenordsåterställning](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune) och [Dra tillbaka enheter från Intune-hantering](/intune/deploy-use/retire-devices-from-microsoft-intune-management)|
|Helskärmsläge|Gör att du kan låsa vissa funktioner i mobila enheter, till exempel skärmbild och strömbrytarens funktion. Du kan även begränsa enheterna till att kunna köra en enda app som du anger.|[Inställningar för iOS-konfigurationsprinciper i Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|

## Apphantering

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Appdistribution och -hantering|Tillhandahåller verktyg som hjälper dig att hantera mobila appar genom hela deras livscykel, inklusive appdistribution från installationsfiler och appbutiker, detaljerad övervakning av appstatus och borttagning av appar.|[Distribuera appar i Microsoft Intune](/intune/deploy-use/deploy-apps)|
|Kompatibla och icke-kompatibla appar|Gör att du kan ange listor med kompatibla appar (som användarna ska kunna installera) och icke-kompatibla appar (som inte får installeras av användarna).|[Principinställningar för iOS i Microsoft Intune](/intune/deploy-use/ios-policy-settings-in-microsoft-intune)|
|Hantering av mobila program|Konfigurera begränsningar för appar med hjälp av hantering av mobilprogram för både enheter som du hanterar med Intune och enheter som inte hanteras av Intune. Med hjälp av dessa principer kan du öka säkerheten för företagets data genom att begränsa åtgärder, exempelvis kopiera och klistra in, extern säkerhetskopiering av data och överföring av data mellan appar.|[Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)<br><br>[Skapa och distribuera hanteringsprinciper för mobilappar med Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)<br /><br />[Förbereda iOS-appar för hantering av mobila program med Microsoft Intune App Wrapping-verktyg](/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)<br /><br />[Förbered Android-appar för hantering av mobila program med Microsoft Intunes App-Wrapping-verktyg](/intune/deploy-use/prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)|
|Konfiguration av mobilapp|Använd konfigurationsprinciper för mobilappar om du vill definiera inställningar för iOS-appar som kan krävas när användaren kör appen. En app kan till exempel kräva att användaren anger ett portnummer för inloggningsinformation. Det kan effektivisera appkonfiguration och minska antalet samtal till supportavdelningen.|[Konfigurera iOS-appar med konfigurationsprinciper för mobilappar i Microsoft Intune](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)|
|Hanterad webbläsare|När du har distribuerat den hanterade webbläsaren till dina användare kan du konfigurera en princip för hanterade webbläsare om du vill kunna kontrollera vilka webbplatser de ska kunna besöka. Du kan dessutom använda principer för hantering av mobila appar på den hanterade webbläsaren.|[Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)|
|Microsoft Passport|Med Intune kan du integrera med Microsoft Passport for Work, som är en alternativ inloggningsmetod för Windows 10 som använder Active Directory eller ett Azure Active Directory-konto för att ersätta ett lösenord, smartkort eller virtuellt smartkort.|[Kontrollera Microsoft Passport-inställningar på enheter med Microsoft Intune](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune)|

## Åtkomst till företagsresurser

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Certifikatprofiler|Skapa och distribuera betrodda certifikatprofiler och SCEP-certifikat (Simple Certificate Enrollment Protocol) som används för att skydda och autentisera Wi-Fi-, VPN-, och e-profiler.|[Skydda resursåtkomst med certifikatprofiler i Microsoft Intune](/intune/deploy-use/secure-resource-access-with-certificate-profiles)|
|Wi-Fi-profiler|Distribuera trådlösa nätverksinställningar till användarna. Genom att distribuera de här inställningarna gör du det enklare för slutanvändaren att ansluta till företagets nätverk.|[Wi-Fi-anslutningar i Microsoft Intune](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)|
|E-postprofiler|Skapa och distribuera e-postinställningar till enheter. Detta gör att användarna kan komma åt företagets e-post på sina personliga enheter utan att behöva göra några särskilda inställningar.|[Konfigurera åtkomst till företagets e-post med hjälp av e-postprofiler med Microsoft Intune](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)|
|VPN-profiler|Distribuera VPN-inställningar till användare och enheter i din organisation. Genom att distribuera inställningarna gör du det enklare för slutanvändaren att ansluta till resurser i företagsnätverket.|[VPN-anslutningar i Microsoft Intune](/intune/deploy-use/vpn-connections-in-microsoft-intune)|
|Villkorliga åtkomstprinciper|Hantera åtkomst till Microsoft Exchange-e-post och SharePoint Online från enheter som inte hanteras av Intune.|[Begränsa åtkomst till e-post och SharePoint med Microsoft Intune](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)|

## Inventering och rapporter

|Funktion|Information|Mer information|
|--------------|-----------|--------------------|
|Inventering och rapporter|Hitta information om de hanterade enheterna och den programvara de använder.|[Förstå dina enheter inventering i Microsoft Intune](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)|


### Se även
[Windows-datorhanteringsfunktioner i Microsoft Intune](windows-pc-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


