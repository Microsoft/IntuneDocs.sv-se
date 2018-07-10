---
title: Använda PKCS-certifikat med Microsoft Intune – Azure | Micrososft Docs
description: Lägg till eller skapa ett Public Key Cryptography Standards-certifikat med Microsoft Intune, inklusive stegen för att exportera ett rotcertifikat, konfigurera certifikatmallen, ladda ned och installera Microsoft Intune Certificate Connector (NDES), skapa en profil för enhetskonfiguration, skapa en PKCS-certifikatprofil i Azure och din certifikatutfärdare.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271549"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurera och använda PKCS-certifikat med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Certifikat används för att autentisera och skydda åtkomst till dina företagsresurser, som VPN eller WiFi-nätverk. Den här artikeln visar hur du exporterar ett PKCS-certifikat, och lägger sedan till certifikatet till en Intuneprofil. 

## <a name="requirements"></a>Krav

Om du vill använda PKCS-certifikat med Intune, måste du ha följande infrastruktur:

- **Active Directory-domän**: Alla servrar i det här avsnittet måste vara anslutna till Active Directory-domänen.

  Mer information om att installera och konfigurera AD DS finns i [Design och planering för AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Certifikatutfärdare** (CA): En företagscertifikatutfärdare (CA)

  Mer information om hur du installerar och konfigurerar Active Directory Certificate Services (AD CS) finns i artikeln [Active Directory Certificate Services stegvis guide](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune kräver att du kör AD CS med en Enterprise-certifikatutfärdare (CA), inte en fristående CA.

- **En klient**: För att ansluta till företags-CA

- **Rotcertifikat**: En exporterad kopia av ditt rotcertifikat från din Enterprise-CA

- **Microsoft Intune Certificate Connector**: Använd Azure-portalen för att hämta installationsprogrammet för **certifikatanslutningsappen** (**NDESConnectorSetup.exe**). 

  NDES-certifikatanslutningsappen har även stöd för FIPS-läge (Federal Information Processing Standard). FIPS krävs inte, men du kan utfärda och återkalla certifikat när det är aktiverat.

- **Windows Server**: Är värd för Microsoft Intune Certificate Connector (NDESConnectorSetup.exe)

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportera rotcertifikatet från Enterprise-CA:n

För att autentisera med VPN, WiFi och andra resurser behöver du ett rot-CA-certifikat eller ett mellanliggande CA-certifikat på varje enhet. Följande steg förklarar hur du hämtar nödvändiga certifikat från din Enterprise CA.

1. Logga in på din Enterprise CA med ett konto som har administratörsbehörighet.
2. Öppna en kommandotolk som administratör.
3. Exportera rot-CA-certifikatet (.cer) till en plats där du senare kan komma åt det.

   Exempel:

4. När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

   `certutil -ca.cert certnew.cer`

   Mer information finns i [Certutil-åtgärder för att hantera certifikat](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Konfigurera certifikatmallar på certifikatutfärdaren

1. Logga in på din Enterprise CA med ett konto som har administratörsbehörighet.
2. Öppna konsolen **Certifikatutfärdare**, högerklicka på **Certifikatmallar** och välj **Hantera**.
3. Leta upp certifikatmallen **användare**, högerklicka på den och välj **duplicera mallen**. **Egenskaper för ny mall** öppnas.
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
11. Välj **Tillämpa** och sedan **OK** för att spara certifikatmallen.
12. Stäng **konsolen för certfikatmallar**.
13. I konsolen **certifikatutfärdare**, högerklickar du på **certifikatmallar**, **Ny**, **certifikatmall att utfärda**. Välj den mall som du skapade i föregående steg och välj **OK**.
14. Följ dessa steg för att servern ska hantera certifikat åt Intune-registrerade enheter och användare:

    1. Högerklicka på certifikatutfärdaren och välj **egenskaper**.
    2. På fliken säkerhet, lägger du till datorkontot för den server där du kör Microsoft Intune Certificate Connector. Bevilja behörigheterna **utfärda och hantera certifikat** och **begära certifikat** till datorkontot.

15. Logga ut från Enterprise-CA:n.

## <a name="download-install-and-configure-the-certificate-connector"></a>Ladda ned, installera och konfigurera certifikatanslutningsappen

![ConnectorDownload][ConnectorDownload]

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** och sedan **Certifikatutfärdare**.
4. Välj **Lägg till** och **Download the connector file** (Ladda ned fil för anslutningsappen). Spara den på en plats där du kan komma åt den från den server där du kommer att installera den.
5. När nedladdningen är klar loggar du in på servern. Efter det:

    1. Se till att .NET 4.5 Framework är installerat, eftersom det krävs av NDES-certifikatanslutningsappen. .NET 4.5 framework ingår automatiskt i Windows Server 2012 R2 och senare versioner.
    2. Kör installationsprogrammet (NDESConnectorSetup.exe) och godkänn standardplatsen. Anslutningsprogrammet installeras då till `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`. Bland installationsalternativen väljer du **PFX-distribution**. Fortsätt och slutför installationen.

6. NDES-anslutningen öppnar fliken **Registrering**. Om du vill aktivera anslutningen till Intune **Loggar du in** och anger ett konto med globala administratörsbehörigheter.
7. På fliken **avancerat** låter du **Använd den här datorns systemkonto (standard)** vara markerad.
8. **Tillämpa** och sedan **Stäng**.
9. Gå tillbaka till Azure-portalen (**Intune** > **Enhetskonfiguration** > **Certifikatutfärdare**). Efter en stund visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.

> [!NOTE]
> Stöd för TSL 1.2 ingår i NDES-certifikatanslutningsappen. Om servern med NDES-certifikatanslutningsappen installerat stödjer TLS 1.2 används därmed TLS 1.2. Om servern inte stödjer TLS 1.2 används TLS 1.1. För närvarande används TLS 1.1 för autentisering mellan enheter och servern.

## <a name="create-a-device-configuration-profile"></a>Skapa en enhetskonfigurationsprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.

   ![NavigateIntune][NavigateIntune]

3. Ange följande egenskaper:

  - **Namnet** på profilen
  - Om du vill kan du ange en beskrivning
  - **Plattform** att distribuera profilen till
  - Ange **profiltypen** som **betrott certifikat**

4. Gå till **Inställningar** och ange .cer-filen med rot CA-certifikatet som du exporterade tidigare.

   > [!NOTE]
   > Beroende på vilken plattform du valde i **steg 3** kan du få alternativet att välja **målarkiv** för certifikatet.

   ![ProfileSettings][ProfileSettings]

5. Välj **OK** och sedan **Skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune** > **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

  - **Namnet** på profilen
  - Om du vill kan du ange en beskrivning
  - **Plattform** att distribuera profilen till
  - Ange **profiltypen** som **PKCS-certifikat**

4. Gå till **Inställningar** och ange följande egenskaper:

  - **Tröskelvärde för förnyelse (%)** – 20% rekommenderas.
  - **Certifikatets giltighetstid** – om du inte har ändrat certifikatmallen ska det här alternativet anges till ett år.
  - **Certifikatutfärdare** – Visar det interna fullständigt kvalificerade domännamnet (FQDN) för din Enterprise CA.
  - **Namn på certifikatutfärdare** – Anger namnet på din Enterprise CA och kan skilja sig från föregående objekt.
  - **Certifikatmallens namn** – Namnet på den mall du skapade tidigare. Kom ihåg att **mallnamnet** som standard är samma som **mallens visningsnamn** *utan blanksteg*.
  - **Ämnesnamnets format** – ange det här alternativet som **nätverksnamn** om inget annat krävs.
  - **Alternativt ämnesnamn** – ange det här alternativet som **användarens huvudnamn (UPN)** om inget annat krävs.
  - **Utökad nyckelanvändning** – Så länge du använde standardinställningarna i steg 10 i avsnittet [Konfigurera certifikatmallar på certifikatutfärdaren](#configure-certificate-templates-on-the-certification-authority) (i den här artikeln) lägger du till följande **fördefinierade värden** från markeringen:
    - **Valfritt ändamål**
    - **Klientautentisering**
    - **Säker e-post**
  - **Rotcertifikat** – (för Android-profiler) Listar .cer-filen som exporterades i steg 3 i avsnittet [Exportera rotcertifikatet från Enterprise CA:n](#export-the-root-certificate-from-the-enterprise-ca) (i den här artikeln).

5. Klicka på **OK** och sedan **Skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="next-steps"></a>Nästa steg
[Använda SCEP-certifikat](certificates-scep-configure.md) eller [utfärda PKCS-certifikat från en Symantec PKI-hanterad webbtjänst](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navigera till Intune i Azure-portalen och skapa en ny profil för ett betrott certifikat"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Skapa en profil och ladda upp ett betrott certifikat"
[ConnectorDownload]: ./media/certificates-download-connector.png "Ladda ner certifikatanslutningsappen från Azure-portalen"  
