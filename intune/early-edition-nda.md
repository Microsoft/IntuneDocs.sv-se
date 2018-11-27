---
title: Tidig utgåva
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: fbe8cc0fc3e835ee5807dfbe56ea1aa3c728547e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184734"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Den tidiga utgåvan för Microsoft Intune – November 2018

> [!Note]
> Meddelande om sekretessavtal: Följande ändringar håller på att utvecklas för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Avinstallera appar på företagsägda övervakade iOS-enheter <!-- 1281677 -->
Du kommer att kunna ta bort alla appar på företagsägda övervakade iOS-enheter. Du kan ta bort en app genom att rikta antingen användar- eller enhetsgrupper med tilldelningstypen **avinstallera**. För personliga eller ej kontrollerade iOS-enheter kommer du fortsätta kunna ta bort appar som har installerats med hjälp av Intune.

### <a name="track-installation-of-office-proplus---2620217--"></a>Spåra installation av Office ProPlus <!--2620217-->
Du kommer att kunna följa installationsförloppet för [Office ProPlus](apps-add-office365.md) med hjälp av sidan [Registreringsstatus](windows-enrollment-status.md).

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>macOS DEP-stöd för Apple School Manager-konton <!--3006133-->
Intune stöder användning av programmet för enhetsregistrering (DEP) på macOS-enheter för Apple School Manager-konton.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Pausa tillfälligt helskärmsläge på Android-enheter för att göra ändringar <!-- 3041935 -->
När du använder Android-enheter i helskärmsläge för flera appar, kan en IT-administratör behöva göra ändringar i enheten. En ny inställning för helskärmsläge för flera appar gör att en IT-administratör tillfälligt kan pausa helskärmsläget med hjälp av en PIN-kod och få åtkomst till hela enheten.
Om du vill se de aktuella inställningarna för helskärmsläge, se [Android-helskärmsinställningar](android-kiosk-settings.md).

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Ange en anpassad bakgrund den hanterade hemskärmsappen  <!-- 3041945 -->
Vi ska lägga till en inställning som låter dig anpassa bakgrundsutseendet på den hanterade hemskärmsappen på Android Enterprise, flera appar, enheter i helskärmsläge.  För att konfigurera **Anpassad URL-bakgrund** går du till Intune i Azure portal > Enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivera den virtuella hemknappen på Android-företagsenheter i helskärmsläge  <!-- 3042021 -->
En ny inställning låter användare trycka på en programstyrd knapp på sin enhet för att växla mellan den hanterade hemskärmsappen och andra tilldelade appar på sin enhet för helskärmsläget för flera appar. Den här inställningen är särskilt användbart i scenarier där en användares app för helskärmsläge inte svarar på rätt sätt på knappen ”Bakåt”. Du kommer att kunna konfigurera den här inställningen för företagsägda Android-enheter för enskild användning. För att aktivera eller inaktivera den **virtuella hemknappen**, går du till Intune i Azure Portal > enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Spara och tillämpa tilldelning av appskyddsprincip <!-- 3104570 -->
Du får bättre kontroll över dina tilldelningar av appskyddsprincip. Genom att spara och tillämpa dina tilldelningar av appskyddsprincip påverkas endast de avsedda användarna direkt av en tilldelningsprincip av appskydd.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nya Microsoft Edge-webbläsarinställningar för Windows 10 och senare <!-- 3174639 -->
En ny inställning läggs till för att styra och hantera Microsoft Edge-webbläsaren på dina enheter. En lista över de aktuella inställningarna finns i [Enhetsbegränsning för Windows 10 (och senare)](device-restrictions-windows-10.md#microsoft-edge-browser).

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Välj appar som spårats på sidan för registreringsstatus<!-- 2531007 -->
Du kommer att kunna välja vilka appar som spåras på sidan för registreringsstatus.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Uppdatering av användargränssnitt för Intune-appskyddsprinciper <!-- 3251427 -->

Med Intune-appskyddsprinciper kan du konfigurera olika dataskyddsinställningar för Intune-skyddade appar, till exempel Microsoft Outlook och Word. Vi ändrar inställningen och knappetiketterna så att varje princip blir lättare att förstå. Kontrollerna kommer att ändras från kontrollerna **ja**/**nej** till främst kontrollerna **blockera**/**tillåta** och **inaktivera**/**aktivera**, och etiketterna kommer också att uppdateras för tydlighetens skull. Inställningarna kommer också formateras så att inställningen och dess etikett är sida vid sida i kontrollen, vilket ger bättre navigering. Standardinställningar och antal inställningar förblir detsamma, men den här ändringen gör att användarna kan förstå, navigera och använda inställningar enklare för att tillämpa valda appskyddsprinciper.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Använd Microsofts rekommenderade inställningar med säkerhetsbaslinjer <!-- 2055484 -->
Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kommer att kunna skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. De kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i deras organisation. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

### <a name="scope-tags-for-apps---1081941---"></a>Omfattningstaggar för appar <!--1081941 -->
Du kommer att kunna skapa omfångstaggar som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).
Om du vill skapa en omfångstagg väljer du **Intune-roller** > **Scope (Tags) (Omfång (taggar))** > **Skapa**.
För att lägga till en omfångstagg till en rolltilldelning väljer du **Intune-roller** > **Alla roller** > **Princip- och profilhanterare** > **Tilldelningar** > **Scope (Tags)** (Omfång (taggar)).
För att lägga till en omfångstagg till en konfigurationsprofil väljer du **Enhetskonfiguration** > **Profiler** > välj en profil > **Egenskaper** > **Scope (Tags)** (Omfång (taggar)).

### <a name="tenant-health-dashboard----1124854---"></a>Instrumentpanelen Hälsa för klientorganisation <!-- 1124854 -->
På sidan med klientorganisationens status i Intune hittar du information om klientorganisationens status på ett och samma ställe. Sidan är uppdelad i fyra delar:  
- **Information om klientorganisationen**: Innehåller information, till exempel MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet**: Innehåller information om konfigurerade anslutningsappar, till exempel Apple VPP, Windows Store för företag och certifikatanslutningar. Baserat på deras aktuella tillstånd är anslutningsapparna flaggade med *Felfri*, *Varning* eller *Ej felfri*.
- **Hälsotillstånd för Intune-tjänsten**: Innehåller aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).
- **Nytt i Intune**: Innehåller aktiva meddelanden för din klientorganisation, t.ex. aviseringar om att klientorganisationen har fått de senaste funktionerna i Intune. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office ([https://portal.office.com](https://portal.office.com)).


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Distribuerade WIP-principer utan användarregistrering <!-- 1434452 -->
WIP-principer (Windows Information Protection) kommer att kunna distribueras utan att MDM-användare behöver registrera sina Windows 10-enheter. Med den här konfigurationen kan företag skydda sina företagsdokument baserat på WIP-konfigurationen, samtidigt som användarna kan fortsätta att hantera sina egna Windows-enheter. När dokument skyddas med en WIP-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-available-in-compliance-policies----1892471---"></a>Versionsnummer och byggenummer för iOS och macOS finns i efterlevnadsprinciperna <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas operativsystemsversionerna iOS och macOS. De är tillgängliga för användning i efterlevnadsprinciper. I en framtida uppdatering kommer även byggenumret att kunna konfigureras för båda plattformarna.

När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att använda byggenumret i en efterlevnadsprincip kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Ändra i uppdateringsprocessen för lokala anslutningsappar <!-- 2277554 -->
Baserat på feedback från kunder kommer det sätt som uppdateringar av lokala anslutningsappar sker på att ändras. När du först installerar en lokal anslutningsapp sker uppdateringar automatiskt. Den här ändringen börjar i och med den nya PFX-certifikatanslutningsappen för Microsoft Intune och kommer därefter att distribueras till andra typer av lokala anslutningsappar. 

<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052 -->
En kommande uppdatering innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompatibilitet** > **Principer** > **Skapa princip** > **Windows 10**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av Intune-inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



