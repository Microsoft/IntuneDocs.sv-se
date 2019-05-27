---
title: Lägga till PowerShell-skript till Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa och kör PowerShell-skript, tilldela skriptprincipen till Azure Active Directory-grupper, övervaka skripten med hjälp av rapporter och följ stegvisa anvisningar för att ta bort skript som du lägger till för Windows 10-enheter i Microsoft Intune. Se även vissa vanliga problem och lösningar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7ea047daca5dad327b431986840a59074614d1
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732638"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Använda PowerShell-skript på Windows 10-enheter i Intune

Använd Microsoft Intune-hanteringstillägget för att ladda upp PowerShell-skript i Intune till att köras på Windows 10-enheter. Hanteringstillägget förbättrar hanteringen av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att övergå till modern hantering.

Den här funktionen gäller för:

- Windows 10 och senare

## <a name="move-to-modern-management"></a>Övergå till modern hantering

Slutanvändarens databehandling genomgår en digital transformation. Klassisk, traditionell IT fokuserar på en enskild enhetsplattform, företagsägda enheter, användare som arbetar från kontoret och olika manuella, reaktiva IT-processer. En modern arbetsplats använder många plattformar som både är användarägda och företagsägda, vilket innebär att användarna kan arbeta från valfri plats och har åtkomst till automatiska och proaktiva IT-processer.

MDM-tjänster (exempelvis Microsoft Intune) kan hantera mobila och stationära enheter som kör Windows 10. Den inbyggda Windows 10-hanteringsklienten kommunicerar med Intune när hanteringsuppgifter för företag utförs. Det finns några uppgifter som du kan behöva göra, till exempel avancerad enhetskonfiguration och felsökning. Vid Win32-apphantering kan du använda funktionen [Win32-apphantering](apps-win32-app-management.md) på dina Windows 10-enheter.

Tillägget för Intune-hantering kompletterar de inbyggda funktionerna i Windows 10 MDM. Du kan skapa PowerShell-skript som körs på Windows 10-enheter. Du kan till exempel skapa ett PowerShell-skript som utför avancerade enhetskonfigurationer, laddar upp skriptet till Intune, tilldelar det till en grupp i Azure Active Directory (AD) och sedan kör skriptet. Du kan sedan övervaka körstatusen för skriptet från början till slut.

## <a name="prerequisites"></a>Krav

Intune-hanteringstillägget har följande krav:

- Enheter måste anslutas till eller registreras i Azure AD och Azure AD samt Intune konfigureras för [automatisk registrering](quickstart-setup-auto-enrollment.md). Intune-hanteringstillägget har stöd för Azure AD-anslutna, Azure AD-hybriddomänanslutna och samhanterade registrerade Windows-enheter.
- Enheterna måste köra Windows 10 version 1607 eller senare.
- Intune-hanteringstilläggsagenten installeras när ett PowerShell-skript eller en Win32-app distribueras till en användare eller en enhetssäkerhetsgrupp.

## <a name="create-a-script-policy"></a>Skapa en skriptprincip 

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **PowerShell-skript** > **Lägg till**.
3. Ange följande egenskaper:
    - **Namn**: Ange ett namn på PowerShell-skriptet. 
    - **Beskrivning**: Ange en beskrivning för PowerShell-skriptet. Denna inställning är valfri, men rekommenderas. 
    - **Skriptplats**: Bläddra till PowerShell-skriptet. Skriptet måste vara mindre än 200 KB (ASCII).
