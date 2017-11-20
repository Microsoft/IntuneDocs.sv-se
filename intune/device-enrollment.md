---
title: "Vad är enhetsregistrering i Microsoft Intune"
titlesuffix: Azure portal
description: "Läs om registrering av iOS-, Android- och Windows-enheter.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: caf399650e0a6382d3e03a133cad3aee1eda2d39
ms.sourcegitcommit: fc24d7eb4838b9102088dd4dcf5d1aa6b2c2e590
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2017
---
# <a name="what-is-device-enrollment"></a>Vad är enhetsregistrering?
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I det här avsnittet beskrivs olika sätt att registrera mobila enheter i Intune-hanteringen.

Registrera enheterna i Intune så att du kan hantera dem. Vi refererar till den här funktionen i Intune-dokumentationen som hantering av mobila enheter (MDM). När enheterna har registrerats i Intune utfärdas ett MDM-certifikat som enheterna sedan använder för att kommunicera med Intune-tjänsten.

Hur du registrerar dina enheter beror på typen av enhet, ägarskapet och vilken hanteringsnivå som krävs. BYOD (Bring Your Own Device)-registrering låter användare att registrera sina personliga telefoner, surfplattor eller datorer. Registrering av företagsägda enheter möjliggör hanteringsscenarier som automatisk registrering, delade enheter och förauktoriserade registreringskrav.

Om du använder Exchange ActiveSync, antingen lokalt eller med värd i molnet, kan du aktivera enkel Intune-hantering utan registrering (mer information kommer snart). Du kan hantera Windows-datorer som mobila enheter, vilket är den rekommenderade metod som beskrivs nedan.


## <a name="overview-of-device-enrollment-methods"></a>Översikt över registreringsmetoder för enheter

Följande tabell ger en översikt över registreringsmetoder för Intune med funktioner och krav beskrivna nedan.

**Förklaring**

- **Återställning krävs** – enheterna fabriksåterställs vid registreringen.
- **Användartillhörighet** – Kopplar enheter till användare. Mer information finns i [Användartillhörighet](device-enrollment-program-enroll-ios.md).
- **Låst** – förhindrar användare från att avregistrera enheter.

**Metoder för iOS-registrering**

| **Metod** |  **Återställning krävs** |    **Användartillhörighet**   |   **Låst** | **Information** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [Mer information](./apple-mdm-push-certificate-get.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  | [Mer information](./device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|   Ja |   Valfri |  Valfri|[Mer information](./device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Ja |   Valfri |  Nej| [Mer information](./apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Nej |    Nej  | Nej|[Mer information](./apple-configurator-direct-enroll-ios.md)|

**Metoder för Windows-registrering**

| **Metod** |  **Återställning krävs** |    **Användartillhörighet**   |   **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej |   Ja |   Nej | [Mer information](windows-enroll.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  |[Mer information](device-enrollment-manager-enroll.md)|
|**Registrera automatiskt** | Nej |Ja |Nej | [Mer information](./windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Massregistrering** |Nej |Nej |Nej | [Mer information](./windows-bulk-enroll.md) |

**Metoder för Android-registrering**

| **Metod** |  **Återställning krävs** |    **Användartillhörighet**   |   **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [Mer information](./android-enroll.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  |[Mer information](./device-enrollment-program-enroll-ios.md)|
|**Android for Work**| Nej | Ja | Nej| [Mer information](./android-enroll.md#enable-enrollment-of-android-for-work-devices) |


## <a name="byod"></a>BYOD
"Bring your own device" användare installerar och kör företagsportalappen för att registrera sina enheter. Det här programmet låter användare komma åt företagsresurser som e-post.

## <a name="corporate-owned-devices"></a>Företagsägda enheter
Här följer några scenarier för registrering av företagsägda enheter (COD). iOS-enheter kan registreras direkt via de verktyg som tillhandahålls av Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

### <a name="dem"></a>DEM
Enhetsregistreringshanteraren (DEM) är ett särskilt användarkonto som används för att registrera och hantera flera företagsägda enheter. Cheferna kan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](./device-enrollment-manager-enroll.md).

### <a name="dep"></a>DEP
Med Apples program för enhetsregistrering kan du skapa och distribuera principen “trådlöst” till iOS-enheter som har köpts och hanteras med DEP. Enheten registreras första gången användaren sätter på enheten och kör iOS-installationsassistenten. Den här metoden har stöd för övervakat läge för iOS som gör det möjligt att konfigurera en enhet med specifika funktioner.

Läs mer om iOS DEP-registrering:

- [Välj hur du vill registrera iOS-enheter](ios-enroll.md)
- [Registrera iOS-enheter med enhetsregistreringsprogrammet](https://docs.microsoft.com/intune/device-restrictions-ios#device-enrollment-program)

### <a name="usb-sa"></a>USB-SA
IT-administratörer använder Apple Configurator, via USB, för att förbereda varje företagsägd enhet manuellt för registrering med installationsassistenten. IT-administratören skapar en registreringsprofil och exporterar den till Apple Configurator. När användarna får sina enheter uppmanas de att köra installationsassistenten för att registrera sin enhet. Den här metoden har stöd för **iOS-övervakat** läge, vilket i sin tur aktiverar följande funktioner:
  - Låst registrering
  - Helskärmsläge och andra avancerade konfigurationer och begränsningar

Läs mer om iOS Apple Configurator-registrering med installationsassistenten:

- [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md)
- [Registrera iOS-enheter med Configurator och Installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
För direkt registrering måste administratören registrera varje enhet manuellt genom att skapa en registreringsprincip och exportera den till Apple Configurator. USB-anslutna, företagsägda enheter registreras direkt och kräver ingen fabriksåterställning. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program.

Mer information om iOS-registrering finns i:

- [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md)
- [Registrera iOS-enheter med Configurator och direktregistrering](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS), kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller i molnet. Mer information kommer snart.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.
