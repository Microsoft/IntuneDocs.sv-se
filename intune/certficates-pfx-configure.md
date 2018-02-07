---
title: Konfigurera och hantera PKCS-certifikat med Intune
titleSuffix: Intune on Azure
description: Skapa och tilldela PKCS-certifikat med Intune.
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d877a1de8e66372d36641dd863a517fecf176d69
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Konfigurera och hantera PKCS-certifikat med Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>Krav

Om du vill använda PKCS-certifikat med Intune, måste du ha följande infrastruktur:

* En befintlig Active Directory Domain Services (AD DS)-domän konfigurerad.
 
  Mer information om hur du installerar och konfigurerar AD DS finns i artikeln [AD DS-design och planering](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

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
3. Exportera rot-CA-certifikatet till en plats där du senare kan komma åt det.

   Exempel:

4.  När guiden slutförts klickar du på **Starta användargränssnittet för Certifikat Connectorn**innan du stänger guiden.

   `certutil -ca.cert certnew.cer`

   Mer information finns i [Certutil-åtgärder för att hantera certifikat](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Konfigurera certifikatmallar på certifikatutfärdaren

1. Logga in på din Enterprise CA med ett konto som har administratörsbehörighet.
2. Öppna konsolen **certifikatutfärdare**.
3. Högerklicka på **certifikatmallar** och välj **hantera**.
4. Leta upp certifikatmallen **användare**, högerklicka på den och välj **duplicera mallen**. Ett fönster öppnas, **egenskaper för ny mall**.
5. På fliken **kompatibilitet**
   * Ställ in **certifikatutfärdare** till **Windows Server 2008 R2**
   * Ställ in **certifikatmottagare** till **Windows 7 / Server 2008 R2**
6. På fliken **Allmänt**:
   * Ange **mallens visningsnamn** till något som betyder något för dig.

   > [!WARNING]
   > **Mallnamnet** är som standard samma som **mallens visningsnamn** med *inga blanksteg*. Anteckna mallnamnet för senare användning.

7. På fliken **begärandehantering** markerar du rutan **tillåt att den privata nyckeln exporteras**.
8. På fliken **kryptografi**, bekräftar du att den **minsta nyckelstorleken** är inställd på 2 048.
9. På fliken **ämnesnamn**, väljer du alternativknappen **anges i begäran**.
10. På fliken **tillägg**, bekräftar du att du ser krypterar filsystem, säker e-post och klientautentisering under **användningsprinciper**.
    
      > [!IMPORTANT]
      > För iOS- och macOS-certifikatmallar: Redigera **Nyckelanvändning** på fliken **Tillägg** och kontrollera att **Signaturen är bevis för ursprung** inte har markerats.

11. På fliken **säkerhet**, lägger du till datorkontot för den server där du installerar Microsoft Intune Certificate Connector.
    * Ge det här kontot **läs-** och **registrera**-behörigheter.
12. Klicka på **tillämpa** och klicka sedan på **OK** för att spara certifikatmallen.
13. Stäng **konsolen för certfikatmallar**.
14. I konsolen **certifikatutfärdare**, högerklickar du på **certifikatmallar**, **Ny**, **certifikatmall att utfärda**.
    * Välj den mall som du skapade i föregående steg och klicka på **OK**.
15. Följ dessa steg för att servern ska hantera certifikat åt Intune-registrerade enheter och användare:

    a. Högerklicka på certifikatutfärdaren och välj **egenskaper**.

    b. På fliken säkerhet, lägger du till datorkontot för den server där du kör Microsoft Intune Certificate Connector.
      * Bevilja behörigheterna **utfärda och hantera certifikat** och **begära certifikat** till datorkontot.
16. Logga ut från Enterprise-CA:n.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Hämta, installera och konfigurera Microsoft Intune Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. I Azure Portal väljer du **Fler tjänster** > **Övervakning och hantering**  > **Intune**.
2. Välj **Enhetskonfiguration** på **Intune**-bladet. 
3. Välj **Certifikatutfärdare** på bladet **Enhetskonfiguration**. 
4. Klicka på **Lägg till** och välj **Download Connector file** (Ladda ned anslutningsfil). Spara den på en plats där du kan komma åt den från den server där du kommer att installera den. 
5.  Logga in på servern där du ska installera Microsoft Intune Certificate Connector.
6.  Kör installationsprogrammet och acceptera standardplatsen. Den installerar anslutningsappen till C:\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.
    1. På sida med installationsalternativ väljer du **PFX-distribution** och klickar på **nästa**.
    2. Klicka på **installera** och vänta tills det är klart.
    3. På sidan för slutförande, markerar du kryssrutan **Starta Intune Connector** och klickar på **Slutför**.
7.  Fönstret NDES Connector borde nu öppnas till fliken **registrering**. Om du vill aktivera anslutningen till Intune klickar du på **Logga in** och anger ett konto med administratörsbehörighet.
8.  På fliken **avancerat**, kan du lämna alternativknappen **använd den här datorns systemkonto (standard)** markerad.
9.  Klicka på **tillämpa** och sedan **stäng**.
10. Gå tillbaks till Azure-portalen. Efter ett par minuter visas en grön bock och ordet **Aktiv** under **Anslutningsstatus** i **Intune** > **Enhetskonfiguration** > **Certifikatutfärdare**. Det innebär att du vet att din anslutningsserver kan kommunicera med Intune.


## <a name="create-a-device-configuration-profile"></a>Skapa en enhetskonfigurationsprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune**, **enhetskonfiguration**, **profiler** och klicka på **skapa profil**.

   ![NavigateIntune][NavigateIntune]

3. Ange följande information:
   * **Namnet** på profilen
   * Om du vill kan du ange en beskrivning
   * **Plattform** att distribuera profilen till
   * Ange **profiltypen** som **betrott certifikat**
4. Gå till **inställningar** och ange .cer-filen med rot CA-certifikatet som du exporterade tidigare.

   > [!NOTE]
   > Beroende på vilken plattform du valde i **steg 3** kan du få alternativet att välja **målarkiv** för certifikatet.

   ![ProfileSettings][ProfileSettings]

5. Klicka på **OK** och sedan **skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter, finns [så här tilldelar du Microsoft Intune-enhetsprofiler](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Skapa en PKCS-certifikatprofil

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Gå till **Intune**, **enhetskonfiguration**, **profiler** och klicka på **skapa profil**.
3. Ange följande information:
   * **Namnet** på profilen
   * Om du vill kan du ange en beskrivning
   * **Plattform** att distribuera profilen till
   * Ange **profiltypen** som **PKCS-certifikat**
4. Gå till **inställningar** och ange följande information:
   * **Tröskelvärde för förnyelse (%)** – 20% rekommenderas.
   * **Certifikatets giltighetstid** – om du inte har ändrat certifikatmallen ska det här alternativet anges till ett år.
   * **Certifikatutfärdare** – det här alternativet är det interna fullständigt kvalificerade domännamnet (FQDN) för din Enterprise CA.
   * **Namn på certifikatutfärdare** – det här alternativet är namnet på din Enterprise CA och kan skilja sig från föregående objekt.
   * **Certifikatmallens namn** – det här alternativet är namnet på den mall du skapade tidigare. Kom ihåg att **mallnamnet** som standard är samma som **mallens visningsnamn** *utan blanksteg*.
   * **Ämnesnamnets format** – ange det här alternativet som **nätverksnamn** om inget annat krävs.
   * **Alternativt ämnesnamn** – ange det här alternativet som **användarens huvudnamn (UPN)** om inget annat krävs.
   * **Utökad nyckelanvändning** – så länge du använde standardinställningarna i steg 10 i föregående avsnitt **konfigurera certifikatmallar på certifikatutfärdaren**, lägger du till följande **fördefinierade värden** från markeringsrutan:
      * **Valfritt ändamål**
      * **Klientautentisering**
      * **Säker e-post**
   * **Rotcertifikat** – (för Android-profiler) det här alternativet är .cer-filen som exporterades i steg 3 i föregående avsnitt [exportera rotcertifikatet från Enterprise CA:n](#export-the-root-certificate-from-the-enterprise-ca).

5. Klicka på **OK** och klicka sedan på **skapa** för att spara din profil.
6. Om du vill tilldela den nya profilen till en eller flera enheter, finns [så här tilldelar du Microsoft Intune-enhetsprofiler](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navigera till Intune i Azure-portalen och skapa en ny profil för ett betrott certifikat"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Skapa en profil och ladda upp ett betrott certifikat"
[ConnectorDownload]: ./media/certificates-download-connector.png "Ladda ner certifikatanslutningsappen från Azure-portalen"  