4. Välj **Konfigurera** och ange följande egenskaper:
    - **Kör det här skriptet med inloggade autentiseringsuppgifter**: Välj **Ja** för att köra skriptet med användarens autentiseringsuppgifter på enheten. Välj **Nej** (standard) om du vill köra skriptet i systemkontexten. Många administratörer väljer **Ja**. Om skriptet måste köras i systemkontexten väljer du **Nej**.
    - **Framtvinga signaturkontroll av skript**: Välj **Ja** om skriptet måste signeras av en betrodd utgivare. Välj **Nej** (standard) om det inte finns något krav på att skriptet signeras. 
    - **Köra skript i 64-bitars PowerShell-värd**: Välj **Ja** för att köra skriptet i en 64-bitars PowerShell-värd (PS) på en 64-bitars klientarkitektur. Om du väljer **Nej** (standard) körs skriptet i en 32-bitars PowerShell-värd.

      När du anger **Ja** eller **Nej** använder du följande tabell för nytt och befintligt principbeteende:

      | Kör skript i 64-bitars PS-värd | Klientarkitektur | Nytt PS-skript | PS-skript för befintlig princip |
      | --- | --- | --- | --- | 
      | Nej | 32-bitars  | 32-bitars PS-värd stöds | Körs bara i 32-bitars PS-värd, vilket fungerar i 32-bitars och 64-bitars arkitekturer. |
      | Ja | 64-bitars | Kör skript i 64-bitars PS-värd för 64-bitars arkitekturer. Vid körning i 32-bitar körs skriptet i en 32-bitars PS-värd. | Kör skript i 32-bitars PS-värd. Om den här inställningen ändras till 64-bitars öppnas skriptet (det körs inte) i en 64-bitars PS-värd och rapporterar resultatet. Vid körning i 32-bitars körs skriptet i 32-bitars PS-värd. |

    ![Lägga till och använda PowerShell-skript i Microsoft Intune](./media/mgmt-extension-add-script.png)
5. Välj **OK** > **Skapa** för att spara skriptet.

> [!NOTE]
> PowerShell-skriptet körs under administratörsbehörighet (som standard) när skriptet har angetts ställts in på användarkontext och slutanvändaren på enheten har administratörsbehörighet.

## <a name="assign-the-policy"></a>Tilldela principen

1. Välj det skript som du vill tilldela i fönstret **PowerShell-skript** och välj sedan **Hantera** > **Tilldelningar**.

    ![Tilldela eller distribuera PowerShell-skript till enhetsgrupper i Microsoft Intune](./media/mgmt-extension-assignments.png)

2. Välj **Välj grupper** för en lista över tillgängliga Azure AD-grupper. 
3. Välj en eller flera grupper som innehåller de användare vars enheter skriptet ska köras på. **Välj** att tilldela principen till de valda grupperna.

> [!NOTE]
> - Slutanvändarna behöver inte vara inloggade på enheten för att köra PowerShell-skript.
> - PowerShell-skript i Intune kan riktas mot säkerhetsgrupper för Azure AD-enheter.
> - PowerShell-skript i Intune kan riktas mot säkerhetsgrupper för Azure AD-användare.

Klienten för Intune-hanteringstillägg kontrollerar varje timme och efter varje omstart med Intune om det finns nya skript eller ändringar. När du tilldelar principen till Azure AD-grupper körs PowerShell-skriptet och körningsresultaten rapporteras. När skriptet körs så körs det inte igen såvida det inte finns en ändring i skriptet eller principen.

## <a name="monitor-run-status"></a>Övervaka körningsstatus

Du kan övervaka körningsstatusen för PowerShell-skript för användare och enheter i Azure Portal.

Välj det skript som du vill övervaka i fönstret **PowerShell-skript**, välj **Övervaka** och välj sedan någon av följande rapporter:

- **Enhetstillstånd**
- **Användarstatus**

## <a name="troubleshoot-scripts"></a>Felsöka skript

Agentloggar på klientdatorn finns vanligtvis i `\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Du kan använda [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools) för att visa dessa loggfiler. 

![Skärmbild eller exempel på cmtrace-agentloggar i Microsoft Intune](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>Ta bort ett skript

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

#### <a name="issue-powershell-scripts-do-not-run"></a>Problem: PowerShell-skript körs inte

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
