---
title: Använda importerade PFX-certifikat i Microsoft Intune – Azure | Microsoft Docs
description: Använd importerade PKCS-certifikat (Public Key Cryptography Standards) med Microsoft Intune, inklusive import av certifikat, konfiguration at certifikatmallen, installation av Intune-anslutningsappen för importerade PFX-certifikat, och skapa en profil för importerade PKCS-certifikat.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: fead8b9d69f5356876c0b3a2a4ce02e9b754128e
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999339"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>Konfigurera och använda importerade PKCS-certifikat med Intune

Microsoft Intune stöder användningen av importerade PKCS-certifikat (certifikat med offentlig nyckel-par), som vanligtvis används för S/MIME-kryptering med e-postprofiler. Vissa e-postprofiler i Intune stöder ett alternativ för att aktivera S/MIME där du kan definiera ett S/MIME-signeringscertifikat och S/MIME-krypteringscertifikat.

S/MIME-kryptering är utmanande eftersom e-post krypteras med ett specifikt certifikat. Du måste ha den privata nyckeln för certifikatet som krypterade e-postmeddelandet på enheten där du läser e-postmeddelandet så att den kan dekrypteras. Krypteringscertifikat förnyas regelbundet, vilket betyder att du kanske behöver din krypteringshistorik på alla dina enheter för att se till att du kan läsa äldre e-post.  Eftersom samma certifikat måste användas på olika enheter kan du inte använda [SCEP](certificates-scep-configure.md)- eller [PKCS](certficates-pfx-configure.md)-certifikatprofiler för detta ändamål eftersom dessa certifikatleveransmekanismer levererar unika certifikat per enhet. 

Mer information om användning av S/MIME med Intune finns i [Använda S/MIME för att kryptera e-post](certificates-s-mime-encryption-sign.md).

## <a name="requirements"></a>Krav

Om du vill använda importerade PKCS-certifikat med Intune behöver du följande infrastruktur:

- **PFX-certifikatanslutningsprogram för Microsoft Intune**:  
  Varje Intune-klient har stöd för en enda instans av den här anslutningen. Du kan installera den här anslutningen på samma server som en instans av Microsoft Intune Certificate Connector.

  Anslutningsappen hanterar begäranden för PFX-filer som importeras till Intune för S/MIME-kryptering av e-post för en specifik användare.  

  Den här anslutningsappen kan uppdatera sig automatiskt när nya versioner blir tillgängliga. Om du vill använda uppdateringsfunktionen måste du se till att brandväggarna är öppna så att anslutningsappen tillåts kontakta **autoupdate.msappproxy.net** på port **443**.  

  Mer information om alla nätverksslutpunkter som anslutningsappen har åtkomst till finns i [Krav för Intune-nätverkskonfiguration och bandbredd](../fundamentals/network-bandwidth-use.md).


- **Windows Server**:  
  Du använder Windows Server som värd för PFX-certifikatanslutningsappen för Microsoft Intune.  Anslutningsappen används för att bearbeta begäranden för certifikat som importerats till Intune.

  Intune stöder installation av *Microsoft Intune Certificate Connector* på samma server som *PFX-certifikatanslutningsappen för Microsoft Intune*.

  För att stödja anslutningsappen måste servern köra .NET 4.6 Framework eller senare. Om .NET 4.6 Framework inte är installerad när du startar installationen av installeras det av anslutningsappens installation automatiskt.

