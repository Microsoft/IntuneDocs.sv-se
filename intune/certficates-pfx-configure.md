---
title: Använda PKCS-certifikat med Microsoft Intune – Azure | Micrososft Docs
description: Lägg till eller skapa ett Public Key Cryptography Standards-certifikat med Microsoft Intune, inklusive stegen för att exportera ett rotcertifikat, konfigurera certifikatmallen, ladda ned och installera Microsoft Intune Certificate Connector, skapa en profil för enhetskonfiguration, skapa en PKCS-certifikatprofil i Azure och din certifikatutfärdare
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61a190be2b4685030438988dab0d0134a8fa9f9b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Konfigurera och använda PKCS-certifikat med Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Certifikat används för att autentisera och skydda åtkomst till dina företagsresurser, som VPN eller WiFi-nätverk. Den här artikeln visar hur du exporterar ett PKCS-certifikat, och lägger sedan till certifikatet till en Intuneprofil. 

## <a name="requirements"></a>Krav

Om du vill använda PKCS-certifikat med Intune, måste du ha följande infrastruktur:

* En befintlig Active Directory Domain Services (AD DS)-domän konfigurerad.
 
  Mer information om att installera och konfigurera AD DS finns i [Design och planering för AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* En befintlig Enterprise-certifikatutfärdare (CA) har konfigurerats.

  Mer information om hur du installerar och konfigurerar Active Directory Certificate Services (AD CS) finns i artikeln [Active Directory Certificate Services stegvis guide](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > Intune kräver att du kör AD CS med en Enterprise-certifikatutfärdare (CA), inte en fristående CA.

* En klient som är ansluten till Enterprise-CA:n.
* En exporterad kopia av ditt rotcertifikat från din Enterprise-CA.
* Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) laddas ned från Intune-portalen.
* En Windows Server för att vara värd för Microsoft Intune Certificate Connector (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportera rotcertifikatet från Enterprise-CA:n

Du behöver en rot- eller mellanliggande CA på varje enhet för autentisering med VPN, WiFi och andra resurser. Följande steg förklarar hur du hämtar nödvändiga certifikat från din Enterprise CA.

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
   * Ställ in **certifikatutfärdare** till **Windows Server 2008 R2**
   * Ställ in **certifikatmottagare** till **Windows 7 / Server 2008 R2**
5. På fliken **Allmänt**:
   * Ange **mallens visningsnamn** till något som betyder något för dig.

   > [!WARNING]
   > **Mallnamnet** är som standard samma som **mallens visningsnamn** med *inga blanksteg*. Anteckna mallens namn. Du behöver det senare.

6. I **Hantering av begäranden** väljer du **Tillåt att den privata nyckeln exporteras**.
7. I **kryptografi** bekräftar du att den **minsta nyckelstorleken** är inställd på 2048.
8. I **Ämnesnamn** väljer du **Anges i begäran**.
9. I **Tillägg**, bekräftar du att du ser krypterar filsystem, säker e-post och klientautentisering under **användningsprinciper**.
    
      > [!IMPORTANT]
      > För iOS-certifikatmallar: uppdatera **Nyckelanvändning** på fliken **Tillägg** och kontrollera att **Signaturen är bevis för ursprung** inte har markerats.

10. I **säkerhet** lägger du till datorkontot för den server där du installerar Microsoft Intune Certificate Connector.
    * Ge det här kontot **läs-** och **registrera**-behörigheter.
11. Välj **Tillämpa** och sedan **OK** för att spara certifikatmallen.
12. Stäng **konsolen för certfikatmallar**.
13. I konsolen **certifikatutfärdare**, högerklickar du på **certifikatmallar**, **Ny**, **certifikatmall att utfärda**.
    * Välj den mall som du skapade i föregående steg och välj **OK**.
14. Följ dessa steg för att servern ska hantera certifikat åt Intune-registrerade enheter och användare:

    a. Högerklicka på certifikatutfärdaren och välj **egenskaper**.

    b. På fliken säkerhet, lägger du till datorkontot för den server där du kör Microsoft Intune Certificate Connector.
      * Bevilja behörigheterna **utfärda och hantera certifikat** och **begära certifikat** till datorkontot.
15. Logga ut från Enterprise-CA:n.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Hämta, installera och konfigurera Microsoft Intune Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** och filtrerar på **Intune**. Välj **Microsoft Intune** och sedan **Enhetskonfiguration**. 
2. Välj **Certifikatutfärdare**, välj **Lägg till** och sedan alternativet för att **ladda ned anslutningsfilen**. Spara den på en plats där du kan komma åt den från den server där den kommer att installeras. 
3. Logga in på den här servern och kör installationsprogrammet: 

    1. Acceptera standardplatsen. Anslutningsprogrammet installeras då till `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`.
    2. Bland installationsalternativen väljer du **PFX-distributionsalternativet**och väljer **Nästa**.
    3. **Installera** och vänta tills det är klart.
    4. När det är klart markerar du **Starta Intune Connector** och sedan **Slutför**.

4. Fönstret NDES Connector borde öppnas till fliken **Registrering**. Om du vill aktivera anslutningen till Intune väljer du **Logga in** och anger ett konto med globala administratörsbehörigheter.
5. På fliken **avancerat** låter du **Använd den här datorns systemkonto (standard)** vara markerad.
6. **Tillämpa** och sedan **Stäng**.
7. Gå tillbaka till Azure-portalen (**Intune** > **Enhetskonfiguration** > **Certifikatutfärdare**). Efter några minuter visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.

## <a name="create-a-device-configuration-profile"></a>Skapa en enhetskonfigurationsprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune**, **Enhetskonfiguration**, **Profiler** och välj **Skapa profil**.

   ![NavigateIntune][NavigateIntune]

3. Ange följande egenskaper:
   * **Namnet** på profilen
   * Om du vill kan du ange en beskrivning
   * **Plattform** att distribuera profilen till
   * Ange **profiltypen** som **betrott certifikat**

4. Gå till **Inställningar** och ange .cer-filen med rot CA-certifikatet som du exporterade tidigare.

   > [!NOTE]
   > Beroende på vilken plattform du valde i **steg 3** kan du få alternativet att välja **målarkiv** för certifikatet.

   ![ProfileSettings][ProfileSettings]

5. Välj **OK** och sedan **Skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter, finns [så här tilldelar du Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune**, **Enhetskonfiguration**, **Profiler** och välj **Skapa profil**.
3. Ange följande egenskaper:
   * **Namnet** på profilen
   * Om du vill kan du ange en beskrivning
   * **Plattform** att distribuera profilen till
   * Ange **profiltypen** som **PKCS-certifikat**
4. Gå till **Inställningar** och ange följande egenskaper:
   * **Tröskelvärde för förnyelse (%)** – 20% rekommenderas.
   * **Certifikatets giltighetstid** – om du inte har ändrat certifikatmallen ska det här alternativet anges till ett år.
   * **Certifikatutfärdare** – Visar det interna fullständigt kvalificerade domännamnet (FQDN) för din Enterprise CA.
   * **Namn på certifikatutfärdare** – Anger namnet på din Enterprise CA och kan skilja sig från föregående objekt.
   * **Certifikatmallens namn** – Namnet på den mall du skapade tidigare. Kom ihåg att **mallnamnet** som standard är samma som **mallens visningsnamn** *utan blanksteg*.
   * **Ämnesnamnets format** – ange det här alternativet som **nätverksnamn** om inget annat krävs.
   * **Alternativt ämnesnamn** – ange det här alternativet som **användarens huvudnamn (UPN)** om inget annat krävs.
   * **Utökad nyckelanvändning** – Så länge du använde standardinställningarna i steg 10 i avsnittet [Konfigurera certifikatmallar på certifikatutfärdaren](#configure-certificate-templates-on-the-certification-authority) (i den här artikeln) lägger du till följande **fördefinierade värden** från markeringen:
      * **Valfritt ändamål**
      * **Klientautentisering**
      * **Säker e-post**
   * **Rotcertifikat** – (för Android-profiler) Listar .cer-filen som exporterades i steg 3 i avsnittet [Exportera rotcertifikatet från Enterprise CA:n](#export-the-root-certificate-from-the-enterprise-ca) (i den här artikeln).

5. Klicka på **OK** och sedan **Skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter, finns [så här tilldelar du Microsoft Intune-enhetsprofiler](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navigera till Intune i Azure-portalen och skapa en ny profil för ett betrott certifikat"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Skapa en profil och ladda upp ett betrott certifikat"
[ConnectorDownload]: ./media/certificates-download-connector.png "Ladda ner certifikatanslutningsappen från Azure-portalen"  
