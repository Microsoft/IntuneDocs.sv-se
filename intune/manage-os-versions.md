---
title: Hantera operativsystemversioner med Microsoft Intune | Microsoft Intune
description: Lär dig mer om att hantera versioner av operativsystemet på plattformar med Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: faf51236be219a860447d2243967b90e3aab1d01
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837245"
---
# <a name="manage-operating-system-versions-with-intune"></a>Hantera versioner av operativsystem med Intune
På moderna bärbara och stationära plattformar, viktiga uppdateringar, korrigeringar och nya versioner snabbt. Du har kontroller för att fullständigt hantera uppdateringar och korrigeringar i Windows, men för andra plattformar som iOS och Android krävs att slutanvändarna deltar i processen.  Microsoft Intune har funktioner som hjälper dig att strukturera versionshanteringen av operativsystem på olika plattformar.

Intune kan hjälpa dig att hantera dessa vanliga scenarier: 
- Fastställa vilka operativsystemversioner som finns på slutanvändarenheterna
- Kontrollera åtkomst till organisationens data på enheter medan du validerar en ny version av operativsystemet
- Uppmuntra/kräv att slutanvändare ska uppgradera till den senaste operativsystemversion som är godkänd av organisationen
- Hantera en organisationsomfattande distribution av en ny version av operativsystemet
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Versionskontroll för operativsystem med registreringsbegränsningar för Intunes hantering av mobila enheter (MDM)
Med Intunes MDM-registreringsbegränsningar kan du definiera krav på klientenheter innan du tillåter att enheten registreras. Målet är att kräva att användarna enbart registrerar kompatibla enheter innan de får tillgång till företagsresurser. Enhetskraven innehåller både de lägsta och högsta tillåtna operativsystemsversionerna för plattformar som stöds.
 
