---
title: Funktioner i Intune-klientprogrammet | Microsoft Intune
description: "Läs om funktionerna du kan använda i Intune när du hanterar Windows-datorer med Intune-klientprogrammet."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 453323aa38eed0a01aa8d583376162734439a69c
ms.openlocfilehash: 0d4ec8077e2521b23808fcb537c4b2389fee714a


---

# Windows datorhanteringsfunktioner när du använder Intune-klientprogrammet
I de flesta fall registrerar du dina enheter i Microsoft Intune, vilket ger tillgång till fler funktioner. Men du kan också hantera datorer med hjälp av Intune-klientprogrammet, vilket innehåller följande funktioner:

-   **[Hantering av programvaruuppdateringar](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)** – Du kan hålla datorerna uppdaterade och bestämma när nya uppdateringar tillämpas.

-   **[Princip för Windows-brandväggen](/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune)** – Den här typen av princip säkerställer att Windows-brandväggen är aktiverad och korrekt konfigurerad på alla datorer som används på företaget.

-   **[Skydd mot skadlig programvara](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)** – Intune innehåller Endpoint Protection, som hjälper dig att skydda datorer mot skadlig kod.

-   **[Fjärrhjälp](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-to-windows-pcs-that-use-the-intune-client-software )** – Intune låter användarna kontakta IT-supportpersonalen som sedan kan ge hjälp via en fjärrskrivbordsfunktion som ingår i Intune (kräver TeamViewer-programvara).

-   **[Hantera programvarulicenser](/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)** – Spåra hur många programlicenser som är tillgängliga och hur många tillgängliga licenser som används.
-   **[Appdistribution](/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)** – Distribuera programvara till datorer som du hanterar. Vissa apphanteringsfunktioner är inte tillgängliga när du hanterar datorer med klientprogrammet.


Intune stöder installation av klientprogrammet på upp till 7 000 Windows-enheter.

## Krav på operativsystem
Intune kan hantera datorer som kör följande Windows-versioner (både 32-bitars och 64-bitars):


-   **Windows Vista** – Business-, Enterprise- och Ultimate-versioner

-   **Windows 7** – Pro-, Enterprise- och Ultimate-versionerna (utan service pack eller med SP1)

-   **Windows 8** – Pro- och Enterprise-versionerna

-   **Windows 8.1** – Pro- och Enterprise-versionerna

- **Windows 10** – Pro-, Education- och Enterprise-versionerna


## Minsta maskinvarukrav
Minimikraven på maskinvara för installation av Intune-klientprogrammet är:

|Krav|Information|
|---------------|--------------------|
|Nätverk|Klienten kräver att datorn är ansluten till Internet.|
|Processor och minne|Se RAM- och processorkraven för datorns operativsystem.|
|Diskutrymme|200 MB ledigt diskutrymme innan klientprogrammet har installerats.|

## Ytterligare krav
Minimikraven på programvara för installation av Intune-klientprogrammet är:

|Krav|Information|
|---------------|--------------------|
|Administrativ behörighet|Kontot som används för att installera klientprogramvaran måste ha lokal administratörsbehörighet på datorn.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune PC-klientprogrammet måste du avinstallera följande klientprogram från datorn:<br /><br />– Alla versioner av Configuration Manager<br />– Alla versioner av Microsoft Systems Management Server (SMS)|

### Se även
[Funktioner för hantering av registrerade enheter i Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


