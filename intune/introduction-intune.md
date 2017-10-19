---
title: "Vad är Microsoft Intune"
description: "Lär dig mer om Intune, komponenten för hantering av mobila enheter (MDM) och mobilapphantering (MAM) i Enterprise Mobility + Security-lösningen, och se hur den kan hjälpa dig att skydda företagsdata."
keywords: what is Intune
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/28/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
ms.custom: 
ms.openlocfilehash: 527a2a1578fcf9ef8e8f80c68091e582f8f2ebd2
ms.sourcegitcommit: 6fae2dfb3a5c8f2e5ccfd120fd15656b26e5d302
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/09/2017
---
# <a name="what-is-intune"></a>Vad är Intune?

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Intune är en molnbaserad tjänst för hantering av företagsmobilitet (EMM) som hjälper anställda att vara produktiva samtidigt som företagets data skyddas. Med Intune kan du:
* Hantera mobila enheter som anställda använder för att komma åt företagets data.
* Hantera mobila appar som används av anställda.
* Skydda företagets information genom att styra hur anställda får åtkomst till och delar den.
* Säkerställa att enheter och program är kompatibla med företagets säkerhetskrav.

## <a name="common-business-problems-that-intune-helps-solve"></a>Exempel på vanliga affärsproblem som Intune kan lösa

