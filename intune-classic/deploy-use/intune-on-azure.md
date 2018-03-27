---
title: Att tänkta på när du hanterar Windows-enheter med Intune i Azure
description: Att tänka på när du använder Intune i Azure för att hantera din organisations Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 71effb587bfb82ecae18afda67b05fffd2127052
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune i Azure-konsolen och den äldre Intune PC-klienten

Intune flyttade nyligen till en Azure-baserad arkitektur för SaaS-programservice. Azure ger betydande förbättringar i skalbarhet, kapacitet och prestanda. Den här övergången erbjuder också förbättrade Intune-adminupplevelser och optimerade arbetsflöden i Azure-portalen. 

När du använder Intune i Azure för att hantera din organisations Windows-enheter bör du tänka på följande:

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Äldre PC-klientfunktioner finns endast tillgängliga i Silverlight-konsolen

Intune PC-klientens arbetsflöde för hantering använder sig av den [Silverlight-baserade Intune-administrationskonsolen](https://manage.microsoft.com/), vilket innebär följande:

- För alla icke-grupperande hanteringsuppgifter med Intune PC-klienten, måste du använda Silverlight-konsolen.
- När du hanterar grupper, måste du använda [Intune i Azure-portalen](https://portal.azure.com/). Det här kravet finns eftersom Intune nu använder sig av Azure AD-grupper istället för äldre Intune-grupper. 

På grund av övergången till Azure AD-grupper, har gruppbaserad filtrering i instrumentpanelsvyerna för Silverlight-konsolen ändrats något. Om du vill filtrera i det uppdaterade Silverlight-gränssnittet, följer du de här stegen:

1. Välj en vy.
2. I rutan **filter**, anger du namn på den grupp som du vill filtrera efter och trycker på retur. Då filtreras listvyn till enheterna i den specifika gruppen.

   ![](media/intune_on_azure/image01.png)

## <a name="manage-windows-10-devices-by-using-mdm"></a>Hantera Windows 10-enheter med hjälp av MDM

Vi rekommenderar att du använder [hantering av mobilenheter (MDM) för att hantera Windows 10-enheter](https://docs.microsoft.com/intune/device-restrictions-windows-10) istället för att använda den äldre Intune PC-klienten. Möjligheten att hantera Windows 10 via MDM är tillgänglig i Intune i Azure-portalen. Windows 10 MDM innehåller många nya hanterings- och säkerhetsfunktioner som inte finns tillgängliga via den äldre Intune PC-klienten.

## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Fortsätt att hantera Windows 7 med hjälp av Intune PC-klienten

Vi kommer att fortsätta att stödja befintliga Intune PC-klientfunktioner enbart i Silverlight-konsolen för Windows 7, som inte går att hantera med hjälp av MDM. Överväg att migrera till MDM-hantering när du uppgraderar till Windows 10.

## <a name="mdm-capabilities"></a>MDM-funktioner

En detaljerad jämförelse mellan funktionerna i PC-klienten och MDM finns i [jämför hantering av Windows-datorer som datorer eller mobila enheter](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison). MDM-uppdateringar kommer att fortsätta introducera nya hanteringsfunktioner till MDM-registrerade Windows 10-enheter, inklusive utvärdering av alternativ för Win 32-appar. Visa [nyheter](https://docs.microsoft.com/intune/whats-new) för de senaste versionstilläggen till tjänsten.

## <a name="switch-from-pc-client-to-mdm"></a>Växla från PC-klienten till MDM

Följ dessa steg om du vill växla från att hantera Windows 10-enheter med Intune PC-klienten till att hantera med MDM:

1. I Silverlight-konsolen, utför du en **selektiv rensning** för att avregistrera enheten från PC-klienten.
  ![](media/intune_on_azure/image02.png)
2. Omregistrera enheten med hjälp av [MDM (och/eller Azure AD-anslut)](https://docs.microsoft.com/intune/windows-enroll). 

## <a name="next-steps"></a>Nästa steg
[Registrera Windows-enheter](https://docs.microsoft.com/intune/windows-enroll)

 
