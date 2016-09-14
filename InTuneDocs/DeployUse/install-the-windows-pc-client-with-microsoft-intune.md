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
ms.sourcegitcommit: 16be49504b24269f9463905ab5767acbda136a0a
ms.openlocfilehash: 8ceeca6735267ab66ab14e72570ace3dc8a9b524


---

# Installera Intune-klientprogrammet på Windows-datorer
Windows-datorer kan registreras genom att installera Intune-klientprogrammet. Intune-klientprogrammet kan installeras på följande sätt:

- Manuell installation
- Installation med hjälp av en grupprincip
- Installation som en del av en diskavbildning
- Installation av användare

## Ladda ned Intune-klientprogrammet

Alla metoder, utom då användarna själva installerar Intune-klientprogrammet, kräver att du laddar ned programvaran så att du kan distribuera den.

1.  I [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com/) klickar du på **Administratör** &gt; **Hämtning av klientprogramvara**.

  ![Hämta Intune PC-klienten](../media/pc-sa-client-download.png)

2.  På sidan **Hämtning av klientprogramvara** klickar du på **Hämta klientprogramvara** och sparar paketet **Microsoft_Intune_Setup.zip** som innehåller programvaran på en säker plats i nätverket.

    > [!NOTE]
    > Installationspaketet för Intune-klientprogramvaran innehåller information om ditt konto. Om obehöriga användare får tillgång till installationspaketet, kan de registrera datorer till kontot som representeras av dess inbäddade certifikat.

3.  Extrahera innehållet i installationspaket till en säker plats i nätverket.

    > [!IMPORTANT]
    > Byt inte namn eller ta inte bort filen **ACCOUNTCERT** som extraheras. Om du gör det, kommer installationen av klientprogramvaran att misslyckas.

## Distribuera manuellt

1.  Bläddra till den mapp där installationsfilerna för klientprogramvaran finns och kör sedan **Microsoft_Intune_Setup.exe** för att installera klientprogramvaran.

    > [!NOTE]
    > Installationsförloppet visas när du hovrar över ikonen i verktygsfältet på klientdatorn.

## Distribuera med hjälp av en grupprincip

1.  I mappen som innehåller filerna **Microsoft_Intune_Setup.exe** och **MicrosoftIntune.accountcert** kör du följande kommando för att extrahera Windows Installer-baserade installationsprogram för 32-bitars och 64-bitars datorer:

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  Kopiera filerna **Microsoft_Intune_x86.msi**, **Microsoft_Intune_x64.msi** och **MicrosoftIntune.accountcert** till en nätverksplats som kan användas av alla datorer som klientprogramvaran ska installeras på.

    > [!IMPORTANT]
    > Dela inte upp och byt inte namn på filerna. Om du gör det, kommer installationen av klientprogramvaran att misslyckas.

3.  Använd grupprinciper för att distribuera programvaran till datorer i nätverket.

    Mer information om hur du använder grupprinciper för att automatiskt distribuera programvara finns i dokumentationen för Windows Server.

## Installera som en del av en avbildning
Du kan distribuera Intune-klientprogramvaran till datorer som en del av en operativsystemsavbildning med hjälp av följande procedur som bas:

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

När den automatiska registreringsuppgiften körs vid nästa schemalagda tidpunkt, kontrolleras förekomsten av registervärdet **WindowsIntuneEnrollPending** och ett försök görs för att registrera måldatorn i Intune. Om registreringen misslyckas av någon anledning försöks registreringsprocessen nästa gång uppgiften körs. Återförsöken fortsätter under en period av en månad.

Den automatiska registreringsuppgiften för Intune registervärdet **WindowsIntuneEnrollPending** och kontocertifikatet tas bort från måldatorn när registreringen lyckas eller efter en månad.

## Be användaren att göra registreringen själv

Användare kan installera Intune-klientprogrammet genom att gå till  [http://portal.manage.microsoft.com](http://portal..manage.microsoft.com). Om webbportalen kan identifiera enheten som en Windows-dator visas en uppmaning om att registrera datorn genom att ladda ned Intune-klientprogrammet. När den har laddats ned kan användare installera programvaran för att lägga till datorerna i hanteringen.

![På Intune-portalen visas en uppmaning om att hämta Intune-klientprogrammet](../media/software-client-download.png)

## Övervaka och kontrollera lyckade klientdistributioner
Använd en av följande procedurer som hjälper dig att övervaka och kontrollera lyckade klientdistributioner.

### Så här kontrollerar du installationen av klientprogrammet från Microsoft Intune-administrationskonsolen

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) klickar du på **Grupper** &gt; **Alla enheter** &gt; **Alla datorer**.

2.  Bläddra nedåt i listan över datorer för att hitta hanterade datorer som kommunicerar med Intune, eller sök efter en viss hanterad dator genom att skriva namnet på datorn eller någon del av namnet i rutan **Sök enheter**.

3.  Kontrollera status för datorn längst ned i fönstret i konsolen och åtgärda eventuella fel.

### Så här skapar du en datorinventeringsrapport för att visa alla datorer som har registrerats

1.  I [Microsoft Intune administrationskonsol](https://manage.microsoft.com/) klickar du på **Rapporter** &gt; **Datorinventeringsrapport**.

2.  På sidan **Skapa ny rapport** lämnar du alla fält som standardvärden (om du inte vill använda filter) och klickar på **Visa rapport**.

3.  Sidan **Datorinventeringsrapport** öppnas i ett nytt fönster och visar alla datorer som registrerats i Intune.

    > [!TIP]
    > Klicka på valfri kolumnrubrik i rapporten för att sortera listan efter innehållet i den kolumnen.


### Se även
[Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
[Felsöka klientkonfiguration](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune)



<!--HONumber=Sep16_HO1-->


