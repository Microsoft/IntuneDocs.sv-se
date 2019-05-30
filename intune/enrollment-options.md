---
title: Registreringsalternativ för enheter som hanteras av Microsoft Intune
titleSuffix: ''
description: En lista med registreringsalternativ som administratörer kan ange för enheter som hanteras av Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8af25bb566a944743209d3cad9be0decc36beeb3
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047551"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Registreringsalternativ för enheter som hanteras av Intune

Som Intune-administratör kan du konfigurera enhetsregistreringen för att hjälpa användarna och aktivera Intune-funktioner.  Intune innehåller följande registreringsalternativ:

## <a name="terms-and-conditions"></a>Villkor

Du kan kräva att användarna måste godkänna företagets allmänna villkor innan de kan använda företagsportalen för att registrera sina enheter och få åtkomst till företagsresurser som appar och e-post. Konfigurationen av de allmänna villkoren är valfri. Läs mer om [villkor](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Registreringsbegränsningar

Du kan välja att begränsa enhetsregistreringen efter:
- Enhetsplattform
- Antalet enheter per användare
- Blockera personliga enheter

Läs mer om [registreringsbegränsningar](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Aktivera Apple-enhetsregistrering

Det krävs ett MDM-pushcertifikat för registrering av iOS- och Mac OS enheter. Läs mer om [MDM-pushcertifikat](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Företagsidentifierare

Du kan visa en lista över IMEI-nummer (International Mobile Equipment Identifier) och serienummer för att identifiera företagsägda enheter. Läs mer om [företagsidentifierare](corporate-identifiers-add.md).
## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

Du kan kräva att användare använder en extra verifieringsmetod, exempelvis telefon, PIN-kod eller biometriska data när de registrera en enhet. Läs mer om [multifaktorautentisering](multi-factor-authentication.md).

## <a name="device-enrollment-manager"></a>Hanterare av enhetsregistrering
Du kan utse användare till enhetsregistreringshanterare (DEM).  Enhetsregistreringshanterare kan registrera många mobila enheter med ett enda användarkonto. Kontot för en enhetsregistreringshanterare kan registrera upp till 1 000 enheter. Läs mer om [enhetsregistreringshanterare](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Enhetskategorier

Du kan använda enhetskategorier för att automatiskt lägga till enheter i grupper baserat på kategorier som du definierar. Det blir enklare att hantera enheterna om du lägger till dem i grupper. Läs mer om [enhetskategorier](device-group-mapping.md).
