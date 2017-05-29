---
title: Hantera datorer med klientprogrammet | Microsoft Docs
description: Hantera Windows genom att installera Intune-klientprogramvaran.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6bd4e3315fd27201e8005b1053fa6e15bf2c21b5
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Hantera Windows-datorer som datorer via Intune-programvaruklienten

Intune är en omfattande lösning som gör att organisationer kan hantera mobila enheter. Intune kan hantera Windows-datorer som mobila enheter med hjälp av de hanteringsfunktioner för moderna enheter som är inbyggda i operativsystemet Windows 10. För att uppfylla organisationens hanteringsbehov kan Intune även hantera Windows-datorer som datorer med Intune-programvaruklienten. Den här hanteringsmetoden använder traditionella funktioner för datorhantering i tidigare Windows-operativsystem.

Intune-programvaruklienten passar bäst för Windows-datorer som kör äldre operativsystem som Windows 7 som inte kan hanteras som mobila enheter. Intune-programvaruklienten använder hanteringsfunktioner som Grupprincip för att hantera datorer från molnet.

Intune stöder hantering av Windows-datorer som datorer med hjälp av programvaruklienten för upp till 7 000 datorer. Hantera Windows 10-datorer som mobila enheter för större distributioner. Varje version av Intune och varje uppdatering av Windows 10 innehåller hanteringsfunktioner som baseras på den mobila arkitekturen för enhetshantering. Vi rekommenderar starkt att du flyttar din organisation till Windows 10 hanterad som mobila enheter.


> [!NOTE]
> Du kan hantera Windows 8.1-enheter och senare som datorer med hjälp av Intune-klientprogrammet eller som mobila enheter. Du kan inte använda båda metoderna på samma enhet. Överväg noggrant innan du bestämmer dig för att hantera datorer med Intune-klientprogrammet. Det här avsnittet gäller endast för att hantera enheter som datorer genom att köra Intune-klientprogrammet.

## <a name="requirements-for-intune-pc-client-management"></a>Krav för hantering av Intune-klienten

**Maskinvara**: Minsta maskinvarukrav för att installera Intune-klientprogrammet:

|Krav|Mer information|
|---------------|--------------------|
|Nätverk|Klienten kräver att datorn är ansluten till Internet.|
|Processor och minne|Se RAM- och processorkraven för datorns operativsystem.|
|Diskutrymme|200 MB ledigt diskutrymme innan klientprogrammet har installerats.|

**Programvara**: Programvarukrav för att installera klientprogrammet:

|Krav|Mer information|
|---------------|--------------------|
|Operativsystem | Windows-enheten måste köra Windows Vista eller senare. </br></br>**Home edition-versioner stöds inte.**|
|Administrativ behörighet|Det konto som installerar klientprogramvaran måste ha lokal administratörsbehörighet på enheten.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1.<br /><br />Så visar du versionen för Windows Installer på en dator:<br /><br />  Högerklicka på **%windir%\System32\msiexec.exe**, och sedan på **Egenskaper**.<br /><br />Du kan hämta den senaste versionen av Windows Installer från [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) på webbplatsen Microsoft Developer Network.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune-klientprogrammet avinstallerar du all Configuration Manager-, Operations Manager-, Operations Management Suite- och Service Manager-klientprogramvara från datorn.|

## <a name="deploying-the-intune-software-client"></a>Distribuera Intune-programklienten
Som Intune-administratör kan du göra Intune programklienten tillgänglig för användarna på en mängd olika sätt. Vägledning finns i [Installera Intune-klientprogrammet på Windows-datorer](install-the-windows-pc-client-with-microsoft-intune.md).

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Datorhanteringsfunktioner med Intune-klientprogrammet
I de flesta fall registrerar du dina enheter i Microsoft Intune, vilket ger tillgång till fler funktioner. Men du kan också hantera datorer med hjälp av Intune-klientprogrammet, vilket innehåller följande funktioner:

-   **[Hantering av programvaruuppdateringar](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** – Du kan hålla datorerna uppdaterade och bestämma när nya uppdateringar tillämpas.

-   **[Princip för Windows-brandväggen](/intune-classic/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** – Den här typen av princip säkerställer att Windows-brandväggen är aktiverad och korrekt konfigurerad på alla datorer som används på företaget.

-   **[Skydd mot skadlig programvara](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** – Intune innehåller Endpoint Protection, som hjälper dig att skydda datorer mot skadlig kod.

-   **[Fjärrhjälp](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** – Intune låter användarna kontakta IT-supportpersonalen som sedan kan ge hjälp via en fjärrskrivbordsfunktion som ingår i Intune (kräver TeamViewer-programvara).

-   **[Hantera programvarulicenser](/intune-classic/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** – Spåra hur många programlicenser som är tillgängliga och hur många tillgängliga licenser som används.
-   **[Appdistribution](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** – Distribuera programvara till datorer som du hanterar. Vissa apphanteringsfunktioner är inte tillgängliga när du hanterar datorer med klientprogrammet.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Principer för distributioner av appar för Intune-klientprogrammet

Även om Intune-klientprogrammet har stöd för [hanteringsfunktioner som skyddar datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md) med hjälp av hantering av programuppdateringar, Windows-brandväggen och Endpoint Protection, så kan inte datorer som hanteras med Intune-klientprogrammet användas med andra Intune-principer, t.ex. de **Windows**-principinställningar som är specifika för hantering av mobila enheter.

När du använder Intune-klientprogrammet för att hantera Windows-datorer kan du använda de principer som visas i avsnittet **Datorhantering**.

Intune hanterar Windows-datorer med principer, på liknande sätt som Windows Server Active Directory Domain Services /intune-classic/deploy-use/resolve-gpo-and-microsoft-intune-policy-conflicts) används i din organisation. Läs mer i avsnittet [Grupprincip för nybörjare](https://technet.microsoft.com/library/hh147307.aspx).

  ![Välj mall för ny Windows-datorprincip](../media/select-template-for-pc-policy.png)

När du distribuerar appar behöver du bara använda Windows Installer (.exe, .msi).

  ![Välj plattform och plats för PC-klientprogramsfiler](../media/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Vanliga åtgärder för Windows-datorer

Du kan använda Intune-administratörskonsolen för att utföra andra vanliga datorhanteringsaktiviteter på Windows-datorer där klienten har installerats:
- [Använd principer för att förenkla datorhanteringen](use-policies-to-simplify-windows-pc-management.md) – Beskriver Intunes principer för **datorhantering** och listar inställningarna för Microsoft Intune Center.

- [Visa maskin- och programvaruinventering för Windows-datorer](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) – Här förklaras hur du kan skapa rapporter som visar information om datorernas maskinvarukapacitet och de program som installerats på dem. Här förklaras även hur du uppdaterar datorinventeringen så att den hålls aktuell.
- [Dra tillbaka en Windows-dator](retire-a-windows-pc-with-microsoft-intune.md) – Listar de steg som måste vidtas för att stegen för att dra tillbaka en Windows-dator och vad som händer när du gör så.
- [Hantera länkning av användarenheter för Windows-datorer](manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) – Förklarar när och hur du måste länka en användare till en dator innan du kan distribuera programvara till användaren.
- [Begära och tillhandhålla fjärrhjälp för Windows-datorer](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) – Här beskrivs hur användare av Intune-datorer får fjärrhjälp, vilka krav som finns och hur du konfigurerar TeamViewer.

Mer information om ovanstående aktiviteter finns i [vanliga datorhanteringsaktiviteter ](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

## <a name="management-limitations-of-the-intune-client-software"></a>Hanteringsbegränsningar för Intune-klientprogrammet

Vissa hanteringsalternativ som kan användas för att hantera datorer som mobila enheter kan inte användas för datorer som hanteras med Intune-klientprogrammet:

-   Fullständig rensning (selektiv rensning är tillgänglig)
-   Villkorlig åtkomst

Observera också att vissa avsnitt, t.ex. **Uppdateringar**, **Skydd** och **Licenser**bara visas i Intune-administrationskonsolen om du har registrerat enheter i Intune-klientprogrammet.

  ![Administratörskonsolobjekt som bara visas för PC-klienter](../media/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>Hjälp med felsökning

Intune-klientprogrammet körs vanligtvis tyst i bakgrunden och kräver sällan omfattande användarinteraktion eller felsökning. Om du behöver lösa datorhanteringsproblem kan kontrollera du loggarna. Intune-klientprogrammet och motsvarande loggar installeras i katalogen %Program Files%\Microsoft\OnlineManagement.

Du kan också läsa [Felsöka klientinstallationen i Microsoft Intune](/intune-classic/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) om du vill söka efter specifika problem som kan uppstå, och vilka eventuella lösningar eller åtgärder som finns.

