---
title: Tidig utgåva – Microsoft Intune
titlesuffix: ''
description: Tidig utgåva av Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203441"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Den tidiga utgåvan för Microsoft Intune – Januari 2019

> [!Note]
> Sekretessavtalsmeddelande: Följande ändringar är under utveckling för Intune. Den här informationen har mycket begränsad spridning, i enlighet med sekretessavtalet. Sprid inte den här informationen vidare på sociala medier eller offentliga webbplatser, till exempel Twitter, UserVoice, Reddit och så vidare. 

Den **tidiga utgåvan** innehåller en lista med funktioner, som delas i enlighet med sekretessavtalet, som ingår i kommande versioner av Microsoft Intune. Den här informationen tillhandahålls på ett begränsat sätt och kan komma att ändras. Dela inte den här informationen på Twitter, UserVoice eller på något annat sätt med någon utanför företaget. Vissa funktioner som beskrivs här kanske inte blir klara i tid och kanske därför inte blir aktuella förrän i framtida versioner. Andra funktioner pilottestas (förhandsversionstestning) för att säkerställa att de är kundklara. Kontakta Microsofts produktgrupp om du har frågor eller funderingar.

Den här sidan uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune i Azure Portal

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android Enterprise-appar <!-- 1352553  -->
Du kommer att kunna ta bort hanterade Google Play-appar från Microsoft Intune. Om du vill ta bort en hanterad Google Play-app måste du öppna Microsoft Intune i Azure-portalen och välja **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

### <a name="managed-google-play-app-type----1352580---"></a>Hanterade Google Play-apptyper <!-- 1352580 -->
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kommer du nu att kunna bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune. Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du kommer inte längre behöva autentisera dig på nytt. I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Hanterat Google Play-konto** som apptyp.

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Förhandsgranskning av stöd för företagsägda, fullständigt hanterade Android-enheter <!-- 1574342  -->
Intune stöder helt hanterade Android-enheter, ett företagsägt scenario av ”enhetsägare” där enheter hanteras noggrant av IT och är kopplade till enskilda användare. Detta gör att administratörer kan hantera hela enheten, tillämpa en utökad uppsättning principkontroller som inte är tillgängliga för arbetsprofiler och begränsa användare från att installera appar från hanterad Google Play endast. För att konfigurera fullständigt hanterade Android-enheter, går du till **Enhetsregistrering** > **Android-registrering** > **Företagsägda, fullständigt hanterade användarenheter**. Observera att den här funktionen är en förhandsversion. Vissa Intune-funktioner, till exempel certifikat, efterlevnad och villkorlig åtkomst, är inte tillgängliga med fullständigt hanterade Android-användarenheter.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribution av online-licensierade Microsoft Store för företag-appar <!-- 1672660  -->
Du kommer att kunna tilldela nödvändiga online-licensierade Microsoft Store för företag-appar i kontexten för enheten. Genom att distribuera en Microsoft Store för företag-app på detta sätt, kan appen installeras för alla användare på enheten. Detta gäller endast för Windows 10 RS4+ desktop-enheter. Alternativet att installera i kontexten för enheten finns på sidan Tilldelning av klientappar för MSFB Online-licensierade appar.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Konfigurera profilen om du vill hoppa över vissa av skärmarna i installationsassistenten <!-- 2276470  -->
När du skapar en macOS-registreringsprofil kommer du att kunna konfigurera den för att hoppa över valfria följande skärmar när en användare går igenom installationsassistenten:
- Android-migrering
- Visningston
- Sekretess
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Tilldela Autopilot-profiler till den virtuella gruppen Alla enheter <!--2715522  -->
Du kommer att kunna tilldela Autopilot-profiler till den virtuella gruppen Alla enheter. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > välj en profil >  **Tilldelningar** > under **Tilldela till** väljer du **Alla enheter**. Mer information om Autopilot-profiler finns i [Registrera Windows-enheter med hjälp av Windows Autopilot](enrollment-autopilot.md).

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>Anpassa bakgrund på övervakade iOS-enheter med hjälp av en profil för enhetskonfiguration <!-- 2809324  -->
När du skapar en profil för enhetskonfiguration för iOS-enheter kommer du att kunna tillåta och begränsa vissa inställningar i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltypen. Den här uppdateringen innehåller nya inställningar för **Bakgrund** som gör att en administratör kan använda en .png-, .jpg- eller .jpeg-bild som bakgrund, förhandsgranska bilden och blockera användare från att ändra bakgrundsbilden. Inställningar för bakgrund gäller endast för övervakade enheter. En lista över de aktuella inställningarna finns i [Enhetsbegränsningar för iOS](device-restrictions-ios.md).

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popup-meddelanden för Win32-appar <!-- 3136566   -->
Du kommer att kunna förhindra att visa slutanvändares popup-meddelanden per apptilldelning. Från Intune, väljer du **Klientappar** > **Appar** > välj appen > **Tilldelningar** > **Inkludera grupper**. 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>Dela kontakter via Bluetooth har tagits bort i Enhetsbegränsningar > Enhetens ägare för Android Enterprise <!-- 3598396 -->
När du skapar en profil för enhetsbegränsningar för Android Enterprise-enheter finns inställningen **Dela kontakter via Bluetooth**. I den här uppdateringen kommer inställningen **Dela kontakter via Bluetooth** att tas bort (**Enhetskonfiguration** > **Profiler**  >  **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar > Enhetens ägare** för profiltyp >  **Allmän**). 

Inställningen **Dela kontakter via Bluetooth** har inte stöd för hantering av Android Enterprise-enhetens ägare. Så när den här inställningen tas bort, påverkar det inga enheter eller klienter, även om den här inställningen är aktiverad och konfigurerad i din miljö.

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md).

