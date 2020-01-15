---
title: Förstå leverans och timing för appskyddsprincip
titleSuffix: Microsoft Intune
description: Lär dig de olika distributionsfönstren för appskyddsprinciper för att känna till när ändringar bör visas på slutanvändarenheterna.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ed343f652c4afe87273eeaa4a2e35b7669056d
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839232"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Förstå leverans och timing för appskyddsprincip

Lär dig de olika distributionsfönstren för appskyddsprinciper för att känna till när ändringar bör visas på slutanvändarenheterna.

## <a name="delivery-timing-summary"></a>Sammanfattning om leveranstiming

Leverans av programskyddsprincip beror på licenstillståndet och Intune-tjänstregistrering för dina användare.  

|    Användartillstånd    |    Appskyddsbeteende     |    Återförsöksintervall (se anteckning)    |    Varför sker det här?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Klientorganisation har inte registrerats    |    Vänta på nästa återförsöksintervall.  Appskydd är inte aktivt för användaren.    |    24 timmar    |    Inträffar när du har inte konfigurerat din klientorganisation för Intune.    |
|    Användaren är inte licensierad     |    Vänta på nästa återförsöksintervall.  Appskydd är inte aktivt för användaren.     |    12 timmar – på Android-enheter kräver det här intervallet dock Intune APP SDK version 5.6.0 eller senare. Annars är intervallet 24 timmar för Android-enheter.   |    Inträffar när du inte har licensierat användaren för Intune.    |
|    Användaren har inte tilldelats appskyddsprinciper    |    Vänta på nästa återförsöksintervall.  Appskydd är inte aktivt för användaren.    |    12 timmar        |    Inträffar när du inte har tilldelat APP-inställningar till användaren.    |
|    Användaren har registrerats för Intune MAM    |    Appskydd tillämpas enligt principinställningar.    Uppdateringar sker baserat på återförsöksintervall    |    Intune-tjänsten definieras baserat på användarbelastning.    Normalt 30 minuter.     |    Inträffar när användaren har registrerats med Intune-tjänsten för MAM-konfiguration.    |

> [!NOTE]
> Återförsöksintervall kan kräva appanvändning för att inträffa, vilket innebär att appen har startats och används.  Om återförsöksintervallet är 24 timmar och användaren väntar 48 timmar med att starta appen försöker programskyddsklienten igen efter 48 timmar.

## <a name="handling-network-connectivity-issues"></a>Hantera problem med nätverksanslutning

När användarregistrering misslyckas på grund av problem med nätverksanslutning används ett påskyndat återförsöksintervall.  Programskyddsklienten försöker på nytt vid allt längre intervall tills intervallet når 60 minuter eller en lyckad anslutning görs.  Klienten fortsätter sedan att försöka igen vid 60 minuters intervall tills en lyckad anslutning görs. Sedan återgår klienten till det standardmässiga återförsöksintervallet baserat på användartillståndet.

## <a name="next-steps"></a>Nästa steg

[Tilldela licenser till användare så att de kan registrera enheter i Intune](../fundamentals/licenses-assign.md)

