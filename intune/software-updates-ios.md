---
title: Konfigurera uppdateringsprinciper för iOS-programvara i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune skapar du eller lägger till en konfigurationsprincip för att begränsa när programvaruuppdateringar installeras automatiskt på iOS-enheter som hanteras eller övervakas av Intune. Du kan välja datum och tid när uppdateringar inte installeras. Du kan även tilldela den här principen till grupper, användare eller enheter samt söka efter eventuella installationsfel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cce77976ea0cb31596ca0a1fd6c4becc9e3cee34
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833607"
---
# <a name="configure-ios-update-policies-in-intune"></a>Konfigurera iOS-uppdateringsprinciper i Intune

Med programvaruuppdateringsprinciper kan du tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen för operativsystemet. Den här funktionen är endast tillgänglig för övervakade enheter. När du konfigurerar en princip kan du lägga till de dagar och tider då du inte vill att enheter installerar en uppdatering. 

Enheten checkar in med Intune ungefär var 8:e timme. Om en uppdatering är tillgänglig och den aktuella tiden inte är en begränsad tid laddar enheten ned och installerar den senaste uppdateringen för operativsystemet. Det krävs inga användaråtgärder för att uppdatera enheten. Principen förhindrar inte att en användare uppdaterar operativsystemet manuellt.

Den här funktionen stöder enheter som kör iOS 10.3 och senare versioner. Fördröjningsinställningen är tillgänglig i iOS 11.3 och senare versioner.

## <a name="configure-the-policy"></a>Konfigurera principen
1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Programuppdateringar** > **Uppdateringsprinciper för iOS** > **Skapa**.
4. Ange ett namn och en beskrivning för principen.
5. Välj **Inställningar**. 

    Ange information om när iOS-enheter inte ska tvingas att installera de senaste uppdateringarna. Dessa inställningar skapar en begränsad tidsram. Du kan konfigurera **Dagar** i veckan, **Tidszon**, **Starttid**, **Sluttid** och **Fördröj visning av programuppdateringar (dagar)** för att ange användare. Du kan välja en fördröjningstid för programuppdateringar från 1 till 90 dagar. När fördröjningen upphör får användarna ett meddelande om att uppdatera till den tidigaste versionen av OS som var tillgänglig när fördröjningen utlöstes. Om du inte vill ställa in en fördröjningstid för programuppdatering anger du 0. De här uppdateringsinställningarna gäller endast övervakade iOS-enheter.
  
    Exempel: Om iOS 12.a är tillgänglig den **1 januari** och du har **fördröjning av OS-uppdateringar** inställt på **5 dagar** visas inte den versionen som en tillgänglig uppdateringar på några slutanvändarenheter tilldelade till den profilen. På den **sjätte dagen** efter utgivningen visas den uppdateringen som tillgänglig och alla slutanvändare kan starta en uppdatering.


6. Klicka på **OK** för att spara ändringarna. Välj **Skapa** för att skapa principen.

Profilen skapas och visas i principlistan. Apple MDM tillåter inte att du tvingar en enhet att installera uppdateringar en viss tid eller ett visst datum. 

## <a name="change-the-restricted-times-for-the-policy"></a>Ändra begränsade tider för principen

1. I **Programuppdateringar** väljer du **Uppdateringsprinciper för iOS**.
2. Välj en befintlig princip > **Egenskaper**.
3. Uppdatera den begränsade tiden:
    
    1. Välj veckodagar
    2. Välj den tidszon som den här principen tillämpas i
    3. Ange start- och sluttid för svartlistade timmar

    > [!NOTE]
    > Om **starttiden** och **sluttiden** båda anges till 12:00 stängs tidskontrollen för underhåll av.

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

