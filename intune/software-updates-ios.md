---
title: Konfigurera uppdateringsprinciper för iOS-programvara i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune skapar du eller lägger till en konfigurationsprincip för att begränsa när programvaruuppdateringar installeras automatiskt på iOS-enheter som hanteras eller övervakas av Intune. Du kan välja datum och tid när uppdateringar inte installeras. Du kan även tilldela den här principen till grupper, användare eller enheter samt söka efter eventuella installationsfel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a5c9dea847ace51c7d6f06cfa43c44beead18f8
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66373422"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Lägga till principer för iOS-programuppdatering i Intune

Med programvaruuppdateringsprinciper kan du tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen för operativsystemet. När du konfigurerar en princip kan du lägga till de dagar och tider då du inte vill att enheter installerar en uppdatering. 

Den här funktionen gäller för:

- iOS 10.3 och senare (övervakade enheter)

Enheten checkar in med Intune ungefär var 8:e timme. Om en uppdatering är tillgänglig och den aktuella tiden inte är en begränsad tid laddar enheten ned och installerar den senaste uppdateringen för operativsystemet. Det krävs inga användaråtgärder för att uppdatera enheten. Principen förhindrar inte att en användare uppdaterar operativsystemet manuellt.

## <a name="configure-the-policy"></a>Konfigurera principen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Programuppdateringar** > **Uppdateringsprinciper för iOS** > **Skapa**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för principen för programuppdatering. Ange till exempel `iOS restricted update times`.
    - **Beskrivning**: Ange en beskrivning av principen. Denna inställning är valfri, men rekommenderas.

4. Välj **Inställningar > Konfigurera**. Ange följande inställningar:

    - **Välj tidpunkter för att förhindra installationer av uppdateringar**: Ange en begränsad tidsram när uppdateringar inte installeras med tvång. 
      - Blockeringar över natten stöds inte och fungerar kanske inte. Till exempel bör du inte konfigurera en princip med en *Starttid* kl. 20:00 och en *Sluttid* på kl. 06:00.
      - En princip som börjar vid kl. 12:00 och slutar kl. 12:00 tolkas som 0 timmar, inte 24 timmar, vilket innebär att det inte finns någon begränsning.

      När du konfigurerar den begränsade tidsramen anger du följande uppgifter:

      - **Dagar**: Välj de veckodagar då uppdateringar inte installeras. Markera till exempel måndag, onsdag och fredag om du vill förhindra att uppdateringar installeras på de dagarna.
      - **Tidzon**: Välj en tidszon.
      - **Starttid**: Välj starttiden för den begränsade tidsramen. Ange till exempel kl. 05:00 så att uppdateringar inte börjar installeras kl. 05:00.
      - **Sluttid**: Välj sluttiden för den begränsade tidsramen. Ange till exempel kl. 01:00 så att uppdateringar kan börja installeras från kl. 01:00.

    - **Fördröj synligheten för programuppdateringar för slutanvändare utan ändring av schemalagda uppdateringar (dagar)** : 

      **Den här inställningen har flyttats till [Enhetsbegränsningar](device-restrictions-ios.md#general). Den kommer att tas bort från den här platsen i portalen**. Under en kort period kan befintliga principer ändras här. Efter ungefär en månad tas den här inställningen bort från befintliga principer.

      Vi rekommenderar följande för att begränsa påverkan:
        - Ta bort den befintliga principen från den här platsen i portalen.
        - Skapa en ny [princip för enhetsbegränsning](device-restrictions-ios.md#general).
        - Ha samma användare som mål som den ursprungliga principen hade.

      Om det finns en konflikt gör den här inställningen ingenting *såvida inte* de två värdena är identiska. För att förhindra konflikt bör du ändra eller ta bort den befintliga principen från den här platsen i portalen.
      > [! Viktigt]  
      > En princip som har en *Starttid* och en *Sluttid* på 12:00 tolkas som 0 timmar och inte som 24 timmar. Detta resulterar i att det inte blir någon begränsning.  

5. Välj **OK** > **Skapa** för att spara ändringarna och skapa principen.

Profilen skapas och visas i principlistan.

Vägledning från Intune-supportteamet finns i [Fördröj synligheten för programvaruuppdateringar i Intune för övervakade enheter](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Apple MDM tillåter inte att du tvingar en enhet att installera uppdateringar en viss tid eller ett visst datum.

## <a name="change-the-restricted-times-for-the-policy"></a>Ändra begränsade tider för principen

1. I **Programuppdateringar** väljer du **Uppdateringsprinciper för iOS**.
2. Välj en befintlig princip > **Egenskaper**.
3. Uppdatera den begränsade tiden:

    1. Välj veckodagar
    2. Välj den tidszon som den här principen tillämpas i
    3. Ange start- och sluttid för svartlistade timmar

    > [!NOTE]
    > Om **Starttid** och **Sluttid** båda anges till kl. 12:00 kontrollerar inte Intune om det finns begränsningar för när uppdateringar får installeras. Det innebär att alla konfigurationer som du har för **Välj tidpunkter för att förhindra installationer av uppdateringar** ignoreras och att uppdateringar kan installeras när som helst.  

## <a name="assign-the-policy-to-users"></a>Tilldela principen till användare

Befintliga principer tilldelas till grupper, användare eller enheter. När de tilldelas tillämpas principen.

1. I **Programuppdateringar** väljer du **Uppdateringsprinciper för iOS**.
2. Välj en befintlig princip > **Tilldelningar**. 
3. Välj de Azure Active Directory-grupper, -användare eller -enheter som ska inkluderas eller exkluderas från den här principen.
4. Välj **Spara** om du vill distribuera principen till grupperna.

De enheter som används av de användare som den här principen inriktar sig på utvärderas för uppdateringsefterlevnad. Den här principen har även stöd för användarlösa enheter.

## <a name="monitor-device-installation-failures"></a>Övervaka enhetsinstallationsfel
<!-- 1352223 -->
**Programuppdateringar** > **Installationsfel för iOS-enheter** visar en lista över övervakade iOS-enheter som är mål för en uppdateringsprincip, försökte genomföra en uppdatering och inte kunde uppdateras. För varje enhet kan du se status om varför enheten inte har uppdaterats automatiskt. Felfria, uppdaterade enheter visas inte i listan. ”Uppdaterade” enheter innefattar den senaste uppdateringen som enheten själv har stöd för.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
