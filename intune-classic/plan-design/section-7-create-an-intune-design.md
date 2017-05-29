---
title: Skapa en Intune-utformning | Microsoft Docs
description: "Den här artikeln hjälper till att skapa en utformning för utformning och implementering av Microsoft Intune i molnet."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: b39076aad873b9e4d0a5e128a76b189ac0ec2008
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="create-an-intune-design"></a>Skapa en Intune-utformning

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Avsnittet i handledningen bör användas tillsammans med andra ämnen i avsnitt 2. Den här utformningen baseras på den information du samlar in och de beslut du fattar när du går igenom föregående avsnitt i denna handledning. I det här avsnittet om utformning koncentrerar vi oss på fristående Intune, som är en molnbaserad Microsoft-tjänst.

Även om kraven på lokal infrastruktur är minimala så arbeta med en utformningsplan, så att du är säker på att du har rätt lösning för mobil enhetshantering som uppfyller dina mål, delmål och krav.

Det är även vanligt att ändringar av utformningen sker under implementerings- och testfaserna, så tänk på att dokumentera dessa ändringar och orsaken till dem när de sker. Vi kommer att diskutera följande områden:

-   Den aktuella miljön

-   Intune-distributionsalternativ

-   Identitetskrav för externa beroenden

-   Överväganden för enhetsplattform

-   Krav som ska levereras  

Vi ska gå igenom dessa områden mer detaljerat. 

## <a name="record-your-environment"></a>Registrera miljön

Det första steget innan du kan skapa utformningen är att registrera den aktuella miljön. Den aktuella miljön kan påverka utformningsbeslut och bör dokumenteras och användas som referens när du fattar andra beslut om Intune-utformning. Här visas några exempel på hur du registrerar den aktuella miljön:

-   **Identitet i molnet**

    -   Använder du DirSync eller Azure Active Directory (AAD) Connect?

    -   Är miljön federerad?

    -   Har multifaktorautentisering aktiverats?

-   **E-postmiljö**

    -   Om Exchange används, är det lokalt eller i molnet?

    -   Befinner du dig mitt i ett projekt med att migrera Exchange till molnet?

-   **Aktuell MDM-lösning**

    -   Använder du andra MDM-lösningar för närvarande?

    -   Vilka MDM-lösningar använder du för företags- och BYOD-användningsfall?

    -   Vilka funktioner använder du (t.ex. appenhetsinställningar, Wi-Fi-konfigurationer osv.)?

    -   Vilka enhetsplattformar stöds?

    -   Vilka grupper och hur många användare använder MDM-lösningen?

-   **Certifikatlösning**

    -   Har du har implementerat en certifikatlösning?

    -   Vilken typ av certifikat använder du?

-   **Systemhantering**

    -   Hur hanterar du dator- och servermiljön?

    -   Används System Center Configuration Manager? Använder du en systemhanteringsplattform från tredje part?

-   **VPN-lösning**

    -   Vad har du för VPN-lösning?

    -   Används den för både företags- och BYOD-användningsfall?

Tänk på att notera eventuella projekt eller andra planer som finns som kan göra ändringar i miljön när du registrerar den befintliga MDM-miljön. Nedan visas ett exempel på ett sätt att registrera den aktuella miljön som kan vara till hjälp när du skapar Intune-utformningen:

| **Lösningsområde** | **Aktuell miljö** | **Kommentarer** |
|:---:|:---:|:---:|
| **Identitet** | Azure AD, Azure AD Connect, inte federerad, ingen MFA | Projekt på plats för att aktivera MFA vid årets slut |                 
| **E-postmiljö** | Exchange On-premises, Exchange Online | Migrerar för närvarande från Exchange On-premises till Exchange Online. 75 % av postlådorna har migrerats. Resterande 25 % kommer att migreras innan Intune-pilottestet påbörjas. |                
| **SharePoint** | Lokalt SharePoint | Inga planer på att övergå till SharePoint online |  
| **Nuvarande MDM** | Exchange ActiveSync |  |
| **Certifikatlösning** | Microsoft Server 2012 R2, AD Certificate Services | Använd endast PKI för webbplatsservrar |
| **Systemhantering** | System Center Configuration Manager CB 1606 | Vill undersöka Intune-hybridlösning |
| **VPN-lösning** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>Välj ett alternativ för Intune-distribution

Intune erbjuder två distributionsalternativ: fristående och hybrid. Du måste avgöra vilket som passar dina affärsbehov. Fristående avser Intune-tjänsten när den körs i molnet, hybrid avser integrering av Intune med System Center Configuration Manager.

