---
title: Selektiv rensning av data med åtkomståtgärder för appskyddsprinciper
titleSuffix: Microsoft Intune
description: Lär dig hur du selektivt rensar data med åtkomståtgärder för appskyddsprinciper i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2cfd426a0ae7165a7aae60a90d104852fd834db6
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37909124"
---
# <a name="selectively-wipe-data-using-app-protection-policy-access-actions-in-intune"></a>Selektiv rensning av data med åtkomståtgärder för appskyddsprinciper i Intune

Med Intune-appskyddsprinciper kan du konfigurera inställningar för att blockera slutanvändare från att komma åt en företagsapp eller ett företagskonto. Dessa inställningar riktar in sig på dataförflyttning och åtkomstkrav som anges av organisationen för sådant som jailbroken enheter och minsta OS-versioner.
 
Du kan uttryckligen välja att rensa ditt företags data från slutanvändarens enhet som en åtgärd att vidta för icke-kompatibilitet genom att använda dessa inställningar. För vissa inställningar kan du konfigurera flera åtgärder, till exempel blockera åtkomst och rensa data utifrån olika angivna värden.

## <a name="create-an-app-protection-policy-using-access-actions"></a>Skapa en appskyddsprincip med åtkomståtgärder

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**.  
    Intune finns i avsnittet **Övervakning och hantering**.
3. I **Intune**-fönstret väljer du **Mobilappar** > **Principer för appskydd**.
4. Klicka på **Lägg till en princip** (du kan även redigera en befintlig princip). 
5. Klicka på **Konfigurera obligatoriska inställningar** för att se listan över inställningar tillgängliga för konfiguration för principen. 
6. När du rullar ned i fönstret **Inställningar** visas avsnittet **Åtkomståtgärder** med en redigerbar tabell.

    ![Skärmbild av åtkomståtgärder för Intune-appskydd](./media/apps-selective-wipe-access-actions01.png)

7. Välj en **inställning** och ange det **värde** som användare måste uppfylla för att logga in på företagsappen. 
8. Välj den **åtgärd** du vill vidta att om användarna inte uppfyller dina krav. I vissa fall kan flera åtgärder konfigureras för en och samma inställning. Mer information finns i [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md).

>[!NOTE]
> Om du vill använda inställningen **Enhetsmodell(er)** anger du en semikolonavgränsad lista över modell-ID:n. 

## <a name="policy-settings"></a>Principinställningar 

Tabellen över inställningar för appskyddsprinciper har kolumner för **Inställning**, **Värde** och **Åtgärd**.

För iOS kan du konfigurera åtgärder för följande inställningar med hjälp av listrutan **Inställning**:
-  Högsta antal PIN-försök
-  Offline-respitperiod
-  Jailbrokade/rotade enheter
-  Lägsta operativsystemversion
-  Lägsta appversion
-  Lägsta SDK-version
-  Enhetsmodell(er)

För Android kan du konfigurera åtgärder för följande inställningar med hjälp av listrutan **Inställning**:
-  Högsta antal PIN-försök
-  Offline-respitperiod
-  Jailbrokade/rotade enheter
-  Lägsta operativsystemversion
-  Lägsta appversion
-  Lägsta korrigeringsversion
-  Enhetstillverkare

Som standard har tabellen ifyllda rader som inställningar konfigurerade för **Offlinerespittid** och **Högsta antal PIN-försök** om inställningen **Kräv PIN-kod för åtkomst** är inställd på **Ja**.
 
Om du vill konfigurera en inställning väljer du en inställning i listrutan under kolumnen **Inställning**. När en inställning har valts aktiveras den redigerbara textrutan under kolumnen **Värde** på amma rad, om ett värde måste anges. Dessutom aktiveras listrutan under kolumnen **Åtgärd** med de villkorsstyrda startåtgärder som gäller för inställningen. 

Följande lista innehåller den vanliga listan över åtgärder:
-  **Blockera åtkomst** – blockera användaren från att komma åt företagsappen.
-  **Rensa data** – rensa företagsdata från slutanvändarens enhet.
-  **Varna** – ange dialogruta till slutanvändaren som ett varningsmeddelande.

### <a name="additional-settings-and-actions"></a>Ytterligare inställningar och åtgärder 

I vissa fall, till exempel inställningen **Lägsta operativsystemversion**, kan du konfigurera inställningen för att utföra alla tillämpliga åtgärder baserat på olika versionsnummer. 

![Skärmbild av åtkomståtgärder för Intune-appskydd – Lägsta operativsystemversion](./media/apps-selective-wipe-access-actions05.png)

När en inställning konfigureras fullständigt visas raden i en skrivskyddad vy och är tillgänglig att redigeras när som helst. Dessutom har raden en tillgänglig listruta för val i kolumnen **Inställning**. Inställningar som redan har konfigurerats och inte tillåter flera åtgärder kan inte väljas i listrutan.

## <a name="next-steps"></a>Nästa steg

Mer information om Intune-appskyddsprinciper finns här:
- [Hur du skapar och tilldelar skyddsprinciper för appar](app-protection-policies.md)
- [Inställningar för iOS-appskyddsprinciper](app-protection-policy-settings-ios.md)
- [Inställningar för Android-appskyddsprinciper i Microsoft Intune](app-protection-policy-settings-android.md) 


