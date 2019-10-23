---
title: Krypteringsrapport för krypterade enheter i Microsoft Intune
titleSuffix: Microsoft Intune
description: Visa en rapport över krypteringsstatusen för iOS- eller Windows-enheter och få åtkomst till FileVault- och BitLocker-återställningsnycklar från Microsoft Intune-portalen.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4d53179ed43697769ec7142ace6b62c08a67f31a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502344"
---
# <a name="monitor-device-encryption-with-intune"></a>Övervaka enhetskryptering med Intune   

Krypteringsrapporten i Microsoft Intune är en central plats där du kan visa information om en enhets krypteringsstatus och se alternativ för hantering av enhetsåterställningsnycklar. Vilka alternativ för återställningsnycklar som är tillgängliga beror på vilken typ av enhet du visar.  

Du hittar rapporten genom att logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), gå till **Enhetskonfiguration** följt av *Övervakare*, där du väljer **Krypteringsrapport**.  

## <a name="view-encryption-details"></a>Visa krypteringsinformation  

Krypteringsrapporten innehåller allmän information för de hanterade enheter som stöds. I följande avsnitt finns information om vilken information som Intune visar i rapporten.  
 
### <a name="prerequisites"></a>Krav:  

Krypteringsrapporten stöder rapportering på enheter som kör följande operativsystemversioner:  
- macOS 10.13 eller senare  
- Windows version 1607 eller senare  

### <a name="report-details"></a>Rapportinformation  

