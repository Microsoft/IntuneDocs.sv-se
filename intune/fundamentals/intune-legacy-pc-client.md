---
title: Äldre Intune PC-klient och Intune på Azure
description: Att tänka på när du använder Intune i Azure för att hantera din organisations Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 1f104923-12df-453c-9c20-942ef65a0945
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5ab1be3d34d52e824d1ff06124e28206fb7b07a1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72510184"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune i Azure-konsolen och äldre Intune PC-klient

Intune använder en Azure-baserad arkitektur för SaaS-tillämpningstjänsten. Azure ger betydande förbättringar i skalbarhet, kapacitet och prestanda. Det här ger förbättrad Intune-administration och optimerade arbetsflöden i Azure-portalen. 

När du använder Intune i Azure för att hantera din organisations Windows-enheter bör du tänka på följande:

## <a name="manage-windows-10-devices-by-using-mdm"></a>Hantera Windows 10-enheter med hjälp av MDM

Vi rekommenderar att du använder [hantering av mobilenheter (MDM) för att hantera Windows 10-enheter](../configuration/device-restrictions-windows-10.md) istället för att använda den äldre Intune PC-klienten. Möjligheten att hantera Windows 10 via MDM är tillgänglig i Intune i Azure-portalen. Windows 10 MDM innehåller många nya hanterings- och säkerhetsfunktioner som inte finns tillgängliga via den äldre Intune PC-klienten.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Äldre PC-klientfunktioner finns endast tillgängliga i Silverlight-konsolen

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune PC-klientens arbetsflöde för hantering använder sig av den [Silverlight-baserade Intune-administrationskonsolen](https://manage.microsoft.com/), vilket innebär följande:

- För alla icke-grupperande hanteringsuppgifter med Intune PC-klienten, måste du använda Silverlight-konsolen.
- När du hanterar grupper, måste du använda [Intune i Azure-portalen](https://portal.azure.com/). Det här kravet finns eftersom Intune nu använder sig av Azure AD-grupper istället för äldre Intune-grupper. 

På grund av övergången till Azure AD-grupper, har gruppbaserad filtrering i instrumentpanelsvyerna för Silverlight-konsolen ändrats något. Om du vill filtrera i det uppdaterade Silverlight-gränssnittet, följer du de här stegen:

1. Välj en vy.
2. I rutan **filter**, anger du namn på den grupp som du vill filtrera efter och trycker på retur. Då filtreras listvyn till enheterna i den specifika gruppen.

   ![Filtrerar List Rute inmatade med ingen vald](./media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Fortsätt att hantera Windows 7 med hjälp av Intune PC-klienten

Vi kommer att fortsätta att stödja befintliga Intune PC-klientfunktioner enbart i Silverlight-konsolen för Windows 7, som inte går att hantera med hjälp av MDM. Överväg att migrera till MDM-hantering när du uppgraderar till Windows 10.

## <a name="mdm-capabilities"></a>MDM-funktioner

En detaljerad jämförelse mellan funktionerna i PC-klienten och MDM finns i [jämför hantering av Windows-datorer som datorer eller mobila enheter](pc-management-comparison.md). MDM-uppdateringar kommer att fortsätta introducera nya hanteringsfunktioner till MDM-registrerade Windows 10-enheter, inklusive utvärdering av alternativ för Win 32-appar. Visa [nyheter](whats-new.md) för de senaste versionstilläggen till tjänsten.

## <a name="switch-from-pc-client-to-mdm"></a>Växla från PC-klienten till MDM

Följ dessa steg om du vill växla från att hantera Windows 10-enheter med Intune PC-klienten till att hantera med MDM:

1. I Silverlight-konsolen, utför du en **selektiv rensning** för att avregistrera enheten från PC-klienten.
  ![varnings fönster med alternativ knappen selektivt rensa enheten valt](./media/intune-legacy-pc-client/image02.png)
2. Omregistrera enheten med hjälp av [MDM (och/eller Azure AD-anslut)](../enrollment/windows-enroll.md).

## <a name="next-steps"></a>Nästa steg
[Registrera Windows-enheter](../enrollment/windows-enroll.md)
