---
title: "Ändringslogg för Intune-informationslagret | Microsoft Docs"
description: "En lista över ändringar i Intunes informationslager-API."
keywords: Intune-informationslager
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6d675a36cd5ea4c11d755174bf2b0bbc5d4b18ec
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/08/2017
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Ändringslogg för Intunes informationslager-API

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Håll dig uppdaterad om uppdateringar för Intune-informationslagret.

## <a name="1710"></a>1710
_Publicerat november 2017_

### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>Användarentiteten innehåller de senaste användardata i datamodellen för informationslagret <!-- 1544273 -->

Den första versionen av datamodellen för Intune-informationslagret innehöll endast de senaste historiska Intune-data. Rapportskaparna kunde inte identifiera det aktuella tillståndet för en användare. I den här uppdateringen kommer [**Användarentiteten**](reports-ref-user.md) att fyllas i med de senaste användardata.

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nya entiteter i datamodellen för Intune-informationslagret <!-- 1479526 --><!-- -->

 - Entiteten [**UserDeviceAssociation**](reports-ref-user-device.md) har lagts till. **UserDeviceAssociation** innehåller användarenhetsassociationer i din organisation.
 - Entiteten, [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md), har lagts till. **IntuneManagementExtension** innehåller entiteter för mobila enheter som spårar information, t.ex. version och installationsstatus.

## <a name="next-steps"></a>Nästa steg
 - Läs mer om [vad som är nytt i Intune varje vecka](whats-new.md). Du kan också läsa mer om kommande ändringar, viktiga meddelanden om tjänsten och information om tidigare versioner. 
 - Läs [Microsoft Intune-bloggen](http://go.microsoft.com/fwlink/?LinkID=273882).