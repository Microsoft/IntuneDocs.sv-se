---
title: Enhetsbegränsningar för Android-arbetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: Du kan begränsa vissa inställningar på Android-företagsprofilenheter, inklusive inställningar för att kopiera och klistra in, visa aviseringar, dela data, använda fingeravtryck för upplåsning, samt för appbehörigheter, lösenordslängd, inloggningsfel, återanvändning av lösenord och aktivering av Bluetooth-delning för arbetskontakter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d6a633b73856b5f9f50ffe0b9993713b888b969b
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828150"
---
# <a name="work-device-restriction-settings-in-intune"></a>Inställning av enhetsbegränsningar för arbetsenheter i Intune

I den här artikeln beskrivs alla begränsningsinställningar för Microsoft Intune-enheter som du kan konfigurera för Android-företagsprofilenheter.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Inställningar för arbetsprofil

### <a name="general-settings"></a>Allmänna inställningar

- **Kopiera och klistra in mellan arbetsprofiler och personliga profiler**: Styr kopiera och klistra in mellan arbetsappar och personliga appar. Aktivera blockering genom att välja **Blockera**. Välj **Inte konfigurerad** för att inaktivera blockering.
- **Datadelning mellan arbetsprofiler och personliga profiler**: Styr om appar i arbetsprofilen ska kunna dela med appar i den personliga profilen. Den här inställningen styr delningsåtgärder i program, till exempel alternativet **Dela** i Chrome-webbläsarappen. Den här inställningen gäller inte för kopierings- och inklistringsbeteendet i Urklipp. Till skillnad från [principinställningarna för appskydd](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) hanteras inställningarna för enhetsbegränsning från Intune-portalen och använder partitionen för Android-arbetsprofilen för att isolera hanterade appar. Välj mellan:
  - **Standardbegränsningar för delning**: Detta är standardinställningen för delning av enheten, vilket varierar beroende på Android-version. Som standard tillåts delning från den personliga profilen till arbetsprofilen. Som standard är dessutom delning mellan arbetsprofilen och den personliga profilen blockerad. Den här inställningen förhindrar att arbetsdata delas till den personliga profilen. För enheter som kör version 6.0 och senare blockerar inte Google delning från den personliga profilen till arbetsprofilen.
  - **Appar i arbetsprofilen kan hantera delningsförfrågningar från personlig profil**: Aktiverar den inbyggda Android-funktionen som tillåter delning från den personliga profilen till arbetsprofilen. När detta är aktiverat, kan en delningsbegäran från en app i den personliga profilen dela med appar i arbetsprofilen. Det här är standardinställningen för Android-enheter som kör tidigare versioner än 6.0.
  - **Tillåt delning över gränser**: Aktiverar delning över arbetsprofilgränsen i bägge riktningarna. När du väljer den här inställningen så kommer appar i arbetsprofilen att kunna dela data med omärkta appar i den personliga profilen. Med den här inställningen kan hanterade appar i arbetsprofilen dela med appar på den ohanterade delen av enheten. Använd därför den här inställningen med försiktighet.

- **Arbetsprofilmeddelanden när enheten är låst**: Styr om appar i arbetsprofilen får visa data i meddelanden när enheten är låst.
- **Standardbehörigheter för app**: Anger principen för standardbehörighet för alla appar i arbetsprofilen. Från och med Android 6, måste användaren bevilja vissa behörigheter som krävs av appar när appen startas. Den här principinställningen låter dig välja om användare ombeds att bevilja behörigheter för alla appar i arbetsprofilen. Om du till exempel tilldelar en app i arbetsprofilen som kräver platsåtkomst. Normalt skulle den appen be användaren att godkänna eller neka platsåtkomst för appen. Använd den här principen för att automatiskt bevilja behörigheter utan att användaren tillfrågas, för att automatiskt neka behörigheter utan att användaren tillfrågas eller för att låta användaren bestämma. Välj mellan:
  - **Standard för enheten**
  - **Fråga**
  - **Bevilja automatiskt**
  - **Neka automatiskt**

    Du kan också använda en appkonfigurationsprincip för att bevilja behörigheter för enskilda appar (**Klientappar** > **Appkonfigurationsprinciper**).

- **Lägga till och ta bort konton**

   Hindrar slutanvändare från att lägga till eller ta bort konton manuellt i arbetsprofilen.

   När du till exempel distribuerar Gmail-appen till en Android-arbetsprofil kan du hindra slutanvändare från att lägga till eller ta bort konton i arbetsprofilen.

- **Kontaktdelning via Bluetooth**: Ger åtkomst till arbetskontakter från en annan enhet, till exempel en bil som har anslutits med Bluetooth. Den här inställningen konfigureras inte som standard och arbetsprofilens kontakter visas därför inte. Välj **Aktivera** för att tillåta denna delning och visa arbetsprofilens kontakter. Inställningen gäller för Androids arbetsprofilenheter i Android OS v6.0 och senare. När den här inställningen är aktiverad kan vissa Bluetooth-enheter tillåtas att cachelagra arbetskontakter vid den första anslutningen. Att inaktiverar den här principen efter en inledande länkning/synkronisering kanske inte kan ta bort arbetskontakter från en bluetooth-enhet.

