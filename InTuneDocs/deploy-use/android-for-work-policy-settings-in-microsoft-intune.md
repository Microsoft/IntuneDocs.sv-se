---

title: "Principinställningar för Android for Work | Microsoft Intune"
description: "Skapa principer som styr inställningar och funktioner på Android for Work-enheter som du hanterar med Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 748b9b74b65e8d17bb3956d0ce1859c160d8c10a


---

# <a name="android-for-work-policy-settings-in-microsoft-intune"></a>Principinställningar för Android for Work i Microsoft Intune

[!INCLUDE[wit_nextref](../includes/afw_rollout_disclaimer.md)]

I Intune finns en uppsättning inbyggda allmänna inställningar som du kan konfigurera i Android for Work-enheter.

## <a name="general-configuration-policy"></a>Allmän konfigurationsprincip

Använd Intunes **allmänna konfigurationsprincip för Android for Work** för att konfigurera inställningar för säkerhet och arbetsprofiler för dina Android for Work-enheter.

Om den inställning som du söker efter inte visas i det här avsnittet kan du skapa den med hjälp av en anpassad Android-princip med vilken du kan använda OMA-URI-inställningar för att styra enheten. Mer information finns i [Anpassade principinställningar](#custom-policy-settings) senare i det här avsnittet.

> [!TIP]
> Enheter krypteras automatiskt när du etablerar en arbetsprofil. Du kan inte ändra den här inställningen.

### <a name="password-settings"></a>Inställningar för lösenord

|Inställningsnamn|Information|
|----------------|-|
|**Kräv ett lösenord för att låsa upp mobila enheter**|Anger om ett lösenord krävs på enheter som hanteras. Välj mellan:<br><br>- **Komplex** – kräver minst en bokstav, en siffra och en symbol<br>- **Alfanumerisk** – kräver minst en siffra och ett alfabetiskt tecken<br>- **Alfabetiskt** – kräver minst bokstäver eller symboler<br>- **Numerisk komplex** – kräver numeriska tecken som inte upprepas eller är i följd<br>- **Numerisk**<br><br>Om den här inställningen inte är aktiverad finns det inga krav på komplexitet.|
|**Minsta längd på lösenord**|Anger det minsta antalet tecken eller siffror som lösenordet måste innehålla.|
|**Minuter av inaktivitet innan enheten låses**|Anger antalet minuter utan användaraktivitet innan enheten låses automatiskt.|
|**Tillåt Smart Lock och andra betrodda agenter**<br>(Android 6 och senare)|Gör att du kan styra Smart Lock-funktionen i kompatibla Android-enheter. Med den här telefonfunktionen, som ibland kallas förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten är på en betrodd plats, till exempel när det är anslutet till en specifik bluetoothenhet eller när den är nära en NFC-tagg. Du kan använda den här inställningen för att förhindra att användare konfigurerar Smart Lock.|
|**Antal tillåtna upprepade felinloggningar innan arbetsprofilen tas bort**|Anger antalet tillåtna felinloggningar innan arbetsprofilen på enheten tas bort. En fullständig enhetsrensning utförs inte.|
|**Kom ihåg tidigare lösenord**|Hindrar återanvändning av lösenord som har använts tidigare.|
|**Spara lösenordshistorik** - **Förhindra återanvändning av tidigare lösenord **|Anger antalet lösenord som har använts tidigare som ska sparas.|
|**Lösenordets giltighetstid (i dagar)**|Anger antalet dagar innan lösenordet måste ändras.|
|**Tillåt fingeravtrycksupplåsning**<br>(Android 6 och senare)|Låter dig använda ett fingeravtryck för att låsa upp enheter med den här funktionen.|


### <a name="work-profile-settings"></a>Inställningar för arbetsprofil

|Inställningsnamn|Information|
|----------------|-|
|**Tillåt datadelning mellan arbetsprofiler och personliga profiler**|Låter appar i arbetsprofilen att dela data med appar i användarens personliga profil. Välj mellan:<br><br>- **Förhindra all delning över gränser**<br>- **Appar i arbetsprofilen kan hantera delningsförfrågningar från den personliga profilen**<br>- **Inga delningsbegränsningar**|
|**Dölj arbetsprofilaviseringar när enheten är låst**<br>(Android 6 och senare)|Kontrollera om du vill visa några meddelanden från arbetsprofilen när enheten är låst.|
|**Ange standardprincipen för behörigheter för appar**<br>(Android 6 och senare)|Ange standardprincipen för behörighet för alla appar i arbetsprofilen.|




## <a name="custom-policy-settings"></a>Anpassade principinställningar
Använd **Anpassad konfigurationsprincip för Android for Work** i Microsoft Intune för att distribuera OMA-URI-inställningar som kan användas till att styra funktioner på Android for Work-enheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna distribuera Android-inställningar som inte går att konfigurera med Intune-principer.

> [!NOTE]
> För närvarande stöder de anpassade Android-principerna enbart konfiguration av Wi-Fi-inställningar i Android-enheter som innehåller en i förväg delad nyckel.

### <a name="general-settings"></a>Allmänna inställningar

|Inställningsnamn|Information|
    |----------------|--------------------|
    |**Namn**|Ange ett unikt namn för den anpassade Android-principen som hjälper dig att identifiera den i Intune-konsolen.|
    |**Beskrivning**|Ange en beskrivning med en översikt av den anpassade Android-principen och annan information som gör det enkelt att hitta den.|

### <a name="oma-uri-settings"></a>OMA-URI-inställningar

   |Inställningsnamn|Information|
    |--------|--------------------|
    |**Namn**|Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.|
    |**Beskrivning av inställning**|Tillhandahåll en beskrivning som ger en översikt över inställningen och annan relevant information som gör det enkelt att hitta den.|
    |**Datatyp**|Ange den datumtyp med vilken du vill specificera den här OMA-URI-inställningen. Välj **sträng, sträng (XML), datum och tid, heltal, flyttal** eller **booleskt**.|
    |**OMA-URI (skiftlägeskänslig)**|Ange den OMA-URI som du vill tillhandahålla en inställning för.|
    |**Värde**|Ange det värde som ska associeras med den OMA-URI som du tidigare angav.|

### <a name="examples"></a>Exempel

- [Skapa en Wi-Fi-profil med en i förväg delad nyckel](pre-shared-key-wi-fi-profile.md)
- [Använda en anpassad princip för att skapa en VPN-profil per app för Android-enheter](per-app-vpn-for-android-pulse-secure.md)

### <a name="see-also"></a>Se även
[Hantera inställningar och funktioner på dina enheter med Microsoft Intune-principer](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO1-->


