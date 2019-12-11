---
title: Appskyddsprinciper och arbetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Se skillnader och för- och nackdelar innan du bestämmer dig för att använda appskyddsprinciper eller arbetsprofiler i personliga eller egna enheter (BYOD) med Android Enterprise i Microsoft Intune. Jämför de skillnader och funktioner som du får med appskyddsprinciper utan registrering (APP-WE) och Android Enterprise-arbetsprofiler.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0b4f8d5124924d013e7ac131dafc947a95c7b65
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059800"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Appskyddsprinciper och arbetsprofiler på Android Enterprise-enheter i Intune

I många organisationer måste administratörer skydda resurser och data på olika enheter. En utmaning är att skydda resurser för användare med personliga Android Enterprise-enheter, även kallat BYOD (Bring Your Own Device). Microsoft Intune stöder två Android-distributionsscenarier för BYOD:

- Appskyddsprinciper utan registrering (APP-WE)
- Android Enterprise-arbetsprofiler

Distributionsscenarierna med APP-WE och Android-arbetsprofiler innehåller följande viktiga funktioner för BYOD-miljöer:

1. **Skydd och uppdelning av organisationshanterade data**: Båda lösningarna skyddar organisationens data genom att tillämpa kontroller av dataförlustskydd (DLP) på organisationshanterade data. Dessa skydd förhindrar oavsiktligt läckage av skyddade data, till exempel om en slutanvändare av misstag delar data till en privat app eller ett privat konto. De ser även till att den enhet som har åtkomst till datan är felfri och inte komprometterad.

2. **Slutanvändarsekretess**: APP-WE och Android Enterprise-arbetsprofiler separerar slutanvändarnas innehåll på enheten och de data som hanteras av administratören för hantering av mobilenheter. I båda scenarierna tillämpar IT-administratörer principer, till exempel autentisering med PIN-kod, på organisationshanterade appar eller identiteter. IT-administratörerna kan inte läsa, få åtkomst till eller radera data som ägs eller kontrolleras av slutanvändare.

Om du väljer APP-WE eller Android Enterprise-arbetsprofiler för din BYOD-distribution beror på dina krav och vad företaget behöver. Målet med den här artikeln är att ge vägledning som kan hjälpa dig att bestämma detta.

## <a name="about-intune-app-protection-policies"></a>Om appskyddsprinciper i Intune

Intunes appskyddsprinciper är dataskyddsprinciper som är avsedda för användarna. Principerna tillämpar skydd mot dataförlust på programnivå. Intunes appskyddsprinciper kräver att apputvecklarna aktiverar appskyddsfunktioner i de appar som de skapar.

Fristående Android-appar har aktiverats för APP på flera sätt:

1. **Inbyggda i Microsofts förstapartsappar**: I Microsoft Offices appar för Android och ett flertal andra Microsoft-appar är Intunes appskyddsprinciper inbyggt. I dessa Office-appar (t.ex. Word, OneDrive och Outlook) behövs det inte någon mer anpassning för att tillämpa principerna. De här apparna kan installeras av slutanvändarna direkt från Google Play Butik.

2. **Integrerade i appversioner av utvecklare som använder Intune SDK**: Apputvecklarna kan integrera Intune SDK i sin källkod och kompilera om sina appar med stöd för principfunktionerna i Intunes appskyddsprinciper.

3. **Omslutna med hjälp av Intunes programhanteringsverktyg**: Vissa kunder kompilerar Android-appar (.APK-fil) utan att ha åtkomst till källkoden. Utvecklaren kan inte integrera Intune SDK utan källkoden. Utan SDK:n går det inte att aktivera appen för appskyddsprinciperna. Utvecklaren måste ändra eller koda om appen så att den stöder appskyddsprinciperna.

    Som hjälp innehåller Intune ett **programhanteringsverktyg** för befintliga Android-appar (APK) som skapar en app som identifierar appskyddsprinciper.

    Mer information om verktyget finns i [förbereda verksamhetsspecifika appar för appskyddsprinciper](../developer/apps-prepare-mobile-application-management.md).

