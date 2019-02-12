---
title: Nyheter i Microsoft Intune – Azure | Microsoft Docs
titlesuffix: ''
description: Ta reda på vad som är nytt i Intune Azure-portalen
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 996b4d85da41b480d73d7a79011e2bbd732ea334
ms.sourcegitcommit: dde9e1e1d15c412751a186410c2a04974ff1b102
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690843"
---
# <a name="whats-new-in-microsoft-intune"></a>Nyheter i Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Läs mer om varje veckas nyheter i Microsoft Intune. Du hittar även kommande ändringar, [viktiga meddelanden](#notices) och information om [tidigare versioner](whats-new-archive.md). 

> [!Note]
> Vissa funktioner kan distribueras över flera veckor och kanske inte är tillgängliga för alla kunder den första veckan.
>
> På [hybridsidan med senaste nytt](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management) finns mer information om nya funktioner för hybridhantering av mobilenheter (MDM).

**RSS-feed**: Håll dig informerad när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-february-4-2019"></a>Veckan för 4 februari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-macos-company-portal-dark-mode----3300524-eeready---"></a>Mörkt läge i Intune macOS-företagsportalen <!-- 3300524 eeready -->
Nu stöder Intune macOS-företagsportalen mörkt läge för macOS. När du aktiverar mörkt läge på en macOS 10.14 +-enhet kommer företagsportalen att justera dess utseende till färger som speglar detta läge.

## <a name="week-of-january-21-2019"></a>Veckan som börjar den 21 januari 2019

### <a name="app-management"></a>Apphantering

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Popup-meddelanden för Win32-appar <!-- 3136566   -->
Du kan förhindra att popup-meddelanden per apptilldelning visas för slutanvändarna. Från Intune, väljer du **Klientappar** > **Appar** > välj appen > **Tilldelningar** > **Inkludera grupper**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Uppdatering av användargränssnitt för Intune-appskyddsprinciper <!-- 3251427  -->
Vi har ändrat etiketterna för inställningar och knappar i Intunes appskydd för att de ska bli lättare att förstå. Några av ändringarna omfattar:  
- Kontroller ändras från **ja** / **nej** till primärt **blockera** / **tillåt** och **inaktivera** / **aktivera** kontroller. Även etiketterna har uppdaterats.  
- Inställningarna formateras om så att inställningen och dess etikett är sida vid sida i kontrollen, vilket ger bättre navigering.   

