---
title: Konfigurera uppdateringsprinciper för iOS/iPadOS-programvara i Microsoft Intune – Azure | Microsoft Docs
description: I Microsoft Intune skapar du eller lägger till en konfigurationsprincip för att begränsa när programvaruuppdateringar installeras automatiskt på iOS/iPadOS-enheter. Du kan välja datum och tid när uppdateringar inte installeras. Du kan även tilldela den här principen till grupper, användare eller enheter samt söka efter eventuella installationsfel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 77d4a90bb2eaa8434ff9c05362dcb0d7cb270651
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576148"
---
# <a name="add-iosipados-software-update-policies-in-intune"></a>Lägga till principer för iOS/iPadOS-programuppdatering i Intune

Med programvaruuppdateringsprinciper kan du tvinga övervakade iOS/iPadOS-enheter att automatiskt installera uppdateringar för operativsystemet. Övervakade enheter är enheter som har registrerats med antingen Apple Business Manager eller Apple School Manager. När du konfigurerar en princip för att distribuera uppdateringar kan du:

- Välj att distribuera den *senaste uppdateringen* som är tillgänglig, eller välja att distribuera en äldre uppdatering med ett lägre versionsnummer om du inte vill distribuera den senaste uppdateringen. Om du väljer att distribuera en äldre uppdatering måste du också ange en princip för enhetskonfiguration för att begränsa visningen av programuppdateringar.
- Ange ett schema som bestämmer när uppdateringen ska installeras. Ett schema kan vara enkelt, till exempel att uppdateringar ska installeras nästa gång enheten checkas in. Du kan också skapa datum- och tidsintervall inom vilka uppdateringar ska kunna installeras eller hindras från att installeras.

Den här funktionen gäller för:

- iOS 10.3 och senare (övervakade enheter)

Som standard checkas enheter in på Intune var 8:e timme. Om en uppdatering är tillgänglig via en uppdateringsprincip laddas uppdateringen ned till enheten. Enheten installerar sedan uppdateringen vid nästa incheckning inom det angivna schemat. Normalt krävs ingen användarinteraktion under uppdateringsprocessen, men om enheten har ett lösenord måste användaren ange detta för att starta en programuppdatering. Profiler hindrar inte användare från att uppdatera operativsystemet manuellt. Användare kan hindras från att uppdatera operativsystemet manuellt med en princip för enhetskonfiguration som begränsar visningen av programuppdateringar.

## <a name="configure-the-policy"></a>Konfigurera principen

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Enheter** > **Uppdatera principer för iOS/iPadOS** > **Skapa profil**.
3. På fliken **Grundläggande** anger du ett namn för den här principen, anger en beskrivning och väljer **Nästa**.

   ![Fliken Grundläggande](./media/software-updates-ios/basics-tab.png)

