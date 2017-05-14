---
title: "Vad är Microsoft Intune? | Microsoft Docs"
description: "Lär dig mer om Intune, komponenten för hantering av mobila enheter i Enterprise Mobility + Security-lösningen, och se hur den kan hjälpa dig att skydda företagsdata."
keywords: what is Intune
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 05/04/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 33febef8787887401960592d95356347f6917681
ms.openlocfilehash: 2552f84dc38c4453851167cd1570143c7a9820c2
ms.contentlocale: sv-se
ms.lasthandoff: 05/04/2017


---

# <a name="what-is-intune"></a>Vad är Intune?

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune är en molnbaserad tjänst för hantering av företagsmobilitet (EMM) som hjälper anställda att vara produktiva samtidigt som företagets data skyddas. Med Intune kan du:
* Hantera mobila enheter som anställda använder för att komma åt företagets data.
* Hantera mobila appar som används av anställda.
* Skydda företagets information genom att styra hur anställda får åtkomst till och delar den.
* Säkerställa att enheter och program är kompatibla med företagets säkerhetskrav.

Intune är nära integrerat med Azure Active Directory (Azure AD) för identitets- och åtkomstkontroll och Azure Information Protection för dataskydd.

Tillsammans hjälper Office 365 och EMS anställda att vara produktiva på alla deras enheter samtidigt som organisationens information är skyddad. Office 365 med EMS är en komplett integrerad svit för företagsmobilitet, inklusive produktivitet, identitet, åtkomstkontroll, hantering och dataskydd. Den ger dig ett effektivt sätt att distribuera och hantera en mobilitetslösning i din organisation.

## <a name="how-does-intune-work"></a>Hur fungerar Intune?
Intune tillhandahåller hantering av mobila enheter (MDM) och hantering av mobila program (MAM). Intunes MDM- och MAM-funktioner används i scenarierna för dataskydd och efterlevnad i EMS.  

