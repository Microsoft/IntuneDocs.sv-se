---
title: Använda rapporter för Uppdateringsefterlevnad för Windows-uppdateringar i Microsoft Intune
titleSuffix: Microsoft Intune
description: Använd OMS Uppdateringsefterlevnad för att visa rapportdata för Windows-uppdateringar som du distribuerar med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728110"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune-efterlevnadsrapporter för uppdateringar
När du använder Intune för att distribuera Windows-uppdateringar till Windows 10-enheter visar du information om uppdateringsefterlevnad med hjälp av Intune eller en kostnadsfri lösning som heter *Uppdateringsefterlevnad*, som ingår i Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Använda Intune
Så här granskar du en principrapport om distributionsstatusen för de Windows 10-uppdateringsringar som du har konfigurerat: 
1. Logga in på [Azure Portal](https://portal.azure.com/).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Programuppdateringar** > **Översikt**. Här kan du se allmän information om status för alla uppdateringsringar som du tilldelade.
4. Öppna någon av följande rapporter:  

   **För alla testgrupper för distribution**:
   1. I **Programuppdateringar** > **Windows 10-uppdateringsringar**
   2. I avsnittet om **övervakning** ska du välja **Distributionsstatus per uppdateringstestgrupp**.  

   **För specifika testgrupper för distribution**:  

   1. I **Programuppdateringar** > **Windows 10-uppdateringsringar** väljer du den testgrupp för distribution som du vill granska.  
   2. I avsnittet om **övervakning** väljer du bland följande rapporter för att visa mer detaljerad information om uppdateringsringen:  
      - **Enhetstillstånd**  
      - **Användarstatus**  

## <a name="use-update-compliance"></a>Använda Uppdateringsefterlevnad
Du kan övervaka Windows 10-uppdateringsdistribution med hjälp av [Uppdateringsefterlevnad](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), en Windows Analytics-lösning. Uppdateringsefterlevnad erbjuds via Azure-portalen och är tillgängligt utan kostnad för enheter som uppfyller dess [krav](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

När du använder den här lösningen distribuerar du ett kommersiellt ID till valfria Intune-hanterade Windows 10 enheter som du vill rapportera uppdateringsefterlevnad för.  

I Intune-konsolen använder du OMA-URI-inställningarna för en anpassad princip till att konfigurera det kommersiella ID:t. Mer information finns i [Intune-principinställningar för Windows 10-enheter i Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).  

Den OMA-URI-sökväg (skiftlägeskänslig) du använder när du ska konfigurera det kommersiella ID:t är: *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

Du kan t.ex. använda följande värden i **Lägga till eller redigera OMA-URI-inställningen**:
- **Inställningsnamn**: Kommersiellt ID för Windows Analytics
- **Beskrivning av inställning**: Konfigurera kommersiellt ID för Windows Analytics-lösningar
- **OMA-URI** (skiftlägeskänsligt): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **Datatyp**: Sträng
- **Värde**: \<Använd det GUID som visas på fliken Windows-telemetri på din OMS-arbetsyta>
 
> [!NOTE]  
> Mer information om MS DM-server finns i [DMClient-konfigurationsprovider]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp).

## <a name="next-steps"></a>Nästa steg
[Hantera programuppdateringar i Intune](windows-update-for-business-configure.md)

