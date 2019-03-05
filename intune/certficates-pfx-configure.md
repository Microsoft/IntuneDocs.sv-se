---
title: Använda certifikat med privata och offentliga nycklar i Microsoft Intune – Azure | Microsoft Docs
description: Lägg till eller skapa ett Public Key Cryptography Standards-certifikat (PKCS) med Microsoft Intune, inklusive stegen för att exportera ett rotcertifikat, konfigurera certifikatmallen, ladda ned och installera Microsoft Intune Certificate Connector (NDES), skapa en profil för enhetskonfiguration, skapa en PKCS-certifikatprofil i Azure och din certifikatutfärdare.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87a7f7f77914b899b7173b8bfacb82cd0c50c6e7
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230048"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurera och använda PKCS-certifikat med Intune

Certifikat autentiserar och skyddar åtkomst till dina företagsresurser, till exempel ett VPN- eller Wi-Fi-nätverk. Certifikat som använder ett nyckelpar med privata och offentliga nycklar, och även kallas PKCS-certifikat, används i många organisationer. Microsoft Intune innehåller inbyggda inställningar för att använda PKCS-certifikat för åtkomst och autentisering till organisationens resurser. De här inställningarna skickas (eller distribueras) till enheter med hjälp av enhetskonfigurationsprofiler i Intune.

Den här artikeln innehåller kraven för att använda PKCS-certifikat, och visar hur du exporterar ett PKCS-certifikat och lägger till certifikatet i en enhetskonfigurationsprofil i Intune.

## <a name="requirements"></a>Krav

Om du vill använda PKCS-certifikat med Intune, måste du ha följande infrastruktur:

