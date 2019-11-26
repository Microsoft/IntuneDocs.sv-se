---
title: Lägga till filinställningar för macOS-enheter i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till en XML-eller plist-fil som innehåller viktig information om din app. Använd en inställnings fil enhets konfigurations profil för att ändra nyckelinformation i filen med egenskaps listan och tilldela den till dina macOS-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acad2e8539da7210c349ffb254af62f370af5f6
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391504"
---
# <a name="add-a-property-list-file-to-macos-devices-using-microsoft-intune"></a>Lägg till en fil med en egenskaps lista till macOS-enheter med Microsoft Intune

Med hjälp av Microsoft Intune kan du lägga till en fil för egenskaps listan (. plist) för macOS-enheter eller appar på macOS-enheter.

Den här funktionen gäller för:

- macOS-enheter som kör 10,7 och senare

Filer med egenskaps listor innehåller vanligt vis information om macOS-program. Mer information finns i avsnittet [om informations egenskaps listor filer](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html) (Apples webbplats) och [anpassade nytto Last inställningar](https://support.apple.com/guide/mdm/custom-mdm9abbdbe7/1/web/1).

Den här artikeln listar och beskriver de olika fil inställningar för egenskaps listor som du kan lägga till i macOS-enheter. Som en del av din lösning för hantering av mobila enheter (MDM) använder du de här inställningarna för att lägga till programpaket-ID: t (`com.company.application`) och lägga till dess. plist-fil.

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa profilen](device-profile-create.md).

## <a name="what-you-need-to-know"></a>Vad du behöver veta

- De här inställningarna har inte verifierats. Se till att testa dina ändringar innan du tilldelar profilen till dina enheter.
- Om du inte är säker på hur du anger en app-nyckel ändrar du inställningen i appen. Granska sedan appens inställnings fil med hjälp av [Xcode](https://developer.apple.com/xcode/) för att se hur inställningen konfigureras. Apple rekommenderar att du tar bort icke-hanterbara inställningar med Xcode innan du importerar filen.
- Endast vissa appar fungerar med hanterade inställningar och du kanske inte kan hantera alla inställningar.
- Se till att ladda upp filer för egenskaps listor som är riktade mot enhets kanal inställningar, inte inställningar för användar kanal. Egenskaps listans filer är riktade till hela enheten.

## <a name="preference-file"></a>Inställnings fil

- **Preferens domän namn**: filer med egenskaps listor används vanligt vis för webbläsare (Microsoft Edge), [Microsoft Defender Avancerat skydd](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)och anpassade appar. När du skapar en inställnings domän skapas även ett paket-ID. Ange paket-ID: t, till exempel `com.company.application`. Ange till exempel `com.Contoso.applicationName`, `com.Microsoft.Edge` eller `com.microsoft.wdav`.
- **Egenskaps lista fil**: Välj den egenskaps list fil som är kopplad till din app. Se till att det är en `.plist`-eller `.xml`-fil. Du kan till exempel Ladda upp en `YourApp-Manifest.plist` eller `YourApp-Manifest.xml` fil.
- **Fil innehåll**: nyckelinformation i filen med egenskaps listan visas. Om du behöver ändra nyckelinformation öppnar du list filen i en annan redigerare och laddar sedan om filen i Intune.

Välj **OK** > **Skapa** för att spara ändringarna. Profilen skapas och visas i profillistan.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. [Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
