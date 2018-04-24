---
title: Synkronisera enheter med Microsoft Intune – Azure | Microsoft Docs
description: Synkronisera enheter som har registrerats eller som hanteras med Intune så att du får de senaste principerna och åtgärderna. Detta omfattar steg för att synkronisera med Azure-portalen och en lista över felkoder som kan försökas på nytt.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1c098c3d7f71a45830f45877f5ce794d9e112b5e
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Synkronisera enheter för att få de senaste principerna och åtgärderna med Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Synkronisera** tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den. Den här funktionen kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Synkronisera en enhet

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj sedan **Microsoft Intune**. 
3. I **Intune** väljer du **Enheter** > **Alla enheter**.
4. I listan över enheter som du hanterar väljer du en enhet, väljer **Mer** och väljer sedan **Synkronisera**.
5. Välj **Ja** för att bekräfta.


## <a name="retryable-error-codes"></a>Återförsöksbara felkoder

När en administratör kör enhetsåtgärden **Synkronisera** är iOS- och Android-appar som misslyckades och genererade en återförsöksbar felkod fortfarande tillgängliga för enheten. Appar som genererade en icke-återförsöksbar felkod måste däremot vänta i sju dagar innan de är tillgängliga för enheten igen.


| Felkod  | Föreslagen beskrivning | Återförsökbar |
|---|---|---|
| 2016330898 | Ett okänt fel uppstod. | Nej |
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

- Välj **Enhetsåtgärder** för att se status för synkroniseringsåtgärden. 
