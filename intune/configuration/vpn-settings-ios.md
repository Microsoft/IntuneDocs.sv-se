---
title: Konfigurera VPN-inställningar för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa en VPN-konfigurationsprofil med hjälp av konfigurationsinställningar för virtuella privata nätverk (VPN), inklusive anslutningsinformation, autentiseringsmetoder och delade tunnlar i de grundläggande inställningarna. Visa även de anpassade VPN-inställningarna med identifieraren och nyckel-värdeparen. Det är även möjligt att visa VPN-inställningarna per app som inkluderar Safari-webbadresser och VPN-anslutningar på begäran med SSID- eller DNS-sökningsdomäner samt proxyinställningar för att inkludera ett konfigurationsskript, en IP- eller FQDN-adress och en TCP-port i Microsoft Intune på iOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d7b831899a740e722560c509c4b09c31d2a42b
ms.sourcegitcommit: 8c25aeefb7cbc6444a8596af22fccd1c5426877a
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72593792"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Lägg till VPN-inställningar på iOS-enheter i Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune innehåller många VPN-inställningar som kan distribueras till iOS-enheter. De här inställningarna används för att skapa och konfigurera VPN-anslutningar till din organisations nätverk. Den här artikeln beskriver dessa inställningar. Vissa inställningar är bara tillgängliga för vissa VPN-klienter, till exempel Citrix och Zscaler.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](vpn-settings-configure.md).

> [!NOTE]
> De här inställningarna är tillgängliga för alla registrerings typer. Mer information om registrerings typerna finns i [iOS-registrering](../enrollment/ios-enroll.md).

## <a name="connection-type"></a>Anslutningstyp

Välj VPN-anslutningstypen från följande leverantörslista:

- **Check Point Capsule VPN**
- **Cisco Legacy AnyConnect VPN**: Gäller för [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924)-appversion 4.0.5x och tidigare.
- **Cisco AnyConnect**: Gäller för [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690)-appversion 4.0.7x och senare.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: Gäller för F5 Access-appversion 2.1 och tidigare.
- **F5 Access**: Gäller för F5 Access-appversion 3.0 och senare.
- **Palo Alto Networks GlobalProtect (Legacy)** : Gäller för Palo Alto Networks GlobalProtect-appversion 4.1 och tidigare.
- **Palo Alto Networks GlobalProtect**: Gäller för Palo Alto Networks GlobalProtect-appversion 5.0 och tidigare.
- **Pulse Secure**
- **Cisco (IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: Om du vill använda Villkorsstyrd åtkomst eller tillåta att användarna hoppar över Zscaler-inloggningsskärmen måste du integrera Zscaler Private Access (ZPA) med ditt Azure AD-konto. Detaljerade anvisningar finns i [Zscaler-dokumentationen](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad). 
- **IKEv2**: [IKEv2-inställningar](#ikev2-settings) (i den här artikeln) beskriver egenskaperna.
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
  - **Certifikat**:Under **Autentiseringscertifikat** väljer du en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](../protect/certificates-configure.md) innehåller vägledning om certifikatprofiler.
  - **Användarnamn och lösenord**: Slutanvändare måste ange ett användarnamn och ett lösenord för att logga in på VPN-servern.  

    > [!NOTE]
    > Om användarnamnet och lösenordet används som autentiseringsmetod för Cisco IPsec VPN, måste de ge SharedSecret via en anpassad profil i Apple Configurator.

  - **Härledd autentiseringsuppgift**: om det inte har kon figurer ATS någon härledd Credential-utfärdare, så kommer Intune att fråga dig om detta.

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

## <a name="ikev2-settings"></a>IKEv2-inställningar

Dessa inställningar gäller när du väljer **Anslutnings typ**  > **IKEv2**.

- **Fjärridentifierare**: Ange NÄTVERKets IP-adress, FQDN, USERFQDN eller ASN1DN för IKEv2-servern. Ange till exempel `10.0.0.3` eller `vpn.contoso.com`. Normalt anger du samma värde som [**anslutnings namnet**](#base-vpn-settings) (i den här artikeln). Men det beror på inställningarna för IKEv2-servern.

- **Typ av klientautentisering**: Välj hur VPN-klienten autentiserar till VPN. Alternativen är:
  - **Användarautentisering** (standard): användarautentiseringsuppgifter autentiseras för VPN.
  - **Datorautentisering**: autentiseringsuppgifter för enhet autentiseras för VPN.

- **Autentiseringsmetod**: Välj den typ av klientautentiseringsuppgifter som ska skickas till servern. Alternativen är:
  - **Certifikat**: använder en befintlig certifikat profil för att AUTENTISERA till VPN. Se till att den här certifikat profilen redan har tilldelats till användaren eller enheten. Annars Miss lyckas VPN-anslutningen.
    - **Certifikat typ**: Välj den typ av kryptering som används av certifikatet. Se till att VPN-servern är konfigurerad för att godkänna den här typen av certifikat. Alternativen är:
      - **RSA** (standard)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - **Användar namn och lösen ord** (endast användarautentisering): när användare ansluter till VPN-nätverket uppmanas de att ange sitt användar namn och lösen ord.
  - **Delad hemlighet** (endast datorautentisering): gör att du kan ange en delad hemlighet att skicka till VPN-servern.
    - **Delad hemlighet**: Ange den delade hemligheten, även kallat PSK (i förväg delad nyckel). Se till att värdet matchar den delade hemlighet som kon figurer ATS på VPN-servern.

- **Server certifikat utfärdarens nätverks namn**: tillåter VPN-servern att autentisera till VPN-klienten. Ange certifikat utfärdarens nätverks namn (CN) för det VPN-servercertifikat som skickas till VPN-klienten på enheten. Se till att CN-värdet matchar konfigurationen på VPN-servern. Annars Miss lyckas VPN-anslutningen.
- **Server certifikatets nätverks namn**: Ange CN för själva certifikatet. Om inget värde anges används värdet för Fjärrvärdet.

- **Identifierings frekvens för döda peer**: Välj hur ofta VPN-klienten ska kontrol lera om VPN-tunneln är aktiv. Alternativen är:
  - **Inte konfigurerad**: använder standard systemet för iOS, vilket kan vara detsamma som att välja **medel**.
  - **Ingen**: inaktiverar utebliven peer-identifiering.
  - **Låg**: skickar ett keepalive-meddelande var 30: e minut.
  - **Medel** (standard): skickar ett keepalive-meddelande var tionde minut.
  - **Hög**: skickar ett keepalive-meddelande var 60 sekund.

- **Lägsta TLS-version intervall**: Ange den minsta TLS-version som ska användas. Ange `1.0`, `1.1` eller `1.2`. Om inget anges används standardvärdet `1.0`.
- **Högsta TLS-versions intervall**: Ange den högsta TLS-version som ska användas. Ange `1.0`, `1.1` eller `1.2`. Om inget anges används standardvärdet `1.2`.
- **Perfect Forward Secrecy**: Välj **Aktivera** för att aktivera PFS (Perfect Forward Secrecy). PFS är en funktion för IP-säkerhet som minskar påverkan om en sessionsnyckel komprometteras. **Disable** (standard) använder inte PFS.
- **Certifikat återkallnings kontroll**: Välj **Aktivera** för att kontrol lera att certifikaten inte återkallas innan du tillåter att VPN-anslutningen lyckas. Den här kontrollen är bästa möjliga. Om VPN-servern tar tid på innan du fastställer om certifikatet har återkallats beviljas åtkomst. **Disable** (standard) söker inte efter återkallade certifikat.

- **Konfigurera säkerhets Associations parametrar**: **inte konfigurerat** (standard) använder iOS-standardvärdet. Välj **Aktivera** för att ange de parametrar som används när du skapar säkerhets associationer med VPN-servern:
  - **Krypteringsalgoritm**: Välj den algoritm du vill använda:
    - DES
    - 3DES
    - AES-128
    - AES-256 (standard)
    - AES-128-GCM
    - AES-256-GCM
  - **Integritetsalgoritm**: Välj den algoritm du vill använda:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (standard)
    - SHA2-384
    - SHA2-512
  - **Diffie-Hellman-grupp**: Välj den grupp du vill använda. Standardvärdet är grupp `2`.
  - **Livs längd** (minuter): Välj hur länge säkerhets associationen ska förbli aktiv tills nycklarna roteras. Ange ett heltal mellan `10` och `1440` (1440 minuter är 24 timmar). Standardvärdet är `1440`.

- **Konfigurera en separat uppsättning parametrar för underordnade säkerhets associationer**: med iOS kan du konfigurera separata parametrar för IKE-anslutningen och eventuella underordnade anslutningar. 

  **Inte konfigurerad** (standard) använder de värden som du anger i den tidigare inställningen **Konfigurera säkerhets Associations parametrar** . Välj **Aktivera** för att ange de parametrar som används när du skapar *underordnade* säkerhets associationer med VPN-servern:
  - **Krypteringsalgoritm**: Välj den algoritm du vill använda:
    - DES
    - 3DES
    - AES-128
    - AES-256 (standard)
    - AES-128-GCM
    - AES-256-GCM
  - **Integritetsalgoritm**: Välj den algoritm du vill använda:
    - SHA1-96
    - SHA1-160
    - SHA2-256 (standard)
    - SHA2-384
    - SHA2-512
  - **Diffie-Hellman-grupp**: Välj den grupp du vill använda. Standardvärdet är grupp `2`.
  - **Livs längd** (minuter): Välj hur länge säkerhets associationen ska förbli aktiv tills nycklarna roteras. Ange ett heltal mellan `10` och `1440` (1440 minuter är 24 timmar). Standardvärdet är `1440`.

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

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Konfigurera VPN-inställningar på [Android](vpn-settings-android.md)-, [Android Enterprise](vpn-settings-android-enterprise.md)-, [MacOS](vpn-settings-macos.md)-och [Windows 10](vpn-settings-windows-10.md) -enheter.
