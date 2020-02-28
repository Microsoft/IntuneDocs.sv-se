---
title: Felsöka problem med registrering av Windows-enheter i Microsoft Intune
titleSuffix: Microsoft Intune
description: Förslag på felsökning av några av de vanligaste problemen när du registrerar Windows-enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: dae8e92209a8640ab3254e073d3043d390c3791b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514259"
---
# <a name="troubleshoot-windows-device-enrollment-problems-in-microsoft-intune"></a>Felsöka problem med registrering av Windows-enheter i Microsoft Intune

Den här artikeln hjälper Intune-administratörer att förstå och felsöka problem när de registrerar Windows-enheter i Intune.

## <a name="prerequisites"></a>Krav
Innan du påbörjar felsökningen är det viktigt att samla in grundläggande information. Den här informationen kan hjälpa dig att bättre förstå problemet och minska tiden för att hitta en lösning.

Samla in följande information om problemet:
- Är en giltig Intune-licens tilldelad användaren? Innan användarna kan registrera sina enheter måste de ha tilldelats rätt licenser.
- Är den senaste uppdateringen installerad på Windows-enheten? Vissa funktioner i Intune fungerar bara med den senaste versionen av Windows. Det finns många korrigeringar för kända problem som är tillgängliga via Windows Update. Genom att använda alla de senaste uppdateringarna korrigeras ofta ett problem med registrering av Windows-enheter. 
- Vilket är det exakta felmeddelandet?
- Var visas felmeddelandet?
- När började problemet? Har registreringen någonsin fungerat? 
- Vilken plattform (Android, iOS/iPad, Windows) har problemet?
- Hur många användare påverkas? Påverkas alla användare eller bara vissa av dem?
- Hur många enheter påverkas? Påverkas alla enheter eller bara vissa av dem?
- Vad är MDM-utfärdare?
- Hur utförs registreringen? Är det ”ta med din egen enhet” (BYOD) eller Apple-programmet för enhetsregistrering (DEP) med registreringsprofiler?

## <a name="error-messages"></a>Felmeddelanden

### <a name="this-user-is-not-authorized-to-enroll"></a>Den här användaren har inte behörighet att registrera.

Fel 0x801c003: "den här användaren har inte behörighet att registrera. Du kan försöka att göra detta igen eller kontakta systemadministratören och ange felkoden (0x801c0003)."
Fel 80180003: ”Något gick fel. Den här användaren har inte behörighet att registrera. Du kan försöka att göra detta igen eller kontakta systemadministratören och ange felkoden 80180003."

**Orsak:** Något av följande villkor: 

- Användaren har redan registrerat det maximala antalet enheter som tillåts i Intune.    
- Enheten blockeras av begränsningar för enhetstyp.    
- Datorn kör Windows 10 Home. Registrering i Intune eller anslutning till Azure AD stöds dock bara på Windows 10 Pro och senare versioner.

#### <a name="resolution"></a>Lösning
Det finns flera möjliga lösningar på det här problemet:

##### <a name="remove-devices-that-were-enrolled"></a>Ta bort enheter som har registrerats
1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).    
2. Gå till **Användare** > **Alla användare**.    
3. Välj det berörda användarkontot och klicka sedan på **Enheter**.    
4. Välj eventuella oanvända eller oönskade enheter och klicka sedan på **Ta bort**. 

##### <a name="increase-the-device-enrollment-limit"></a>Öka enhetens registreringsgräns

> [!NOTE]
> Den här metoden ökar enhetsregistreringsgränsen för alla användare, inte bara den berörda användaren.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Gå till **Enheter** > **Registreringsbegränsningar** > **Standard** (under **Begränsningar för antal enheter**) > **Egenskaper** > **Redigera** (intill **Enhetsgräns**) > öka **Enhetsgränsen** (max 15) > **Granska + Spara**.    
 