Fönstret Krypteringsrapport innehåller en lista över de enheter som du hanterar med översiktlig information om enheterna. Du kan välja en enhet i listan om du vill granska och visa mer information i fönstret [Enhetens krypteringsstatus.](#device-encryption-status)  

- **Enhetsnamn** – Namnet på enheten.  
- **Operativsystem** – Enhets plattform, till exempel Windows eller macOS.  
- **Operativsystemversion** – Versionen av Windows eller macOS på enheten.  
- **TPM-version** *(gäller endast Windows 10)* – Versionen av TPM-kretsen (Trusted Platform Module) på Windows 10-enheten.  
- **Krypteringsberedskap** – En utvärdering av enheternas beredskap för en viss krypteringsteknik, t.ex. BitLocker- eller FileVault-kryptering. Enheter identifieras som:  
  - **Redo**: Enheten kan krypteras med MDM-principen, som kräver att enheten uppfyller följande krav:  
    
    **För macOS-enheter**:  
    - MacOS version 10.13 eller senare  
    
    **För Windows 10-enheter**:  
    - Version 1703 eller senare av *Business*, *Enterprise* eller *Education*, eller version 1809 eller senare av *Pro*  
    - Enheten måste ha en TPM-krets  
    
    Mer information finns i [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) i Windows-dokumentationen.  

  - **Ej redo**: Enheten har inte fullständiga krypteringsfunktioner, men har fortfarande stöd för kryptering. Exempelvis kan en Windows-enhet krypteras manuellt av en användare, eller via en grupprincip som kan konfigureras att tillåta kryptering utan en TPM.
  - **Ej tillämpligt**: Det finns inte tillräckligt med information för att klassificera den här enheten.  

- **Krypteringsstatus** – avser huruvida OS-enheten är krypterad.  

- **Namn på användarprincip** – Enhetens primära användare.  

### <a name="device-encryption-status"></a>Enhetskrypteringsstatus  

När du väljer en enhet från krypteringsrapporten visas fönstret **Enhetens krypteringsstatus** i Intune. Det här fönstret innehåller följande information:  

- **Enhetsnamn** – namnet på den enhet som du visar.  

- **Krypteringsberedskap** – En utvärdering av enheternas beredskap för kryptering via MDM-principen.  
  
  Exempel: När en Windows 10-enhet har beredskapen *Inte klar* kan den fortfarande ha stöd för kryptering. För att Windows 10-enheten ska ha statusen *Klar* måste den ha en TPM-krets. TPM-kretsar krävs inte för att det ska gå att kryptera. (Mer information finns i *Krypteringsberedskap* i föregående avsnitt.)  

- **Krypteringsstatus** – avser huruvida OS-enheten är krypterad. Det kan ta upp till 24 timmar innan Intune rapporterar om enhetens krypteringsstatus eller en statusändring. Tiden omfattar tiden då operativsystemet ska krypteras plus den tid då enheten ska rapportera tillbaka till Intune.  

  Om du vill påskynda rapporteringen av FileVault-krypteringsstatus innan enhetsincheckningen normalt sker låter du användarna synkronisera sina enheter när krypteringen har slutförts.  

- **Profiler** – En lista över *enhetskonfigurationsprofilerna* som gäller för den här enheten och som är konfigurerade med följande värden:  

  - macOS:
    - Profiltyp = *Slutpunktsskydd*  
    - Inställningar > FileVault > FileVault = *Aktivera*

  - Windows 10:
    - Profiltyp = *Slutpunktsskydd*  
    - Inställningar > Windows-kryptering > Kryptera enheter = *Kräv*  

  Du kan använda listan över profiler för att identifiera enskilda principer för granskning om *Sammanfattning av profilstatus* indikerar problem.  

- **Sammanfattning av profiltillstånd** – en sammanfattning av de profiler som gäller för den här enheten. Sammanfattningen representerar det minst fördelaktiga tillståndet bland de tillämpliga profilerna. Om till exempel bara en av flera tillämpliga profiler resulterar i ett fel visar *Sammanfattning av profilstatus* *Fel*.  
  
  Om du vill se mer information för en status går du till **Intune** > **Enhetskonfiguration** > **Profiler** och väljer profilen. Du kan också välja **Enhetsstatus** och sedan välja en enhet.  

- **Statusinformation** – avancerad information om enhetens krypteringstillstånd.  

  > [!IMPORTANT]  
  > För Windows 10-enheter visar Intune endast *statusinformation* för enheter som kör *Windows-uppdateringen från 10 april 2019* eller senare.  
  
  Det här fältet visar information för varje tillämpligt fel som kan identifieras. Du kan använda den här informationen för att förstå varför en enhet kanske inte är redo för kryptering.  

  Följande är några exempel på den statusinformation som Intune kan rapportera:  
  
  **macOS**:
  - Återställningsnyckeln har inte hämtats och lagrats ännu. Förmodligen har enheten inte låsts upp, eller så har den inte checkat in.  
 
    *Tänk på att: Det här resultatet inte nödvändigtvis är ett feltillstånd, utan ett tillfälligt tillstånd som kan bero på en tidsinställning på enheten där återställningsnycklarnas deponering måste konfigureras innan krypteringsbegäran skickas till enheten. Denna status kan även indikera att enheten är låst eller inte har checkat in med Intune nyligen. Eftersom FileVault-kryptering inte startar förrän en enhet är ansluten (laddas) är det möjligt för en användare att ta emot en återställningsnyckel för en enhet som ännu inte har krypterats*.  

  - Användaren skjuter upp krypteringen eller håller för närvarande på med krypteringsprocessen.  
 
    *Tänk på att: Antingen har användaren inte loggat ut än efter att ha tagit emot krypteringsbegäran, vilket är nödvändigt innan FileVault kan kryptera enheten, eller så har användaren dekrypterat enheten manuellt. Intune kan inte hindra en användare från att dekryptera sin enhet.*  

  - Enheten är redan krypterad. Enhetsanvändaren måste dekryptera enheten för att kunna fortsätta.  
 
    *Tänk på att: Intune kan inte konfigurera FileVault på en enhet som redan är krypterad. I stället måste användaren dekryptera enheten manuellt innan den kan hanteras av en enhetskonfigurationsprincip och Intune*. 
 
  - FileVault kräver att användaren godkänner sin hanteringsprofil i MacOS Catalina och senare.  
 
    *Tänk på att: Från och med MacOS version 10.15 (Catalina) kan användargodkända registreringsinställningar resultera i kravet att användare godkänner FileVault-kryptering manuellt. Mer information finns i avsnittet [om användargodkänd registrering](../enrollment/macos-enroll.md) i Intune-dokumentationen*.  

  - Okänt.  

    *Tänk på att: En möjlig orsak till okänd status är att enheten är låst och att Intune inte kan starta depositions- eller krypteringsprocessen. När enheten har låsts upp kan förloppet fortsätta*.  

  **Windows 10**:  
  - BitLocker-principen kräver användarens medgivande för att starta guiden för BitLocker-diskkryptering för att starta kryptering av OS-volymen, men användare gav inte sitt medgivande.  
  
  - OS-volymens krypteringsmetod matchar inte BitLocker-principen.  
  
  - BitLocker-principen kräver ett TPM-skydd för att skydda OS-volymen, men TPM används inte.  
  
  - BitLocker-principen kräver ett skydd som endast använder TPM för OS-volymen, men TPM-skydd används inte.  
  
  - BitLocker-principen kräver skydd med TPM och PIN-kod för OS-volymen, men skydd med TPM och PIN-kod används inte.  
  
  - BitLocker-principen kräver skydd med TPM och startnyckel för OS-volymen, men skydd med TPM och startnyckel används inte.  
  
  - BitLocker-principen kräver skydd med TPM, PIN-kod och startnyckel för OS-volymen, men skydd med TPM, PIN-kod och startnyckel används inte.  
  
  - OS-volymen är inte skyddad.  
  
  - Säkerhetskopiering av återställningsnyckel misslyckades.  
  
  - En fast enhet är oskyddad.  
  
  - Den fasta enhetens krypteringsmetod matchar inte BitLocker-principen.  
  
  - För att kryptera enheter kräver BitLocker-principen antingen att användaren loggar in som administratör eller, om enheterna är ansluten till Azure AD, att principen AllowStandardUserEncryption anges till 1.  
  
  - Windows Recovery Environment (WinRE) är inte konfigurerat.  
  
  - Ingen TPM är tillgänglig för BitLocker, antingen eftersom den inte finns eller har gjorts otillgänglig i registret, eller på grund av att operativsystemet finns på en flyttbar enhet.  
  
  - TPM:en är inte redo för BitLocker.  
  
  - Nätverket är inte tillgängligt, vilket krävs för säkerhetskopiering av återställningsnyckel.  

## <a name="export-report-details"></a>Exportera rapportinformation 
När du visar fönstret Krypteringsrapport kan du välja **Exportera** för att ladda ned en *CSV*-fil med rapportinformation.  Den här rapporten innehåller översiktlig information från fönstret *Krypteringsrapport* och *Enhetens krypteringsstatus* för varje enhet som du hanterar.   
 
  
![Exportera information](./media/encryption-monitor/export.png) 
 
Den här rapporten kan användas för att identifiera problem för grupper av enheter. Du kan till exempel använda rapporten för att identifiera en lista med macOS-enheter som alla rapporterar *FileVault har redan aktiverats av användaren*, vilket indikerar enheter som måste dekrypteras manuellt innan Intune kan hantera deras FileVault-inställningar.  
 
## <a name="filevault-recovery-keys"></a>FileVault-återställningsnycklar   
När Intune först krypterar en macOS-enhet med FileVault skapas en personlig återställningsnyckel. Efter krypteringen visas den personliga nyckeln en enda gång för slutanvändaren.  
 
För hanterade enheter kan Intune deponera en kopia av den personliga återställningsnyckeln. Deponeringen av nycklar gör att Intune-administratörer kan rotera nycklar för att skydda enheter, och användare för att återställa en förlorad eller roterad personlig återställningsnyckel.  
 
Intune stöder flera alternativ för att rotera och återställa personliga återställningsnycklar. En nyckel kan exempelvis roteras om den nuvarande personliga nyckeln försvinner eller misstänks vara utsatt för risk.  
 
> [!IMPORTANT]  
>  Enheter som krypteras av användare, och inte av Intune, kan inte hanteras av Intune. Det innebär att Intune inte kan deponera den personliga återställningsnyckeln för dessa enheter, eller hantera rotationen av återställningsnyckeln.  Innan Intune kan hantera FileVault och återställningsnycklar för enheten måste användaren dekryptera enheten och sedan låta Intune kryptera enheten.  

### <a name="rotate-recovery-keys"></a>Rotera återställningsnycklar  

- **Automatisk rotation**: Som administratör kan du konfigurera FileVault-inställningen Rotering av privat återställningsnyckel för att automatiskt generera nya återställningsnycklar med jämna mellanrum.  När en ny nyckel skapas för en enhet visas inte nyckeln för användaren. Användaren måste i stället få nyckeln från en administratör eller via företagsportalappen.  

- **Manuell rotation**: Som administratör kan du visa information om en enhet som du hanterar med Intune och som krypteras med FileVault. Du kan sedan välja att manuellt rotera återställningsnyckeln för företagsenheter. Du kan inte rotera återställningsnycklar för personliga enheter.  

  Så här roterar du en återställningsnyckel: 
  1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), gå till  **Enheter**  och välj  **Alla enheter** under Hantera.  
  2. I listan med enheter väljer du den enhet som är krypterad och som du vill rotera nyckeln för. Välj  **Återställningsnycklar** under Övervaka.  
  3. Välj **Rotera FileVault-återställningsnyckel** i fönstret Återställningsnycklar.  
  
     Nästa gång enheten checkar in med Intune roteras den personliga nyckeln. Om det behövs kan den nya nyckeln hämtas av slutanvändaren via företagsportalen. 


