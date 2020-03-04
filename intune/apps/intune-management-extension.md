---
title: Lägga till PowerShell-skript till Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa och kör PowerShell-skript, tilldela skriptprincipen till Azure Active Directory-grupper, övervaka skripten med hjälp av rapporter och följ stegvisa anvisningar för att ta bort skript som du lägger till för Windows 10-enheter i Microsoft Intune. Se även vissa vanliga problem och lösningar.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8af7a756d95051be52a5380467cb4f9be2533b3
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216204"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Använda PowerShell-skript på Windows 10-enheter i Intune

Använd Microsoft Intune-hanteringstillägget för att ladda upp PowerShell-skript i Intune till att köras på Windows 10-enheter. Hanteringstillägget förbättrar hanteringen av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att övergå till modern hantering.

Den här funktionen gäller för:

- Windows 10 och senare

## <a name="move-to-modern-management"></a>Övergå till modern hantering

Slutanvändarens databehandling genomgår en digital transformation. Klassisk, traditionell IT fokuserar på en enskild enhetsplattform, företagsägda enheter, användare som arbetar från kontoret och olika manuella, reaktiva IT-processer. En modern arbetsplats använder många plattformar som både är användarägda och företagsägda, vilket innebär att användarna kan arbeta från valfri plats och har åtkomst till automatiska och proaktiva IT-processer.

MDM-tjänster (exempelvis Microsoft Intune) kan hantera mobila och stationära enheter som kör Windows 10. Den inbyggda Windows 10-hanteringsklienten kommunicerar med Intune när hanteringsuppgifter för företag utförs. Det finns några uppgifter som du kan behöva göra, till exempel avancerad enhetskonfiguration och felsökning. Vid Win32-apphantering kan du använda funktionen [Win32-apphantering](app-management.md) på dina Windows 10-enheter.

Tillägget för Intune-hantering kompletterar de inbyggda funktionerna i Windows 10 MDM. Du kan skapa PowerShell-skript som körs på Windows 10-enheter. Du kan till exempel skapa ett PowerShell-skript som skapar avancerade enhetskonfigurationer. Sedan laddar du upp skriptet till Intune, tilldelar skriptet till en AD-grupp (Azure Active Directory) och kör skriptet. Du kan sedan övervaka körstatusen för skriptet från början till slut.

## <a name="prerequisites"></a>Krav

Intune-hanteringstillägget har följande krav. När förhandskraven är uppfyllda installeras Intune-hanteringstillägget automatiskt när ett PowerShell-skript eller en Win32-app tilldelas till användaren eller enheten.

- Enheter som kör Windows 10 version 1607 eller senare. Om enheten registrerats med hjälp av [automatisk massregistrering](../enrollment/windows-bulk-enroll.md) måste enheter köra Windows 10 version 1703 eller senare. Intune-hanteringstillägget stöds inte på Windows 10 i S-läge, eftersom S-läge inte tillåter körning av andra appar än Store-appar. 
  
- Enheter som anslutits till Azure Active Directory (AD), inklusive:  
  
  - Azure AD-anslutna hybridenheter: Enheter som anslutits till Azure Active Directory (AD), och även anslutits till lokal Active Directory (AD). Mer information finns i [Planera implementeringen av din Azure Active Directory-hybridanslutning](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan).

