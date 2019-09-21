---
title: Felsöka problem med registrering av Windows-enheter i Microsoft Intune
titleSuffix: Microsoft Intune
description: Förslag på fel sökning av några av de vanligaste problemen när du registrerar Windows-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f78f069f46ce036752fde80519abc03dc7c424c
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167773"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Felsöka problem med registrering av Windows-enheter i Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem vid registrering av Windows-enheter i Intune.

## <a name="prerequisites"></a>Krav
Innan du påbörjar fel sökningen är det viktigt att samla in grundläggande information. Den här informationen kan hjälpa dig att bättre förstå problemet och minska tiden för att hitta en lösning.

Samla in följande information om problemet:
- Är en giltig Intune-licens tilldelad användaren? Innan användarna kan registrera sina enheter måste de ha tilldelats rätt licenser.
- Är den senaste uppdateringen installerad på Windows-enheten? Vissa funktioner i Intune fungerar bara med den senaste versionen av Windows. Det finns många korrigeringar för kända problem som är tillgängliga via Windows Update. Genom att använda alla de senaste uppdateringarna korrigeras ofta ett problem med registrering av Windows-enheter. 
- Vilket är det exakta felmeddelandet?
- Var visas fel meddelandet?
- När började problemet? Har registreringen någonsin fungerat? 
- Vilken plattform (Android, iOS, Windows) har problemet?
- Hur många användare påverkas? Påverkas alla användare eller bara vissa av dem?
- Hur många enheter påverkas? Påverkas alla enheter eller bara vissa av dem?
- Vad är MDM-utfärdare? Vilken version av Configuration Manager använder du om det är System Center Configuration Manager?
- Hur utförs registreringen? Är det "ta med din egen enhet" (BYOD) eller Apple Programmet för enhetsregistrering (DEP) med registrerings profiler?

## <a name="error-messages"></a>Felmeddelanden

### <a name="this-user-is-not-authorized-to-enroll"></a>Den här användaren har inte behörighet att registrera.

Fel 0x801c003: "den här användaren har inte behörighet att registrera. Du kan försöka att göra detta igen eller kontakta system administratören och få felkod (0x801c0003). "
Fel 80180003: ”Något gick fel. Den här användaren har inte behörighet att registrera. Du kan försöka att göra detta igen eller kontakta system administratören och få felkod 80180003. "

**Orsak:** Något av följande villkor: 

- Användaren har redan registrerat det maximala antalet enheter som tillåts i Intune.    
- Enheten blockeras av begränsningar för enhets typ.    
- Datorn kör Windows 10 Home. Registrering i Intune eller anslutning till Azure AD stöds dock bara på Windows 10 Pro och senare versioner.

#### <a name="resolution"></a>Lösning
Det finns flera möjliga lösningar på det här problemet:

##### <a name="remove-devices-that-were-enrolled"></a>Ta bort enheter som har registrerats
1. Logga in på [Azure Portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).    
2. Gå till **användare** > **alla användare**.    
3. Välj det berörda användar kontot och klicka sedan på **enheter**.    
4. Välj eventuella oanvända eller oönskade enheter och klicka sedan på **ta bort**. 

##### <a name="increase-the-device-enrollment-limit"></a>Öka enhetens registreringsgräns

> [!NOTE]
> Den här metoden ökar enhets registrerings gränsen för alla användare, inte bara den berörda användaren.

1. Logga in på [Azure Portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview).
2. Gå till**registrerings begränsningar**för **enhets registrering** > och välj sedan **begränsningar för enhets gräns**.    
3. Öka värdet för **enhets gräns**. 

