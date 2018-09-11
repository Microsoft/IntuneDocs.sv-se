---
title: VPN-inställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Visa tillgängliga konfigurationsinställningar för virtuella privata nätverk (VPN), inklusive anslutningsinformation, autentiseringsmetoder och delade tunnlar i de grundläggande inställningarna. Visa även de anpassade VPN-inställningarna med identifieraren och nyckel-värdeparen. Det är även möjligt att visa VPN-inställningarna per app som inkluderar Safari-webbadresser och VPN-anslutningar på begäran med SSID- eller DNS-sökningsdomäner samt proxyinställningar för att inkludera ett konfigurationsskript, en IP- eller FQDN-adress och en TCP-port i Microsoft Intune på iOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313878"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör iOS.

Beroende på vilka inställningar du väljer kan bara vissa värden i följande lista konfigureras.

## <a name="base-vpn-settings"></a>Grundläggande VPN-inställningar
De faktiska inställningar som visas i listan nedan bestäms av den VPN-anslutningstyp som du väljer.  
- **Anslutningsnamn**: Slutanvändarna ser det här namnet när de bläddrar i en lista över tillgängliga VPN-anslutningar på enheten.
- **Anpassat domännamn** (endast Zscaler): Fyll i Zscaler-appens inloggningsfält på förhand med den domän som användarna tillhör. Om ett användarnamn till exempel är **Joe@contoso.net** kan domänen **contoso.net** visas statiskt i fältet när appen öppnas. Om du inte anger ett domännamn används domändelen i UPN-namnet i Azure Active Directory.
- **IP-adress eller fullständigt domännamn**: IP-adressen eller det fullständiga domännamnet för VPN-servern som enheterna ska ansluta till. Ange till exempel **192.168.1.1** eller **vpn.contoso.com**. 
- **Organisationens molnnamn** (endast Zscaler): Ange namnet på det moln där organisationen har etablerats. Titta i den URL som du använder för att logga in på Zscaler för att hitta namnet.  
- **Autentiseringsmetod**: Välj hur enheter autentiserar mot VPN-servern. 
  - **Certifikat**:Under **Autentiseringscertifikat** väljer du en befintlig SCEP- eller PKCS-certifikatprofil för att autentisera anslutningen. [Konfigurera certifikat](certificates-configure.md) innehåller vägledning om certifikatprofiler.
  - **Användarnamn och lösenord**: Slutanvändare måste ange ett användarnamn och ett lösenord för att logga in på VPN-servern.  

    > [!NOTE]
    > Om användarnamnet och lösenordet används som autentiseringsmetod för Cisco IPsec VPN, måste de ge SharedSecret via en anpassad profil i Apple Configurator.
  
- **Anslutningstyp**: Välj VPN-anslutningstypen från leverantörslistan nedan:
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
  - **Zscaler**: Kräver att du integrerar Zscaler Private Access (ZPA) med ditt Azure Active Directory-konto. Detaljerade anvisningar finns i [Zscaler-dokumentationen](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO). 
  - **Anpassat VPN**    

    > [!NOTE]
    > Cisco, Citrix, F5 och Palo Alto har tillkännagivit att deras äldre klienter inte kommer att fungera på den kommande versionen av iOS 12. Du bör migrera till de nya apparna så snart som möjligt. Mer information finns i [Microsoft Intune-supportteamets blogg](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409).

* **Undantagna webbadresser** (endast Zscaler): Vid anslutning till Zscaler VPN är de angivna webbadresserna tillgängliga utanför Zscaler-molnet. 

- **Delade tunnlar**: **Aktivera** eller **Inaktivera** för att låta enheterna bestämma vilken anslutning som ska användas beroende på trafiken. En användare på ett hotell kan till exempel använda VPN-anslutningen för att komma åt arbetsfiler, men använda hotellets standardnätverk för vanlig webbsurfning.   

## <a name="custom-vpn-settings"></a>Anpassade VPN-inställningar

Om du har valt **Anpassat VPN** som anslutningstyp konfigurerar du följande inställningar. De här inställningarna syns även för Zscaler- och Citrix-anslutningar.

- **VPN-ID** En identifierare för VPN-appen som du använder och som tillhandahålls av VPN-leverantören.
- **Ange nyckel/värdepar för organisationens anpassade VPN-attribut**: Lägg till eller importera **Nycklar** och **Värden** som anpassar VPN-anslutningen. Även dessa värden tillhandahålls vanligtvis av VPN-leverantören.

## <a name="automatic-vpn-settings"></a>Inställningar för automatiskt VPN

- **Per app-VPN**: Om du väljer det här alternativet aktiveras per app-VPN, vilket gör att VPN-anslutningen utlöses automatiskt när vissa program öppnas. Utöver att välja det här alternativet måste du även associera programmen med den här VPN-profilen. Läs mer i [instruktionerna för att konfigurera per app-VPN för iOS](vpn-setting-configure-per-app.md). 
  - Inställningen **Typ av provider** är endast tillgänglig för Pulse Secure och Anpassat VPN.
  - När du använder **per app-VPN-profiler** med Pulse Secure eller Anpassat VPN kan du välja att använda händelsedirigering nedåt på applager (app-proxy) eller på paketnivå (paket-tunnel). Ange värdet **Typ av provider** på **app-proxy** för händelsedirigering nedåt på applager eller **paket-tunnel** för händelsedirigering på paketnivå. Om du inte är säker på vilket värde du ska använda kan du läsa VPN-providerns dokumentation. 
  - **Safari-webbadresser som utlöser denna VPN**: Välj det här alternativet för att lägga till en eller flera webbadresser. VPN-anslutningen upprättas automatiskt när de här webbadresserna besöks i Safari-webbläsaren på enheten.

- **VPN på begäran**: Konfigurera villkorliga regler som styr när VPN-anslutningen ska initieras. Du kan till exempel skapa ett villkor där VPN-anslutningen endast används när en enhet inte är ansluten till ett trådlöst företagsnätverk. Du kan även skapa ett villkor där VPN-anslutningen inte initieras om enheten inte får åtkomst till en DNS-sökdomän som du har angett.

  - **SSID:n eller DNS-sökdomäner**: Välj om det här villkoret ska använda det trådlösa nätverkets **SSID:n** eller **DNS-sökdomäner**. Välj **Lägg till** för att konfigurera en eller flera SSID:er eller sökdomäner.
  - **URL-strängavsökning**: Valfritt. Ange en URL som regeln använder som ett test. Om den enhet där profilen har installerats får tillgång till den här webbadressen utan omdirigering startas VPN-anslutningen och enheten ansluter till målwebbadressen. Användaren ser inte URL-strängens avsökningsplats. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att webbadressen testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till målwebbadressen via VPN.
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

- **Skript för automatisk konfiguration**: Använd en fil för att konfigurera proxyservern. Ange **webbadress till proxyserver** (till exempel **http://proxy.contoso.com**) som innehåller konfigurationsfilen.
- **Adress**: Ange IP-adressen för det fullt kvalificerade värdnamnet för proxyservern.
- **Portnummer**: Ange det portnummer som är associerat med proxyservern.

## <a name="next-step"></a>Nästa steg
[Skapa VPN-profiler i Intune](vpn-settings-configure.md)  
