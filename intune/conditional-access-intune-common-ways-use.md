---
title: Villkorlig åtkomst med Microsoft Intune
titlesuffix: ''
description: Läs om hur villkorlig åtkomst med Intune ofta används för enhetsbaserad och appbaserad villkorlig åtkomst.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 49fd06d4f0f75f1aeff434ce3b271284ec1a0340
ms.sourcegitcommit: 27f365f5e67e83562883e0c1fc9fdfae8fd60ce4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "40252752"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Hur används villkorlig åtkomst vanligtvis med Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Det finns två typer av villkorlig åtkomst som används med Intune: enhetsbaserad villkorlig åtkomst och appbaserad villkorlig åtkomst. Du måste konfigurera de relaterade efterlevnadsprinciperna för att få en villkorlig åtkomst som följer standard i din organisation. Villkorlig åtkomst används vanligtvis för att tillåta eller blockera åtkomst till Exchange On-premises, styra åtkomsten till nätverket eller integrering med en Mobile Thread Defense-lösning.

Nedanstående information visar hur du ska använda Intunes funktioner för mobil *enhets*efterlevnad och hantering av mobil*program* (MAM). 

> [!NOTE]
> Villkorlig åtkomst är en funktion i Azure Active Directory som ingår i Azure Active Directory Premium-licenser. Intune utökar den här funktionen genom att lägga till efterlevnad för mobila enheter och hantering av mobilappar i lösningen.

## <a name="device-based-conditional-access"></a>Enhetsbaserad villkorlig åtkomst