- **Active Directory-domän**: Alla servrar i det här avsnittet måste vara anslutna till Active Directory-domänen.

  Mer information om att installera och konfigurera AD DS finns i [Design och planering för AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Certifikatutfärdare**: En utfärdare av företagscertifikat (CA)

  Mer information om hur du installerar och konfigurerar Active Directory Certificate Services (AD CS) finns i artikeln [Active Directory Certificate Services stegvis guide](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune kräver att du kör AD CS med en Enterprise-certifikatutfärdare (CA), inte en fristående CA.

- **En klient**: För att ansluta till företags-CA

- **Rotcertifikat**: En exporterad kopia av rotcertifikatet från företags-CA

- **Microsoft Intune Certificate Connector**: Använd Azure-portalen för att ladda ner installationsprogrammet för **Certificate Connector** (**NDESConnectorSetup.exe**). 

  Anslutningsappen bearbetar PKCS-certifikatbegäranden som används för autentisering eller S/MIME-signering för e-post.

  NDES-certifikatanslutningsappen har även stöd för FIPS-läge (Federal Information Processing Standard). FIPS krävs inte, men du kan utfärda och återkalla certifikat när det är aktiverat.

- **PFX-certifikatanslutningsprogram för Microsoft Intune**: Om du planerar att använda S/MIME-kryptering för e-post använder du Azure-portalen för att ladda ned installationsprogrammet **PFX-certifikatanslutningsprogram för Microsoft Intune** ( **PfxCertificateConnectorBootstrapper.exe**). Anslutningsprogrammet hanterar begäranden för PFX-filer som importeras till Intune för S/MIME-kryptering av e-post för en specifik användare.

- **Windows Server**: Värd för:

  - Microsoft Intune-certifikatanslutningsapp (NDESConnectorSetup.exe) för scenarier med autentisering och S/MIME-signering av e-post
  - PFX-certifikatanslutningsapp för Microsoft Intune (PfxCertificateConnectorBootstrapper.exe) för scenarier med S/MIME-kryptering av e-post.

  Du kan köra båda anslutningsapparna (**Microsoft Intune-certifikatanslutningsapp** och **PFX-certifikatanslutningsapp för Microsoft Intune**) på samma server.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportera rotcertifikatet från Enterprise-CA:n

För att autentisera med VPN, Wi-Fi eller andra resurser behöver du ett rot-CA-certifikat eller ett mellanliggande CA-certifikat på varje enhet. Följande steg förklarar hur du hämtar nödvändiga certifikat från din Enterprise CA.

1. Logga in på din Enterprise CA med ett konto som har administratörsbehörighet.
2. Öppna en kommandotolk som administratör.
3. Exportera rot-CA-certifikatet (.cer) till en plats där du senare kan komma åt det.
4. När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

   `certutil -ca.cert certnew.cer`

   Mer information finns i [Certutil-åtgärder för att hantera certifikat](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

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

## <a name="download-install-and-configure-the-certificate-connectors"></a>Ladda ned, installera och konfigurera certifikatanslutningsapparna

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune certifikat Connector

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector **måste** installeras på en separat Windows-server. Den kan inte installeras på den utfärdande certifikatutfärdaren (CA).

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster**, filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Certifikatutfärdare** > **Lägg till**.
3. Hämta och spara anslutningsfilen. Spara den på en plats som är tillgänglig från servern där du ska installera anslutningsappen.

    ![ConnectorDownload][ConnectorDownload]

4. När nedladdningen är klar loggar du in på servern. Efter det:

    1. Se till att .NET 4.5 Framework eller senare är installerat, eftersom det krävs av NDES-certifikatanslutningsappen. .NET 4.5 framework ingår automatiskt i Windows Server 2012 R2 och senare versioner.
    2. Kör installationsprogrammet (NDESConnectorSetup.exe) och godkänn standardplatsen. Anslutningsprogrammet installeras då till `\Program Files\Microsoft Intune\NDESConnectorUI`. Bland installationsalternativen väljer du **PFX-distribution**. Fortsätt och slutför installationen.
    3. Som standard körs anslutningsapptjänsten under det lokala systemkontot. Om en proxy krävs för att få åtkomst till Internet kontrollerar du att det lokala tjänstkontot kan komma åt proxyinställningarna på servern.

5. NDES-anslutningen öppnar fliken **Registrering**. Om du vill aktivera anslutningen till Intune **Loggar du in** och anger ett konto med globala administratörsbehörigheter.
6. Vi rekommenderar att du på fliken **Avancerat** låter **Använd den här datorns systemkonto (standard)** vara markerat.
7. **Tillämpa** > **Stäng**
8. Gå tillbaka till Azure-portalen (**Intune** > **Enhetskonfiguration** > **Certifikatutfärdare**). Efter en stund visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.
9. Om du har en webbproxy i nätverksmiljön kan du behöva ytterligare konfigurationer för att anslutningsappen ska fungera. Mer information finns i [Arbeta med befintliga lokala proxyservrar](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers) i Azure Active Directory-dokumentationen.

> [!NOTE]
> Stöd för TSL 1.2 ingår i Microsoft Intune-certifikatanslutningsappen. Om servern med Microsoft Intune-certifikatanslutningsappen installerad stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>PFX-certifikatanslutningsapp för Microsoft Intune

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Certifikatutfärdare** > **Lägg till**
3. Ladda ned och spara PFX-certifikatanslutningsappen för Microsoft Intune. Spara den på en plats som är tillgänglig från servern där du ska installera anslutningsappen.
4. När nedladdningen är klar loggar du in på servern. Efter det:

    1. Se till att .NET 4.6 Framework eller senare är installerat, eftersom det krävs av PFX-certifikatanslutningsappen för Microsoft Intune. Om .NET 4.6 Framework inte är installerat kommer installationsprogrammet att installera det automatiskt.
    2. Kör installationsprogrammet (PfxCertificateConnectorBootstrapper.exe) och acceptera standardplatsen. Anslutningsprogrammet installeras då till `Program Files\Microsoft Intune\PFXCertificateConnector`.
    3. Anslutningsapptjänsten körs under det lokala systemkontot. Om en proxy krävs för Internetåtkomst kontrollerar du att det lokala tjänstkontot kan komma åt proxyinställningarna på servern.

5. PFX-certifikatanslutningsappen för Microsoft Intune öppnar fliken **Registrering** efter installationen. Om du vill aktivera anslutningen till Intune **loggar du in** och anger ett konto med behörigheter för global Azure-administratör eller Intune-administratör.
6. Stäng fönstret.
7. Gå tillbaka till Azure-portalen (**Intune** > **Enhetskonfiguration** > **Certifikatutfärdare**). Efter en stund visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.

## <a name="create-a-trusted-certificate-profile"></a>Skapa en betrodd certifikatprofil

1. I [Azure Portal](https://portal.azure.com) går du till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

   ![NavigateIntune][NavigateIntune]

2. Ange följande egenskaper:

    - **Namnet** på profilen
    - Om du vill kan du ange en beskrivning
    - **Plattform** att distribuera profilen till
    - Ange **profiltypen** som **betrott certifikat**

3. Gå till **Inställningar** och ange .cer-filen med rot CA-certifikatet som du exporterade tidigare.

   > [!NOTE]
   > Beroende på vilken plattform du valde i **steg 3** kan du få alternativet att välja **målarkiv** för certifikatet.

   ![ProfileSettings][ProfileSettings]

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. I [Azure Portal](https://portal.azure.com) går du till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
2. Ange följande egenskaper:

    - **Namnet** på profilen
    - Om du vill kan du ange en beskrivning
    - **Plattform** att distribuera profilen till
    - Ange **profiltypen** som **PKCS-certifikat**

3. Gå till **Inställningar** och ange följande egenskaper:

    - **Tröskelvärde för förnyelse (%)**: 20 % rekommenderas.
    - **Certifikatets giltighetsperiod**: Om du inte har ändrat certifikatmallen kan det här alternativet anges till ett år.
    - **Nyckellagringsprovider (KSP)**: För Windows väljer du var du vill lagra nycklarna på enheten.
    - **Certifikatutfärdare**: Visar det interna fullständiga domännamnet (FQDN) för din Enterprise-CA.
    - **Namn på certifikatutfärdare**: Anger namnet på din Enterprise-CA, till exempel ”Contoso Certification Authority”.
    - **Certifikatmallens namn**: Namnet på den mall som du skapade tidigare. Kom ihåg att **mallnamnet** som standard är samma som **mallens visningsnamn** *utan blanksteg*.
    - **Ämnesnamnets format**: Ange det här alternativet som **Eget namn** om inget annat krävs.
    - **Alternativt namn för certifikatmottagare**: Ange det här alternativet som **Användarens huvudnamn** om inget annat krävs.

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Skapa en PKCS-importerad certifikatprofil

Du kan importera certifikat som tidigare utfärdats till en viss användare från valfri CA till Intune. Importerade certifikat installeras på varje enhet som en användare registrerar. S/MIME-kryptering för e-post är det vanligaste scenariot för att importera befintliga PFX-certifikat till Intune. En användare kan ha många certifikat för att kryptera e-post. Privata nycklar för de certifikaten måste finnas på alla användarens enheter så att de kan dekryptera tidigare krypterad e-post.

Om du vill importera certifikat till Intune kan du använda [PowerShell-cmdletar som tillhandahålls på GitHub](https://github.com/Microsoft/Intune-Resource-Access).

När du har importerat certifikaten till Intune skapar du en profil för **PKCS-importerat certifikat** och tilldelar den till Azure Active Directory-grupper.

1. I [Azure Portal](https://portal.azure.com) går du till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
2. Ange följande egenskaper:

    - **Namnet** på profilen
    - Om du vill kan du ange en beskrivning
    - **Plattform** att distribuera profilen till
    - Ange **profiltypen** som **PKCS-importerat certifikat**

3. Gå till **Inställningar** och ange följande egenskaper:

    - **Avsett syfte**: Syftet med de certifikat som har importerats för den här profilen. En administratör kan ha importerat certifikat med olika syften (till exempel autentisering, S/MIME-signering eller S/MIME-kryptering). Avsett syfte som valts i certifikatprofilen matchar certifikatprofilen med rätt importerade certifikat.
    - **Certifikatets giltighetsperiod**: Om du inte har ändrat certifikatmallen kan det här alternativet anges till ett år.
    - **Nyckellagringsprovider (KSP)**: För Windows väljer du var du vill lagra nycklarna på enheten.

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

[Använda SCEP-certifikat](certificates-scep-configure.md) eller [utfärda PKCS-certifikat från en Symantec PKI Manager-webbtjänst](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navigera till Intune i Azure-portalen och skapa en ny profil för ett betrott certifikat"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Skapa en profil och ladda upp ett betrott certifikat"
[ConnectorDownload]: ./media/certificates-download-connector.png "Ladda ner certifikatanslutningsappen från Azure-portalen"  
