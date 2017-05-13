---
title: "Inställningar av begränsningar i Intune-enheter för Android for Work | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om de Intune-inställningar du kan använda för att styra inställningar och funktioner på Android for Work-enheter."
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
ms.translationtype: Human Translation
ms.sourcegitcommit: f9e8a5deb17ebb77d480213567e5ccf6550e3493
ms.openlocfilehash: be6303f2db508c2aca9ba9a40fcd43278f83c045
ms.contentlocale: sv-se
ms.lasthandoff: 05/03/2017


---

# <a name="android-for-work-device-restriction-settings-in-microsoft-intune"></a>Inställningar av enhetsbegränsningar för Android for Work-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="work-profile-settings"></a>Inställningar för arbetsprofil
-     **Datadelning mellan arbetsprofiler och personliga profiler** – Använd den här inställningen för att styra om appar i arbetsprofilen ska kunna dela data med appar i den personliga profilen. Välj mellan:
    - **Standardbegränsningar för delning** – Detta är standardinställningen för delning av enheten, vilket varierar beroende på den version av Android den använder. Som standard tillåts delning från den personliga profilen till arbetsprofilen. Som standard är dessutom delning mellan arbetsprofilen och den personliga profilen blockerad. Detta förhindrar av data sprids från arbetet till den personliga profilen. Google kan inte blockera data från den personliga profilen till arbetsprofilen på enheter som kör tidigare versioner än 6.0.  
    - **Appar i arbetsprofilen kan hantera delningsförfrågningar från personlig profil** – Använd det här alternativet för att aktivera den inbyggda Android-funktionen som tillåter delning från den personliga profilen till arbetsprofilen. När detta är aktiverat kommer en delningsförfrågan som initieras från en app i den personliga profilen att kunna delas med appar i arbetsprofilen. Det här är standardinställningen för Android-enheter som kör tidigare versioner än 6.0.
    - **Appar i den personliga profilen kan hantera delningsförfrågningar från arbetsprofilen** – Aktiverar delning över arbetsprofilgränsen i båda riktningarna. När du väljer den här inställningen kan appar i arbetsprofilen dela data med appar som inte hanteras i den personliga profilen.  Använd den här inställningen med försiktighet. Den innebär att hanterade data i arbetsprofilen kan överföras till en sida av enheten som inte hanteras.


-     **Arbetsprofilmeddelanden när enheten är låst** – Styr om appar i arbetsprofilen kan visa meddelanden på skärmen när enheten är låst.
-     **Standardbehörigheter för app** – Anger principen för standardbehörighet för alla appar i arbetsprofilen. Från och med Android 6 visas behörigheter som krävs av appen för slutanvändaren vid körning. Med denna principinställning kan du bestämma hur eller om användarna ska uppmanas att bevilja behörighet för appar i arbetsprofilen.
Till exempel kan du tilldela en app till den arbetsprofil som kräver platsåtkomst. Vanligtvis visas en dialogruta i appen som frågar användaren om denne vill ge platsåtkomst till appen, varpå användaren kan godkänna eller avvisa detta. Med den här principen kan du avgöra om alla behörigheter ska beviljas automatiskt utan att användaren tillfrågas, nekas automatiskt utan att användaren tillfrågas eller låta användaren bestämma. Välj mellan:
    -     **Standard för enheten**
    -     **Fråga**
    -     **Bevilja automatiskt**
    -     **Neka automatiskt**

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

## <a name="custom-policy-settings"></a>Anpassade principinställningar
Använd **Anpassad konfigurationsprincip för Android for Work** i Microsoft Intune för att tilldela OMA-URI-inställningar som kan användas till att styra funktioner på Android for Work-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela Android-inställningar som inte går att konfigurera med Intune-principer.
Intune har för närvarande stöd för ett begränsat antal anpassade Android-principer. Se exemplen i det här avsnittet för att ta reda på vilka principer du kan konfigurera.

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn** |Ange ett unikt namn för den anpassade Android-principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning** |Ange en beskrivning med en översikt av den anpassade Android-principen och annan information som gör det enkelt att hitta den.|

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

  |Inställningsnamn|Information|
  |--------|--------------------|
  |**Namn** |Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
  |**Beskrivning** |Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**OMA-URI (skiftlägeskänslig)** |Ange den OMA-URI som du vill tillhandahålla en inställning för.|
  |**Datatyp** |Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj **sträng, sträng (XML), datum och tid, heltal, flyttal** eller **booleskt**.|
  |**Värde** |Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