- Enheter som registrerats i Intune, inklusive:

  - Enheter som registrerats i en grupprincip (GPO). Mer information finns i [Registrera en Windows 10-enhet automatiskt med hjälp av en grupprincip](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy).
  
  - Enheter som registrerats manuellt i Intune, enligt följande:
  
    - [Automatisk registrering i Intune](../enrollment/quickstart-setup-auto-enrollment.md) aktiveras i Microsoft Azure AD. Slutanvändaren loggar in på enheten med ett lokalt användarkonto, ansluter enheten till Microsoft Azure AD manuellt och loggar sedan in på enheten med sitt Microsoft Azure AD-konto.
    
    ELLER  
    
    - Användaren loggar in på enheten med sitt Azure AD-konto, och registrerar sedan i Intune.

  - Samhanterade enheter som använder Configuration Manager och Intune. Kontrollera att arbetsbelastningen för **Appar** är inställd på **Pilot Intune** eller **Intune**. Se följande artiklar för vägledning: 
  
    - [Vad är samhantering?](https://docs.microsoft.com/configmgr/comanage/overview) 
    - [Arbetsbelastning för klientappar](https://docs.microsoft.com/configmgr/comanage/workloads#client-apps)
    - [Så här växlar du Configuration Manager-arbetsbelastningar till Intune](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads)
  
> [!TIP]
> Se till att enheterna är [anslutna](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) till Microsoft Azure AD. Enheter som endast är [registrerade](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) i Microsoft Azure AD kommer inte att ta emot skripten.

## <a name="create-a-script-policy-and-assign-it"></a>Skapa en skriptprincip och tilldela den

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **PowerShell-skript** > **Lägg till**.

    ![Lägga till och använda PowerShell-skript i Microsoft Intune](./media/intune-management-extension/mgmt-extension-add-script.png)

3. I **Grundläggande** anger du följande egenskaper och väljer sedan **Nästa**:
    - **Namn**: Ange ett namn på PowerShell-skriptet. 
    - **Beskrivning**: Ange en beskrivning för PowerShell-skriptet. Denna inställning är valfri, men rekommenderas.
4. I **Skriptinställningar** anger du följande egenskaper och väljer **Nästa**:
    - **Skriptplats**: Bläddra till PowerShell-skriptet. Skriptet måste vara mindre än 200 KB (ASCII).
    - **Kör det här skriptet med inloggade autentiseringsuppgifter**: Välj **Ja** för att köra skriptet med användarens autentiseringsuppgifter på enheten. Välj **Nej** (standard) om du vill köra skriptet i systemkontexten. Många administratörer väljer **Ja**. Om skriptet måste köras i systemkontexten väljer du **Nej**.
    - **Framtvinga signaturkontroll av skript**: Välj **Ja** om skriptet måste signeras av en betrodd utgivare. Välj **Nej** (standard) om det inte finns något krav på att skriptet signeras. 
    - **Köra skript i 64-bitars PowerShell-värd**: Välj **Ja** för att köra skriptet i en 64-bitars PowerShell-värd (PS) på en 64-bitars klientarkitektur. Om du väljer **Nej** (standard) körs skriptet i en 32-bitars PowerShell-värd.

      När du anger **Ja** eller **Nej** använder du följande tabell för nytt och befintligt principbeteende:

      | Kör skript i 64-bitars PS-värd | Klientarkitektur | Nytt PS-skript | PS-skript för befintlig princip |
      | --- | --- | --- | --- | 
      | Nej | 32-bitars  | 32-bitars PS-värd stöds | Körs bara i 32-bitars PS-värd, vilket fungerar i 32-bitars och 64-bitars arkitekturer. |
      | Ja | 64-bitars | Kör skript i 64-bitars PS-värd för 64-bitars arkitekturer. Vid körning i 32-bitar körs skriptet i en 32-bitars PS-värd. | Kör skript i 32-bitars PS-värd. Om den här inställningen ändras till 64-bitars öppnas skriptet (det körs inte) i en 64-bitars PS-värd och rapporterar resultatet. Vid körning i 32-bitars körs skriptet i 32-bitars PS-värd. |

5. Välj **Omfångstaggar**. Omfångstaggar är valfria. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](../fundamentals/scope-tags.md).

    Så här lägger du till en omfångstagg:

    1. Välj **Välj omfångstaggar** > välj en befintlig omfångstagg i listan > **Välj**.

    2. När du är klar väljer du **Nästa**.

6. Välj **Tilldelningar** > **Välj grupper att ta med**. En befintlig lista över Azure AD-grupper visas.

    1. Välj en eller flera grupper som innehåller de användare vars enheter skriptet ska köras på. Välj **Välj**. De grupper du väljer visas i listan och kommer att tilldelas din princip.

        > [!NOTE]
        > PowerShell-skript i Intune kan riktas mot säkerhetsgrupper för Azure AD-enheter eller säkerhetsgrupper för Azure AD-användare.

    2. Välj **Nästa**.

        ![Tilldela eller distribuera PowerShell-skript till enhetsgrupper i Microsoft Intune](./media/intune-management-extension/mgmt-extension-assignments.png)

7. I **Granska + lägg till** visas en sammanfattning av de inställningar som du har konfigurerat. Välj **Lägg till** för att spara skriptet. När du väljer **Lägg till** distribueras principen till de grupper som du har valt.

## <a name="important-considerations"></a>Viktiga överväganden

- När skript är inställda på användarkontext och slutanvändaren har administratörsbehörighet, körs PowerShell-skriptet som standard under administratörsbehörigheten.

- Slutanvändarna behöver inte vara inloggade på enheten för att köra PowerShell-skript.

- Klienten för Intune-hanteringstillägg kontrollerar varje timme, och efter varje omstart, om det finns nya skript eller ändringar. När du tilldelar principen till Azure AD-grupper körs PowerShell-skriptet och körningsresultaten rapporteras. När skriptet körs så körs det inte igen såvida det inte finns en ändring i skriptet eller principen.

## <a name="monitor-run-status"></a>Övervaka körningsstatus

Du kan övervaka körningsstatusen för PowerShell-skript för användare och enheter i Azure Portal.

Välj det skript som du vill övervaka i fönstret **PowerShell-skript**, välj **Övervaka** och välj sedan någon av följande rapporter:

- **Enhetstillstånd**
- **Användarstatus**

## <a name="intune-management-extension-logs"></a>Loggar för Intune-hanteringstillägg

Agentloggar på klientdatorn finns vanligtvis i `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Du kan använda [CMTrace.exe](https://docs.microsoft.com/configmgr/core/support/cmtrace) för att visa dessa loggfiler.

![Skärmbild eller exempel på cmtrace-agentloggar i Microsoft Intune](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Ta bort ett skript

Högerklicka på skriptet i fönstret **PowerShell-skript** och välj **Ta bort**.

## <a name="common-issues-and-resolutions"></a>Vanliga problem och lösningar

### <a name="issue-intune-management-extension-doesnt-download"></a>Problem: Intune-hanteringstillägget laddas inte ned

**Möjliga lösningar**:

- Enheten är inte ansluten till Azure AD. Kontrollera att enheterna uppfyller [kraven](#prerequisites) (i den här artikeln). 
- Inga PowerShell-skript eller Win32-appar har tilldelats till de grupper som användaren eller enheten tillhör.
- Enheten kan inte checka in i Intune-tjänsten, på grund av ingen Internetåtkomst, ingen åtkomst till WNS (Windows Push Notification Service) och så vidare.
- Enheten är i S-läge. Intune-hanteringstillägget stöds inte på enheter som körs i S-läge. 

Om du vill se om enheten är automatiskt registrerad kan du:

  1. Gå till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**.
  2. Välj det anslutna kontot > **Information**.
  3. Under **Avancerad diagnostikrapport** väljer du **Skapa rapport**.
  4. Öppna `MDMDiagReport` i en webbläsare.
  5. Sök efter egenskapen **MDMDeviceWithAAD**. Om egenskapen finns är enheten automatiskt registrerad. Om egenskapen inte finns är enheten inte automatiskt registrerad.

[Aktivera automatisk registrering i Windows 10](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) innehåller anvisningar för att konfigurera automatisk registrering i Intune.

### <a name="issue-powershell-scripts-do-not-run"></a>Problem: PowerShell-skript körs inte

**Möjliga lösningar**:

- PowerShell-skripten körs inte vid varje inloggning. De körs:

  - När skriptet tilldelas till en enhet
  - Om du ändrar skriptet, laddar upp det och tilldelar skriptet till en användare eller enhet
  
    > [!TIP]
    > **Microsoft Intune-hanteringstillägget** är en tjänst som körs på enheten, precis som andra tjänster som visas i appen Tjänster (services.msc). När en enhet startas om kan den här tjänsten också startas om och söka efter tilldelade PowerShell-skript med Intune-tjänsten. Om tjänsten för **Microsoft Intune-hanteringstillägget** är inställd på Manuellt kanske inte tjänsten startas om när enheten startas om.

- Se till att enheterna är [anslutna](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) till Microsoft Azure AD. Enheter som endast är anslutna till din arbetsplats eller organisation ([registrerade](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network) i Microsoft Azure AD) tar inte emot skripten.
- Intune-hanteringstilläggsklienten kontrollerar en gång i timmen om det finns några ändringar i skriptet eller principen i Intune.
- Kontrollera att Intune-hanteringstillägget har laddats ned till `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Skript körs inte på Surface Hub-enheter eller Windows 10 i S-läge.
- Granska loggarna för eventuella fel. Mer information finns i [Loggar för Intune-hanteringstillägg](#intune-management-extension-logs) (i den här artikeln).
- Vid eventuella behörighetsproblem kontrollerar du att egenskaperna för PowerShell-skriptet är inställda på `Run this script using the logged on credentials`. Kontrollera också att den inloggade användaren har lämplig behörighet att köra skriptet.

- Om du vill isolera skriptproblem kan du göra följande:

  - Granska PowerShell-körningskonfigurationen på dina enheter. Mer information finns i [PowerShell-körningsprincip](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6).
  - Kör ett exempelskript med hjälp av Intune-hanteringstillägget. Skapa t.ex. katalogen `C:\Scripts` och ge alla fullständig behörighet. Kör följande skript:

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    Om det lyckas ska output.txt skapas och bör inkludera texten ”Skriptet fungerade”.

  - Testa skriptkörningen utan Intune genom att köra skripten på systemkontot med hjälp av [psexec-verktyget](https://docs.microsoft.com/sysinternals/downloads/psexec) lokalt:

    `psexec -i -s`  
    
  - Om skriptet rapporterar att det har utförts, men det egentligen har misslyckats, är det möjligt att din antivirustjänst har AgentExecutor i begränsat läge. Följande skript rapporterar alltid ett fel i Intune. Som ett test kan du använda det här skriptet:
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    Om skriptet rapporterar att det har utförts tittar du i `AgentExecutor.log` för att bekräfta felresultatet. Om skriptet körs ska längden vara >2.

  - För att registrera .error- och .output-filerna kör följande kodavsnitt skriptet via AgentExecutor till PSx86 (`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`). Här sparas loggarna som du kan granska. Kom ihåg att Intune-hanteringstilläget rensar loggarna när skriptet har körts:
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>Nästa steg

[Övervaka](../device-profile-monitor.md) och [felsöka](../device-profile-troubleshoot.md) profiler.