Hur du använder MDM- och MAM-funktionerna i Intune och dataskydd i EMS beror på vilket [affärsproblem som du försöker lösa](#common-business-problems-that-intune-helps-solve). Exempel:
* Du använder MDM i hög grad om du skapar en pool med enheter för en viss typ av användning som ska delas av skiftarbetare i en butik.
* Du förlitar dig på MAM och dataskydd om du låter anställda använda egna personliga enheter för att komma åt företagsdata (BYOD).  
* Om du delar ut företagsägda telefoner till informationsarbetare använder du alla dessa tekniker i hög utsträckning.

## <a name="intune-mobile-device-management-mdm-explained"></a>Förklaring av Intunes hantering av mobila enheter (MDM)
MDM använder protokollen eller API:erna som är tillgängliga i mobiloperativsystem. Med MDD kan du bland annat:
* Registrera enheter i hantering så att IT-avdelningen enkelt kan se vilka enheter som har åtkomst till företagstjänster.
* Konfigurera enheter så att de uppfyller företagets säkerhets- och hälsostandarder.
* Tillhandahålla certifikat och Wi-Fi-/VPN-profiler för åtkomst till företagstjänster.
* Rapportera om och mäta enheternas efterlevnad mot företagets standarder.
* Ta bort företagsdata från hanterade enheter.  

En del tror att **åtkomstkontroll till företagsdata** är en MDM-funktion. Vi ser det inte så eftersom det inte är något som tillhandahålls av mobiloperativsystemet. Det är snarare något som identitetsprovidern tillhandahåller. I vårt fall är identitetsprovidern Azure AD (Active Directory Azure), Microsofts identitets- och åtkomsthanteringssystem.  

Intune är integrerat med Azure AD för att ge stöd för en bred uppsättning åtkomstkontrollscenarier. Du kan till exempel kräva att en mobil enhet är kompatibel med företagets standarder så som de har definierats i Intune innan enheten kan komma åt en företagstjänst, t.ex. Exchange. På samma sätt kan du låsa företagstjänsten till en specifik uppsättning mobila appar. Du kan till exempel låsa Exchange Online så att tjänsten endast kan nås av Outlook eller Outlook Mobile.

## <a name="intune-mobile-app-management-mam-explained"></a>Förklaring av Intunes hantering av mobila appar (MAM)
När vi pratar om MAM syftar vi på de saker som IT-administratörer kan göra med mobila appar med hjälp av våra lösningar, t.ex.:
* Publicera mobila appar till anställda.
* Konfigurera appar.
* Styra hur företagsdata används och delas i mobilappar.
* Ta bort företagsdata från mobilappar.   
* Uppdatera mobilappar
* Rapportera om inventering av mobilappar.
* Spåra användningen av mobilappar.

Vi har sett termen MAM användas för att beskriva alla dessa saker separat eller en specifik kombination av dem. Det är särskilt vanligt att folk blandar ihop begreppet appkonfiguration (dvs. användningen av tekniker som [hanterad appkonfiguration i iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)) med begreppet att skydda företagsdata i mobilappar. Det beror på att vissa mobilappar exponerar inställningar som gör att deras säkerhetsfunktioner kan konfigureras.

Det, i kombination med funktioner i operativsystemet för att skydda data (till exempel MDM-funktioner som Windows Information Protection i Windows 10), ger bra skydd för data på mobila enheter.

När du använder Intune med andra tjänster i EMS kan du genom appkonfigurationer tillämpa organisationens säkerhetskrav för mobilappar utöver säkerhetsfunktionerna i operativsystemet och själva mobilapparna. En app som hanteras med EMS har åtkomst till bredare mobilapps- och dataskydd, bland annat:

* [Enkel inloggning](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*    [Multifaktorautentisering](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
* [Villkorlig appåtkomst (tillåt åtkomst om mobilappen innehåller företagsdata)](https://docs.microsoft.com/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [Isolera företagsdata från personliga data i samma app](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Princip för appskydd (PIN-kod, kryptering, Spara som, Urklipp osv.)](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Rensa företagsdata från en mobilapp](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [Stöd för rättighetshantering](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Bild som visar datasäkerhetsnivåerna för apphantering](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Säkerhet för mobilappar med Intune
Att tillhandahålla appsäkerhet är en del av MAM, och när vi pratar om mobilappssäkerhet i Intune menar vi:
* Isolera personlig information och förhindra åtkomst av företagets IT-personal.
* Begränsa vad användarna kan göra med företagsdata, till exempel kopiera, klippa ut/klistra in, spara och visa.
* Ta bort företagsdata från mobilappar, även kallat selektiv rensning eller företagsrensning.

Ett sätt som Intune tillhandahåller säkerhet för mobilappar är genom en funktion för **appskyddsprinciper**. Principer för appskydd använder Azure AD-identiteter för att isolera företagsdata från personliga data. Data som kräver företagsautentiseringsuppgifter för åtkomst får ytterligare företagsskydd.

När en användare loggar in på sin enhet med sina företagsuppgifter ger användarens företagsidentitet åtkomst till data som inte är tillgängliga för användarens personliga identitet. När dessa företagsdata används styr Intune, tillsammans med andra EMS-tekniker, hur de sparas och delas. Samma skydd tillämpas inte på data som blir tillgängliga när användaren loggar in på sin enhet med hans eller hennes personliga identitet. På så sätt har IT-administratörerna kontroll över företagsdata medan slutanvändaren behåller sin integritet och kontrollen över personliga data.

## <a name="emm-with-and-without-device-enrollment"></a>EMM med och utan enhetsregistrering
De flesta lösningar för hantering av företagsmobilitet stöder grundläggande tekniker för enheter och mobilappar. Dessa är vanligtvis kopplade till enheten som registreras i din organisations MDM-lösning. Intune stöder dessa scenarier och stöder dessutom många scenarier som inte kräver registrering.  

Organisationer skiljer sig åt i den grad de implementerar scenarier ”utan registrering”. Vissa organisationer har det som standard. Vissa tillåter det för kompletterande enheter, till exempel en personlig surfplatta. Andra stöder det inte alls. Även i det sista fallet, då en organisation kräver att alla medarbetares enheter registreras i MDM, stöder dessa företag vanligtvis scenarier ”utan registrering” för leverantörer och för andra enheter som har ett specifikt undantag.

Du kan även använda Intunes ”utan registrering”-teknik på registrerade enheter. Exempelvis kan en enhet som har registrerats i MDM ha ”Öppna i”-skydd som tillhandahålls av mobiloperativsystemet. (Öppna i-skydd är en iOS-funktion som hindrar dig från att öppna ett dokument från en app, som Outlook, i en annan app, som Word, om inte båda apparna hanteras av MDM-providern.) IT-administratören kan dessutom tillämpa principen för appskydd på EMS-hanterade mobilappar för att styra ”Spara som” eller för att tillhandahålla multifaktorautentisering.

Oavsett hur din organisation förhåller sig till registrerade och oregistrerade mobilenheter och mobilappar har Intune, som en del av EMS, verktyg som kan öka de anställdas produktivitet samtidigt som dina företagsdata är skyddade.

## <a name="common-business-problems-that-intune-helps-solve"></a>Exempel på vanliga affärsproblem som Intune kan lösa
Följande lista över affärsproblem länkar till mer detaljerad information om de lösningar som vi kan erbjuda. Endast den sista punkten kräver MDM-registrering som en del av lösningen:

* [Skydda lokal e-post och lokala data så att mobila enheter kan komma åt dem](common-ways-to-use-intune.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Skydda e-post och data i Office 365 så att mobila enheter kan komma åt dem på ett säkert sätt](common-ways-to-use-intune.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Dela ut företagsägda telefoner till anställda](common-ways-to-use-intune.md#issue-corporate-owned-phones-to-your-information-workers)
* [Erbjud BYOD (Bring Your Own Device) eller ett program för personliga enheter till alla anställda](common-ways-to-use-intune.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Gör det möjligt för anställda att på ett säkert sätt få åtkomst till Office 365 från en ej hanterad offentlig dator](common-ways-to-use-intune.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Dela ut delade surfplattor med begränsad användning till uppdragspersonal](common-ways-to-use-intune.md#issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>Nästa steg
* Läs om några av de [vanliga sätten att använda Intune](common-ways-to-use-intune.md).
* Bekanta dig med produkten [med en 30-dagars utvärderingsversion av Intune](get-started-with-a-30-day-trial-of-microsoft-intune.md).
* Fördjupa dig i de [tekniska kraven och möjligheterna](/intune/get-started/what-to-know-before-you-start-microsoft-intune) med Intune.

