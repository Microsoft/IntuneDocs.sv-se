---
# required metadata

title: Konfigurera infrastrukturen för certifikat | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3a435650-3891-4754-8abc-4bbac244f33b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurera infrastrukturen för certifikat
Det här avsnittet beskriver vad du behöver för att skapa och distribuera certifikatprofiler.

Om du vill utföra certifikatbaserad autentisering i organisationen måste du ha en utfärdare av företagscertifikat.

Om du vill använda SCEP-certifikatprofiler behöver du, förutom utfärdaren av företagscertifikat:

-   En server som kör registreringstjänsten för nätverksenheter

-   Intunes certifikat Connector som installeras på Windows Server 2012 R2-servern som kör NDES

Om du vill använda .PFX-certifikatprofiler behöver du, förutom utfärdaren av företagscertifikat:

-  En dator som kan kommunicera med certifikatutfärdaren eller använda certifikatutfärdar-datorn.

-  Intunes certifikat Connector, som körs på datorn som kan kommunicera med certifikatutfärdaren.

## Lokal infrastruktur


-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare** (CA): En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Installera certifikatutfärdare](http://technet.microsoft.com/library/jj125375.aspx)
    Om certifikatutfärdaren kör Windows Server 2008 R2 måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/)

-  **NDES-server** (endast SCEP): På en server som kör Windows Server 2012 R2 eller senare måste du konfigurera registreringstjänsten för nätverksenheter (NDES). Intune stöder inte användning av registreringstjänsten för nätverksenheter när den körs på en server som också kör företagscertifikatutfärdaren. Se [Vägledning för nätverksenhetsregistreringstjänster](http://technet.microsoft.com/library/hh831498.aspx) för instruktioner om hur du konfigurerar Windows Server 2012 R2 som värd för registreringstjänsten för nätverksenheter.|
-  **Dator som kan kommunicera med certifikatutfärdaren** (endast -PFX): Använd alternativt certifikatutfärdardatorn.
-  **Microsoft Intune-certifikatanslutningsapp**: Använd Intune-administratörskonsolen för att hämta installationsprogrammet för **Certifikatanslutningsapp** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector. För. PFX-certifikatprofiler, installera certifikat connector på datorn som kommunicerar med certifikatutfärdaren.
-  **Webbprogramproxyserver** (valfritt): Du kan använda en server som kör Windows Server 2012 R2 eller senare som en webbprogramproxyserver (WAP). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

> [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769) eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135)
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramproxy](http://technet.microsoft.com/library/dn584113.aspx).


### Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Du konfigurerar den här mallen på den utfärdande certifikatutfärdaren.|
|**Certifikat för klientautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från offentlig certifikatutfärdare, du installerar certifikatet på NDES-servern.|
|**Certifikat för serverautentisering**|Begärs från den utfärdande certifikatutfärdaren eller från offentlig certifikatutfärdare, du installerar och binder SSL-certifikatet i IIS på NDES-servern.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **CER** -fil från den utfärdande certifikatutfärdare eller en enhet som litar på certifikatutfärdaren och distribuerar den till enheter med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|

### Konton

|Namn|Information|
|--------|-----------|
|**NDES-tjänstkonto**|Du anger ett domänanvändarkonto som används som NDES-tjänstkontot|

## Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du utföra följande åtgärder, som kräver kunskaper om Windows Server 2012 R2 och Active Directory-certifikattjänster (ADCS):

**Uppgift 1** – Konfigurera certifikatmallar på certifikatutfärdaren

**Uppgift 2**, endast för SCEP-profil – Konfigurera krav på NDES-servern

**Uppgift 3**, endast för SCEP-profil – Konfigurera NDES för användning med Intune

**Uppgift 4** – Aktivera, installera och konfigurera Intune-certifikatanslutningsapp

## Uppgift 1 – konfigurera certifikatmallar på certifikatutfärdaren
I det här steget kommer du att:

-   Skapa ett NDES-tjänstkonto

    > Om du vill återkalla certifikat behöver NDES-tjänstkontot rättigheter för att *Utfärda och hantera certifikat* för varje certifikatmall som används av en certifikatprofil.

-   Konfigurera en certifikatmall för NDES

-   Publicera certifikatmallen för NDES

##### Så här konfigurerar du certifikatutfärdaren

1.  Skapa domänanvändarkonto som används som NDES-tjänstkontot Du anger det här kontot när du konfigurerar mallar på den utfärdande certifikatutfärdaren innan du installerar och konfigurerar NDES.

2.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatmallar för att skapa en ny anpassad mall eller kopiera en befintlig mall och sedan redigera en befintlig mall (t.ex. mallen Användare) för användning med NDES.

    Mallen måste ha följande konfigurationer:

    -   Ange ett eget **visningsnamn för mallen** .

    -   På fliken **Ämnesnamn** väljer du **Anges i begäran**. (Säkerhet tvingas av Intune-principmodulen för NDES).

    -   På fliken **Tillägg** kontrollerar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**

        > För iOS- och Mac OS X-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.

    -   På fliken **Säkerhet** lägger du till NDES-tjänstekontot och ger det **Registreringsrättigheter** för mallen.

3.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > iOS- och Mac OS X-plattformen använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

    Om du vill konfigurera certifikatutfärdaren att tillåta att den som begär anger giltighetsperioden, kör du följande kommandon på certifikatutfärdaren:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.

    1.  Välj noden **Certifikatmallar**, klicka på **Åtgärd**-&gt; **Ny** &gt; **Certifikatmall som ska utfärdas**. Välj sedan den mall du skapade i steg 2.

    2.  Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .

5.  För. PFX-profiler: på datorn med Certifikatutfärdaren se till att datorn som har Intunes certifikat connector har registreringsrättigheter, så den kommer åt mallen som används för att skapa .PFX-profilen. Ställ in behörighet på **säkerhetsfliken** i datoregenskaper för Certifikatutfärdar-datorn.

## Uppgift 2 (enbart SCEP-profiler) - Konfigurera förutsättningar på NDES servern
I det här steget kommer du att:

-   Lägga till NDES till en Windows Server och konfigurera IIS för att stöda NDES

-   Lägga till NDES-tjänstkontot i gruppen IIS_IUSR

-   Ange SPN för NDES-tjänstkontot

##### Konfigurera förhandskraven för NDES-servern

1.  DU måste logga in som en **Företagsadministratör**på servern som står värd för NDES och sedan använda [guiden Lägg till roller och funktioner](https://technet.microsoft.com/library/hh831809.aspx) för att installera NDES:

    1.  I guiden väljer du **Active Directory-certifikattjänster** för att få tillgång till AD CS-rolltjänsterna. Välj **Registreringstjänsten för nätverksenheten**, avmarkera **Certifikatutfärdare**och slutför guiden.

        > [!TIP]
        > Klicka inte på **Stäng** på sidan **Installationsförlopp**i guiden. Klicka istället på länken **Konfigurera Active Directory-certifikattjänster på målservern**. Då öppnas guiden **AD CS-konfiguration** som du använder för nästa åtgärd. När AD CS-konfiguration öppnats stänger du guiden Lägg till roller och funktioner.

    2.  När NDES läggs till på servern installerar guiden även IIS. Kontrollera att IIS har följande konfigurationer:

        -   **Webbserver** &gt; **Säkerhet** &gt; **Begäransfiltrering**

        -   **Webbserver** &gt; **Programutveckling** &gt; **ASP.NET 3.5**. Om du installerar ASP.NET 3.5 installeras även .NET Framework 3.5. När du installerar .NET Framework 3.5 installerar du både kärnfunktionen **.NET Framework 3.5** och **HTTP-aktivering**

        -   **Webbserver** &gt; **Programutveckling** &gt; **ASP.NET 4.5**. Om du installerar ASP.NET 4,5 installeras även .NET Framework 4,5. När du installerar .NET Framework 4.5 installerar du kärnfunktionen **.NET Framework 4.5**, **ASP.NET 4.5** och funktionen **WCF-tjänster** &gt; **HTTP-aktivering**.

        -   **Hanteringsverktyg** &gt; **IIS 6-kompatibilitetshantering** &gt; **IIS 6-metabaskompatibilitet**

        -   **Hanteringsverktyg** &gt; **IIS 6-kompatibilitetshantering** &gt; **IIS 6 WMI-kompatibilitet**

2.  Lägg till NDES-tjänstkontot som en medlem i gruppen **IIS_IUSR** på servern.

3.  Kör följande kommando för att ange SPN för NDES-tjänstkontot:

    -   **setspn -s http/&lt;DNS-namn för NDES-server&gt; &lt;Domännamn&gt;\&lt;NDES-tjänstkontots namn&gt;**

    Exempel: om NDES-serverns namn är **Server01**, domänen är **Contoso.com**och tjänstkontot är **NDESService**, använd:

    -   **setspn –s http/Server01.contoso.com contoso\NDESService**

## Uppgift 3 (endast SCEP-profil) – Konfigurera NDES för användning med Microsoft Intune 
I det här steget kommer du att:

-   Konfigurera NDES för användning med den utfärdande certifikatutfärdaren

-   Binda serverautentiseringscertifikatet (SSL) i IIS

-   Konfigurera begäransfiltrering i IIS

##### Konfigurera NDES för användning med Intune

1.  Öppna guiden AD CS-konfiguration och gör följande konfigurationer på NDES-servern.

    > [!TIP]
    > Om du klickade på länken i föregående åtgärd är guiden redan öppen. Annars öppnar du Serverhanteraren för att komma åt konfigurationen efter distribution för Active Directory-certifikattjänster.

    -   På sidan **Rolltjänster** väljer du **Registreringstjänsten för nätverksenheter**

    -   På sidan **Tjänstkonto för NDES** anger du NDES-tjänstkontot.

    -   På sidan **Certifikatutfärdare för NDES** klickar du på **Välj**och väljer sedan den utfärdande certifikatutfärdaren där du konfigurerade certifikatmallen.

    -   På sidan **Kryptografi för NDES** ställer du in nyckellängden enligt företagets krav.

    Klicka på **Konfigurera** på sidan **Bekräftelse** för att slutföra guiden.

2.  När guiden är slutförd redigerar du följande registernyckel på NDES-servern:

    -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\*\**

    När du ska redigera den här nyckeln identifierar du certifikatmallarnas **Syfte**, som finns under fliken **Hantering av begäranden** och redigerar sedan motsvarande post i registret genom att ersätta den befintliga informationen med namnet på den certifikatmall (inte mallens visningsnamn) som du angav i Uppgift 1. I följande tabell visas certifikatmallens syfte för värdena i registret:

    |Certifikatmallens syfte (på fliken Hantering av begäranden)|Registervärde som redigeras|Värde som visas i Intune-administratörskonsolen för SCEP-profilen|
    |--------------------------------------------------------------|--------------------------|------------------------------------------------------------------------------------------------------------|
    |Signatur|SignatureTemplate|Digital signatur|
    |Kryptering|EncryptionTemplate|Nyckelchiffrering|
    |Signatur och kryptering|GeneralPurposeTemplate|Nyckelchiffrering<br /><br />Digital signatur|
    Exempel: Om syftet för certifikatmallen är **Kryptering**, ersätter du värdet **EncryptionTemplate** värdet med namnet på certifikatmallen.

3.  När du redigerat registret, kör **iisreset** på servern för att tvinga servern att hämta senaste konfigurationsändringar.

##### Så här installerar och binder du certifikat på NDES-servern

1.  På NDES-servern: begär och installera ett certifikat för **serverautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Bind sedan SSL-certifikatet i IIS.

    > [!TIP]
    > När du bundit SSL-certifikatet i IIS installerar du ett certifikat för klientautentisering. Det här certifikatet kan utfärdas av vilken certifikatutfärdare som helst som är betrodd av NDES-servern. Även om det inte rekommenderas, kan du använda samma certifikat för både server- och klientautentisering så länge som certifikatet har båda förbättrade nyckelanvändningar (EKU). Granska följande steg för information om dessa certifikat för autentisering.

    1.  När du har fått certifikat för serverautentisering, öppnar du **IIS-hanteraren**, väljer **Standardwebbplats** i rutan **Anslutningar** och klickar sedan på **Bindningar** i rutan **Åtgärder** .

    2.  Klicka på **Lägg till**, ställ in **Typ** till **https**och kontrollera att porten är **443**. (Endast port 443 stöds för fristående Intune).

    3.  För **SSL-certifikat**anger du certifikatet för serverautentiserning.

        > Om NDES-servern använder både ett externt och ett internt namn för en enda nätverksadress, måste certifikatet för serverautentisering ha ett **Ämnesnamn** med ett externt offentligt servernamn och ett **Alternativt ämnesnamn** som innehåller namnet på den interna servern.

2.  På NDES-servern: begär och installera ett certifikat för **klientautentisering** från den interna certifikatutfärdaren eller en offentlig certifikatutfärdare. Detta kan vara samma certifikat som certifikatet för serverautentisering om certifikatet har båda funktioner.

    Certifikatet för klientautentisering måste ha följande egenskaper:

    **Förbättrad nyckelanvändning** – Måste innehålla **Klientautentisering**

    **Ämnesnamn** – Måste vara samma som DNS-namnet på servern där du installerar certifikatet (NDES-servern).

##### Så här konfigurerar du IIS-begäransfiltrering

1.  På NDES-servern öppnar du **IIS-hanteraren**, väljer **Standardwebbplats** i rutan **Anslutningar** och öppnar sedan **Begäransfiltrering**

2.  Klicka på **Redigera funktionsinställningar**och ställ in följande:

    **frågesträng (byte)** = **65534**

    **Maximal URL-längd (byte)** = **65534**

3.  Granska följande registernyckel:

    **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters**

    Kontrollera att följande värden anges som DWORD-poster:

    Namn: **MaxFieldLength**, med decimalvärdet **65534**

    Namn: **MaxRequestBytes**, med decimalvärdet **65534**

4.  Starta om NDES-servern. Servern är nu klar att stödja Certifikat Connectorn.

## Uppgift 4 - Aktivera, installera och konfigurera Intunes certifikat connector - För SCEP- och .PFX-certifikat.
I det här steget kommer du att:

Aktivera stöd för NDES i Intune

Ladda ner, installera och konfigurera Certifikat connectorn på NDES-servern

##### Så här aktiverar du stöd för Certifikat Connectorn

1.  Öppna [Intune-administrationskonsolen](https://manage.microsoft.com), klicka på **Admin** &gt; **Certifikatanslutningsapp**

2.  Klicka på **Konfigurera lokal certifikatanslutningsapp**

3.  Välj **Aktivera certifikatanslutningsapp** och klicka sedan på **OK**

##### Så här laddar du ner, installerar och konfigurerar Certifikat Connectorn

1.  Öppna [Intune-administrationskonsolen](https://manage.microsoft.com) och klicka sedan på **Admin** &gt; **Hantering av mobila enheter** &gt; **Certifikatanslutningsapp** &gt; **Ladda ned certifikatanslutningsappen**

2.  När nedladdningen är klar så kör du det nedladdade installationsprogrammet (**ndesconnectorssetup.exe**):

    -   För .PFX-certifikat, kör installationsprogrammet på datorn som kan ansluta till certifikatutfärdaren. Välj PFX-distributionsalternativet och klicka sedan på Installera. När installationen är slutförd fortsätter du genom att skapa en certifikatprofil enligt beskrivningen i [Konfigurera certifikatprofiler](configure-intune-certificate-profiles.md)

    -   För SCEP-certifikat, kör installationsprogrammet på en Windows Server 2012 R2 server

    För SCEP-alternativet så installerar installationsprogrammet också en policymodul för NDES och CRP-webbtjänst. (CRP-webbtjänsten, CertificateRegistrationSvc, körs som ett program i IIS).

    > [!NOTE]
    > När du installerar NDES för fristående Intune installeras CRP-tjänsten automatiskt med certifikatanslutningsappen. När du använder Intune med Configuration Manager installerar du certifikatregistreringsplatsen som en separat platssystemroll.

3.  När du tillfrågas om klientcertifikatet för Certifikat Connectorn så klickar du på **Välj**och väljer det certifikat för **klientautentisering** som du installerat på NDES-servern i Uppgift 3.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas, klicka på **Nästa** för att visa egenskaperna för certifikatet. Klicka sedan på **Nästa** och på **Installera**

4.  När guiden har slutförts klickar du på **Starta användargränssnittet för certifikatanslutningsappen** innan du stänger guiden

    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  I användargränssnittet för **certifikat connectorn** :

    Klicka på **Logga in** och ange autentiseringsuppgifter för en tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

    Om organisationen använder en proxyserver och proxyn krävs för att NDES-servern ska få tillgång till Internet klickar du på **Använd proxyserver** och anger proxyservernamn, port och autentiseringsuppgifter för att ansluta.

    Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren. Klicka sedan på **Använd**

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

6.  Öppna kommandotolken och skriv **services.msc**. Tryck sedan på **Retur**, högerklicka på **certifikatanslutningstjänsten** och klicka sedan på **Starta om**

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL, vilket borde returnera ett **403** -fel:

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Nästa steg
Du är nu redo att konfigurera certifikatprofiler enligt beskrivningen i [Konfigurera certifikatprofiler](configure-intune-certificate-profiles.md)


<!--HONumber=May16_HO2-->


