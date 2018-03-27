---
title: Konfigurera certifikatinfrastruktur för PFX
description: Skapa och distribuera .PFX-certifikatprofiler.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/17/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: vinaybha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a19dbd6ad2b65e7d2d090b543f3e2200180c660a
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="configure-certificate-infrastructure"></a>Konfigurera infrastrukturen för certifikat

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver vad du behöver för att skapa och distribuera .PFX-certifikatprofiler.

Om du vill utföra certifikatbaserad autentisering i organisationen måste du ha en utfärdare av företagscertifikat.

Om du vill använda .PFX-certifikatprofiler behöver du, förutom utfärdaren av företagscertifikat:

-   En dator som kan kommunicera med certifikatutfärdaren; du kan även använda den dator som fungerar som certifikatutfärdare.

-  Intunes certifikat Connector, som körs på datorn som kan kommunicera med certifikatutfärdaren.

## <a name="on-premises-infrastructure-description"></a>Beskrivning av lokal infrastruktur


-    **Active Directory-domän**: Alla servrar i det här avsnittet (förutom webbprogramsproxyservern) måste vara anslutna till Active Directory-domänen.

-  **Certifikatutfärdare**: En utfärdare av företagscertifikat som körs på en Enterprise-version av Windows Server 2008 R2 eller senare. En fristående certifikatutfärdare stöds inte. Instruktioner om hur du ställer in en certifikatutfärdare finns i [Install the Certification Authority](http://technet.microsoft.com/library/jj125375.aspx).
    Om certifikatutfärdaren kör Windows Server 2008 R2, måste du [installera snabbkorrigeringen från KB2483564](http://support.microsoft.com/kb/2483564/).

-  **En dator som kan kommunicera med certifikatutfärdaren**: Du kan också använda den dator som fungerar som certifikatutfärdare.
-  **Microsoft Intune-certifikatanslutningsapp**: Använd Intune-administratörskonsolen för att hämta installationsprogrammet för **Certifikatanslutningsapp** (**ndesconnectorssetup.exe**). Sen kör du **ndesconnectorssetup.exe** på datorn där du vill installera Certifikat Connector. För. PFX-certifikatprofiler, installera certifikat connector på datorn som kommunicerar med certifikatutfärdaren.
-  **Webbprogramsproxyserver** (valfritt): Du kan använda en server som kör Windows Server 2012 R2 eller senare som en webbprogramproxyserver (WAP, Web Application Proxy). Den här konfigurationen:
    -  Tillåter enheter att ta emot certifikat med hjälp av en internetanslutning.
    -  Är en säkerhetsrekommendation när enheter ansluter via internet för att ta emot och förnya certifikat.

 > [!NOTE]           
> -    Servern som är värd för WAP [måste installera en uppdatering](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) som aktiverar stöd för de långa URL:er som används av registreringstjänsten för nätverksenheter (NDES). Uppdateringen finns med i [samlad uppdatering för december 2014](http://support.microsoft.com/kb/3013769), eller individuellt från [KB3011135](http://support.microsoft.com/kb/3011135).
>-  Dessutom måste den server som är värd för WAP ha ett SSL-certifikat som överensstämmer med det namn som publiceras på externa klienter, samt lita på SSL-certifikatet som används på NDES-servern. Certifikaten gör det möjligt för WAP servern att avbryta SSL-anslutningen från klienter och skapa en ny SSL-anslutning till NDES-servern.
    Information om certifikat för WAP finns i sektionen **Planera certifikat** av [Installera och konfigurera webbprogramproxy för publicering av interna program](https://technet.microsoft.com/library/dn383650.aspx). Allmän information om WAP-servrar finns i [Arbeta med webbprogramsproxy](http://technet.microsoft.com/library/dn584113.aspx).|


### <a name="certificates-and-templates"></a>Certifikat och mallar

|Objekt|Information|
|----------|-----------|
|**Certifikatmall**|Du konfigurerar den här mallen på den utfärdande certifikatutfärdaren.|
|**Certifikat från betrodd rotcertifikatutfärdare**|Du exporterar detta som en **CER** -fil från den utfärdande certifikatutfärdare eller en enhet som litar på certifikatutfärdaren och distribuerar den till enheter med hjälp av certifikatprofilen för den betrodda certifikatutfärdaren.<br /><br />Du använder ett enstaka certifikat från en betrodd rotcertifikatutfärdare per operativsystemplattform och associerar det med varje betrodd rotcertifikatprofil som du skapar.<br /><br />Du kan använda ytterligare certifikat från betrodda rotcertifikatutfärdare när det behövs. Exempel: du kan göra detta för att ge ett förtroende till en certifikatutfärdare som signerar serverautentiseringscertifikaten för dina WiFi-åtkomstpunkter.|


## <a name="configure-your-infrastructure"></a>Konfigurera infrastrukturen
Innan du kan konfigurera certifikatprofiler måste du slutföra följande uppgifter. Dessa uppgifter kräver kunskaper om Windows Server 2012 R2 och Active Directory Certificate Services (ADCS):

- **Uppgift 1** – Konfigurera certifikatmallar på certifikatutfärdaren.
- **Uppgift 2** – Aktivera, installera och konfigurera Intune-certifikatanslutningsappen.

### <a name="task-1---configure-certificate-templates-on-the-certification-authority"></a>Uppgift 1 – konfigurera certifikatmallar på certifikatutfärdaren
I det här steget kommer du att publicera certifikatmallen.

##### <a name="to-configure-the-certification-authority"></a>Så här konfigurerar du certifikatutfärdaren

1.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatmallar och skapar en ny anpassad mall eller kopierar och redigerar en befintlig mall (t.ex. mallen Användare) för användning med .PFX.

    Mallen måste innefatta följande:

    -   Ange ett eget **visningsnamn för mallen** .

    -   På fliken **Ämnesnamn** väljer du **Anges i begäran**. 

    -   På fliken **Tillägg** kontrollerar du att **beskrivningen av användningsprinciper** omfattar **Klientautentisering**.

        > [!IMPORTANT]
        > För iOS- och Mac OS X-certifikatmallar: På fliken **Tillägg** redigerar du **Nyckelanvändning** och ser till att **Signaturen är bevis för ursprung** inte är markerat.

2.  Granska **Giltighetsperioden** på mallens flik **Allmänt** . Som standard använder Intune värdet som konfigurerats i mallen. Du kan dock välja att konfigurera certifikatutfärdaren att tillåta att den som begär anger ett annat värde, som du sedan kan ställa in i Intune-administratörskonsolen. Om du alltid vill använda värdet i mallen kan du hoppa över resten av det här steget.

    > [!IMPORTANT]
    > iOS- och Mac OS X-plattformen använder alltid värdet i mallen, oavsett vilka andra inställningar du gör.

    Om du vill konfigurera certifikatutfärdaren att tillåta att beställaren anger giltighetsperioden, kör du följande kommandon på certifikatutfärdaren:

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b.  **net stop certsvc**

    c.  **net start certsvc**

3.  På den utfärdande certifikatutfärdaren använder du snapin-modulen för certifikatutfärdaren för att publicera certifikatmallen.

    a.  Välj noden **Certifikatmallar**, klicka på **Åtgärd** -&gt;**Ny** &gt; **Certifikatmall som ska utfärdas** och välj sedan den mall som du skapade i steg 2.

    b.  Kontrollera att mallen publicerats genom att se om den finns i mappen **Certifikatmallar** .

4.  På certifikatutfärdardatorn ser du till att den dator som har Intunes certifikatanslutningsapp har registreringsrättigheter, så att den kommer åt den mall som användes för att skapa .PFX-profilen. Ställ in behörighet på **säkerhetsfliken** i datoregenskaper för Certifikatutfärdar-datorn.

### <a name="task-2---enable-install-and-configure-the-intune-certificate-connector"></a>Uppgift 2 – Aktivera, installera och konfigurera Intune-certifikatanslutningsappen
I det här steget kommer du att:

Hämta, installera och konfigurera certifikatanslutningsappen.

##### <a name="to-enable-support-for-the-certificate-connector"></a>Så här aktiverar du stöd för Certifikat Connectorn

1.  Öppna [Intune-administratörskonsolen](https://manage.microsoft.com) och välj **Admin** &gt; **Certifikatanslutningsapp**.

2.  Välj **Konfigurera lokal certifikatanslutningsapp**.

3.  Markera **Aktivera certifikatanslutningsapp** och välj sedan **OK**.

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>Så här laddar du ned, installerar och konfigurerar certifikatanslutningsappen

1.  Öppna [administratörskonsolen i Intune](https://manage.microsoft.com) och välj sedan **Admin** &gt; **Hantering av mobila enheter** &gt; **Certifikatanslutningsapp** &gt; **Ladda ned certifikatanslutningsappen**.

2.  När nedladdningen är klar så kör du det nedladdade installationsprogrammet (**ndesconnectorssetup.exe**).

  Kör installationsprogrammet på den dator som kan ansluta med certifikatutfärdaren. Välj PFX-distributionsalternativet och klicka sedan på **Installera**. När installationen har slutförts fortsätter du genom att skapa en certifikatprofil enligt beskrivningen i [Konfigurera certifikatprofiler](configure-intune-certificate-profiles.md).

   <!-- Not sure about step 3 below -->

3.  När du tillfrågas om klientcertifikatet för certifikatanslutningsappen väljer du **Välj** och väljer det certifikat för **klientautentisering** som du installerade i uppgift 3.

    När du har valt certifikatet för klientautentisering tas du tillbaka till ytan **Klientcertifikat för Microsoft Intune Certifikat Connector** . Även om certifikatet du valt inte visas väljer du **Nästa** för att visa egenskaperna för certifikatet. Välj **Nästa** och sedan **Installera**.

4.  När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

    > [!TIP]
    > Om du stängt guiden innan du startade användargränssnittet kan du öppna det genom att skriva följande kommando:
    >
    > **&lt;install_Path&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  I användargränssnittet för **certifikat connectorn** :

    a. Välj **Logga in** och ange dina autentiseringsuppgifter som tjänstadministratör i Intune eller för en klientadministratör med behörighet för global administration.

    b. Välj fliken **Avancerat** och ange autentiseringsuppgifter för ett konto som har behörigheten **Utfärda och hantera certifikat** på den utfärdande certifikatutfärdaren.

    c. Välj **Använd**.

    Nu kan du stänga användargränssnittet för Certifikat Connectorn.

6.  Öppna en kommandotolk och skriv **services.msc**. Tryck på **Retur**, högerklicka på **Intune-anslutningstjänsten** och välj **Starta om**.


### <a name="next-steps"></a>Nästa steg
Du är nu redo att konfigurera certifikatprofiler enligt beskrivningen i [Konfigurera certifikatprofiler](Configure-Intune-certificate-profiles.md).
