---
title: inställningar för macOS kernel-tillägg i Microsoft Intune-Azure | Microsoft Docs
titleSuffix: ''
description: Lägg till, konfigurera eller skapa inställningar på macOS-enheter för att använda kernel-tillägg. Tillåt också att användare åsidosätter godkända tillägg, tillåter alla tillägg från ett team-ID eller tillåter vissa tillägg eller appar i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89f54111258b5e628d9f83c381fde146bf996216
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206337"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>macOS-enhets inställningar för att konfigurera och använda kernel-tillägg i Intune



I den här artikeln beskrivs de olika inställningar för kerneltillägg som du kan kontrollera på macOS-enheter. Som en del av din lösning för hantering av mobila enheter (MDM) använder du dessa inställningar för att lägga till och hantera kernel-tillägg på dina enheter.

Mer information om kernel-tillägg i Intune och eventuella krav finns i [lägga till MacOS kernel-tillägg](../kernel-extensions-overview-macos.md).

Dessa inställningar läggs till en profil för enhetskonfiguration i Intune som sedan tilldelas eller distribueras till dina macOS-enheter.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en konfigurations profil för enhets kernel-tillägg](../kernel-extensions-overview-macos.md).

> [!NOTE]
> De här inställningarna gäller för olika registrerings typer. Mer information om de olika registrerings typerna finns i [MacOS-registrering](../macos-enroll.md).

## <a name="kernel-extensions"></a>Kernel-tillägg

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>Inställningarna gäller för: användare godkänd, automatisk enhets registrering

- **Tillåt åsidosättning av användare**: Tillåt tillåter användare **att** godkänna kernel-tillägg som inte ingår i konfigurations profilen. **Inte konfigurerat** (standard) förhindrar användare från att tillåta tillägg som inte ingår i konfigurations profilen. Det innebär att endast tillägg som ingår i konfigurations profilen tillåts.

  Mer information om den här funktionen finns i [User-godkänd Kernel Extension inläsning](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (öppnar Apples webbplats).

- **Tillåtna team identifierare**: Använd den här inställningen om du vill tillåta ett eller flera team-ID: n. Alla kernel-tillägg som är signerade med de grupp-ID: n som du anger är tillåtna och betrodda. Med andra ord kan du använda det här alternativet för att tillåta alla kernel-tillägg i samma team-ID, som kan vara en speciell utvecklare eller partner.

  **Lägg till** ett team-ID för giltiga och signerade kernel-tillägg som du vill läsa in. Du kan lägga till flera team identifierare. Team-ID: n måste vara alfanumerisk (bokstäver och siffror) och ha 10 tecken. Ange till exempel `ABCDE12345`.

  När du har lagt till ett team-ID kan den också tas bort.

  [Leta upp ditt team-ID](https://help.apple.com/developer-account/#/dev55c3c710c) (öppna Apples webbplats) om du vill ha mer information.

- **Tillåtna kernel-tillägg**: Använd den här inställningen för att tillåta vissa kernel-tillägg. Endast de kernel-tillägg som du anger är tillåtna eller betrodda. 

  **Lägg till** paket identifieraren och team identifieraren för ett kernel-tillägg som du vill läsa in. Använd ett tomt Team-ID för osignerade gamla kernel-tillägg. Du kan lägga till flera kernel-tillägg. Team-ID: n måste vara alfanumerisk (bokstäver och siffror) och ha 10 tecken. Ange till exempel `com.contoso.appname.macos` för **paket-ID**och `ABCDE12345` för **team**-ID.

  > [!TIP]
  > Om du vill hämta paket-ID: t för ett kernel-tillägg (KEXT) på en macOS-enhet kan du:
  >
  > 1. Kör `kextstat | grep -v com.apple`i terminalen och anteckna utdata. Installera den program vara eller KEXT som du vill använda. Kör `kextstat | grep -v com.apple` igen och leta efter ändringar.
  >
  >    I terminalen visar `kextstat` alla kernel-tillägg på operativ systemet. 
  >
  > 2. På enheten öppnar du filen med informationens egenskaps lista (info. plist) för en KEXT. Paket-ID: t visas. Varje KEXT har en info. plist-fil som lagras i. 

> [!NOTE]
> Du behöver inte lägga till Team identifierare och kernel-tillägg. Du kan konfigurera en eller ett annat.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](../device-profile-assign.md) och [övervaka dess status](../device-profile-monitor.md).
