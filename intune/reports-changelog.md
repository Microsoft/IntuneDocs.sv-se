---
title: "Ändringslogg för Intune-informationslagret | Microsoft Docs"
description: "En lista över ändringar i Intunes informationslager-API."
keywords: Intune-informationslager
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e17ca34897a707360d802e37ffe3fa91fad0860
ms.sourcegitcommit: d44c32aad3e84f6c0b296bdb010981d3a818befb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2018
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Ändringslogg för Intunes informationslager-API

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Håll dig uppdaterad om uppdateringar för Intune-informationslagret.

## <a name="1710"></a>1710
_Publicerat november 2017_

### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1544273---"></a>En ny entitetssamling med namnet aktuell användare, är begränsad till aktuell aktiv användardata <!-- 1544273 -->

Entitetssamlingen **Användare** innehåller alla Azure Active Directory-användare (Azure AD) med tilldelade licenser i ditt företag. De här posterna innehåller användarens tillstånd vid datainsamlingsperioden, även om användaren har tagits bort. En användare kan till exempel läggas till i Intune och sedan tas bort under den senaste månaden. Användaren är då inte tillgänglig vid tidpunkten för rapporten, men användaren och tillståndet finns i data. Du kan skapa en rapport som visar varaktigheten för användarens historiska förekomst i dina data.

Den nya entitetssamlingen **aktuell användare** innehåller däremot bara användare som inte har tagits bort. Entitetssamlingen **aktuell användare** innehåller bara användare som är aktiva för tillfället. Mer information om entitetssamlingen **aktuell användare** finns i [referens för den aktuella användarentiteten](reports-ref-current-user.md).

## <a name="1709"></a>1709
_Publicerad oktober 2017_

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Användarenhetens associationsentitetssamling lades till i datamodellen för Intunes informationslager <!-- 1187917 -->

Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar. Datamodellen kan nås via Power BI-filen (PBIX) som hämtas från Intune-sidan Informationslager via OData-slutpunkten, eller genom att utveckla en anpassad klient. Mer information finns i [användarenhetens associering](reports-ref-user-device.md).

### <a name="new-entities-in-the-in-data-warehouse-data-model----1479526--------"></a>Nya entiteter i datamodellen för Intune-informationslagret <!-- 1479526 --><!-- -->

 - Entiteten [**UserDeviceAssociation**](reports-ref-user-device.md) har lagts till. **UserDeviceAssociation** innehåller användarenhetsassociationer i din organisation. Du kan nu skapa rapporter och datavisualiseringar med hjälp av enhetens associationsinformation som associerar användaren och enhetens entitetssamlingar.  
 - Entiteten, [**IntuneManagementExtension**](reports-ref-intunemanagementextension.md), har lagts till. **IntuneManagementExtension** innehåller entiteter för mobila enheter som spårar information, t.ex. version och installationsstatus.

## <a name="next-steps"></a>Nästa steg
 - Läs mer om [vad som är nytt i Intune varje vecka](whats-new.md). Du kan också läsa mer om kommande ändringar, viktiga meddelanden om tjänsten och information om tidigare versioner.
 - Läs [Microsoft Intune-bloggen](http://go.microsoft.com/fwlink/?LinkID=273882).
