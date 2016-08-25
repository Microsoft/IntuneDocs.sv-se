---
title: "Funktioner för hantering av Windows-datorer | Microsoft Intune"
description: "Läs om funktionerna du kan använda i Intune när du hanterar datorer med Windows Intune-klientprogrammet."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 77fa5c66-a87c-47df-964c-800eea509b33
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a6caef9e0f4d6235ecf1a89c1765d6c8e6ce1a7b
ms.openlocfilehash: e5e3833a38434d4fe55cae554fc49f567b606ad8


---

# Funktioner för hantering av Windows-datorer (med Microsoft Intune PC-klienten)
I de flesta fall registrerar du dina enheter i Microsoft Intune, vilket ger tillgång till fler funktioner än med Intune PC-klienten. Men du kan också hantera datorer med hjälp av Intune PC-klienten som tillhandahåller följande funktioner:

-   **Hantering av programvaruuppdateringar** – Du kan hålla datorerna uppdaterade och bestämma när nya uppdateringar tillämpas.

-   **Princip för Windows-brandväggen** – Den här typen av princip säkerställer att Windows-brandväggen är aktiverad och korrekt konfigurerad på alla datorer som används på företaget.

-   **Skydd mot skadlig programvara** – Intune innehåller Endpoint Protection, som hjälper dig att skydda datorer mot skadlig kod.

-   **Fjärrhjälp** – Intune låter användarna kontakta IT-supportpersonalen som sedan kan ge hjälp via en fjärrskrivbordsfunktion som ingår i Intune (kräver TeamViewer-programvara).

-   **Hantera programvarulicenser** –Spåra hur många programlicenser som är tillgängliga och hur många tillgängliga licenser som används.
-   **Appdistribution** – Distribuera programvara till datorer som du hanterar. Vissa apphanteringsfunktioner är inte tillgängliga när du hanterar datorer med klientprogramvaran.


Intune stöder installation av PC-klientprogramvara på upp till 7 000 Windows-enheter.

## Krav på operativsystem
Intune kan hantera datorer som kör följande Windows-versioner (både 32-bitars och 64-bitars):


-   **Windows Vista** – Business-, Enterprise- och Ultimate-versioner

-   **Windows 7** – Pro-, Enterprise- och Ultimate-versionerna (utan service pack eller med SP1)

-   **Windows 8** – Pro- och Enterprise-versionerna

-   **Windows 8.1** – Pro- och Enterprise-versionerna

- **Windows 10** – Pro-, Education- och Enterprise-versionerna


## Minsta maskinvarukrav
Minsta maskinvarukrav för att installera Intune PC-klienten:

|Krav|Information|
|---------------|--------------------|
|Nätverk|Klienten kräver att datorn är ansluten till Internet.|
|Processor och minne|Se RAM- och processorkraven för datorns operativsystem.|
|Diskutrymme|200 MB ledigt diskutrymme innan klientprogrammet har installerats.|

## Ytterligare krav
Minsta programvarukrav för att installera Intune PC-klienten:

|Krav|Information|
|---------------|--------------------|
|Administrativ behörighet|Kontot som används för att installera klientprogramvaran måste ha lokal administratörsbehörighet på datorn.|
|Windows Installer 3.1|Datorn måste minst ha Windows Installer 3.1.|
|Ta bort klientprogram som inte är kompatibla|Innan du installerar Intune PC-klientprogrammet måste du avinstallera följande klientprogram från datorn:<br /><br />– Alla versioner av Configuration Manager<br />– Alla versioner av Microsoft Systems Management Server (SMS)|

### Se även
[Funktioner för hantering av mobila enheter i Microsoft Intune](./mobile-device-management-capabilities-in-microsoft-intune.md)



<!--HONumber=Aug16_HO3-->


