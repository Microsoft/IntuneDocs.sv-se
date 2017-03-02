---

title: Installera datorklientprogrammet | Microsoft Docs
description: "Använd den här guiden för att låta dina Windows-datorer hanteras av Microsoft Intune-klientprogrammet."
keywords: 
author: staciebarker
ms.author: stabar
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 2e7062169ceb855f03a13d1afb4b4de41af593ac
ms.openlocfilehash: 9606d8f79166e6b38f02aefd4afc52f2a47c1362
ms.lasthandoff: 02/16/2017


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>Installera Intune-klientprogrammet på Windows-datorer
Windows-datorer kan registreras genom att installera Intune-klientprogrammet. Intune-klientprogrammet kan installeras med följande metoder:

- Av en IT-administratör som använder någon av följande metoder: manuell installation, grupprincip, installation som finns i en diskavbildning

- Av slutanvändare som installerar klientprogrammet manuellt

Intune-klientprogrammet innehåller lägsta nödvändiga programvara för att registrera datorn i Intune-hanteringen. När en dator har registrerats hämtar Intune-klientprogrammet det fullständiga klientprogrammet som behövs för datorhantering.

Den här serien med hämtningar minskar påverkan på nätverkets bandbredd och minimerar den tid som krävs för att börja registrera datorn i Intune. Det garanterar även att klienten har den senaste tillgängliga programvaran efter att den andra hämtningen har slutförts.

## <a name="download-the-intune-client-software"></a>Hämta Intune-klientprogramvaran

Alla metoder, förutom då användarna själva installerar Intune-klientprogramvaran, kräver att IT-administratörer hämtar programvaran först så att den kan distribueras till slutanvändarna.

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) klickar du på **Administratör** &gt; **Hämtning av klientprogramvara**.

  ![Hämta Intune PC-klienten](../media/pc-sa-client-download.png)

2.  På fliken **Hämtning av klientprogram** klickar du på **Hämta klientprogram**. Spara sedan paketet **Microsoft_Intune_Setup.zip** som innehåller programvaran på en säker plats i nätverket.

Intune-installationspaketet för klientprogramvaran innehåller unik och specifik information om ditt konto som finns tillgängligt via ett inbäddat certifikat. Om obehöriga användare får tillgång till installationspaketet kan de registrera datorer till kontot som representeras av dess inbäddade certifikat och kan då få tillgång till företagsresurser.

3.  Extrahera innehållet i installationspaket till en säker plats i nätverket.

    > [!IMPORTANT]
    > Byt inte namn på eller ta bort filen **ACCOUNTCERT** som har extraheras. Om du gör det kommer installationen av klientprogrammet att misslyckas.

## <a name="deploy-the-client-software-manually"></a>Distribuera klientprogramvaran manuellt

Gå till den mapp där installationsfilerna för klientprogrammet finns på de datorer där klientprogrammet ska installeras. Kör sedan **Microsoft_Intune_Setup.exe** för att installera klientprogramvaran.

> [!NOTE]
> Installationsförloppet visas när du hovrar över ikonen i verktygsfältet på klientdatorn.

## <a name="deploy-the-client-software-by-using-group-policy"></a>Distribuera klientprogramvaran automatiskt med hjälp av en grupprincip

1.  I mappen som innehåller filerna **Microsoft_Intune_Setup.exe** och **MicrosoftIntune.accountcert** kör du följande kommando för att extrahera Windows Installer-baserade installationsprogram för 32-bitars och 64-bitars datorer:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Kopiera filerna **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** och **MicrosoftIntune.accountcert** till en nätverksplats som kan användas av alla datorer som klientprogramvaran ska installeras på.

    > [!IMPORTANT]
    > Dela inte upp och byt inte namn på filerna. Om du gör det, kommer installationen av klientprogramvaran att misslyckas.

3.  Använd grupprinciper för att distribuera programvaran till datorer i nätverket.

    Mer information om hur du använder grupprinciper för automatisk distribution av programvara finns i [Grupprincip för nybörjare](https://technet.microsoft.com/library/hh147307.aspx).

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

## <a name="instruct-users-to-self-enroll"></a>Be användarna att göra registreringen själv

Användare installerar Intune-klientprogrammet genom att gå till [företagsportalens webbplats](http://portal.manage.microsoft.com). Den exakta informationen som användarna ser i webbportalen kan variera beroende på ditt kontos MDM-auktoritet och OS-plattformen/versionen på användarens dator. 

Om användarna inte har tilldelats en licens för Intune eller om organisationens MDM-auktoritet inte har konfigurerats för Intune kan användarna inte se några alternativ för att registrera sig.

Om användarna inte har tilldelats en licens för Intune och organisationens MDM-auktoritet har konfigurerats för Intune:

- Användare med Windows 7 eller Windows 8-datorer kan ENDAST se alternativet att registrera på Intune genom att hämta och installera klientprogrammet för datorer som är unik för deras organisation.

- Användare av Windows 10- eller Windows 8.1-datorer visas två registreringsalternativ:

  -  **Registrera Windows-datorer som mobila enheter**: Användare trycker på knappen **Läs mer om att registrera** och tas till anvisningar om hur du registrerar datorn som en mobil enhet. Den här knappen visas tydligt eftersom MDM-registreringen anses vara det registreringsalternativ som är standard och föredras. Dock gäller inte MDM-alternativet för det här avsnittet, som endast omfattar installationen av klientprogrammet.
  - **Registrera datorn med Intune-klientprogrammet**: Du måste berätta för användarna att de ska välja länken **Klicka här om du vill ladda ned** som tar dem genom installationen av klientprogrammet.

Följande tabell innehåller en sammanfattning av alternativen.

  ![Standardalternativen för registrering per plattform](../media/default-enrollment-options-table.png)

De följande skärmbilderna visar vad användarna ser när de registrerar sina enheter med hjälp av klientprogrammet.

Användare uppmanas att identifiera eller registrera enheten.

  ![identifiera eller registrera enhet](../media/identify-device-or-enroll.png)

För att få användarna att installera klientprogrammet för datorer måste du be dem att välja länken **Klicka här om du vill ladda ned** som låter dem att ladda ned klientprogrammet för datorer och tar dem genom installationsprocessen. Knappen **Läs mer om att registrera** tar användare till dokumentationen om hur du registrerar med hjälp av MDM-registrering, som inte är relevant för de här instruktionerna om klientprogrammet.

  ![välj länken Klicka här om du vill ladda ned](../media/enroll-your-windows-device.png)

När användarna klickar på länken visas knappen **Hämta programvara** som användaren kan trycka på för att starta installationen av klientprogrammet för datorer.

  ![Tryck på knappen Hämta program](../media/download-pc-client-software.png)

Användarna uppmanas sedan att logga in med sina företagsuppgifter.

  ![Logga in med dina inloggningsuppgifter](../media/sign-in-to-intune.png)

Användarna tas till välkomstsidan för installationen.

  ![Välkomstsida för installation av klient för datorer](../media/welcome-to-pc-agent-install-wizard.png)

Användarna väljer **Nästa** för att starta installationen.

  ![Välkomstsida för installation av klient för datorer](../media/welcome-to-pc-agent-install-wizard.png)

När installationen har slutförts väljer användarna **Slutför**.

  ![Avsluta installationen av klienten för datorer](../media/completed-the-setup-wizard.png)

Om användare försöker registrera sina datorer som mobila enheter när de redan har registrerat sig med hjälp av Intune-klientprogrammet för datorer visas följande felmeddelande.

  ![Skärmbilden som visas om datorn redan har registrerats](../media/page-shown-if-pc-already-enrolled.png)

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

