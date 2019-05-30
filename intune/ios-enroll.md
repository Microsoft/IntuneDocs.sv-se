---
title: Registrera iOS-enheter i Intune
titleSuffix: Microsoft Intune
description: Konfigurera registrering av iOS-enheter i Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 943aa8361778c60f498f6b1919299d99bf678fd9
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047114"
---
# <a name="enroll-ios-devices-in-intune"></a>Registrera iOS-enheter i Intune

Intune stöder hantering av mobila enheter (MDM) för iPad och iPhone och ger användarna åtkomst till företagets e-post och appar.

Som en Intune-administratör kan du aktivera registrering för iOS-enheter. Du kan låta användare registrera personligt ägda enheter, vilket även kallas ”bring your own device” (BYOD)-registrering. Du kan också aktivera registrering av företagsägda enheter.

## <a name="prerequisites-for-ios-enrollment"></a>Krav för iOS-registrering
Innan du kan aktivera iOS-enheter måste du göra följande:
- [Konfigurera Intune](setup-steps.md) - följande steg konfigurerar din Intune-infrastruktur. I synnerhet kräver registrering av enheter att du [anger en MDM-utfärdare](mdm-authority-set.md).
- [Hämta ett certifikat för Apple MDM Push](apple-mdm-push-certificate-get.md) -Apple kräver ett certifikat för att aktivera hantering av iOS- och macOS-enheter.

## <a name="user-owned-ios-devices-byod"></a>Användarägda iOS-enheter (BYOD)

Du kan låta användare registrera sina personliga enheter för Intune-hantering, vilket kallas "bring your own device" eller BYOD. När du uppfyller kraven och har tilldelat licenser till användarna, kan de ladda ned företagsportalappen för Intune från App Store och följa instruktionerna för registrering i appen.

## <a name="company-owned-ios-devices"></a>Företagsägda iOS-enheter
Intune stöder följande registreringsmetoder för iOS-enheter som ägs av företaget för organisationer som köper enheter till sina användare:

- Apples program för enhetsregistrering (DEP)
- Apple School Manager
- Apple Configurator-registrering med installationsassistenten
- Apple Configurator – direkt registrering

Du kan även registrera företagsägda iOS-enheter med ett konto för [enhetsregistreringshantering](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Program för enhetsregistrering
Företag kan nu hantera iOS-enheter som köpts via Apples program för enhetsregistrering (DEP). Med DEP kan du distribuera en registreringsprofil ”over-the-air” för att hantera enheter. Läs mer om [programmet för enhetsregistrering](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager är ett enhetsregistreringsprogram för skolor. Du kan distribuera en profil för att registrera enheter på samma sätt som i DEP. Lär dig mer om [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
Du kan registrera iOS-enheter med Apple Configurator på en Mac-dator. För att förbereda enheter ansluter du dem med USB och installerar en registreringsprofil. Du kan registrera enheter med Apple Configurator på två sätt:
- Registrering med installationsassistenten – rensar enheten, förbereder den för att köra installationsassistenten och installerar företagets principer för enhetens nya användare.
- Direktregistrering – rensar inte enheten och registrerar den med en fördefinierad princip. Den här metoden är för enheter utan användartillhörighet.

Läs mer om [registrering med Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Använda företagsportalen på enheter som registrerats med enhetsregistreringsprogrammet eller Apple Configurator

Enheter som har konfigurerats med användartillhörighet kan installera och köra företagsportalappen för att ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ett antal ytterligare steg för att slutföra installationen och installera företagsportalsappen.

Användartillhörighet krävs för att ge stöd åt följande:
  - Hantering av mobilprogramsappar (MAM, Mobile Application Management)
  - Villkorlig åtkomst till e-post och företagsdata
  - Företagsportalappen

**Hur en användare registrerar företagsägda iOS-enheter med användartillhörighet**
1. När användaren startar enheten uppmanas han eller hon att slutföra arbetet med installationsassistenten. 
2. Efter installationen uppmanas användarna att ange ett Apple-ID. Användarna måste ange ett Apple-ID för att företagsportalen ska kunna installeras på enheten. 
3. Företagsportalappen installeras automatiskt på iOS-enheten från App Store.
4. Användarna bör starta företagsportalappen och logga in med de autentiseringsuppgifter (unikt namn eller UPN) som är associerade med prenumerationen i Intune. 
5. Registreringen är färdig när du har loggat in. Användarna kan nu använda den här enheten med fullständiga funktioner.

### <a name="about-corporate-owned-managed-devices-with-no-user-affinity"></a>Om företagsägda hanterade enheter som saknar användartillhörighet

Det går inte att använda företagsportalen i enheter som har konfigurerats utan användartillhörighet. Appen ska därför inte installeras på dessa. Företagsportalen är avsedd för användare som har företagsautentiseringsuppgifter och behöver åtkomst till anpassade företagsresurser (t.ex. e-post). Enheter som har registrerats utan användartillhörighet är inte avsedda för dedikerad användarinloggning. Informationsenheter, POS-enheter (Point Of Sale) och enheter med delade verktyg är typiska exempel på enheter som registrerats utan användartillhörighet.

Om användartillhörighet krävs måste du välja **Användartillhörighet** för enhetens registreringsprofil innan du registrerar enheten. Om du vill ändra tillhörighetsstatus på en enhet måste du ta enheten ur bruk och registrera den på nytt.

## <a name="see-also"></a>Se även

[Felsöka problem med registrering av iOS-enhet i Microsoft Intune](https://support.microsoft.com/help/4039809)
