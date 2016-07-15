---
title: "Registrera företagsägda enheter | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: e07053b9b26afacc03e45f2cb104eda6088a1e05


---

# Registrera företagsägda enheter med Microsoft Intune
Organisations- eller företagsägda enheter kan anslutas till hantering av Intune på en mängd olika sätt beroende på enheten, hur den har köpts och organisationens behov.

## Företagsägda iOS-enheter
Dessa registreringsmetoder är bra för "Välj din egna enhet"(CYOD)-scenarier där organisationen köper in enheter för användare, men behåller hanteringsbefogenheter av enheten. Om din organisation har köpt iOS-enheter kan du konfigurera registreringen så att enheten är hanterad redan första gången dess användare aktiverar den. Intune stöder registrering via [Apples Enhetsregistreringsprogram (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) eller verktyget Apple Configurator på en Mac-dator för registrering [direkt](ios-direct-enrollment-in-microsoft-intune.md) eller med [installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Registrera företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Hanterare av enhetsregistrering
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto som kallas konto för enhetsregistreringshantering. När du har skapat ett konto för enhetsregistreringshantering kan kontot användas av en chef för att registrera mer än de fem enheter som tillåts som standard för normal användare. Att registrera enheter med en enhetsregistreringshanterare fungerar endast för enheter som inte används av en viss användare. Dessa enheter är bra för till exempel återförsäljning- eller verktygsappar men inte bra för användare som behöver åtkomst till e-post eller företagsresurser.

[Registrera företagsägda enheter med enhetsregistreringshanteraren](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## IMEI (International Mobile Equipment Identity)
Unika IMEI-siffror är enhetsegenskap som är gemensam för många tillverkare av mobila enheter. Intune-administratörer kan importera IMEI-nummer för enheter som företaget äger. När enheten hanteras av Intune kan den markeras som en företagsägd enhet och lämpliga principer kan appliceras på den.

[Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)



<!--HONumber=Jun16_HO5-->


