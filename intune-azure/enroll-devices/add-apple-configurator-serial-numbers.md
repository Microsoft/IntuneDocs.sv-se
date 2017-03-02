---
title: "Lägg till Apple Configurator-serienummer"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Läs om hur du lägger till serienummer till företagsägda iOS-enheter med Apple Configurator."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 26d253f013195cc18f9a97b8259c603d707d22bf
ms.lasthandoff: 02/18/2017


---

# <a name="add-apple-configurator-serial-numbers"></a>Lägg till Apple Configurator-serienummer

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Följ de här stegen när du ska lägga till serienummer till Intune när du vill [registrera företagsägda iOS-enheter med hjälp av Apple Configurator med installationsassistenten](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). Du kan lägga till serienumren ett i taget eller ladda upp en fil med kommateckenavgränsade fält (CSV) med serienummer. När du har lagt till serienumren tilldelar du dem en profil. Profilen innehåller specifika hanteringsinställningar som du tillämpar på enheter.

Andra metoder för att registrera iOS-enheter beskrivs i [Välj hur du vill registrera iOS-enheter i Intune](choose-ios-enrollment-method.md).

**Lägga till Apple Configurator-serienummer till Intune**

1. Skapa en fil med kommaseparerade värden (CSV) med två kolumner och ingen rubrik. Lägg till IMEI-identifieraren i den vänstra kolumnen och informationen i den högra kolumnen. Det maximala antalet rader i kolumnen är för närvarande 500. Om du öppnar CSV-listan i en textredigerare ser den ut ungefär så här:

    F7TLWCLBX196, enhetsinformation</br>
   DLXQPCWVGHMJ, enhetsinformation

2. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

3.  Välj **Registrera enheter** på Intune-bladet och välj sedan **Apple-registrering**.

4. Välj **Apple Configurator-serienummer** under **Hantera Apple Configurator-registreringsinställningar**.

5. Välj **Lägg till** på bladet **Apple Configurator-serienummer**.

6. Välj den profil som ska tillämpas på de serienummer som du importerar på bladet **Lägg till serienummer**. Om du importerar en fil med ny information som kommer att skriva över befintlig information, så välj Skriv över information för befintliga identifierare. Då ersätts den befintliga informationen av den nya.

7. Navigera till CSV-filen med serienummer och välj **Lägg till**.

## <a name="assign-a-profile-to-specific-serial-numbers"></a>Tilldela specifika serienummer en profil

Med Intune kan du tilldela profiler från två olika platser i Azure-portalen. Följ stegen nedan, eller tilldela profiler från bladet Apple Configurator Registreringsprofiler, där du skapar profilen. Mer information finns i [Registrera iOS-enheter med Apple Configurator med hjälp av installationsassistenten](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). Du kan bara tilldela profilen enligt stegen nedan om du redan har skapat profilen.

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Apple-registrering**.

3. Välj det serienummer som du vill tilldela en profil på bladet **Apple Configurator-serienummer** och välj sedan **Tilldela profil**.

4. Välj den profil som du vill tilldela på bladet **Tilldela profil** och välj sedan **Tilldela**.

## <a name="delete-serial-numbers"></a>Ta bort serienummer
Du kan ta bort serienummer som du tidigare har importerat. Du kan bara ta bort serienummer sedan enheten har avregistreras. När du väl har tagit bort ett serienummer kan du inte använda Apple Configurator via Installationsassistenten såvida du inte först lägger till serienumret igen.

## <a name="view-the-state-of-a-device"></a>Visa enhetens tillstånd
Enhetens serienummer kan ha ett av två tillstånd:

- Registrerad – enheten har registrerats och anslutits till Intune-tjänsten
- Inte kontaktad – enheten har aldrig anslutits till Intune-tjänsten.
- Väntar på återställning – enheten har registrerats, men en ändring har gjorts (t.ex. har registreringsinställningarna eller den tillämpade DEP-profilen ändrats). Om du ändrar en enhets DEP-profil tillämpas inte ändringarna förrän enheten har avregistrerats och sedan registrerats på nytt.

**Visa ett serienummers tillstånd**

Välj det serienummer vars tillstånd du vill se på bladet **Apple Configurator-serienummer** och kontrollera det sedan under **Tillstånd**.