- Läs mer om att [välja mellan Microsoft Intune fristående hantering och hybridhantering av mobila enheter med System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Plats för Intune-klient

Om organisationen har global närvaro måste du se till att planera var klienten kommer att finnas när den prenumererar på tjänsten. Landet definieras när du registrerar dig för en Intune-prenumeration första gången och mappas till områden världen över som anges nedan:

-   Nordamerika

-   Europa, Mellanöstern och Afrika

-   Asien och Stillahavsområdet

>[!IMPORTANT]
> Det går inte att ändra land/klientplats senare.

## <a name="external-dependencies"></a>Externa beroenden

Externa beroenden är tjänster och produkter som skiljer sig från Intune men som antingen är ett krav i Intune eller kan integreras med Intune. Det är viktigt att identifiera krav för eventuella externa beroenden och hur de ska konfigureras. Nedan visas några exempel på vanliga externa beroenden.

-   Identitet

-   Användar- och enhetsgrupper

-   PKI

Vi ska gå igenom dessa vanliga externa beroenden mer detaljerat nedan

### <a name="identity"></a>Identitet

Identiteten är det som används för att identifiera användarna som tillhör din organisation och som registrerar en enhet. Intune kräver Azure AD (Active Directory Azure) som leverantör av användaridentitet. Om du redan använder den här tjänsten kommer du att kunna använda din befintliga identitet som redan finns i molnet. Dessutom är Azure AD Connect det verktyg som rekommenderas för att synkronisera lokala användaridentiteter med Microsofts molntjänster. Om företaget redan använder Office 365 är det viktigt att Intune använder samma Azure Active Directory-miljö.

Du hittar mer information om Intunes identitetskrav nedan.

-   Läs mer om [identitetskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Läs mer om [katalogsynkroniseringskrav](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Läs mer om [krav för multifaktorautentisering](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

### <a name="user-and-device-groups"></a>Användar- och enhetsgrupper

Användar- och enhetsgrupper fastställer målet för en distribution. Detta kan omfatta distributionsinriktning för principer, program och profiler. Intune-molnet har endast stöd för användar- och enhetsgrupper, så du måste bestämma vilka användar- och enhetsgrupper som är obligatoriska. Vi rekommenderar att alla grupper skapas i Active Directory lokalt och sedan synkroniseras till Azure Active Directory. Du kan hitta mer information om planering och skapande av användar- och enhetsgrupper nedan.

-   Läs mer om att [planera användar- och enhetsgrupper](/intune-classic/deploy-use/plan-your-user-and-device-groups).

-   Läs om att [skapa användar- och enhetsgrupper](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

### <a name="public-key-infrastructure-pki"></a>Public Key Infrastructure (PKI)

Public Key Infrastructure tillhandahåller certifikat till enheter eller användare så att de på ett säkert sätt kan autentisera till en tjänst. Intune stöder en Microsoft PKI-infrastruktur. Enhets- och användarcertifikat kan utfärdas till en mobil enhet för att uppfylla kraven på certifikatbaserad autentisering. Innan du implementerar certifikat måste du fastställa om certifikat krävs, om nätverksinfrastrukturen har stöd för certifikatbaserad autentisering och om certifikat används för närvarande i den befintliga miljön.

Om du planerar att använda certifikat med VPN-, Wi-Fi- eller e-postprofiler med Intune måste du kontrollera att du har en [PKI-infrastruktur på plats](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles) som stöds och är redo att skapa och distribuera certifikatprofiler.

Dessutom måste du fastställa vilken server som ska vara värd för registreringstjänsten för nätverksenheter (NDES) och hur kommunikationen ska ske om SCEP-certifikat ska utfärdas.

Mer om att konfigurera certifikat i Intune:

-   [Konfigurera certifikatinfrastruktur för SCEP](/intune-classic/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Konfigurera certifikatinfrastruktur för PFX](/intune-classic/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Konfigurera certifikatprofiler för Intune](/intune-classic/deploy-use/configure-intune-certificate-profiles).

-   [Konfigurera resursåtkomstprinciper](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="device-platform-considerations"></a>Överväganden för enhetsplattform

Du behöver ta en närmare titt på enheterna för att förstå dem korrekt.

-   Fastställa enhetsplattformar som stöds

-   Egenskaper

-   Äganderätt till enhet

-   Massregistrering

Vi ska gå igenom dessa områden mer detaljerat.

### <a name="determine-supported-device-platforms"></a>Fastställa enhetsplattformar som stöds

Du behöver veta vilka enheter som kommer att finnas i miljön och bekräfta om de stöds av Intune eller inte när du skapar utformningen. Intune stöder iOS-, Android- och Windows-plattformar.

-   Läs mer om [enheter som stöds av Intune](/intune-classic/get-started/supported-mobile-devices-and-computers).

### <a name="devices"></a>Egenskaper

Intune hanterar mobila enheter för att skydda företagets data och gör att slutanvändarna kan arbeta från fler platser. Intune har stöd för flera enhetsplattformar, så vi rekommenderar att du dokumenterar de enheter och OS-plattformar som det kommer att finnas stöd för i organisationens utformning. Detta utökar de enheter och plattformar som skapades i avsnittet (krav för användningsfall).

Vi rekommenderar också att man känner till versionerna för att hänvisa till listan vid kontroll av enhetsfunktioner efter OS-plattform och version. Här är ett exempel:

| **Enhetsplattform** | **OS-versioner** |
|:---:|:---:|
| iOS – iPhone | 9.0+ |                
| iOS – iPad | 8.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10-surfplatta | 10+ |

### <a name="device-ownership"></a>Äganderätt till enhet

Intune har stöd för både företagsägda enheter och BYOD-ägande. En enhet betraktas som företagsägd om den registreras av en hanterare av enhetsregistrering eller ett enhetsregistreringsprogram. En enhet kan till exempel registreras via Apple DEP, markeras som företagsenhet och placeras i en enhetsgrupp som tar emot inriktade företagsprinciper och appar.

Se [Avsnitt 3: Fastställa krav för användningsfall](section-3-determine-use-case-requirements.md) om du vill veta mer om företags- och BYOD-användningsfall.

### <a name="bulk-enrollment"></a>Massregistrering

Det finns flera registreringsalternativ för att registrera en enhet i Intune som kompletterar självbetjäningsregistreringen via företagsportalen. Massregistrering kan utföras på olika sätt beroende på plattformen. Om massregistrering krävs måste du först fastställa metod för massregistrering och sedan inkludera den i utformningen. Hitta mer information om olika metoder för massregistrering nedan.

-   Läs mer om [massregistrering](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune).

## <a name="feature-requirements"></a>Funktionskrav

I de här avsnitten ska vi granska följande funktioner och egenskaper som är anpassade till dina krav för användningsfall:

-   Principer för allmänna villkor

-   Konfigurationsprinciper

-   Resursprofiler

-   Appar

-   Efterlevnadsprincip

-   Villkorlig åtkomst

Vi ska gå igenom dessa områden mer detaljerat.

### <a name="terms-and-conditions-policies"></a>Principer för villkor

Villkor kan användas för att beskriva principer eller villkor som slutanvändaren måste godkänna före registrering. Intune har stöd för möjligheten att lägga till och distribuera flera villkorsprinciper till användargrupper. Du måste avgöra om villkorsprinciper behövs. I så fall måste du avgöra vem som ansvarar för att tillhandahålla den här informationen i organisationen.

-   Läs om att [skapa principer för villkor](/intune-classic/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) i Intune. Ett exempel på hur du kan dokumentera principen för villkor visas nedan.

| **Namn på villkor** | **Användningsfall** | **Målgrupp** |
|:---:|:---:|:---:|
| Företagets allmänna villkor | Företag | Företagsanvändare |                 
| Allmänna villkor för BYOD | BYOD | BYOD-användare |                

### <a name="configuration-policies"></a>Konfigurationsprinciper

Konfigurationsprinciper används för att hantera säkerhetsinställningar och -funktioner på en enhet. När du utformar konfigurationsprinciperna kan du se avsnittet om krav för användningsfall för att fastställa de konfigurationer som krävs för Intune-enheter. Dokumentera inställningarna och hur de ska konfigureras och dokumentera även vilka användar- eller enhetsgrupper de ska riktas in på.

Du bör skapa minst en konfigurationsprincip per plattform. Du kan skapa flera konfigurationsprinciper per plattform om det behövs. Nedan visas ett exempel på utformning av fyra olika konfigurationsprinciper för olika plattformar och användningsfall.

| **Principnamn** | **Enhetsplattform** | **Inställningar** | **Målgrupp** |   
|:---:|:---:|:---:|:---:|
| Företag – iOS | iOS | PIN-kod krävs, längd: 6, begränsa säkerhetskopiering i molnet | Företagsenheter |                                                           
| Företag – Android | Android | PIN-kod krävs, längd: 6, begränsa säkerhetskopiering i molnet | Företagsenheter |                                                           
| BYOD – iOS  | iOS | PIN-kod krävs, längd: 4 | BYOD-enheter |
| BYOD – Android  | Android | PIN-kod krävs, längd: 4 | BYOD-enheter |

### <a name="profiles"></a>Profiler

Profiler används för att hjälpa slutanvändaren att ansluta till företagsdata. Intune stöder många typer av profiler. Se användningsfallen och kraven för att fastställa när [profilerna](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune) ska konfigureras. Alla enhetsprofiler kategoriseras per plattformstyp och ska tas med i den tekniska dokumentationen.

-   Certifikatprofiler

-   Wi-Fi-profil

-   VPN-profil

-   E-postprofil

Vi ska gå igenom varje profiltyp mer detaljerat.

##### <a name="certificate-profiles"></a>Certifikatprofiler

Certifikatprofiler gör det möjligt för Intune för att utfärda certifikat till en användare eller enhet. Intune har stöd för följande:

-   Simple Certificate Enrollment Protocol (SCEP)

-   Betrott rotcertifikat

-   PFX-certifikat.

Vi rekommenderar att du dokumenterar vilken användargrupp som behöver ett certifikat, hur många certifikatprofiler som krävs och vilka användargrupper de ska distribueras till.

>[!NOTE]
> Kom ihåg att det betrodda rotcertifikatet krävs för SCEP-certifikatet, så se till att alla användare som är mål för SCEP-certifikatet även får ett betrott rotcertifikat. Om SCEP-certifikat krävs ska du utforma och dokumentera vilka SCEP-certifikatmallar som krävs.

Följande är ett exempel på hur du kan dokumentera certifikaten under utformningen:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Rotcertifikatutfärdare | Företagets rotcertifikatutfärdare | Android, iOS, Windows Mobile | Företag, BYOD  |                                                           
| SCEP | Användarcertifikat | Android, iOS, Windows Mobile | Företag, BYOD |                                                           

##### <a name="wi-fi-profile"></a>Wi-Fi-profil

Wi-Fi-profiler används för att ansluta en mobil enhet till ett trådlöst nätverk automatiskt. Intune har stöd för distribution av Wi-Fi-profiler till alla plattformar som stöds.

-   Läs mer om [Intunes stöd för Wi-Fi-profiler.]/intune-classic/deploy-use/wi-fi-connections-in-microsoft-intune)

Nedan visas ett exempel på en utformning för en Wi-Fi-profil:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Wi-Fi-profil | Android | Företag, BYOD regionen Asien|                                                           
| Wi-Fi | Nordamerika Wi-Fi-profil | Android, iOS, Windows 10 Mobile | Företag, BYOD regionen Nordamerika |                                                           

##### <a name="vpn-profile"></a>VPN-profil

Med VPN-profiler kan användarna få säker åtkomst till nätverket från fjärrplatser. Intune har stöd för VPN-profiler från interna mobila VPN-anslutningar och tredjepartsleverantörer.

-   Läs mer om [VPN-profiler och leverantörer som stöds av Intune](/intune-classic/deploy-use/vpn-connections-in-microsoft-intune).

Nedan visas ett exempel på dokumentering av utformningen av en VPN-profil.

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco, valfri anslutningsprofil | Android, iOS, Windows 10 Mobile | Företag, BYOD Nordamerika och Tyskland|                                                           
| VPN | Pulse Secure | Android | Företag, BYOD regionen Asien |                                                           

##### <a name="email-profile"></a>E-postprofil

Med e-postprofiler kan en e-postklient konfigureras automatiskt med anslutningsinformation och ställa in e-postkonfiguration. Intune har stöd för e-postprofiler på vissa enheter.

-   Läs mer om [e-postprofiler](/intune-classic/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) och vilka plattformar som stöds.

Nedan visas ett exempel på dokumentering av utformningen av e-postprofiler:

| **Typ** | **Profilnamn** | **Enhetsplattform** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| E-postprofil | E-postprofil för iOS | iOS | Företag – informationsarbetare BYOD |                                                           
| E-postprofil | Android Knox e-postprofil | Android Knox | BYOD |

### <a name="apps"></a>Appar

Intune har stöd för leverans av appar till användare eller enheter på flera olika sätt. Den typ av program som kan levereras kan vara appar för programinstallation, appar från en offentlig appbutik, externa länkar eller hanterade iOS-appar. Förutom distribution av enskilda appar kan även volyminköpta appar hanteras och distribueras via volyminköpsprogrammen för iOS och Windows. Nedan finns mer information om hur Intune stöder appar och volyminköpsprogram.

-   Läs mer om [typer av appar](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune)

-   Läs mer om [iOS-volyminköpsprogrammet för företag /intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)).

-   Läs mer om [Windows Store för företag](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

#### <a name="app-type-requirements"></a>Krav på apptyper

Eftersom appar kan distribueras till användare och enheter rekommenderar vi att du bestämmer vilka program som ska hanteras av Intune. Försök att besvara följande frågor när du skapar listan:

-   Behöver apparna integrera med molntjänster?

-   Kommer alla program vara tillgängliga för BYOD-användare?

-   Vilka är de tillgängliga distributionsalternativen för dessa appar?

-   Behöver företaget ge sina partner åtkomst till data för SaaS-appar (Software as a service)?

-   Behöver apparna Internetåtkomst från användarnas enheter?

-   Är apparna allmänt tillgängliga i en appbutik eller är de anpassade branschspecifika appar?


>[!TIP]
> Ta en titt på de [olika typer av program som Intune har stöd för](/intune-classic/deploy-use/add-apps).

#### <a name="app-protection-policies"></a>Appskyddsprinciper

Appskyddsprinciper minimerar dataförlust genom att definiera hur programmet hanterar företagsdata. Intune har stöd för appskyddsprinciper för alla program som är skapade för att fungera med hantering av mobilappar. När du utformar appskyddsprincipen måste du fastställa vilka begränsningar du vill ha för företagsdata i en viss app. Vi rekommenderar att du läser om hur [appskyddsprinciper](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) fungerar. Nedan visas ett exempel på hur du dokumenterar befintliga program och vilka skydd som krävs.

| **Program** | **Syfte** | **Plattformar** | **Användningsfall** | **Appskyddsprincip** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Tillgänglig | iOS | Företag – chefer | Får inte vara be jailbrokad, kryptera filer |                                                         
| Word | Tillgänglig | iOS, Android – Samsung Knox, inte Knox, Windows 10 Mobile | Företag, BYOD | Får inte vara be jailbrokad, kryptera filer |                                                         

#### <a name="compliance-policies"></a>Efterlevnadsprinciper

Efterlevnadsprinciper fastställer om en enhet uppfyller vissa krav. Intune använder efterlevnadsprinciper för att avgöra om en enhet anses vara kompatibel eller icke-kompatibel. Kompatibilitetsstatus kan sedan användas för att begränsa åtkomsten till företagsresurser. Om villkorlig åtkomst krävs rekommenderar vi att du utformar en [enhetsefterlevnadsprincip](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Se kraven och användningsfallen för att fastställa hur många efterlevnadsprinciper som krävs och vilka användargrupper som är målgrupper. Du måste även fastställa hur länge en enhet kan vara offline utan att checka in innan den anses vara ej kompatibel.

Nedan visas ett exempel på hur du utformar en efterlevnadsprincip:

| **Principnamn** | **Enhetsplattform** | **Inställningar** | **Målgrupp** |   
|:---:|:---:|:---:|:---:|
| Policy för efterlevnad | iOS, Android – Samsung Knox, inte Knox, Windows 10 Mobile | PIN-kod – krävs, får inte vara jailbrokad | Företag, BYOD |

#### <a name="conditional-access-policies"></a>Villkorliga åtkomstprinciper

Villkorlig åtkomst används för att endast tillåta att kompatibla enheter får åtkomst till företagets resurser. Intune fungerar med hela Enterprise Mobility + Security (EMS) för att styra åtkomst till företagets resurser. Du måste avgöra om villkorlig åtkomst är obligatorisk och vad som måste skyddas.

-   Läs mer om [villkorlig åtkomst](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

Vid onlineåtkomst fastställer du vilka plattformar och användargrupper som du riktar in villkorliga åtkomstprinciper på.

Du måste även fastställa om du behöver installera/konfigurera Intune Service-to-Service Connector för Exchange Online eller Exchange On-premises.

Läs mer om att installera och konfigurera Intune Service-to-Service Connector:

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange On-premises](/intune-classic/deploy-use/intune-on-premises-exchange-connector)

Här visas ett exempel på hur du kan dokumentera villkorliga åtkomstprinciper:

| **Tjänst** | **Plattformar för modern autentisering** | **Grundläggande autentisering** | **Användningsfall** |   
|:---:|:---:|:---:|:---:|
| Exchange online | iOS, Android | Blockera icke-kompatibla enheter på plattformar som stöds av Intune | Företag, BYOD |
| SharePoint Online | iOS, Android |  | Företag, BYOD |

## <a name="next-section"></a>Nästa avsnitt

Nästa avsnitt innehåller råd om [Intune-implementeringsprocessen](section-8-onboarding-process.md).

