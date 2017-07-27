---
title: "Välj hur du vill registrera Windows-enheter i Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du konfigurerar registrering av Windows-enheter i Microsoft Intune.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Registrera iOS-enheter i Intune

Intune stöder hantering av mobila enheter (MDM) för iPad och iPhone och ger användarna åtkomst till företagets e-post och appar.

Som en Intune-administratör kan du aktivera registrering för iOS-enheter. Du kan tillåta användare att registrera personligt ägda enheter, vilket även kallas ”bring your own device” (BYOD)-registrering. Du kan också aktivera registrering av företagsägda enheter.

## <a name="prerequisites-for-ios-enrollment"></a>Krav för iOS-registrering
Innan du kan aktivera iOS-enheter måste du göra följande:
- [Konfigurera Intune](setup-steps.md) - följande steg konfigurerar din Intune-infrastruktur. I synnerhet kräver registrering av enheter att du [anger en MDM-utfärdare](mdm-authority-set.md).
- [Hämta ett certifikat för Apple MDM Push](apple-mdm-push-certificate-get.md) -Apple kräver ett certifikat för att aktivera hantering av iOS- och macOS-enheter.

När kraven har uppfyllts kan användare installera företagsportalappen och registrera sina personliga iOS-enheter, eller så kan administratören konfigurera hantering av företagsägda iOS-enheter. Administratörer kan också tilldela [enhetsregistreringshanterare](device-enrollment-manager-enroll.md) som kan registrera flera enheter med ett enda hanteringskonto. Intune stöder följande registreringsmetoder för iOS-enheter som ägs av företaget:

## <a name="device-enrollment-program"></a>Program för enhetsregistrering
Företag kan nu hantera iOS-enheter som köpts via Apples program för enhetsregistrering (DEP). Med DEP kan du distribuera en registreringsprofil ”over-the-air” för att hantera enheter. Läs mer om [programmet för enhetsregistrering](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager är ett enhetsregistreringsprogram för skolor. Du kan distribuera en profil för att registrera enheter på samma sätt som i DEP. Lär dig mer om [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Du kan registrera iOS-enheter med Apple Configurator på en Mac-dator. För att förbereda enheter ansluter du dem med USB och installerar en registreringsprofil. Du kan registrera enheter med Apple Configurator på två sätt:
- Registrering med installationsassistenten – fabriksåterställer enheten, förbereder den att köra installationsassistenten och installerar företagets principer för enhetens nya användare.
- Direkt registrering – fabriksåterställer inte enheten och registrerar den med en fördefinierad princip. Den här metoden är för enheter utan användartillhörighet.

Läs mer om [registrering med Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
