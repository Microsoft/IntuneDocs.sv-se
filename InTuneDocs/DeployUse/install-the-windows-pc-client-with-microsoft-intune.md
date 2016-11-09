---

title: Installera datorklientprogrammet | Microsoft Intune
description: "Använd den här guiden för att låta dina Windows-datorer hanteras av Microsoft Intune-klientprogrammet."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eba2421fb929d21eb36c273eb6cb43a06ac03cb4
ms.openlocfilehash: ed92874cce2877d31d83a619ec8ffb63a57cd5c3


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installera Intune-klientprogrammet på Windows-datorer
Windows-datorer kan registreras genom att installera Intune-klientprogrammet. Intune-klientprogrammet kan installeras på följande sätt:

- Manuell installation
- Installation med hjälp av en grupprincip
- Inkluderad i en diskavbildning
- Installation av användare

Klienten för Intune-programvara som hämtas först innehåller lägsta nödvändiga programvara för att registrera datorn i Intune-hanteringen. När en dator har registrerats hämtar sedan Intune-programvaruklienten den fullständiga klientprogramvaran som behövs för datorhantering.

Den här serien med hämtningar minimerar den tid som krävs för att börja registrera datorn i Intune. Det garanterar även att klienten har den senaste tillgängliga programvaran efter att den andra hämtningen har slutförts.

## <a name="download-the-intune-client-software"></a>Hämta Intune-klientprogramvaran

Alla metoder, förutom då användarna själva installerar Intune-klientprogramvaran, kräver att du hämtar programvaran så att du kan distribuera den.

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) klickar du på **Administratör** &gt; **Hämtning av klientprogramvara**.

  ![Hämta Intune PC-klienten](../media/pc-sa-client-download.png)

2.  På fliken **Hämtning av klientprogram** klickar du på **Hämta klientprogram**. Spara sedan paketet **Microsoft_Intune_Setup.zip** som innehåller programvaran på en säker plats i nätverket.

    > [!NOTE]
    > Installationspaketet för Intune-klientprogramvaran innehåller information om ditt konto. Om obehöriga användare får tillgång till installationspaketet, kan de registrera datorer till kontot som representeras av dess inbäddade certifikat och kan då få tillgång till företagsresurser.

3.  Extrahera innehållet i installationspaket till en säker plats i nätverket.

    > [!IMPORTANT]
    > Byt inte namn eller ta inte bort filen **ACCOUNTCERT** som extraheras. Om du gör det, kommer installationen av klientprogramvaran att misslyckas.

## <a name="deploy-the-client-software-manually"></a>Distribuera klientprogramvaran manuellt

Gå till den mapp på en dator där installationsfilerna för klientprogramvaran finns. Kör sedan **Microsoft_Intune_Setup.exe** för att installera klientprogramvaran.

    > [!NOTE]
    > The status of the installation is displayed when you hover over the icon in the taskbar on the client computer.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Distribuera klientprogramvaran automatiskt med hjälp av en grupprincip

1.  I mappen som innehåller filerna **Microsoft_Intune_Setup.exe** och **MicrosoftIntune.accountcert** kör du följande kommando för att extrahera Windows Installer-baserade installationsprogram för 32-bitars och 64-bitars datorer:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Kopiera filerna **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** och **MicrosoftIntune.accountcert** till en nätverksplats som kan användas av alla datorer som klientprogramvaran ska installeras på.

    > [!IMPORTANT]
    > Dela inte upp och byt inte namn på filerna. Om du gör det, kommer installationen av klientprogramvaran att misslyckas.

3.  Använd grupprinciper för att distribuera programvaran till datorer i nätverket.

    Mer information om hur du använder grupprinciper för att automatiskt distribuera programvara finns i dokumentationen för Windows Server.

## <a name="deploy-the-client-software-as-part-of-an-image"></a>Distribuera klientprogramvaran som en del av en avbildning
Du kan distribuera Intune-klientprogramvaran till datorer som en del av en operativsystemsavbildning med hjälp av följande procedur som vägledning:

1.  Kopiera klientinstallationsfilerna **Microsoft_Intune_Setup.exe** och **MicrosoftIntune.accountcert** till mappen **%Systemdrive%\Temp\Microsoft_Intune_Setup** på referensdatorn.

2.  Skapa registerposten **WindowsIntuneEnrollPending** genom att lägga till följande kommando i skriptet **SetupComplete.cmd** :

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  Lägg till följande kommando i **setupcomplete.cmd** för att köra registreringspaketet med kommandoradsargumentet /PrepareEnroll:

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > Skriptet **SetupComplete.cmd** gör det möjligt för installationsprogrammet för Windows att göra ändringar i systemet innan en användare loggar in. Kommandoradsargumentet **/PrepareEnroll** förbereder en måldator för att registreras automatiskt i Intune efter att installationsprogrammet för Windows slutförts.

4.  Lägg **SetupComplete.cmd** i mappen **%Windir%\Setup\Scripts** på referensdatorn.

5.  Avbilda referensdatorn och distribuera avbildningen till måldatorerna.

När måldatorn startar efter att installationsprogrammet för Windows slutförts, skapas registernyckeln **WindowsIntuneEnrollPending** . Registreringspaketet kontrollerar om datorn har registrerats. Om datorn har registrerats, vidtas inga ytterligare åtgärder. Om datorn inte har registrerats, skapar registreringspaketet en automatisk registreringsuppgift för Microsoft Intune.

När den automatiska registreringsuppgiften körs vid nästa schemalagda tidpunkt, kontrolleras förekomsten av registervärdet **WindowsIntuneEnrollPending** och ett försök görs för att registrera måldatorn i Intune. Om registreringen misslyckas av någon anledning försöks registreringsprocessen nästa gång uppgiften körs. Återförsöken fortsätter under en månad.

Den automatiska registreringsuppgiften för Intune, registervärdet **WindowsIntuneEnrollPending** och kontocertifikatet tas bort från måldatorn antingen när registreringen lyckas eller efter en månad (beroende på vad som kommer först).

## <a name="instruct-users-to-selfenroll"></a>Be användarna att göra registreringen själv

Användare kan installera Intune-klientprogramvaran genom att gå till  [företagsportalens webbplats](http://portal..manage.microsoft.com). Om webbportalen kan identifiera enheten som en Windows-dator visas en uppmaning om att registrera datorn genom att ladda ned Intune-klientprogramvaran. När programvaran har laddats ned kan användare installera den för att lägga till datorerna i hanteringen.

![På Intune-portalen visas en uppmaning om att hämta Intune-klientprogramvaran](../media/software-client-download.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>Övervaka och kontrollera lyckade klientdistributioner
Använd en av följande procedurer som hjälper dig att övervaka och kontrollera lyckade klientdistributioner.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Så här kontrollerar du installationen av klientprogrammet från Microsoft Intune-administrationskonsolen

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) klickar du på **Grupper** &gt; **Alla enheter** &gt; **Alla datorer**.

2.  I listan letar du reda på de hanterade datorer som kommunicerar med Intune, eller söker efter en viss hanterad dator genom att skriva namnet på datorn (eller någon del av namnet) i rutan **Sök enheter**.

3.  Kontrollera status för datorn längst ned i fönstret i konsolen. Åtgärda eventuella fel.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>Så här skapar du en datorinventeringsrapport för att visa alla datorer som har registrerats

1.  I [Microsoft Intune administrationskonsol](https://manage.microsoft.com/) klickar du på **Rapporter** &gt; **Datorinventeringsrapport**.

2.  På sidan **Skapa ny rapport** lämnar du alla fält som standardvärden (om du inte vill använda filter) och klickar sedan på **Visa rapport**.

3.  Sidan **Datorinventeringsrapport** öppnas i ett nytt fönster och visar alla datorer som registrerats i Intune.

    > [!TIP]
    > Klicka på valfri kolumnrubrik i rapporten för att sortera listan efter innehållet i den kolumnen.


### <a name="see-also"></a>Se även
[Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Felsöka klientkonfiguration](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Nov16_HO1-->