Intune och Azure Active Directory ser tillsammans till att endast hanterade och kompatibla enheter får åtkomst till e-post, Office 365-tjänster, SaaS-appar (Software as a Service) och [lokala appar](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Dessutom kan du konfigurera en princip i Azure Active Directory så att endast datorer som är anslutna till en domän, eller mobila enheter som är registrerade i Intune, kan få åtkomst till Office 365-tjänster.

Intune innehåller funktioner för enhetskompatibilitetprinciper som utvärderar enheternas efterlevnadsstatus. Kompatibilitetsstatusen rapporteras till Azure Active Directory som använder den för att verkställa den princip för villkorlig efterlevnad som skapas i Azure Active Directory när användaren försöker få åtkomst till företagets resurser.

Enhetsbaserad villkorlig åtkomst för Exchange Online och andra Office 365-produkter konfigureras via [Azure-portalen](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Läs mer om [villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Läs mer om [Intunes enhetsefterlevnad](device-compliance.md).

-   Lär dig mer om [skydd av e-post, Office 365 och andra tjänster med villkorlig åtkomst i Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="conditional-access-for-exchange-on-premises"></a>Villkorlig åtkomst för Exchange lokalt

Villkorlig åtkomst kan användas för att tillåta eller blockera åtkomst till **Exchange On-premises** baserat på enhetsefterlevnadsprinciperna och registreringsstatusen. När villkorlig åtkomst använd i kombination med en enhetsefterlevnadsprincip ges endast kompatibla enheter åtkomst till Exchange On-premises.

Du kan konfigurera avancerade inställningar för villkorlig åtkomst om du vill ha mer detaljerad kontroll, som t.ex.:

-   Tillåta eller blockera vissa plattformar.

-   Omedelbart blockera enheter som inte hanteras av Intune.

Efterlevnaden för alla enheter som används för att få åtkomst till Exchange lokalt kontrolleras när principerna för enhetsefterlevnad och villkorlig åtkomst tillämpas.

När en enhet inte uppfyller de angivna villkoren leds slutanvändaren genom en process för att registrera enheten och åtgärda de problem som gör att enheten inte är kompatibel.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Hur villkorlig lokal åtkomst för Exchange lokalt fungerar

Intune Exchange Connector tar emot alla Exchange Active Sync-poster (EAS) som finns på Exchange-servern, så att Intune kan ta dessa EAS-poster och mappa den till Intune-enhetsposterna. Dessa poster och enheter har registrerats och identifierats av Intune. Den här processen tillåter eller blockerar åtkomst till e-post.

Om Intune EAS-posten är helt ny, och Intune inte känner till detta, så utfärdar ett kommando som blockerar åtkomsten till e-post. Här följer lite mer information om hur den här processen fungerar:

![Exchange lokalt med CA-flödesschema](./media/ca-intune-common-ways-1.png)

1.  Användaren försöker få åtkomst till företagets e-post som finns på Exchange lokalt, version 2010 SP1 eller senare.

2.  Om enheten inte hanteras av Intune, blockeras åtkomsten till e-post. Intune skickar blockmeddelande till EAS-klienten.

3.  EAS får ett blockmeddelande, sätter enheten i karantän och skickar e-postkarantänmeddelandet med åtgärdsförslag med länkar så att användarna kan registrera sina enheter.

4.  Den arbetsplatsanslutna processen är det första steget mot att låta enheten hanteras av Intune.

5.  Enheten registreras i Intune.

6.  Intune mappar EAS-posten till en enhetspost, och sparar enhetens efterlevnadstillstånd.

7.  EAS-klient-ID:t registreras i Azure AD:s enhetsregistreringsprocess, i vilken det skapas en relation mellan Intune-enhetsposten och EAS-klient-ID:t.

8.  Under Azure AD:s enhetsregistrering sparas enhetens statusinformation.

9.  Om användaren uppfyller principerna för villkorlig åtkomst, skickar Intune ett kommando genom vilket Intune Exchange-anslutningsappen tillåter att brevlådan synkroniseras.

10. Exchange-servern skickar meddelandet till EAS-klienten, så att användaren får åtkomst till e-posten.

#### <a name="whats-the-intune-role"></a>Vad är Intune-rollen?

Intune utvärderar och hanterar enhetens tillstånd.

#### <a name="whats-the-exchange-server-role"></a>Vad är Exchange-serverrollen?

Exchange-servern tillhandahåller det API och den infrastruktur som krävs för att flytta enheter till deras karantän.

> [!IMPORTANT]
> Tänk på att en efterlevnadsprofil måste tilldelas enhetsanvändaren för att enhetens efterlevnad ska kunna utvärderas. Om ingen efterlevnadsprincip har distribuerats till användaren behandlas enheten som kompatibel och inga åtkomstbegränsningar tillämpas.

### <a name="conditional-access-based-on-network-access-control"></a>Villkorlig åtkomst baserad på åtkomstkontroll för nätverk

Intune har integrerats med partner som Cisco ISE, Aruba Clear Pass och Citrix NetScaler för att kunna ge åtkomstkontroll baserad på Intune-registreringen och enhetsefterlevnadstillståndet.

Användare kan tillåtas eller nekas åtkomst när de försöker att få åtkomst till företagets Wi-Fi- eller VPN-resurser baserat på huruvida enheten hanteras eller är kompatibel med Intunes enhetsefterlevnadsprinciper eller inte.

-   Läs mer om [NAC-integrering med Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Villkorlig åtkomst baserad på enhetsrisk

Intune samarbetar med Mobile Threat Defense-leverantörer om att tillhandahålla en säkerhetslösning som identifierar skadlig kod, trojaner och andra hot på mobila enheter.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Så här fungerar Intune med Mobile Threat Defense-integrering

När mobila enheter har Mobile Threat Defense-agenten installerad, kan denna skicka meddelanden om efterlevnadstillstånd till Intune om ett hot har identifierats i själva den mobila enheten.

Intune och integrerat mobilhotsskydd spelar en viktig roll vid beslut om villkorlig åtkomst baserat på enhetsrisk.

-   Läs mer om [Intunes mobilhotsskydd](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### <a name="conditional-access-for-windows-pcs"></a>Villkorlig åtkomst för Windows-datorer

Villkorlig åtkomst för datorer har ungefär samma funktioner som för mobila enheter. Låt oss tala om hur du kan använda villkorlig åtkomst när du hanterar datorer med Intune.

#### <a name="corporate-owned"></a>Företagsägd

-   **Lokalt domänanslutet AD:** Det här alternativet används ofta av organisationer som är relativt nöjda med sitt sätt att hantera datorer via AD-grupprinciper och/eller System Center Configuration Manager.

-   **Domänanslutet Azure AD och Intune-hantering:** Det här scenariot är vanligtvis avsett för CYOD (Choose Your Own Device) och roaming-scenarier för bärbara datorer där dessa enheter sällan är anslutna till företagets nätverk. Enheten ansluter till Azure AD och registreras i Intune, vilket tar bort alla beroenden på AD lokalt och på domänkontrollanter. Detta kan användas som villkor för villkorlig åtkomst vid anslutning till företagets resurser.

-   **Domänanslutet AD och System Center Configuration Manager:** Från och med den aktuella grenen tillhandahåller System Center Configuration Manager funktioner för villkorlig åtkomst som kan utvärdera specifika efterlevnadsvillkor, förutom att vara en domänansluten dator:

    -   Har datorn krypterats?

    -   Har skadlig kod installerats? Är den uppdaterad?

    -   Är enheten är jailbrokad eller rotad?

#### <a name="bring-your-own-device-byod"></a>BYOD (Bring Your Own Device)

-   **Arbetsplatsanslutning och Intune-hantering:** Här kan användaren ansluta sina personliga enheter och få åtkomst till företagets resurser och tjänster. Du kan använda arbetsplatsanslutning och registrera enheter i Intune och ta emot principer på enhetsnivå, vilket är ett alternativ till att utvärdera kriterier för villkorlig åtkomst.

## <a name="app-based-conditional-access"></a>Appbaserad villkorlig åtkomst

Intune och Azure Active Directory fungerar tillsammans så att endast hanterade appar har åtkomst till företagets e-post eller andra Office 365-tjänster.

-   Läs mer om [appbaserad villkorlig åtkomst med Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Nästa steg

[Konfigurera villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Så här installerar du Exchange Connector lokalt med Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Skapa en princip för villkorlig åtkomst för Exchange On-premises](conditional-access-exchange-create.md)
