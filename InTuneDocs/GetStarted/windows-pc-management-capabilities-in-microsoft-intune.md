---
# required metadata

title: Funktioner för hantering av Windows-datorer | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Funktioner för hantering av Windows-datorer (med Microsoft Intune PC-klienten)
I de flesta fall registrerar du dina enheter i Microsoft Intune, vilket ger tillgång till fler funktioner än med Intune PC-klienten. Men du kan också hantera datorer med hjälp av Intune PC-klienten som tillhandahåller följande funktioner:

-   **Hantera programvaruuppdateringar** – Du kan hålla datorerna uppdaterade och hantera dem när nya uppdateringar tillämpas.

-   **Princip för Windows-brandväggen** – Den här typen av princip säkerställer att Windows-brandväggen är aktiverad och korrekt konfigurerad på alla datorer som används på företaget.

-   **Skydd mot skadlig programvara** – Intune innehåller Endpoint Protection, som hjälper dig att skydda datorer mot skadlig kod.

-   **Fjärrhjälp** – Intune låter användarna kontakta IT-supportpersonalen som sedan kan ge hjälp via en fjärrskrivbordsfunktion som ingår i Intune (kräver TeamViewer-programvara).

-   **Hantera programvarulicenser** –Spåra hur många programlicenser som är tillgängliga och hur många tillgängliga licenser som används.
-   **Appdistribution** – Distribuera programvara till datorer som du hanterar. Vissa apphanteringsfunktioner är inte tillgängliga när du hanterar datorer med klientprogramvaran.


## Krav på operativsystem
Intune kan hantera datorer som kör följande Windows-versioner (både x86 och x64):


-   **Windows Vista** – Business-, Enterprise- och Ultimate-versioner.

-   **Windows 7** – Pro-, Enterprise- och Ultimate-versionerna (utan service pack eller med SP1).

-   **Windows 8** – Pro- och Enterprise-versionerna.

-   **Windows 8.1** – Pro- och Enterprise-versionerna.

- **Windows 10** – Home-, Pro-, Education- och Enterprise-versionerna.


## Minsta maskinvarukrav
Följande är de minsta maskinvarukraven för att installera Intune PC-klienten:

|Krav|Information|
|---------------|--------------------|
|Nätverk|Klienten kräver att datorn är ansluten till Internet.|
|Processor och minne|Se RAM- och processorkraven för datorns operativsystem.|
|Diskutrymme|200 MB ledigt diskutrymme innan klientprogrammet har installerats.|

## Ytterligare krav
Nedan visas programvarukraven för att installera Intune PC-klienten:

|Krav|Information|
|---------------|--------------------|
|Administrativ behörighet|Det konto som installerar klientprogrammet måste ha lokal administratörsbehörighet på datorn.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1 installerat.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune PC-klientprogrammet måste du avinstallera följande klientprogram från datorn:<br /><br />– Alla versioner av Configuration Manager<br />– Alla versioner av Microsoft Systems Management Server (SMS)|

### Se även
[Funktioner för hantering av mobila enheter i Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)


<!--HONumber=May16_HO3-->