Gäller för: Ägare av Android Enterprise-enhet

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kommer du att kunna använda hanterade Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan IT-avdelningen kan ge slutanvändarna en app-katalog och installationsupplevelse som inte längre kräver att slutanvändare minskar säkerhetspositionen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK stöder 256-bitars krypteringsnycklar <!-- 1832174 -->
Intune App SDK för Android använder 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Uppdatering av Intune-principers autentiseringsmetod och installation av företagsportalappen  <!-- 1927359 -->
På enheter som redan har registrerats via Installationsassistenten med någon av Apples metoder för registrering av företagsenheter, stöder Intune inte längre företagsportalen om den installeras manuellt av slutanvändarna från App Store. Den här ändringen gäller endast när du autentiserar med Apple-installationsassistenten under registreringen. Den här ändringen påverkar också bara iOS-enheter som registrerats via:  
* Apple configurator
* Apple Business Manager
* Apple School Manager
* Apples program för enhetsregistrering (DEP)

Om användare installerar företagsportalappen från App store och sedan försöker att registrera enheterna genom den, får de ett felmeddelande. Dessa enheter kommer förväntas att bara använda företagsportalen när den har skickats automatiskt av Intune under registreringen. Profiler för registrering i Intune i Azure-portalen kommer att uppdateras så att du kan ange hur enheter ska autentiseras och om de får företagsportalappen. Om du vill att dina DEP-enhetsanvändare ska ha företagsportalen behöver du ange dina preferenser i en registreringsprofil. Dessutom kommer skärmen **Identifiera din enhet** i företagsportalappen snart att bli föråldrad.  
För att installera företagsportalen på redan registrerade DEP-enheter, måste du gå till Intune > Klientappar, och skicka den som en hanterad app med konfigurationsprinciper för appar. Information om hur du utför dessa steg kommer att ges i framtida dokument.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379 -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar. Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering. De aktuella inställningarna finns i [Endpoint protection-inställningar för Windows 10](endpoint-protection-windows-10.md#windows-encryption).


### <a name="additional-settings-for-outlook----3301182---"></a>Ytterligare inställningar för Outlook <!-- 3301182 -->
Nu kan du konfigurera ytterligare inställningar för Outlook för iOS och Android med hjälp av Intune.  Det här är några inställningar:
- Tillåt bara arbets- eller skolkonton att användas i Outlook i iOS och Android
- Distribuera modern autentisering för Office 365 och lokala konton med modern hybridautentisering
- Använd `SAMAccountName` för användarnamnfältet i e-postprofilen när grundläggande autentisering väljs
- Tillåt att kontakter sparas
- Konfigurera e-posttips för externa mottagare
- Konfigurera **Prioriterad inkorg**
- Kräv biometri för åtkomst till Outlook för iOS 
- Blockera externa bilder

> [!NOTE]
> Om du använder principer för Intune-appskydd till att hantera åtkomsten för företagsidentiteter bör du inte aktivera att **kräva biometri**. Mer information finns i **Kräva företagsautentiseringsuppgifter för åtkomst** för [iOS-åtkomstkrav](app-protection-policy-settings-ios.md#access-settings) och [Android-åtkomstkrav](app-protection-policy-settings-android.md#access-settings).

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till deras egna konfigurationsprofil <!-- 3322847 -->
Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i privat förhandsvisning. I denna uppdatering: De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
Administrativa mallar finns i offentlig förhandsversion, administrativa mallar flyttar från **Enhetskonfiguration** > **Administrationsmallar** till **Enhetskonfiguration** > **Profiler** >**Skapa profil** > i **Plattform**, välj  **Windows 10 och senare**i **Profiltyp**, välj **Administrationsmallar**.
Rapportering är aktiverad och gäller för: Windows 10 och senare

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Mörkt läge i Intune macOS-företagsportalen <!-- 3300524 -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Använd Microsofts rekommenderade inställningar med säkerhetsbaslinjer <!-- 2055484 -->
Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kommer att kunna skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. De kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i deras organisation. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Distribuerade WIP-principer utan användarregistrering <!-- 1434452 -->
WIP-principer (Windows Information Protection) kommer att kunna distribueras utan att MDM-användare behöver registrera sina Windows 10-enheter. Med den här konfigurationen kan företag skydda sina företagsdokument baserat på WIP-konfigurationen, samtidigt som användarna kan fortsätta att hantera sina egna Windows-enheter. När dokument skyddas med en WIP-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>APP-inställningar (App Protection Policy) för webbdata <!-- 2662995 -->
Principinställningarna för webbinnehåll på både Android och iOS-enheter kommer att uppdateras så att de blir bättre på att hantera både http- och https-länkar liksom dataöverföring via universella iOS-länkar och Android App-länkar.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Apple VPP-token som används av en annan MDM <!-- 1488946 -->
Intune identifierar och visar information om en token för volyminköpt Apple-program (VPP) används av både Intune och en annan MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Tillbakadragna enheter i instrumentpanelen för enhetsefterlevnad <!-- 1981119 -->
I en kommande uppdatering tas tillbakadragna enheter bort från instrumentpanelen för enhetsefterlevnad. Detta ändrar dina efterlevnadsnummer.



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052 -->
En kommande uppdatering innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompatibilitet** > **Principer** > **Skapa princip** > **Windows 10**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av Intune-inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd kommer enheten inte att vara kompatibel i Intune.

Gäller för Windows 10 och senare



## <a name="notices"></a>Meddelanden

Det finns inga aktiva meddelanden just nu.

### <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).



