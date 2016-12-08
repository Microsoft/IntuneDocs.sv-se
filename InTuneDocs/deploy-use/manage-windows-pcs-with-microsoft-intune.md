---
title: Hantera datorer med klientprogrammet | Microsoft Intune
description: Hantera Windows genom att installera Intune-klientprogramvaran.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: fb862178e0791936243ebb21c6b70ea808d07d16


---

# <a name="manage-windows-pcs-with-intune-pc-client-software"></a>Hantera Windows-datorer med Intune-klientprogramvara
I stället för att [registrera Windows-datorer som mobila enheter](set-up-windows-device-management-with-microsoft-intune.md) kan du registrera och hantera Windows-datorer genom att installera klientprogramvaran för Intune.

Intune hanterar Windows-datorer med hjälp av principer på liknande sätt som AD DS-grupprincipobjekt (Active Directory Domain Services) för Windows Server gör. Om du ska hantera domänanslutna Active Directory-datorer med Intune bör du [försäkra dig om att Intune-principerna inte står i konflikt med grupprincipobjekt](resolve-gpo-and-microsoft-intune-policy-conflicts.md) som används i din organisation.

Även om Intune-klientprogrammet har stöd för [hanteringsfunktioner som skyddar datorer](policies-to-protect-windows-pcs-in-microsoft-intune.md) med hjälp av hantering av programuppdateringar, Windows-brandväggen och Endpoint Protection, så kan inte datorer som hanteras med Intune-klientprogrammet användas med andra Intune-principer, t.ex. de **Windows**-principinställningar som är specifika för hantering av mobila enheter.

> [!NOTE]
> Enheter som kör Windows 8.1 eller senare kan hanteras med Intune-klienten eller som mobila enheter. Det här avsnittet gäller för datorer som kör Intune-klientprogrammet. Installation av Intune-klienten och registrering i hantering av mobila enheter stöds inte.

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
|Operativsystem | Windows-enheten måste köra Windows Vista eller senare. Home edition-versioner stöds inte.|
|Administrativ behörighet|Det konto som installerar klientprogramvaran måste ha lokal administratörsbehörighet på enheten.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1.<br /><br />Så visar du versionen för Windows Installer på en dator:<br /><br />-   Högerklicka på **%windir%\System32\msiexec.exe**, och sedan på **Egenskaper**.<br /><br />Du kan hämta den senaste versionen av Windows Installer från [Windows Installer Redistributables](http://go.microsoft.com/fwlink/?LinkID=234258) på webbplatsen Microsoft Developer Network.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune-klientprogrammet avinstallerar du all Configuration Manager-, Operations Manager-, Operations Management Suite- och Service Manager-klientprogramvara från datorn.|

## <a name="computer-management-with-the-intune-computer-client"></a>Datorhantering med Intune-datorklienten
När Intune-klientprogrammet har installerats ingår följande hanteringsfunktioner: [programhantering](deploy-apps-in-microsoft-intune.md), [realtidsövervakning och Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md), [hantering av inställningar för Windows-brandväggen](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md), maskinvaru- och programvaruinventering, fjärrstyrning (via begäran om fjärrhjälp), [inställningar för programuppdateringar](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md) och rapportering av efterlevnadsinställningar.

Vissa hanteringsalternativ som är tillgängliga för datorer som hanteras som mobila enheter är inte tillgängliga för datorer som hanteras med klientprogram, till exempel:

-   Fullständig rensning (selektiv rensning är tillgänglig)
-   Villkorlig åtkomst
-   Andra Windows-principer än principer för **datorhantering**

![Principmall för Windows-datorer](../media/pc_policy_template.png)

Förutom att vidta åtgärder med Intune-klientagenten lokalt på enskilda datorer kan du utföra andra [vanliga datorhanteringsåtgärder](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md) med Intune-administratörskonsolen på Windows-datorer där klienten är installerad:

-   Visa maskin- och programvaruinventering för hanterade datorer

-   Starta om en dator via en fjärranslutning

-   Dra tillbaka en dator för att avinstallera klientprogramvaran och ta bort den från hantering i Intune

-   Länka användare till specifika hanterade datorer

-   Svara på en begäran om Fjärrhjälp

Intune-klientagenten körs vanligtvis tyst i bakgrunden och kräver sällan omfattande användarinteraktion eller felsökning. Om du ändå behöver hjälp med att lösa datorhanteringsproblem finns det flera [tillgängliga resurser där du kan få hjälp](/intune/troubleshoot/troubleshoot-client-setup-in-microsoft-intune).



<!--HONumber=Nov16_HO1-->


