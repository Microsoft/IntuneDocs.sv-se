---
title: Använda certifikat med privata och offentliga nycklar i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa ett Public Key Cryptography Standards-certifikat (PKCS) med Microsoft Intune, inklusive stegen för att exportera ett rotcertifikat, konfigurera certifikatmallen, ladda ned och installera Intune-certifikatanslutningsappen (NDES), skapa en profil för enhetskonfiguration samt skapa en PKCS-certifikatprofil i Azure och din certifikatutfärdare.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ee5ef1b5c59bbef3834d44354508b767ae99088
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722936"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurera och använda PKCS-certifikat med Intune

Intune stöder användning av PKCS-certifikat (privata och offentliga nyckelpar). Den här artikeln kan hjälpa dig att konfigurera den nödvändiga infrastrukturen som lokala certifikatanslutningsappar, exportera ett PKCS-certifikat och sedan lägga till certifikatet i en Intune-enhetskonfigurationsprofil.

Microsoft Intune innehåller inbyggda inställningar för att använda PKCS-certifikat för åtkomst och autentisering till organisationens resurser. Certifikat autentiserar och skyddar åtkomst till dina företagsresurser, till exempel ett VPN- eller Wi-Fi-nätverk. Du distribuerar de här inställningarna till enheter med hjälp av enhetskonfigurationsprofiler i Intune.

Information om användning av importerade PKCS-certifikat finns i [Importerade PFX-certifikat](certificates-imported-pfx-configure.md).


## <a name="requirements"></a>Krav

Om du vill använda PKCS-certifikat med Intune behöver du följande infrastruktur:

- **Active Directory-domän**:  
  Alla servrar i det här avsnittet måste vara anslutna till Active Directory-domänen.

  Mer information om att installera och konfigurera Active Directory Domain Services (AD DS) finns i [Design och planering för AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Certifikatutfärdare**:  
   En utfärdare av företagscertifikat (CA).

  Information om hur du installerar och konfigurerar Active Directory Certificate Services (AD CS) finns i [den stegvisa guiden för Active Directory Certificate Services](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]  
  > Intune kräver att du kör AD CS med en Enterprise-certifikatutfärdare (CA), inte en fristående CA.

- **En klient**:  
  För att ansluta till företags-CA.

- **Rotcertifikat**:  
  En exporterad kopia av ditt rotcertifikat från din Enterprise-CA.

- **Microsoft Intune Certificate Connector** (kallas även *NDES Certificate Connector*):  
  I Intune-portalen går du till **Enhetskonfiguration** > **Certifikatanslutningsappar** > **Lägg till** och följer *stegen för att installera anslutningsappen för PKCS #12*. Använd nedladdningslänken i portalen för att påbörja nedladdningen av installationsprogrammet för certifikatanslutningsappen: **NDESConnectorSetup.exe**.  

  Intune har stöd för upp till 100 instanser av den här anslutningen per klient, med varje instans på en separat Windows Server. Du kan installera en instans av den här anslutningen på samma server som en instans av PFX-certifikatanslutningsappen för Microsoft Intune. När du använder flera kopplingar stöder kopplingsinfrastrukturen hög tillgänglighet och belastningsutjämning eftersom alla tillgängliga anslutningsinstanser kan bearbeta dina PKCS-certifikatbegäranden. 

  Anslutningsappen bearbetar PKCS-certifikatbegäranden som används för autentisering eller S/MIME-signering för e-post.

  Microsoft Intune Certificate Connector har även stöd för FIPS-läge (Federal Information Processing Standard). FIPS krävs inte, men du kan utfärda och återkalla certifikat när det är aktiverat.

- **PFX-certifikatanslutningsprogram för Microsoft Intune**:  
  Om du planerar att använda S/MIME-kryptering för e-post använder du Intune-portalen för att ladda ned *PFX-anslutningsappen* som stöder import av PFX-certifikat.  Gå till **Enhetskonfiguration** > **Certifikatanslutningsappar** > **Lägg till** och följer *stegen för att installera anslutningsapp för importerade PFX-certifikat*. Använd nedladdningslänken i portalen för att påbörja nedladdningen av installationsprogrammet **PfxCertificateConnectorBootstrapper.exe**. 

  Varje Intune-klient har stöd för en enda instans av den här anslutningen. Du kan installera den här anslutningen på samma server som en instans av Microsoft Intune Certificate Connector.

  Anslutningsappen hanterar begäranden för PFX-filer som importeras till Intune för S/MIME-kryptering av e-post för en specifik användare.  

  Den här anslutningsappen kan uppdatera sig automatiskt när nya versioner blir tillgängliga. För att kunna uppdatera kapaciteten behöver du:
  - Installera anslutningsappen för PFX-certifikat för Microsoft Intune på din server.  
  - För att automatiskt få viktiga uppdateringar ser du till att brandväggarna är öppna så att anslutningsappen tillåts kontakta **autoupdate.msappproxy.net** på port **443**.   

  Mer information om nätverksslutpunkter som Intune och anslutningsappen måste kunna få åtkomst till finns i [Nätverksslutpunkter för Microsoft Intune](../fundamentals/intune-endpoints.md).

- **Windows Server**:  
  Du använder en Windows Server som värd för:

  - Microsoft Intune-certifikatanslutningsapp – för scenarier med autentisering och S/MIME-signering av e-post
  - PFX-certifikatanslutningsapp för Microsoft Intune – för scenarier med S/MIME-kryptering av e-post.

  Intune stöder installation av *PFX-certifikatanslutningsappen* på samma server som *Microsoft Intune Certificate Connector*.
  
## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportera rotcertifikatet från Enterprise-CA:n

För en enhet ska autentiseras med VPN, Wi-Fi eller andra resurser behöver enheten ett rot-CA-certifikat eller ett mellanliggande CA-certifikat. Följande steg förklarar hur du hämtar nödvändiga certifikat från din Enterprise CA.

**Använda en kommandorad**:  
1. Logga in på servern för rotcertifikatutfärdare med ett administratörskonto.
 
2. Gå till **Start** > **Kör** och ange **Cmd** för att öppna kommandotolken. 
    
3. Ange **certutil -ca.cert ca_name.cer** för att exportera rotcertifikatet som en fil med namnet *ca_name.cer*.



## <a name="configure-certificate-templates-on-the-ca"></a>Konfigurera certifikatmallar på CA

1. Logga in på din Enterprise CA med ett konto som har administratörsbehörighet.
2. Öppna konsolen **Certifikatutfärdare**, högerklicka på **Certifikatmallar** och välj **Hantera**.
3. Leta upp certifikatmallen **Användare**, högerklicka på den och välj **Duplicera mall**. **Egenskaper för ny mall** öppnas.

    > [!NOTE]
    > För scenarier med S/MIME-signering och kryptering av e-post använder många administratörer separata certifikat för signering och kryptering. Om du använder Microsoft Active Directory-certifikattjänster kan du använda mallen **Exchange Signature Only** (Endast Exchange-signatur) för certifikat för S/MIME-e-postsignering och mallen **Exchange User** (Exchange-användare) för S/MIME-krypteringscertifikat.  Om du använder en tredje parts certifikatutfärdare rekommenderas det att du granskar deras vägledning för att konfigurera mallar för signering och kryptering.

4. På fliken **Kompatibilitet**:

    - Ställ in **certifikatutfärdare** till **Windows Server 2008 R2**
    - Ställ in **certifikatmottagare** till **Windows 7 / Server 2008 R2**

5. På fliken **Allmänt** ställer du in **Mallens visningsnamn** till något som betyder något för dig.

    > [!WARNING]
    > **Mallnamnet** är som standard samma som **mallens visningsnamn** med *inga blanksteg*. Anteckna mallens namn. Du behöver det senare.

6. I **Hantering av begäranden** väljer du **Tillåt att den privata nyckeln exporteras**.
7. I **kryptografi** bekräftar du att den **minsta nyckelstorleken** är inställd på 2048.
8. I **Ämnesnamn** väljer du **Anges i begäran**.
9. I **Tillägg**, bekräftar du att du ser krypterar filsystem, säker e-post och klientautentisering under **användningsprinciper**.

    > [!IMPORTANT]
    > För iOS-certifikatmallar: uppdatera **Nyckelanvändning** på fliken **Tillägg** och kontrollera att **Signaturen är bevis för ursprung** inte har markerats.

10. I **säkerhet** lägger du till datorkontot för den server där du installerar Microsoft Intune Certificate Connector. Ge det här kontot **läs-** och **registrera**-behörigheter.
11. Välj **Tillämpa** > **OK** för att spara certifikatmallen. Stäng **konsolen för certfikatmallar**.
12. I konsolen **Certifikatutfärdare** högerklickar du på **Certifikatmallar** > **Ny** > **Certifikatmall som ska utfärdas**. Välj den mall som du skapade i föregående steg. Välj **OK**.
13. Använd följande steg för att servern ska hantera certifikat för registrerade enheter och användare:

    1. Högerklicka på certifikatutfärdaren och välj **egenskaper**.
    2. På fliken för säkerhet lägger du till datorkontot för den server där du kör anslutningsapparna (**Microsoft Intune-certifikatanslutningsapp** eller **PFX-certifikatanslutningsapp för Microsoft Intune**). 
    3. Bevilja behörigheterna **utfärda och hantera certifikat** och **begära certifikat** till datorkontot.

14. Logga ut från Enterprise-CA:n.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Ladda ned, installera och konfigurera Microsoft Intune Certificate Connector

> [!IMPORTANT]  
> Microsoft Intune-certifikatanslutningsappen kan inte installeras på den utfärdande certifikatutfärdaren (CA) och måste i stället installeras på en separat Windows-server.  

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Certifikatanslutningsappar** > **Lägg till**.
3. Ladda ned och spara anslutningsappfilen på en plats där du kan komma åt den från den server där du kommer att installera anslutningsappen.

    ![Microsoft Intune Certificate Connector nedladdning](./media/certficates-pfx-configure/download-ndes-connector.png)
 

4. När nedladdningen är klar loggar du in på servern. Efter det:

    1. Se till att .NET 4.5 Framework eller senare är installerat, eftersom det krävs av NDES-certifikatanslutningsappen. .NET 4.5 framework ingår automatiskt i Windows Server 2012 R2 och senare versioner.
    2. Kör installationsprogrammet (NDESConnectorSetup.exe) och godkänn standardplatsen. Anslutningsprogrammet installeras då till `\Program Files\Microsoft Intune\NDESConnectorUI`. Bland installationsalternativen väljer du **PFX-distribution**. Fortsätt och slutför installationen.
    3. Som standard körs anslutningsapptjänsten under det lokala systemkontot. Om en proxy krävs för att få åtkomst till Internet kontrollerar du att det lokala tjänstkontot kan komma åt proxyinställningarna på servern.

5. Microsoft Intune-certifikatanslutningsappen öppnar fliken **Registrering**. Om du vill aktivera anslutningen till Intune **Loggar du in** och anger ett konto med globala administratörsbehörigheter.
6. Vi rekommenderar att du på fliken **Avancerat** låter **Använd den här datorns systemkonto (standard)** vara markerat.
7. **Tillämpa** > **Stäng**
8. Gå tillbaka till Intune-portalen (**Intune** > **Enhetskonfiguration** > **Certifikatanslutningsappar**). Efter en stund visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.
9. Om du har en webbproxy i nätverksmiljön kan du behöva ytterligare konfigurationer för att anslutningsappen ska fungera. Mer information finns i [Arbeta med befintliga lokala proxyservrar](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) i Azure Active Directory-dokumentationen.

> [!NOTE]  
> Microsoft Intune-certifikatanslutningsappen har stöd för TLS 1.2. Om TLS 1.2 installeras på den server som är värd för anslutningsappen använder anslutningsappen TLS 1.2. I annat fall används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

1. I [Azure Portal](https://portal.azure.com) går du till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
    ![Navigera till Intune och skapa en ny profil för ett betrott certifikat](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. Ange följande egenskaper:

    - **Namnet** på profilen
    - Om du vill kan du ange en beskrivning
    - **Plattform** att distribuera profilen till
    - Ange **profiltypen** som **betrott certifikat**

3. Gå till **Inställningar** och ange .cer-filen med rot CA-certifikatet som du exporterade tidigare.

   > [!NOTE]
   > Beroende på vilken plattform du valde i **steg 2** kan du få alternativet att välja **målarkiv** för certifikatet.

   ![Skapa en profil och ladda upp ett betrott certifikat](./media/certficates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](../configuration/device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. I [Azure Portal](https://portal.azure.com) går du till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
2. Ange följande egenskaper:

    - **Namnet** på profilen
    - Om du vill kan du ange en beskrivning
    - **Plattform** att distribuera profilen till
    - Ange **profiltypen** som **PKCS-certifikat**

3. Gå till **Inställningar** och ange följande egenskaper:

    - **Tröskelvärde för förnyelse (%)** : 20 % rekommenderas.
    - **Certifikatets giltighetsperiod**: Om du inte har ändrat certifikatmallen kan det här alternativet anges till ett år.
    - **Nyckellagringsprovider (KSP)** : För Windows väljer du var du vill lagra nycklarna på enheten.
    - **Certifikatutfärdare**: Visar det interna fullständiga domännamnet (FQDN) för din Enterprise-CA.
    - **Namn på certifikatutfärdare**: Anger namnet på din Enterprise-CA, till exempel ”Contoso Certification Authority”.
    - **Certifikatmallens namn**: Namnet på den mall som du skapade tidigare. Kom ihåg att **mallnamnet** som standard är samma som **mallens visningsnamn** *utan blanksteg*.
    - **Ämnesnamnets format**: Ange det här alternativet som **Eget namn** om inget annat krävs.
    - **Alternativt namn för certifikatmottagare**: Ange det här alternativet som **Användarens huvudnamn** om inget annat krävs.

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](../configuration/device-profile-assign.md).

   > [!NOTE]
   > På enheter med en Android Enterprise-profil syns inte certifikat som har installerats med en PKCS-certifikatprofil på enheten. Kontrollera statusen för profilen i Intune-konsolen för att bekräfta lyckad certifikatdistribution.

## <a name="whats-new-for-connectors"></a>Nyheter för anslutningsappar
Uppdateringar för de två certifikatanslutningsapparna släpps regelbundet. När vi uppdaterar en anslutningsapp kan du läsa om ändringarna här. 

*PFX-certifikatanslutningsappen för Microsoft Intune* [har stöd för automatiska uppdateringar](#requirements), medan *Intune-certifikatanslutningsappen* uppdateras manuellt.

### <a name="may-17-2019"></a>17 maj 2019  
- **PFX-certifikatanslutningsprogram för Microsoft Intune – version 6.1905.0.404**  
  Ändringar i den här versionen:  
  - Åtgärdade ett problem där befintliga PFX-certifikat fortsätter att bearbetas, vilket gör att anslutningsappen slutar att bearbeta nya begäranden. 

### <a name="may-6-2019"></a>Den 6 maj 2019  
- **PFX-certifikatanslutningsprogram för Microsoft Intune – version 6.1905.0.402**  
  Ändringar i den här versionen:  
  - Avsökningsintervallet för anslutningsappen har minskats från 5 minuter till 30 sekunder.
 
### <a name="april-2-2019"></a>2 april 2019  
- **Intune-certifikatanslutningsapp – version 6.1904.1.0**  
  Ändringar i den här versionen:  
  - Åtgärdade ett problem där anslutningsappen kunde misslyckas med att registrera till Intune efter inloggning till anslutningsappen med ett konto för global administratör.  
  - Innehåller tillförlitlighetsåtgärder för certifikatåterkallande.  
  - Innehåller prestandaåtgärder som ökar hastigheten för bearbetning av PKCS-certifikatbegäranden.  

- **PFX-certifikatanslutningsprogram för Microsoft Intune – version 6.1904.0.401**
  > [!NOTE]  
  > Automatisk uppdatering för den här versionen av PFX-anslutningsappen är inte tillgänglig förrän den 11 april 2019.  

  Ändringar i den här versionen:  
  - Åtgärdade ett problem där anslutningsappen kunde misslyckas med att registrera till Intune efter inloggning till anslutningsappen med ett konto för global administratör.  


## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](../configuration/device-profile-assign.md) och [övervaka dess status](../configuration/device-profile-monitor.md).

[Använda SCEP för certifikat](certificates-scep-configure.md) eller [utfärda PKCS-certifikat från en Symantec PKI Manager-webbtjänst](certificates-digicert-configure.md).
