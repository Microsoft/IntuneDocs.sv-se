---
title: Enhetsbegränsningar för Android for Work i Microsoft Intune – Azure | Microsoft Docs
description: Du kan begränsa vissa inställningar på enheter som kör Android for Work, inklusive kopiera och klistra in, visa aviseringar, appbehörigheter, datadelning, lösenordslängd, inloggningsfel, användning av fingeravtryck för att låsa upp, återanvändning av lösenord och aktivering av bluetooth-delning för arbetskontakter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1db0e98318c05c7a1a854ed1af77d9d9654cc38
ms.sourcegitcommit: 401cedcd7acc6cb3a6f18d4679bdadb0e0cdf443
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2018
ms.locfileid: "32046323"
---
# <a name="work-device-restriction-settings-in-intune"></a>Inställning av enhetsbegränsningar för arbetsenheter i Intune

I den här artikeln visas alla inställningar av begränsningar för Microsoft Intune-enheter som du kan konfigurera för enheter som kör Android for Work.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Inställningar för arbetsprofil

### <a name="general-settings"></a>Allmänna inställningar

- **Kopiera och klistra in mellan arbetsprofiler och personliga profiler**: Styr kopiera och klistra in mellan arbetsappar och personliga appar. Aktivera blockering genom att välja **Blockera**. Välj **Inte konfigurerad** för att inaktivera blockering.
- **Datadelning mellan arbetsprofiler och personliga profiler**: Styr om appar i arbetsprofilen ska kunna dela med appar i den personliga profilen. Den här inställningen styr delningsåtgärder inom program (till exempel alternativet **Dela...** i Chrome-webbläsarappen) och gäller inte för kopiera och klistra in för Urklipp. Till skillnad från [principinställningarna för appskydd](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) hanteras inställningarna för enhetsbegränsning från Intune-portalen och använder partitionen för Android for Work-arbetsprofilen för att isolera hanterade appar. Välj mellan:
  - **Standardbegränsningar för delning**: Detta är standardinställningen för delning av enheten, vilket varierar beroende på Android-version. Som standard tillåts delning från den personliga profilen till arbetsprofilen. Som standard är dessutom delning mellan arbetsprofilen och den personliga profilen blockerad. Den här inställningen förhindrar att arbetsdata delas till den personliga profilen. Google tillhandahåller inget sätt att blockera delning från den personliga profilen till arbetsprofilen för enheter som version 6.0 eller senare.
  - **Appar i arbetsprofilen kan hantera delningsförfrågningar från personlig profil**: Aktiverar den inbyggda Android-funktionen som tillåter delning från den personliga profilen till arbetsprofilen. När detta är aktiverat, kan en delningsbegäran från en app i den personliga profilen dela med appar i arbetsprofilen. Det här är standardinställningen för Android-enheter som kör tidigare versioner än 6.0.
  - **Tillåt delning över gränser**: Aktiverar delning över arbetsprofilgränsen i bägge riktningarna. När du väljer den här inställningen så kommer appar i arbetsprofilen att kunna dela data med omärkta appar i den personliga profilen. Använd den här inställningen med försiktighet, eftersom den gör att hanterade appar i arbetsprofilen kan dela med appar på den ohanterade delen av enheten.

- **Arbetsprofilmeddelanden när enheten är låst**: Styr om appar i arbetsprofilen får visa data i meddelanden när enheten är låst.
- **Standardbehörigheter för app**: Anger principen för standardbehörighet för alla appar i arbetsprofilen. Från och med Android 6, måste användaren bevilja vissa behörigheter som krävs av appar när appen startas. Den här principinställningen låter dig välja om användare ombeds att bevilja behörigheter för alla appar i arbetsprofilen. Om du till exempel tilldelar en app i arbetsprofilen som kräver platsåtkomst. Normalt skulle den appen be användaren att godkänna eller neka platsåtkomst för appen. Med den här principen kan du avgöra om alla behörigheter ska beviljas automatiskt utan att användaren tillfrågas, nekas automatiskt utan att användaren tillfrågas eller låta användaren bestämma. Välj mellan:
  - **Standard för enheten**
  - **Fråga**
  - **Bevilja automatiskt**
  - **Neka automatiskt**

    Bevilja-tillstånd för behörigheter kan definieras ytterligare för specifika appar, genom att använda en princip för appkonfiguration för en enskild app (under **Mobilappar** > **Appkonfigurationsprinciper**).

- **Lägga till och ta bort konton**

   Hindrar slutanvändare från att lägga till eller ta bort konton manuellt i arbetsprofilen.

   När du till exempel distribuerar Gmail-appen till en Android for Work-profil kan du hindra slutanvändare från att lägga till eller ta bort konton i arbetsprofilen.

