---
title: Konfigurera uppdateringsprinciper för iOS-programvara i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune skapar du eller lägger till en konfigurationsprincip för att begränsa när programvaruuppdateringar installeras automatiskt på iOS-enheter. Du kan välja datum och tid när uppdateringar inte installeras. Du kan även tilldela den här principen till grupper, användare eller enheter samt söka efter eventuella installationsfel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f9750603d19d9b19697c7d2660351c4586432f6
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984185"
---
# <a name="add-ios-software-update-policies-in-intune"></a>Lägga till principer för iOS-programuppdatering i Intune

Med programvaruuppdateringsprinciper kan du tvinga övervakade iOS-enheter att automatiskt installera den senaste tillgängliga uppdateringen för operativsystemet. När du konfigurerar en princip kan du lägga till de dagar och tider då du inte vill att enheter installerar en uppdatering.

Den här funktionen gäller för:

- iOS 10.3 och senare (övervakade enheter)

Enheten checkar in med Intune ungefär var 8:e timme. Om det finns en uppdatering tillgänglig laddar enheten ned och installerar den, förutom under begränsade tider. Normalt krävs ingen användarinteraktion under uppdateringsprocessen, men om enheten har ett lösenord måste användaren ange detta för att starta en programuppdatering. Detta gäller för iOS 10.3 och senare versioner. Principen förhindrar inte att en användare uppdaterar operativsystemet manuellt.

## <a name="configure-the-policy"></a>Konfigurera principen

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Programuppdateringar** > **Uppdateringsprinciper för iOS** > **Skapa**.
3. På fliken **Grundläggande** anger du ett namn för den här principen, anger en beskrivning och väljer **Nästa**.

   ![Fliken Grundläggande](./media/software-updates-ios/basics-tab.png) 

4. På fliken **Uppdatera principinställningar** anger du en begränsad tidsram när uppdateringar inte installeras med tvång.  
   - Blockeringar över natten stöds inte och fungerar kanske inte. Till exempel bör du inte konfigurera en princip med en *Starttid* kl. 20:00 och en *Sluttid* på kl. 06:00.
   - En princip som börjar kl. 12:00 och slutar kl. 12:00 tolkas som 0 timmar, inte 24 timmar. Den här konfigurationen resulterar i att det inte blir någon begränsning alls.

   När du konfigurerar den begränsade tidsramen anger du följande uppgifter:

   - **Dagar**: Välj de veckodagar då uppdateringar inte installeras. Markera till exempel måndag, onsdag och fredag om du vill förhindra att uppdateringar installeras på de dagarna.
   - **Tidzon**: Välj en tidszon.
   - **Starttid**: Välj starttiden för den begränsade tidsramen. Ange till exempel kl. 05:00 så att uppdateringar inte börjar installeras kl. 05:00.
   - **Sluttid**: Välj sluttiden för den begränsade tidsramen. Ange till exempel kl. 01:00 så att uppdateringar kan börja installeras från kl. 01:00.
  
   > [!IMPORTANT]  
   > En princip som har en *Starttid* och en *Sluttid* på 12:00 tolkas som 0 timmar och inte som 24 timmar. Detta resulterar i att det inte blir någon begränsning.  
    
   Om du vill fördröja programuppdateringars synlighet under en viss tid på dina övervakade iOS-enheter konfigurerar du de inställningarna i [Enhetsbegränsningar](../configuration/device-restrictions-ios.md#general). Principer för programuppdatering åsidosätter eventuella enhetsbegränsningar. När du anger både en princip för programuppdatering och en begränsning som fördröjer programuppdateringars synlighet framtvingar enheten en programuppdatering enligt principen. Begränsningen gäller så att användarna inte ser alternativet att själva uppdatera enheten, och uppdateringen överförs i den första tidsperioden enligt vad som definieras av din iOS-uppdateringsprincip.

   När du har konfigurerat *Inställningar för uppdateringsprincip* väljer du **Nästa**. 

5. På fliken **Omfångstaggar** väljer du **+ Välj omfångstaggar** för att öppna fönstret *Välj taggar* om du vill tillämpa dem på uppdateringsprincipen.
   
   - I fönstret **Välj taggar** väljer du en eller fler taggar och klickar sedan på **Välj** för att lägga till dem i principen och återgå till fönstret *Omfångstaggar*.  

   När du är klar väljer du **Nästa** för att fortsätta till *Tilldelningar*.

6. På fliken **Tilldelningar** väljer du **+ Välj grupper som ska inkluderas** och tilldelar sedan uppdateringsprincipen till en eller fler grupper. Använd **+ Välj grupper att utesluta** för att finjustera tilldelningen. När du är klar väljer du **Nästa** för att fortsätta. 

   De enheter som används av de användare som den här principen inriktar sig på utvärderas för uppdateringsefterlevnad. Den här principen har även stöd för användarlösa enheter.

7. På fliken **Granska och skapa** granskar du inställningarna och väljer **Skapa** när du är redo att spara din iOS-uppdateringsprincip. Den nya principen visas i listan över uppdateringsprinciper för iOS.


Vägledning från Intune-supportteamet finns i [Fördröj synligheten för programvaruuppdateringar i Intune för övervakade enheter](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Apple MDM tillåter inte att du tvingar en enhet att installera uppdateringar en viss tid eller ett visst datum.

## <a name="edit-a-policy"></a>Redigera en princip
Du kan redigera en befintlig princip, inklusive att ändra de begränsade tiderna:

1. I **Programuppdateringar** väljer du **Uppdateringsprinciper för iOS** och väljer sedan den princip som du vill redigera.

2. När du visar principernas **Egenskaper** väljer du **Redigera** för den principsida som du vill ändra.  
   ![Redigera en princip](./media/software-updates-ios/edit-policy.png)   

3. När du har infört en ändring väljer du **Granska och spara** > **Spara** för att spara ändringarna och återgår till principernas *Egenskaper*.  
 
> [!NOTE]
> Om **Starttid** och **Sluttid** båda anges till kl. 12:00 kontrollerar inte Intune om det finns begränsningar för när uppdateringar får installeras. Det innebär att alla konfigurationer som du har för **Välj tidpunkter för att förhindra installationer av uppdateringar** ignoreras och att uppdateringar kan installeras när som helst.  


## <a name="monitor-device-installation-failures"></a>Övervaka enhetsinstallationsfel
<!-- 1352223 -->
**Programuppdateringar** > **Installationsfel för iOS-enheter** visar en lista över övervakade iOS-enheter som är mål för en uppdateringsprincip, försökte genomföra en uppdatering och inte kunde uppdateras. För varje enhet kan du se status om varför enheten inte har uppdaterats automatiskt. Felfria, uppdaterade enheter visas inte i listan. ”Uppdaterade” enheter innefattar den senaste uppdateringen som enheten själv har stöd för.

## <a name="next-steps"></a>Nästa steg

[Övervaka dess status](../configuration/device-profile-monitor.md).