![Blad med begränsningar för plattformskonfiguration](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>I praktiken
Organisationer använder begränsningar för enhetstyp för att kontrollera åtkomsten till företagsresurser genom att använda följande inställningar: 
1. Använd den lägsta operativsystemversionen så att slutanvändarna använder aktuella plattformar och plattformar som stöds i din organisation. 
2. Lämna högsta operativsystemversion ospecificerat (ingen gräns) eller ställ in det på den senaste validerade versionen i din organisation för att låta intern testning av nya operativsystemversioner ske.

Mer information finns i [Ange begränsningar för enhetstyp](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions).
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>Rapportering av operativsystemversion och efterlevnad av Intunes MDM-efterlevnadsprinciper för enheter
Efterlevnadsprinciper för Intune MDM-enheter innehåller följande verktyg: 
- Ange regler för efterlevnad
- Visa principefterlevnad via rapportering
- Vidta åtgärder vid inkompatibilitet via enhetskarantän och villkorlig åtkomst

Precis som registreringsbegränsningar innehåller efterlevnad för enhet både lägsta och högsta operativsystemversioner. Principer har också en tidslinje för efterlevnad för att ge användarna en respitperiod för att följa standard. Enhetsefterlevnadsprinciper håller dina registrerade slutanvändares enheter kompatibla med organisationens principer.

![Enhetsefterlevnad – åtgärder för icke-kompatibla enheter](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>I praktiken
Organisationer använder principer för enhetsefterlevnad i samma scenarier som begränsningar för registrering. Dessa principer ser till att användare håller sig till aktuella, validerade operativsystemversioner i din organisation. När slutanvändare inte följer standard kan åtkomsten till företagsresurser blockeras via villkorlig åtkomst tills slutanvändarna är inom det operativsystemintervall som krävs för organisationen. Slutanvändarna meddelas att de inte uppfyller kraven och de får anvisningar för att få åtkomst.   

Mer information finns i [Kom igång med enhetsefterlevnad](https://docs.microsoft.com/intune/device-compliance-get-started).
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Kontroller för operativsystemversion med appskyddsprinciper i Intune    
Med Intunes appskyddsprinciper och åtkomstinställningar för hantering av mobilprogram (MAM) kan du ange en lägsta operativsystemversion i appnivån. På så sätt kan du informera och uppmuntra, eller kräva, att dina slutanvändare uppdaterar sina operativsystem till en viss lägstaversion.
 
Du har två olika alternativ: 
- **Varna** – Varna informerar slutanvändaren om att han eller hon ska uppgradera om de öppnar en app med en programskyddsprincip eller MAM-åtkomstinställningar på en enhet med ett operativsystem som är äldre än den angivna versionen. Åtkomst tillåts för programmet och organisationens data.
  ![Bild av Android-dialogruta med uppdateringsvarning](./media/os-version-update-warning.png) 

- **Blockera** – Blockera informerar slutanvändaren om att han eller hon måste uppgradera när han eller hon öppnar en app med en programskyddsprincip eller MAM-åtkomstinställningar på en enhet med ett operativsystem som är äldre än den angivna versionen. Åtkomst tillåts inte för programmet och organisationens data.
  ![Bild av dialogruta för blockerad programåtkomst](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>I praktiken
Organisationer använder principinställningar för appskydd idag när appar öppnas eller återupptas som ett sätt att utbilda slutanvändarna om behovet av att hålla sina program uppdaterade. En exempelkonfiguration betyder att slutanvändarna varnas om de använder aktuell version minus en och blockeras vid aktuell version minus två.
 
Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](https://docs.microsoft.com/intune/app-protection-policies).

## <a name="managing-a-new-operating-system-version-rollout"></a>Hantera distribution av en ny operativsystemversion
Du kan använda Intune-funktionerna som beskrivs i den här artikeln för att flytta organisationen till en ny operativsystemversion inom tidslinjen du anger. I följande steg finns en exempel-distributionsmodell för att flytta dina användare från operativsystemet v1 till operativsystemet v2 på sju dagar.
- **Steg 1**: Använd begränsningar för registrering för att kräva operativsystem v2 som den lägsta versionen för att registrera enheten. Det säkerställer att nya slutanvändarenheter är kompatibla vid registreringen.
- **Steg 2a**: Använd Intune-appskyddsprinciper för att varna användare när appen öppnas eller återupptas om att operativsystem v2 krävs.
- **Steg 2b**. Använd efterlevnadsprinciper för enheter för att kräva operativsystem v2 som lägsta version för att en enhet ska vara kompatibel. Använd **Åtgärder** för icke-kompatibilitet för att tillåta en sju dagar lång respitperiod och för att skicka ett e-postmeddelande till slutanvändarna med din tidslinje och dina krav.
  -  Dessa principer informerar slutanvändarna om att befintliga enheter måste uppdateras via e-post, via Intune-företagsportalen, och informera när appen öppnas för appar som aktiverats med en appskyddsprincip.
  - Du kan köra en efterlevnadsrapport för att identifiera användare som inte följer standard. 
- **Steg 3a**: Använd Intune-appskyddsprinciper för att blockera användare när en app öppnas eller återupptas om enheten inte kör operativsystem v2.
- **Steg 3b**: Använd efterlevnadsprinciper för enheter för att kräva operativsystem v2 som lägsta version för att en enhet ska vara kompatibel.
  - Principerna kräver att enheterna ska vara uppdaterade för att de ska fortsätta att få åtkomst till organisationsdata. Skyddade tjänster blockeras när de används med villkorlig åtkomst för enheten. Appar som är aktiverade med en appskyddsprincip blockeras när de öppnas eller när de får åtkomst till organisationsdata.

## <a name="next-steps"></a>Nästa steg
Använd följande resurser för att hantera versioner av operativsystemet i din organisation: 

- [Ange begränsningar för enhetstyp](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [Kom igång med enhetsefterlevnad](https://docs.microsoft.com/intune/device-compliance-get-started)
- [Hur du skapar och tilldelar skyddsprinciper för appar](https://docs.microsoft.com/intune/app-protection-policies)