##### <a name="check-device-type-restrictions"></a>Kontrollera begränsningar för enhetstypen
1. Logga in på [Intune-portalen](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) med ett konto som global administratör.
2. Gå till**registrerings begränsningar**för **enhets registrering** > och välj sedan **standard** begränsning under **begränsningar av enhets typ**.    
3. Välj **plattformar**och välj sedan **Tillåt** för **Windows (MDM)** .

    > [!IMPORTANT]
    > Om den aktuella inställningen redan **tillåter**, ändra den till **blockera**, spara inställningen och ändra sedan tillbaka till **Tillåt** och spara inställningen igen. Detta återställer inställningen för registrering.

4. Vänta i cirka 15 minuter och registrera sedan den berörda enheten igen.    

##### <a name="upgrade-windows-10-home"></a>Uppgradera Windows 10 Home
[Uppgradera Windows 10 Home till Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) eller en högre utgåva. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Den här användaren får inte registreras.

Fel 0x801c0003: "den här användaren får inte registreras. Du kan försöka igen eller kontakta system administratören och returnera felkoden 801c0003. "

**Orsak:** **Användare kan ansluta enheter till Azure AD** -inställningen är inställd på **ingen**. Detta förhindrar att nya användare ansluter sina enheter till Azure AD. Det går därför inte att registrera Intune.

