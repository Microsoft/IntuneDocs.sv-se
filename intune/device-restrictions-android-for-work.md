---
title: "Inställningar av begränsningar i Intune-enheter för Android for Work"
titleSuffix: Intune on Azure
description: "Läs vilka Intune-inställningar du kan använda för att kontrollera enhetsinställningar och funktioner på Android for Work-enheter.”"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1830720b-16cb-4f2f-a71a-62967f882563
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca51c413e3148039b05a9d05a9a511e7158c9a1c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Inställningar av enhetsbegränsningar för Android for Work-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Inställningar för arbetsprofil
- **Datadelning mellan arbetsprofiler och personliga profiler** – Använd den här inställningen för att styra om appar i arbetsprofilen ska kunna dela med appar i den personliga profilen. Den här inställningen styr delningsåtgärder inom program (till exempel alternativet **Dela...** i Chrome-webbläsarappen) och gäller inte för kopiera och klistra in beteendet för Urklipp. Till skillnad från [principinställningarna för appskydd](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), hanteras inställningarna för enhetsbegränsning från Intune-portalen och använder partitionen för Android for Work-arbetsprofilen för att isolera hanterade appar. Välj mellan:
    - **Standardbegränsningar för delning** – Detta är standardinställningen för delning av enheten, vilket varierar beroende på den version av Android den använder. Som standard tillåts delning från den personliga profilen till arbetsprofilen. Som standard är dessutom delning mellan arbetsprofilen och den personliga profilen blockerad. Detta förhindrar att arbetsdata delas till den personliga profilen. Google tillhandahåller inget sätt att blockera delning från den personliga profilen till arbetsprofilen för enheter som version 6.0 eller senare.   
    - **Appar i arbetsprofilen kan hantera delningsförfrågningar från personlig profil** – Använd det här alternativet för att aktivera den inbyggda Android-funktionen som tillåter delning från den personliga profilen till arbetsprofilen. När detta är aktiverat, kan en delningsbegäran från en app i den personliga profilen dela med appar i arbetsprofilen. Det här är standardinställningen för Android-enheter som kör tidigare versioner än 6.0.
    - **Tillåt delning över gränser** – aktiverar delning över arbetsprofilgränsen i bägge riktningarna. När du väljer den här inställningen så kommer appar i arbetsprofilen att kunna dela data med omärkta appar i den personliga profilen. Använd den här inställningen med försiktighet. Den gör att hanterade appar i arbetsprofilen kan dela med appar på den ohanterade delen av enheten.

-   **Arbetsprofilmeddelanden när enheten är låst** – Styr om appar i arbetsprofilen får visa data i meddelanden när enheten är låst.
-   **Standardbehörigheter för app** – Anger principen för standardbehörighet för alla appar i arbetsprofilen. Från och med Android 6, måste användaren bevilja vissa behörigheter som krävs av appar när appen startas. Den här principinställningen låter dig välja om användare ombes att bevilja behörigheter för alla appar i arbetsprofilen. Om du till exempel tilldelar en app i arbetsprofilen som kräver platsåtkomst. Normalt skulle den appen be användaren att godkänna eller neka platsåtkomst för appen. Med den här principen kan du avgöra om alla behörigheter ska beviljas automatiskt utan att användaren tillfrågas, nekas automatiskt utan att användaren tillfrågas eller låta användaren bestämma. Välj mellan:
    -   **Standard för enheten**
    -   **Fråga**
    -   **Bevilja automatiskt**
    -   **Neka automatiskt**

    Bevilja-tillstånd för behörigheter kan definieras ytterligare för specifika appar, genom att definiera en princip för appkonfiguration för en enskild app (under **mobilappar** > **appkonfigurationsprinciper**).

### <a name="work-profile-password"></a>Lösenord för arbetsprofilen
- **Kräv lösenord för arbetsprofilen** –(Android 7.0 och senare med arbetsprofil aktiverad) definiera en lösenordsprincip som bara gäller för appar i arbetsprofilen. Som standard kan slutanvändaren använda de två separat definierade PIN-koderna, eller så kan de välja att kombinera de två definierade PIN-koderna till den starkare av de två.
- **Minsta lösenordslängd** – Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**16**)
- **Maximalt antal inaktiva minuter tills skärmen låser sig** – Välj hur lång tid innan en inaktiv enhet kräver en att en användare anger arbetsprofilens lösenord för att köra en app i arbetsprofilen.
- **Antal felaktiga inloggningar innan enheten rensas** – Ange hur många gånger ett felaktigt lösenord kan anges innan arbetsprofilen rensas från enheten.
- **Lösenordets giltighetstid (dagar)** – Ange antal dagar innan användarens lösenord måste ändras (från **1**-**255**).
- **Krav på lösenordstyp** – Välj den typ av lösenord som måste anges på enheten. Välj mellan:
    - **Standard för enheten**
    - **Låg säkerhetsbiometri**
    - **Obligatoriskt**
    - **Minst numeriskt**
    - **Numeriskt avancerat** – (upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte)
    - **Minst alfabetiskt**
    - **Minst alfanumeriskt**
    - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord** – Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck** – Blockerar en användare från att använda enhetens fingeravtrycksläsare för att låsa upp den.
- **Smart Lock och andra betrodda agenter** – Innebär att du kan styra Smart Lock-funktionen på kompatibla enheter. Med den här telefonfunktionen, som ibland kallas för en betrodd agent, kan du inaktivera eller kringgå lösenordet för arbetsprofilen, om enheten är på en betrodd plats (till exempel när den är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg). Du kan använda den här inställningen för att förhindra att användarna konfigurerar Smart Lock.

## <a name="password"></a>Lösenord

- **Minsta längd på lösenord** – Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**14**)
- **Maximalt antal minuter av inaktivitet tills skärmen låses** – Välj hur lång tid det tar innan en inaktiv enhet låses automatiskt.
- **Antal felaktiga inloggningar innan enheten rensas** – Ange hur många gånger ett felaktigt lösenord kan anges innan alla data rensas från enheten.
- **Lösenordets giltighetstid (dagar)** – Ange antal dagar innan användarens lösenord måste ändras (från **1**-**255**).
- **Krav på lösenordstyp** – Välj den typ av lösenord som måste anges på enheten. Välj mellan:
    - **Standard för enheten**
    - **Låg säkerhetsbiometri**
    - **Obligatoriskt**
    - **Minst numeriskt**
    - **Numeriskt avancerat** – (upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte)
    - **Minst alfabetiskt**
    - **Minst alfanumeriskt**
    - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord** – Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck** – Blockerar en användare från att använda enhetens fingeravtrycksläsare för att låsa upp den.
- **Smart Lock och andra betrodda agenter** – Innebär att du kan styra Smart Lock-funktionen på kompatibla enheter. Med den här telefonfunktionen, som ibland kallas för en betrodd agent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats (till exempel när den är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg). Du kan använda inställningen för att förhindra att användarna konfigurerar Smart Lock.