Standardinställningar och antal inställningar förblir detsamma, men den här ändringen gör att användarna kan förstå, navigera och använda inställningar enklare för att tillämpa valda appskyddsprinciper. Mer information finns i [iOS-inställningar](app-protection-policy-settings-ios.md) och [Android-inställningar](app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook----3301182----"></a>Ytterligare inställningar för Outlook <!-- 3301182  -->
Nu kan du konfigurera följande ytterligare inställningar för Outlook för iOS och Android med hjälp av Intune:
- Tillåt bara arbets- eller skolkonton att användas i Outlook i iOS och Android
- Distribuera modern autentisering för Office 365 och lokala konton med modern hybridautentisering
- Använd `SAMAccountName` för användarnamnfältet i e-postprofilen när grundläggande autentisering väljs

Följande inställningar lanseras fortfarande gradvis och blir tillgängliga i konsolen snart:
- Tillåt att kontakter sparas
- Konfigurera e-posttips för externa mottagare
- Konfigurera **Prioriterad inkorg**
- Kräv biometri för åtkomst till Outlook för iOS

Inställningen nedan visas i Intune-konsolen men fungerar inte som förväntat när den har konfigurerats. Det här problemet åtgärdas snart:
- Blockera externa bilder

> [!NOTE]
> Om du använder principer för Intune-appskydd till att hantera åtkomsten för företagsidentiteter bör du inte aktivera att **kräva biometri**. Mer information finns i **Kräva företagsautentiseringsuppgifter för åtkomst** för [iOS-åtkomstinställningar](app-protection-policy-settings-ios.md#access-requirements) och [Android-åtkomstinställningar](app-protection-policy-settings-android.md#access-requirements).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Ta bort Android Enterprise-appar <!-- 1352553 -->
Du kan ta bort hanterade Google Play-appar från Microsoft Intune. Om du vill ta bort en hanterad Google Play-app öppnar du Microsoft Intune i Azure-portalen och väljer **Klientappar** > **Appar**. Från listan över appar väljer du ellipserna (...) till höger om den hanterade Google Play-appen och väljer sedan **Ta bort** från den visade listan. När du tar bort en hanterad Google Play-app från applistan blir den hanterade Google Play-appen automatiskt ej godkänd.

#### <a name="managed-google-play-app-type----1352580---"></a>Hanterade Google Play-apptyper <!-- 1352580 -->
Den **hanterade Google Play**-apptypen gör att du kan lägga till mer specifikt [hanterade Google Play-appar](https://play.google.com/work/search?q=microsoft&c=apps) till Intune. Som Intune-administratör kan du bläddra, söka, godkänna, synkronisera och tilldela godkända hanterad Google Play-appar i Intune.  Du behöver inte längre bläddra till den hantera Google Play-konsolen separat och du behöver inte längre autentisera dig på nytt.  I Intune, väljer du **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** väljer du **Hanterat Google Play-konto** som apptyp.

### <a name="default-android-pin-keyboard----3802457---"></a>Standardtangentbord för PIN-kod i Android <!-- 3802457 -->
För slutanvändare som har angett en PIN-kod för Intune-appskydd (APP) på sina Android-enheter med PIN-kodtypen ”Numerisk” visas nu standardtangentbordet för Android istället för det fasta Android-tangentbordsgränssnittet som utformats tidigare. Den här ändringen har gjorts för att vara konsekvent när standardtangentbord används på både Android och iOS, för båda PIN-typerna ”Numerisk” och/eller ”Lösenord”. Mer information om inställningar för slutanvändaråtkomst på Android, till exempel PIN-kod för APP finns i [Åtkomstkrav för Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Använd Microsofts rekommenderade inställningar med säkerhetsbaslinjer (allmänt tillgänglig förhandsversion) <!-- 2055484   -->

Intune integrerar med andra tjänster som fokuserar på säkerhet, inklusive Windows Defender ATP och Office 365 ATP. Kunder efterfrågar en gemensam strategi och en sammanhängande uppsättning säkerhetsarbetsflöden från slutpunkt till slutpunkt för alla Microsoft 365-tjänster. Vårt mål är att optimera strategier och skapa lösningar som kan hantera säkerhetsåtgärder och vanliga administratörsuppgifter. I Intune vill vi uppnå det här målet genom att publicera en uppsättning Microsoft-rekommenderade ”säkerhetsbaslinjer” (**Intune** > **Security baselines** ((Säkerhetsbaslinjer)).  En administratör kan skapa säkerhetsprinciper direkt från dessa baslinjer, och sedan distribuera dem till sina användare. Du kan också anpassa rekommendationerna om bästa praxis för att uppfylla behoven i organisationen. Intune kontrollerar att enheterna uppfyller baslinjerna och meddelar administratören om användare eller enheter inte uppfyller efterlevnadskraven.

Den här funktionen är en offentlig förhandsversion, så profiler som skapas nu flyttas inte över till säkerhetsbaslinjemallar som är allmänt tillgängliga. Du bör inte planera att använda dessa förhandsmallar i produktionsmiljö.

Läs mer om säkerhetsbaslinjer i [Skapa en säkerhetsbaslinje för Windows 10 i Intune](security-baselines-monitor.md).

Den här funktionen gäller för: Windows 10 och senare

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>Icke-administratörer kan aktivera BitLocker på Windows 10-enheter som är anslutna till Azure AD<!-- 2147379   -->
När du aktiverar BitLocker-inställningar på Windows 10-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** för plattform > **Endpoint protection** för Profiltyp > **Windows-kryptering**), lägger du till BitLocker-inställningar. 

Den här uppdateringen innehåller en ny inställning för BitLocker för att låta standardanvändare (icke-administratörer) aktivera kryptering. 

De här inställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Kontrollera Configuration Manager-kompatibilitet <!-- 2192052  eepublished  -->
Den här uppdateringen innehåller en ny kompatibilitetsinställning för System Center Configuration Manager (**Enhetskompabilitet** > **Principer** > **Skapa princip** > **Windows 10 och senare** > **Configuration Manager-kompabilitet**). Configuration Manager skickar signaler till Intune-kompatibilitet. Med hjälp av inställningen kan du kräva att alla Configuration Manager-signaler returnerar ”kompatibel”.

Du kan till exempel kräva att alla programuppdateringar installeras på enheter. Det här kravet har tillståndet ”installerad” i Configuration Manager. Om några program på enheten är i ett okänt tillstånd är enheten inte kompatibel i Intune.

[Configuration Manager-kompatibilitet](compliance-policy-create-windows.md#configuration-manager-compliance) beskriver den här inställningen.

Gäller för: Windows 10 och senare

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Anpassa bakgrund på övervakade iOS-enheter med hjälp av en profil för enhetskonfiguration <!-- 2809324   -->
När du skapar en profil för enhetskonfiguration för iOS-enheter kan du anpassa vissa inställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsfunktioner** för profiltypen). Den här uppdateringen innehåller nya inställningar för **Bakgrund** som gör att administratörer kan använda en .png-, .jpg- eller .jpeg-bild på startsidan eller låsskärmen. Inställningar för bakgrund gäller endast för övervakade enheter. 

En lista över de här inställningarna finns i [Funktionsinställningar för iOS-enheter](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Helskärmsläge för Windows 10 är allmänt tillgänglig <!-- 3594661  -->
I den här uppdateringen är funktionen helskärmsläge på Windows 10 och senare enheter allmänt tillgängligt (GA). Alla inställningar som du kan lägga till och konfigurera finns i [Inställningar för helskärmsläge för Windows 10 (och senare)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Dela kontakter via Bluetooth har tagits bort i Enhetsbegränsningar > Enhetens ägare för Android Enterprise <!-- 3598396   -->
När du skapar en profil för enhetsbegränsningar för Android Enterprise-enheter finns inställningen **Dela kontakter via Bluetooth**. I den här uppdateringen tas inställningen **Dela kontakter via Bluetooth** bort (**Enhetskonfiguration** > **Profiler**  >  **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar > Enhetens ägare** för profiltyp > **Allmän**). 

Inställningen **Dela kontakter via Bluetooth** har inte stöd för hantering av Android Enterprise-enhetens ägare. Så när den här inställningen tas bort, påverkar det inga enheter eller klienter, även om den här inställningen är aktiverad och konfigurerad i din miljö.

Om du vill se den aktuella listan över inställningar, gå till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner](device-restrictions-android-for-work.md).

Gäller för: Ägare av Android Enterprise-enhet

### <a name="device-management"></a>Enhetshantering

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Stöd för selektiv rensning för WIP-WE-enheter <!-- 1434452 -->
Med WIP-WE (Windows Information Protection Without Enrollment) kan kunder skydda sina företagsdata på Windows 10-enheter utan att fullständig MDM-registrering krävs. När dokument skyddas med en WIP-WE-princip kan skyddade data rensas selektivt av en Intune-administratör. Genom att välja användaren och enheten, och skicka en rensningsbegäran, blir alla data som skyddades via WIP-WE-principen oanvändbara. Från Intune på Azure-portalen väljer du **Mobilapp** > **Selektiv radering av app**.

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Ny arbetsloggar och möjligheten att skicka loggar till Azure Monitor-tjänster <!-- 3762211  -->
Intune har inbyggd granskningsloggning som spårar händelser när de ändras. Den här uppdateringen innehåller nya loggningsfunktioner, inklusive: 
- Arbetsloggar (förhandsversion) som visar information om användare och enheter som registrerats, inklusive lyckade och misslyckade försök.
- Granskningsloggarna och arbetsloggarna kan skickas till Azure Monitor, inklusive lagringskonton, händelsehubbar och logganalyser. De här tjänsterna gör att du kan lagra och använda analyser som Splunk och QRadar samt få visualiseringar av dina loggningsdata.

[Skicka data till lagring, händelsehubbar eller logganalyser i Intune](review-logs-using-azure-monitor.md) har mer information om den här funktionen.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Hoppa över flera skärmar för installationsassistenten på en iOS DEP-enhet <!-- 2687509  -->
Förutom de skärmar som du kan hoppa över just nu kan du ange att iOS DEP-enheter hoppar över följande skärmar i installationsassistenten när en användare registrerar enheten: Skärmton, Sekretess, Android-migrering, Start-knapp, iMessage och FaceTime, Registrering, Bevaka migrering, Utseende, Skärmtid, Programuppdatering, SIM-installation.
Om du vill välja vilka skärmar som ska hoppas över, går du till **Enhetsregistrering** > **Apple-registrering** > **Tokens för registreringsprogram** > välj en token > **Profiler** > välj en profil > **Egenskaper** > **Anpassning av installationsassistenten** > välj **Dölj** för alla skärmar som du vill hoppa över > **OK**.
Om du skapar en ny profil eller redigerar en profil måste den valda överhoppningsskärmen synkroniseras med Apple MDM-servern. Användare kan utfärda en manuell synkronisering av enheterna så att det inte sker någon fördröjning i att plocka upp profiländringarna.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Appdistribution för Android Enterprise APP-WE <!-- 1171203 -->
För Android-enheter i ett distributionsscenario med en appskyddsprincip utan registrering (APP-WE) kan du nu använda hanterad Google Play för att distribuera store-appar och LOB-appar till användare. Mer specifikt kan du ge slutanvändarna en appkatalog och installationsfunktioner som inte längre kräver att slutanvändare lättar på säkerhetshållningen för sina enheter genom att tillåta installationer från okända källor. Dessutom kan det här distributionsscenariot ge en förbättrad slutanvändarupplevelse.

## <a name="week-of-january-14-2019"></a>Veckan som börjar den 14 januari 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Förhandsgranskning av stöd för företagsägda, fullständigt hanterade Android-enheter <!-- 1574342  -->
Nu har Intune fullt stöd för hanterade Android-enheter, ett företagsägt scenario av ”enhetsägare” där enheter hanteras noggrant av IT och är kopplade till enskilda användare. Detta gör att administratörer kan hantera hela enheten, tillämpa en utökad uppsättning principkontroller som inte är tillgängliga för arbetsprofiler och begränsa användare från att installera appar från hanterad Google Play endast. Mer information finns i artiklarna om att [konfigurera Intune-registrering av fullständigt hanterade Android-enheter](android-fully-managed-enroll.md) och att [registrera dedikerade enheter eller fullständigt hanterade enheter](android-dedicated-devices-fully-managed-enroll.md).  Observera att den här funktionen är en förhandsversion. Vissa Intune-funktioner, till exempel certifikat, efterlevnad och villkorlig åtkomst, är inte tillgängliga med fullständigt hanterade Android-användarenheter.

## <a name="week-of-january-7-2019"></a>Veckan som börjar med 7 januari 2019

### <a name="app-management"></a>Apphantering

#### <a name="intune-app-pin----2298397---"></a>Intune-appens PIN-kod <!-- 2298397 -->
Som IT-administratör kan du nu konfigurera hur många dagar en användare kan vänta tills Intune-appens PIN-kod måste ändras. Den nya inställningen är *Återställ PIN-kod efter antal dagar* och är tillgänglig i Azure-portalen genom att välja **Intune** > **Klientappar** > **Appskyddsprinciper** > **Skapa princip** > **Inställningar** > **Åtkomstbehörigheter**. Den här funktionen, som är tillgänglig för [iOS](app-protection-policy-settings-ios.md)- och [Android](app-protection-policy-settings-android.md)-enheter, stöder ett positivt heltalsvärde.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune-enhetens rapportfält <!-- 2748738 -->
Intune ger ytterligare fält för enhetsrapportering inklusive appregistrerings-ID, Android-tillverkare, modell och version av säkerhetsuppdatering samt iOS-modell. I Intune är dessa fält tillgängliga genom att välja **Klientappar** > **Appskyddsstatus** och sedan välja **Appskyddsrapport: iOS, Android**. Dessutom kan du via dessa parametrar konfigurera listan **Tillåt** för enhetens tillverkare (Android), listan **Tillåt** för enhetsmodell (Android och iOS) och lägsta inställning för version av Android-säkerhetsuppdatering. 


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>Administrativa mallar finns i offentlig förhandsversion och flyttas till deras egna konfigurationsprofil <!-- 3322847 -->

Administrativa mallar i Intune (**Enhetskonfiguration** > **Administrationsmallar**) är för tillfället i privat förhandsvisning. I denna uppdatering:

- De administrativa mallarna innehåller ungefär 300 inställningar som kan hanteras i Intune. De här inställningarna fanns tidigare endast i redigeraren.
- Administrativa mallar finns i offentlig förhandsversion.
- Administrativa mallar flyttar från **Enhetskonfiguration** > **Administrativa mallar** till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10 och senare** > i **Profiltyp**, välj **Administrativa mallar**.
- Rapportering är aktiverad

Mer information om den här funktionen finns i [Windows 10-mallar för att konfigurera grupprincipinställningar](administrative-templates-windows.md).

Gäller för: Windows 10 och senare

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Använda S/MIME för att kryptera och signera flera enheter för en användare <!-- 1333642 -->
Den här uppdateringen innehåller S/MIME-e-postkryptering som använder en ny importerad certifikatprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj plattformen > profiltypen **PKCS-importerat certifikat**). Du kan importera certifikat i PFX-format i Intune. Intune kan sedan leverera samma certifikat till flera enheter som registrerats av en enda användare. Detta omfattar även följande:
- Den interna e-postprofilen för iOS har stöd för att aktivera S/MIME-kryptering med importerade certifikat i PFX-format.
- Den interna e-postappen på Windows Phone 10-enheter använder S/MIME-certifikatet automatiskt.
- Det privata certifikatet kan levereras över flera plattformar. Men alla e-postappar har inte stöd för S/MIME.
- På andra plattformar kan du behöva konfigurera e-postappen manuellt för att aktivera S/MIME.  
- E-postappar som har stöd för S/MIME-kryptering kan hantera hämtning av certifikat för S/MIME-kryptering av e-post på ett sätt som MDM inte stöder, till exempel genom att läsa från utgivarens certifikatarkiv.
Mer information om den här funktionen finns i [S/MIME-översikt för att signera och kryptera e-post](certificates-s-mime-encryption-sign.md).
Stöds på: Windows, Windows Phone 10, macOS, iOS och Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nya alternativ för att automatiskt ansluta och bevara regler när du använder DNS-inställningarna på Windows 10 och senare enheter <!-- 1333665, 2999078 -->
I Windows 10 och senare enheter kan du skapa en VPN-profil som innehåller en lista över DNS-servrar för att lösa domäner, som till exempel contoso.com. Den här uppdateringen omfattar nya inställningar för namnmatchning (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **Windows 10 och senare** för plattform > välj **VPN** för Profiltyp > **DNS-inställningarna** >**Lägg till**): 
- **Anslut automatiskt**: När den är **Aktiverad**, ansluter enheten automatiskt till VPN-anslutningen när en enhet kontaktar en domän som du anger, t.ex contoso.com.
- **Beständig**: Som standard är alla NRPT-regler (principtabell för namnmatchning) aktiva så länge enheten är ansluten med hjälp av den här VPN-profilen. När inställningen är **Aktiverad** för en NRPT-regel förblir regeln aktiv på enheten, även om VPN-anslutningen kopplas bort. Regeln gäller tills VPN-profilen tas bort eller tills regeln tas bort manuellt, vilket kan göras med hjälp av PowerShell.
[Windows 10 VPN-inställningar](vpn-settings-windows-10.md) beskriver inställningarna. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Använd identifiering av betrott nätverk för VPN-profiler på Windows 10-enheter <!-- 1500165 -->
När du använder identifiering av betrott nätverk kan du förhindra VPN-profiler från att automatiskt skapa en VPN-anslutning när användaren redan är i ett betrott nätverk. Med den här uppdateringen kan du lägga till DNS-suffix om du vill aktivera identifiering av betrott nätverk på enheter som kör Windows 10 och senare (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **VPN** för profiltyp).
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md) visar en lista över aktuella VPN-inställningar.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Hantera Windows Holographic for Business-enheter som används av flera användare <!-- 1907917, 1063203 -->
För närvarande kan du konfigurera delade datorinställningar på Windows 10- och Windows Holographic for Business-enheter med en anpassad OMA-URI-inställning. Med den här uppdateringen läggs en ny profil till för att konfigurera delade enhetsinställningar (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Delad enhet för flera användare**).
Mer information om den här funktionen finns i [Intune-inställningar för att hantera delade enheter](shared-user-device-settings.md).
Gäller för: Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nya Windows 10 Update-inställningar <!--2626030  2512994  -->
För dina [Windows 10-uppdateringsringar](windows-update-for-business-configure.md) kan du konfigurera:
- **Funktionssätt för automatisk uppdatering** – Använd ett nytt alternativ, *Återställ till standard*, för att återställa de ursprungliga inställningarna för automatisk uppdatering på Windows 10-datorer som kör *uppdateringen från oktober 2018*
- **Blockera användaren från att pausa Windows-uppdateringar** – Konfigurera en ny programuppdateringsinställning som gör att du kan blockera eller tillåta användarna att pausa uppdateringsinstallationen från *Inställningar* på deras datorer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS e-postprofiler kan använda S/MIME-signering och kryptering <!-- 2662949 -->
Du kan skapa en e-postprofil som innehåller olika inställningar. Den här uppdateringen inkluderar S/MIME-inställningar som kan användas för signering och kryptering av e-postmeddelanden på iOS-enheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > **E-post** för profiltyp).
[iOS e-postkonfigurationsinställningar](email-settings-ios.md) visar en lista över inställningarna.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Vissa inställningar för BitLocker har stöd för Windows 10 Pro-versionen <!-- 2727036 -->
Du kan skapa en konfigurationsprofil som anger inställningar för slutpunktsskydd för Windows 10-enheter, inklusive BitLocker. Den här uppdateringen lägger till stöd för Windows 10 Professional-versionen för vissa BitLocker-inställningar. De här skyddsinställningarna finns i [Inställningar för slutpunktsskydd för Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>Konfiguration av delad enhet har bytt namn till Meddelande på låsskärm för iOS-enheter i Azure-portalen<!-- 2809362 -->
När du skapar en profil för iOS-enheter kan du lägga till inställningar för **Konfiguration för delad enhet** för att visa specifik text på låsskärmen. Den här uppdateringen innehåller följande ändringar: 
- Inställningarna **Konfiguration för delad enhet** i Azure-portalen har bytt namn till ”Meddelande på låsskärmen (endast övervakat)” (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > välj **iOS** för plattform > välj **Enhetsfunktioner** för Profiltyp > **Meddelande på låsskärmen**).
- När du lägger till meddelanden på låsskärmen kan du infoga ett serienummer, ett enhetsnamn eller ett annat enhetsspecifikt värde som en variabel i **Resurstagginformation** och **Fotnot på låsskärmen**. Du kan till exempel ange `Device name: {{devicename}}` eller `Serial number is {{serialnumber}}` med hjälp av klammerparenteser. [iOS-token](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) visar en lista över de tillgängliga token som kan användas.
[Inställningar för att visa meddelanden på låsskärmen](shared-device-settings-ios.md) visar en lista över inställningarna.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nya inställningar för enhetsbegränsning av App Store, dokumentvisning, spel har lagts till i iOS-enheter <!-- 2827760-->
I **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **Enhetsbegränsningar** för profiltyp > **App Store, dokumentvisning, spel** läggs följande inställningar till: Tillåt hanterade appar att skriva kontakter till ohanterade kontaktkonton Tillåt ohanterade appar att läsa från hanterade kontaktkonton Om du vill se de här inställningarna går du till [iOS-enhetsbegränsningar](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Inställningar för nytt meddelande, tips och keyguard för enhetsägare av Android Enterprise-enheter <!-- 3201839 3201843 -->
Den här uppdateringen innehåller flera nya funktioner på Android Enterprise-enheter vid körning som enhetsägare. Om du vill använda dessa funktioner, gå till **Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Android Enterprise** > i **Profiltyp**, välj **Endast enhetens ägare** > **Enhetsbegränsningar**.
Nya funktioner som ingår: 
- Inaktivera systemmeddelanden till att inte visas, inklusive inkommande anrop, systemaviseringar, systemfel och mer
- Föreslår hoppa över start av självstudier och tips för appar som öppnas för första gången
- Inaktivera avancerade keyguard-inställningar, till exempel kamera, meddelanden, upplåsning med fingeravtryck med mera. Om du vill se inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Enhetsägda Android Enterprise-enheter kan använda Always On VPN-anslutningar <!-- 3202194 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android Enterprise-enheter. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Enhetsbegränsningar** för enhetsägare endast > **Anslutningar**. Om du vill visa inställningarna går du till avsnittet om [begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Ny inställning för slutprocesser i Aktivitetshanteraren på Windows 10-enheter <!-- 3285177 --> 
Den här uppdateringen innehåller en ny inställning för att avsluta processer med hjälp av Aktivitetshanteraren på Windows 10-enheter. Med hjälp av en profil för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > i **Plattform**, välj **Windows 10** > i **Profiltyp**, välj **Enhetsbegränsningar** > **Allmänna** inställningar), väljer du att tillåta eller förhindra den här inställningen.
Om du vill visa de här inställningarna går du till [Inställningar av begränsningar för Windows 10-enheter](device-restrictions-windows-10.md).
Gäller för: Windows 10 och senare


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Mer detaljerade felmeddelanden för registreringsbegränsning <!-- 3111564 -->
Mer detaljerade felmeddelanden är tillgängliga när registreringsbegränsningar inte har uppfyllts. Om du vill se dessa meddelanden går du till **Intune** > **Felsök** > och markerar tabellen Registreringsfel. Mer information finns i [listan över registreringsfel](help-desk-operators.md#configuration-policies-reference).



### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="tenant-status-dashboard-----1124854---"></a>Instrumentpanelen Klientorganisationsstatus <!-- 1124854 -->
Den nya [sidan Klientorganisationsstatus](tenant-status.md) utgör en enskild plats där du kan visa status och relaterad information för din klient.  Instrumentpanelen är uppdelad i fyra områden:
- **Information om klientorganisation** – Visar information som innefattar klientens namn och plats, MDM-utfärdare, totalt antal registrerade enheter i klientorganisationen och antal licenser. I det här avsnittet visas även den aktuella versionen av tjänsten för din klientorganisation.
- **Status för anslutningsprogrammet** – Visar information om tillgängliga anslutningsprogram du har konfigurerat och kan även visa dem som du inte har aktiverat ännu.  
   Baserat på det aktuella tillståndet för varje anslutningsprogram är de flaggade med Felfri, Varning eller Ej felfri. Välj ett anslutningsprogram för att visa detaljer och visa information eller konfigurera ytterligare information för det.
-  **Hälsotillstånd för Intune-tjänsten** – Visar information om aktiva incidenter eller avbrott i klientorganisationen. Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.
-  **Nytt i Intune** – Visar aktiva meddelanden för klientorganisationen. Meddelanden omfattar till exempel aviseringar när klientorganisationen får de senaste funktionerna för Intune.  Informationen i det här avsnittet hämtas direkt från meddelandecentret för Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Ny hjälp- och supportupplevelse i Företagsportal för Windows 10 <!-- 1488939-->
Den nya sidan Hjälp och support i Företagsportal hjälper användare att felsöka och be om hjälp med problem med appen och åtkomst. Från den nya sidan kan de skicka fel- och diagnostiklogginformation via e-post och hitta information om organisationens supportavdelning. De hittar också avsnittet Vanliga frågor och svar med länkar till relevant Intune-dokumentation. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Ny hjälp- och supportupplevelse för Intune   <!-- #3307080 -->
Vi lanserar den nya hjälp- och supportupplevelsen för alla klientorganisationer under de närmaste dagarna. Den här nya upplevelsen är tillgänglig för Intune och kan nås när du använder Intune-bladen på [Azure-portalen](https://portal.azure.com/).
Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor. Utöver problemspecifika rekommendationer använder du det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon. Den här nya upplevelsen ersätter den tidigare hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support. Mer information finns i [Ta reda på hur du kan få support för Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-apps----1081941---"></a>Omfattningstaggar för appar <!-- 1081941 -->
Du kan skapa omfångstaggar som begränsar åtkomsten för roller och appar. Du kan lägga till en omfångstagg för en app så att endast personer med roller som också tilldelats den omfångstaggen har åtkomst till appen. Appar som har köpts med hjälp av Apples volymköpsprogram kan inte tilldelas omfångstaggar.  Mer information finns i [Använda omfångstaggar för att filtrera principer](scope-tags.md).



## <a name="week-of-december-10-2018"></a>Veckan som börjar med 10 december 2018

### <a name="app-management"></a>Apphantering

#### <a name="updates-for-application-transport-security----748318---"></a>Uppdateringar för Application Transport Security <!-- 748318 -->

Microsoft Intune har stöd för TLS 1.2+ (Transport Layer Security) i syfte att tillhandahålla förstklassig kryptering, göra Intune säkrare som standard och anpassa programmet till andra Microsoft-tjänster som t.ex. Microsoft Office 365. För att uppfylla detta krav framtvingar iOS- och macOS-företagsportalerna Apples uppdaterade ATS-krav (Application Transport Security), som även kräver TLS 1.2 +. ATS används för att upprätthålla strängare säkerhet på all kommunikation med appar via HTTPS. Den här ändringen påverkar Intune-kunder som använder iOS- och macOS-appar i företagsportalen. Mer information finns i [Intunes supportblogg](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK stöder 256-bitars krypteringsnycklar <!-- 1832174 -->
Intune App SDK för Android använder nu 256-bitars krypteringsnycklar när kryptering har aktiverats av appskyddsprinciperna. SDK fortsätter att stödja 128-bitars nycklar för kompatibilitet med innehåll och appar som använder äldre versioner av SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsofts version 4.5.0 för automatisk uppdatering krävs för macOS-enheter <!-- 3503442 -->
Om du vill fortsätta att få uppdateringar av företagsportalen och andra Office-program, måste de macOS-enheter som hanteras av Intune uppgraderas till Microsofts version 4.5.0 för automatisk uppdatering. Användarna kanske redan har den här versionen för sina Office-appar.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune kräver macOS 10.12 eller senare <!-- 2827778 -->
Intune kräver nu macOS version 10.12 eller senare. Enheter med tidigare macOS-versioner kan inte använda företagsportalen när de registrerar sig i Intune. För att fortsätta att få support och nya funktioner måste användarna uppgradera sina enheter till macOS 10.12 eller senare, samt uppgradera företagsportalen till den senaste versionen.

## <a name="week-of-november-26-2018"></a>Veckan som börjar den 26 november 2018

### <a name="app-management"></a>Apphantering

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Avinstallera appar på företagsägda övervakade iOS-enheter <!-- 1281677 -->

Du kan ta bort alla appar på företagsägda övervakade iOS-enheter. Du kan ta bort en app genom att rikta antingen användar- eller enhetsgrupper med tilldelningstypen **avinstallera**. För personliga eller ej kontrollerade iOS-enheter kommer du fortsätta kunna ta bort appar som har installerats med hjälp av Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Hämta innehåll för Intune Win32-app <!-- 2617320 -->
Windows 10 RS3-klienter och högre hämtar Intune Win32-appinnehåll med en komponent för leveransoptimering på Windows 10-klienten. Leveransoptimering ger Peer-to-Peer-funktioner som är aktiverat som standard. Leveransoptimering kan konfigureras av en grupprincip och i framtiden via Intune MDM. Mer information finns i [Leveransoptimering för Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Slutanvändarenhet och appinnehållsmenyn <!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Ange en anpassad bakgrund den hanterade hemskärmsappen  <!-- 3041945 -->
Vi ska lägga till en inställning som låter dig anpassa bakgrundsutseendet på den hanterade hemskärmsappen på Android Enterprise, flera appar, enheter i helskärmsläge.  För att konfigurera **Anpassad URL-bakgrund** går du till Intune i Azure portal > Enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Spara och tillämpa tilldelning av appskyddsprincip <!-- 3104570 -->
Du har nu bättre kontroll över dina [Tilldelningar av appskyddsprinciper](app-protection-policies.md#deploy-a-policy-to-users). När du väljer *Tilldelningar* för att ange eller redigera en princips tilldelningar måste du **Spara** konfigurationen för att ändringen ska tillämpas. Använd **Ignorera** för att rensa alla ändringar du gör utan att spara dessa till listorna inkludera eller exkludera.  Genom att kräva Spara eller Ignorera tilldelas endast de användare som du avser en appskyddsprincip.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nya Microsoft Edge-webbläsarinställningar för Windows 10 och senare <!-- 3174639 -->
Den här uppdateringen innefattar en ny inställning för att styra och hantera Microsoft Edge-webbläsaren på dina enheter. En lista över dessa inställningar finns i [Enhetsbegränsning för Windows 10 (och senare)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Nya appstöd med appskyddsprinciper <!-- 3330037 -->
Du kan nu hantera följande appar med [Intune principer för appskydd](app-protection-policies.md):
- Stream (iOS)
- Att göra (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Använd appskyddsprinciper för att skydda företagsdata och kontrollera dataöverföring för dessa appar, så som andra principhanterade Intune-appar. Obs! Om Flow ännu inte syns i konsolen kan du lägga till det när du skapar eller redigerar principerna för appskydd. Du gör detta genom att använda alternativet **+ fler appar** och sedan ange *app-ID* för Flow i indatafältet. Använd *com.microsoft.flow* för Android och *com.microsoft.procsimo* för iOS.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Versionsnummer och build-nummer för iOS och macOS visas <!-- 1892471 -->
I **Enhetsefterlevnad** > **Enhetsefterlevnad** visas operativsystemsversionerna iOS och macOS. De är tillgängliga för användning i efterlevnadsprinciper. Uppdateringen innefattar versionsnumret vilket kan konfigureras för båda plattformarna.
När säkerhetsuppdateringar lanseras låter Apple vanligtvis versionsnumret vara som det är men uppdaterar byggenumret. Genom att använda byggenumret i en efterlevnadsprincip kan du enkelt kontrollera om en säkerhetsriskuppdatering har installerats.
Se efterlevnadsprinciper för [iOS](compliance-policy-create-ios.md#device-health) och [macOS](compliance-policy-create-mac-os.md#device-properties) om du vill använda funktionen.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Uppdateringsringar ersätts med leveransoptimeringsinställningar för Windows 10 och senare <!-- 2753807 -->
Leveransoptimering är en ny konfigurationsprofil för Windows 10 och senare. Funktionen ger en smidigare upplevelse för att leverera programuppdateringar till enheter i din organisation. Uppdateringen hjälper dig även att leverera inställningarna till nya och befintliga uppdateringsringar med en konfigurationsprofil.
Se [leveransoptimeringsinställningar för Windows 10 (och senare)](delivery-optimization-windows.md) för att konfigurera en konfigurationsprofil för leveransoptimering.

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nya inställningar för enhetsbegränsning har lagts till i iOS- och macOS-enheter <!-- 2827760 -->
Den här uppdateringen innehåller nya inställningar för iOS- och macOS-enheter med iOS 12:

**Inställningar för iOS**: 
- Allmänt: Blockera borttagning av appar (endast övervakat)
- Allmänt: Blockera USB-begränsat läge (endast övervakat)
- Allmänt: Framtvinga automatiskt datum och tid (endast övervakat)
- Lösenord: Blockera automatisk ifyllning av lösenord (endast övervakat)
- Lösenord: Blockera förfrågningar om lösenordsnärhet (endast övervakat)
- Lösenord: Blockera lösenordsdelning (endast övervakat)

**Inställningar för macOS**: 
- Lösenord: Blockera automatisk ifyllning av lösenord
- Lösenord: Blockera förfrågningar om lösenordsnärhet
- Lösenord: Blockera lösenordsdelning

Mer information om dessa inställningar finns i inställningarna för enhetsbegränsning i [iOS](device-restrictions-ios.md) och [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Välj appar som spårats på sidan för registreringsstatus<!-- 2531007 -->
Du kan välja vilka appar som spåras på sidan för registreringsstatus. Användaren kan inte använda enheten förrän dessa appar har installerats. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Sök efter Autopilot-enheter med serienummer <!--2595788 -->
Du kan nu söka efter Autopilot-enheter med serienummer. Om du vill göra det väljer du **Enhetsregistrering** > **Windows-registrering** > **Enheter** > ange ett serienummer i rutan **Sök efter serienummer** > tryck på Retur.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Spåra installation av Office ProPlus <!--2620217 -->
Användare kan följa installationsförloppet för [Office ProPlus](apps-add-office365.md) med hjälp av sidan [Registreringsstatus](windows-enrollment-status.md). Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Aviseringar om utgående VPP-token eller om att kvarvarande licenser för företagsportalen håller på att ta slut <!-- 2237572 -->
Om du använder Volume Purchase Program (VPP) för att företablera företagsportalen vid DEP-registrering visas en varning i Intune när en VPP-token håller på att upphöra och när licenserna för företagsportalen nästan är slut.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>macOS DEP-stöd för Apple School Manager-konton <!--3006133 -->
Intune stöder nu användning av programmet för enhetsregistrering (DEP) på macOS-enheter för Apple School Manager-konton.  Mer information finns i [Registrera macOS-enheter automatiskt med Apple School Manager eller programmet för enhetsregistrering](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Ny SKU för Intune-enhetsprenumeration <!--3312071-->
För att sänka kostnaderna för hantering av enheter i företag finns det nu en ny enhetsbaserad prenumerations-SKU. Den här SKU:n för Intune-enheter licensieras per enhet och månad. Priset varierar beroende på licensprogrammet. Den är tillgänglig direkt via administrationsportalen för Office och via [Enterprise-avtal](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA), [Microsoft Products and Services Agreement](https://www.microsoft.com/licensing/mpsa/default) (MPSA) [Microsofts öppna avtal ](https://partner.microsoft.com/licensing/licensing-agreements) och [Molnlösningsleverantör](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453).

### <a name="device-management"></a>Enhetshantering

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Pausa tillfälligt helskärmsläge på Android-enheter för att göra ändringar <!-- 3041935 -->
När du använder Android-enheter i helskärmsläge för flera appar, kan en IT-administratör behöva göra ändringar i enheten. Den här uppdateringen innefattar nya inställningar för helskärmsläge för flera appar så att IT-administratörer tillfälligt kan pausa helskärmsläget med hjälp av en PIN-kod och få åtkomst till hela enheten.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Aktivera den virtuella hemknappen på Android-företagsenheter i helskärmsläge  <!-- 3042021 -->
En ny inställning låter användare trycka på en programstyrd knapp på sin enhet för att växla mellan den hanterade hemskärmsappen och andra tilldelade appar på sin enhet för helskärmsläget för flera appar. Den här inställningen är särskilt användbart i scenarier där en användares app för helskärmsläge inte svarar på rätt sätt på knappen ”Bakåt”. Du kommer att kunna konfigurera den här inställningen för företagsägda Android-enheter för enskild användning. För att aktivera eller inaktivera den **virtuella hemknappen**, går du till Intune i Azure Portal > enhetskonfiguration. Välj en aktuell enhetskonfigurationsprofil eller skapa en ny om du vill redigera dess inställningar för helskärmsläge.
Mer information om inställningar för helskärmsläge finns i avsnittet om [Begränsningsinställningar för Android Enterprise-enheter](device-restrictions-android-for-work.md).

## <a name="week-of-november-12-2018"></a>Veckan som börjar den 12 november 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Stöd för Network Access Control (NAC) för Citrix SSO för iOS <!-- 3259404 -->

Citrix släppte en uppdatering av Citrix Gateway som tillåter Network Access Control (NAC) för Citrix SSO för iOS i Intune. Du kan välja att inkludera ett enhets-ID i en VPN-profil i Intune och sedan skicka den här profilen till dina iOS-enheter. Du måste installera den senaste uppdateringen av Citrix Gateway för att kunna använda den här funktionen.

[Konfigurera VPN-inställningar på iOS-enheter](vpn-settings-ios.md#base-vpn-settings) innehåller mer information om hur du använder NAC, samt information om vissa ytterligare krav. 

## <a name="week-of-november-5-2018"></a>Veckan som börjar med 5 november 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Stöd för iOS 12 OAuth i iOS-e-postprofiler <!--2155106 -->

Intunes iOS-e-postprofiler stöder iOS 12 Open Authorization (OAuth). Om du vill se den här funktionen skapar du en ny profil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS** för plattform > **E-post** för profiltyp) eller uppdaterar en befintlig iOS-e-postprofil. Om du aktiverar OAuth i en profil som redan har distribuerats till användare uppmanas användarna att autentisera på nytt och ladda ned sin e-post igen.

[iOS-e-postprofiler](email-settings-ios.md) innehåller mer information om hur du använder OAuth i en e-postprofil.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Autopilot-stöd för Azure Active Directory-anslutna hybridenheter (förhandsgranskning) <!-- 1048100-->
Du kan nu konfigurera Azure Active Directory-anslutna hybridenheter med hjälp av Autopilot. Enheterna måste vara anslutna till organisationens nätverk för att du ska kunna använda Autopilot-hybridfunktionen. Du hittar mer information under [Distribuera Hybrid Azure Active Directory-anslutna enheter med Intune och Autopilot för Windows](windows-autopilot-hybrid.md).
Den här funktionen kommer att lanseras till hela användarbasen under de närmaste dagarna. Därför kanske du inte kan följa stegen förrän funktionen har distribuerats till ditt konto.

## <a name="week-of-october-29-2018"></a>Veckan då den 29 oktober 2018 infaller

### <a name="app-management"></a>Apphantering

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Kräv icke-biometrisk PIN efter en angiven tidsgräns <!-- 1506985 -->
Genom att kräva en icke-biometrisk PIN-kod efter en tidsgräns angiven av en administratör förbättras säkerheten för appar som har aktiverats för hantering av mobilprogram (MAM) genom att användningen av biometrisk identifiering för åtkomst till företagets data begränsas av Intune. Inställningarna påverkar användare som använder sig av Touch ID (iOS), Face ID (iOS), Android Biometric eller någon annan framtida metod för biometrisk autentisering för åtkomst till sina APP/MAM-aktiverade program. De här inställningarna ger Intune-administratörer bättre kontroll över användarnas åtkomst. Du slipper situationer där en enhet med flera fingeravtryck eller andra metoder för biometrisk åtkomst kan avslöja företagets data för fel användare. Öppna **Microsoft Intune** i Azure Portal. Välj **Klientappar** > **Principer för appskydd** > **Lägg till en princip** > **Inställningar**. Leta upp avsnittet **Åtkomst** för specifika inställningar. Läs om åtkomstinställningar i [Inställningar för iOS](app-protection-policy-settings-ios.md#access-requirements) och [Inställningar för Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter <!-- 2244713 -->
Du kan skilja kontroll över inställningar för Intune APP-dataöverföring på MDM-registrerade iOS-enheter från att ange identiteten för den registrerade användaren, även kända som UPN (User Principal Name). Administratörer som inte använder IntuneMAMUPN kommer inte att se någon funktionalitetsförändring. När den här funktionen är tillgänglig, bör administratörer som använder IntuneMAMUPN för att styra beteende för dataöverföring på registrerade enheter granska de nya inställningarna och uppdatera sina APP-inställningar efter behov.

#### <a name="windows-10-win32-apps----2617325---"></a>Win32-appar för Windows 10 <!-- 2617325 -->
Du kan konfigurera Win32-appar som ska installeras i användarkontext för enskilda användare och installera appen för alla användare på enheten.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Win32-appar för Windows och PowerShell-skript <!-- 2617330 -->
Slutanvändare behöver inte längre vara inloggade på enheten för att installera Win32-appar eller köra PowerShell-skript. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Felsöka klientappinstallationen <!-- 1363711 -->
Du kan felsöka installationen av klientappar genom att granska kolumnen **Appinstallation** i fönstret **Felsök**. För att visa fönstret **Felsök** i Intune-portalen väljer du **Felsök** under **Hjälp och support**.

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Stöd för åtkomstkontroll på nätverk på iOS VPN-klienter <!-- 1333693 -->
Med den här uppdateringen finns en ny inställning för att aktivera åtkomstkontroll på nätverk (NAC) när du skapar en VPN-profil för Cisco AnyConnect, F5-åtkomst och Citrix SSO för iOS. Den här inställningen tillåter att NAC-ID för enheten inkluderas i VPN-profilen. För närvarande finns det inte några VPN-klienter eller NAC-partnerlösningar som har stöd för detta nya NAC-ID, men vi håller dig informerad via vårt [supportblogginlägg](ttps://aka.ms/iOS12_and_vpn) när det finns.

Om du vill använda NAC, måste du:
1. Välja att tillåta att Intune inkluderar enhets-ID i VPN-profiler
2. Uppdatera din NAC-providers programvara/inbyggda programvara, enligt anvisningarna direkt från din NAC-provider

Information om den här inställningen i en iOS VPN-profil finns i [Lägga till VPN-inställningar på iOS-enheter i Microsoft Intune](vpn-settings-ios.md). Mer information om åtkomstkontrollen för nätverk finns i [Integrering av åtkomstkontroll för nätverk (NAC) med Intune](network-access-control-integrate.md). 

Gäller för: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Ta bort en e-postprofil från en enhet, även om det bara finns en e-postprofil <!-- 1818139 -->
Tidigare gick det inte att ta bort en e-postprofil från en enhet *om* det var den enda e-postprofilen. Detta beteende ändras i och med den här uppdateringen. Nu kan du ta bort en e-postprofil, även om det är den enda e-postprofilen på enheten. Läs mer i informationen om att [lägga till e-postinställningar för enheter med Intune](email-settings-configure.md).

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell-skript och Azure Active Directory <!-- 2309469 -->
PowerShell-skript i Intune kan riktas till säkerhetsgrupper för AAD-enheter.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Ny standardinställning för ”Krav på lösenordstyp” för Android, Android-företag<!-- 2649963 -->
När du skapar en ny efterlevnadsprincip (**Intune** > **enhetsefterlevnad** > **principer** > **skapa princip** > **Android** eller **Android Enterprise** för Plattform > Systemsäkerhet), ändras standardvärdet för **krav på lösenordstyp**:

Från: Standard för enheten Till: Minst numeriskt

Gäller för: Android, Android Enterprise

Om du vill se de här inställningarna går du till [Android](compliance-policy-create-android.md) och [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Använda en i förväg delad nyckel i en Windows 10 Wi-Fi-profil <!-- 2662938 -->
Med den här uppdateringen kan du använda en i förväg delad nyckel (PSK) med säkerhetsprotokollet WPA/WPA2-Personal för att autentisera en Wi-Fi-konfigurationsprofil för Windows 10. Du kan också ange kostnadskonfigurationen för ett avgiftsbelagt nätverk av enheter i Windows-10 oktober 2018-uppdateringen.

För närvarande måste du importera en Wi-Fi-profil eller skapa en anpassad profil för att använda en i förväg delad nyckel. [Wi-Fi-inställningar för Windows 10](wi-fi-settings-windows.md) visar en lista över de aktuella inställningarna. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Ta bort PKCS- och SCEP-certifikat från dina enheter <!-- 3218390 -->
I vissa scenarier fanns PKCS- och SCEP-certifikaten kvar på enheterna, även om du tog bort en princip från en grupp, om du tog bort en konfiguration eller efterlevnadsdistribution eller om en administratör uppdaterade en befintlig SCEP- eller PKCS-profil. Detta beteende ändras i och med den här uppdateringen. Det finns vissa scenarier då PKCS- och SCEP-certifikat tas bort från enheter och vissa scenarier då certifikaten finns kvar på enheten. Mer information om dessa scenarier finns i [Ta bort SCEP- och PKCS-certifikat i Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Använda Gatekeeper på macOS-enheter för kompatibilitet <!-- 2504381 -->
Den här uppdateringen innehåller macOS Gatekeeper för att utvärdera enheter för kompatibilitet. För att ställa in Gatekeeper-egenskaper, [Lägg till en enhetsefterlevnadsprincip för macOS-enheter](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="enrollment-abandonment-report----1382924---"></a>Rapport över avbrutna registreringar <!-- 1382924 -->
En ny rapport som innehåller information om övergivna registreringar finns tillgänglig under **Enhetsregistrering** > **Övervaka**. Mer information finns i [Företagsportalens lämningsrapport](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Ny funktion för Azure Active Directory-användningsvillkor <!-- 2870393 -->
Azure Active Directory har en funktion för användningsvillkor som du kan använda i stället för de befintliga Intune-villkoren. Funktionen för användningsvillkor i Azure AD ger större flexibilitet över vilka villkor som ska visas och när, bättre lokaliseringsstöd, bättre kontroll över hur villkoren återges och bättre rapportering. Funktionen för användningsvillkor i Azure AD kräver Azure Active Directory Premium P1 som också är en del av programsviten Enterprise Mobility + Security E3. Mer information finns i artikeln [Hantera företagets villkor för användaråtkomst](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Stöd för läget Android-enhetens ägare <!--3188762-->
För registrering av Samsung Knox-registrering, stöder nu Intune registrering av enheter till läget för hantering av Android-enhetens ägare. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](android-samsung-knox-mobile-enroll.md).

### <a name="device-management"></a>Enhetshantering
#### <a name="new-settings-for-software-updates------1907869---"></a>Nya inställningar för programuppdateringar   <!-- 1907869 -->  
- Du kan nu konfigurera att vissa meddelanden aviserar slutanvändarna om de omstarter som krävs för att slutföra installationen av de senaste programuppdateringarna.   
- Du kan nu konfigurera en omstartsvarning vid omstarter som sker utanför arbetstid, vilket har stöd för BYOD-scenarier.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Gruppera Windows Autopilot-registrerade enheter efter korrelator-ID <!-- 2075110 -->
Intune stöder nu gruppering av Windows-enheter med ett korrelator-ID när de har registrerats med hjälp av [Autopilot för befintliga enheter](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) via Configuration Manager. Korrelator-ID:t är en parameter i Autopilot-konfigurationsfilen. Intune matchar automatiskt [Azure AD-enhetsattributet enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) med ”OfflineAutopilotprofile-<correlator ID>”. På så sätt kan godtyckligt dynamiska grupper i Azure AD skapas baserat på korrelator-ID via attributet enrollmentprofileName för Autopilot-offlineregistreringar. Mer information finns i [Windows Autopilot för befintliga enheter](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Appskyddsprinciper i Intune<!-- 2984657 -->
Med Intune-appskyddsprinciper kan du konfigurera olika dataskyddsinställningar för Intune-skyddade appar, till exempel Microsoft Outlook och Microsoft Word. Vi har ändrat utseendet och känslan för de här inställningarna för både [iOS](app-protection-policy-settings-ios.md) och [Android](app-protection-policy-settings-android.md) för att göra det enklare att hitta individuella inställningar. Det finns tre typer av principinställningar:
- **Dataflytt** – Den här gruppen innehåller kontroller för dataförlustskydd (DLP), såsom begränsningar för klipp ut, kopiera och klistra in och spara som. De här inställningarna avgör hur användarna samverkar med data i apparna.
- **Åtkomstbehörigheter** – Den här gruppen innehåller alternativ för PIN-kod per app som avgör hur slutanvändare får åtkomst till apparna i en arbetskontext.  
- **Villkorlig start** – Den här gruppen innehåller inställningar som lägsta OS-inställningar, uppbrytning och identifiera rotade enheter och offlinerespittid.  
  
Funktionerna i inställningarna ändras inte, men det är lättare att hitta dem när du arbetar i principen för redigering av flödet.

### <a name="intune-apps"></a>Intune-appar

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune stöder en maximal paketstorleken 8 GB för LOB-appar <!-- 1727158 -->
Intune ökade den maximala paketstorleken till 8 GB för LOB-appar (Line-of-business). Du hittar mer information i [Lägg till appar i Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Lägga till en anpassad varumärkesbild för företagsportalappen <!-- 1916266 -->
Som Microsoft Intune-administratör kan du ladda upp en anpassad varumärkesbild som visas som bakgrundsbild på användarens profilsida i iOS-företagsportalappen. Mer information om hur du konfigurerar företagsportalappen finns i [Så här konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune bevarar det lokaliserade språket i Office när Office uppdateras på slutanvändarnas datorer <!-- 2971030 -->
När Intune installerar Office på slutanvändarnas datorer får användarna automatiskt samma språkpaket som de hade med tidigare .MSI Office-installationer. Du hittar mer information i [Tilldela Office 365-appar till Windows 10-enheter med Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nya Intune Support-upplevelsen i Microsoft 365-enhetshanteringsportalen <!-- 3076965 -->
Vi lanserar en ny upplevelse för hjälp och support för Intune i [Microsoft 365-enhetshanteringsportalen]( http://devicemanagement.microsoft.com). Med den nya upplevelsen kan du beskriva problemet med egna ord och ta emot felsökningsinsikter och webbaserat åtgärdsinnehåll. De här lösningarna är tillgängliga via en regelbaserad maskininlärningsalgoritm som drivs av användarfrågor.  

Utöver problemspecifika rekommendationer kan du också använda det nya arbetsflödet för att öppna ett supportärende via e-post eller telefon.  

För kunder som är en del av distributionen, ersätter den här nya upplevelsen den aktuella hjälp- och supportupplevelsen av en statisk uppsättning förvalda alternativ som är baserade på området i konsolen du befinner dig i när du öppnar Hjälp och support.  

*Denna nya hjälp- och supportupplevelse distribueras till vissa men inte alla klienter och är tillgänglig i enhetshanteringsportalen. Deltagare i den här nya upplevelsen väljs ut slumpmässigt bland de tillgängliga Intune-klientorganisationerna. Nya klienter läggs till då vi expanderar distributionen.*  

Mer information finns i [Hjälp- och supportupplevelse](get-support.md#help-and-support-experience) i Ta reda på hur du kan få support för Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>PowerShell-modul för Intune – en förhandsversion är tillgänglig <!-- 951068 -->
Nu finns en ny PowerShell-modul, som har stöd för Intune-API:et via Microsoft Graph, tillgänglig som en förhandsversion på [GitHub]( https://aka.ms/intunepowershell). Mer information om hur du använder den här modulen finns i Viktigt-filen på den platsen. 


## <a name="week-of-october-15-2018"></a>Veckan då den 15 oktober 2018 infaller

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Ange PIN-kod när du ändrar fingeravtryck eller ansikts-ID på en iOS-enhet  <!-- 2637704  -->
Nu uppmanas användarna att ange en PIN-kod när de gör biometriska ändringar på sin iOS-enhet. Detta omfattar ändringar i registrerade fingeravtryck eller ansikts-ID. Tidsinställningen för uppmaningen beror på hur konfigurationen av *Kontrollera åtkomstkraven efter (minuter)* löper ut.  När ingen PIN-kod har angetts, uppmanas användaren att skapa en. 
 
Den här funktionen är endast tillgänglig för iOS och kräver medverkan av program som integrerar Intune APP SDK för iOS, version 9.0.1 eller senare. Integrering av SDK krävs så att beteendet kan tillämpas på de berörda programmen. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. Vissa appar som deltar omfattar WXP, Outlook, Managed Browser och Yammer.


## <a name="week-of-october-1-2018"></a>Veckan då den 1 oktober 2018 infaller

### <a name="app-management"></a>Apphantering

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Åtkomst till viktiga profilegenskaper med hjälp av företagsportalappen <!-- 772203 -->
Slutanvändare kan nu komma åt viktiga egenskaper och åtgärder, till exempel lösenordsåterställning, från företagsportalappen. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Du kan blockera tangentbord från tredje part via APP-inställningarna i iOS <!-- 1248481 -->
Intune-administratörer kan blockera användningen av tredjepartstangentbord på iOS-enheter vid åtkomst till organisationens data i skyddade appar. När APP (Application Protection Policy) är inställt på att blockera tredjepartstangentbord visas ett meddelande första gången användaren interagerar med företagsdata och använder ett tredjepartstangentbord. Alla alternativ förutom det interna tangentbordet är blockerade och visas inte för användaren. Enhetsanvändarna ser bara det här meddelandet en gång. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Åtkomst till användarkonto för Intune-appar på hanterade Android- och iOS-enheter <!-- 1248496 -->
Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook iOS och Android – Princip för appkonfiguration <!--1828527 -->
Du kan nu skapa en Outlook-iOS och Android-appkonfigurationsprincip för iOS och Android för lokala användare som använder grundläggande autentisering med ActiveSync-protokollet. Ytterligare konfigurationsinställningar läggs till vartefter de aktiveras för Outlook för iOS och Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Språkpaket för Office 365 Pro Plus <!-- 1833450 -->
Som Intune-administratör kan du distribuera ytterligare språk för Office 365 Pro Plus-appar som hanteras via Intune. I listan med tillgängliga språk står även **typen** av språkpaket med (kärnspråk, delspråk och språkverktyg). Gå till Azure Portal och välj **Microsoft Intune** > **Klientappar** > **Appar** > **Lägg till**. I listan **Apptyp** på bladet **Lägg till app** väljer du **Windows 10** under **Office 365 Suite**. Välj **Språk** på bladet **Inställningar för appsviten**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Filnamnstillägg för verksamhetsspecifika appar (LOB) för Windows <!-- 1884873 -->
Filnamnstillägg för LOB-appar på Windows omfattar nu *.msi*, *.appx*, *.appxbundle*, *.msix* och *.msixbundle*. Du kan lägga till en app i Microsoft Intune genom att välja **Klientappar** > **Appar** > **Lägg till**. Fönstret **Lägg till app** visas och där du kan välja **Apptyp**. För LOB-appar på Windows väljer du **Verksamhetsspecifik app** som apptyp, väljer **Appaketfil** och anger sedan en installationsfil med rätt filnamnstillägg.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribution av Windows 10-appar med Intune <!-- 2309001 -->
Genom att bygga vidare på det befintliga stödet för verksamhetsspecifika appar och appar för Microsoft Store för företag kan administratörer använda Intune för att distribuera de flesta av organisationens befintliga program till slutanvändare på Windows 10-enheter. Administratörer kan lägga till, installera och avinstallera program för Windows 10-användare i flera olika format, till exempel MSI, Setup.exe eller MSP. Intune utvärderar regler för krav innan nedladdningen och installationen, och meddelar slutanvändarna om statusen eller krav på omstart via Åtgärdscenter för Windows 10. Den här funktionen hjälper organisationer som vill flytta den här arbetsbelastningen till Intune och molnet. Den här funktionen är för närvarande tillgänglig som en offentlig förhandsversion. Vi planerar att introducera många nyheter i funktionen under de kommande månaderna. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Slutanvändarenhet och appinnehållsmenyn <!-- 2771453 -->
Slutanvändare kan nu använda snabbmenyn på enheter och appar för att utlösa vanliga åtgärder som att byta namn på en enhet eller kontrollera efterlevnad. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Kortkommandon för Windows-företagsportalen <!-- 2771518 -->
Slutanvändare kan nu utlösa app- och enhetsåtgärder i Windows-företagsportalen med hjälp av kortkommandon (acceleratorer).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Skapa DNS-suffix i VPN-konfigurationsprofiler på enheter som kör Windows 10<!-- 1333668 -->
När du skapar en profil för VPN-enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  plattform: **Windows 10 och senare** > profiltyp: **VPN**), anger du vissa DNS-inställningar. Med den här uppdateringen kan du även ange flera **DNS-suffix** i Intune. När du använder DNS-suffix, kan du söka efter en nätverksresurs med dess korta namn i stället för det fullständiga domännamnet (FQDN). I och med den här uppdateringen kan du ändra ordningen på DNS-suffix i Intune.
[Windows 10-VPN-inställningar](vpn-settings-windows-10.md#dns-settings) visar en lista över aktuella DNS-inställningar.
Gäller för: Windows 10-enheter

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Stöd för ständig VPN för Android-arbetsprofiler <!-- 1333705 -->
I den här uppdateringen kan du använda VPN-anslutningar som alltid är aktiva på Android-företagsenheter med hanterade arbetsprofiler. Ständiga VPN-anslutningar förblir anslutna eller återansluter omedelbart när användaren låser upp sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. Du kan också placera anslutningen i ”låst” läge, vilket blockerar all nätverkstrafik tills VPN-anslutningen aktiveras.
Du kan aktivera VPN-anslutningar som alltid är aktiva i **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android-företag** för plattform > **Enhetsbegränsningar** > **Anslutningar**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Utfärda SCEP-certifikat till användarlösa enheter <!-- 1744554 -->
För närvarande utfärdas certifikat till användare. Med den här uppdateringen kan SCEP-certifikat utfärdas till enheter, inklusive användarlösa enheter som informationsdatorer (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **SCEP-certifikat** för profil). Exempel på andra uppdateringar är:
- Egenskapen **Ämne** i en SCEP-profil är nu en anpassad textruta och kan innehålla nya variabler. 
- Egenskapen **Alternativt namn för certifikatmottagare (SAN)** i en SCEP-profil är nu i tabellformat och kan innehålla nya variabler. I tabellen kan en administratör lägga till ett attribut och fylla i värdet i en anpassad textruta. SAN stöder följande attribut: 
  - DNS
  - E-postadress
  - UPN

  Dessa nya variabler kan läggas till med statisk text i en textruta för anpassat värde. Till exempel DNS-attributet kan läggas till som `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Klammerparenteser { }, semikolon ; och vertikalstreck | fungerar inte i den statiska texten för SAN. Klammerparenteser får endast omfatta en av de nya variablerna för enhetscertifikat för antingen `Subject` eller `Subject alternative name`. 

Nya variabler för enhetscertifikat:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` fungerar endast för Windows-enheter och domänanslutna enheter. 
>  -  När du anger enhetsegenskaper som IMEI, serienummer och fullständigt domännamn i ämnet eller SAN för ett certifikat, tänk på att de här egenskaperna kan förfalskas av en person med åtkomst till enheten. 

[Skapa en SCEP-certifikatprofil](certificates-scep-configure.md#create-a-scep-certificate-profile) visar en lista över aktuella variabler när du skapar en konfigurationsprofil för SCEP. 

Gäller för: Windows 10 och senare samt iOS, stöds för Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Fjärrlåsa enheter som inte är kompatibla <!-- 2064495 -->
När en enhet inte är kompatibel kan du skapa en åtgärd i efterlevnadsprincipen som fjärrlåser enheten. I Intune > **Enhetskompatibilitet** skapar du en ny princip eller väljer en befintlig princip > **Egenskaper**. Välj **Åtgärder vid inkompatibilitet** > **Lägg till** och välj att fjärrlåsa enheten.
Stöds på: 
- Android
- iOS
- macOS
- Windows 10 Mobil 
- Windows Phone 8.1 och senare 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Profilförbättringar för informationsdatorer med Windows 10 och senare i Azure Portal <!-- 2748224 -->
Den här uppdateringen innehåller följande förbättringar i konfigurationsprofilen för Windows 10-informationsenheter (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** för plattform > **Helskärm (förhandsgranskning)** för profiltyp): 
- För närvarande kan du skapa flera informationsdatorprofiler på samma enhet. I och med den här uppdateringen stöder Intune endast en informationsdatorprofil per enhet. Om du fortfarande behöver flera informationsdatorprofiler på en enskild enhet kan du använda en anpassad URI.
- I en profil för **informationsdator med flera appar** kan du välja programikonernas storlek och ordning i **Startmenylayout** i programrutnätet. Om du vill anpassa mera, kan du ladda upp en XML-fil.
- Inställningarna för webbläsare för informationsdator flyttas till inställningarna för **Informationsdator**. För närvarande har inställningarna för **Webbläsare för informationsdator** sin egen kategori i Azure Portal.
Gäller för: Windows 10 och senare




### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Använda Autopilot-profil för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot <!-- 1558983 -->
Du kan använda Autopilot-profiler för registrerade Windows 10-enheter som inte redan har registrerats för Autopilot. I Autopilot-profilen väljer du alternativet **Omvandla alla målenheter till Autopilot** för att automatiskt registrera andra än Autopilot-enheter med Autopilot-distributionstjänsten. Det kan ta upp till 48 timmar för registreringen att bearbetas. Autopilot konfigurerar enheten efter att den har avregistrerats och återställts.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Skapa flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper <!-- 2526564 -->
Nu kan du [skapa](windows-enrollment-status.md) flera profiler för sidan för registreringsstatus och tilldela dem till Azure AD-grupper.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migrering från program för enhetsregistrering till Apple Business Manager i Intune <!--2748613-->
Apple Business Manager (ABM) fungerar i Intune och du kan uppgradera ditt konto från program för enhetsregistrering (DEP) till ABM. Processen i Intune är samma. Om du vill uppgradera ditt Apple-konto från DEP till ABM, gå till [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Statusflikar för avisering och registrering på översiktssidan för enhetsregistrering <!--2748656-->
Aviseringar och registreringsfel visas nu på separata flikar på översiktssidan för enhetsregistrering.

### <a name="device-management"></a>Enhetshantering

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Begränsa appar och blockera åtkomsten till företagsresurser på Android-enheter <!-- 2451462  -->  
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **Android**  >  **Systemsäkerhet** finns det en ny inställning under avsnittet *Enhetssäkerhet* med namnet **Begränsade appar**. Inställningen **Begränsade appar** använder en efterlevnadsprincip för att blockera åtkomsten till företagsresurser om vissa appar installeras på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: 
- Android




## <a name="week-of-september-24-2018"></a>Veckan då den 24 september 2018 infaller

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Administrationscenter för Microsoft 365-enhetshantering <!-- 3078424 -->
En av löftena för Microsoft 365 är förenklad administration och under åren har vi integrerat Microsoft 365-tjänsterna i serverdelen för att leverera scenarier från början till slut, till exempel Intune och Azure AD villkorsstyrd åtkomst. Den nya [Administrationscentret för Microsoft 365](http://devicemanagement.microsoft.com) låter dig konsolidera, förenkla och integrera administratörsupplevelsen. Specialist-arbetsytan för enhetshantering ger enkel åtkomst till all den enhets- och apphanteringsinformation och uppgifter som din organisation behöver. Vi förväntar oss att det här blir den primära molnarbetsytan för enterprise-slutanvändares databehandlingsteam.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Stöd för fler tredjeparts certifikatutfärdare (CA) <!-- 3093107 -->
Genom att använda Simple Certificate Enrollment Protocol (SCEP) så kan du nu utfärda nya certifikat och förnya certifikat på mobila enheter med Windows, iOS, Android och macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune går över till stöd för iOS 10 och senare <!-- 2454656 -->  
Nu stöder Intune-registrering, företagsportalen och den hanterade webbläsaren endast iOS-enheter som kör iOS 10 och senare. Om du vill söka efter enheter eller användare som påverkas i din organisation går du till Intune på Azure-portalen > **Enheter** > **Alla enheter**. Filtrera efter operativsystem och klicka sedan på **Kolumner** för att visa information om operativsystemversionen. Be användarna att uppgradera sina enheter till en operativsystemversion som stöds.  

Om du har någon av enheterna som anges nedan, eller om du vill registrera någon av enheterna som anges nedan, bör du vara medveten om att de endast stöder iOS 9 och tidigare.  För att även fortsättningsvis ha åtkomst till Intune-företagsportalen måste du uppgradera dessa enheter till enheter som stöder iOS 10 eller senare:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (tredje generationen) 
* iPad Mini (första generationen)  

## <a name="week-of-september-17-2018"></a>Veckan då den 17 september 2018 infaller

### <a name="app-management"></a>Apphantering

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Ta bort duplicering av statuspaneler för appskydd <!-- 3083391 -->
Panelerna **användarstatus för iOS** och **användarstatus för Android** fanns både på sidan **Klientappar – översikt** samt sidan **Klientappar – Appskyddsstatus**. Statuspanelerna har tagits bort från sidan **Klientappar – översikt** för att undvika duplicering. 

## <a name="week-of-august-27-2018"></a>Veckan 27 augusti 2018

### <a name="app-management"></a>Apphantering

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Stöd för pakettunnel för per app-VPN-profiler i iOS för anpassade anslutningstyper och Pulse Secure-anslutningstyper <!-- 1520957 -->
När du använder per app-VPN-profiler i iOS kan du välja att använda händelsedirigering nedåt på appnivå (app-proxy) eller på paketnivå (paket-tunnel). Dessa alternativ är tillgängliga med följande anslutningstyper:
- Anpassat VPN
- Pulse Secure om du inte är säker på vilket värde du ska använda läser du VPN-leverantörens dokumentation.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Fördröjning när iOS-programuppdateringar visas på enheten <!-- 1949583 -->
I Intune > **Programuppdateringar** > **Uppdateringsprinciper för iOS** kan du konfigurera dagar och tider då du inte vill att enheter installerar uppdateringar. I en kommande uppdatering kommer du kunna fördröja tidpunkten då en programuppdatering visas på enheten från 1–90 dagar. 
[Konfigurera uppdateringsprinciper för iOS i Microsoft Intune](software-updates-ios.md) visar en lista över aktuella inställningar.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus version <!-- 2213968 -->
När du tilldelar Office 365 ProPlus-appar till Windows 10-enheter med Intune kommer du att kunna välja version av Office. I Azure-portalen väljer du **Microsoft Intune** > **Appar** > **Lägg till app**. Välj sedan **Office 365 ProPlus-paket (Windows 10)** från listrutan **Typ**. Välj **Inställningar för appsvit** för att visa det associerade bladet. Ange **Uppdateringskanalen** till ett värde såsom **Varje månad**. Du kan även ta bort andra versioner av Office (msi) från slutanvändarenheter genom att välja **Ja**. Välj **Specifik** för att installera en specifik version av Office för den valda kanalen på slutanvändarenheter. Nu kan du välja den **specifika version** av Office som ska användas. De versioner som är tillgängliga ändras över tid. När du skapar en ny distribution kan de versioner som är tillgängliga därför vara nyare och inte ha vissa äldre versioner tillgängliga. Befintliga distributioner fortsätter att distribuera den äldre versionen, men versionslistan uppdateras kontinuerligt per kanal. Mer information finns i [Översikt över uppdateringskanaler för Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Stöd för inställningen Registrera DNS för Windows 10-VPN <!-- 2282852 -->
Med den här uppdateringen kan du konfigurera Windows 10-VPN-profiler så att de dynamiskt registrerar de IP-adresser som tilldelas till VPN-gränssnittet med intern DNS, utan behov av anpassade profiler.
Information om de aktuella VPN-profilinställningar som är tillgängliga finns i [Windows 10-VPN-inställningar](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Installationsprogrammet för macOS-företagsportalen innehåller nu versionsnumret i filnamnet för installationsprogrammet <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Automatiska appuppdateringar i iOS <!-- 2729759 -->
Automatiska appuppdateringar fungerar för både enhets- och användarlicensierade appar för iOS version 11.0 och senare.




### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello riktar in sig på användare och enheter <!-- 1106609 -->
När du skapar en [Windows Hello för företag](windows-hello.md)-princip gäller den för alla användare i organisationen (i hela klientorganisationen). Med den här uppdateringen kan principen även tillämpas på specifika användare eller specifika enheter med hjälp av en princip för enhetskonfiguration (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Identity Protection (Identitetsskydd)** > **Windows Hello för företag**).
I Intune i Azure-portalen finns konfiguration och inställningar för Windows Hello nu i både **Enhetsregistrering** och **Enhetskonfiguration**. **Enhetsregistrering** riktar sig till hela organisationen (i hela klientorganisationen) och har stöd för Windows AutoPilot (OOBE). **Enhetskonfiguration** riktar sig mot enheter och användare som använder en princip som tillämpas under incheckning.
Den här funktionen gäller för:  
- Windows 10 och senare
- Windows 10 Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler är en tillgänglig anslutning för VPN-profiler i iOS <!-- 1769858 -->
När du skapar en VPN-profil för enhetskonfiguration i iOS (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS**-plattform > **VPN**-profiltyp) finns det flera anslutningstyper, inklusive Cisco, Citrix och mer. Den här uppdateringen lägger till Zscaler som anslutningstyp. 
[VPN-inställningar för enheter som kör iOS](vpn-settings-ios.md) visar en lista över tillgängliga anslutningstyper.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>FIPS-läge för företagets Wi-Fi-profiler för Windows 10 <!-- 1879077 -->
Du kan nu aktivera FIPS-läge (Federal Information Processing Standards) för företagets Wi-Fi-profiler för Windows 10 i Intune Azure-portalen. Se till att FIPS-läge är aktiverat i Wi-Fi-infrastrukturen om du aktiverar det i Wi-Fi-profilerna.
[Wi-Fi-inställningar för Windows 10 och senare enheter i Intune](wi-fi-settings-windows.md) visar hur du skapar en Wi-Fi-profil.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Kontrollera S-läge på Windows 10-enheter och senare enheter – förhandsversion <!-- 1958649 -->
Med den här funktionsuppdateringen kan du skapa en profil för enhetskonfiguration som växlar en Windows 10-enhet ut ur S-läge, eller förhindra att användare växlar enheten ut ur S-läge. Den här funktionen finns i Intune > **Enhetskonfiguration** > **Profiler** >  **Windows 10 och senare** > **Edition upgrade and mode switch** (Versionsuppgradering och lägesväxling).
[Introduktion till Windows 10 i S-läge](https://www.microsoft.com/windows/s-mode) innehåller mer information om S-läge.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Konfigurationspaketet för Windows Defender ATP läggs automatiskt till i konfigurationsprofilen <!-- 2144658 -->
När du använder enheter med [Advanced Threat Protection och registrering](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) i Intune behövde du tidigare ladda ned ett konfigurationspaket och lägga till det i din konfigurationsprofil. Med den här uppdateringen hämtar Intune paketet automatiskt från Windows Defender Säkerhetscenter och lägger till det i din profil.
Gäller för Windows 10 och senare.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Kräv att användare ansluter under enhetskonfiguration <!--2311457-->
Du kan nu ange enhetsprofiler som kräver att enheten ansluter till ett nätverk innan den går vidare förbi sidan Nätverk under Windows 10-installationen. När den här funktionen är i förhandsversion krävs Windows Insider-version 1809 eller senare för att använda den här inställningen.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Begränsa appar och blockera åtkomst till företagsresurser på iOS- och Android Enterprise-enheter <!-- 2451462 -->
I **Enhetsefterlevnad** > **Principer** > **Skapa princip** > **iOS** > **Systemsäkerhet** finns det en ny inställning för **Begränsade program**. Den här nya inställningen använder en policy för efterlevnad för att blockera åtkomst till företagsresurser om vissa appar är installerade på enheten. Enheten betraktas som icke-kompatibel tills de begränsade apparna tas bort från enheten.
Gäller för: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Uppdateringar med stöd för modernt VPN för iOS <!-- 2459928, 1819876, and 2650856 -->
Den här uppdateringen har stöd för följande VPN-klienter för iOS: 
- F5 Access (version 3.0.1 och senare)
- Citrix SSO
- Palo Alto Networks GlobalProtect version 5.0 och senare även i den här uppdateringen:
- Den befintliga anslutningstypen **F5 Access** byter namn till **F5 Access Legacy** för iOS.
- Den befintliga anslutningstypen **Palo Alto Networks GlobalProtect** byter namn till **Legacy Palo Alto Networks GlobalProtect** för iOS.
Befintliga profiler med de här anslutningstyperna fortsätter att fungera med sina respektive äldre VPN-klienter. Om du använder Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN eller Palo Alto Networks GlobalProtect version 4.1 och tidigare med iOS bör du gå över till de nya apparna. Gör det så snart som möjligt för att säkerställa att VPN-åtkomst är tillgänglig för iOS-enheter när de uppdaterar till iOS 12.
Mer information om iOS 12 och VPN-profiler finns i [Microsoft Intune-supportteamets blogg](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Exportera efterlevnadsprinciper för den klassiska Azure-portalen för att återskapa dessa principer i Intune Azure-portalen <!-- 2469637 -->
Principer för enhetsefterlevnad som skapats i den klassiska Azure-portalen upphör att gälla. Du kan granska och ta bort alla befintliga principer, men du kan inte uppdatera dem. Om du behöver migrera några efterlevnadsprinciper till den befintliga Intune Azure-portalen kan du exportera principerna som en kommaavgränsad fil (*.csv*-fil). Använd sedan informationen i filen för att återskapa dessa principer i Intune Azure-portalen.

> [!IMPORTANT]
> När den klassiska Azure-portalen upphör kommer du inte längre att kunna komma åt eller visa dina efterlevnadsprinciper. Tänk därför på att exportera dina principer och återskapa dem i Azure-portalen innan den klassiska Azure-portalen upphör.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile – ny partner för skydd mot mobilhot <!-- 22662717 -->
Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Better Mobile, en lösning med skydd mot mobilhot som är integrerad i Microsoft Intune.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Lås företagsportalen i enkelt appläge tills användaren loggar in <!--1067692 --> 
Du kan nu välja att köra företagsportalen i enkelt appläge om du autentiserar en användare via företagsportalen i stället för installationsassistenten vid DEP-registrering. Det här alternativet låser enheten omedelbart efter att installationsassistenten är klar så att en användare måste logga in för att komma åt enheten. Den här processen ser till att enheten slutför registrering inte frånkopplas i ett tillstånd utan någon kopplad användare.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Tilldela en användare och ett eget namn till en Autopilot-enhet <!--1346521 -->
Du kan nu [tilldela en användare till en specifik Autopilot-enhet](enrollment-autopilot.md). Administratörer kommer även att kunna ge egna namn som möter användaren vid konfiguration av enheten med Autopilot.
Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Använda VPP enhetslicenser för att företablera företagsportalen vid DEP-registrering <!-- 1608345 -->
Nu kan du använda VPP-enhetslicenser (volyminköpsprogram) till att företablera företagsportalen under registreringar med Programmet för enhetsregistrering (DEP). Detta gör du genom att ange den VPP-token du vill använda för att installera företagsportalen när du [skapar eller redigerar en registreringsprofil](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). Se till att din token inte upphör att gälla och att du har tillräckligt många licenser för företagsportalappen. Om token upphör att gälla eller om licenserna tar slut kan Intune push-överföra företagsportalen från App Store istället (då krävs ett Apple-ID).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Om du vill ta bort en VPP-token som används för företablering av företagsportalen krävs en bekräftelse <!-- 2237634 -->
En bekräftelse krävs nu för att ta bort en token för volymköpsprogram (VPP) om den används för att företablera företagsportalen vid DEP-registrering.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Blockera personliga enhetsregistreringar i Windows <!-- 1849498 -->
Du kan [blockera personliga Windows-enheter](enrollment-restrictions-set.md#set-device-type-restrictions) från att registrera med [hantering av mobilenheter](windows-enroll.md) i Intune. Enheter som registreras med [Intune PC-agenten](manage-windows-pcs-with-microsoft-intune.md) kan inte blockeras med den här funktionen. Den här funktionen tas i bruk inom de närmaste veckorna, så den syns kanske inte direkt i användargränssnittet.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Ange mönster för datornamn i en Autopilot-profil <!--1849855-->
Du kan [ange en mall för datornamn](enrollment-autopilot.md#create-an-autopilot-deployment-profile) för att generera och ange [datornamnet](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) under Autopilot-registreringen. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>För Windows Autopilot-profiler döljer du alternativen för att ändra konto på företagets inloggningssida och sidan för domänfel <!--1901669 -->
Det finns [nya Windows Autopilot-profilalternativ](enrollment-autopilot.md#create-an-autopilot-deployment-profile) som administratörer kan använda för att dölja ändra alternativ för att ändra konto på företagets inloggningssida och sidorna för domänfel. För att dölja de här alternativen krävs att företagsanpassning konfigureras i Azure Active Directory. Gäller för: senaste [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/)-version (medan förhandsversion används).



### <a name="device-management"></a>Enhetshantering

#### <a name="delete-jamf-devices----2653306--"></a>Ta bort Jamf-enheter <!-- 2653306-->
Du kan ta bort JAMF-hanterade enheter genom att gå till **Enheter** > välj Jamf-enheten > **Ta bort**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Ändra terminologin till ”dra tillbaka” och ”rensa” <!-- 2175759 -->
För att överensstämma med Graph API har följande termer för Intune-användargränssnittet och dokumentationen ändrats:
- **Ta bort företagsinformation** ändras till ”Dra tillbaka”
- **Fabriksåterställning** ändras till **Rensa**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Bekräftelsedialogruta om administratören försöker ta bort MDM-pushcertifikat <!-- 297909500-->
Om någon försöker ta bort ett Apple MDM-pushcertifikat visar en bekräftelsedialogruta antalet relaterade iOS- och macOS-enheter. Dessa enheter måste registreras igen om certifikatet tas bort.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Ytterligare säkerhetsinställningar för Windows Installer <!-- 2282430 -->
Du kan tillåta användarna att styra appinstallationer. Om den här inställningen är aktiverad tillåts installationer som i annat fall skulle stoppats på grund av en säkerhetsöverträdelse. Du kan ange att Windows Installer ska använda förhöjd behörighet när program installeras i ett system. Du kan också ange att WIP-objekt (Windows Information Protection) ska indexeras och att deras metadata ska lagras på en okrypterad plats. När principen är inaktiverad indexeras inte Windows informationsskyddade objekt och resultaten visas inte i Cortana eller Utforskaren. Funktionerna för dessa alternativ är inaktiverade som standard. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Ny uppdatering av användarupplevelse för företagsportalens webbsida <!--2000968 -->
Vi har lagt till nya funktioner på företagsportalen baserat på våra kunders synpunkter. Du kommer att se tydliga förbättringar av befintliga funktioner och användbarheten för dina enheter. Delar av webbplatsen, som enhetsinformation, feedback och support samt enhetsöversikten, har fått en ny och modern design. Andra nyheter:

- Effektiva arbetsflöden mellan olika plattformar
- Bättre flöden för identifiering och registrering av enheter
- Fler användbara felmeddelanden
- Mer användarvänligt språk, mindre teknisk jargong
- Möjlighet att dela direktlänkar till appar
- Förbättrad prestanda för stora app-kataloger
- Bättre tillgänglighet för alla användare  

[Dokumentationen till Intune-företagsportalens webbplats](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) har uppdaterats för att återspegla dessa ändringar. Om du vill se ett exempel på appförbättringarna kan du se [Uppdateringar i användargränssnittet för Intunes slutanvändarappar](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Övervaka och felsöka

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Förbättrad upplåsningsidentifiering i efterlevnadsrapportering<!-- 2198738 -->
Inställningsstatus för förbättrad upplåsningsidentifiering visas nu i all efterlevnadsrapportering i administrationskonsolen.

### <a name="role-based-access-control"></a>Rollbaserad åtkomstkontroll

#### <a name="scope-tags-for-policies---1081974---"></a>Omfångstaggar för principer <!--1081974 -->
Du kan [skapa omfångstaggar](scope-tags.md) som begränsar åtkomsten till Intune-resurser. Lägg till en omfångstagg till en rolltilldelning och lägg sedan till omfångstaggen i en konfigurationsprofil. Rollen får endast åtkomst till resurser med konfigurationsprofiler som har matchande omfångstaggar (eller inga omfångstaggar).

## <a name="week-of-august-14-2018"></a>Veckan 14 augusti 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS-stöd för Apples program för enhetsregistrering (Device Enrollment Program) <!-- 747651 -->
Intune har nu stöd för registrering av macOS-enheter i Apples program för enhetsregistrering (DEP). Mer information finns i [Registrera macOS-enheter automatiskt med Apples program för enhetsregistrering](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Veckan som inleds den 23 juli 2018

### <a name="app-management"></a>Apphantering

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1895847 -->
I Microsoft Intune kan verksamhetsspecifika macOS-appar distribueras med inställningen **Obligatorisk** eller **Tillgänglig med registrering**. Slutanvändarna kan hämta appar som har distribuerats som **tillgängliga** via företagsportalen för macOS eller [företagsportalwebbplatsen](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Stöd för inbyggda iOS-appar i helskärmsläge <!-- 2051098 -->
Utöver Store-appar och hanterade appar kan du nu välja en inbyggd App (till exempel Safari) som körs i helskärmsläge på en iOS-enhet.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Redigera dina distributioner av Office 365 Pro Plus-appar <!-- 2150145 -->
Som Microsoft Intune-administratör har du större möjlighet att redigera distributioner av Office 365 Pro Plus-appar. Dessutom behöver du inte längre ta bort dina distributioner för att ändra svitens egenskaper. I Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appar**. Välj Office 365 Pro Plus Suite i listan med appar.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>Uppdaterad Intune App SDK för Android är nu tillgänglig <!-- 2744271-->

En uppdaterad version av Intune App SDK för Android är tillgänglig som stöd för Android P-versionen. Om du är en apputvecklare och använder Intune SDK för Android, måste du installera den uppdaterade versionen av Intune App SDK för att säkerställa att Intune-funktionerna i dina Android-appar fortsätter att fungera som förväntat på Android P-enheter. Den här versionen av Intune App SDK innehåller ett inbyggt plugin-program som utför SDK-uppdateringarna. Du behöver inte skriva om någon befintlig kod som ingår. Mer information finns i [Intune SDK för Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Om du använder den gamla badging-stilen för Intune, rekommenderar vi att du använder portföljikonen. Mer information relaterad till olika varumärken finns i [den här GitHub-lagringsplatsen](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Skapa en princip för enhetskompatibilitet med hjälp av brandväggsinställningar på macOS-enheter <!-- 1497640 -->
När du skapar en ny efterlevnadsprincip i macOS (**Enhetsefterlevnad** > **Principer** > **skapa princip** > **Plattform: macOS** > **Systemsäkerhet**) finns det några nya **brandväggsinställningar** tillgängliga: 

- **Brandvägg**: Konfigurera hur inkommande anslutningar ska hanteras i din miljö.
- **Inkommande anslutningar**: **Blockera** alla inkommande anslutningar, förutom de som behövs för grundläggande Internettjänster som DHCP, Bonjour och IPSec. Den här inställningen blockerar också alla delningstjänster.
- **Dolt läge**: **Aktivera** dolt läge om du vill förhindra att enheten svarar på avsökningsförfrågningar. Enheten fortsätter att besvara inkommande begäranden för godkända appar.

Gäller: macOS 10.12 och senare

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Ny enhetskonfigurationsprofil för Wi-Fi för Windows 10 och senare <!-- 1879077 -->
För närvarande kan du importera och exportera Wi-Fi-profiler med hjälp av XML-filer. Med den här uppdateringen kan du skapa en enhetskonfigurationsprofil för Wi-Fi direkt i Intune, precis som på vissa andra plattformar.

Om du vill skapa profilen öppnar du **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Windows 10 och senare** > **Wi-Fi**. 

Gäller för Windows 10 och senare.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Helskärmsläge – inaktuell är nedtonad och kan inte ändras <!-- 2149998 -->
Funktionen [Helskärmsläge](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10 och senare** > **Enhetsbegränsningar**) är inaktuell och ersätts med [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md). Med den här uppdateringen är funktionen **Helskärmsläge – inaktuell** nedtonad och användargränssnittet kan inte ändras eller uppdateras. 

Om du vill aktivera helskärmsläge kan du läsa mer i [Inställningar för helskärmsläge för Windows 10 och senare](kiosk-settings.md).

Gäller för Windows 10 och senare, Windows 10 Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API:erna använder tredjeparts certifikatutfärdare <!-- 2184013 -->
I den här uppdateringen finns det ett Java-API som gör det möjligt för tredjeparts certifikatutfärdare att integrera med Intune och SCEP. Sedan kan användarna lägga till SCEP-certifikatet till en profil och tillämpa det på enheter med hjälp av MDM.

Intune stöder för närvarande [SCEP-förfrågningar med hjälp av Active Directory Certificate Services](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Växla för att visa eller dölja knappen Avsluta session i en webbläsare i helskärmsläge <!-- 2455253 -->
Du kan nu konfigurera om webbläsare i helskärmsläge ska visa knappen Avsluta session. Du kan se kontrollen under **Enhetskonfiguration** > **Helskärmsläge (förhandsgranskning)** > **Webbläsare i helskärmsläge**. När en användare klickar på knappen när den är aktiverad frågar appen om du verkligen vill avsluta sessionen. När du bekräftar rensar webbläsaren alla webbdata och går tillbaka till den webbadress som är standard.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Skapa en konfigurationsprofil för eSIM-mobilnät <!-- 2564077 -->
I **Enhetskonfiguration** kan du skapa en profil för eSIM-mobilnät. Du kan importera en fil som innehåller aktiveringskoder för mobilnät som tillhandahålls av din mobiloperatör. Du kan sedan distribuera de här profilerna till dina Windows 10-enheter som aktiverat eSIM LTE, till exempel Surface Pro LTE och andra eSIM-kompatibla enheter.

Kontrollera om dina [enheter stöder eSIM-profiler](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Gäller för Windows 10 och senare. 




### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Markera automatiskt Android-enheter som registrerats med hjälp av Samsung Knox Mobile-registrering som ”företagsägda”. <!-- 2404851 -->
Som standard markeras Android-enheter som registrerats med Samsung Knox Mobile-registrering nu som **företagsägda** under **Ägarskap för enhet**. Du behöver inte identifiera företagets enheter manuellt med hjälp av IMEI- eller serienummer innan du registrerar med Samsung Knox Mobile-registrering.

### <a name="device-management"></a>Enhetshantering

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Massborttagning av enheter på enhetsbladet <!-- 1793693 -->

Du kan nu ta bort flera enheter samtidigt på enhetsbladet. Välj **Enheter** > **Alla enheter** > välj de enheter som du vill ta bort > **Ta bort**. En avisering visas för enheter som inte kan tas bort.

## <a name="week-of-july-16-2018"></a>Veckan som inleds den 16 juli 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Fler möjligheter att synkronisera i företagsportalappen för Windows  
Med företagsportalappen för Windows kan du nu initiera en synkronisering direkt från Windows-aktivitetsfältet och Start-menyn. Den här funktionen är särskilt användbart om din enda uppgift är att synkronisera enheter och få åtkomst till företagsresurser. För att komma åt den nya funktionen högerklickar du på ikonen för företagsportalen som har fästs till verktygsfältet eller Start-menyn. I menyalternativen (kallas även en snabblista) väljer du **Sync this device** (Synkronisera den här enheten). Företagsportalen öppnas till sidan **inställningar** och initierar synkroniseringen. En titt på de nya funktionerna finns på sidan om [nyheter i användargränssnittet](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nya bläddringsfunktioner i företagsportalappen för Windows  

När du bläddrar eller söker efter appar i företagsportalappen för Windows kan du nu växla mellan den befintliga vyn **Paneler** och den nyligen tillagda vyn **Information**. Den nya vyn visar information om programmet, som namn, utgivare, publiceringsdatum och installationsstatus.  

På sidan **Appar** kan du använda vyn **Installerade** för att se information om slutförda och pågående appinstallationer. Du kan se hur den nya vyn ser ut på sidan om [nyheter i användargränssnittet](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Förbättrade funktioner i företagsportalappen för enhetsregistreringshanterare  
När en enhetsregistreringshanterare (DEM) loggar in på företagsportalappen för Windows visar appen nu endast DEM:ens aktuella enhet som körs. Den här förbättringen minskar uppnådda tidsgränser som tidigare förekom när appen försökte visa alla DEM-registrerade enheter.  


## <a name="week-of-july-9-2018"></a>Veckan som inleds med den 9 juli 2018

### <a name="app-management"></a>Apphantering

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Blockera åtkomst till appen baserat på icke-godkända enhetsleverantörer och modeller  <!-- 1425689 ! -->
Intune IT-administratören kan tillämpa en angiven lista över Android-tillverkare och/eller iOS-modeller via Intune App Protection-principer. IT-administratören kan ange en semikolonavgränsad lista över tillverkare för Android-principer och enhetsmodeller för iOS-principer. Intune App Protection-principer gäller endast för Android och iOS. Det finns två separata åtgärder som kan utföras på den angivna listan:
- En blockering från åtkomst till appen på enheter som inte har angetts.
- Eller en selektiv rensning av företagets data på enheter som inte har angetts. 

Användaren kommer inte att få åtkomst till det aktuella programmet om principkraven inte uppfylls. Baserat på inställningarna kan användaren bli blockerad eller rensas selektivt på sina företagsdata i appen. På iOS-enheter kräver den här funktionen att program deltar (t.ex. WXP, Outlook, Managed Browser, Yammer) för att integrera Intune APP SDK:n för att funktionen ska framtvingas i berörda program. Den här integreringen händer på löpande bas, och är beroende av specifika programteam. På Android kräver funktionen den senaste företagsportalen. 

På slutanvändarens enheter utför Intune-klienten åtgärder baserat på en enkel matchning av strängar som angetts i Intune-bladet för programskyddsprinciper. Detta beror helt på värdet som enheten rapporterar. IT-administratören rekommenderas därför att säkerställa att det avsedda funktionssättet är korrekt. Detta kan åstadkommas genom att testa den här inställningen baserat på en rad olika enhetstillverkare och modeller som är riktade till en liten användargrupp. I Microsoft Intune väljer du **Klientappar** > **Appskyddsprinciper** för att visa och lägga till appskyddsprinciper. Mer information om att appskyddsprinciper finns i [Vad är appskyddsprinciper](app-protection-policy.md) och [Selektiv rensning av data med åtkomståtgärder för appskyddsprinciper i Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Åtkomst till förhandsversionen av företagsportalen på macOS <!-- 1734766 -->
Du kan registrera dig för att ta emot versioner tidigt genom att gå med i Insider-programmet med hjälp av Microsoft AutoUpdate. När du registrerat dig kan du använda den uppdaterade företagsportalen innan den är tillgänglig för dina slutanvändare. Mer information finns i [Microsoft Intune-bloggen](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Veckan som inleds med den 2 juli 2018

### <a name="app-management"></a>Apphantering

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Övervaka konfigurationsstatus för iOS-appar per enhet <!-- 880037 -->
Som administratör för Microsoft Intune kan du övervaka konfigurationsstatusen för iOS-appar för varje hanterad enhet. Gå till **Microsoft Intune** i Azure Portal och välj **Enheter** > **Alla enheter**. Välj en specifik enhet från listan med hanterade enheter för att visa ett blad för enheten. Välj **Appkonfiguration** på enhetsbladet.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Åtkomståtgärder för appskyddsprinciper <!-- 1483510 -->
Du kan konfigurera appskyddsprinciper för att uttryckligen rensa, blockera eller varna icke-kompatibla enheter. Åtgärden *Rensa* tar bort företagets företagsdata från en enhet. Om en rensning utförs meddelas enhetens användare om både orsaken till rensningen och reparationsstegen. För vissa inställningar som lägsta version av operativsystemet, kommer du att kunna använda flera åtgärder, till exempel blockering och rensa. Observera att de här åtgärderna utlöses när appen startas.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Selektiv rensning av organisations appdata <!-- 1507030 -->
Nu kan administratörer konfigurera en selektiv rensning av organisationens data som en ny åtgärd när villkoren i APP-åtkomstinställningarna inte uppfylls.  Den här funktionen gör att administratörer kan skydda och ta bort känsliga organisationsdata från appar baserat på förkonfigurerade kriterier.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Återkalla en iOS-app som köpts via VPP <!-- 1777384 -->
Som Microsoft Intune-administratör kan du återkalla alla licenser för en iOS-app som köpts via volyminköpsprogrammet (VPP). Du kan meddela användarna när en användarlicensierad app inte längre är tilldelad till dem. Om du återkallar en applicens så avinstalleras inte den relaterade VPP-appen från enheten. Om du vill avinstallera en VPP-app, måste du ändra tilldelningsåtgärden till **avinstallera**. Du kan se antalet återkallade licenser vid noden **Licensierade appar** i arbetsbelastningen **App** i Intune. Mer information om VPP-appar i iOS finns i [Så här hanterar du iOS-appar som köpts genom ett volyminköpsprogram med Microsoft Intune](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Uppdateringar till meddelanden om brist på efterlevnad i företagsportalappen <!-- 1832222 -->
Vi har uppdaterat meddelandena som visas för enhetsanvändarna när en enhet inte är kompatibel. Meddelandena behåller sina ursprungliga betydelser men har uppdaterats med mer användarvänligt språk och mindre teknisk jargong. Vi har även uppdaterat länkar till dokumentation och reparationssteg så att de är uppdaterade.
Följande text är ett exempel på de förbättrade meddelandena som du kommer att se:
- **Före**: *Den här enheten har inte kontaktat Intune-tjänsten inom den tidsperiod som krävs av din IT-administratör. Du kan lösa det här problemet genom att öppna företagsportalappen på enheten och klicka på knappen Kontrollera efterlevnad.*
- **Efter**: *Din enhet har inte checkats in till organisationen på ett tag. Återupprätta anslutningen genom att öppna företagsportalappen på enheten och trycka på Kontrollera inställningar för enheten.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Återkalla VPP-applicenser i iOS <!-- 1863797 -->
Som administratör kan du frigöra en iOS VPP-applicens som har tilldelats en användare eller enhet. När du avinstallerar en VPP-app i iOS kan du också återkalla applicensen. Innan du avinstallerar appen måste användaren eller enheten tas bort från gruppen som är appens mål. Om användaren eller enheten tas bort från gruppen behöver inte appen installeras om. När dessa steg har slutförts kan du välja att tilldela applicensen till en annan användare eller enhet. Mer information om licenser för VPP-appar i iOS finns i [Hantera volyminköpta iOS-appar i Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Välj enhetskategorier med hjälp av inställningarna för åtkomst till arbete eller skola <!-- 1058963 eenotready --> 
Om du har aktiverat [mappning av enhetsgrupp](https://docs.microsoft.com/intune/device-group-mapping), uppmanas Windows 10-användare nu att välja en enhetskategori efter registreringen via knappen **Anslut** i **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Använd sAMAccountName som användarnamn för e-postprofiler <!-- 1500307 -->
Du kan använda det lokala **sAMAccountName** som kontonamn för e-postprofiler för Android, iOS och Windows 10. Du kan även hämta domänen från attributet `domain` eller `ntdomain` i Azure Active Directory (Azure AD). Eller ange en anpassad statisk domän.

Om du vill använda den här funktionen måste du synkronisera attributet `sAMAccountName` från din lokala Active Directory-miljö till Azure AD.

Gäller [Android](email-settings-android.md), [iOS](email-settings-ios.md) samt [Windows 10 och senare](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Se enhetskonfigurationsprofiler som har konflikter <!-- 1556983 -->
I **Enhetskonfiguration** visas en lista över de befintliga profilerna. I och med den här uppdateringen läggs en ny kolumn till som innehåller information om de profiler som står i konflikt. Du kan välja en rad med en konflikt för att se den inställning och den profil som orsakar konflikten. 

Mer om [hantering av konfigurationsprofiler](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Ny status för enheter i enhetsefterlevnad <!-- 2308882 -->
Följande nya tillstånd har lagts till i **Enhetskonfiguration** > **Principer** > välj en princip > **Översikt**:
- lyckades
- fel
- konflikt
- Väntar
- inte tillämpligt En bild med antalet enheter på andra plattformar visas också. Om du till exempel tittar på en iOS-profil visas antalet enheter med andra system än iOS som också har tilldelats till den här profilen. Se [Efterlevnadsprinciper för enheter](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>Enhetsefterlevnaden får stöd för antiviruslösningar från tredje part <!-- 2325484 -->
När du skapar en princip för enhetsefterlevnad (**Enhetsefterlevnad** > **Principer** > **Skapa princip**  >  **Plattform: Windows 10 och senare** > **Inställningar** > **Systemsäkerhet**), finns det nya alternativ för **[Enhetssäkerhet](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: När **Kräv** har valts kan du kontrollera efterlevnaden med antivirusprogram som är registrerade i Windows Security Center, t.ex. Symantec eller Windows Defender. 
- **AntiSpyware**: När **Kräv** har valts kan du kontrollera efterlevnaden med något av de antispionprogram som har registrerats med Windows Security Center, t.ex. Symantec eller Windows Defender. 

Gäller för: Windows 10 och senare 

### <a name="device-enrollment"></a>Enhetsregistrering

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Enheter utan profilkolumn i listan med token för registreringsprogram <!-- 1853904 -->
Det finns en ny kolumn i listan med token för registreringsprogram som visar antalet enheter som inte har någon tilldelad profil. På så sätt kan administratörer tilldela profiler till dessa enheter innan användarna får dem. Om du vill se den nya kolumnen går du till **Enhetsregistrering** > **Apple-registrering** > **Token för registreringsprogram**.

### <a name="device-management"></a>Enhetshantering

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Googla namnändringar för Android for Work och Play for Work <!--842873 -->
Intune har uppdaterat ”Android for Work”-terminologin med Googles namnändringar. Termerna ”Android for Work” och ”Play for Work” används inte längre. Annan terminologi används beroende på kontext:
- ”Android enterprise” syftar på den moderna programserien för Android-hantering som helhet.
- ”Arbetsprofil” eller ”profilägare” syftar på BYOD-enheter som hanteras med arbetsprofiler.
- ”Managed Google Play” syftar på Googles appbutik.

#### <a name="rules-for-removing-devices----1609459---"></a>Regler för att ta bort enheter <!-- 1609459 -->
Det finns nya regler som gör att du automatiskt kan ta bort enheter som inte har checkats in under ett visst antal dagar som du anger. Om du vill se den nya regeln går du till fönstret **Intune**, väljer **Enheter** och sedan **Regler för rensning av enhet**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>COSU-stöd (Corporate Owned, Single Use) för Android-enheter <!-- 1630973 -->

Nu har Intune stöd för strikt hanterade och låsta Android-enheter i helskärmsläge. Det här gör att administratörer får fler verktyg när det gäller att begränsa användningen på en enhet till en enda upp eller en grupp av appar, så att användarna inte kan starta andra appar eller utföra andra åtgärder på enheten. Du konfigurerar Android-kioskenheter genom att gå till Intune > **Enhetsregistrering** > **Android-registrering** > **Registreringar av kiosk- och aktivitetsenheter**. Läs mer i informationen om att [konfigurera registrering av Android-kioskenheter för företag](android-kiosk-enroll.md).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Radgranskning av dubbletter av uppladdade företagsenhets-id:n <!-- 2203794-->
När du laddar upp företags-ID:n får du nu en lista med eventuella dubbletter i Intune, och du kan välja mellan att ta bort eller behålla den befintliga informationen. Rapporten visas om det finns dubbletter när du har valt **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till id:n**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Lägga till företagsenhets-id:n manuellt <!-- 2203803 -->
Nu kan du lägga till ID:n för företagsenheter manuellt. Välj **Enhetsregistrering** > **Id:n för företagsenheter** > **Lägg till**. 

## <a name="week-of-june-25-2018"></a>Veckan som inleds med 25 juni, 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo – ny partner för skydd mot mobilhot <!-- 1169249 -->

Du kan styra åtkomsten från mobila enheter till företagsresurser med villkorlig åtkomst. Den baseras på riskbedömning som utförs av Pradeo, en lösning för skydd mot mobila hot som är integrerad med Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Veckan som inleds med 18 juni, 2018

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Microsoft Edge-mobilstöd för Intune-appskyddsprinciper <!-- 1817882 -->

Microsoft Edge-webbläsaren för mobila enheter stödjer nu appskyddsprinciper som definieras i Intune.

## <a name="week-of-june-11-2018"></a>Veckan som inleds med 11 juni, 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Använd FIPS-läge med NDES-certifikatanslutningsappen <!-- 1333688 -->
När du installerar NDES-certifikatanslutningsappen på en dator med FIPS-läget (Federal Information Processing Standard) aktiverat fungerade inte utfärdande och återkallande av certifikat som förväntat. I och med den här uppdateringen ingår stöd för FIPS i NDES-certifikatanslutningsappen. 

Den här uppdateringen innehåller även:

- För NDES-certifikatanslutningsappen krävs .NET 4.5 Framework, som automatiskt ingår i Windows Server 2016 och Windows Server 2012 R2. Tidigare var .NET 3.5 Framework den minimiversion som krävdes.
- Stöd för TSL 1.2 ingår i NDES-certifikatanslutningsappen. Om servern med NDES-certifikatanslutningsappen installerat stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

Mer information finns på sidorna om att [konfigurera och använda SCEP-certifikat](certificates-scep-configure.md) och [konfigurera och använda PKCS-certifikat](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Vecka 4 juni 2018

### <a name="app-management"></a>Apphantering

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Hämta den kopplade appanvändarens modell-ID (AUMID) för Microsoft Store för företagsappar i helskärmsläge <!-- 1560077 ! -->
Intune kan nu hämta appanvändarens modell-ID:n (AUMID:er) för Microsoft Store för företagsappar (WSfB) för bättre konfiguration av helskärmslägesprofilen.

Mer information om Microsoft Store för företagsappar finns i [Hantera appar från Microsoft Store för företag](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Ny sida för företagsportalanpassning <!-- 1916370 -->
Sidan för företagsportalanpassning har en ny layout, nya meddelanden och beskrivningar.


### <a name="device-configuration"></a>Enhetskonfiguration

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Stöd för Palo Alto Networks GlobalProtect VPN-profiler <!-- 1333680 ! -->
Med den här uppdateringen kan du välja Palo Alto Networks GlobalProtect som VPN-anslutningstyp för VPN-profiler i Intune (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Profiltyp** > **VPN**). I den här versionen stöds följande plattformar: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Tillägg till inställningar av säkerhetsalternativ för lokal enhet <!-- 1403702 -->
Nu kan du konfigurera ytterligare inställningar av säkerhetsalternativ för lokala Windows 10-enheter. Det finns fler inställningar i Microsoft-nätverksklienten, Microsoft-nätverksservern, för nätverksåtkomst och säkerhet, samt för interaktiv inloggning. Inställningarna finns i kategorin Endpoint Protection när du skapar en princip för Windows 10-enhetskonfiguration.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Aktivera helskärmsläge på Windows 10-enheter <!-- 1560072 ! -->
På Windows 10-enheter kan du skapa en konfigurationsfil och aktivera helskärmsläge (**Enhetskonfiguration** > **Profiler** > **Skapa profil**  >  **Windows 10** > **Enhetsbegränsningar** > **Helskärmsläge**). I den här uppdateringen av **Helskärmsläge (förhandsgranskning)** döps inställningen om till **Helskärmsläge (föråldrad)**. **Helskärmsläge (föråldrad)** rekommenderas inte längre för användning, men fortsätter att fungera fram till juli-uppdateringen. **Helskärmsläge (föråldrad)** ersätts av den nya profiltypen **Helskärmsläge** (**Skapa profil** > **Windows 10**  >  **Helskärmsläge (förhandsgranskning)**), som innehåller inställningar för att konfigurera helskärmslägen på Windows 10 RS4 och senare.

Gäller för Windows 10 och senare.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Enhetsprofilens grafiska användardiagram är tillbaka <!-- 2160133 -->
För att förbättra det numeriska antal som visas på enhetsprofilens grafiska diagram (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**), togs det grafiska diagrammet tillfälligt bort.

Med den här uppdateringen är det grafiska användardiagrammet tillbaka och visas i Azure Portal.

### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Stöd för Windows Autopilot-registrering utan användarautentisering <!-- 1165118 -->
Nu finns det stöd i Intune för Windows Autopilot-registrering utan användarautentisering. Det här är ett nytt alternativ i distributionsprofilen för Windows Autopilot där ”Distributionsläge för Autopilot” får värdet ”Automatisk distribution”.  Enheten måste köra Windows 10 Insider Preview-version 17672 eller senare och ha ett TPM 2.0-chip för att slutföra den här typen av registrering. Eftersom det inte krävs någon användarautentisering bör du bara tilldela det här alternativet för enheter du har fysisk kontroll över.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Ny språk-/regionsinställning när du konfigurerar OOBE för Autopilot <!-- 1821766 -->
En ny konfigurationsinställning kan ange språk och region för Autopilot-profiler från första början. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Ny inställning för att konfigurera enhetstangentbord <!-- 1821768 -->
En ny inställning kommer att kunna konfigurera tangentbordet för Autopilot-profiler under Out of Box-upplevelsen. Du ser den nya inställningen om du väljer **Enhetsregistrering** > **Windows-registrering** > **Distributionsprofiler** > **Skapa profil** > **Distributionsläge** = **Självdistribuerande** > **Standardkonfiguration**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>AutoPilot-profiler flyttas till en grupp som är riktad mot <!-- 1877935 -->
AutoPilot-distributionsprofiler kan tilldelas till Azure AD-grupper som innehåller AutoPilot-enheter.

### <a name="device-management"></a>Enhetshantering

#### <a name="set-compliance-by-device-location----851881----"></a>Ange efterlevnad enligt enhetsplats <!-- 851881 ! -->
I vissa fall kanske du vill begränsa åtkomsten till företagets resurser till en specifik plats som definierats av en nätverksanslutning. Nu kan du skapa en efterlevnadsprincip (**Enhetsefterlevnad** > **Platser**) baserat på IP-adressen till enheten. Om enheten flyttas utanför IP-intervallet kan enheten inte komma åt företagets resurser.

Gäller för: Android-enheter med version 6.0 och senare, med den uppdaterade företagsportalappen

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Förhindra konsumentappar och funktioner för anpassad upplevelse i Windows 10 Enterprise RS4 AutoPilot-enheter<!-- 1621980 -->
Du kommer att kunna förhindra installationen av konsumentappar och funktioner för anpassad upplevelse på dina Windows 10 Enterprise RS4 AutoPilot-enheter. Du ser den här funktionen om du går till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Plattform** = **Windows 10 eller senare** > **Profiltyp** = **Enhetsbegränsningar** > **Konfigurera** > **Windows Spotlight** > **Konsumentfunktioner**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Avinstallera den senaste programuppdateringen för Windows 10 <!-- 1732948 -->
Om du upptäcker ett allvarligt problem på dina Windows 10-datorer kan du avinstallera den senaste funktionsuppdateringen eller den senaste kvalitetsuppdateringen. Du kan bara avinstallera en funktions- eller kvalitetsuppdatering via enhetens underhållskanal. Vid avinstallationen utlöses en princip för att återställa den tidigare uppdateringen på Windows 10-datorerna. För funktionsuppdateringar specifikt kan du begränsa tiden från 2–60 dagar som en avinstallation av den senaste versionen kan tillämpas. Om du vill ange alternativ för avinstallation av programuppdateringar väljer du **Programuppdateringar** från bladet **Microsoft Intune** i Azure Portal. Välj sedan **Windows 10-uppdateringsringar** på bladet **Programuppdateringar**. Du kan sedan välja alternativet **Avinstallera** i avsnittet **Översikt**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Söka alla enheters IMEI och serienummer <!-- 1793685 -->
Du kan nu söka efter IMEI och serienummer på bladet Alla enheter (e-post, UPN, enhetsnamn och hanteringsnamn finns kvar). Välj **Enheter** > **Alla enheter** i Intune och ange dina sökvillkor i sökrutan.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Hanteringsnamnfältet kan redigeras <!-- 1875989 -->
Nu kan du redigera hanteringsnamnfältet på bladet **Egenskaper** för en enhet. Om du vill redigera det här fältet väljer du **Enheter** > **Alla enheter** > välj enheten > **Egenskaper**. Du kan använda hanteringsnamnfältet för att unikt identifiera en enhet.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nytt filter för Alla enheter: Enhetskategori <!-- 1878520 -->
Nu kan du filtrera listan **Alla enheter** efter enhetskategori. Om du vill göra det väljer du **Enheter** > **Alla enheter** > **Filter** > **Enhetskategori**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Använd TeamViewer för att skärmdela iOS- och MacOS-enheter <!-- 1985547 -->
Nu kan administratörer ansluta till [TeamViewer](device-profile-android-teamviewer.md) och börja skärmdela en session med iOS- och macOS-enheter. iPhone-, iPad- och macOS-användare kan dela sina skärmar live med andra stationära och mobila enheter. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Stöd för flera Exchange Connector <!-- 2070451 -->
Du är inte längre begränsad till en Exchange-anslutningsapp per klientorganisation i Microsoft Intune. Intune har nu stöd för flera Exchange-anslutningsappar, så att du kan ställa in villkorlig åtkomst i Intune med flera lokala Exchange-organisationer.

Med en lokal Exchange Connector för Intune kan du hantera enhetsåtkomst till dina lokala Exchange-postlådor, baserat på om en enhet har registrerats i Intune och uppfyller Intunes enhetsefterlevnadsprinciper. Om du vill konfigurera ett anslutningsprogram laddar du ned den lokala Exchange Connector för Intune från Azure-portalen och installerar den på en server i Exchange-organisationen. På Microsoft Intune-instrumentpanelen väljer du **Lokal åtkomst** och under **Installation** väljer du sedan **Exchange ActiveSync Connector**. Ladda ned det lokala Exchange-anslutningsprogrammet och installera det på en server i din Exchange-organisation. Nu när du är inte längre begränsad till ett Exchange-anslutningsprogram per klient, och om du har ytterligare Exchange-organisationer, kan du följa samma process för att ladda ned och installera ett anslutningsprogram för varje ytterligare Exchange-organisation.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Ny detalj i enhetens maskinvara: CCID <!-- 2156657 -->
Nu ingår CCID-informationen (Chip Card Interface Device) för varje enhet. Om du vill se den väljer du **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**> leta under **Nätverksinformation**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Tilldela alla användare och alla enheter som omfångsgrupper <!-- 2196803 -->
Nu kan du tilldela alla användare, alla enheter samt alla användare och alla enheter i omfångsgrupper. Om du vill göra det väljer du **Intune-roller** > **Alla roller** > **Policy and profile manager** > **Tilldelningar** > välj en tilldelning > **Omfång (grupper)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Nu ingår UDID-information för iOS- och macOS-enheter <!-- 2219806 -->
Om du vill se UDID (Unique Device Identifier) för iOS- och macOS-enheter går du till **Enheter** > **Alla enheter** > välj en enhet > **Maskinvara**. UDID är endast tillgängligt för företagsenheter (anges under **Enheter** > **Alla enheter** > välj en enhet > **Egenskaper** > **Ägarskap för enhet**).

### <a name="intune-apps"></a>Intune-appar

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Förbättrad felsökning för appinstallationen <!-- 928990 -->
På Microsoft Intune MDM-hanterade enheter kan ibland appinstallationer misslyckas. När dessa appinstallationer misslyckas, kan det vara en utmaning att förstå felorsaken eller felsöka problemet. Vi levererar en allmänt tillgänglig förhandsversion av våra appfelsökningsfunktioner. Du ser en ny nod under varje enskild enhet som kallas **Hanterade appar**. Den visar en lista med appar som har levererats via Intune MDM. I noden visas en lista över installeringstillstånd för appar. Om du väljer en enskild app visas vyn felsökning för den specifika appen. I felsökningsvyn visas slutpunkt till slutpunkt-livscykeln för appen, till exempel när appen har skapats, ändrats, riktats och levererats till en enhet. Dessutom, om inte appinstallationen lyckades visas felkoden och ett användbart meddelande om orsaken till felet. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Skyddsprinciper för Intune-appen och Microsoft Edge <!-- 1818968 -->
Microsoft Edge-webbläsaren för mobila enheter (iOS och Android) har nu stöd för skyddsprinciper i Microsoft Intune-appen. Användare med iOS- och Android-enheter som loggar in med företagets Azure AD-konto i Edge kommer att skyddas av Intune. På iOS-enheter gör principen **Kräver hanterad webbläsare för webbinnehåll** att användarna kan öppna länkar i Microsoft Edge när det hanteras.

## <a name="week-of-may-14-2018"></a>Vecka 14 maj 2018

### <a name="app-management"></a>Apphantering

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Kräv installation av principer, appar, certifikat och nätverksprofiler <!-- 1553555 -->

Administratörer kan blockera slutanvändarna från att komma åt skrivbordet i Windows 10 RS4 tills Intune har installerat principer, appar, certifikat och nätverksprofiler under etableringen av AutoPilot-enheter. Mer information finns i [Konfigurera en sida för registreringsstatus](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Konfigurera dina appskyddsprinciper <!-- 2144597 Part 2 -->

I stället för att gå till bladet för Intunes appskyddstjänst på Azure Portal går du bara till Intune nu. Nu finns det bara en plats för appskyddsprinciper i Intune. Observera att alla dina appskyddsprinciper finns på bladet **Mobilapp** i Intune under **Appskyddsprinciper**. Den här integrationen gör det enklare att administrera molnhanteringen. Alla appskyddsprinciper finns redan i Intune och du kan ändra redan konfigurerade principer. Intunes apprincipskydd (APP) och principer för villkorlig åtkomst (CA) finns nu under **Villkorlig åtkomst**, som du hittar under avsnittet **Hantera** på bladet **Microsoft Intune** under avsnittet **Säkerhet** på bladet **Azure Active Directory**. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Vecka 7 maj 2018

### <a name="app-management"></a>Apphantering

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Stöd för Samsung Knox Mobile-registrering <!--1112863-->

När du använder Intune med Samsung Knox Mobile-registrering (KME), kan du registrera ett stort antal företagsägda Android-enheter. Användarna på Wi-Fi eller mobila nätverk kan registrera sig med bara några få tryck när de aktiverar på sina enheter för första gången. När du använder Knox-distributionsprogrammet kan enheter registreras med hjälp av Bluetooth eller NFC. Mer information finns i [Registrera Android-enheter automatiskt med hjälp av från Samsung Knox Mobile-registrering](android-samsung-knox-mobile-enroll.md).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Be om hjälp i företagsportalen för Windows 10 <!-- 1874137 -->

Företagsportalen för Windows 10 kommer nu att skicka apploggar direkt till Microsoft när användaren startar arbetsflödet för att få hjälp med problemet. Detta gör det enklare att felsöka och lösa problem som tas upp till Microsoft.

## <a name="week-of-april-23-2018"></a>Veckan 23 april 2018

### <a name="app-management"></a>Apphantering

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Lösenordsstöd för MAM PIN-kod på Android<!-- 1438086 -->

Intune-administratörer kan ange ett programstartskrav för att framtvinga ett lösenord i stället för en numerisk MAM PIN-kod. Om det har konfigurerats måste användaren vid uppmaning ställa in och använda ett lösenord innan användaren får åtkomst till MAM-integrerade program. Ett lösenord definieras som en numerisk PIN-kod med minst ett specialtecken eller en gemen/versal. Intune stöder lösenord på liknande sätt som numeriska PIN-koder. En minsta längd kan anges, vilket tillåter upprepning av tecken och sekvenser via administratörskonsolen. Den här funktionen kräver den senaste versionen av företagsportalen för Android. Funktionen finns redan tillgänglig för iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Stöd för verksamhetsspecifika appar (LOB) för macOS <!-- 1473977 -->
I Microsoft Intune går det att installera branschspecifika macOS-appar från Azure Portal. Du kommer att kunna lägga till en branschspecifik macOS-app i Intune som redan har förbehandlats av verktyget i GitHub. I Azure Portal väljer du **Klientappar** på bladet **Intune**. På bladet **Klientappar** väljer du **Appar** > **Lägg till**. På bladet **Lägg till app** väljer du **Branschspecifik app**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>De inbyggda grupperna Alla användare och Alla enheter för apptilldelning av Android Enterprise-arbetsprofil <!-- 1813073 -->
Du kan använda de inbyggda grupperna **Alla användare** och **Alla enheter** vid apptilldelning för Android enterprise-arbetsprofil. Mer information finns i [Inkludera och exkludera apptilldelningar i Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune kommer att installera om obligatoriska appar som avinstalleras av användare <!-- 1947010 -->
Om en slutanvändare avinstallerar en obligatorisk app, installerar Intune automatiskt om appen igen inom 24 timmar i stället för att vänta på omvärderingscykeln på 7 dagar.

### <a name="device-configuration"></a>Enhetskonfiguration

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Enhetens profildiagram och statuslista visar alla enheter i en grupp <!-- 1449153 -->
När du konfigurerar en enhetsprofil (**Enhetskonfiguration** > **Profiler**) väljer du enhetsprofil, till exempel iOS. Du tilldelar profilen till en grupp med både iOS-enheter och enheter som inte är iOS. Antalet i det grafiska diagrammet visar att profilen tillämpas på både iOS-enheter *och* enheter som inte är iOS (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**). När du väljer det grafiska diagrammet på fliken **Översikt** visar **Enhetsstatus** alla enheterna i gruppen, i stället för enbart iOS-enheterna. 

Med den här uppdateringen visar det grafiska diagrammet (**Enhetskonfiguration** > **Profiler** > välj en befintlig profil > **Översikt**) endast antalet för den specifika enhetsprofilen. Om till exempel den konfigurerade enhetsprofilen gäller för iOS-enheter, visar diagrammet endast antal iOS-enheter. Om du väljer det grafiska diagrammet och öppnar **Enhetsstatus**, visas endast iOS-enheterna.

När uppdateringen gjorts har det grafiska diagrammet tillfälligt tagits bort. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>AlwaysOn-VPN för Windows 10 <!--1333666 -->

För närvarande kan [AlwaysOn](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) användas på Windows 10-enheter med hjälp av en anpassad VPN-profil (virtuellt privat nätverk) som skapats med OMA-URI.

Med den här uppdateringen kan administratörer aktivera AlwaysOn för VPN-profiler i Windows 10 direkt i Intune i Azure-portalen. VPN-profiler med AlwaysOn ansluts automatiskt när:

- Användarna loggar in på sina enheter
- Nätverket på enheten ändras
- Skärmen på enheten sätts på efter att ha varit avstängd

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nya skrivarinställningar för utbildningsprofiler <!-- 1308900 -->

Det finns nya inställningar för utbildningsprofiler under kategorin **Skrivare**: **Skrivare**, **Standardskrivare**, **Lägg till nya skrivare**.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Visa nummerpresentation i personlig profil – Android Enterprise-arbetsprofilen <!--1098984 -->
När du använder en personlig profil på en enhet, kan slutanvändare inte se nummerpresentation för en arbetskontakt. 

I och med uppdateringen finns en ny inställning i **Android Enterprise** > **Enhetsbegränsningar** > **Arbetsprofilinställningar**:
- Visa arbetskontaktens nummerpresentation i personlig profil

När aktiverat (inte konfigurerat), visas arbetskontaktens nummerpresentation i den personliga profilen. När blockerad, visas inte arbetskontaktens nummerpresentation i den personliga profilen. 

Gäller för: Androids arbetsprofilenheter på Android OS v6.0 och senare

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nya Windows Defender Credential Guard-inställningar har lagts till i inställningarna för slutpunktsskydd<!--1102252 --><!--from 1802 and 1804-->

Med denna uppdatering, inkluderar [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Enhetskonfiguration** > **Profiler** > **Slutpunktsskydd**) följande inställningar: 

- **Windows Defender Credential Guard**: Aktiverar Credential Guard med virtualiseringsbaserad säkerhet. Aktivering av den här funktionen hjälper till att skydda autentiseringsuppgifterna vid nästa omstart när både **Säker start för Säkerhetsnivå för plattform** och **Virtualiseringsbaserad säkerhet** är aktiverade. Alternativen är:
  - **Inaktiverad**: Om Credential Guard har aktiverats tidigare med alternativet**Aktiverat utan lås**, slås Credential Guard av på distans.

  - **Aktiverat med UEFI-lås**: Ser till att Credential Guard inte kan inaktiveras med en registernyckel eller via en grupprincip. Om du vill inaktivera Credential Guard när du använder den här inställningen måste du ställa in Grupprincip som ”Inaktiverad”. Ta sedan bort säkerhetsfunktionen från varje dator med en användare fysiskt närvarande. De här stegen rensar den kvarstående konfigurationen i UEFI. Så länge UEFI-konfigurationen finns kvar är Credential Guard aktiverat.

  - **Aktiverat utan lås**: Innebär att Credential Guard kan inaktiveras på distans med grupprincipen. Enheterna som använder den här inställningen måste köra Windows 10 eller senare (version 1511).

Följande beroende tekniker aktiveras automatiskt när du konfigurerar Credential Guard: 

  - **Aktivera virtualiseringsbaserad säkerhet (VBS)**: Aktiverar virtualiseringsbaserad säkerhet (VBS) vid nästa omstart. Virtualiseringsbaserad säkerhet använder Windows Hypervisor för att ge stöd för säkerhetstjänster och kräver Säker start.
  - **Säker start med direkt minnesåtkomst (DMA)**: Aktiverar VBS med säker start och direkt minnesåtkomst. DMA-skydd kräver maskinvarustöd och aktiveras endast på enheter som är korrekt konfigurerade. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Använda ett anpassat certifikatmottagarnamn på SCEP-certifikat <!-- 2064190 -->
Du kan använda det egna namnet **OnPremisesSamAccountName** i en anpassad certifikatmottagare för en SCEP-certifikatprofil. Du kan till exempel använda `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Blockera kamera och skärmbilder i Android Enterprise-arbetsprofiler <!-- 1098977 -->
Två nya egenskaper kan blockeras när du konfigurerar enhetsbegränsningar för Android-enheter: 
- Kamera: Blockerar åtkomsten till alla kameror på enheten
- Skärmbild: Blockerar skärmbildtagning och förhindrar också att innehållet visas på enheter som inte har någon säker videoutgång

Gäller för Android Enterprise-arbetsprofiler.


### <a name="device-enrollment"></a>Enhetsregistrering

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nya registreringssteg för användarna på enheter med macOS High Sierra 10.13.2+ <!--1734567 -->
I macOS High Sierra 10.13.2 finns nu begreppet ”Användargodkänd” MDM-registrering. Godkända registreringar tillåter Intune att hanterar vissa säkerhetskänsliga inställningar. Mer information finns i Apples supportdokumentation här: https://support.apple.com/HT208019.

Enheter som registreras med macOS-företagsportalen betraktas som ”Inte användargodkända” tills användaren öppnar systeminställningarna och ger sitt manuella godkännande. Därför dirigerar macOS-företagsportalen nu användare av macOS 10.13.2 och senare till att manuellt godkänna registreringen i slutet av registreringsprocessen. Intune-administratörskonsolen rapporterar om en registrerad enhet är användargodkänd.



### <a name="device-management"></a>Enhetshantering

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) och Intune är helt integrerade <!-- 1629303 -->

[Avancerat skydd (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) visar risknivån för Windows 10-enheter. I Windows Defender Security Center (ATP-portal), kan du skapa en anslutning till Microsoft Intune. När du skapat anslutningen används en efterlevnadsprincip av Intune för att fastställa en godtagbar hotnivå. Om hotnivån överskrids kan sedan en villkorlig åtkomstprincip för Azure Active Directory (AD) blockera åtkomst till olika appar i din organisation.

Den här funktionen tillåter ATP att söka igenom filer, identifiera hot och rapportera eventuella risker på Windows 10-enheter.

Se [Aktivera ATP med villkorlig åtkomst i Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Stöd för användarlösa enheter <!-- 1637553 -->
Intune stöder möjligheten att utvärdera efterlevnaden på en användarlös enhet som exempelvis Microsoft Surface Hub. Policyer för efterlevnad kan riktas mot specifika enheter. Det innebär att efterlevnad (och inkompatibilitet) kan fastställas för enheter som inte har någon associerad användare.

#### <a name="delete-autopilot-devices----1713650---"></a>Ta bort AutoPilot-enheter <!-- 1713650 -->
Intune-administratörer kan [ta bort AutoPilot-enheter](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Förbättrad enhetsborttagning <!--1832333 -->
Du kommer inte längre behöva ta bort företagets data eller fabriksåterställa en enhet innan du [tar bort enheten från Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Om du vill se den nya funktionen loggar du in på Intune och väljer **Enheter** > **Alla enheter** > namnet på enheten > **Ta bort**.

Om du fortfarande vill att rensningen ska utföras kan du använda standardenhetens livscykel med hjälp av **Ta bort företagsinformation** och **Fabriksåterställning** innan du väljer **Ta bort**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Spela upp ljud på iOS när den befinner sig i Borttappat läge <!-- 1947769 -->
När övervakade iOS-enheter är i hanteringen av mobilenheters (MDM) [Borttappat läge](device-lost-mode.md), kan du [spela upp ett ljud](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Enheter** > **Alla enheter** > välj en iOS-enhet > **Översikt** > **Mer**). Ljudet fortsätter att spelas upp tills enheten tas bort från Borttappat läge, eller en användare stänger av ljudet. Gäller för iOS-enheter 9.3 och nyare.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Blockera eller tillåta webbresultat i sökningar på en Intune-enhet <!--1972804-->

Administratörer kan nu blockera webbresultat från sökningar gjorda på en enhet.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Förbättrade felmeddelanden när Apple MDM-pushcertifikat inte kan överföras <!-- 2172331 -->

Felmeddelandet förklarar att samma Apple-ID måste användas när du förnyar ett befintligt MDM-certifikat.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testa företagsportalen för macOS på virtuella datorer <!-- 2216679 -->

Vi har publicerat vägledning som hjälper IT-administratörer testa företagsportalappen för macOS i Parallels Desktop och VMware Fusion. Du hittar mer information i avsnittet om att [registrera virtuella macOS-datorer för testning](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Användargränssnitt

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Förbättrade enhetspaneler i företagsportalen för Windows 10 <!--2213364 -->

Panelerna har uppdaterats för att blir lättillgängligare för användare med sämre syn och för att fungera bättre tillsammans med skärmläsningsverktyg.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Skicka diagnostikrapporter i företagsportalappen för macOS <!-- 2216677 -->
Företagsportalappen för macOS-enheter har uppdaterats för att förbättra hur användarna rapporterar Intune-relaterade fel. Från företagsportalappen kan dina anställda:

- Ladda upp diagnostikrapporter direkt till Microsofts utvecklingsteam.
- E-posta ett incident-ID till ditt företags IT-supportteam.

Mer information finns i [Skicka fel till rätt personer för din hanterade macOS-enhet](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune anpassar sig efter Fluent Design System i företagsportalappen för Windows 10 <!-- 1195010 -->
Intunes företagsportalapp för Windows 10 har uppdaterats med [Fluent Design Systems navigeringsvy](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). Längs appen ser du en statisk, lodrät lista över alla sidor på översta nivån. Klicka på en länk för att snabbt visa och växla mellan sidor. Det här är den första av flera uppdateringar som visas som en del av vårt pågående arbete för att skapa en mer anpassningsbar, empatisk och bekant upplevelse i Intune. Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Veckan 16 april 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Använda Cisco AnyConnect klienten för iOS <!-- 1333708 -->

Det finns nu två alternativ när du skapar en ny VPN-profil för iOS: **Cisco AnyConnect** och **Cisco Legacy AnyConnect**. Cisco AnyConnect-profiler stöder 4.0.7x och nyare versioner. Befintliga iOS Cisco AnyConnect VPN-profiler är märkta **Cisco Legacy AnyConnect** och kommer fortsatt att fungera med Cisco AnyConnect 4.0.5x och äldre versioner som de gör i dag.

> [!NOTE]
> Den här ändringen gäller bara för iOS. Det finns fortfarande ett enda Cisco AnyConnect-alternativ för Android-, Android Enterprise-arbetsprofiler- och macOS-plattformar.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>MacOS Jamf-registrerade enheter kan nu registreras med Intune <!-- 2370684 -->

Version 1.3 och 1.4 av macOS-företagsportal registrerades inte Jamf-enheter med Intune korrekt. Version 1.4.2 av macOS-portalen åtgärdar det här problemet.


## <a name="week-of-april-9-2018"></a>Veckan som börjar med 9 april 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Uppdaterad hjälpfunktion i företagsportalappen för Android <!-- 1631531 -->

Vi har uppdaterat hjälpfunktionen i Android-versionen av företagsportalappen och anpassat den till bästa praxis för Android-plattformen. När användarna stöter på ett problem i appen kan de nu trycka på **Menu (Meny)** > **Help (Hjälp)** och:
- Skicka diagnostikloggar till Microsoft.
- Skicka ett e-postmeddelande som beskriver problemet och incident-ID till företagets supportavdelning.  

Om du vill kolla in den uppdaterade hjälpfunktionen går du till [Send logs using email](/intune-user-help/send-logs-to-your-it-admin-by-email-android) (Skicka loggar via e-post) och [Send errors to Microsoft](/intune-user-help/send-logs-to-microsoft-android) (Skicka fel till Microsoft).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nytt trenddiagram för registreringsfel och tabell över felorsaker <!-- 1471783 -->

På registreringsöversiktssidan kan du se trenden för registreringsfel och de fem viktigaste felorsakerna. Genom att klicka på diagrammet eller tabellen kan du gå in på detaljnivå för att hitta felsökningstips och åtgärdsförslag.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Uppdatera var du konfigurerar dina appskyddsprinciper <!-- 2144597 -->

I tjänsten Microsoft Intune i Azure Portal kommer vi att tillfälligt dirigera om dig från bladet för tjänsten **Intune-appskydd** till bladet **Mobilapp**. Alla dina appskyddsprinciper finns redan på bladet **Mobilapp** i Intune under appkonfigurationen. I stället för att gå till Intune-appskydd går du bara till Intune. I april 2018 stoppar vi omdirigeringen och tar helt bort bladet för tjänsten **Intune-appskydd** så att det bara finns en plats för appskyddsprinciper i Intune. 

**Hur påverkar det här mig?**
Den här förändringen påverkar både kunder som har fristående Intune och hybridkunder (Intune med Configuration Manager). Den här integreringen hjälper till att förenkla administrationen av molnhanteringen.

**Vad kan jag göra för att förbereda mig för den här ändringen?**
Lägg till **Intune** som favorit i stället för bladet för tjänsten **Intune-appskydd**, och se till att du känner till arbetsflödet för appskyddsprinciper på bladet **Mobilapp** i Intune. Vi omdirigerar under en kort tidsperiod och tar sedan bort **appskyddsbladet**. Tänk på att alla appskyddsprinciper redan finns i Intune och att du kan ändra dina villkorliga åtkomstprinciper. Mer information om hur du ändrar principer för villkorlig åtkomst finns [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Ytterligare information finns i [Vad är appskyddsprinciper?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Veckan 2 april 2018

### <a name="intune-apps"></a>Intune-appar

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Uppdatering av användarupplevelsen för appen Företagsportal för iOS <!--1412866 -->
Vi har släppt en större uppdatering av användarupplevelsen i företagsportalappen för iOS. Uppdateringen är en fullständig visuell omarbetning som ger appen en modernare design. Vi har bevarat appens funktionalitet men förbättrat användarvänligheten och tillgängligheten.  

Andra nyheter:
- Stöd för iPhone X.
- Snabbare appstart och inläsning som sparar tid för användarna.
- Fler förloppsindikatorer som ger användarna den senaste statusinformationen.
- Sättet att skicka loggar har förbättrats och det har blivit enklare att rapportera om något går fel.  

Gå till avsnittet om [nyheter i appgränssnittet](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Skydda lokala Exchange-data med hjälp av Intune APP och CA <!-- 1056954 -->
Du kan nu använda Intunes appskyddsprincip (APP) och villkorlig åtkomst (CA) för att skydda åtkomsten till lokala Exchange-data med Outlook Mobile. Om du vill lägga till eller ändra en appskyddsprincip i Azure Portal väljer du **Microsoft Intune** > **Klientappar** > **Appskyddsprinciper**. Innan du använder den här funktionen måste du se till att du uppfyller [kraven för Outlook för iOS och Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="notices"></a>Meddelanden

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Kommande tvingad lösenordsändring för macOS 10.14.2 i Intune <!--1873216-->
I juli meddelade vi i MC145129 att Intune planerar att integrera Apples nyligen utgivna inställning Change Password at Next Auth (Ändra lösenord vid nästa autentisering) för enheter som kör macOS versioner 10.13 och senare. Vi planerar att distribuera den här inställningen i februari för macOS 10.14.2 och senare. 

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Detta påverkar dig om du har eller planerar att ha enheter som kör macOS 10.14.2 och senare. Nu när Apple har introducerat inställningen Change Password at New Auth (Ändra lösenord vid ny autentisering) kan Intune tvinga användare att uppdatera sina lösenord till ett som är kompatibelt när en lösenordsprincip skickas ut. Dina macOS-användare får en begäran om att uppdatera sina lösenord när vi integrerar den här nya Apple-funktionen, även om lösenorden redan är kompatibla. Observera att om ett lösenord redan är kompatibelt och du inte har något krav om upprepade lösenord, så kan slutanvändarna uppdatera till sina befintliga lösenord. Slutanvändarna ser bara en begäran att uppdatera sitt lösenord när de försöker autentisera eller logga in på sin enhet. Om du blockerar företagsresurser tills enheten har markerats som kompatibel ska du komma ihåg att slutanvändarna på enheter med macOS 10.14.2 kanske blockeras från att komma åt företagsresurser som e-post och SharePoint-webbplatser tills de återställer sina lösenord. I framtiden kommer alla uppdateringar av principer för konfiguration och lösenordskompatibilitet att tvinga användarna att uppdatera sina lösenord. Våra kundundersökningar innan vi implementerade den här ändringen visade att de flesta kunder inte påverkas av den här ändringen, eftersom användarna normalt uppdaterar sitt lösenord när de får en begäran om att registrera sig med ett lösenord eller återställa sitt lösenord för att fortsätta vara kompatibla

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du kanske ska informera supportavdelningen. Vi uppdaterar den här sidan när ändringen distribueras. Om du inte vill tillämpa den här lösenordsprincipen för macOS-enheter rekommenderar vi att du tar bort tilldelningen eller tar bort den befintliga macOS-principen.

###<a name="plan-for-change-update-to-ios-setting-for-supervised-devices-in-the-intune-console"></a>Planera för förändring: Uppdatering av iOS-inställning för övervakade enheter i Intune-konsolen  
Med februariuppdateringen av Intune-tjänsten byter inställningen ”Aktivera begränsningar i enhetsinställningarna” för övervakade iOS-enheter namn till ”Skärmtid (endast övervakat)”. Efter den här ändringen förändras funktionen för slutanvändare utifrån iOS-version.

####<a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
När inställningen ”Aktivera begränsningar i enhetsinställningarna (endast övervakat)” byter namn till ”Skärmtid (endast övervakat)” är följande miljön för övervakade enheter (enheter registrerade med Apples registreringsprogram): 

För enheter med iOS 11.4 och tidigare: Den här inställningen kan användas till att förhindra användare att ändra enhetsbegränsningar som förut. Slutanvändarna ser ingen ändring i miljön.
 
För enheter med iOS 12 och senare: Slutanvändarna ser inte längre fliken Begränsningar under Inställningar > Allmänt > Enhetshantering > Hanteringsprofil > Begränsningar.
Istället blir det en del av Inställningar > Allmänt > Skärmtid. Om du konfigurerar inställningen med värdet ”Blockera” så blockeras användarna från att ändra inställningarna under Skärmtid på sina enheter, vilket också omfattar innehåll och sekretessbegränsningar.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Uppdatera din vägledning för slutanvändare så att ändringen av funktioner noteras för enheter som uppgraderas till iOS 12 och senare versioner.


###<a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Planera för förändring: Ändringar av arbetsflödet för iOS 12-registrering i Intune
Apple har tillkännagivit några ändringar relaterade till iOS-enheters registrering i MDM-tjänster. Ändringen kommer sannolikt i iOS-utgåvan som släpps på våren 2019 och alla framtida iOS-versioner.

####<a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Om dina slutanvändare uppgraderar sina enheter till den här nya versionen av iOS 12 på våren bör du känna till att arbetsflödet ändras och att de måste vidta ytterligare åtgärder för att slutföra registreringen i Intune. När Apple introducerar dessa ändringar måste slutanvändarna: •            inleda registreringsprocessen i appen Företagsportal för att ladda ned en hanteringsprofil •            gå till Inställningar > Allmänt > Profiler •            välja rätt profil och klicka fram till Installera •            gå tillbaka till Företagsportal för att slutföra registreringen 

Enheter som redan har registrerats och uppgraderats till den nya iOS-versionen bör inte påverkas om de inte avregistreras och behöver en ny registrering.
Registreringsprocessen på enheter med iOS 12.1 eller tidigare ändras inte med den här nya versionen av Apple.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du bör planera en uppgradering av dokumentationen och vägledningen för slutanvändare. Du kanske också vill meddela supportavdelningen om ändringarna. Vi informerar dig via Meddelandecenter och sidan Nyheter när den här ändringen börjar gälla.

Klicka på Ytterligare information så visas ett blogginlägg med skärmbilder och en video om det förväntade registreringsflödet.

####<a name="additional-information"></a>Ytterligare information
https://aka.ms/iOS_enrollment_changes

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Planera för förändring: Uppdatering av användarupplevelsen för appen Intune-företagsportal för iOS
Vi är glada att kunna meddela att Intune snart lanserar en större uppdatering av användarupplevelsen i appen Företagsportal för iOS. Uppdateringen omfattar en visuell omarbetning av startsidan med avancerade filter och snabbare åtkomst till appar och böcker.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Nuvarande iOS-funktioner i Företagsportalen bevaras, men den här uppdateringen omfattar följande:
- En startsida med typiskt iOS-utseende 
- Filtreringsfunktioner i innehållslistor och sökning, bland annat möjligheten att filtrera efter innehållstyp (appar eller e-böcker) och tillgänglighet (enhetshantering obligatorisk eller tillgängligt utan registrering)
- Möjligheten att söka i e-böcker
- Sökhistorik för appar och e-böcker Om du deltar i Apple TestFlight-programmet kommer du att meddelas om förhandsversionen av Intunes uppdaterade app Företagsportal för iOS när den blir tillgänglig. Om du inte deltar i Apple TestFlight-programmet är det inte för sent att registrera dig. Om du registrerar dig kan du använda den uppdaterade appen Företagsportal innan den är tillgänglig för dina slutanvändare. Du kan också ge feedback direkt till Intune-teamet.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte vidta några åtgärder. De här ändringarna kommer att lanseras i en kommande version av appen iOS FP. 

#### <a name="additional-information"></a>Ytterligare information
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Planera för förändring: Exchange Online till Intune-anslutningsprogrammet kommer inte finnas tillgängligt i Intune <!-- 3105122 -->
Vi kommer att inaktivera Exchange Online till Intune-anslutningsprogrammet ”Service to Service” för att förenkla din upplevelse med Exchange Online och villkorlig åtkomst.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
Du får det här meddelandet eftersom våra uppgifter visar att du använder anslutningsfunktionen ”Service to Service” i din miljö. Anslutningsprogrammet ”Service to Service” stöder Intune-hantering av enheter med endast Exchange Active Sync för Exchange Online och stöder inte lokal infrastruktur. På grund av sättet som anslutningsprogrammet visas på konsolen verkar den vara nödvändig för villkorlig åtkomst (CA), men i verkligheten behövs den inte för CA. I februariuppdateringen av Intune-tjänster kommer vi, för att göra detta tydligt i konsolen, att inaktivera knappen för att konfigurera nya anslutningsprogram. I mars 2019 kommer sedan alla befintliga anslutningar för Exchange Online till Intune att inaktiveras.

Om du använder dessa anslutningsprogram i din miljö kommer du inte kunna övervaka eller rensa enheter med endast Exchange Active Sync i Intune efter att anslutningsprogram har inaktiverats i mars. Det finns ingen förväntad påverkan för slutanvändare under ändringen.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?

Om du har anslutningsprogrammet ”Service to Service” konfigurerat och enheter med endast Exchange Active Sync måste du byta till andra hanteringsmetoder för dina enheter. Du kan välja mellan följande alternativ:

- Registrera enheter i hantering av mobilenheter (MDM)
- Använd Intunes appskyddsprinciper för att hantera dina enheter
- Använd Exchange-kontrollerna som beskrivs i dokumentationen. 

#### <a name="additional-information"></a>Ytterligare information
[Konfigurera Exchange-tjänstens anslutningsprogram för Intune och Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Ändringsplan: Prestandauppdateringar av Intune for Education <!--1750215-->
Vi lägger till några uppdateringar till Intune for Education för att öka hastigheten och tillförlitligheten när du tilldelar inställningar till användare eller enheter. Som en del av den här ändringen kommer vi fram emot slutet av november att flytta dina tilldelningar av principer eller inställningar till nya grupper.

#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?

Som Intune for Education-kund har du två dynamiska Azure Active Directory-grupper (AD Azure): ”Alla användare” och ”Alla enheter”. Med de här uppdateringarna kommer Azure AD-grupperna ”Alla användare” och ”Alla enheter” inte att synas i Intune for Education-konsolen. De kommer dock fortfarande att vara synliga i Intune på Azure-konsolen och kommer att byta namn till ”All Users (Obsolete, do not use)” (Alla användare (inaktuell; använd ej)) och ”All Devices (Obsolete, do not use)” (Alla enheter (inaktuell; använd ej)).

När uppdateringarna lanseras behöver du inte längre använda Azure AD-grupper för att tilldela appar och inställningar i Intune. I stället flyttar vi dina inställningstilldelningar till nya grupper i den Intune for Education-konsol som vi skapar. De här grupperna visas fortfarande som ”Alla användare” och ”Alla enheter” som förut. Dessa ändringar finns i serverdelen, så du kommer inte att märka något annorlunda i Intune for Education-konsolen. Det förväntas inte bli någon påverkan på dina slutanvändare eller registrerade enheter. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Vad kan jag göra för att förbereda mig för den här ändringen?
Du behöver inte göra något medan vi flyttar din principtilldelningar. Om du för närvarande tilldelar principer i Intune for Education-konsolen kan du fortsätta med det.

Om du för närvarande tilldelar principer i de Azure AD-grupper som nämns ovan i Intune på Azure kan du börja tilldela dem till grupperna Alla användare och Alla enheter i Intune for Education-konsolen i stället. När du ser Azure AD-grupper som bytt namn till ”obsolete” (inaktuell) i konsolen slutar du tilldela principer i Azure AD. Om du för närvarande inte använder de grupper som bytt namn i något annat syfte bör du ta bort dem.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Vidta åtgärd: Uppdatera Android-enhetsbegränsningen eller efterlevnadsprincipen för lösenordsinställningar i Intune
Intune kommer att ta bort den tillgängliga lösenordstypen ”Standard för enheten” för enheter med Android 4.4 eller senare. På grund av skillnader mellan Android-plattformar och enhetsstandarder behandlas principen ofta som valfri av enheten. Vi kommer att ta bort den här inställningen från användargränssnittet i en kommande version i syfte att undvika förvirring kring när inställningen genomdrivs i Android. 
#### <a name="how-does-this-affect-me"></a>Hur påverkar det här mig?
- Om din avsikt är att kräva ett lösenord på enheterna rekommenderar vi att du redigerar dina Android-plattformsprofiler och tydligt anger vilken lösenordstyp som krävs, istället för att använda ”Standard för enheten”.
- Om din avsikt är att låta användarna själva välja om de vill skapa ett lösenord väljer du knappen ”Inte konfigurerad”. Om inställningen fortfarande är konfigurerad när vi tar bort den från användargränssnittet uppmanas du att välja ett annat värde än ”Standard för enheten” nästa gång du redigerar profilen.
Vad kan jag göra för att förbereda mig för den här ändringen?
Granska lösenordsinställningarna för enhetsbegränsning och efterlevnadsprinciper för Android och Android enterprise. Du hittar dem under Systemsäkerhet för efterlevnadsprinciper och under antingen Enhetslösenord eller Arbetsprofilinställningar för enhetsbegränsningar. Under Ytterligare information finns en länk till mer information och skärmdumpar som visar var du gör de här inställningarna.
#### <a name="additional-information"></a>Ytterligare information
https://aka.ms/PasswordSettings 

