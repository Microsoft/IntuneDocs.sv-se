---
title: Synkronisera enheter med Intune
titlesuffix: Azure portal
description: "Läs om hur man synkroniserar enheter med Intune för att få de senaste principerna och åtgärderna.\""
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f784143535188c6bee2082c5717b752f08c5490
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Synkronisera enheter med Intune för att få de senaste principerna och åtgärderna


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Enhetsåtgärden **Synkronisera** tvingar den valda enheten att omedelbart checka in med Intune. När en enhet checkar in tar den omedelbart emot eventuella väntande åtgärder eller principer som har tilldelats till den.  Den här åtgärden kan hjälpa dig att validera och felsöka principer som du har tilldelat utan att du behöver vänta på nästa schemalagda incheckning.

## <a name="supported-platforms"></a>Plattformar som stöds

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="how-to-sync-a-device"></a>Synkronisera en enhet

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enheter** på bladet **Intune**.
4. På bladet **Enheter och grupper** väljer du **Alla enheter**.
5. I listan med enheter som du hanterar väljer du en enhet och sedan fjärråtgärden **Synkronisera**.
7. Bekräfta genom att klicka på **Ja** .


## <a name="retriable-error-codes"></a>Återförsöksbara felkoder

När en administratör kör enhetsåtgärden för **synkronisering** blir iOS- och Android-appar som misslyckades men genererade en återförsöksbar felkod tillgängliga för enheten. Appar som genererade en icke-återförsöksbar felkod måste däremot vänta i sju dagar innan de blir tillgängliga för enheten igen.


| Felkod  | Föreslagen beskrivning                                                                                                                  | Återförsöksbar |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 2016330898 | Ett okänt fel uppstod.                                                                                                             | Nej        |
| 2016330897 | Anslutningen till Intune har nått tidsgränsen. Återställ anslutningen                                                                             | Ja       |
| 2016330896 | Du har förlorat anslutningen till Internet. Återställ anslutningen.                                                                            | Ja       |
| 2016330895 | Du har förlorat anslutningen till Internet. Återställ anslutningen.                                                                            | Ja       |
| 2016330894 | Du har förlorat anslutningen till Internet. Återställ anslutningen.                                                                            | Ja       |
| 2016330893 | Du har förlorat anslutningen till Internet. Återställ anslutningen.                                                                            | Ja       |
| 2016330892 | Internationell nätverksväxling är inaktiverad.                                                                                                     | Nej        |
| 2016330891 | Mobildataanslutningen för den här enheten kan inte nås när ett mobiltelefonsamtal rings. Vänta tills telefonsamtalet har avslutats. | Ja       |
| 2016330890 | Det mobila nätverket för den här enheten. Dessa enheter kan inte användas just nu.                                                   | Nej        |
| 2016330889 | Det gick inte att skapa en säker anslutning. Återställ anslutningen.                                                                                   | Ja       |
| 2016330888 | Utvärderingen av serverförtroendet misslyckades.                                                                                                | Nej        |

## <a name="next-steps"></a>Nästa steg

Välj **Enhetsåtgärder** att se status för synkroniseringsåtgärden. 