En lista med appar som är aktiverade med appskyddsprinciper finns i [Hanterade appar med en omfattande uppsättning skyddsprinciper för mobila program](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Distributionsscenarier

I det här avsnittet beskrivs viktiga kännetecken för distributionsscenarier med APP-WE och Android Enterprise-arbetsprofiler.

### <a name="app-we"></a>APP-WE

En distribution med APP-WE (appskyddsprinciper utan registrering) definierar principer på appar, inte enheter. I det här scenariot är enheter vanligtvis inte registrerade eller hanterade av en MDM-utfärdare, t.ex Intune. För att skydda appar och åtkomst till organisationens data använder administratörer appar som det går att tillämpa dataskyddsprinciper på.

Den här funktionen gäller för:

- Android 4.4 och senare

> [!TIP]
> Mer information finns i [Vad är appskyddsprinciper?](app-protection-policy.md).

APP-WE-scenarier används av slutanvändare som vill ha en liten organisations fotavtryck på sina enheter och som inte vill registrera i MDM. Som administratör måste du fortfarande skydda dina data. Dessa enheter hanteras inte. Det innebär att vanliga MDM-uppgifter och funktioner, t.ex Wi-Fi, enhets-VPN och certifikathantering inte ingår i det här distributionsscenariot.

### <a name="android-enterprise-work-profiles"></a>Android Enterprise-arbetsprofiler

Arbetsprofiler är kärnan i distributionsscenariot för Android Enterprise och det enda scenario som är riktat mot BYOD-användning. Arbetsprofilen är en separat partition som skapas på operativsystemnivå i Android och som kan hanteras av Intune.

Den här funktionen gäller för:

- Android 5.0 och senare enheter med Googles mobiltjänster

Arbetsprofilen innehåller följande funktioner:

- **Traditionella MDM-funktioner**: Viktiga MDM-funktioner som till exempel hantering av appens livscykel med hjälp av hanterad Google Play, finns tillgängliga i alla Android Enterprise-scenarier. Hanterad Google Play är en stabil funktion som installerar och uppdaterar appar utan att användaren behöver göra något. IT-avdelningen kan även skicka appkonfigurationsinställningar till organisationens appar. Dessutom behöver inte slutanvändarna tillåta installationer från okända källor. Andra vanliga MDM-aktiviteter, till exempel att distribuera certifikat, konfigurera Wi-Fi/VPN och ange enhetslösenord, finns tillgängliga i arbetsprofilerna.

- **DLP på arbetsprofilgränsen**: Precis som med APP-WE kan IT-avdelningen tillämpa principer för dataskydd. Med en arbetsprofil tillämpas DLP-principerna på arbetsprofilnivå, inte på appnivå. Till exempel tillämpas skyddet för att kopiera och klistra in av appskyddsprincipen på en app, eller så tillämpas det av arbetsprofilen. När appen har distribuerats till en arbetsprofil, kan administratörer pausa skyddet för att kopiera och klistra in på arbetsprofilen genom att stänga av principen på appnivå.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Tips för att optimera arbetsprofilupplevelsen

### <a name="when-to-use-app-within-work-profiles"></a>När man ska använda appskyddsprinciper i arbetsprofiler

Intunes appskyddsprinciper och arbetsprofiler är kompletterande tekniker som kan användas tillsammans eller separat. Arkitektoniskt sett tillämpar lösningarna sina principer på olika nivåer – appskyddsprincipen på enskild appnivå och arbetsprofilen på profilnivå. Att distribuera appar som hanteras av en appskyddsprincip till en app i en arbetsprofil är ett giltigt scenario som stöds. Om du vill använda appskyddsprinciper, arbetsprofiler eller en kombination av dem beror på dina DLP-krav.

Arbetsprofiler och appskyddsprinciper kompletterar varandras inställningar genom att ge ytterligare säkerhet om en profil inte uppfyller organisationens dataskyddskrav. Till exempel innehåller inte arbetsprofiler interna kontroller som hindrar att en app sparas på en molnlagringsplats som inte är betrodd. Appskyddsprinciperna innehåller denna funktion. Du kan bestämma att den DLP som tillhandahålls av arbetsprofilen räcker och att du inte ska använda appskyddsprinciper. Eller så anser du att du behöver skydd från en kombination av båda.

### <a name="suppress-app-policy-for-work-profiles"></a>Ignorera appskyddsprinciper för arbetsprofiler

Du kan behöva stöd för enskilda användare som har flera enheter – ohanterade enheter i ett APP-WE-scenario och hanterade enheter med arbetsprofiler.

Exempelvis kan du kräva att slutanvändarna anger en PIN-kod när de öppnar en arbetsapp. Beroende på enhet hanteras funktionerna för PIN-koder av appskyddsprincipen eller av arbetsprofilen. För APP-WE-enheter tillämpas PIN-koden vid start av appskyddsprincipen. För arbetsprofilenheter kan du använda den PIN-kod för enheten eller arbetsprofilen som tillämpas av operativsystemet. Konfigurera inställningarna för appskyddsprinciper för det här scenariot, så att de inte tillämpas *när* en app distribueras till en arbetsprofil. Om du inte konfigurerar på det här sättet kommer slutanvändaren uppmanas ange en PIN-kod för enheten och sedan en gång till för appskyddsprincipen.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Kontrollera funktionssättet för flera identiteter i arbetsprofiler

Office-program, till exempel Outlook och OneDrive, har funktioner för flera identiteter. Slutanvändaren kan lägga till anslutningar till flera olika konton eller molnlagringsplatser inom en instans av programmet. Data som hämtats från dessa platser i programmet kan vara separata eller sammanfogade. Användaren kan utföra ett kontextbyte mellan personliga identiteter (user@outlook.com) och organisationsidentiteter (user@contoso.com).

När du använder arbetsprofiler kan du inaktivera den här funktionen för flera identiteter, om du vill. När du inaktiverar funktionen kan märkta instanser av appen i arbetsprofilen bara konfigureras med en organisationsidentitet. Använd appkonfigurationsinställningen Tillåtna konton om du vill ha stöd för Androids Office-appar.

Mer information finns i [appkonfigurationsinställningar för att distribuera Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>När du ska använda Intunes appskyddsprinciper

Det finns flera Enterprise Mobility-scenarier där användningen av Intunes appskyddsprinciper är det bästa alternativet.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Äldre enheter som kör Android 4.4–5.1 används

Officiellt innehåller alla enheter med Android 5.0 eller senare Googles mobiltjänster med stöd för arbetsprofiler. Vissa Android 5.0- och 5.1-enheter från vissa OEM-tillverkare stöder dock inte arbetsprofiler.

Om du använder versioner som saknar stöd för arbetsprofiler och om du vill ha ett dataförlustskydd (DLP) för organisationens data på enheterna, måste du använda Intunes appskyddsprinciper.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Ingen MDM, ingen registrering, Google-tjänster är inte tillgängliga

Vissa kunder vill inte ha någon form av enhetshantering, inklusive arbetsprofiler, av olika skäl:

- Juridiska och ansvarsmässiga orsaker
- För att ha en konsekvent användarupplevelse
- Android-enhetsmiljön är mycket heterogen
- Det finns inte någon anslutning till Google-tjänster, vilket krävs vid hanteringen av arbetsprofilen.

Till exempel kan kunder i (eller som har användare i) Kina inte använda Androids enhetshantering eftersom Google-tjänsterna är blockerade. I det fallet används Intunes appskyddsprinciper för DLP.

## <a name="summary"></a>Sammanfattning

Om du använder Intune har du tillgång till både APP-WE och Android Enterprise-arbetsprofiler för dina Android BYOD-program. Om du ska välja APP-WE eller arbetsprofiler beror på dina krav på verksamhet och användning. Sammanfattningsvis ska du använda arbetsprofiler om du behöver MDM-aktiviteter på hanterade enheter, till exempel distribution av certifikat, app-push och så vidare. Använd APP-WE om du inte vill eller kan hantera enheter och om du bara använder appar med Intunes appskyddsprinciper.

## <a name="next-steps"></a>Nästa steg
[Börja använda appskyddsprinciper](app-protection-policy.md) eller [registrera dina enheter](../enrollment/android-enroll.md).
