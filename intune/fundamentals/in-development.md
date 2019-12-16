---
title: Under utveckling – Microsoft Intune
titleSuffix: ''
description: Microsoft Intune-funktioner under utveckling
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74540728"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Under utveckling för Microsoft Intune – december 2019

För att hjälpa dig med förberedelser och planering innehåller den här sidan information om uppdateringar av och funktioner i användargränssnittet i Intune som är under utveckling, men som inte släppts än. Förutom informationen på den här sidan:

- Om vi tror att du behöver vidta åtgärder innan en ändring genomförs, publicerar vi ett extra inlägg i meddelandecentret för Office.
- När en funktion går in i produktion, oavsett om det är en för hands version eller är allmänt tillgänglig, kommer funktions beskrivningen att flyttas från den här sidan till [vad som är nytt](whats-new.md).
- Den här sidan och sidan [Nyheter](whats-new.md) uppdateras regelbundet. Kom tillbaka och se om det finns nya uppdateringar.
- Information om planerade produktlanseringar och tidslinjer finns i [Microsoft 365-översikten](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS).

> [!NOTE]
> Den här sidan visar våra aktuella förväntningar om Intune-funktioner i en framtida version. Datum och enskilda funktioner kan ändras. Den här sidan beskriver inte alla funktioner som utvecklas.

