---
title: "Välj hur du vill registrera iOS-enheter i Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du konfigurerar registrering av iOS-enheter i Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>Välj hur du vill registrera iOS- och macOS-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I det här avsnittet beskrivs de metoder som en IT-administratör kan använda för att aktivera registrering av iOS-enheter i Intune.

Använd följande information när du ska bestämma vilken metod som ska användas för att registrera iOS-enheter. Alla av de följande metoderna, förutom BYOD, är avsedda för registrering av företagsägda enheter.

**Krav:** Ett [certifikat för Apple Push Notification Service](apple-mdm-push-certificate-get.md) krävs.

## <a name="user-owned-ios-devices-byod"></a>Användarägda iOS-enheter (BYOD)

Om användarna vill registrera sina personliga BYOD-enheter, så kan de hämta företagsportalsappen för iOS från App Store och sedan följa registreringsanvisningarna i appen. När registreringen är klar kan användarna ansluta till företagets nätverk, ansluta till domänen eller Azure Active Directory och få åtkomst till företagets resurser. Om du vill aktivera BYOD är det enda kravet att du har ett [certifikat för Apple Push Notification Service](apple-mdm-push-certificate-get.md). Du kan även blockera registrering av personligt ägda iOS-enheter. Anvisningar finns i [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md).

## <a name="user-owned-macos-devices-byod"></a>Användarägda macOS-enheter (BYOD)

Du kan aktivera registrering av macOS-enheter. Om du vill aktivera registrering av macOS är det enda kravet att du har ett [certifikat för Apple Push Notification Service](apple-mdm-push-certificate-get.md). Mer information finns i [Registrera macOS-enheter](./macos-enroll.md)

## <a name="enrollment-program-with-apple"></a>Registreringsprogram med Apple
Apple erbjuder inköpsprogram för enheter som omfattar en infrastruktur för registrering och hantering av enheter. Enheter som köpts via något av dessa program kan massregistreras trådlöst genom att tilldelas ett enhetsserienummer för Intune-hantering.

- **Programmet för enhetsregistrering** – Apples enhetsregistreringsprogram för organisationer och företag. Mer information finns i [Registrera iOS-enheter med enhetsregistreringsprogrammet](device-enrollment-program-enroll-ios.md).
- **Apple School Manager** – Apples enhetsregistreringsprogram för skolor. Mer information finns i [Aktivera registrering av iOS-enheter med Apple School Manager](apple-school-manager-set-up-ios.md)

## <a name="apple-configurator"></a>Apple Configurator

Du kan registrera iOS-enheter genom att exportera en företagsregistreringsprofil och sedan ansluta de mobila enheterna till en Mac som kör Apple Configurator. Apple Configurator stöder två typer av registrering:

- **Registrering av installationsassistenten**: Återställer enheten till fabriksinställningarna och förbereder den för installation av enhetens nya användare. Den här metoden kräver att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator så att registreringen kan förkonfigureras. Enheterna levereras sedan till de användare som kör installationsassistenten när enheten startas första gången. Den här processen konfigurerar enheten med användarnas autentiseringsuppgifter arbetet eller skolan och slutför registreringen. Mer information finns i [Registrera iOS-enheter med Apple Configurator och installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md).

- **Direktregistrering**: Skapar en Apple Configurator-kompatibel fil som används vid förberedelse av enheten. Den registrerade enheten är inte fabriksåterställd, och den har ingen anknytning till användaren. För att kunna registrera enheter krävs det att administratören ansluter iOS-enheten via USB till en Mac-dator som kör Apple Configurator. Mer information finns i [Registrera iOS-enheter som använder direktregistrering i Apple Configurator](apple-configurator-direct-enroll-ios.md).

## <a name="use-the-device-enrollment-program-dep"></a>Använd enhetsregistreringsprogrammet (DEP)

DEP distribuerar en registreringsprofil trådlöst till enheter som köpts via DEP. Enheten registreras i Intune när användaren kör installationsassistenten på enheten när den startas första gången. Mer information finns i [Registrera iOS-enheter med enhetsregistreringsprogrammet](device-enrollment-program-enroll-ios.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Använda enhetsregistreringshanteraren (DEM)
Enhetsregistreringshanteraren är ett generiskt användarkonto som kan registrera upp till 1 000 enheter. DEM-hanterade enheter kan inte ha användartillhörighet, så de kan inte ha någon ägare. Du ger Intune-användare DEM-behörigheter så att de ska få tillgång till dessa funktioner. Varje enhet som en DEM-användare registrerar använder en enda Intune-licens. Mer information finns i [Registrera enheter med enhetsregistreringshanteraren](device-enrollment-manager-enroll.md).