- **Skärmdump**: Blockerar skärmdumpen på enheten i arbetsprofilen. Förhindrar också att innehållet visas på visningsenheter som inte har en säker videoutgång.

- **Visa arbetskontaktens nummerpresentation i personlig profil**: När alternativet aktiverats (inte konfigurerats) visas arbetskontaktens nummerpresentation i den personliga profilen. När det är blockerat visas inte arbetskontaktens nummerpresentation i den personliga profilen. Gäller Android OS v6.0 och nyare versioner.

- **Kamera**: Blockerar kameran på enheten i arbetsprofilen. Kameran på den personliga sidan påverkas inte av inställningen.

### <a name="work-profile-password"></a>Lösenord för arbetsprofilen

- **Kräv lösenord för arbetsprofil**: Gäller för Android 7.0 och senare med arbetsprofil aktiverad. Definiera en lösenordsprincip som endast gäller för apparna i arbetsprofilen. Användaren kan som standard välja att använda två separat definierade PIN-koder, eller välja att kombinera PIN-koderna till den starkaste av de två.
- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**16**).
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
- **Smart Lock och andra betrodda agenter**: Styr Smart Lock-funktionen på kompatibla enheter. Den här telefonfunktionen, även kallad förtroendeagent, gör det möjligt att inaktivera eller kringgå lösenordet för arbetsprofilen om enheten finns på en betrodd plats. Du kan exempelvis kringgå lösenordet för arbetsprofilen när enheten är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

## <a name="device-password"></a>Enhetslösenord

- **Minsta lösenordslängd**: Ange det minsta antal tecken som användarens lösenord måste innehålla (från **4**-**14**).
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
- **Smart Lock och andra betrodda agenter**: Styr Smart Lock-funktionen på kompatibla enheter. Med den här telefonfunktionen, även kallad förtroendeagent, kan du inaktivera eller kringgå lösenordet för enhetens låsskärm om enheten finns på en betrodd plats. Du kan exempelvis kringgå lösenordet för arbetsprofilen när enheten är ansluten till en specifik Bluetooth-enhet eller när den är nära en NFC-tagg. Använd den här inställningen för att förhindra att användare konfigurerar Smart Lock.

## <a name="system-security"></a>Systemsäkerhet

- **Hotgenomsökning för appar**: Se till att inställningen för **Verifiera appar** är aktiverad för arbetsprofiler och personliga profiler.

   > [!Note]
   > Den här inställningen fungerar endast för Android O-enheter och senare.

## <a name="connectivity"></a>Anslutning

- **Always-on VPN (Alltid aktivt VPN)**: Välj **Aktivera** om du vill konfigurera en VPN-klient att automatiskt ansluta och återansluta till VPN. VPN-anslutningar som alltid är aktiva är alltid anslutna eller ansluter direkt när användaren låser sin enhet, när enheten startas om eller när det trådlösa nätverket ändras. 

  Välj **Inte konfigurerad** om du inte vill att VPN-anslutningarna alltid ska vara aktiva. Inställningen tillämpas på alla VPN-klienter. 

  > [!IMPORTANT]
  > Var noga med att endast distribuera en princip för VPN som alltid är aktivt för en enskild enhet. Det går inte att distribuera flera principer av den här typen till en enskild enhet.

- **VPN-klient**: Välj en VPN-klient som stöder VPN-anslutningar som alltid är aktiva. Alternativen är:
  - Cisco AnyConnect
  - F5 Access
  - Palo Alto Networks GlobalProtect
  - Pulse Secure
  - Anpassad
    - **Paket-ID**: Ange paket-ID:t för appen i Google Play Store. Om URL:en för appen i Google Play Store exempelvis är `https://play.google.com/store/details?id=com.contosovpn.android.prod` är paket-ID:t `com.contosovpn.android.prod`.

    > [!IMPORTANT]
    >  - Den VPN-klient som du väljer måste vara installerad på enheten och den måste ha stöd för ”per app-VPN” i arbetsprofiler. Annars uppstår ett fel. 
    >  - Du måste godkänna VPN-klientappen i **den hanterade Google Play Store-butiken**, synkronisera appen till Intune och distribuera appen till enheten. När du har gjort det installeras appen i användarens arbetsprofil.

- **Låsningsläge**: **Aktivera** om du vill tvinga all nätverkstrafik att använda VPN-tunneln. Om en anslutning till VPN inte upprättas har inte enheten åtkomst till nätverket.

  Välj **Inte konfigurerad** om du vill tillåta att trafik flödar via VPN-tunneln eller det mobila nätverket.

## <a name="next-step"></a>Nästa steg

[Tilldela profiler](device-profile-assign.md) till användare och enheter.
