---
title: "Registrera företagsägda enheter | Microsoft Docs"
description: "Registrera företagsägda enheter på flera olika sätt beroende på typen av enhet, hur den köptes och organisationens behov."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 8ef5f26eced99dac547be727fc96e41c11d3a0e7
ms.lasthandoff: 04/24/2017


---

# <a name="enroll-corporate-owned-devices-by-using-intune"></a>Registrera företagsägda enheter med hjälp av Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Du kan registrera organisationsägda eller företagsägda enheter för hantering med Intune på flera olika sätt beroende på typen av enhet, hur enheten köptes och organisationens behov. Du kan också installera företagsportalappen för att registrera och hantera företagsägda enheter, som i ett BYOD-scenario (”Bring Your Own Device”).

Som standard Som standard tillåts enheter för alla plattformar registreras i Intune. Om du vill blockera enheter från registrering loggar du in på [administrationsportalen för Microsoft Intune](https://manage.microsoft.com) med dina autentiseringsuppgifter som administratör. Välj **Admin** > **Hantering av mobila enheter** > **Registreringsregler** och avmarkera de tillämpliga kryssrutorna för plattformarna du vill blockera.

## <a name="enroll-corporate-owned-ios-devices"></a>Registrera företagsägda iOS-enheter

Registreringsmetoderna för företagsägda enheter är ett bra alternativ för CYOD-scenarier (”Choose Your Own Device”). I en CYOD-miljö betalar organisationen för en enhet som användaren väljer, och organisationen hanterar enheten.

Om du erbjuder användare att välja mellan iOS-enheter kan du förkonfigurera registreringen så att enheten hanteras med Intune från första gången användaren sätter på enheten. Intune stöder registrering via [Apples enhetsregistreringsprogram (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) eller med verktyget Apple Configurator på en Mac-dator för [direkt](ios-direct-enrollment-in-microsoft-intune.md) registrering eller registrering med [Installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

Lär dig hur du [registrerar företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

## <a name="create-a-device-enrollment-manager-account"></a>Skapa ett konto för enhetsregistreringshanterare

Du kan skapa ett konto för enhetsregistreringshanterare (DEM) för en enskild användare i Intune för att hantera många mobila enheter i din organisation. När du har skapat ett DEM-konto, kan en utsedd kontoansvarig registrera fler än de 15 enheter som en standardanvändare kan registrera.

Du kan använda ett DEM-konto för att endast registrera enheter som inte används av en enda, specifika användare. Dessa typer av enheter är till exempel bra för verktygs- eller kassaappar (Point-of-Sale), men inte för användare som behöver åtkomst till e-post eller företagsresurser.

Lär dig hur du [registrerar företagsägda enheter med ett DEM-konto](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md).

## <a name="enroll-corporate-owned-windows-10-enterprise-devices"></a>Registrera företagsägda Windows 10 Enterprise-enheter

Om du använder Azure Active Directory Premium eller Microsoft Enterprise Mobility Suite i din organisation kan du [registrera Windows 10 Enterprise-enheter](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview). När en användare lägger till ett arbets- eller skolkonto på en enhet märks enheten automatiskt som ”företagsägd”.

## <a name="import-imei-numbers"></a>Importera IMEI-nummer

Många tillverkare av mobila enheter använder ett unikt nummer kallat IMEI (International Mobile Equipment Identity) på sina enheter. Du kan importera IMEI-nummer för enheter som din organisation äger. När enheten hanteras av Intune märks den som en företagsägd enhet.

Lär dig hur du [märker företagsägda enheter med hjälp av IMEI-nummer](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md).

## <a name="identify-a-device-as-corporate-owned"></a>Identifiera en enhet som företagsägd

Intune identifierar en enhet som "företagets" när något av följande villkor är uppfyllt:

 - Enheten [registrerades med ett DEM-konto](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) (alla plattformar).
 - Enheten registrerades med [Apple DEP](ios-device-enrollment-program-in-microsoft-intune.md) eller [Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md) (endast iOS).
 - Enhetstillverkaren [fördeklarerade enheten genom att använda IMEI-nummer](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) (alla plattformar med IMEI-nummer).
 - Enheten är registrerad i [Azure Active Directory eller Enterprise Mobility Suite som en Windows 10 Enterprise-enhet](https://docs.microsoft.com/active-directory/active-directory-azureadjoin-windows10-devices-overview) (endast Windows 10).

När en enhet har taggats som företagets ser du **Företag** i kolumnen **Ägarskap** för den enhetens post i administratörskonsolen. 

