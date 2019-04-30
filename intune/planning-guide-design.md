---
title: Skapa din Microsoft Intune-design
titleSuffix: Microsoft Intune
description: Den här artikeln hjälper till att skapa en utformning för utformning och implementering av Microsoft Intune i molnet.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 307895935e1cd6fe2489a4ee8ae03333ce97d55b
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "61512727"
---
# <a name="create-a-design"></a>Skapa en design

Intune-designen baseras på den information du samlar in och de beslut du fattar när du går igenom övriga [avsnitt i den här guiden](planning-guide.md). Det hjälper dig att sammanföra:

-   Den aktuella miljön

-   Intune-distributionsalternativ

-   Identitetskrav för externa beroenden

-   Överväganden för enhetsplattform

-   Krav som ska levereras  

Även om kraven på lokal infrastruktur är minimala kan en utformningsplan hjälpa dig att se till att du har rätt lösning för mobil enhetshantering som uppfyller dina mål, delmål och krav.

Vi ska gå igenom dessa områden mer detaljerat. 

## <a name="record-your-current-environment"></a>Registrera din aktuella miljö
Det är dessutom vanligt att det sker utformningsändringar under implementerings- och testfaserna. Använd utformningsplanen för att dokumentera dessa ändringar och tanken bakom dem när de sker.

Den aktuella miljön kan påverka utformningsbeslut och bör dokumenteras och användas som referens när du fattar andra beslut om Intune-utformning. Här visas några exempel på hur du registrerar den aktuella miljön:

-   **Identitet i molnet**

    -   Använder du DirSync eller Azure Active Directory (Azure AAD) Connect?

    -   Är miljön federerad?

    -   Är multifaktorautentisering (MFA) aktiverad?

-   **E-postmiljö**

    -   Använder du Exchange? Är det lokalt eller i molnet?

    -   Befinner du dig mitt i ett projekt med att migrera Exchange till molnet?

-   **Aktuell lösning för hantering av mobilenheter (MDM)**

    -   Använder du andra MDM-lösningar för närvarande?

    -   Vilka MDM-lösningar använder du för företags- och BYOD-användningsfall?

    -   Vilka funktioner använder du (t.ex. appenhetsinställningar, Wi-Fi-konfigurationer)?

    -   Vilka enhetsplattformar stöds?

    -   Vilka grupper och hur många användare använder MDM-lösningen?

-   **Certifikatlösning**

    -   Har du har implementerat en certifikatlösning?

    -   Vilken typ av certifikat använder du?

-   **Systemhantering**

    -   Hur hanterar du dator- och servermiljön?

    -   Använder du System Center Configuration Manager? Använder du en systemhanteringsplattform från tredje part?

-   **VPN-lösning**

    -   Vad har du för VPN-lösning?

    -   Använder du den för både företags- och BYOD-användningsfall?

Tänk på att notera eventuella projekt eller andra planer som finns som kan påverka miljön när du registrerar den befintliga MDM-miljön. Nedan visas ett exempel på ett sätt att registrera den aktuella miljön när du skapar Intune-utformningen:

| **Lösningsområde** | **Aktuell miljö** | **Kommentarer** |
|---|---|---|
| **Identitet** | Azure AD, Azure AD Connect, inte federerad, ingen MFA | Projekt på plats för att aktivera MFA vid årets slut |                 
| **E-postmiljö** | Exchange On-premises, Exchange Online | Migrerar för närvarande från Exchange On-premises till Exchange Online. 75 % av postlådorna har migrerats. Resterande 25 % kommer att migreras innan Intune-pilottestet påbörjas. |                
| **SharePoint** | Lokalt SharePoint | Inga planer på att övergå till SharePoint online |  
| **Nuvarande MDM** | Exchange ActiveSync |  |
| **Certifikatlösning** | Microsoft Server 2012 R2, AD Certificate Services | Använd endast PKI för webbplatsservrar |
| **Systemhantering** | System Center Configuration Manager CB 1606 | Vill undersöka Intune-hybridlösning |
| **VPN-lösning** | Cisco AnyConnect |  |


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att utveckla din utformningsplan för Intune.

## <a name="choose-an-intune-deployment-option"></a>Välj ett alternativ för Intune-distribution

