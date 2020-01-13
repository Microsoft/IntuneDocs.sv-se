---
title: Använda rapporter för Uppdateringsefterlevnad för Windows-uppdateringar i Microsoft Intune
titleSuffix: Microsoft Intune
description: Använd OMS Uppdateringsefterlevnad för att visa rapportdata för Windows-uppdateringar som du distribuerar med Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1e493e0d2d562c0f69454d1999e82b528c724a2
ms.sourcegitcommit: e4602481a25a5e12379f673dfe801c611f51c35b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75731287"
---
# <a name="intune-compliance-reports-for-updates"></a>Intune-efterlevnadsrapporter för uppdateringar

När du använder Intune för att distribuera Windows-uppdateringar till Windows 10-enheter visar du information om uppdateringsefterlevnad med hjälp av Intune eller en kostnadsfri lösning som heter *Uppdateringsefterlevnad*, som ingår i Microsoft Operations Management Suite (OMS).

## <a name="use-intune"></a>Använda Intune

Så här granskar du en principrapport om distributionsstatusen för de Windows 10-uppdateringsringar som du har konfigurerat:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Välj **Enheter** > **Översikt** > **Programuppdateringsstatus**. Här kan du se allmän information om status för alla uppdateringsringar som du tilldelade.

3. Om du vill visa mer information väljer du **Övervaka**. Under **Programuppdateringar**väljer du **Per distributionsstatus för uppdateringsring** och väljer den distributionsring som ska granskas.

   I avsnittet om **övervakning** väljer du bland följande rapporter för att visa mer detaljerad information om uppdateringsringen:

   - **Enhetsstatus** – här visas enhetens konfigurationsstatus. Mer information finns i [Uppdatera enhetskonfigurationsstatus]( https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationdevicestatus-update?view=graph-rest-1.0).

   - **Användarstatus** – här visas användarnamn, status och senaste rapportdatum. Mer information finns i [Lista med status för enhetskonfigureringsanvändare](https://docs.microsoft.com/graph/api/intune-deviceconfig-deviceconfigurationuserstatus-list?view=graph-rest-1.0).

   - **Status för slutanvändaruppdatering** – detta visar status för Windows enhets uppdatering. Mer information finns i [Windows uppdateringsstatus](https://docs.microsoft.com/graph/api/resources/intune-shared-windowsupdatestate?view=graph-rest-beta).

## <a name="use-update-compliance"></a>Använda Uppdateringsefterlevnad

Du kan övervaka Windows 10-uppdateringsdistribution med hjälp av [Uppdateringsefterlevnad](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor), en Windows Analytics-lösning. Uppdateringsefterlevnad erbjuds via Azure-portalen och är tillgängligt utan kostnad för enheter som uppfyller dess [krav](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites).  

När du använder den här lösningen distribuerar du ett kommersiellt ID till valfria Intune-hanterade Windows 10 enheter som du vill rapportera uppdateringsefterlevnad för.  

I Intune kan du konfigurera det kommersiella ID:t med hjälp av OMA-URI-inställningarna för en anpassad princip. Se [Använda anpassade inställningar för Windows 10-enheter i Intune](../configuration/custom-settings-windows-10.md).

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
