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
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4f3424c0d9712affbbf8ba3929e825b62ce5864
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71940324"
---
# <a name="enroll-ios-devices-in-intune"></a>Registrera iOS-enheter i Intune

Intune stöder hantering av mobila enheter (MDM) för iPad och iPhone och ger användarna säker åtkomst till företagets e-post, data och appar.

Som Intune-administratör kan du konfigurera registrering för iOS- och iPad-enheter för åtkomst till företagets resurser. Du kan låta användare registrera personligt ägda enheter, även kallat BYOD-registrering (Bring Your Own Device). Du kan också konfigurera registrering av företagsägda enheter.

## <a name="prerequisites-for-ios-enrollment"></a>Krav för iOS-registrering

Innan du kan aktivera iOS-enheter måste du göra följande:

- [Kontrollera att enheten är kvalificerad för registrering av Apple-enheter](https://support.apple.com/en-us/HT204142#eligibility).
- [Konfigurera Intune](../fundamentals/setup-steps.md) - följande steg konfigurerar din Intune-infrastruktur. I synnerhet kräver registrering av enheter att du [anger en MDM-utfärdare](../fundamentals/mdm-authority-set.md).
- [Hämta ett certifikat för Apple MDM Push](apple-mdm-push-certificate-get.md) -Apple kräver ett certifikat för att aktivera hantering av iOS- och macOS-enheter.

## <a name="user-owned-ios-and-ipados-devices-byod"></a>Användarägda iOS- och iPad-enheter (BYOD)

Du kan låta användare registrera sina personliga enheter för Intune-hantering, vilket kallas "bring your own device" eller BYOD. Det finns tre användarregistreringsalternativ:
- Appskyddsprinciper ger den enklaste BYOD-upplevelsen, med hantering endast på appnivå. Om du även vill skydda enheten med en 6-siffrig komplex PIN-kod kan du använda dessa principer tillsammans med Användarregistrering.
- Enhetsregistrering är antagligen det du tänker på när du tänker på en typisk BYOD-registrering. Med Enhetsregistrering har administratörer tillgång till en rad olika hanteringsalternativ.
- Användarregistrering är en enklare registreringsprocess som ger tillgång till en mindre uppsättning enhetshanteringsalternativ. Den här funktionen finns för närvarande som en förhandsversion. 

När alla krav är uppfyllda och du har tilldelat licenser till användarna, kan de ladda ned företagsportalappen för Intune från App Store och följa instruktionerna för registrering i appen. Du kan anpassa sekretesspolicyn för Företagsportal på iOS-enheter enligt beskrivningen i [anpassning av sekretesspolicy](../apps/company-portal-app.md#privacy-statement-customization).

## <a name="company-owned-ios-devices"></a>Företagsägda iOS-enheter

Intune stöder följande registreringsmetoder för iOS-enheter som ägs av företaget för organisationer som köper enheter till sina användare:

- Apples program för enhetsregistrering (DEP)
- Apple School Manager
- Apple Configurator-registrering med installationsassistenten
- Apple Configurator – direkt registrering

Du kan även registrera företagsägda iOS-enheter med ett konto för [enhetsregistreringshantering](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Program för enhetsregistrering

Företag kan nu hantera iOS-enheter som köpts via Apples program för enhetsregistrering (DEP). Med DEP kan du distribuera en registreringsprofil ”over-the-air” för att hantera enheter. Mer information finns i [Programmet för enhetsregistrering](device-enrollment-program-enroll-ios.md).

## <a name="user-enrollment"></a>Användarregistrering
Med Användarregistrering får administratörer tillgång till en deluppsättning hanteringsalternativ jämfört med andra registreringsmetoder. Mer information finns i [Åtgärder, lösenord och andra alternativ som stöds i Användarregistrering](ios-user-enrollment-supported-actions.md) och [Konfigurera Användarregistrering för iOS och iPadOS](ios-user-enrollment.md).

## <a name="apple-school-manager"></a>Apple School Manager

Apple School Manager är ett enhetsregistreringsprogram för skolor. Du kan distribuera en profil för att registrera enheter på samma sätt som i DEP. Lär dig mer om [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator

Du kan registrera iOS-enheter med Apple Configurator på en Mac-dator. För att förbereda enheter ansluter du dem med USB och installerar en registreringsprofil. Du kan registrera enheter med Apple Configurator på två sätt:

- Registrering med installationsassistenten – rensar enheten, förbereder den för att köra installationsassistenten och installerar företagets principer för enhetens nya användare.
- Direktregistrering – rensar inte enheten och registrerar den med en fördefinierad princip. Den här metoden är för enheter utan användartillhörighet.

Läs mer om [registrering med Apple Configurator](apple-configurator-enroll-ios.md).

## <a name="use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices"></a>Använda företagsportalen på enheter som registrerats med enhetsregistreringsprogrammet eller Apple Configurator

Enheter som har konfigurerats med användartillhörighet kan installera och köra företagsportalappen för att ladda ned appar och hantera enheter. Efter det att användarna fått sina enheter måste de utföra ett antal ytterligare steg för att slutföra installationen och installera företagsportalsappen.

Användartillhörighet krävs för att ge stöd åt följande:

- Hantering av mobilprogramsappar (MAM, Mobile Application Management)
- Villkorlig åtkomst till e-post och företagsdata
- Företagsportalappen

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Hur en användare registrerar företagsägda iOS-enheter med användartillhörighet

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
