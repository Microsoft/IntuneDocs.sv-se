---
title: Lägga till VPN-inställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en VPN-konfigurationsprofil med hjälp av konfigurationsinställningar för virtuella privata nätverk (VPN), inklusive anslutningsinformation, autentiseringsmetoder och delade tunnlar i de grundläggande inställningarna. Visa även de anpassade VPN-inställningarna med identifieraren och nyckel-värdeparen. Det är även möjligt att visa VPN-inställningarna per app som inkluderar Safari-webbadresser och VPN-anslutningar på begäran med SSID- eller DNS-sökningsdomäner samt proxyinställningar för att inkludera ett konfigurationsskript, en IP- eller FQDN-adress och en TCP-port i Microsoft Intune på iOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/25/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c40146f37ff6477663dc63468d1081a73ac2544a
ms.sourcegitcommit: dde4b8788e96563edeab63f612347fa222d8ced0
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65135161"
---
# <a name="configure-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Konfigurera VPN-inställningar på iOS-enheter i Microsoft Intune

Microsoft Intune innehåller många VPN-inställningar som kan distribueras till iOS-enheter. De här inställningarna används för att skapa och konfigurera VPN-anslutningar till din organisations nätverk. Den här artikeln beskriver dessa inställningar. Vissa inställningar är bara tillgängliga för vissa VPN-klienter, till exempel Citrix och Zscaler.

## <a name="connection-type"></a>Anslutningstyp

