---
title: Lägga till PowerShell-skript i Microsoft Intune för Windows 10-enheter – Azure | Microsoft Docs
description: Lägg till PowerShell-skript, tilldela skriptprincipen till Azure Active Directory-grupper, övervaka skripten med hjälp av rapporter och följ stegvisa anvisningar för att ta bort skript som du lägger till för Windows 10-enheter i Microsoft Intune. Se även vissa vanliga problem och lösningar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 063a5cbbe18efc5c406c9dc7f2fa40d614b2e48a
ms.sourcegitcommit: d3b1e3fffd3e0229292768c7ef634be71e4736ae
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/04/2018
ms.locfileid: "52860970"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Hantera PowerShell-skript i Intune för Windows 10-enheter

Använd Intunes hanteringstillägg till att ladda upp PowerShell-skript i Intune för att köra på Windows 10-enheter. Hanteringstillägget förbättrar hanteringen av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att övergå till modern hantering.

## <a name="moving-to-modern-management"></a>Flytta till modern hantering

Slutanvändarens databehandling genomgår en digital transformation. Klassisk, traditionell IT fokuserar på en enskild enhetsplattform, företagsägda enheter, användare som arbetar från kontoret och en mängd manuella, reaktiva IT-processer. En modern arbetsplats använder många plattformar som både är användarägda och företagsägda, vilket innebär att användarna kan arbeta från valfri plats och har åtkomst till automatiska och proaktiva IT-processer.

MDM-tjänster (exempelvis Microsoft Intune) kan hantera mobila och stationära enheter som kör Windows 10. Den inbyggda Windows 10-hanteringsklienten kommunicerar med Intune när hanteringsuppgifter för företag utförs. Vissa uppgifter som du kan behöva är dock för närvarande inte är tillgängliga i Windows 10 MDM, till exempel avancerad enhetskonfiguration, felsökning och äldre Win32-apphantering. För de här funktionerna kan du köra Intunes programvaruklient på dina Windows 10-enheter. Att kunna [jämföra hanteringen av Windows-datorer som datorer respektive mobila enheter](pc-management-comparison.md) är mycket användbart.

Tillägget för Intune-hantering kompletterar de inbyggda funktionerna i Windows 10 MDM. Du kan skapa PowerShell-skript som körs på Windows 10-enheter. Du kan till exempel skapa ett PowerShell-skript som installerar en äldre Win32-app, laddar upp skriptet till Intune, tilldelar det till en grupp i Azure Active Directory (AD) och sedan kör skriptet. Du kan sedan övervaka körstatusen för skriptet från början till slut.

## <a name="prerequisites"></a>Krav

Intune-hanteringstillägget har följande krav:

- Enheter måste vara anslutna till Azure AD och [automatiskt registrerade](windows-enroll.md#enable-windows-10-automatic-enrollment). Intune-hanteringstillägget har stöd för Azure AD-anslutna, hybriddomänanslutna och samhanterade registrerade Windows-enheter. GPO-registrerade enheter stöds inte.
- Enheterna måste köra Windows 10 version 1607 eller senare.
- Intune-hanteringstilläggsagenten installeras när ett PowerShell-skript eller en Win32-app distribueras till en användare eller en enhetssäkerhetsgrupp.

## <a name="create-a-powershell-script-policy"></a>Skapa en princip för PowerShell-skript 

1. I [Azure Portal](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **PowerShell-skript** > **Lägg till**.
3. Ange ett **namn** och en **beskrivning** för PowerShell-skriptet. Navigera till PowerShell-skriptet för att ange **platsen för skriptet**. Skriptet måste vara mindre än 200 KB (ASCII) eller 100 KB (Unicode).
4. Välj **Konfigurera**. Välj sedan att köra skriptet med användarens autentiseringsuppgifter på enheten (**Ja**), eller i systemkontexten (**Nej**). Som standard körs skriptet i systemkontexten. Välj **Ja** om inte skriptet kräver att det körs i systemkontexten. 
  ![Fönstret Lägg till PowerShell-skript](./media/mgmt-extension-add-script.png)
5. Välj om skriptet måste signeras av en betrodd utgivare (**Ja**). Som standard finns inga krav på att skriptet ska signeras. 
6. Välj **OK** och sedan **Skapa** för att spara skriptet.

## <a name="assign-a-powershell-script-policy"></a>Tilldela en princip för PowerShell-skript

1. Välj det skript som du vill tilldela i fönstret **PowerShell-skript** och välj sedan **Hantera** > **Tilldelningar**.

    ![Lägg till ett PowerShell-skriptfönster](./media/mgmt-extension-assignments.png)

2. Välj **Välj grupper** för en lista över tillgängliga Azure AD-grupper. 
3. Välj en eller flera grupper som innehåller de användare vars enheter skriptet ska köras på. **Välj** att tilldela principen till de valda grupperna.

> [!NOTE]
> - PowerShell-skript kan inte tillämpas på datorgrupper.
> - Slutanvändarna behöver inte vara inloggade på enheten för att köra PowerShell-skript.
> - PowerShell-skript i Intune kan riktas mot säkerhetsgrupper för Azure AD-enheter.

Intune-hanteringstilläggsklienten kontrollerar Intune en gång i timmen. När du tilldelar principen till Azure AD-grupper körs PowerShell-skriptet och körningsresultaten rapporteras.

## <a name="monitor-run-status-for-powershell-scripts"></a>Övervaka körningsstatus för PowerShell-skript

Du kan övervaka körningsstatusen för PowerShell-skript för användare och enheter i Azure Portal.

Välj det skript som du vill övervaka i fönstret **PowerShell-skript**, välj **Övervaka** och välj sedan någon av följande rapporter:

- **Enhetstillstånd**
- **Användarstatus**

## <a name="troubleshoot-powershell-scripts"></a>Felsöka PowerShell-skript

Agentloggar på klientdatorn finns vanligtvis i `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Du kan använda [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) för att visa dessa loggfiler. 

![Skärmbild av agentloggar](./media/apps-win32-app-10.png)  

## <a name="delete-a-powershell-script"></a>Ta bort ett PowerShell-skript

Högerklicka på skriptet i fönstret **PowerShell-skript** och välj **Ta bort**.

## <a name="common-issues-and-resolutions"></a>Vanliga problem och lösningar

PowerShell-skripten körs inte vid varje inloggning. De körs bara efter omstarter, eller om tjänsten **Microsoft Intune-hanteringstillägg** startas om. Intune-hanteringstilläggsklienten kontrollerar en gång i timmen om det finns några ändringar i skriptet eller principen i Intune.

#### <a name="issue-intune-management-extension-doesnt-download"></a>Problem: Intune-hanteringstillägget laddas inte ned

**Möjliga lösningar**:

- Kontrollera att enheterna är automatiskt registrerade i Azure AD. Gör detta genom att på enheten: 

  1. Gå till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**.
  2. Välj det anslutna kontot > **Information**.
  3. Under **Avancerad diagnostikrapport** väljer du **Skapa rapport**.
  4. Öppna `MDMDiagReport` i en webbläsare och gå till avsnittet **Registrerade konfigurationskällor**.
  5. Leta efter egenskapen **MDMDeviceWithAAD**. Om egenskapen inte finns är enheten inte automatiskt registrerad.

    Det finns anvisningar i [Aktivera automatisk registrering i Windows 10](windows-enroll.md#enable-windows-10-automatic-enrollment).

#### <a name="issue-the-powershell-scripts-do-not-run"></a>Problem: PowerShell-skripten körs inte

**Möjliga lösningar**:

- Kontrollera att Intune-hanteringstillägget har laddats ned till `%ProgramFiles(x86)%\Microsoft Intune Management Extension`.
- Det körs inte några skript på Surface Hub.
- Kontrollera loggarna i `\ProgramData\Microsoft\IntuneManagementExtension\Logs` för eventuella fel.
- Vid eventuella behörighetsproblem kontrollerar du att egenskaperna för PowerShell-skriptet är inställda på `Run this script using the logged on credentials`. Kontrollera också att den inloggade användaren har lämplig behörighet att köra skriptet.
- Kör ett exempelskript för att isolera skriptproblem. Skapa t.ex. katalogen `C:\Scripts` och ge alla fullständig behörighet. Kör följande skript:

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  Om det lyckas ska output.txt skapas och bör inkludera texten ”Skriptet fungerade”.

- Testa skriptkörningen utan Intune genom att köra skripten under systemkontexten med hjälp av [psexec-verktyget](https://docs.microsoft.com/sysinternals/downloads/psexec) lokalt:

  `psexec -i -s`

## <a name="next-steps"></a>Nästa steg

[Övervaka](device-profile-monitor.md) och [felsöka](device-profile-troubleshoot.md) profiler.