- **Visual Studio 2015 eller senare** (valfritt): Du använder Visual Studio för att bygga PowerShell-hjälpmodulen med cmdletar för import av PFX-certifikat till Microsoft Intune. Information om hur du hämtar PowerShell-hjälp-cmdletar finns i [PFXImport PowerShell Project på GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="how-it-works"></a>Så här fungerar det

När du använder Intune för att distribuera ett **importerat PFX-certifikat** till en användare finns det två komponenter i spel utöver enheten: 

- **Intune-tjänsten**: Lagrar PFX-certifikaten i ett krypterat tillstånd och hanterar distributionen av certifikatet till användarenheten.  Lösenorden som skyddar de privata nycklarna för certifikaten krypteras innan de laddas upp med hjälp av antingen en modul för maskinvarusäkerhet (HSM) eller Windows-kryptografi, vilket säkerställer att Intune inte kan komma åt den privata nyckeln när som helst.
- **PFX-certifikatanslutningsprogram för Microsoft Intune**: När en enhet begär ett PFX-certifikat som har importerats till Intune skickas det krypterade lösenordet, certifikatet och enhetens offentliga nyckel till anslutningsappen.  Anslutningsappen dekrypterar lösenordet med hjälp av den lokala privata nyckeln och krypterar sedan lösenordet på nytt (och eventuella plist-profiler om du använder iOS) med enhetsnyckeln innan certifikatet skickas tillbaka till Intune.  Intune levererar sedan certifikatet till enheten och enheten kan dekryptera det med enhetens privata nyckel och installera certifikatet.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Ladda ned, installera och konfigurera PFX-certifikatanslutningsappen för Microsoft Intune

1. I [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)-portalen väljer du **Enhetskonfiguration** > **Certifikatanslutningsappar** > **Lägg till**

   ![Ladda ned PFX-certifikatanslutningsappen för Microsoft Intune](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

2. Följ anvisningarna för att ladda ned *PFX-certifikatanslutningsappen för Microsoft Intune* till en plats som är åtkomlig från servern där du kommer att installera anslutningsappen.
3. När nedladdningen har slutförts loggar du in på servern och kör installationsprogrammet (PfxCertificateConnectorBootstrapper.exe).  
   - När du accepterar standardinstallationsplatsen installeras anslutningsappen i `Program Files\Microsoft Intune\PFXCertificateConnector`.
   - Anslutningsapptjänsten körs under det lokala systemkontot. Om en proxy krävs för Internetåtkomst kontrollerar du att det lokala tjänstkontot kan komma åt proxyinställningarna på servern.

4. PFX-certifikatanslutningsappen för Microsoft Intune öppnar fliken **Registrering** efter installationen. Om du vill aktivera anslutningen till Intune **loggar du in** och anger ett konto med behörigheter för global Azure-administratör eller Intune-administratör.

   > [!WARNING]
   > Som standard är **Förbättrad säkerhetskonfiguration i IE** i Windows Server inställt på **På** som kan orsaka problem med inloggningen till Office 365.

5. Stäng fönstret.
6. I Intune-portalen går du tillbaka till **Enhetskonfiguration** > **Certifikatanslutningsappar**. Efter en stund visas en grön bockmarkering och **Anslutningsstatus** är **Aktiv**. Anslutningsservern kan nu kommunicera med Intune.

## <a name="import-pfx-certificates-to-intune"></a>Importera PFX-certifikat till Intune

Du använder [Microsoft Graph](https://docs.microsoft.com/graph) för att importera dina användares PFX-certifikat till Intune. Hjälpkomponenten [PFXImport PowerShell Project på GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell) ger dig cmdletar för att utföra åtgärderna enkelt.

Om du föredrar att använda en egen anpassad lösning med hjälp av Graph använder du [resurstypen userPFXCertificate](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta).

### <a name="build-pfximport-powershell-project-cmdlets"></a>Bygg PFXImport PowerShell Project-cmdletar

Om du vill använda PowerShell-cmdletarna bygger du projektet själv med hjälp av Visual Studio. Processen är enkel och kan köras på servern, men vi rekommenderar att du kör den på din arbetsstation.  

1. Gå till roten på lagringsplatsen [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) på GitHub och ladda sedan ned eller klona lagringsplatsen med Git på din dator.

   ![GitHub-nedladdningsknappen](./media/certificates-imported-pfx-configure/github-download.png)

2. Gå till `.\Intune-Resource-Access-develop\src\PFXImportPowershell\` och öppna projektet med Visual Studio med hjälp av filen **PFXImportPS.sln**.
3. Ändra **Debug** till **Release**.
4. Gå till **Build** och välj **Build PFXImportPS**. Efter en stund visas bekräftelsen **Build succeeded** längst ned till vänster i Visual Studio.

   ![Build-alternativet i Visual Studio](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. Byggprocessen skapar en ny mapp med PowerShell-modulen i `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`.

   Du använder den här **Release**-mappen för nästa steg.

### <a name="create-the-encryption-public-key"></a>Skapa den offentliga nyckeln för kryptering

Du importerar PFX-certifikat och deras privata nycklar till Intune. Lösenordet som skyddar den privata nyckeln krypteras med en offentlig nyckel som lagras lokalt. Du kan använda Windows-kryptografi, en modul för maskinvarusäkerhet eller en annan typ av kryptografi för att generera och lagra offentlig/privat nyckel-paren.  Beroende på vilken typ av kryptografi som används kan offentlig/privat nyckel-paret exporteras i ett filformat för säkerhetskopiering.

PowerShell-modulen tillhandahåller metoder för att skapa en nyckel med Windows-kryptografi. Du kan också använda andra verktyg för att skapa en nyckel.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Så här skapar du krypteringsnyckeln med Windows-kryptografi

1. Kopiera *Release*-mappen som har skapats av Visual Studio till servern där du har installerat **PFX-certifikatanslutningsappen för Microsoft Intune**. Den här mappen innehåller PowerShell-modulen.  
2. Öppna *PowerShell* på servern som administratör och gå sedan till *Release*-mappen som innehåller PowerShell-modulen.
3. Kör `Import-Module .\IntunePfxImport.psd1` för att importera modulen.
4. Kör sedan `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`

   > [!TIP]  
   > Providern du använder måste väljas igen när du importerar PFX-certifikat. Du kan använda  **Microsoft-programvaruprovidern för nyckellagring** men den stöds för att använda en annan provider. Nyckelnamnet anges också som ett exempel och du kan välja ett annat nyckelnamn.  

   Om du planerar att importera certifikatet kan du exportera den här nyckeln till en fil med följande kommando: `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   Den privata nyckeln måste importeras på servern som är värd för PFX-certifikatanslutningsappen för Microsoft Intune så att importerade PFX-certifikat kan bearbetas korrekt.  

#### <a name="to-use-a-hardware-security-module-hsm"></a>Använda en modul för maskinvarusäkerhet (HSM)  

Du kan använda en modul för maskinvarusäkerhet (HSM) för att generera och lagra offentlig/privat nyckel-paret. Mer information finns i HSM-providerns dokumentation.

### <a name="import-pfx-certificates"></a>Importera PFX-certifikat 

I följande process används PowerShell-cmdletarna som ett exempel på hur du importerar PFX-certifikaten. Du kan välja olika alternativ beroende på dina krav.

Alternativen är:  
- Avsett syfte (grupperar certifikat baserat på en tagg):  
  - unassigned
  - smimeEncryption
  - smimeSigning


- Utfyllnadsschema:  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

Välj den nyckellagrinsprovider som matchar providern du använde för att skapa nyckeln.

#### <a name="to-import-the-pfx-certificate"></a>Så här importerar du PFX-certifikatet  

1. Exportera certifikaten från en certifikatutfärdare (CA) genom att följa dokumentationen från providern.  För Microsoft Active Directory-certifikattjänster kan du använda [det här exempelskriptet](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b).   
2. Öppna *PowerShell* på servern som administratör och gå sedan till *Release*-mappen som innehåller PowerShell-modulen.
3. Kör `Import-Module .\IntunePfxImport.psd1` för att importera modulen  
4. Kör `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"` för autentisera till Intune Graph

   > [!NOTE]
   > Då autentiseringen körs mot Graph måste du ange behörigheter för AppID. Om det är först gången du använder det här verktyget krävs en *global administratör*. PowerShell-cmdletarna använder samma AppID som den som används med [PowerShell Intune-exempel](https://github.com/microsoftgraph/powershell-intune-samples).   
5. Konvertera lösenordet för varje PFX-filen du importerar till en säker sträng genom att köra `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`.  
6. Om du vill skapa ett **UserPFXCertificate**-objekt kör du `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`

   Exempelvis: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`

   > [!NOTE]  
   > När du importerar certifikatet från ett annat system än servern där anslutningsappen är installerad måste du använda följande kommando som innehåller nyckelfilsökvägen: `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. Importera **UserPFXCertificate**-objektet till Intune genom att köra `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`

8. Validera certifikatet som har importerats genom att köra `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`

Mer information om andra tillgängliga kommandon finns i readme-filen i [PFXImport PowerShell Project på GitHub](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).

## <a name="create-a-pkcs-imported-certificate-profile"></a>Skapa en PKCS-importerad certifikatprofil

När du har importerat certifikaten till Intune skapar du en profil för **PKCS-importerat certifikat** och tilldelar den till Azure Active Directory-grupper.

1. I [Intune-portalen](https://go.microsoft.com/fwlink/?linkid=2090973) går du till **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
2. Ange följande egenskaper:

   - **Namnet** på profilen
   - Om du vill kan du ange en beskrivning
   - **Plattform** att distribuera profilen till
   - Ange **profiltypen** som **PKCS-importerat certifikat**

3. Gå till **Inställningar** och ange följande egenskaper:

   - **Avsett syfte**: Ange syftet med de certifikat som har importerats för den här profilen. Administratörer kan importera certifikat med olika syften (till exempel S/MIME-signering eller S/MIME-kryptering). Avsett syfte som valts i certifikatprofilen matchar certifikatprofilen med rätt importerade certifikat. Avsett syfte är en tagg för att gruppera importerade certifikat och garanterar inte att certifikat som importerats med den taggen uppfyller det avsedda syftet.  
   - **Certifikatets giltighetsperiod**: Om giltighetsperioden inte har ändrats i certifikatmallen är standardinställningen för det här alternativet ett år.  
   - **Nyckellagringsprovider (KSP)** : För Windows väljer du var du vill lagra nycklarna på enheten.  

4. Välj **OK** > **Skapa** för att spara profilen.
5. Om du vill tilldela den nya profilen till en eller flera enheter läser du [tilldela Microsoft Intune-enhetsprofiler](../configuration/device-profile-assign.md).



