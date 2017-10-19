---
title: VPN-anslutningar
description: "Använd VPN-profiler för att distribuera VPN-inställningar till användare och enheter i organisationen."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5b1140d990ac5d1c4364b1f48107a355c43c6cdb
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2017
---
# <a name="vpn-connections-in-microsoft-intune"></a>VPN-anslutningar i Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheter använder en *profil för VPN-anslutning* för att initiera en anslutning till VPN-servern. Använd *VPN-profiler* i Microsoft Intune för att distribuera VPN-inställningar till användare och enheter i din organisation så att de enkelt och säkert kan ansluta till nätverket.

Exempel: Anta att du vill förse alla enheter som kör iOS med de inställningar som krävs för att ansluta till en filresurs i företagsnätverket. Då kan du skapa en VPN-profil som innehåller de inställningar som behövs för att ansluta till företagsnätverket och sedan distribuera profilen till alla användare som har enheter som kör iOS. Användarna ser VPN-anslutningen i listan över tillgängliga nätverk och kan enkelt ansluta.

Du kan konfigurera följande enhetstyper med VPN-profiler:

* Enheter som kör Android 4 och senare
* Android for Work-enheter
* Enheter som kör iOS 8.0 och senare
* Enheter som kör Mac OS X 10.9 och senare
* Registrerade enheter som kör Windows 8.1 och senare
* Enheter som kör Windows Phone 8.1 och senare
* Enheter som kör Windows 10 Desktop och Mobile

Konfigurationsalternativen för VPN-profiler varierar beroende på vilken enhetstyp du väljer.

## <a name="vpn-connection-types"></a>VPN-anslutningstyper

Intune har stöd för att skapa VPN-profiler som använder följande anslutningstyper:


Anslutningstyp |iOS och Mac OS X  |Android och Android for Work|Windows 8,1|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop och Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|Ja |Ja   |Nej    |Nej  |Nej    | Ja, (OMA-URI, endast mobil)|     
Cisco (IPsec)|Ja |Ja   |Nej  |Nej  |Nej | Nej|
Citrix|Ja |Ja (endast Android)   |Nej  |Nej  |Nej | Nej|
Pulse Secure|Ja  |Ja |Ja   |Ja  |Ja| Ja|        
F5 Edge Client|Ja |Ja |Ja |Ja  |   Ja |  Ja|   
Dell SonicWALL Mobile Connect|Ja |Ja |Ja |Ja |Ja |Ja|         
Kontrollpunkt för mobilt VPN:|Ja |Ja |Ja |Ja|Ja|Ja|
Microsoft SSL (SSTP)|Nej |Nej |Nej |Nej|Nej|VPNv1 OMA-URI*|
Microsoft Automatic|Nej |Nej |Nej |Nej|Ja (OMA-URI)|Ja|
IKEv2|Anpassad profil för iOS|Nej |Nej |Nej|Ja (OMA-URI)|Ja|
PPTP|Anpassad profil för iOS|Nej |Nej |Nej|Nej|Ja|
L2TP|Anpassad profil för iOS|Nej |Nej |Nej|Ja (OMA-URI)|Ja|

\* Utan ytterligare inställningar som är tillgängliga för Windows 10 på annat sätt.

> [!IMPORTANT]
> Innan du kan använda de VPN-profiler som har distribuerats till en enhet måste du installera lämplig VPN-app för profilen. Använd informationen i avsnittet [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md) när du ska distribuera appar med hjälp av Intune.  

 Läs om hur du skapar anpassade VPN-profiler med hjälp av URI-inställningarna i [Anpassade konfigurationer för VPN-profiler](create-custom-vpn-profiles.md).     

## <a name="methods-of-securing-vpn-profiles"></a>Metoder för att skydda VPN-profiler

VPN-profiler kan använda ett antal olika anslutningstyper och protokoll från olika tillverkare. Dessa anslutningar skyddas vanligtvis med en av följande metoder.

### <a name="certificates"></a>Certifikat

