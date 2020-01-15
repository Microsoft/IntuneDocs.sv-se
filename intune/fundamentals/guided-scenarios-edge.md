---
title: Guidat scenario – Distribuera Microsoft Edge för mobil
titleSuffix: Microsoft Intune
description: Lär dig mer om det guidade scenariot för att distribuera Microsoft Edge för mobil från Microsoft 365-enhetshanteringsportalen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88beb8f4791c127b0a225878f5bc43b6dd9b4025
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839380"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Guidat scenario – Distribuera Microsoft Edge för mobil 

Genom att följa det här [guidade scenariot](~/fundamentals/guided-scenarios-overview.md) kan du tilldela Microsoft Edge-appen till dina användare på iOS- eller Android-enheter i din organisation. Genom att tilldela den här appen kan användarna sömlöst bläddra bland innehåll med hjälp av sina företagsenheter. 

Med Microsoft Edge kan användare få ordning och reda på webben med inbyggda funktioner som hjälper dem att konsolidera, organisera och hantera arbetsinnehåll. Användare av iOS- och Android-enheter som loggar in med sina Azure AD-företagskonton i Microsoft Edge-programmet får arbetsplatsens **Favoriter** och webbplatsfilter som du definierar i sin webbläsare.

> [!NOTE]
> Om du har blockerat användare från att registrera antingen iOS- eller Android-enheter möjliggör detta scenario inte registrering, och användarna behöver då själva installera Edge.
Nedanstående Microsoft Edge-företagsfunktioner som aktiveras med Intune-principer är tillgängliga: 

- **Dubbel identitet** – Användarna kan lägga till både ett arbetskonto och ett personligt konto för surfning. Det finns en fullständig uppdelning mellan de två identiteterna, vilket liknar arkitektur och funktioner i Office 365 och Outlook. Intune-administratörer kommer att kunna ställa in de önskade principerna för en skyddad surfupplevelse på arbetskontot. 
- **Integrering med Intunes appskyddsprincip** – Administratörer kan nu använda appskyddsprinciper i Microsoft Edge, inklusive kontroll av klipp ut, kopiera och klistra in, förhindra skärmdumpar och säkerställa att användarvalda länkar bara öppnas i andra hanterade appar.
- **Integrering med Azure Application-proxy** – Administratörer kan styra åtkomsten till SaaS-appar och webbappar, vilket garanterar att webbläsarbaserade appar endast körs i den skyddade Microsoft Edge-webbläsaren, oavsett om användarna ansluter från företagets nätverk eller från Internet. 
- **Genvägar till hanterade favoriter och startsida** – För att underlätta åtkomsten kan administratörer ange URL:er som visas i Favoriter när slutanvändarna använder sin företagsmiljö. Administratörer kan ange en genväg till startsidan som visas som primär genväg när företagsanvändaren öppnar en ny sida eller en ny flik i Microsoft Edge.

## <a name="prerequisites"></a>Krav