##### <a name="check-device-type-restrictions"></a>Kontrollera begränsningar för enhetstypen
1. Logga in på [Administrationscenter för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ett globalt administratörskonto.
2. Gå till **Enheter** > **Registreringsbegränsningar** och välj sedan **Standardbegränsning** under **Regränsningar för enhetstyp**.    
3. Välj **Plattformar** och välj sedan **Tillåt** för **Windows (MDM)** .

    > [!IMPORTANT]
    > Om den aktuella inställningen redan är **Tillåt**, ändra den till **Blockera**, spara inställningen och ändra sedan tillbaka till **Tillåt** och spara inställningen igen. Detta återställer registreringsinställningen.

4. Vänta i cirka 15 minuter och registrera sedan den berörda enheten igen.    

##### <a name="upgrade-windows-10-home"></a>Uppgradera Windows 10 Home
[Uppgradera Windows 10 Home till Windows 10 Pro](https://support.microsoft.com/help/12384/windows-10-upgrading-home-to-pro) eller en senare utgåva. 



### <a name="this-user-is-not-allowed-to-enroll"></a>Den här användaren får inte registreras.

Fel 0x801c0003: "Den här användaren får inte registreras. Du kan försöka igen eller kontakta systemadministratören och ange felkoden 801c0003."

**Orsak:** **Användare kan ansluta enheter till Azure AD** inställningen är inställd på **Ingen**. Detta förhindrar att nya användare ansluter sina enheter till Azure AD. Intune-registreringen misslyckades därför.

#### <a name="resolution"></a>Lösning
1. Logga in på [Azure-portalen](https://portal.azure.com/) som administratör.    
2. Gå till **Azure Active Directory** > **Enheter** > **Enhetsinställningar**.    
3. Ange **Användare kan ansluta enheter till Azure AD** till **Alla**.    
4. Registrera enheten igen.   

### <a name="the-device-is-already-enrolled"></a>Enheten är redan registrerad.

Fel 8018000a: "Något gick fel. Enheten är redan registrerad.  Du kan kontakta systemadministratören och ange felkod 8018000a."

**Orsak:** Ett av följande villkor är sant:
- En annan användare har redan registrerat enheten i Intune eller anslutit enheten till Azure AD. Du kan ta reda på om detta är fallet genom att gå till **Inställningar** > **Konton** > **Åtkomst till arbetsplats**. Sök efter ett meddelande som liknar det följande: "En annan användare på systemet är redan ansluten till en arbetsplats eller en skola. Ta bort den här arbets- eller skolanslutningen och försök igen."    

#### <a name="resolution"></a>Lösning

Använd någon av följande metoder för att lösa problemet:

##### <a name="remove-the-other-work-or-school-account"></a>Ta bort det andra arbets- eller skolkontot
1. Logga ut från Windows och logga sedan in med det andra kontot som har registrerat eller anslutit enheten.    
2. Gå till **Inställningar** > **Konton** > **Arbetsåtkomst** och ta sedan bort arbets- eller skolkontot.
3. Logga ut från Windows och logga sedan in med ditt konto.    
4. Registrera enheten i Intune eller anslut enheten till Azure AD. 



### <a name="this-account-is-not-allowed-on-this-phone"></a>Det här kontot är inte tillåtet på den här telefonen.

Fel: "Det här kontot är inte tillåtet på den här telefonen. Kontrollera att informationen du angav är korrekt och försök sedan igen eller be om support från ditt företag."

**Orsak:** Användaren som försökte registrera enheten har ingen giltig Intune-licens.

#### <a name="resolution"></a>Lösning
Tilldela användaren en giltig Intune-licens och registrera sedan enheten.


### <a name="looks-like-the-mdm-terms-of-use-endpoint-is-not-correctly-configured"></a>Det verkar som om slutpunkten för MDM-användningsvillkoren inte har konfigurerats korrekt.

**Orsak:** Ett av följande villkor är sant: 
 - Du använder både hantering av mobila enheter (MDM) för Office 365 och Intune på klienten och den användare som försöker registrera enheten har ingen giltig Intune-licens eller licens för Office 365.     
- MDM-villkoren i Azure AD är tomma eller innehåller inte rätt URL.    

#### <a name="resolution"></a>Lösning

Använd någon av följande metoder för att åtgärda problemet: 
 
##### <a name="assign-a-valid-license-to-the-user"></a>Tilldela användaren en giltig licens
Gå till [Administrationscentret för Microsoft 365](https://portal.office.com/adminportal/home) och tilldela sedan antingen en Intune- eller Office 365-licens till användaren.

##### <a name="correct-the-mdm-terms-of-use-url"></a>Korrigera MDM-villkor för användning för MDM
  1. Logga in på [Azure-portalen](https://portal.azure.com/) och välj sedan **Azure Active Directory**.    
  2. Välj **Mobilitet (MDM och MAM)** och klicka sedan på **Microsoft Intune**.    
  3. Välj **Återställ standard-MDM-URL:er**, kontrollera att **URL:en för MDM-användning** är **https://portal.manage.microsoft.com/TermsofUse.aspx** .    
  4. Välj **Spara**.    


### <a name="something-went-wrong"></a>Något gick fel.

Fel 80180026: ”Något gick fel. Bekräfta att du använder rätt inloggningsinformation och att din organisation använder den här funktionen. Du kan försöka att göra detta igen eller kontakta systemadministratören och ange felkoden 80180026."

**Orsak:** Det här felet kan inträffa när du försöker ansluta en Windows 10-dator till Azure AD och båda följande villkor är uppfyllda: 
- Automatisk MDM-registrering är aktiverat i Azure.    
- Intune PC-klienten (Intune PC agent) är installerad på Windows 10-datorn.

#### <a name="resolution"></a>Lösning
Använd någon av följande metoder för att åtgärda problemet:

##### <a name="disable-mdm-automatic-enrollment-in-azure"></a>Inaktivera automatisk registrering i MDM i Azure.
1. Logga in på [Azure Portal](https://portal.azure.com/).    
2. Gå till **Azure Active Directory** > **Mobilitet (MDM och MAM)**  > **Microsoft Intune**.    
3. Ställ in **Användaromfång för MDM** på **Ingen** och klicka sedan på **Spara**.    
     
##### <a name="uninstall"></a>Avinstallera
Avinstallera Intune PC-klientagenten från datorn.    

### <a name="the-software-cannot-be-installed"></a>Det går inte att installera programmet.

Fel: "Det går inte att installera programvaran, 0x80cf4017."

**Orsak:** Klientprogramvaran är inaktuell.

#### <a name="resolution"></a>Lösning
1. Logga in på [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Gå till **Admin** > **Hämta klientprogramvara**och klicka sedan på **Hämta klientprogramvara**.    
3. Spara installationspaketet och installera sedan klientprogramvaran. 


### <a name="the-account-certificate-is-not-valid-and-may-be-expired"></a>Kontocertifikatet är inte giltigt och kan ha upphört att gälla.

Fel: ”Kontocertifikatet är inte giltigt och kan ha upphört att gälla, 0x80cf4017”.

**Orsak:** Klientprogramvaran är inaktuell.

#### <a name="resolution"></a>Lösning
1. Logga in på [https://admin.manage.microsoft.com](https://admin.manage.microsoft.com).    
2. Gå till **Admin** > **Hämta klientprogramvara**och klicka sedan på **Hämta klientprogramvara**.    
3. Spara installationspaketet och installera sedan klientprogramvaran.    

### <a name="your-organization-does-not-support-this-version-of-windows"></a>Din organisation har inte stöd för den här versionen av Windows. 

Fel: "Det uppstod ett problem. Din organisation har inte stöd för den här versionen av Windows.  (0x80180014)"

**Orsak:** Windows MDM-registrering har inaktiverats i din Intune-klient.

#### <a name="resolution"></a>Lösning
Följ dessa steg om du vill åtgärda det här problemet i en fristående Intune-miljö: 
 
1. I [Administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Enheter** > **Registreringsbegränsningar** > välj en begränsning av enhetstyp.    
2. Välj **Egenskaper** > **Redigera** (intill **Plattformsinställningar**) > **Tillåt** **Windows (MDM)** .    
3. Klicka på **Granska och spara**.    

### <a name="a-setup-failure-has-occurred-during-bulk-enrollment"></a>Ett installationsfel uppstod under massregistreringen.

**Orsak:** Azure AD-användarkontona i kontopaketet (Package_GUID) för respektive etableringspaket får inte ansluta enheter till Azure AD. Dessa Azure AD-konton skapas automatiskt när du konfigurerar ett konfigurationspaket med Windows Configuration Designer (WCD) eller ställer in skoldatorer. Dessa konton används sedan för att ansluta enheterna till Azure AD.

#### <a name="resolution"></a>Lösning
1. Logga in på [Azure-portalen](https://portal.azure.com/) som administratör.    
2. Gå till **Azure Active Directory > Enheter > Enhetsinställningar**.    
3. Ange **Användare kan ansluta enheter till Azure AD** som **Alla** eller **Markerade**.

   Om du väljer **Markerad** klickar du på **Markerad** och klickar sedan på **Lägg till medlemmar** för att lägga till alla användare som kan ansluta sina enheter till Azure AD. Se till att alla Azure AD-konton för etableringspaketet har lagts till.
 
Mer information om hur du skapar ett konfigurationspaket för Windows Configuration Designer finns i [Skapa ett konfigurations paket för Windows 10](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-create-package).

Mer information om appen för att konfigurera skoldatorer finns i [Använda appen för att konfigurera skoldatorer](https://docs.microsoft.com/education/windows/use-set-up-school-pcs-app).


### <a name="auto-mdm-enroll-failed"></a>Automatisk MDM-registrering: Misslyckades 

När du försöker registrera en Windows 10-enhet automatiskt med hjälp av grupprincip uppstår följande problem: 
- I Schemaläggaren, under **Microsoft** > **Windows** > **EnterpriseMgmt** är det senaste körningsresultatet från uppgiften **Schemat som skapats av registreringsklienten för automatisk registrering i MDM från AAD** följande: **Händelse 76 automatisk MDM-registrering: Misslyckades (okänd Win32-felkod: 0x8018002b)**       
- I loggboken loggas följande händelse under **Program- och tjänstloggar/Microsoft/Windows/DeviceManagement-Enterprise-Diagnostics-Provider/admin**:   
    ```asciidoc
    Log Name: Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider/Admin
    Source: DeviceManagement-Enterprise-Diagnostics-Provider
    Event ID: 76
    Level: Error
    Description: Auto MDM Enroll: Failed (Unknown Win32 Error code: 0x80180002b)
    ```
**Orsak:** Ett av följande villkor är sant: 
- UPN:en innehåller en overifierad eller icke-dirigerad domän, till exempel .local (t.ex. joe@contoso.local).    
- **MDM-användaromfång** har angetts till **Ingen**. 

#### <a name="resolution"></a>Lösning
Om UPN:en innehåller en overifierad eller icke-dirigerad domän ska du följa följande steg: 

1. Öppna **Active Directory-användare och -datorer** genom att skriva **DSA.msc** i dialogrutan **kör** på den server som Active Directory Domain Services (AD DS) körs på och klicka sedan på **OK**.    
2. Klicka på **Användare** under din domän och gör sedan följande:  
    - Om det bara finns en berörd användare högerklickar du på användaren och klickar sedan på **Egenskaper**. På fliken **Konto** i listrutan UPN-suffix under **Användarens inloggningsnamn** väljer du ett giltigt UPN-suffix, till exempel contoso.com, och klickar sedan på **OK**.    
    - Om det finns flera berörda användare väljer du användare i menyn **Åtgärd** och klickar på **Egenskaper**. Markera kryssrutan **UPN-suffix** på fliken **Konto**. Välj ett giltigt UPN-suffix, till exempel contoso.com, i listrutan och klicka sedan på **OK**.
3. Vänta på nästa synkronisering eller framtvinga en Delta-synkronisering från synkroniseringstjänsten genom att köra följande kommandon i en upphöjd PowerShell-prompt:
    ```powershell
    Import-Module ADSync
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

Om **användarområdet för MDM** är inställt på **Ingen** följer du dessa steg: 
 
1. Logga in på [Azure-portalen](https://portal.azure.com/) och välj sedan **Azure Active Directory**.
2. Välj **Mobilitet (MDM och MAM)** och välj sedan **Microsoft Intune**.    
3. Ange **Användaromfång för MDM** till **Alla**. Eller ange **MDM-användaromfånget** till **Vissa** och välj de grupper som kan registrera sina Windows 10-enheter automatiskt.    
4. Ange **MAM-användaromfång** till **Ingen**.


### <a name="an-error-occurred-while-creating-autopilot-profile"></a>Ett fel uppstod när Autopilotprofilen skulle skapas.

**Orsak:** Det angivna namngivningsformatet för enhetsnamnsmallen uppfyller inte kraven. Du kan till exempel använda gemener för det seriella makrot, t. ex .%seriell% i stället för %SERIELL%.

#### <a name="resolution"></a>Lösning

Kontrollera att namngivningsformatet uppfyller följande krav:

- Skapa ett unikt namn på dina enheter. Namnet får innehålla högst 15 tecken som ska bestå av bokstäver (a-z, A-Z), siffror (0-9) och bindestreck (-).
- Namn kan inte bestå av enbart siffror.
- Namn får inte innehålla blanksteg.
- Använd makrot %SERIAL% för att lägga till ett maskinvaruspecifikt serienummer. Du kan också använda kommandot %RAND:<antal siffror>% för att lägga till en slumpmässig sträng med siffror. Strängen innehåller <antal siffror> siffror. Till exempel skapar MYPC-%RAND:6% namn som MYPC-123456.

### <a name="something-went-wrong-oobeidps"></a>Något gick fel. OOBEIDPS.

**Orsak:** Det här problemet uppstår om det finns en proxy, brandvägg eller annan nätverksenhet som blockerar åtkomsten till identitetsleverantören (IdP).

#### <a name="resolution"></a>Lösning
Se till att den begärda åtkomsten till internetbaserade tjänster för autopilot inte är blockerad. Mer information finns i [Nätverkskrav för Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements-network).


### <a name="registering-your-device-for-mobile-management-failed3-0x801c03ea"></a>Registrera enheten för mobilhantering (misslyckades: 3, 0x801C03EA).

**Orsak:** Enheten har ett TPM-chip som stöder version 2.0, men som ännu inte har uppgraderats till version 2.0.

#### <a name="resolution"></a>Lösning
Uppgradera TPM-kretsen till version 2.0.

Om problemet kvarstår kontrollerar du om samma enhet finns i två tilldelade grupper, där varje grupp tilldelas en annan Autopilotprofil. Om det finns två grupper bestämmer du vilken Autopilotprofil som ska användas på enheten och tar sedan bort den andra profiltilldelningen.

Mer information om hur du distribuerar en Windows-enhet i helskärmsläge med Autopilot finns i [Distribuera helskärmsläge med Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="securing-your-hardware-failed-0x800705b4"></a>Skydda maskinvaran (misslyckades: 0x800705b4).

Fel 800705b4: 
```
Securing your hardware (Failed: 0x800705b4)
Joining your organization's network (Previous step failed)
Registering your device for mobile management (Previous step failed)
```

**Orsak:** Den riktade Windows-enheten uppfyller inte något av följande krav:

- Enheten måste ha ett fysiskt TPM 2.0-chip. Enheter med virtuella TPM:er (till exempel virtuella Hyper-V-datorer) eller TPM 1.2-chips fungerar inte med självdistributionsläge.
- Enheten måste köra någon av följande versioner av Windows:
    - Windows 10 version 1703 eller senare.
    - Om Hybrid Azure AD Join används, Windows 10 version 1809 eller senare.


#### <a name="resolution"></a>Lösning
Kontrollera att målenheten uppfyller båda kraven som beskrivs i avsnittet **Orsak**.

Mer information om hur du distribuerar en Windows-enhet i helskärmsläge med Autopilot finns i [Distribuera helskärmsläge med Windows Autopilot](https://blogs.technet.microsoft.com/mniehaus/2018/06/07/deploying-a-kiosk-using-windows-autopilot/).


### <a name="something-went-wrong-error-code-80070774"></a>Något gick fel. Felkod 80070774.

Fel 0x80070774: Något gick fel. Bekräfta att du använder rätt inloggningsinformation och att din organisation använder den här funktionen. Du kan försöka att göra detta igen eller kontakta systemadministratören och ange felkoden 80070774.

Det här problemet uppstår vanligtvis innan enheten startas om i ett scenario med en Hybrid Azure AD-pilot när enheten har nått sin första inloggningsskärm. Det innebär att domänkontrollanten inte kan hittas eller nås på grund av anslutningsproblem. Eller att enheten har hamnat i ett tillstånd som inte kan ansluta till domänen.

**Orsak:** Den vanligaste orsaken är att Hybrid Azure AD-anslutning används och att funktionen Tilldela användare konfigureras i Autopilot-profilen. Om du använder funktionen Tilldela användare utförs en Azure AD-anslutning på enheten under den första inloggningsskärmen som placerar enheten i ett tillstånd där den inte kan ansluta till din lokala domän. Därför bör funktionen Tilldela användare bara användas i standardscenarier för Azure AD Join Autopilot.  Funktionen ska inte användas i scenarier med Hybrid Azure AD-anslutning.

#### <a name="resolution"></a>Lösning

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du > **Enheter** > **Windows** > **Windows-enheter**.
2. Välj den enhet där problemet förekommer > Klicka på ellipsen (...) på den högra sidan.
3. Välj **Ta bort tilldelning av användare** och vänta tills processen har slutförts.
4. Verifiera att Hybrid Azure AD Autopilot-profilen tilldelas innan du försöker att starta om OOBE.

#### <a name="second-resolution"></a>Alternativ lösning
Om problemet kvarstår går du till den server som är värd för Offline Domain Intune Connector och kontrollerar om händelse-ID 30312 har loggats i ODJ Connector Service-loggen. Händelse 30312 ser ut ungefär så här:

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

Det här problemet beror vanligtvis på felaktigt delegerade behörigheter till organisationsenheten där Windows Autopilot-enheter skapas. Mer information finns i [Öka datorkontogränsen i organisationsenheten](windows-autopilot-hybrid.md#increase-the-computer-account-limit-in-the-organizational-unit).

1. Öppna **Active Directory – användare och datorer (DSA.msc)** .
2. Högerklicka på den organisationsenhet som ska användas för att skapa Azure AD-anslutna hybriddatorer > **Delegera kontroll**.
3. I guiden för **delegering av kontroll** väljer du **Nästa** > **Lägg till** > **Objekttyper**.
4. I fönstret **Objekttyper** markerar du kryssrutan **Datorer** > **OK**.
5. I fönstret **Välj användare**, **Datorer** eller **Grupper** går du till rutan **Ange de objektnamn som ska väljas** och anger namnet på datorn där anslutningsappen är installerad.
6. Välj **Kontrollera namn** för att verifiera posten > **OK** > **Nästa**.
7. Välj **Skapa en anpassad aktivitet och delegera kontroll för den** > **Nästa**.
8. Markera kryssrutan **Endast följande objekt i mappen** och markera sedan kryssrutorna **Datorobjekt**, **Skapa valda objekt i den här mappen** och **Ta bort valda objekt i den här mappen**.
9. Välj **Nästa**.
10. Under **Behörigheter** markerar du kryssrutan **Fullständig kontroll**. Den här åtgärden markerar alla de andra alternativen.
11. Välj **Nästa** > **Slutför**.

### <a name="the-enrollment-status-page-times-out-before-the-sign-in-screen"></a>Sidan för registreringsstatus har nått sin tidsgräns före inloggningsskärmen

**Orsak:** Det här problemet kan uppstå om samtliga följande villkor är uppfyllda:
- Du använder sidan registreringsstatus för att spåra Microsoft Store för företagsprogram.
- Du har en princip för villkorlig åtkomst till Azure AD som använder alternativet Kräv att en enhet är markerad som kompatibilitetskontroll.
- Principen gäller för alla molnappar och Windows.

#### <a name="resolution"></a>Lösning:
Prova något av följande:
- Rikta dina Intune-efterlevnadsprinciper till enheter. Kontrollera att efterlevnaden kan fastställas innan användaren loggar in.
- Använd offline-licensiering för Store-appar. På så sätt behöver inte Windows-klienten kontrollera med Microsoft Store innan du fastställer enhetens kompatibilitet.



## <a name="next-steps"></a>Nästa steg

- [Felsöka enhetsregistrering i Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Ställ en fråga i Intunes forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Läs Microsoft Intune-supportteamets blogg](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Läs bloggen om Enterprise Mobility and Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
- [Få support för Microsoft Intune](../fundamentals/get-support.md)
- [Hitta registreringsfel för samhantering](https://docs.microsoft.com/configmgr/comanage/how-to-monitor#enrollment-errors)
