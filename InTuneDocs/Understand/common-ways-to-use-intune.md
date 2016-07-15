---
title: "Vanliga sätt att använda Intune | Microsoft Intune"
description: 
keywords: 
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9cb6894cefad1da14332f9994fdf45fe2d1e9b9c
ms.openlocfilehash: c854893f457a60a7424010cdf69a91cb8476e167


---

# Vanliga sätt att använda Intune

Innan du ger dig in på implementeringsåtgärder är det viktigt att samla företagets intressenter för Enterprise Mobility kring affärsmålen.  Det är viktigt oavsett om ni precis har börjat med Enterprise Mobility eller om ni migrerar från en annan produkt.  Behoven kring Enterprise Mobility utvecklas dynamiskt och Microsofts metoder för att möta dessa behov kan ibland skilja sig från andra lösningar på marknaden.  Det bästa sättet att samlas runt affärsmålen är att uttrycka vad ni vill åstadkomma i fråga om det ni vill göra möjligt för medarbetare, partners och IT.  Nedan följer korta introduktioner för de 6 vanligaste scenarierna som förlitar sig på Intune, tillsammans med länkar till mer information om hur man kan planera och distribuera vart och ett.

>[!NOTE] Vill du veta hur Microsoft IT använder Intune för att göra det möjligt för Microsofts medarbetare att få åtkomst till företagsresurser på sina mobila enheter, samtidigt som man skyddar företagsdata? [Läs denna tekniska fallstudie](https://www.microsoft.com/itshowcase/Article/Content/588) för att få reda på hur Microsoft IT använder Intune och andra tjänster för att hantera identitet, enheter, appar och data.  

## Skydda lokal e-post och lokala data så att det går att komma åt dem på ett säkert sätt från mobila enheter
De flesta Enterprise Mobility-strategier börjar med en plan för att möjliggöra säker åtkomst till e-post för anställda med mobila enheter på Internet. Många organisationer har fortfarande lokala data och programservrar, t.ex. Microsoft Exchange, som finns på företagets nätverk. Med Intune och Enterprise Mobility Suite (EMS) får ni en unikt integrerad lösning för villkorlig åtkomst för Exchange Server som ser till att inga mobilappar kan få åtkomst till e-post förrän enheten har registrerats med Intune, helt utan att distribuera någon annan gateway-dator i utkanten av företagets nätverk!

Förutom e-post har Intune stöd för att hantera åtkomst till mobilappar som kräver säker åtkomst till lokala data, t.ex. branschspecifik appserver.  Detta görs normalt med Intune-hanterade certifikat för åtkomstkontroll som kombineras med en VPN-gateway eller proxy av standardtyp i perimeternätverket, t.ex. Microsoft Azure AD-programproxy.  I dessa fall är det enda sättet att komma åt företagets data att registrera enheten i hanteringen.  När registreringen är klar säkerställer hanteringssystemet att enheter som får åtkomst till företagsdata är kompatibla med principerna.  Dessutom kan Intunes apphanteringsverktyg användas för att hjälpa till att hålla kvar data i den branschspecifika appen, så att det inte går att vidareföra företagsdata till konsumentappar eller -tjänster.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->

## Skydda e-post och data i Office 365 så att det går att komma åt dem på ett säkert sätt från mobila enheter
Det kan inte bli enklare för dig eller smidigare för användarna att skydda företagets data i Office 365 (e-post, dokument, snabbmeddelanden, kontakter). Intune och Enterprise Mobility Suite ger en unikt integrerad lösning för villkorlig åtkomst som säkerställer att inga användare, appar eller enheter kan få åtkomst till Office 365-data om de inte uppfyller företagets efterlevnadskrav (genomförd multifaktorautentisering, registrering med Intune, använder hanterad app, OS-version som stöds, PIN-kod för enhet, profil med låg användarrisk osv.). Office-mobilapparna i respektive appbutik är redo att köras med datainneslutningsprinciper som du kan konfigurera via Intune, som gör det möjligt att förhindra att data delas med appar (t.ex. intern e-postapp) och lagringsplatser (t.ex. Dropbox) som inte hanteras av IT-avdelningen.  Alla dessa funktioner är inbyggda i Office 365 och EMS.  Du behöver inte distribuera ytterligare infrastruktur för att dra nytta av detta mervärde.

En vanlig metod för Office 365-distribution är att kräva att enheterna registrerar sig för hantering om de måste vara helt etablerade med företagsappar/certifikat/Wi-Fi/VPN-konfigurationer, vilket ofta är fallet för företagsägda enheter.  Om användaren dock bara behöver åtkomst till e-post och dokument för företaget, vilket ofta är fallet för personligt ägda enheter, måste användaren använda Office-mobilapparna (där du har verkställt datainneslutningsprinciper) och behöver inte registrera enheten alls!  Vilken metod som än används skyddas Office 365-data av principer som du har definierat.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->

## Erbjuder ett BYOD-program (”bring your own device”) för alla medarbetare
BYOD blir allt populärare hos organisationer som ett sätt att minska maskinvaruutgifterna eller öka medarbetarnas valmöjligheter för mobil produktivitet. I princip alla har en egen telefon idag så varför ska de behöva en till att bära på? Den främsta utmaningen har alltid varit att övertyga medarbetarna att registrera sina personliga enheter i hantering, eftersom de är oroliga för vad IT-avdelningen kommer att kunna se och göra med enheten.  

Om enhetsregistrering inte är ett genomförbart alternativ erbjuder Intune en alternativ BYOD-metod som innebär att helt enkelt hantera de appar som innehåller företagsdata.  Intune skyddar företagets data även om appen i fråga har åtkomst till både företagsrelaterade och personliga data, som är fallet för Office-mobilappar.  Som administratör kan du kräva att användarna bereder sig åtkomst till Office 365 från Office-mobilapparna och konfigurerar apparna med principer som skyddar data (kryptering, PIN-kodsskydd osv.).  Dessa principer förhindra dataförlust i ej hanterade appar och lagringsplatser – i eller utanför dessa appar.  Principerna förhindrar till exempel att en användare kopierar text från e-postprofil för företaget till en privat e-postprofil, även om båda profilerna är konfigurerade i Outlook Mobile.  Liknande konfigurationer kan distribueras för andra tjänster och program som krävs av BYOD-användarna.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## Utfärda företagsägda telefoner till informationsarbetarna
De flesta informationsarbetare är idag mobila, vilket gör att produktivitet på mobila enheter är avgörande för att vara konkurrenskraftig.  Dessa medarbetare behöver smidig åtkomst till alla företagets appar och data, när som helst, var som helst.  Du måste se till att företagets data är säkra och att de administrativa kostnaderna är låga.  

Intune erbjuder massetablering och hanteringslösningar som är integrerade med de flesta stora enhetshanteringsplattformar som finns på marknaden idag, inklusive Apple Device Enrollment Program och mobilsäkerhetsplattformen Samsung KNOX.  Centraliserad redigering av enhetskonfigurationer med Intune gör att det i hög grad går att automatisera etablering av företagsenheter.  

Tänk dig detta: ge en medarbetare en oöppnad låda med en iPhone. Medarbetaren aktiverar den och går igenom ett företagsanpassat konfigurationsflöde där användaren måste autentisera sig. iPhone-enheten konfigureras enkelt med säkerhetsprinciper (kryptering av hårddisk, PIN-kod för enheten osv.), e-post-/Wi-Fi-/VPN-/certifikatprofiler och en grunduppsättning med appar. Medarbetaren startar sedan Intune-företagsportalappen för att komma åt valfria företagsappar som är tillgängliga.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## Utfärda delade surfplattor med begränsad användning till uppdragspersonal
Uppdragspersonal använder mobil teknik i allt större omfattning.  Till exempel är delade surfplattor nu vanligt för detaljhandelspersonal.  Oavsett om de används för att hantera en försäljning eller snabbt kontrollera lagret hjälper surfplattorna till att skapa positiva kundmöten.  Den enkla användarupplevelsen är avgörande i detta fall.  Därför får medarbetarna ofta surfplattor med begränsad användning, så att en enda branschspecifik app är allt medarbetaren kan interagera med.  Intune gör det möjligt att massetablera, skydda och centralt hantera dessa delade surfplattor som kan konfigureras för att köras i detta läge med begränsad användning.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## Gör det möjligt för medarbetarna att på ett säkert sätt få åtkomst till Office 365 från en ej hanterad offentlig dator
Ibland behöver medarbetarna använda enheter, appar eller webbläsare som du inte kan hantera, t.ex. offentliga datorer på mässor och hotell. Ska du tillåta att medarbetarna får åtkomst till företagets e-post från dem? Med Intune och Enterprise Mobility Suite <!--you have choices. The--> blir svaret helt enkelt ”nej” genom att begränsa e-poståtkomsten till enheter som hanteras av din organisation.  <!-- Alternatively, you can choose to allow limited access to these untrusted computers by requiring multi-factor authentication and only allowing browser access (Outlook Web Access) in a mode where files cannot be downloaded (e.g. email attachments).-->  Det säkerställer att den starkt autentiserade medarbetaren inte råkar lämna företagsdata på den ej betrodda datorn.

<!-- Learn more about how to plan and deploy Intune to support kiosks. -->



<!--HONumber=Jun16_HO4-->