Intune erbjuder två distributionsalternativ: fristående och hybrid. Fristående avser den Intune-tjänst som körs i molnet. Hybrid avser integreringen av Intune med System Center Configuration Manager. Den här guiden är främst avsedd att användas med det fristående alternativet. [Bestäm vilket alternativ som passar dina affärsbehov](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

> [!Important]
>Registrering av nya hybrid-MDM-kunder är nu inaktuell. Mer information finns i blogginlägget [Flytt från hybridhantering av mobilenheter till Intune i Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).


## <a name="intune-tenant-location"></a>Plats för Intune-klient

Om organisationen har global närvaro måste du se till att planera var klienten ska finnas när du prenumererar på tjänsten. Landet definieras när du registrerar dig för en Intune-prenumeration första gången och mappas till områden världen över som anges nedan:

-   Nordamerika

-   Europa, Mellanöstern och Afrika

-   Asien och Stillahavsområdet

>[!IMPORTANT]
> Det går inte att ändra land eller klientplats senare.

## <a name="external-dependencies"></a>Externa beroenden

Externa beroenden är tjänster och produkter som skiljer sig från Intune men som antingen är ett krav i Intune eller kan integreras med Intune. Det är viktigt att identifiera krav för eventuella externa beroenden och hur de ska konfigureras. Några exempel på vanliga externa beroenden är:

-   Identitet

-   Användar- och enhetsgrupper

-   Public Key Infrastructure (PKI)

Nedan utforskar vi de här vanliga externa beroendena närmare.

### <a name="identity"></a>Identitet

Identiteten är det som används för att identifiera användarna som tillhör din organisation och som registrerar en enhet. Intune kräver Azure AD (Active Directory Azure) som leverantör av användaridentitet. Om du redan använder den här tjänsten kan du använda din befintliga identitet som redan finns i molnet. Dessutom är Azure AD Connect det verktyg som rekommenderas för att synkronisera lokala användaridentiteter med Microsofts molntjänster. Om företaget redan använder Office 365 är det viktigt att Intune använder samma Azure AD-miljö.

Läs mer om följande identitetskrav för Intune:

- [Identitetskrav](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [Katalogsynkroniseringskrav](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [Multifaktorautentiseringskrav](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Användar- och enhetsgrupper

Användar- och enhetsgrupper fastställer målet för en distribution, inklusive principer, program och profiler. Du måste bestämma vilka användar- och enhetsgrupper som krävs.

Vi rekommenderar att du skapar alla grupper i Active Directory lokalt och sedan synkroniserar till Azure AD. Läs mer om att planera och skapa användar- och enhetsgrupper:

-   [Planera dina användar- och enhetsgrupper](users-add.md).

-   [Skapa användar- och enhetsgrupper](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Public Key Infrastructure (PKI)
Public Key Infrastructure tillhandahåller certifikat till enheter eller användare så att de på ett säkert sätt kan autentisera till en tjänst. Intune stöder en Microsoft PKI-infrastruktur. Enhets- och användarcertifikat kan utfärdas till en mobil enhet för att uppfylla kraven på certifikatbaserad autentisering. Innan du använder certifikat måste du fastställa om de behövs, om nätverksinfrastrukturen har stöd för certifikatbaserad autentisering och om certifikat används för närvarande i den befintliga miljön.

Om du planerar att använda certifikat med VPN-, Wi-Fi- eller e-postprofiler med Intune kontrollerar du att du har en [PKI-infrastruktur på plats](certificates-configure.md) som stöds och är redo att skapa och distribuera certifikatprofiler.

Dessutom måste du fastställa vilken server som ska vara värd för registreringstjänsten för nätverksenheter (NDES) och hur kommunikationen ska ske om SCEP-certifikat ska utfärdas.

Läs mer om:

-   [Konfigurera certifikatprofiler för Intune](certificates-configure.md)

-   [Konfigurera certifikatinfrastrukturen för SCEP](certificates-scep-configure.md)

-   [Konfigurera certifikatinfrastruktur för PFX](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Överväganden för enhetsplattform

Ta en närmare titt på följande aspekter av enheterna att förstå hur de ska hanteras korrekt.

-   Enhetsplattformar som stöds

-   Egenskaper

-   Äganderätt till enhet

-   Massregistrering

Vi ska gå igenom dessa områden mer detaljerat.

### <a name="determine-supported-device-platforms"></a>Fastställa enhetsplattformar som stöds

Du behöver veta vilka enheter som kommer att finnas i miljön och bekräfta om de stöds av Intune eller inte när du skapar utformningen. Intune stöder iOS-, Android- och Windows-plattformar.

[Fullständig lista över Intune-enheter som stöds](supported-devices-browsers.md).

### <a name="devices"></a>Egenskaper

Intune hanterar mobila enheter för att skydda företagets data och gör att slutanvändarna kan arbeta från fler platser. Intune har stöd för många enhetsplattformar, så vi rekommenderar att du dokumenterar de enheter, OS-plattformar och versioner som det kommer att finnas stöd för i organisationens utformning. Exempel:

| **Enhetsplattform** | **OS-versioner** |
|:---:|:---:|
| iOS – iPhone | 10.0 + |                
| iOS – iPad | 10.0 + |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10-surfplatta | 10+ |


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att utveckla din lista över enheter.
### <a name="device-ownership"></a>Äganderätt till enhet

Intune stöder både företagsägda enheter och personliga enheter. En enhet betraktas som företagsägd om du registrerar den med en hanterare av enhetsregistrering eller ett enhetsregistreringsprogram. En enhet registreras till exempel via Apples program för enhetsregistrering (DEP), markeras som företagsenhet och placeras i en enhetsgrupp som tar emot inriktade företagsprinciper och appar.

Se [Avsnitt 3: Fastställa krav för användningsfall](planning-guide-requirements.md) om du vill veta mer om företags- och BYOD-användningsfall.

### <a name="bulk-enrollment"></a>Massregistrering

 Du kan massregistrera enheter på olika sätt beroende på plattform. Om massregistrering krävs måste du först [fastställa metod för massregistrering](device-enrollment.md) och sedan inkludera den i utformningen.

## <a name="feature-requirements"></a>Funktionskrav

I de här avsnitten ska vi granska följande funktioner och egenskaper som är anpassade till dina krav för användningsfall:

-   Principer för allmänna villkor

-   Konfigurationsprinciper

-   Resursprofiler

-   Appar

-   Policy för efterlevnad

-   Villkorlig åtkomst

Vi ska gå igenom dessa områden mer detaljerat.

### <a name="terms-and-conditions-policies"></a>Principer för allmänna villkor

Du kan använda [allmänna villkor](terms-and-conditions-create.md) för att förklara principer eller villkor som en användare måste godkänna innan dennes enhet kan registreras. Intune har stöd för möjligheten att lägga till och distribuera flera villkorsprinciper till användargrupper.

Du måste avgöra om villkorsprinciper behövs. I så fall måste du avgöra vem som ansvarar för att tillhandahålla den här informationen i organisationen. Ett exempel på hur du kan dokumentera principen för villkor visas nedan.

| **Namn på villkor** | **Användningsfall** | **Målgrupp** |
|:---:|:---:|:---:|
| Företagets allmänna villkor | Företag | Företagsanvändare |                 
| Allmänna villkor för BYOD | BYOD | BYOD-användare |                


Du kan [hämta en mall i tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att mappa villkoren till användargrupperna.

### <a name="configuration-policies"></a>Konfigurationsprinciper

Använd konfigurationsprinciper för att hantera säkerhetsinställningar och -funktioner på en enhet. När du utformar konfigurationsprinciperna kan du se avsnittet om krav för användningsfall för att fastställa de konfigurationer som krävs för Intune-enheter. Dokumentera inställningarna och hur de ska konfigureras. Dokumentera även vilka användar- eller enhetsgrupper som de ska tillämpas på.

Du bör skapa minst en konfigurationsprincip per plattform. Du kan skapa flera konfigurationsprinciper per plattform om det behövs. Nedan visas ett exempel på utformning av fyra olika konfigurationsprinciper för olika plattformar och användningsfall.

| **Principnamn** | **Enhetsplattform** | **Inställningar** | **Målgrupp** |   
|:---:|:---:|:---:|:---:|
| Företag – iOS | iOS | PIN-kod krävs, längd: 6, Begränsa molnsäkerhetskopiering | Företagsenheter |                                                           
| Företag – Android | Android | PIN-kod krävs, längd: 6, Begränsa molnsäkerhetskopiering | Företagsenheter |                                                           
| BYOD – iOS  | iOS | PIN-kod krävs, längd: 4 | BYOD-enheter |
| BYOD – Android  | Android | PIN-kod krävs, längd: 4 | BYOD-enheter |


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för konfigurationsprincipen.

### <a name="profiles"></a>Profiler

Använd profiler för att hjälpa slutanvändaren att ansluta till företagsdata. Intune stöder många typer av profiler. Se användningsfallen och kraven för att fastställa när profilerna ska konfigureras. Alla enhetsprofiler kategoriseras efter plattformstyp och ska tas med i den tekniska dokumentationen.

-   Certifikatprofiler

-   Wi-Fi-profil

-   VPN-profil

-   E-postprofil

Vi ska gå igenom varje profiltyp mer detaljerat.

#### <a name="certificate-profiles"></a>Certifikatprofiler

Certifikatprofiler gör det möjligt för Intune för att utfärda certifikat till en användare eller enhet. Intune har stöd för följande:

-   Simple Certificate Enrollment Protocol (SCEP)

-   Betrott rotcertifikat

-   PFX-certifikat.

Vi rekommenderar att du dokumenterar vilken användargrupp som behöver ett certifikat, hur många certifikatprofiler som krävs och vilka användargrupper de ska distribueras till.

>[!NOTE]
> Kom ihåg att det betrodda rotcertifikatet krävs för SCEP-certifikatet, så se till att alla användare som är mål för SCEP-certifikatet även får ett betrott rotcertifikat. Om du behöver SCEP-certifikat ska du utforma och dokumentera vilka SCEP-certifikatmallar som krävs.

Följande är ett exempel på hur du kan dokumentera certifikaten under utformningen:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Rotcertifikatutfärdare | Företagets rotcertifikatutfärdare | Android, iOS, Windows Mobile | Företag, BYOD  |                                                           
| SCEP | Användarcertifikat | Android, iOS, Windows Mobile | Företag, BYOD |                                                           


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för certifikatprofilen.

#### <a name="wi-fi-profile"></a>Wi-Fi-profil

Wi-Fi-profiler används för att ansluta en mobil enhet till ett trådlöst nätverk automatiskt. Intune har stöd för distribution av Wi-Fi-profiler till alla plattformar som stöds. Läs mer om [hur Intune stöder Wi-Fi-profiler.](wi-fi-settings-configure.md)

Nedan visas ett exempel på en utformning för en Wi-Fi-profil:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Wi-Fi-profil | Android | Företag, BYOD regionen Asien|                                                           
| Wi-Fi | Nordamerika Wi-Fi-profil | Android, iOS, Windows 10 Mobile | Företag, BYOD regionen Nordamerika |                                                           


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för Wi-Fi-profilen.

#### <a name="vpn-profile"></a>VPN-profil

Med VPN-profiler kan användarna få säker åtkomst till nätverket från fjärrplatser. Intune har stöd för VPN-profiler från interna mobila VPN-anslutningar och tredjepartsleverantörer. Läs mer om [VPN-profiler och leverantörer som stöds av Intune](vpn-settings-configure.md).

Nedan visas ett exempel på dokumentering av utformningen av en VPN-profil.

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco, valfri anslutningsprofil | Android, iOS, Windows 10 Mobile | Företag, BYOD Nordamerika och Tyskland|                                                           
| VPN | Pulse Secure | Android | Företag, BYOD regionen Asien |                                                           


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för VPN-profilen.
#### <a name="email-profile"></a>E-postprofil

Med e-postprofiler kan en e-postklient konfigureras automatiskt med anslutningsinformation och e-postkonfiguration. Intune har stöd för e-postprofiler på vissa enheter. Läs mer om [e-postprofiler och vilka plattformar som stöds](email-settings-configure.md).

Nedan visas ett exempel på dokumentering av utformningen av e-postprofiler:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| E-postprofil | E-postprofil för iOS | iOS | Företag – informationsarbetare BYOD |                                                           
| E-postprofil | Android Knox e-postprofil | Android Knox | BYOD |


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för e-postprofilen.
### <a name="apps"></a>Appar

Du kan använda Intune för att leverera appar till användare eller enheter på flera sätt. Programtypen kan vara appar för programinstallation, appar från en offentlig appbutik, externa länkar eller hanterade iOS-appar. Förutom distribution av enskilda appar kan du hantera och distribuera volyminköpta appar som har köpts via volyminköpsprogrammen för iOS och Windows. Läs mer om:

-   [Apptyperna som du kan leverera](app-management.md)

-   [iOS volyminköpsprogram för företag (VPP)](vpp-apps-ios.md)

-   [Microsoft Store för företag-appar](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Krav på apptyper

Eftersom appar kan distribueras till användare och enheter rekommenderar vi att du bestämmer vilka program som ska hanteras av Intune. Försök att besvara följande frågor när du skapar listan:

-   Behöver apparna integrera med molntjänster?

-   Kommer alla program vara tillgängliga för BYOD-användare?

-   Vilka är de tillgängliga distributionsalternativen för dessa appar?

-   Behöver företaget ge sina partner åtkomst till data för SaaS-appar (Software as a service)?

-   Behöver apparna Internetåtkomst från användarnas enheter?

-   Är apparna allmänt tillgängliga i en appbutik eller är de anpassade verksamhetsspecifika appar (LOB)?


#### <a name="app-protection-policies"></a>Appskyddsprinciper

Appskyddsprinciper minimerar dataförlust genom att definiera hur programmet hanterar företagsdata. Intune har stöd för appskyddsprinciper för alla program som är skapade för att fungera med hantering av mobilappar. När du utformar appskyddsprincipen måste du fastställa vilka begränsningar du vill ha för företagsdata i en viss app. Vi rekommenderar att du läser om hur [appskyddsprinciper](app-protection-policy.md) fungerar. Nedan visas ett exempel på hur du dokumenterar befintliga program och vilka skydd som krävs.

| **Program** | **Syfte** | **Plattformar** | **Användningsfall** | **Appskyddsprincip** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Tillgänglig | iOS | Företag – chefer | Får inte vara be jailbrokad, kryptera filer |                                                         
| Word | Tillgänglig | iOS, Android – Samsung Knox, inte Knox, Windows 10 Mobile | Företag, BYOD | Får inte vara be jailbrokad, kryptera filer |                                                         


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för appskyddsprincipen.
#### <a name="compliance-policies"></a>Efterlevnadsprinciper

Efterlevnadsprinciper fastställer om en enhet uppfyller vissa krav. Intune använder efterlevnadsprinciper för att avgöra om en enhet anses vara kompatibel eller icke-kompatibel. Kompatibilitetsstatus kan sedan användas för att begränsa eller tillåta åtkomst till företagsresurser. Om villkorlig åtkomst krävs rekommenderar vi att du utformar en [enhetsefterlevnadsprincip](device-compliance.md).

Se kraven och användningsfallen för att fastställa hur många efterlevnadsprinciper som krävs och vilka användargrupper som är målgrupper. Du måste även fastställa hur länge en enhet kan vara offline utan att checka in innan den anses vara ej kompatibel.

Nedan visas ett exempel på hur du utformar en efterlevnadsprincip:

| **Principnamn** | **Enhetsplattform** | **Inställningar** | **Målgrupp** |   
|:---:|:---:|:---:|:---:|
| Policy för efterlevnad | iOS, Android – Samsung Knox, inte Knox, Windows 10 Mobile | PIN-kod – krävs, får inte vara jailbrokad | Företag, BYOD |


Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för efterlevnadsprincipen.
#### <a name="conditional-access-policies"></a>Villkorliga åtkomstprinciper

Villkorlig åtkomst används för att endast tillåta att kompatibla enheter får åtkomst till e-post och andra företagsresurser. Intune fungerar med Enterprise Mobility + Security (EMS) för att styra åtkomst till företagets resurser. Avgör om du behöver villkorsstyrd och vad som måste skyddas. Läs mer om [villkorlig åtkomst](conditional-access.md).

Vid onlineåtkomst fastställer du vilka plattformar och användargrupper som du anger som mål för principer för villkorsstyrd åtkomst. Du behöver även fastställa huruvida du behöver installera eller konfigurera Intune-anslutningsappen för lokal Exchange: 

-   [Exchange On-premises](exchange-connector-install.md)

Här visas ett exempel på hur du kan dokumentera villkorliga åtkomstprinciper:

| **Tjänst** | **Plattformar för modern autentisering** | **Grundläggande autentisering** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Exchange online | iOS, Android | Blockera icke-kompatibla enheter på plattformar som stöds av Intune | Företag, BYOD |
| SharePoint Online | iOS, Android |  | Företag, BYOD |

Du kan [ladda ned en mall med tabellen ovan](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) för att identifiera behoven för principen för villkorlig åtkomst.

## <a name="next-steps"></a>Nästa steg

Nästa avsnitt innehåller råd om [Intune-implementeringsprocessen](planning-guide-onboarding.md).
