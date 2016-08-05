---
title: "Registrera företagsägda enheter | Microsoft Intune"
description: "Företagsägda enheter (COD) kan hanteras på en mängd olika sätt beroende på enheten, hur den köptes och företagets behov."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecfeb73efed4a47256275120c52de232c556adfe
ms.openlocfilehash: 58efadf2f9fc34a31070aff93e86083583630caa


---

# Registrera företagsägda enheter med Microsoft Intune
Organisations- eller företagsägda enheter kan anslutas till hantering av Intune på en mängd olika sätt beroende på enheten, hur den har köpts och organisationens behov. Företagsägda enheter kan också registreras och hanteras genom installation av företagsportalappen, som i BYOD-scenarier (Bring Your Own Device).

## Företagsägda iOS-enheter
Dessa registreringsmetoder är bra för "Välj din egna enhet"(CYOD)-scenarier där organisationen köper in enheter för användare, men behåller hanteringsbefogenheter av enheten. Om din organisation har köpt iOS-enheter kan du konfigurera registreringen så att enheten är hanterad redan första gången dess användare aktiverar den. Intune stöder registrering via [Apples Enhetsregistreringsprogram (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) eller verktyget Apple Configurator på en Mac-dator för registrering [direkt](ios-direct-enrollment-in-microsoft-intune.md) eller med [installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Registrera företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Hanterare av enhetsregistrering
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto som kallas konto för enhetsregistreringshantering. När du har skapat ett konto för enhetsregistreringshantering kan kontot användas av en chef för att registrera mer än de fem enheter som tillåts som standard för normal användare. Att registrera enheter med en enhetsregistreringshanterare fungerar endast för enheter som inte används av en viss användare. Dessa enheter är bra för till exempel återförsäljning- eller verktygsappar men inte bra för användare som behöver åtkomst till e-post eller företagsresurser.

[Registrera företagsägda enheter med enhetsregistreringshanteraren](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## Registrera företagsägda Windows 10-datorer

Om din organisation har Azure Active Directory Premium (AADP) eller Enterprise Management Suite (EMS) kan du [registrera Windows 10 för företag](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). Då markeras de automatiskt som ”företagsägda” när användarna lägger till sina arbets- eller skolkonton.

## Identifiera enheter som företagsägda

Företagsägda enheter listas som **Företag** under **Ägarskap** i listan med enheter. Enheter kan identifieras som företagsägda på följande sätt:

 - [Registrerade med enhetsregistreringshanteraren (DEM)](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)
 - Registrerade med Apples [enhetsregistreringsprogram](ios-device-enrollment-program-in-microsoft-intune.md) eller [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md)
 - [Fördeklarera enheter med IMEI-nummer](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)
 - [Azure Active Directory/Enterprise Management Suite-registrering av Windows 10-enheter](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview)

### IMEI (International Mobile Equipment Identity)

Unika IMEI-siffror är enhetsegenskap som är gemensam för många tillverkare av mobila enheter. Intune-administratörer kan importera IMEI-nummer för enheter som företaget äger. När enheten hanteras av Intune markeras den som en företagsägd enhet.

[Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jul16_HO4-->