**RSS-feed**: Få reda på när den här sidan uppdateras genom att kopiera och klistra in följande webbadress i feed-läsaren: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Apphantering

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS User-licensierade VPP-appar<!-- 5619268 idready -->
För användar registrering av iOS-enheter kan slutanvändare inte längre visas med enhets licensierade VPP-program som distribueras som tillgängliga. Slutanvändare kommer dock att fortsätta att se alla licensierade VPP-appar inom Företagsportal. Mer information om VPP-appar finns i [Så här hanterar du iOS- och macOS-appar som köpts genom ett Apples volymköpsprogram med Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Hämta personlig återställnings nyckel från MEM-krypterade macOS-enheter<!-- 4851745 idready -->
Slutanvändarna kan hämta sin personliga återställnings nyckel (FileVault Key) med hjälp av iOS Företagsportal-appen. Enheten som har den personliga återställnings nyckeln måste registreras med Intune och krypteras med FileVault via Intune. Med hjälp av iOS Företagsportal-appen kan slutanvändaren öppna Safari-webbvyn och hämta sin personliga återställnings nyckel. I Intune väljer du **enheter** > *den krypterade och registrerade macOS-enheten* > **Hämta återställnings nyckel**. Mer information om FileVault finns i [FileVault-kryptering för MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Uppdatering av Microsoft app-ikoner<!--4677605-->
Ikonerna som används för Microsoft-appar i appens mål fönster för skydds principer för appar och konfigurations principer för appar kommer att uppdateras.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>S/MIME-stöd för Microsoft Outlook Mobile<!-- 2669398  -->
Intune har stöd för att leverera S/MIME-signering och krypterings certifikat som kan användas med Outlook Mobile på iOS och Android. Relaterad information finns i [e-postinställningar för iOS-enheter](~/configuration/email-settings-ios.md) och [e-postinställningar för Android-enheter](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Stöd för anpassade inställningar för macOS-program<!-- 4736278  -->
Intune stöder anpassade inställningar, så att du kan lägga till vissa nycklar och värden i en befintlig egenskaps lista för inställningar (. plist) för att konfigurera macOS-appar och enheten. Alla appar har inte stöd för hanterade inställningar, och i vissa fall kan endast vissa inställningar hanteras. Inställningarna distribueras endast via enhets kanalen. Du bör bara ladda upp filer för egenskaps listor eller XML-filer som är riktade mot enhets kanal inställningar.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visa meddelanden för Företagsportal-appen i Windows<!-- 1808082  -->
Vi uppdaterar Företagsportal-appen på Windows-enheter för att visa popup-meddelanden till användare, även när programmet stängs. Uppdateringen visar endast meddelanden för tillgängliga appar när installations statusen är slutförd eller inte fungerar. Företagsportal appen visar inte meddelanden för nödvändiga program.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visa installations status meddelanden för appen Företagsportal<!-- 2514416  -->
Företagsportal-appen visar ytterligare status meddelanden för Programinstallation för slutanvändare. Följande villkor gäller för nya Win32-beroende funktioner:
- Appen gick inte att installera. Beroenden som definierats av administratören uppfylldes inte.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Konfigurera program meddelande innehåll för organisations konton<!-- 2576686 -->
Med Intune-appen på Android-och iOS-enheter kan du styra appens meddelande innehåll för organisations konton. Den här funktionen kommer att kräva stöd från program och är kanske inte tillgänglig för alla APP-aktiverade program. Mer information om APP finns i [Vad är appskyddsprinciper?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Enhetskonfiguration

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Blockera användare från att konfigurera autentiseringsuppgifter för certifikat i det hanterade nyckel arkivet på Android Enterprise-enhet ägare enheter<!-- 3311998 idready -->
På Android-enheter för enhets ägare finns det en ny inställning för att hindra användare från att konfigurera sina autentiseringsuppgifter för certifikat i det hanterade nyckel arkivet (**enhets konfiguration** > **profiler** > **Skapa profil** > **Android Enterprise** for Platform > **enhets ägaren endast > enhets begränsningar** för profil typ > **användare + konton**).

Om du vill se aktuella inställningar, går du till [Inställningar för Android Enterprise-enheter som tillåter eller begränsar funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-enhetens ägare, inklusive dedikerade och fullständigt hanterade enheter

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Konfigurations profiler för enheter med kabelanslutna nätverk för macOS-enheter<!-- 3508686 idready -->
På macOS-enheter innehåller en framtida uppdatering en ny enhets konfigurations profil som konfigurerar kabelanslutna nätverk (**enhets konfiguration** > **profiler** > **Skapa profil** > **MacOS** för plattform > **kabelanslutet nätverk** för profil typ). Använd den här funktionen för att skapa 802.1 x-profiler för att hantera kabelanslutna nätverk och distribuera dessa kabelanslutna nätverk till dina macOS-enheter.

Gäller för:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Lägg till automatiska proxyinställningar i Wi-Fi-profiler för Android Enterprise Work-profiler<!-- 4490822 idready -->
På Android Enterprise Work Profile-enheter kan du skapa Wi-Fi-profiler. När du väljer företags typen Wi-Fi kan du också ange den EAP-typ (Extensible Authentication Protocol) som används i ditt Wi-Fi-nätverk.

När du väljer företags typ i en framtida uppdatering kan du ange inställningar för automatisk proxy, inklusive en proxyserver-URL, till exempel `proxy.contoso.com`.

Om du vill se de aktuella Wi-Fi-inställningar som du kan konfigurera går du till [Lägg till Wi-Fi-inställningar för enheter som kör Android Enterprise och Android i Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Gäller för:
- Android Enterprise-arbetsprofil

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Aktivera nätverks åtkomst kontroll (NAC) med Cisco AnyConnect VPN på iOS-enheter<!-- 4860111 idready -->
På iOS-enheter kan du skapa en VPN-profil och använda olika anslutnings typer, inklusive Cisco AnyConnect (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS** för Platform > **VPN** för profil typ > **Cisco AnyConnect** för Anslutnings typ). 

I en framtida uppdatering kan du aktivera Network Access Control (NAC) med Cisco AnyConnect. Gör så här för att använda funktionen:

1. I [Administratörs hand boken för Cisco Identity Services Engine](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)använder du stegen i **Konfigurera Microsoft INTUNE som en MDM-Server** för att konfigurera Cisco Identity Services Engine (ISE) i Azure.
2. I enhets konfigurations profilen för Intune väljer du inställningen **Aktivera nätverks Access Control (NAC)** .

Om du vill se alla tillgängliga VPN-inställningar går du till [Konfigurera VPN-inställningar på iOS-enheter](../configuration/vpn-settings-ios.md).

Gäller för:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Uppdaterad enkel inloggnings upplevelse för appar och webbplatser på iOS-, iPad-och macOS-enheter<!-- 4999578 idready -->
Intune lägger till fler inställningar för enkel inloggning för iOS-, iPad-och macOS-enheter. För närvarande kan du konfigurera inloggnings program tillägg för SSO och Apples inbyggda Kerberos-tillägg i Intune. I en framtida uppdatering kommer du att kunna konfigurera omdirigerings-app-tillägg som skrivits av din organisation eller av din identitets leverantör. 

Använd de här inställningarna för att konfigurera en sömlös enkel inloggning för appar och webbplatser som använder moderna autentiseringsmetoder, till exempel OAuth och SAML2. 

Om du vill se Inställningar för SSO-programtillägg som du kan konfigurera går du till [SSO på iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) och [SSO på MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Gäller för:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Kräv användning av godkända tangent bord på Android<!--4761794 IDready -->
Du kan ange en lista över godkända tangent bord som ska användas i hanterade Android-appar. Från den hanterade appen uppmanas användaren att byta till ett av de godkända tangent bord som redan är installerat på enheten eller, om det behövs, de dirigeras till Google Play Butik att ladda ned och konfigurera ett av de godkända tangent bord. Användaren kan bara redigera textfält i en hanterad app om deras aktiva tangent bord är ett av de godkända tangent borden.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Använda PKCS-certifikat med Wi-Fi-profiler på enheter med Windows 10 och senare<!-- 3246388  -->
För närvarande kan du autentisera Windows Wi-Fi-profiler med SCEP-certifikat (**enhets konfiguration** > **profiler** > **Skapa profil** > **Windows 10 och senare** för platform > **Wi-Fi** för profil typ > **Enterprise** > **EAP-typ**). Du kommer att kunna använda PKCS-certifikat med dina Windows Wi-Fi-profiler. Med den här funktionen kan användarna autentisera Wi-Fi-profiler med hjälp av nya eller befintliga PKCS-certifikat profiler i din klient organisation. 

Mer information om Wi-Fi-profiler finns i [lägga till Wi-Fi-inställningar för enheter med Windows 10 och senare i Intune](../configuration/wi-fi-settings-windows.md).

Gäller för:
- Windows 10 och senare

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Nya Exchange ActiveSync-inställningar när du skapar en profil för e-postenhetskonfiguration på iOS-enheter<!-- 4892824  --> 
På iOS/iPad-enheter kan du konfigurera e-postanslutningen i en enhetskonfigurationsprofil (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **iOS/iPad** för plattform > **E-post** för profiltyp). 

Det kommer att finnas nya ExchangeActiveSync-inställningar tillgängliga, inklusive:
- Välj vilka tjänster som ska synkroniseras (eller blockera synkronisering), till exempel e-post, kalender och kontakter.
- Tillåt (eller blockera) användare att ändra synkroniseringsinställningarna för dessa tjänster på sina enheter. 

Om du vill se de aktuella inställningarna går du till [Inställningar för e-postprofil för iOS-enheter i Intune](../configuration/email-settings-ios.md).

Gäller för:
- iOS 13.0 och senare
- iPadOS 13.0 och senare

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Hindra användare från att lägga till personliga Google-konton i företagsägda och dedikerade Android Enterprise-enheter<!-- 5353228  -->
På fullständigt hanterade och dedikerade Android Enterprise-enheter kan du hindra användare från att skapa personliga Google-konton (**Enhetskonfiguration** > **Profiler** > **Skapa profil** > **Android Enterprise** för plattform > **Endast enhetens ägare > Enhetsbegränsningar** för profiltypen > **Användar- och kontoinställningar**).

Om du vill se de aktuella inställningar som du kan konfigurera går du till [Inställningar för Android Enterprise-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-android-for-work.md).

Gäller för:
- Android Enterprise-enhetsägare
- Dedikerade Android Enterprise-enheter

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>Loggning på serversidan för Siri-kommandon tas bort från enhetsbegränsningsprofilen för iOS<!-- 5468501  -->
På iOS-enheter kan du skapa en profil för enhets begränsningar som konfigurerar loggning på Server sidan för Siri-kommandon (**enhets konfiguration** > **profiler** > **Skapa profil** > **iOS/iPad** för plattforms > **enhets begränsningar** för profil typ > **inbyggda appar**). Inställningen på **Server sidans loggning för Siri-kommandon** kommer att tas bort.

Den här inställningen tas bort från Intunes administratörs konsol. Den här inställningen har ingen påverkan på enheten trots att befintliga principer som har den här inställningen konfigurerad kommer att fortsätta att visa inställningen. Om du vill ta bort inställningen från befintliga principer går du till principen, gör en mindre redigering, sparar den och principen kommer att uppdateras.

Om du vill se de inställningar som du kan konfigurera går du till [Inställningar för iOS- och IPadOS-enheter för att tillåta eller begränsa funktioner med Intune](../configuration/device-restrictions-ios.md).

Gäller för:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Övervakning och fel sökning

### <a name="centralized-audit-logs--5603185-5697164--"></a>Centraliserade gransknings loggar<!--5603185, 5697164-->
En ny Centraliserad gransknings loggs upplevelse samlar in gransknings loggar för alla kategorier på en sida. You'l kan filtrera loggarna för att hämta de data du söker. Om du vill se gransknings loggarna går du till **klient administration** > **gransknings loggar**. Mer information finns i [kommande ändring av gransknings loggar i Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>Säkerhet

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Använd PKCS-certifikat profiler för att etablera enheter med certifikat<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Du kommer att kunna använda en PKCS-certifikatfil för att utfärda certifikat till enheter, vilket utökar det aktuella stödet för användarbaserade certifikat. Enhets certifikat kommer att stödja Android-, iOS-och Windows-plattformarna och kan användas för Wi-Fi-och VPN-profiler.

<!-- ***********************************************-->
## <a name="notices"></a>Meddelanden

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Se även
Mer information om den senaste utvecklingen finns i [Nyheter i Microsoft Intune](whats-new.md).