### <a name="recover-recovery-keys"></a>Återställa återställningsnycklar  
- **Administratör**: Administratörer kan inte visa personliga återställningsnycklar för enheter som är krypterade med FileVault.  

- **Slutanvändare**: Slutanvändare använder webbplatsen för företagsportalen från valfri enhet för att visa den aktuella personliga återställningsnyckeln för någon av deras hanterade enheter. Du kan inte visa återställningsnycklar från appen Företagsportal.  

 
  Så här visar du en återställningsnyckel:  
  1. Logga in på webbplatsen för *Intune-företagsportalen* från valfri enhet.  
  2. På portalen går du till **Enheter** och väljer den macOS-enhet som är krypterad med FileVault.  
  3. Välj **Hämta återställningsnyckel**. Den aktuella återställningsnyckeln visas.  
 

## <a name="bitlocker-recovery-keys"></a>BitLocker-återställningsnycklar  

Intune ger åtkomst till Azure AD-bladet för BitLocker så att du kan visa BitLocker-nyckel-ID:n och återställningsnycklar för dina Windows 10-enheter från Intune-portalen.  För att enheten ska vara nåbar måste dess nycklar vara deponerade till Azure AD. 
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), gå till **Enheter** följt av *Hantera* och välj **Alla enheter**.  

2. Välj en enhet i listan. Under *Övervaka* väljer du sedan **Återställningsnycklar**.  
  
När nycklar är tillgängliga i Azure AD finns följande information tillgänglig:
- BitLocker-nyckel-ID  
- BitLocker-återställningsnyckel  
- Enhetstyp  

När nycklar inte finns i Azure AD visar Intune *Det gick inte att hitta någon BitLocker-nyckel för den här enheten*.  

Information för BitLocker hämtas med hjälp av den [BitLocker-CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp). BitLocker-CSP stöds på Windows 10 version 1703 och senare samt för Windows 10 Pro version 1809 och senare.  

## <a name="next-steps"></a>Nästa steg  

Skapa en princip för [enhetsefterlevnad](compliance-policy-create-windows.md).