- [Ange MDM-auktoriteten till Intune](mdm-authority-set.md#set-mdm-authority-to-intune) – inställningen för hantering av mobilenheter (MDM, Mobile Device Management) avgör hur du hanterar dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.
- Intune-administratörsbehörigheter som krävs:
    - Behörighet att läsa, skapa, ta bort och tilldela för hanterade appar
    - Behörighet att läsa, skapa och tilldela för mobilappar
    - Behörighet att läsa, skapa och tilldela för principuppsättningar
    - Behörighet att läsa och uppdatera för organisationen

## <a name="step-1---introduction"></a>Steg 1 – Introduktion

Genom att följa det guidade scenariot **Distribuera Microsoft Edge för mobil** konfigurerar du en grundläggande distribution av Microsoft Edge för en vald grupp av iOS- och Android-användare. Den här distributionen implementerar **Dubbla identiteter** och **Hanterade favoriter och genvägar för startsidan**. Dessutom installeras Microsoft Edge-appen automatiskt av Intune på enheter som registreras av de valda användarna. Den här automatiska installationen sker på alla användarstyrda registreringstyper, som omfattar: 
- iOS-registrering via Företagsportal-appen 
- iOS-registrering för användartillhörighet via Apple Business Manager 
- Äldre Android-registrering via Företagsportal-appen 

Det här guidade scenariot gör automatiskt så att **MyApps** visas i Microsoft Edge-favoriter och konfigurerar webbläsaren med samma varumärke som du har angett för Intune-företagsportalappen. 

### <a name="what-you-will-need-to-continue"></a>Det här behöver du för att fortsätta
Vi frågar dig om de favoriter på arbetsplatsen som dina användare behöver samt de filter du behöver för webbsurfning. Slutför följande uppgifter innan du fortsätter:

- Lägg till användare till Azure AD-grupper. Mer information finns i [Skapa en grundläggande grupp och lägga till medlemmar med hjälp av Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Registrera iOS- eller Android-enheter i Intune. Mer information finns i [Enhetsregistrering](https://go.microsoft.com/fwlink/?linkid=2102547).
- Skapa en lista över arbetsplatsens favoriter som ska läggas till i Microsoft Edge.
- Skapa en lista över webbplatsfilter som ska framtvingas i Microsoft Edge.

## <a name="step-2---basics"></a>Steg 2 – Grunderna

I det här steget måste du ange ett namn och en beskrivning för dina nya Microsoft Edge-principer. Dessa principer kan refereras senare om du behöver ändra tilldelningarna och konfigurationerna. Det guidade scenariot lägger till och tilldelar både en Microsoft Edge iOS-app för dina iOS-enheter och en Microsoft Edge Android-app för dina Android-enheter. Det här steget skapar även konfigurationsprinciper för dessa appar.

## <a name="step-3---configuration"></a>Steg 3 – Konfiguration

I det här steget konfigurerar det guidade scenariot Microsoft Edge till att visa alla andra appar som tilldelas till användare via Intune och delar samma varumärke som Microsoft Intune Företagsportal-appen. Du kan ytterligare konfigurera Microsoft Edge med en **URL för genväg för startsida**, en lista över **Hanterade bokmärken** samt en lista över **Blockerade URL:er**. **URL:en för genväg för startsida** visas för användare som den första ikonen nedanför sökfältet när de öppnar en ny flik i Microsoft Edge på sin enhet. **Hanterade bokmärken** är en lista över favorit-URL:er som användarna har tillgängliga när de använder Microsoft Edge i arbetskontexten. **Blockerade URL:er** anger de webbplatser som blockeras för användarna i arbetskontexten. Alla andra webbplatser tillåts. 

## <a name="step-4---assignments"></a>Steg 4 – Tilldelningar

I det här steget kan du välja de användargrupper som du vill inkludera för att få Microsoft Edge mobilkonfigurerat för arbete. Microsoft Edge installeras även på alla iOS- och Android-enheter som registreras av dessa användare.

## <a name="step-5---review--create"></a>Steg 5 – Granska och skapa

I det sista steget kan du granska en sammanfattning av de inställningar som du har konfigurerat. När du har granskat dina val klickar du på **Skapa** för att slutföra det guidade scenariot. 

> [!NOTE]
> Det kan ta upp till 12 timmar innan Edge får konfigurationen. Mer information finns i [Appkonfigurationsprinciper för Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> När det guidade scenariot är klart visas en sammanfattning. Du kan ändra de resurser som visas i sammanfattningen senare, men den tabell som visar dessa resurser kommer inte att sparas.

## <a name="next-steps"></a>Nästa steg

- Förbättra säkerheten för användning av Microsoft Edge genom att konfigurera integrering av Intune-appskyddsprincip. Mer information finns i [Appskyddsprinciper för Microsoft Edge](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Om du har webbplatser i intranätet som ska inkluderas bör du gå igenom skydd av åtkomst med integrering av Azure-programproxy. Mer information finns i [Konfigurera programproxyinställningar för Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