När du skapar VPN-profilen väljer du en SCEP- eller PFX-certifikatprofil som du tidigare har skapat i Intune. Detta kallas identitetscertifikat. Det används för att autentisera mot en betrodd certifikatprofil (eller *rotcertifikat*) som du har skapat för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet distribueras till datorn som autentiserar VPN-anslutningen, vanligtvis VPN-servern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md).

### <a name="user-name-and-password"></a>Användarnamn och lösenord

Användaren autentiseras mot VPN-servern genom att ange användarnamn och lösenord.

## <a name="create-a-vpn-profile"></a>Skapa en VPN-profil

1. I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) väljer du **Princip** > **Lägg till princip**.
2. Välj en mall för den nya principen genom att expandera den aktuella enhetstypen. Välj sedan VPN-profilen för den enheten:
    * **VPN-profil (Android 4 och senare)**
    * **VPN-profil (Android for Work)**
    * **VPN-profil (iOS 8.0 och senare)**
    * **VPN-profil (Mac OS X 10.9 och senare)**
    * **VPN-profil (Windows 8.1 och senare)**
    * **VPN-profil (Windows Phone 8.1 och senare)**
    * **VPN-profil (Windows 10 Desktop och Mobile och senare)**

 Du kan skapa och distribuera endast en anpassad VPN-profilprincip. Rekommenderade inställningar är inte tillgängliga.

> [!Note]
> En VPN-profil för Android for Work-enheter aktiverar endast en VPN-anslutning för appar som är installerade på enhetens arbetsprofil.
>
> Vissa VPN-anslutningstyper stöder Per app-VPN för Android for Work-enheter och aktivering av Per app-VPN för appar som distribuerats via Intune.  

3. Använd följande tabell för att konfigurera inställningarna för VPN-profilen:

Inställningsnamn  |Mer information  
---------|---------
**Namn**     |Ange ett unikt namn för VPN-profilen som hjälper dig att identifiera den i Intune-konsolen.         
**Beskrivning**     |Ange en lämplig beskrivning av VPN-profilen och annan information som gör det enkelt att hitta profilen.         
**VPN-anslutningens namn (visas för användare)**     |Ange ett namn på VPN-profilen. Detta är det namn som användarna ser i listan över tillgängliga VPN-anslutningar på sina enheter.         
**Anslutningstyp**     |  Välj någon av följande anslutningstyper som ska användas i VPN-profilen: **Cisco AnyConnect** (inte tillgänglig för Windows 8.1 eller Windows Phone 8.1), **Pulse Secure**, **Citrix**, **F5 Edge Client**, **Dell SonicWALL Mobile Connect**, **CheckPoint Mobile VPN**.
**VPN-serverbeskrivning**     | Ange en beskrivning för den VPN-server som enheterna ska ansluta till. Exempel: **Contoso VPN Server**. Om anslutningstypen är **F5 Edge Client** använder du fältet **Serverlista** för att ange en lista med serverbeskrivningar och IP-adresser.
**Serverns IP-adress eller fullständiga domännamn**    |Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.  Om anslutningstypen är **F5 Edge Client** använder du fältet **Serverlista** för att ange en lista med serverbeskrivningar och IP-adresser.         |         
**Serverlista**     |Välj **Lägg till** om du vill lägga till en ny VPN-server som ska användas för VPN-anslutningen. Du kan även ange vilken server som ska vara standardserver för anslutningen. Det här alternativet visas endast när anslutningstypen är **F5 Edge Client**.         
**Skicka all nätverkstrafik via VPN-anslutningen**     |Om du väljer det här alternativet skickas all nätverkstrafik via VPN-anslutningen. Om du inte väljer det här alternativet kommer klienten dynamiskt att förhandla vägar i delade tunnlar vid anslutning till tredjeparts VPN-server. Endast anslutningar till företagsnätverket skickas via en VPN-tunnel. VPN-tunnlar används inte vid anslutning till resurser på Internet.
**Autentiseringsmetod**| Välj den autentiseringsmetod som används av VPN-anslutningen: **Certifikat** eller **Användarnamn och lösenord**. (**Användarnamn och lösenord** är inte tillgängligt om anslutningstypen är Cisco AnyConnect.) Alternativet **Autentiseringsmetod** är inte tillgängligt för Windows 8.1.
**Spara autentiseringsuppgifterna för varje inloggning**|Välj det här alternativet om användarnas autentiseringsuppgifter ska sparas, så att användarna slipper ange dem varje gång som en anslutning ska upprättas.
**Välj ett certifikat för klientautentisering (identitetscertifikat)**|Välj det SCEP-klientcertifikat du skapade tidigare och som ska användas för att autentisera VPN-anslutningen. Mer information om hur du använder certifikatprofiler i Intune finns i [Skydda resursåtkomst med certifikatprofiler](secure-resource-access-with-certificate-profiles.md). Det här alternativet visas endast när autentiseringsmetoden är **Certifikat**.
**Roll**| Ange namnet för den användarroll som har åtkomst till anslutningen. En användarroll definierar personliga inställningar och alternativ, och aktiverar eller inaktiverar vissa åtkomstfunktioner. Det här alternativet visas endast när anslutningstypen är **Pulse Secure** eller **Citrix**.
**Område**|Ange namnet för den autentiseringssfär som ska användas. En autentiseringssfär är en grupp autentiseringsresurser som används av Pulse Secure- eller Citrix-anslutningstypen. Det här alternativet visas endast när anslutningstypen är **Pulse Secure** eller **Citrix**.
**Inloggningsgrupp eller -domän**|Ange namnet för den inloggningsgrupp eller domän som du vill ansluta till. Det här alternativet visas endast när anslutningstypen är **Dell SonicWALL Mobile Connect**.
**Fingeravtryck**|Ange en sträng, till exempel ”Contoso fingeravtryckskod” som ska användas för att verifiera att VPN-servern är betrodd. Ett fingeravtryck kan skickas till klienten så att den vet att den ska lita på alla servrar som visar upp samma fingeravtryck vid anslutningen. Om enheten inte redan har fingeravtrycket uppmanas användaren att lita på VPN-servern medan fingeravtrycket visas. (Användaren verifierar fingeravtrycket manuellt och väljer **betrodd** för att ansluta.) Det här alternativet visas endast när anslutningstypen är **CheckPoint Mobile VPN**.
**Per app-VPN**|Välj det här alternativet om du vill koppla VPN-anslutningen till en iOS- eller Mac OS X-app så att anslutningen öppnas när appen körs. Du kan associera VPN-profilen med en app när du distribuerar programvaran. Mer information finns i [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).
**VPN på begäran**|Du kan konfigurera VPN på begäran för enheter med iOS 8.0 eller senare. Anvisningar för hur du konfigurerar detta finns i [VPN på begäran för iOS-enheter](#on-demand-vpn-for-ios-devices).
**Identifiera proxyinställningar automatiskt** (endast iOS, Mac OS X, Windows 8.1 och Windows Phone 8.1)|Om VPN-servern kräver en proxyserver för anslutningen kan du ange om du vill att enheterna automatiskt ska identifiera anslutningsinställningarna. Mer information finns i dokumentationen till Windows Server.
**Använd automatiskt konfigurationsskript** (endast iOS, Mac OS X, Windows 8.1 och Windows Phone 8.1)|Om VPN-servern kräver en proxyserver för anslutningen kan du ange om du vill använda ett automatiskt konfigurationsskript för att ange inställningarna och sedan ange en URL till den fil som innehåller inställningarna. Mer information finns i dokumentationen till Windows Server.
**Använd proxyserver** (endast iOS, Mac OS X, Windows 8.1 och Windows Phone 8.1)|Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och ange proxyserverns adress och portnummer. Mer information finns i dokumentationen till Windows Server.
**Kringgå proxyinställningar för lokala adresser** (endast iOS, Mac OS X, Windows 8.1 och Windows Phone 8.1)|Välj det här alternativet om VPN-servern kräver en proxyserver för anslutningen och du inte vill använda proxyservern för de lokala adresser som du anger. Mer information finns i dokumentationen till Windows Server.
**Anpassad XML** (endast Windows 8.1 och senare och Windows Phone 8.1 och senare)|Ange anpassade XML-kommandon som konfigurerar VPN-anslutningen. Exempel för **Pulse Secure**: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. Exempel för **CheckPoint Mobile VPN**: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. Exempel för **Dell SonicWALL Mobile Connect**: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. Exempel för **F5 Edge Client**: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. Läs VPN-dokumentationen för varje tillverkare för mer information om hur du skriver anpassade XML-kommandon.
**Söklista för DNS-suffix** (endast Windows Phone 8.1)|Ange ett DNS-suffix på varje rad. Varje DNS-suffix som du anger genomsöks vid anslutning till en webbplats med ett kort namn. Ange till exempel DNS-suffixen **domain1.contoso.com** och **domain2.contoso.com**. Besök webbadressen **http://mywebsite** så genomsöks webbadresserna **http://mywebsite.domain1.contoso.com** och **http://mywebsite.domain2.contoso.com**.
**Kringgå VPN vid anslutning till företagets Wi-Fi-nätverk** (endast Windows Phone 8.1)|Välj det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till företagets Wi-Fi-nätverk.
**Kringgå VPN vid anslutning till ett hemma-Wi-Fi-nätverk** (endast Windows Phone 8.1)|Välj det här alternativet om du vill ange att VPN-anslutningen inte ska användas när enheten är ansluten till Wi-Fi hemma.

Följande ytterligare inställningar är tillgängliga för Windows 10 Desktop- och Mobile-enheter.

Inställningsnamn  |Mer information  
---------|---------
**Regler för nätverkstrafik**|Ange vilka protokoll, vilka lokala portar och fjärrportar samt vilka adressintervall som ska aktiveras för VPN-anslutningen. Om du inte skapar någon regel för nätverkstrafik aktiveras alla protokoll, portar och adressintervall. När du har skapat en regel använder VPN-anslutningen bara de protokoll, portar och adressintervall som du har angett i regeln.
**Vägar**|Välj vilka vägar som ska använda VPN-anslutningen.
**DNS-servrar**| Välj vilka DNS-servrar som ska användas av VPN-anslutningen när anslutningen har upprättats.         
**Associerade appar**|Ange en lista över appar som ska använda VPN-anslutningen automatiskt. Appidentifieraren beror på typen av app. För en universell app anger du paketfamiljenamnet. För en skrivbordsapp anger du appens filsökväg.          


> [!IMPORTANT]
> Vi rekommenderar att du skyddar alla listor över appar som du sammanställer för användning i konfigurationen av per app-VPN. Om en obehörig användare ändrar listan och du importerar den till per app-VPN-applistan finns risken att du tillåter VPN-åtkomst till appar som inte ska ha åtkomst. Ett sätt att skydda applistor är att använda en åtkomstkontrollista (ACL, Access Control List).

Här är ett exempel på när du kan använda inställningar för företagsgränser. Om du bara vill aktivera VPN för Fjärrskrivbord skapar du en regel för nätverkstrafik som tillåter trafik för protokoll nummer 27 på den externa porten 3996. Ingen annan trafik använder VPN-anslutningen.

Det är praktiskt att definiera vägar i företagsgränser om VPN-anslutningstypen inte tillåter att du definierar hur trafiken hanteras i delade tunnlar (Split Tunneling). I så fall använder du **Vägar** för att visa en lista med de vägar som ska använda VPN-anslutningen.

Du kan begränsa VPN-användningen på Windows 10-enheter till specifika appar genom att skapa en anpassad OMA-URI-inställning.

Den nya principen visas i noden **Konfigurationsprinciper** på arbetsytan **Principer** .

### <a name="on-demand-vpn-for-ios-devices"></a>VPN på begäran för iOS-enheter
Du kan konfigurera VPN på begäran för enheter med iOS 8.0 eller senare.

> [!NOTE]
>  
> Du kan inte använda per app-VPN och VPN på begäran i samma princip.

1. Leta reda på principkonfigurationssidan och sök efter **på begäran-regler för den här VPN-anslutningen**. Kolumnerna som är märkta med **Matchning**, villkoret som reglerna söker efter och **Åtgärd**, den åtgärd som principen utlöser när villkoret matchas.
2. Skapa en regel genom att välja **Lägg till**. Det finns två typer av matchningar som du kan konfigurera i regeln. Du kan bara konfigurera en typ per regel.
  - **SSID:er** – som refererar till trådlösa nätverk.
  - **DNS-sökdomäner** – Du kan använda fullständiga kvalificerade domännamn som *team. corp.contoso.com* eller använda domäner som *contoso.com*, vilket är detsamma som att använda **contoso.com*.
3. Valfritt: Ange en URL-strängavsökning som är en URL som regeln använder som ett test. Om den enhet där den här profilen har installerats kan få tillgång till denna URL utan omdirigering upprättas VPN-anslutningen och enheten ansluter till mål-URL:en. Användaren ser inte URL-strängavsökningsplatsen. Ett exempel på en URL-strängavsökning är adressen till en granskningswebbserver som kontrollerar enhetens efterlevnad innan VPN-anslutningen görs. En annan möjlighet är att URL:en testar VPN-nätverkets förmåga att ansluta till en webbplats innan enheten ansluts till mål-URL:en via VPN.
4. Välj någon av följande åtgärder:
  - **Ansluta**
  - **Utvärdera anslutning**, som har tre inställningar A. **Domänåtgärd**  – välj **Anslut om det behövs** eller **Anslut aldrig** B. **Kommaavgränsad lista över domäner** – du konfigurerar detta endast om du väljer en **domänåtgärd** för **Anslut om det behövs** C. **Nödvändig URL-strängsavsökning** – en URL av typen HTTP eller HTTPS (rekommenderas), t.ex. *https://vpntestprobe.contoso.com*. Den regel som ska kontrollera om det finns ett svar från den här adressen. Om inte, och om **Domänåtgärd** är **Anslut om det behövs** utlöses VPN-anslutningen.
      
     > [!TIP]
     >
     >Ett exempel på när du kan använda den här åtgärden är när vissa platser i företagsnätverk kräver en direkt anslutning eller en VPN-företagsnätverksanslutning, medan andra inte gör det. Om du listar *corp.contoso.com* i en **kommaavgränsad lista över DNS-sökdomäner** kan du välja **Anslut om det behövs** och sedan lista specifika platser i nätverket som kan kräva VPN, t.ex. *sharepoint.corp.contoso.com*. Regeln kontrollerar sedan om *vpntestprobe.contoso.com* kan nås. Om den inte nås utlöses VPN för SharePoint-webbplatsen.
  - **Ignorera** – detta orsakar inte någon ändring i VPN-anslutningen. Om VPN-nätverket är anslutet, så låt det vara anslutet. Om det inte är anslutet, så anslut det inte. Du kan till exempel ha en regel som ansluter VPN-nätverket för alla dina interna företagswebbplatser, men vill göra något av dessa interna webbplatser tillgänglig enbart när enheten faktiskt är ansluten till företagsnätverket. I så fall kan skapa du en ignoreringsregel för den webbplatsen.
  - **Koppla från** – koppla från enheter från VPN-nätverket när villkoren uppfylls. Du kan t.ex. lista din företags trådlösa nätverk i fältet **SSID** och skapa en regel som kopplar bort enheter från VPN-nätverket när de ansluter till något av dessa nätverk.

Domänspecifika regler utvärderas före allmänna domänregler.


## <a name="deploy-the-policy"></a>Distribuera principen

1.  På arbetsytan **Princip** markerar du den princip som du vill distribuera och väljer sedan **Hantera distribution**.

2.  I dialogrutan **Hantera distribution** :

    -   Om du vill distribuera principen väljer du en eller flera grupper som du vill distribuera principen till. Välj sedan **Lägg till** &gt; **OK**.

    -   Om du vill stänga dialogrutan utan att distribuera den väljer du **Avbryt**.


Efter slutförd distribution ser användarna det namn du gav VPN-anslutningen i listan över VPN-anslutningar på sina enheter.

En statssammanfattning och varningar på sidan **Översikt** på arbetsytan **Principer** identifierar problem med principer som kräver din uppmärksamhet. Dessutom visas en statussammanfattning på arbetsytan Instrumentpanel.