4. Konfigurera följande på fliken **Uppdatera principinställningar**:

   1. **Välj vilken version som ska installeras**. Du kan välja mellan:

      - *Senaste uppdateringen*: Detta distribuerar den senast utgivna uppdateringen för iOS/iPadOS.
      - En tidigare version som är tillgänglig i listrutan. Om du väljer en tidigare version måste du också distribuera en princip för enhetskonfiguration för att fördröja visningen av programuppdateringar.

   2. **Schematyp**: Konfigurera schemat för den här principen:

      - *Uppdatera vid nästa incheckning*: Uppdateringen installeras på enheten nästa gång enheten checkar in på Intune. Det här är det enklaste alternativet och kräver inga fler inställningar.
      - *Uppdatera under schemalagd tid*: Du anger en eller flera tidsperioder inom vilka uppdateringen ska installeras vid incheckning.
      - *Uppdatera utanför schemalagd tid*: Du anger en eller flera tidsperioder inom vilka uppdateringen inte ska installeras vid incheckning.

   3. **Veckoschema**: Om du väljer en annan schematyp än *Uppdatera vid nästa incheckning* konfigurerar du följande alternativ:

      ![Exempel på val av Uppdatera under schemalagd tid](./media/software-updates-ios/scheduled-time.png)

      - **Tidzon**: Välj en tidszon.
      - **Tidsperiod**: Definiera en eller flera tidsperioder för att begränsa när uppdateringar ska kunna installeras. Effekterna av följande alternativ beror på vilken schematyp du har valt. Genom att ange en startdag och en slutdag kan du använda blockeringar över natten. Alternativen är:

        - **Startdag**: Välj den dag då tidsperioden för schemat ska starta.
        - **Starttid**: Välj den tid på dagen då tidsperioden för schemat ska starta. Om du till exempel väljer 5:00 och har schematypen *Uppdatera under schemalagd tid* kan uppdateringar börja installeras från kl 5:00. Om du väljer schematypen *Uppdatera utanför schemalagd tid* blir 5:00 i stället starttiden för en tidsperiod då det inte går att installera uppdateringar.
        - **Slutdag**: Välj den dag då tidsperioden för schemat ska sluta.
        - **Sluttid**: Välj vilken tid på dagen som tidsperioden för schemat ska sluta. Om du till exempel väljer 1:00 och har schematypen *Uppdatera under schemalagd tid* kan uppdateringarna inte längre installeras efter kl 1:00. Om du väljer schematypen *Uppdatera utanför schemalagd tid* blir 1:00 i stället starttiden för en tidsperiod då det går att installera uppdateringar.

       Om du inte anger någon start- och sluttid gäller ingen begränsning, och uppdateringar kan installeras när som helst.  

       > [!NOTE]
       > Om du vill fördröja visningen av programuppdateringar under en viss tid på dina övervakade iOS/iPadOS-enheter konfigurerar du de inställningarna i [Enhetsbegränsningar](../configuration/device-restrictions-ios.md#general). Principer för programuppdatering åsidosätter eventuella enhetsbegränsningar. När du anger både en princip för programuppdatering och en begränsning som fördröjer programuppdateringars synlighet framtvingar enheten en programuppdatering enligt principen. Begränsningen gäller så att användarna inte ser alternativet att själva uppdatera enheten, och uppdateringen överförs enligt vad som definieras av din iOS-uppdateringsprincip.

   När du har konfigurerat *Inställningar för uppdateringsprincip* väljer du **Nästa**.

5. På fliken **Omfångstaggar** väljer du **+ Välj omfångstaggar** för att öppna fönstret *Välj taggar* om du vill tillämpa dem på uppdateringsprincipen.

   - I fönstret **Välj taggar** väljer du en eller fler taggar och klickar sedan på **Välj** för att lägga till dem i principen och återgå till fönstret *Omfångstaggar*.

   När du är klar väljer du **Nästa** för att fortsätta till *Tilldelningar*.

6. På fliken **Tilldelningar** väljer du **+ Välj grupper som ska inkluderas** och tilldelar sedan uppdateringsprincipen till en eller fler grupper. Använd **+ Välj grupper att utesluta** för att finjustera tilldelningen. När du är klar väljer du **Nästa** för att fortsätta.

   De enheter som används av de användare som den här principen inriktar sig på utvärderas för uppdateringsefterlevnad. Den här principen har även stöd för användarlösa enheter.

7. På fliken **Granska och skapa** granskar du inställningarna och väljer **Skapa** när du är redo att spara din iOS/iPadOS-uppdateringsprincip. Den nya principen visas i listan över uppdateringsprinciper för iOS/iPadOS.

Vägledning från Intune-supportteamet finns i [Fördröj synligheten för programvaruuppdateringar i Intune för övervakade enheter](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Delaying-visibility-of-software-updates-in-Intune-for-supervised/ba-p/345753).

> [!NOTE]
> Apple MDM tillåter inte att du tvingar en enhet att installera uppdateringar en viss tid eller ett visst datum. Du kan inte använda principer för programvaruuppdateringar i Intune till att nedgradera operativsystemversionen på en enhet.

## <a name="edit-a-policy"></a>Redigera en princip

Du kan redigera en befintlig princip, inklusive att ändra de begränsade tiderna:

1. Välj **Enheter** > **Uppdateringsprinciper för iOS**. Välj den princip som du vill redigera.

2. När du visar principernas **Egenskaper** väljer du **Redigera** för den principsida som du vill ändra.

   ![Redigera en princip](./media/software-updates-ios/edit-policy.png)

3. När du har infört en ändring väljer du **Granska och spara** > **Spara** för att spara ändringarna och återgår till principernas *Egenskaper*.

> [!NOTE]
> Om **Starttid** och **Sluttid** båda anges till kl. 12:00 kontrollerar inte Intune om det finns begränsningar för när uppdateringar får installeras. Det innebär att alla konfigurationer som du har för **Välj tidpunkter för att förhindra installationer av uppdateringar** ignoreras och att uppdateringar kan installeras när som helst.

## <a name="monitor-device-installation-failures"></a>Övervaka enhetsinstallationsfel

<!-- 1352223 -->
**Programuppdateringar** > **Installationsfel för iOS-enheter** visar en lista över övervakade iOS/iPadOS-enheter som är mål för en uppdateringsprincip, försökte genomföra en uppdatering och inte kunde uppdateras. För varje enhet kan du se status om varför enheten inte har uppdaterats automatiskt. Felfria, uppdaterade enheter visas inte i listan. ”Uppdaterade” enheter innefattar den senaste uppdateringen som enheten själv har stöd för.

## <a name="next-steps"></a>Nästa steg

[Övervaka dess status](../configuration/device-profile-monitor.md).
