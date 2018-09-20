---
title: Ändringslogg för Intune-informationslagret
titlesuffix: Microsoft Intune
description: En lista över ändringar i Intunes informationslager-API.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E85DBB2D-67BB-4E10-82D6-E43046B9C43C
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 08f5437141cc98161af740d7b8cad7c6cc1ff61c
ms.sourcegitcommit: 443b4cb3390da47bf1e497b1f0c0137a5ddda7bd
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43821196"
---
# <a name="change-log-for-the-intune-data-warehouse-api"></a>Ändringslogg för Intunes informationslager-API

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Håll dig uppdaterad om uppdateringar för Intune-informationslagret.

## <a name="1808"></a>1808
_Publicerad augusti 2018_

### <a name="v10-collections"></a>v1.0-samlingar  

Det går nu att använda v1.0-versionen av Intune-informationslagret genom att ange frågeparametern `api-version=v1.0`. Uppdateringar av samlingar i datalagret är additiva och avbryter inte befintliga scenarier.

### <a name="enrollment-failure-collection-released-to-beta"></a>Samlingen Registreringsfel utgiven som betaversion

Den nya samlingen `Enrollment Failure` har släppts som betaversion. Du kan använda den här samlingen för att förstå hur registreringen framskrider genom att granska de vanligaste felen. 


## <a name="1805"></a>1805
_Utgiven: maj 2018_

### <a name="correction-to-device-count-in-devices-collection"></a>Korrigering av antal enheter i samlingen **Enheter** 

En korrigering har gjorts till samlingen **Enheter** som kan minska det totala antalet enheter som filtreras med attributet `isDeleted`. Den här sänkningen är ett resultat av korrigeringen och är inte ett fel. Mer information om samlingen **enheter** finns i [Referens för enhetsentiteter](reports-ref-devices.md). 


## <a name="1801"></a>1801
_Publicerad i januari 2018_

### <a name="intune-data-warehouse-application-only-authentication----1867540---"></a>Autentisering endast med program för Intune-informationslager <!-- 1867540 -->

Du kan konfigurera ett program med Azure Active Directory (Azure AD) och autentisera till Intune-informationslagret. Mer information finns i [Autentisering endast med program för Intune-informationslager](data-warehouse-app-only-auth.md).

### <a name="azure-ad-and-intune-credential-requirements----2077525---"></a>Krav på Azure AD- och Intune-autentiseringsuppgifter <!-- 2077525 -->

- Det krävs inte längre att någon Intune-licens tilldelas till användaren vid åtkomst till Intune-informationslagret (inklusive API).
- Intune-rollnamnet har ändrats från **Rapporter** till **Intune-informationslager**. 

    Mer information finns i [Krav på Azure AD- och Intune-autentiseringsuppgifter](reports-api-url.md#azure-ad-and-intune-credential-requirements).

### <a name="odata-query-options----2077711---"></a>OData-frågealternativ <!-- 2077711 -->

Du kan använda <code>$select</code> som en OData-frågeparameter. Den aktuella versionen har stöd för följande OData-frågeparametrar: <code>$filter</code>, <code>$orderby</code>, <code>$select</code>, <code>$skip</code> och <code>$top</code>. Mer information finns i [OData-frågealternativ](reports-api-url.md#odata-query-options).

### <a name="new-entities-in-the-in-data-warehouse-data-model----2077804---"></a>Nya entiteter i datamodellen för informationslager <!-- 2077804 -->

 - Entiteten [**MobileAppDeviceuserInstallStatus**](reports-ref-application.md#mobileappdeviceuserinstallstatus) har lagts till. **MobileAppDeviceUserInstallStatus** representerar en mobilapps installationstillstånd för en viss enhet och en användare.
 - Entiteten [**MobileAppInstallState**](reports-ref-application.md#mobileappinstallstate) har lagts till. Entiteten **MobileAppInstallState** visar installationsstatus för ett mobilt program när det har tilldelats till en grupp som innehåller enheter och/eller användare. 

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