#### <a name="resolution"></a>Lösning
1. Logga in på [Azure Portal](https://portal.azure.com/) som administratör.    
2. Gå till**enhets inställningarna**för **Azure Active Directory** > **enheter** > .    
3. Ange **Användare kan ansluta enheter till Azure AD** till **Alla**.    
4. Registrera enheten igen.   

### <a name="the-device-is-already-enrolled"></a>Enheten är redan registrerad.

Fel 8018000a: "något gick fel. Enheten är redan registrerad.  Du kan kontakta system administratören och få felkod 8018000a. "

**Orsak:** Ett av följande villkor är uppfyllt:
- En annan användare har redan registrerat enheten i Intune eller anslutit enheten till Azure AD. Du kan ta reda på om detta är fallet genom att gå till **Inställningar** > **konton** > **åtkomst till arbets**plats. Sök efter ett meddelande som liknar följande: "en annan användare på systemet är redan ansluten till ett jobb eller en skola. Ta bort den här arbets-eller skol anslutningen och försök igen. "    
- Configuration Manager klient agenten är installerad på datorn.    

#### <a name="resolution"></a>Lösning

Använd någon av följande metoder för att lösa problemet:

##### <a name="remove-the-other-work-or-school-account"></a>Ta bort det andra arbets-eller skol kontot
1. Logga ut från Windows och logga sedan in med det andra kontot som har registrerat eller anslutit enheten.    
2. Gå till **Inställningar** > **konton** > **arbets åtkomst**och ta sedan bort arbets-eller skol kontot.
3. Logga ut från Windows och logga sedan in med ditt konto.    
4. Registrera enheten i Intune eller Anslut enheten till Azure AD. 

##### <a name="remove-the-configuration-manager-client"></a>Ta bort Configuration Manager-klienten
Ta bort Configuration Manager klienten och registrera sedan enheten igen.



### <a name="this-account-is-not-allowed-on-this-phone"></a>Det här kontot är inte tillåtet på den här telefonen.

Fel: "det här kontot tillåts inte på den här telefonen. Kontrol lera att informationen du angav är korrekt och försök sedan igen eller be om support från ditt företag. "

**Orsak:** Den användare som försökte registrera enheten har ingen giltig Intune-licens.

#### <a name="resolution"></a>Lösning
Tilldela användaren en giltig Intune-licens och registrera sedan enheten.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Det verkar som om MDM-villkor för användnings villkoren inte har kon figurer ATS korrekt.

**Orsak:** Ett av följande villkor är uppfyllt: 
 - Du använder både hantering av mobila enheter (MDM) för Office 365 och Intune på klienten, och den användare som försöker registrera enheten har ingen giltig Intune-licens eller en licens för Office 365.     
- MDM-villkoren i Azure AD är tomma eller innehåller inte rätt URL.    

#### <a name="resolution"></a>Lösning

Använd någon av följande metoder för att åtgärda problemet: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Tilldela användaren en giltig licens
Gå till [Microsoft 365 administrations Center](https://portal.office.com/adminportal/home)och tilldela sedan antingen en Intune-eller Office 365-licens till användaren.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Korrigera MDM-villkor för användning för MDM
  1. Logga in på [Azure-portalen](https://portal.azure.com/) och välj sedan **Azure Active Directory**.    
  2. Välj **mobilitet (MDM och MAM)** och klicka sedan på **Microsoft Intune**.    
  3. Välj **Återställ standard MDM-URL: er**, kontrol lera att **URL: en för MDM-användning** har angetts till. **https://portal.manage.microsoft.com/TermsofUse.aspx**    
  4. Välj **Spara**.    


### <a name="something-went-wrong"></a>Något gick fel.

Fel 80180026: ”Något gick fel. Bekräfta att du använder rätt inloggnings information och att din organisation använder den här funktionen. Du kan försöka att göra detta igen eller kontakta system administratören och få felkod 80180026. "

**Orsak:** Det här felet kan inträffa när du försöker ansluta till en Windows 10-dator till Azure AD och båda följande villkor är uppfyllda: 
- Automatisk registrering i MDM är aktiverat i Azure.    
- Antingen Intune PC-klienten (Intune PC agent) eller Configuration Manager klient agenten är installerad på Windows 10-datorn.

#### <a name="resolution"></a>Lösning
Använd någon av följande metoder för att åtgärda problemet:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Inaktivera automatisk registrering i MDM i Azure.
1. Logga in på [Azure Portal](https://portal.azure.com/).    
2. Gå till **Azure Active Directory** > **Mobility (MDM och MAM)**  > **Microsoft Intune**.    
3. Ange **användar omfång för MDM** till **ingen**och klicka sedan på **Spara**.    
     
##### <a name="uninstall"></a>Avinstallera
Avinstallera Intune PC-klienten eller Configuration Manager klient agenten från datorn.    

### <a name="the-software-cannot-be-installed"></a>Det går inte att installera programmet.

Fel: "det går inte att installera program vara, 0x80cf4017."

**Orsak:** Klient program varan är inaktuell.

#### <a name="resolution"></a>Lösning
1. Logga in på [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Gå till **Administratörs** > **program vara Ladda ned**och klicka på **Hämta klient program vara**.    
3. Spara installations paketet och installera sedan klient program varan. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Kontocertifikatet är inte giltigt och kan ha upphört att gälla.

Fel: ”Kontocertifikatet är inte giltigt och kan ha upphört att gälla, 0x80cf4017”.

**Orsak:** Klient program varan är inaktuell.

#### <a name="resolution"></a>Lösning
1. Logga in på [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Gå till **Administratörs** > **program vara Ladda ned**och klicka på **Hämta klient program vara**.    
3. Spara installations paketet och installera sedan klient program varan.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Din organisation har inte stöd för den här versionen av Windows. 

Fel: "det uppstod ett problem. Din organisation har inte stöd för den här versionen av Windows.  (0x80180014) "

**Orsak:** Windows MDM-registrering har inaktiverats i din Intune-klient.

#### <a name="resolution"></a>Lösning
Följ dessa steg om du vill åtgärda det här problemet i en fristående Intune-miljö: 
 
1. Logga in på [Azure Portal](https://portal.azure.com/) som administratör.    
2. Välj **Intune** till vänster och gå sedan till enhets **registrering** > **registrerings begränsningar**.    
3. I **begränsningar för enhets typ**klickar du på **plattformar**och väljer **Tillåt** för **Windows (MDM)** .    
4. Klicka på **Spara**.    
 
Följ dessa steg för att åtgärda problemet i hybrid MDM med Intune och Configuration Manager: 
1. Öppna Configuration Manager-konsolen.    
2. Välj **Administration**och välj sedan **Cloud Services**.    
3. Högerklicka på **Microsoft Intune prenumeration**och välj sedan **Konfigurera plattformar > Windows**.    
4. Markera **Aktivera Windows-registrering** > **Använd** > **OK**.  


### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Ett installations fel uppstod under Mass registreringen.

**Orsak:** Azure AD-användarkontonna i konto paketet (Package_GUID) för respektive etablerings paket får inte ansluta enheter till Azure AD. Dessa Azure AD-konton skapas automatiskt när du konfigurerar ett konfigurations paket med Windows Configuration designer (WCD) eller Ställ in skol datorer, och dessa konton används sedan för att ansluta enheterna till Azure AD.

#### <a name="resolution"></a>Lösning
1. Logga in på [Azure Portal](https://portal.azure.com/) som administratör.    
2. Gå till **Azure Active Directory > enheter > enhets inställningar**.    
3. Ange **Användare kan ansluta enheter till Azure AD** som **Alla** eller **Markerade**.

   Om du väljer **markerad**klickar du på **markerad**och klickar sedan på **Lägg till medlemmar** för att lägga till alla användare som kan ansluta sina enheter till Azure AD. Se till att alla Azure AD-konton för etablerings paketet har lagts till.
 
Mer information om hur du skapar ett konfigurations paket för Windows Configuration Designer finns i [skapa ett konfigurations paket för Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Mer information om appen konfigurera skol datorer finns i [använda appen konfigurera skol datorer](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Automatisk MDM-registrering: misslyckades 

När du försöker registrera en Windows 10-enhet automatiskt med hjälp av grupprincip uppstår följande problem: 
- I Schemaläggaren, under **Microsoft** > **Windows** > **EnterpriseMgmt**, är det senaste körnings resultatet av **schemat som skapats av registrerings klienten för automatisk registrering i MDM från AAD** -uppgiften följande: **Händelse 76 automatisk MDM-registrering: misslyckades (okänd Win32-felkod: 0x8018002b)**       
- I Loggboken loggas följande händelse under **program-och tjänst loggar/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Orsak:** Ett av följande villkor är uppfyllt: 
- UPN: en innehåller en overifierad eller icke-dirigerad domän, t. ex. joe@contoso.locallokal (t. ex.).    
- **MDM-användar omfång** har angetts till **ingen**. 

#### <a name="resolution"></a>Lösning
Om UPN: en innehåller en overifierad eller icke-dirigerad domän, följer du dessa steg: 

1. Öppna **Active Directory användare och datorer** genom att skriva **DSA. msc** i dialog rutan **kör** på den server som Active Directory Domain Services (AD DS) körs på och klicka sedan på **OK**.    
2. Klicka på **användare** under din domän och gör sedan följande:  
    - Om det bara finns en berörd användare högerklickar du på användaren och klickar sedan på **Egenskaper**. På fliken **konto** , i list rutan UPN-suffix under **användarens inloggnings namn**, väljer du ett giltigt UPN-suffix, till exempel contoso.com, och klickar sedan på **OK**.    
    - Om det finns flera berörda användare väljer du användare i menyn **åtgärd** och klickar på **Egenskaper**. Markera kryss rutan **UPN-suffix** på fliken **konto** , Välj ett giltigt UPN-suffix, till exempel contoso.com i list rutan, och klicka sedan på **OK**.
3. Vänta på nästa synkronisering eller framtvinga en Delta synkronisering från synkroniseringstjänsten genom att köra följande kommandon i en upphöjd PowerShell-prompt:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Om **användar området för MDM** är inställt på **ingen**, följer du dessa steg: 
 
1. Logga in på [Azure-portalen](https://portal.azure.com/) och välj sedan **Azure Active Directory**.
2. Välj **mobilitet (MDM och MAM)** och välj sedan **Microsoft Intune**.    
3. Ange **användar omfång för MDM** till **alla**. Eller ange **MDM-användarnamnet** till **vissa**och välj de grupper som kan registrera sina Windows 10-enheter automatiskt.    
4. Ange **Mam användar omfång** till **ingen**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Ett fel uppstod när autopilot-profilen skulle skapas.

**Orsak:** Det angivna namngivnings formatet för enhets namns mal len uppfyller inte kraven. Du kan till exempel använda gemener för det seriella makrot, t. ex.% seriell% i stället för% seriell%.

#### <a name="resolution"></a>Lösning

Kontrol lera att namngivnings formatet uppfyller följande krav:

- Skapa ett unikt namn på dina enheter. Namnet får innehålla högst 15 tecken som ska bestå av bokstäver (a-z, A-Z), siffror (0-9) och bindestreck (-).
- Namn kan inte bestå av enbart siffror.
- Namn får inte innehålla blank steg.
- Använd makrot %SERIAL% för att lägga till ett maskinvaruspecifikt serienummer. Du kan också använda kommandot% RAND: < # av siffror >% för att lägga till en slumpmässig sträng med siffror. strängen innehåller < # siffror > siffror. Till exempel, min-% RAND: 6% genererar ett namn som till exempel min-123456.

### <a name="something-went-wrong-oobeidps"></a>Något gick fel. OOBEIDPS.

**Orsak:** Det här problemet uppstår om det finns en proxy, brand vägg eller annan nätverks enhet som blockerar åtkomsten till identitets leverantören (IdP).

#### <a name="resolution"></a>Lösning
Se till att den begärda åtkomsten till Internetbaserade tjänster för autopilot inte är blockerad. Mer information finns i [Windows autopilot-nätverks krav](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrerar enheten för mobil hantering (misslyckades: 3, 0x801C03EA).

**Orsak:** Enheten har ett TPM-chip som stöder version 2,0, men som ännu inte har uppgraderats till version 2,0.

#### <a name="resolution"></a>Lösning
Uppgradera TPM-kretsen till version 2,0.

Om problemet kvarstår kontrollerar du om samma enhet finns i två tilldelade grupper, där varje grupp tilldelas en annan autopilot-profil. Om det finns två grupper bestämmer du vilken autopilot-profil som ska användas på enheten och tar sedan bort den andra profil tilldelningen.

Mer information om hur du distribuerar en Windows-enhet i hel skärms läge med autopilot finns i [distribuera en kiosk med Windows autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Skydda maskin varan (misslyckades: 0x800705b4).

Fel 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Orsak:** Den riktade Windows-enheten uppfyller inte något av följande krav:

- Enheten måste ha ett fysiskt TPM 2,0-chip. Enheter med virtuella TPM: er (till exempel virtuella Hyper-V-datorer) eller TPM 1,2-chips fungerar inte med själv distributions läge.
- Enheten måste köra någon av följande versioner av Windows:
    - Windows 10 version 1703 eller senare.
    - Om hybrid Azure AD Join används, Windows 10 version 1809 eller senare.


#### <a name="resolution"></a>Lösning
Kontrol lera att den riktade enheten uppfyller båda kraven som beskrivs i avsnittet **orsak** .

Mer information om hur du distribuerar en Windows-enhet i hel skärms läge med autopilot finns i [distribuera en kiosk med Windows autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Något gick fel. Felkod 80070774.

Fel 0x80070774: något gick fel. Bekräfta att du använder rätt inloggnings information och att din organisation använder den här funktionen. Du kan försöka att göra detta igen eller kontakta system administratören och få felkod 80070774.

Det här problemet uppstår vanligt vis innan enheten startas om i ett scenario med en hybrid Azure AD-pilot när enheten har nått sin första inloggnings skärm. Det innebär att domänkontrollanten inte kan hittas eller har nåtts på grund av anslutnings problem. Eller att enheten har angett ett tillstånd som inte kan ansluta till domänen.

**Orsak:** Den vanligaste orsaken är att hybrid Azure AD-anslutning används och att funktionen tilldela användare konfigureras i autopilot-profilen. Om du använder funktionen tilldela användare utförs en Azure AD-anslutning på enheten under den inledande inloggnings skärmen som placerar enheten i ett tillstånd där den inte kan ansluta till din lokala domän. Därför bör funktionen tilldela användare bara användas i scenarier för automatisk pilot i Azure AD Join.  Funktionen ska inte användas i scenarier med hybrid Azure AD-anslutning.

#### <a name="resolution"></a>Lösning

1. Gå till **Intune** >  **enhets registrering** > **Windows** > -**enheter**för registrering.
2. Välj den enhet som upplever problemet > Klicka på ellipsen (...) på den högra sidan.
3. Välj **ta bort tilldelning av användare** och vänta tills processen har slutförts.
4. Verifiera att hybrid Azure AD autopilot-profilen tilldelas innan du försöker att starta om OOBE.

#### <a name="second-resolution"></a>Andra upplösning
Om problemet kvarstår går du till den server som är värd för den frånkopplade domänen Anslut till Intune Connector för att se om händelse-ID 30312 är loggat i ODJ Connector service-loggen. Händelse 30312 ser ut ungefär så här:

```
Log Name:      ODJ Connector Service
Source:        ODJ Connector Service Source
Event ID:      30132
Level:         Error
Description:
{
          "Metric":{
                   "Dimensions":{
                             "RequestId":"<RequestId>",
                             "DeviceId":"<DeviceId>",
                             "DomainName":"contoso.com",
                             "ErrorCode":"5",
                             "RetryCount":"1",
                              "ErrorDescription":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation",
                              "InstanceId":"<InstanceId>",
                              "DiagnosticCode":"0x00000800",
                              "DiagnosticText":"Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation [Exception Message: \"DiagnosticException: 0x00000800. Failed to get the ODJ Blob. The ODJ connector does not have sufficient privileges to complete the operation\"] [Exception Message: \"Failed to call NetProvisionComputerAccount machineName=<ComputerName>\"]"
                   },
                   "Name":"RequestOfflineDomainJoinBlob_Failure",
                   "Value":0
          }
}
```

Det här problemet beror vanligt vis på felaktigt delegerade behörigheter till organisationsenheten där Windows autopilot-enheter skapas. Mer information finns i [öka dator konto gränsen i organisationsenheten](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Öppna **Active Directory – användare och datorer (DSA.msc)** .
2. Högerklicka på den organisationsenhet som ska användas för att skapa Azure AD-anslutna hybriddatorer > **Delegera kontroll**.
3. I guiden för **delegering av kontroll** väljer du **Nästa** > **Lägg till** > **Objekttyper**.
4. I fönstret **Objekttyper** markerar du kryssrutan **Datorer** > **OK**.
5. I fönstret **Välj användare**, **Datorer** eller **Grupper** går du till rutan **Ange de objektnamn som ska väljas** och anger namnet på datorn där anslutningsappen är installerad.
6. Välj **kontrol lera namn** för att validera posten > **OK** > **Nästa**.
7. Välj **Skapa en anpassad aktivitet och delegera kontroll för den** > **Nästa**.
8. Markera kryssrutan **Endast följande objekt i mappen** och markera sedan kryssrutorna **Datorobjekt**, **Skapa valda objekt i den här mappen** och **Ta bort valda objekt i den här mappen**.
9. Välj **Nästa**.
10. Under **Behörigheter** markerar du kryssrutan **Fullständig kontroll**. Den här åtgärden markerar alla de andra alternativen.
11. Välj **Nästa** > **Slutför**.

## <a name="next-steps"></a>Nästa steg

- [Felsöka enhetsregistrering i Intune](troubleshoot-device-enrollment-in-intune.md)
- [Ställ en fråga i Intunes forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Kontrol lera Microsoft Intune support teamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Kontrol lera Microsoft Enterprise Mobility and Security-bloggen](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Få support för Microsoft Intune](get-support.md)
