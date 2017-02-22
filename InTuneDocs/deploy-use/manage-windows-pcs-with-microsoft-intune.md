---
title: Hantera datorer med klientprogrammet | Microsoft Docs
description: Hantera Windows genom att installera Intune-klientprogramvaran.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 45c32cf08e4d6fd570af287ed64411edc9d9b394
ms.openlocfilehash: 21e83b68bb68384a8916db8d7f779cddde18a8a6


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Hantera Windows-datorer med Intune-klientprogramvara
I stället för att [registrera Windows-datorer som mobila enheter](set-up-windows-device-management-with-microsoft-intune.md) kan du registrera och hantera Windows-datorer genom att installera klientprogramvaran för Intune.

Intune hanterar Windows-datorer med hjälp av principer på liknande sätt som AD DS-grupprincipobjekt (Active Directory Domain Services) för Windows Server gör. [Försäkra dig om att Intune-principerna inte står i konflikt med grupprincipobjekt](resolve-gpo-and-microsoft-intune-policy-conflicts.md) som används i din organisation om du ska hantera domänanslutna Active Directory-datorer med Intune. Läs mer om [GPO:er](https://technet.microsoft.com/library/hh147307.aspx).

Även om Intune-klientprogrammet har stöd för [hanteringsfunktioner som skyddar datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md) med hjälp av hantering av programuppdateringar, Windows-brandväggen och Endpoint Protection, så kan inte datorer som hanteras med Intune-klientprogrammet användas med andra Intune-principer, t.ex. de **Windows**-principinställningar som är specifika för hantering av mobila enheter. 

När du använder Intune-programvaruklienten för att hantera Windows-datorer, kan du använda de principer som visas i avsnittet **Datorhantering**.

  ![Välj mall för ny Windows-datorprincip](../media/select-template-for-pc-policy.png)

Mer information om de principer som du kan ställa in finns här:

- [Använd principer för att skydda Windows-datorer som kör Intune-klientprogramvaran](https://docs.microsoft.com/intune/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)
- [Hålla datorerna uppdaterade med programvaruuppdateringar i Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)
- [Hjälp till att skydda Windows-datorer med principer för Windows-brandväggen i Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)
- [Skydda Windows-datorer med Endpoint Protection för Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

När du distribuerar appar behöver du dessutom bara använda Windows Installer (.exe, .msi).

  ![Välj plattform och plats för PC-klientprogramsfiler](../media/select-platform-of-software-files-for-pc-agent.png)

> [!NOTE]
> Du kan hantera Windows 8.1-enheter eller senare som datorer med hjälp av Intune-klienten, eller som mobila enheter genom att använda funktionen för hantering av mobilenheter (MDM). Du kan använda båda metoderna tillsammans, så tänk dig för innan du bestämmer dig att hantera datorer med hjälp av Intunes programvaruklient. Det här avsnittet gäller endast för att hantera enheter som datorer genom att köra Intune-programvaruklienten.

## <a name="requirements-for-intune-pc-client-management"></a>Krav för hantering av Intune-klienten

**Maskinvara**: Minsta maskinvarukrav för att installera Intune-klienten:

|Krav|Mer information|
|---------------|--------------------|
|Nätverk|Klienten kräver att datorn är ansluten till Internet.|
|Processor och minne|Se RAM- och processorkraven för datorns operativsystem.|
|Diskutrymme|200 MB ledigt diskutrymme innan klientprogrammet har installerats.|

**Programvara**: Programvarukrav för att installera klienten:

|Krav|Mer information|
|---------------|--------------------|
|Operativsystem | Windows-enheten måste köra Windows Vista eller senare. </br></br>**Home edition-versioner stöds inte.**|
|Administrativ behörighet|Det konto som installerar klientprogramvaran måste ha lokal administratörsbehörighet på enheten.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1.<br /><br />Så visar du versionen för Windows Installer på en dator:<br /><br />  Högerklicka på **%windir%\System32\msiexec.exe**, och sedan på **Egenskaper**.<br /><br />Du kan hämta den senaste versionen av Windows Installer från [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) på webbplatsen Microsoft Developer Network.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune-klientprogrammet avinstallerar du all Configuration Manager-, Operations Manager-, Operations Management Suite- och Service Manager-klientprogramvara från datorn.|

## <a name="computer-management-capabilities-with-the-intune-software-client"></a>Datorhanteringsfunktioner med Intunes programvaruklient

När Intune-klientprogrammet har installerats kan du använda följande hanteringsfunktioner: 

- [Programhantering](deploy-apps-in-microsoft-intune.md)

- [Realtidsövervakning och Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)

 > [!NOTE]
 > Endpoint Protection är detsamma som Windows Defender. Endpoint Protection gäller för Windows 7 och Windows 8. För Windows 10 och senare har produktens namn ändrats till Windows Defender.

- [Hantering av inställningar för Windows-brandväggen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), inventering av maskinvara och programvara, fjärrkontroll (via förfrågningar om fjärrhjälp)

- [Inställningar för programvaruuppdatering](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)

- Rapportering om kompatibilitetsinställningar

I Intune-administrationskonsolen visas vissa avsnitt, t.ex. Uppdateringar, Skydd och Licenser, bara om du har registrerat enheter med Intune-programvaruklienten.

  ![Administratörskonsolobjekt som bara visas för PC-klienter](../media/admin-console-settings-only-for-pc-agent.png)

Du kan också använda Intune-administratörskonsolen för att utföra andra [vanliga datorhanteringsaktiviteter](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) på Windows-datorer där klienten har installerats:

-   Visa maskin- och programvaruinventering för hanterade datorer

-   Starta om en dator via en fjärranslutning

-   Dra tillbaka en dator för att avinstallera programvaruklienten och ta bort den från hantering i Intune

-   Länka användare till specifika hanterade datorer

-   Svara på en begäran om Fjärrhjälp

## <a name="management-limitations-of-the-intune-software-client"></a>Hanteringsbegränsningar för Intune-programvaruklienten

Vissa hanteringsalternativ, som kan användas för att hantera datorer som mobila enheter, kan inte användas för datorer som hanteras med Intune-programvaruklienten:

-   Fullständig rensning (selektiv rensning är tillgänglig)

-   Villkorlig åtkomst

## <a name="help-with-troubleshooting"></a>Hjälp med felsökning

Intune-klientagenten körs vanligtvis tyst i bakgrunden och kräver sällan omfattande användarinteraktion eller felsökning. Om du behöver lösa datorhanteringsproblem kan kontrollera du loggarna. Intune-programvaruklienten och motsvarande loggar installeras i katalogen % Program Files%\Microsoft\OnlineManagement.

Du kan också läsa [Felsöka klientinstallationen i Microsoft Intune](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune) om du vill söka efter specifika problem som kan uppstå, och vilka eventuella lösningar eller åtgärder som finns.



<!--HONumber=Feb17_HO2-->