Välj VPN-anslutningstypen från följande leverantörslista:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect VPN**: Gäller för [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-appversion 4.0.5x och tidigare.
- **Cisco AnyConnect**: Gäller för [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-appversion 4.0.7x och senare.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: Gäller för F5 Access-appversion 2.1 och tidigare.
- **F5 Access**: Gäller för F5 Access-appversion 3.0 och senare.
- **Palo Alto Networks GlobalProtect (Legacy)**: Gäller för Palo Alto Networks GlobalProtect-appversion 4.1 och tidigare.
- **Palo Alto Networks GlobalProtect**: Gäller för Palo Alto Networks GlobalProtect-appversion 5.0 och tidigare.
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: Om du vill använda villkorsstyrd åtkomst eller tillåta att användarna hoppar över Zscaler-inloggningsskärmen måste du integrera Zscaler Private Access (ZPA) med ditt Azure AD-konto. Detaljerade anvisningar finns i [Zscaler-dokumentationen](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
- **Anpassat VPN**

> [!NOTE]
> Cisco, Citrix, F5 och Palo Alto har tillkännagivit att deras äldre klienter inte fungerar i iOS 12. Du bör migrera till de nya apparna så snart som möjligt. Mer information finns i [Microsoft Intune-supportteamets blogg](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar

De inställningar som visas i följande lista bestäms av den VPN-anslutningstyp som du väljer.  

- **Anslutningsnamn**: Slutanvändarna ser det här namnet när de bläddrar i en lista över tillgängliga VPN-anslutningar på enheten.
- **Anpassat domännamn** (endast Zscaler): Fyll i Zscaler-appens inloggningsfält på förhand med den domän som användarna tillhör. Om ett användarnamn exempelvis är `Joe@contoso.net`, kommer domänen `contoso.net` att visas statiskt i fältet när appen öppnas. Om du inte anger ett domännamn används domändelen av UPN-namnet i Azure Active Directory (AD).
- **IP-adress eller fullständigt domännamn**: IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel `192.168.1.1` eller `vpn.contoso.com`.
- **Organisationens molnnamn** (endast Zscaler): Ange namnet på det moln där din organisation har etablerats. URL:en som du använder för att logga in till Zscaler innehåller namnet.  
- **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. 
  - **Certifikat**:Under **Autentiseringscertifikat** väljer du en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) innehåller vägledning om certifikatprofiler.
  - **Användarnamn och lösenord**: Slutanvändare måste ange ett användarnamn och ett lösenord för att logga in på VPN-servern.  

    > [!NOTE]
    > Om användarnamnet och lösenordet används som autentiseringsmetod för Cisco IPsec VPN, måste de ge SharedSecret via en anpassad profil i Apple Configurator.

- **Undantagna webbadresser** (endast Zscaler): Vid anslutning till Zscaler VPN är de angivna webbadresserna tillgängliga utanför Zscaler-molnet. 

- **Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.

- **VPN-identifierare** (Anpassad VPN, Zscaler och Citrix): En identifierare för VPN-appen som du använder och som tillhandahålls av din VPN-leverantör.
  - **Ange nyckel/värdepar för organisationens anpassade VPN-attribut**: Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Glöm inte att dessa värden vanligtvis tillhandahålls av VPN-leverantören.

- **Aktivera nätverksåtkomstkontroll (NAC)** (Citrix SSO, F5-åtkomst): När du väljer **Jag godkänner** inkluderas enhetens ID i VPN-profilen. Detta ID kan användas för VPN-autentisering för att tillåta eller förhindra nätverksåtkomst.

  **När du använder F5-åtkomst** måste du se till att:

  - Bekräfta att du använder F5 BIG-IP 13.1.1.5. BIG-IP 14 inte stöds.
  - Integrera BIG-IP med Intune för NAC. Se F5-guiden [Overview: Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) (Översikt: Konfigurera APM för enhetsstatuskontroller med slutpunktshanteringssystem).
  - Aktivera NAC i VPN-profilen.

  **När du använder Citrix SSO med Gateway** så var noga med att:

  - Bekräfta att du använder Citrix Gateway 12.0.59 eller senare.
  - Bekräfta att dina användare har Citrix SSO 1.1.6 eller senare installerat på sina enheter.
  - Integrera Citrix Gateway med Intune för NAC. Se Citrix-distributionsguiden [Integrating Microsoft Intune/Enterprise Mobility Suite with NetScaler (LDAP+OTP Scenario)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) (Integrera Microsoft Intune/Enterprise Mobility Suite med NetScaler (LDAP+OTP-scenario)).
  - Aktivera NAC i VPN-profilen.

  **Viktig information**:  

  - När NAC har aktiverats kopplas VPN-anslutningen bort en gång per dygn. VPN-anslutningen kan omedelbart återanslutas.
  - Enhets-ID:t är en del av profilen, men det visas inte i Intune. Detta ID lagras inte av Microsoft någonstans, och det delas inte heller av Microsoft.

  Om enhets-ID:t stöds av VPN-partner kan VPN-klienten, till exempel Citrix SSO, hämta ID:t. Sedan kan den skicka en fråga till Intune för att bekräfta att enheten är registrerad, och om VPN-profilen är kompatibel eller inte.

  - Om du vill ta bort den här inställningen återskapar du profilen och markerar inte **Jag accepterar**. Tilldela sedan profilen på nytt.

## <a name="automatic-vpn-settings"></a>Inställningar för automatiskt VPN

- **Per app-VPN**: Gör det möjligt att använda VPN per app. Tillåter att VPN-anslutningen aktiveras automatiskt när vissa program öppnas. Associerar även appar med den här VPN-profilen. Om du vill ha mer information läser du [instruktionerna för hur du konfigurerar per app-VPN för iOS](vpn-setting-configure-per-app.md).
  - **Typ av provider**: Endast tillgängligt för Pulse Secure och anpassat VPN.
  - När du använder **per app-VPN-profiler** i iOS med Pulse Secure eller Anpassat VPN väljer du händelsedirigering nedåt på applager (app-proxy) eller på paketnivå (paket-tunnel). Ställ in värdet **Providertyp** på **app-proxy** för händelsedirigering på appnivå eller **paket-tunnel** för händelsedirigering på paketnivå. Om du inte är säker på vilket värde du ska använda läser du VPN-leverantörens dokumentation.
  - **Safari-webbadresser som utlöser denna VPN**: Lägg till en eller flera webbadresser. VPN-anslutningen upprättas automatiskt när de här webbadresserna besöks i Safari-webbläsaren på enheten.

- **VPN på begäran**: Konfigurera villkorliga regler som styr när VPN-anslutningen ska initieras. Du kan till exempel skapa ett villkor där VPN-anslutningen endast används när en enhet inte är ansluten till ett trådlöst företagsnätverk. Eller skapa ett villkor. Om en enhet till exempel inte kan komma åt en DNS-sökdomän som du har angett startas inte VPN-anslutningen.

  - **SSID:n eller DNS-sökdomäner**: Välj om det här villkoret ska använda det trådlösa nätverkets **SSID:n** eller **DNS-sökdomäner**. Välj **Lägg till** för att konfigurera en eller flera SSID:er eller sökdomäner.
  - **URL-strängavsökning**: Valfritt. Ange en URL som regeln använder som ett test. Om enheten med den här profilen kommer åt den här URL:en utan omdirigering, startas VPN-anslutningen. Och enheten ansluter till mål-URL:en. Användaren ser inte URL-strängens avsökningsplats. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att webbadressen testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till målwebbadressen via VPN.
  - **Domänåtgärd**: Välj något av följande:
    - Anslut vid behov
    - Anslut aldrig
  - **Åtgärd**: Välj något av följande:
    - Ansluta
    - Utvärdera anslutning
    - Ignorera
    - Koppla från

## <a name="proxy-settings"></a>Proxyinställningar

Konfigurera följande inställningar om du använder en proxyserver. Proxyinställningar är inte tillgängliga för Zscaler VPN-anslutningar.  

- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange den **Proxyserver-URL** (till exempel `http://proxy.contoso.com`) som innehåller konfigurationsfilen.
- **Adress**: Ange IP-adressen för det fullt kvalificerade värdnamnet för proxyservern.
- **Portnummer**: Ange det portnummer som är associerat med proxyservern.

## <a name="next-step"></a>Nästa steg
[Skapa VPN-profiler i Intune](vpn-settings-configure.md)  
