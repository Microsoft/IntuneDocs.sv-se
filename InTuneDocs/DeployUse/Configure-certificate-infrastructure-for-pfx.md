---
title: "Konfigurera certifikatinfrastrukturen för PFX | Microsoft Intune"
description: Skapa och distribuera .PFX-certifikatprofiler.
keywords: 
author: nbigman
manager: angrobe
ms.date: 05/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f400f8b2ffd85b6328eceb74b97de1e67203ee6b
ms.openlocfilehash: 7376713410e802ffbee6238e7242e6d8ecc204df



---
# Konfigurera certifikatinfrastruktur för PFX
Det här avsnittet beskriver vad du behöver för att skapa och distribuera .PFX-certifikatprofiler.

Om du vill utföra certifikatbaserad autentisering i organisationen måste du ha en utfärdare av företagscertifikat.

Om du vill använda .PFX-certifikatprofiler behöver du, förutom utfärdaren av företagscertifikat:

-   En dator som kan kommunicera med certifikatutfärdaren; du kan även använda den dator som fungerar som certifikatutfärdare.

 -  Intunes certifikat Connector, som körs på datorn som kan kommunicera med certifikatutfärdaren.

## Beskrivning av lokal infrastruktur


-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare** (CA): En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).

 -  **En dator som kan kommunicera med certifikatutfärdaren**: Du kan också använda den dator som fungerar som certifikatutfärdare.
-  **Microsoft Intune-certifikatanslutningsapp**: Använd Intune-administratörskonsolen för att hämta installationsprogrammet för **Certifikatanslutningsapp** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector. För. PFX-certifikatprofiler, installera certifikat connector på datorn som kommunicerar med certifikatutfärdaren.
-  **Webbprogramsproxyserver** (valfritt): Du kan använda en server som kör Windows Server 2012 R2 eller senare som en webbprogramproxyserver (WAP, Web Application Proxy). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

 > [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter. Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramsproxy](http://technet.microsoft.com/library/dn584113.aspx).|


### Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Du konfigurerar den här mallen på den utfärdande certifikatutfärdaren.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **CER** -fil från den utfärdande certifikatutfärdare eller en enhet som litar på certifikatutfärdaren och distribuerar den till enheter med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|


## Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du utföra följande åtgärder, som kräver kunskaper om Windows Server 2012 R2 och Active Directory-certifikattjänster (ADCS):

**Uppgift 1** – Konfigurera certifikatmallar på certifikatutfärdaren **Uppgift 2** – Aktivera, installera och konfigurera Intunes certifikatanslutningsapp

### Uppgift 1 – konfigurera certifikatmallar på certifikatutfärdaren
I det här steget kommer du att publicera certifikatmallen

##### Så här konfigurerar du certifikatutfärdaren

1.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatmallar och skapar en ny anpassad mall eller kopierar en befintlig mall och redigerar sedan en befintlig mall (t.ex. mallen Användare) för användning med .pFX.

    Mallen måste ha följande konfigurationer:

    -   Ange ett eget **visningsnamn för mallen** .

    -   På fliken **Ämnesnamn** väljer du **Anges i begäran**. (Säkerhet tvingas av Intune-principmodulen för NDES).

    -   På fliken **Tillägg** kontrollerar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**.

        > [!IMPORTANT]
        > För iOS- och Mac OS X-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.


3.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > [!IMPORTANT]
    > iOS- och Mac OS X-plattformen använder alltid värdet i mallen, oavsett andra konfigurationer som du gör.

    Om du vill konfigurera certifikatutfärdaren att tillåta att den som begär anger giltighetsperioden, kör du följande kommandon på certifikatutfärdaren:

    1.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    2.  **net stop certsvc**

    3.  **net start certsvc**

4.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.

    1.  Välj noden **Certifikatmallar**, klicka på **Åtgärd**-&gt; **Ny** &gt; **Certifikatmall som ska utfärdas**, och välj sedan den mall som du skapade i steg 2.

    2.  Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .

5.  På certifikatutfärdardatorn se du till att den dator som har Intunes certifikatanslutningsapp har registreringsrättigheter, så att den kommer åt den mall som användes för att skapa .PFX-profilen. Ställ in behörighet på **säkerhetsfliken** i datoregenskaper för Certifikatutfärdar-datorn.

### Uppgift 2 – Aktivera, installera och konfigurera Intune-certifikatanslutningsappen
I det här steget kommer du att:

Hämta, installera och konfigurera certifikatanslutningsappen

##### Så här aktiverar du stöd för Certifikat Connectorn

1.  Öppna [administrationskonsolen för Intune](https://manage.microsoft.com), klicka på **Admin** &gt; **Certifikatanslutningsapp**.

2.  Klicka på **Konfigurera lokal certifikatanslutningsapp**.

3.  Välj **Aktivera Certifikat Connector**och klicka sedan på **OK**.

##### Så här laddar du ner, installerar och konfigurerar Certifikat Connectorn

1.  Öppna [administratörskonsolen i Intune](https://manage.microsoft.com) och klicka sedan på **Admin** &gt; **Hantering av mobila enheter** &gt; **Certifikatanslutningsapp** &gt; **Ladda ned certifikatanslutningsappen**.

2.  När nedladdningen är klar så kör du det nedladdade installationsprogrammet (**ndesconnectorssetup.exe**):

  Kör installationsprogrammet på den dator som kan ansluta med certifikatutfärdaren. Välj PFX-distributionsalternativet och klicka sedan på Installera. När installationen har slutförts fortsätter du genom att skapa en certifikatprofil enligt beskrivningen i [Konfigurera certifikatprofiler](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  När du tillfrågas om klientcertifikatet för certifikatanslutningsappen klickar du på **Välj**och väljer det certifikat för **klientautentisering** som du installerade i uppgift 3.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas, klicka på **Nästa** för att visa egenskaperna för certifikatet. Klicka sedan på **Nästa**och på **Installera**.

4.  När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

    > [!TIP]
    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  I användargränssnittet för **certifikat connectorn** :

    Klicka på **Logga in** och ange autentiseringsuppgifter för en tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

  <!--  If your organization uses a proxy server and the proxy is needed for the NDES server to access the Internet, click **Use proxy server** and then provide the proxy server name, port, and account credentials to connect.-->

    Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren. Klicka sedan på **Använd**.

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

6.  Öppna kommandotolken och skriv **services.msc**. Tryck sedan på **Retur**, högerklicka på **Intune-anslutningstjänsten** och klicka sedan på **Starta om**.

Kontrollera att tjänsten körs genom att öppna en webbläsare och ange följande URL, vilket borde returnera ett **403** -fel:

**http:// &lt;FQDN_of_your_NDES_server&gt;/certsrv/mscep/mscep.dll**

### Nästa steg
Du är nu redo att konfigurera certifikatprofiler enligt beskrivningen i [Konfigurera certifikatprofiler](Configure-Intune-certificate-profiles.md).



<!--HONumber=Aug16_HO3-->


