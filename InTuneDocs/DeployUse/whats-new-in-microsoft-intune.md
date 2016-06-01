---
# required metadata

title: Vad är nytt | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Nyheter i Microsoft Intune

## April 2016
Alla dessa funktioner stöds även för kunder med hybriddistributioner (Configuration Manager integrerat med Intune).
### Apphantering
- **MAM-efterlevnad.**
Nu kan du visa [statusen](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) för dina programhanteringsprinciper för alla användare i din Azure Active Directory-klientorganisation (AAD). Du måste bland annat:
   - Egenskaper
   - Appar på enheten

   Statusvärden:

   **Incheckad**: Anger att principen distribuerades till användaren, att appen har använts i arbetskontexten och att principen har tillämpats.

    **Inte incheckad**: Anger att principen distribuerades till användaren, men att appen inte har använts i arbetskontexten sedan dess.


- **MAM-kontroller för att förhindra att Outlook-kontakter synkroniseras (Android).**
En ny inställning är tillgänglig för [hantering av mobila program](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) utan enhetsregistrering. Med den här inställningen kan du förhindra att ett program synkroniserar kontakter till den interna adressboken på Android-enheter. Om den här inställningen är aktiverad kan berörda program inte längre spara kontakter i den interna adressboken. Om den här inställningen är inaktiverad kan berörda program spara kontakter i den interna adressboken. När du [fjärraderar en enhet eller app](wipe-managed-company-app-data-with-Microsoft-Intune.md) tas kontakter som redan har sparats i den interna adressboken bort. Den här nya inställningen stöds av Outlook på Android-enheter.

### Enhetshantering
- **Identifiering av telefonnummer för företagsägda enheter.** Telefoner kategoriserade som ”företagsägda” identifieras nu med sina fullständiga telefonnummer, t.ex. när du kör en inventeringsrapport för mobila enheter. BYOD-telefonnummer döljs fortfarande med ***, och bara de fyra sista siffrorna visas.


### Uppdateringar av företagsportalen
Företagsportalappen för Android Användare som inte har registrerat sin enhet i Intune och som inte har rätt certifikat installerat kan inte logga in på företagsportalappen för Android och får meddelandet ”Du kan inte logga in eftersom enheten saknar ett obligatoriskt certifikat”. Meddelandet innehåller länken ”Så här löser du problemet” som användarna kan trycka på för att visa installationsanvisningar för certifikatet.

De steg som användarna följer för att lösa problemet finns i [Enheten saknar ett certifikat som krävs](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing) iOS-företagsportalappen

Stöd har lagts till för ”dra för att uppdatera”-åtgärden som uppdaterar innehållet på startskärmen, t.ex. tillgängliga appar, enheter och IT-kontaktinformation. Den här åtgärden kontrollerar inte kompatibiliteten eller principinformation, vilket du kan göra genom att välja panelen för din aktuella enhet och trycka på knappen **Synkronisera**. Företagsportalappen för Windows 10 Mobile och Windows Phone 8.1

Appinstallationen har förbättrats för slutanvändare som installerar affärsspecifika appar.

* Om appinstallationen tar lång tid kan användarna synkronisera sina enheter manuellt för att tvinga synkroniseringen att fortsätta. Instruktioner för slutanvändaren finns i [Synkronisera enheten manuellt för att påskynda appinstallationer](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually) Företagsportalens webbplats
* När Windows 10 Mobile- och Windows Phone 8.1-användare installerar affärsspecifika appar ser de nu följande nya statusar, som ger dem mer information om installationens status:

**Väntar på att enheten ska synkroniseras** – användaren har tryckt på ”Installera” och nu försöker enheten synkronisera med Intune-infrastrukturen. Synkroniseringen krävs innan installationen kan slutföras.

### Meddelandet ”Väntar på att enheten ska synkroniseras” är också en länk som användarna kan trycka på för att visa [instruktioner](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) om hur de manuellt synkroniserar sina enheter med Intune om synkroniseringsprocessen tar lång tid eller fastnar.

****Hämtar** – användarens hämtningsbegäran behandlas och enheten laddar ned och installerar appen.** Innan dessa statusar lades till var det förvirrande för användarna när en appinstallation tog lång tid eftersom de bara såg statusen ”Installerar”, som kan visas på skärmen i flera timmar. Med de nya statusarna kan användarna, i stället för att kontakta supportavdelningen, trycka på länken ”Väntar på att enheten ska synkroniseras” och följa anvisningarna för att tvinga synkroniseringen att fortsätta. Kommande nyheter  Ändringar av konton för Enhetsregistreringshanterare. För att förbättra prestanda och skalning visar Intune inte längre alla enheter i Enhetsregistreringshanteraren (DEM) i fönstret Mina enheter i företagsportalappen.  Endast den lokala enheten som kör appen visas och endast om den har registrerats via företagsportalappen.

DEM-användaren kan utföra åtgärder på den lokala enheten, men fjärrhanteringen av andra registrerade enheter kan endast utföras från Intune-administrationskonsolen.


## Dessutom kommer Intune sluta använda DEM-konton med antingen Apples DEP (Device Enrollment Program) eller verktyget Apple Configurator.
Båda dessa registreringsmetoder stöder redan användarlös registrering för delade iOS-enheter.



### Använd endast DEM-konton om användarlös registrering för delade enheter inte är tillgängligt.
* [Håll dig informerad om Intunes utveckling i [översikten över molnplattformen](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)](http://go.microsoft.com/fwlink/?LinkID=273882)


<!--HONumber=May16_HO2-->