- **Kontaktdelning via Bluetooth**: Ger åtkomst till arbetskontakter från en annan enhet, till exempel en bil som har anslutits med Bluetooth. Den här inställningen konfigureras inte som standard och arbetsprofilens kontakter visas därför inte. Välj **Aktivera** för att tillåta denna delning och visa arbetsprofilens kontakter. Inställningen gäller för Androids arbetsprofilenheter i Android OS v6.0 och senare. Genom att aktivera det här kan vissa Bluetooth-enheter tillåtas cache-lagra arbetskontakter vid första anslutningen. Att inaktiverar den här principen efter en inledande länkning/synkronisering kanske inte kan ta bort arbetskontakter från en bluetooth-enhet.

- **Skärmdump**: Blockerar skärmdumpen på enheten i arbetsprofilen. Förhindrar också att innehållet visas på visningsenheter som inte har en säker videoutgång.

- **Visa arbetskontaktens nummerpresentation i personlig profil**: När alternativet aktiverats (inte konfigurerats) visas arbetskontaktens nummerpresentation i den personliga profilen. När blockerad, visas inte arbetskontaktens nummerpresentation i den personliga profilen. Gäller Android OS v6.0 och nyare versioner.

- **Kamera**: Blockerar kameran på enheten i arbetsprofilen. Kameran på den personliga sidan påverkas inte av inställningen.

### <a name="work-profile-password"></a>Lösenord för arbetsprofilen

- **Kräv lösenord för arbetsprofil**: Gäller för Android 7.0 och senare med arbetsprofil aktiverad. Definiera en lösenordsprincip som endast gäller för apparna i arbetsprofilen. Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera PIN-koderna till den starkaste av de två.
- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**16**)
- **Maximalt antal minuter av inaktivitet innan arbetsprofilen låses**: Välj efter hur lång tid arbetsprofilen ska låsas. Därefter måste användaren ange sina autentiseringsuppgifter för att få åtkomst igen.
- **Antal felaktiga inloggningar innan enheten rensas**: Ange hur många gånger ett felaktigt lösenord kan anges innan arbetsprofilen rensas från enheten.
- **Lösenordets giltighetstid (dagar)**: Ange antal dagar innan användarens lösenord måste ändras (från **1**-**255**).
- **Krav på lösenordstyp**: Välj den typ av lösenord som måste anges på enheten. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck**: Blockerar slutanvändare från att använda enhetens fingeravtrycksläsare för att låsa upp den
- **Smart Lock och andra betrodda agenter**: Styr Smart Lock-funktionen på kompatibla enheter. Den här telefonfunktionen, som ibland kallas förtroendeagent, gör det möjligt att inaktivera eller kringgå lösenordet för arbetsprofilen om enheten är på en betrodd plats. Till exempel när enheten är ansluten till en specifik bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

## <a name="device-password"></a>Enhetslösenord

- **Minsta längd på lösenord**: Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**14**)
- **Maximalt antal minuter av inaktivitet tills skärmen låses**: Välj hur lång tid det tar innan en inaktiv enhet låses automatiskt
- **Antal felaktiga inloggningar innan enheten rensas**: Ange hur många gånger ett felaktigt lösenord kan anges innan alla data rensas från enheten
- **Lösenordets giltighetstid (dagar)**: Ange antal dagar innan användarens lösenord måste ändras (från **1**-**255**)
- **Krav på lösenordstyp**: Välj den typ av lösenord som måste anges på enheten. Välj mellan:
  - **Standard för enheten**
  - **Låg säkerhetsbiometri**
  - **Obligatoriskt**
  - **Minst numeriskt**
  - **Numeriskt avancerat**: Upprepande eller efterföljande siffror som ”1111” eller ”1234” tillåts inte
  - **Minst alfabetiskt**
  - **Minst alfanumeriskt**
  - **Minst alfanumeriskt med symboler**
- **Förhindra återanvändning av tidigare lösenord**: Ange hur många nya lösenord som måste ha använts innan ett gammalt kan återanvändas (från **1**-**24**).
- **Upplåsning med fingeravtryck**: Blockerar slutanvändare från att använda enhetens fingeravtrycksläsare för att låsa upp den
- **Smart Lock och andra betrodda agenter**: Styr Smart Lock-funktionen på kompatibla enheter. Den här telefonfunktionen, som ibland kallas förtroendeagent, låter dig inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats. Till exempel när enheten är ansluten till en specifik bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

## <a name="system-security"></a>Systemsäkerhet

- **Hotgenomsökning för appar**: Se till att inställningen för **Verifiera appar** är aktiverad för arbetsprofiler och personliga profiler.

   > [!Note]
   > Den här inställningen fungerar endast för Android O-enheter och senare.

## <a name="next-step"></a>Nästa steg

Om du vill spara och tilldela profilen till användare och enheter kan du läsa [Konfigurera inställningar för enhetsbegränsningar](device-restrictions-configure.md).