* [Skydda lokal e-post och lokala data så att mobila enheter kan komma åt dem](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Skydda e-post och data i Office 365 så att mobila enheter kan komma åt dem på ett säkert sätt](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [Dela ut företagsägda telefoner till anställda](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
* [Erbjud BYOD (Bring Your Own Device) eller ett program för personliga enheter till alla anställda](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
* [Gör det möjligt för anställda att på ett säkert sätt få åtkomst till Office 365 från en ej hanterad offentlig dator](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [Utfärda delade surfplattor med begränsad användning till uppdragspersonal](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)


## <a name="how-does-intune-work"></a>Hur fungerar Intune?
Intune är en komponent i Enterprise Mobility + Security (EMS) som hanterar mobila enheter och appar. Det är nära integrerat med andra EMS-komponenter som Azure Active Directory (Azure AD) för identitets- och åtkomstkontroll och Azure Information Protection för dataskydd. När du använder det tillsammans med Office 365 gör du det möjligt för dina anställda att vara produktiva på alla deras enheter samtidigt som organisationens information är skyddad.

![Bild av Intune-arkitektur](./media/intunearch_sm.png)

Visa en [större version](./media/intunearchitecture.svg) av Intune-arkitekturdiagrammet.

Hur du använder enhets- och apphanteringsfunktionerna i Intune och dataskydd i EMS beror på vilket [affärsproblem som du försöker lösa](#common-business-problems-that-intune-helps-solve). Exempel:
* Du använder enhetshantering i hög grad om du skapar en pool med enheter för en viss typ av användning som ska delas av skiftarbetare i en butik.
* Du förlitar dig på apphantering och dataskydd om du låter anställda använda egna personliga enheter för att komma åt företagsdata (BYOD).  
* Om du delar ut företagsägda telefoner till informationsarbetare använder du alla dessa metoder.

## <a name="intune-device-management-explained"></a>Så fungerar Intune-enhetshantering
I Intune-enhetshantering används protokollen eller API:erna som är tillgängliga i mobiloperativsystem. Med MDD kan du bland annat:
* Registrera enheter för hantering så att it-avdelningen enkelt kan se vilka enheter som har åtkomst till företagstjänster
* Konfigurera enheter så att de uppfyller företagets säkerhets- och hälsostandarder.
* Tillhandahålla certifikat och Wi-Fi-/VPN-profiler för åtkomst till företagstjänster.
* Rapportera om och mäta enheternas efterlevnad mot företagets standarder.
* Ta bort företagsdata från hanterade enheter.  

En del tror att **åtkomstkontroll till företagsdata** är en enhetshanteringsfunktion. Vi ser det inte så eftersom det inte är något som tillhandahålls av mobiloperativsystemet. Det är snarare något som identitetsprovidern tillhandahåller. I vårt fall är identitetsprovidern Azure AD (Active Directory Azure), Microsofts identitets- och åtkomsthanteringssystem.  

Intune är integrerat med Azure AD för att ge stöd för en bred uppsättning åtkomstkontrollscenarier. Du kan till exempel kräva att en mobil enhet ska vara kompatibel med företagets standarder som du har definierat i Intune innan enheten kan komma åt en företagstjänst, t.ex. Exchange. På samma sätt kan du låsa företagstjänsten till en specifik uppsättning mobila appar. Du kan till exempel låsa Exchange Online så att tjänsten endast kan nås av Outlook eller Outlook Mobile.

## <a name="intune-app-management-explained"></a>Så fungerar Intune-apphantering
Med apphantering menar vi:
* Tilldela anställda mobilappar
* Konfigurera appar med standardinställningar som används när appen körs
* Styra hur företagsdata används och delas i mobilappar.
* Ta bort företagsdata från mobilappar.   
* Uppdatera appar
* Rapportera om inventering av mobilappar.
* Spåra användningen av mobilappar.

Vi har sett begreppet mobilapphantering (MAM) användas för att beskriva allt det här separat eller kombinerat. Det är särskilt vanligt att begreppet appkonfiguration blandas ihop med begreppet att skydda företagsdata i mobilappar. Det beror på att vissa mobilappar exponerar inställningar som gör att deras säkerhetsfunktioner kan konfigureras.

När vi talar om appkonfiguration och Intune avser vi särskilt teknik som [hanterad appkonfiguration i iOS](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html).

När du använder Intune med andra tjänster i EMS kan du genom appkonfigurationer tillämpa organisationens säkerhetskrav för mobilappar utöver säkerhetsfunktionerna i operativsystemet och själva mobilapparna. En app som hanteras med EMS har åtkomst till bredare mobilapps- och dataskydd, bland annat:

* [Enkel inloggning](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [Multifaktorautentisering](https://docs.microsoft.com/multi-factor-authentication/multi-factor-authentication)
* [Villkorlig appåtkomst – tillåt åtkomst om mobilappen innehåller företagsdata](app-based-conditional-access-intune.md)
* [Isolera företagsdata från personliga data i samma app](app-protection-policy.md)
* [Princip för appskydd (PIN-kod, kryptering, Spara som, Urklipp osv.)](app-protection-policies.md)
* [Rensa företagsdata från en mobilapp](apps-selective-wipe.md)
* [Stöd för rättighetshantering](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![Bild som visar datasäkerhetsnivåerna för apphantering](./media/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Appsäkerhet i Intune
Att tillhandahålla appsäkerhet är en del av apphanteringen, och när vi pratar om mobilappssäkerhet i Intune menar vi:
* Isolera personlig information och förhindra åtkomst av företagets IT-personal.
* Begränsa vad användarna kan göra med företagsdata, till exempel kopiera, klippa ut/klistra in, spara och visa.
* Ta bort företagsdata från mobilappar, även kallat selektiv rensning eller företagsrensning.

Ett sätt som Intune tillhandahåller säkerhet för mobilappar är genom en funktion för **appskyddsprinciper**. Principer för appskydd använder Azure AD-identiteter för att isolera företagsdata från personliga data. Data som kräver företagsautentiseringsuppgifter för åtkomst får ytterligare företagsskydd.

När exempelvis en användare loggar in på sin enhet med sina företagsuppgifter ger användarens företagsidentitet åtkomst till data som inte är tillgängliga för användarens personliga identitet. När den här företagsinformationen används reglerar appskyddsprinciper hur den ska sparas och delas. Samma skydd tillämpas inte på data som blir tillgängliga när användaren loggar in på sin enhet med hans eller hennes personliga identitet. På så sätt har IT-administratörerna kontroll över företagsdata medan slutanvändaren behåller sin integritet och kontrollen över personliga data.

## <a name="emm-with-and-without-device-enrollment"></a>EMM med och utan enhetsregistrering
De flesta lösningar för hantering av företagsmobilitet stöder grundläggande tekniker för enheter och mobilappar. De är vanligtvis kopplade till enheten som registreras i din organisations lösning för mobilenhetshantering (MDM). Intune stöder dessa scenarier och stöder dessutom många scenarier som inte kräver registrering.  

Organisationer skiljer sig åt i den grad de implementerar scenarier ”utan registrering”. Vissa organisationer har det som standard. Vissa tillåter det för kompletterande enheter, till exempel en personlig surfplatta. Andra stöder det inte alls. Även i det sista fallet, då en organisation kräver att alla medarbetares enheter registreras i MDM, stöder de vanligtvis scenarier ”utan registrering” för leverantörer och för andra enheter som har ett särskilt undantag.

Du kan även använda Intunes ”utan registrering”-teknik på registrerade enheter. Exempelvis kan en enhet som har registrerats i MDM ha ”Öppna i”-skydd som tillhandahålls av mobiloperativsystemet. Öppna i-skydd är en iOS-funktion som hindrar dig från att öppna ett dokument från en app, som Outlook, i en annan app, som Word, om inte båda apparna hanteras av MDM-leverantören. IT-administratören kan dessutom tillämpa principen för appskydd på EMS-hanterade mobilappar för att styra ”Spara som” eller för att tillhandahålla multifaktorautentisering.

Oavsett hur din organisation förhåller sig till registrerade och oregistrerade mobilenheter och mobilappar har Intune, som en del av EMS, verktyg som kan öka de anställdas produktivitet samtidigt som dina företagsdata är skyddade.



### <a name="next-steps"></a>Nästa steg
* Läs om några av de [vanliga sätten att använda Intune](common-scenarios.md).
* Bekanta dig med produkten [med en 30-dagars utvärderingsversion av Intune](free-trial-sign-up.md).
* Fördjupa dig i de [tekniska kraven och möjligheterna](supported-devices-browsers.md) med Intune.
