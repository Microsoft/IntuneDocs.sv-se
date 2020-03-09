---
title: Synkronisera enheter med Microsoft Intune – Azure | Microsoft Docs
description: Synkronisera enheter som har registrerats eller som hanteras med Intune så att du får de senaste principerna och åtgärderna. Detta omfattar steg för att synkronisera med Azure-portalen och en lista över felkoder som kan försökas på nytt.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee3020c2a1dfadb21b55ca29a2295498bf893080
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781973"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Synkronisera enheter för att få de senaste principerna och åtgärderna med Intune


Enhetsåtgärden **Synkronisera** tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den. Den här funktionen kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Synkronisera en enhet

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). 
3. Välj **Enheter** > **Alla enheter**.
4. I listan med enheter som du hanterar väljer du en enhet för att öppna dess *Översikt*. Välj sedan **Synkronisera**.
5. Välj **Ja** för att bekräfta.

Välj **Enheter** > **Övervaka** > **Enhetsåtgärder** om du vill se statusen för synkroniseringsåtgärden.

Du kan hitta incheckningsfrekvensen för Intunes standardprincip i [Uppdatera cykeltider](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retryable-error-codes"></a>Återförsöksbara felkoder

När en administratör kör enhetsåtgärden **Synkronisera** är iOS/iPadOS- och Android-appar som misslyckades och genererade en återförsöksbar felkod fortfarande tillgängliga för enheten. Appar som genererade en icke-återförsöksbar felkod måste däremot vänta i sju dagar innan de är tillgängliga för enheten igen.


| Felkod  | Föreslagen beskrivning | Återförsökbar |
|---|---|---|
| 2016330898 | Det har uppstått ett oväntat fel. | Nej |
| 2016330897 | Anslutningen till Intune har nått tidsgränsen. Återställ anslutningen. | Ja |
| 2016330896 | Du har förlorat anslutningen till Internet. Återställ anslutningen. | Ja |
| 2016330895 | Du har förlorat anslutningen till Internet. Återställ anslutningen. | Ja |
| 2016330894 | Du har förlorat anslutningen till Internet. Återställ anslutningen. | Ja |
| 2016330893 | Du har förlorat anslutningen till Internet. Återställ anslutningen. | Ja|
| 2016330892 | Internationell nätverksväxling är inaktiverad. | Nej|
| 2016330891 | Mobildataanslutningen för den här enheten kan inte nås när ett mobiltelefonsamtal rings. Vänta tills telefonsamtalet har avslutats. | Ja|
| 2016330890 | Det mobila nätverket för den här enheten. Dessa enheter kan inte användas just nu. | Nej|
| 2016330889 | Det gick inte att skapa en säker anslutning. Återställ anslutningen. | Ja|
| 2016330888 | Utvärderingen av serverförtroendet misslyckades. | Nej|

## <a name="next-steps"></a>Nästa steg

Du kan [kontrollera informationen](device-inventory.md) om enheten.
 
