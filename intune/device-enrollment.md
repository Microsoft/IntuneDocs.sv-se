---
title: "Vad är enhetsregistrering i Microsoft Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig mer om registrering av iOS-, Android- och Windows-enheter."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 57bad4be991b61fe5212d340ab8d89cb6af3b0f7
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="what-is-device-enrollment"></a>Vad är enhetsregistrering?
[!INCLUDE[azure_preview](./includes/azure_preview.md)]

I det här avsnittet beskrivs olika sätt att registrera mobila enheter i Intune-hanteringen.

Registrera enheterna i Intune så att du kan hantera dem. Vi refererar till den här funktionen i Intune-dokumentationen som hantering av mobila enheter (MDM). När enheterna har registrerats i Intune utfärdas ett MDM-certifikat som enheterna sedan använder för att kommunicera med Intune-tjänsten.

Hur du registrerar dina enheter beror på typen av enhet, ägarskapet och vilken hanteringsnivå som krävs. BYOD (Bring Your Own Device)-registrering låter användare att registrera sina personliga telefoner, surfplattor eller datorer. Registrering av företagsägda enheter möjliggör hanteringsscenarier som automatisk registrering, delade enheter och förauktoriserade registreringskrav.

Om du använder Exchange ActiveSync, antingen lokalt eller med värd i molnet, kan du aktivera enkel Intune-hantering utan registrering (mer information kommer snart). Du kan hantera Windows-datorer som mobila enheter, vilket är den rekommenderade metod som beskrivs nedan.


## <a name="overview-of-device-enrollment-methods"></a>Översikt över registreringsmetoder för enheter

Följande tabell visar Intune-registreringsmetoder och de funktioner som stöds och kraven för varje metod. Funktionerna och kraven beskrivs nedan. I tabellen används följande termer:

- **Rensa** – Anger om enheten måste rensas innan användarna kan registrera enheten. Termen ”rensa” innebär en fabriksåterställning av enheten, vilket tar bort alla data. Mer information finns i [Använd fullständig eller selektiv rensning av enheter](devices-wipe.md).
- **Tillhörighet** – Kopplar enheter till användare. Krävs för hantering av mobila program (MAM) och villkorlig åtkomst till företagsdata. Mer information finns i [Användartillhörighet](device-enrollment-program-enroll-ios.md).
- **Lås** – Indikerar om användare hindras från att avregistrera sina enheter från hanteringen. Användare kan avregistrera sina enheter på alla plattformar med företagsportalappen. De kan inte använda menyerna i operativsystemet för att avregistrera.


**Metoder för iOS-registrering**

| **Metod** |    **Krävs rensning?** |    **Tillhörighet**    |    **Lås** | **Information** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |    Nej | Mer information kommer snart|
|**[DEM](#dem)**|    Nej |Nej |Nej    | [Mer information](device-enrollment-program-enroll-ios.md)|
|**[DEP](#dep)**|    Ja |    Valfri |    Valfri|[Mer information](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**|    Ja |    Valfri |    Nej| [Mer information](apple-configurator-setup-assistant-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**|    Nej |    Nej    | Nej|[Mer information](apple-configurator-direct-enroll-ios.md)|

**Metoder för Windows-registrering**

| **Metod** |    **Krävs rensning?** |    **Tillhörighet**    |    **Lås** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej |    Ja |    Nej | [Mer information](windows-enroll.md)|
|**[DEM](#dem)**|    Nej |Nej |Nej    |[Mer information](device-enrollment-manager-enroll.md)|

**Metoder för Android-registrering**

| **Metod** |    **Krävs rensning?** |    **Tillhörighet**    |    **Lås** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |    Nej | [Mer information](android-enroll.md)|
|**[DEM](#dem)**|    Nej |Nej |Nej    |[Mer information](device-enrollment-program-enroll-ios.md)|
|**Android for Work**| Nej | Ja | Nej| [Mer information](android-enroll.md) |


## <a name="byod"></a>BYOD
"Bring your own device"-användare installerar företagsportalsappen och registrerar sina enheter. Detta gör det möjligt för användare att ansluta till företagets nätverk och till domänen eller Azure Active Directory. För de flesta plattformar måste du aktivera BYOD-registrering för många COD-scenarier. Du kan blockera registrering av personligt ägda iOS- och Android-enheter. Anvisningar finns i [Ange begränsningar för enhetstyp](enrollment-restrictions-set.md#set-device-type-restrictions).

## <a name="corporate-owned-devices"></a>Företagsägda enheter
Företagsägda enheter kan hanteras med Azure-portalen. iOS-enheter kan registreras direkt via de verktyg som tillhandahålls av Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

### <a name="dem"></a>DEM
Enhetsregistreringshanteraren (DEM) är ett särskilt användarkonto som används för att registrera och hantera flera företagsägda enheter. Cheferna kan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](device-enrollment-manager-enroll.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Med Apples program för enhetsregistrering kan du skapa och distribuera principen “trådlöst” till iOS-enheter som har köpts och hanteras med DEP. Enheten registreras första gången användaren sätter på enheten och kör iOS-installationsassistenten. Den här metoden har stöd för **iOS-övervakat** läge, som i sin tur stöder:

  -    Låst registrering
  -    Helskärmsläge och andra avancerade konfigurationer och begränsningar

Mer information om iOS-registrering finns i:

- [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md)
- [Registrera iOS-enheter med enhetsregistreringsprogrammet](device-enrollment-program-enroll-ios.md)
- [Gå tillbaka till tabellen ovan](#overview-of-device-enrollment-methods)

### <a name="usb-sa"></a>USB-SA
IT-administratörer använder Apple Configurator, via USB, för att förbereda varje företagsägd enhet manuellt för registrering med installationsassistenten. IT-administratören skapar en registreringsprofil och exporterar den till Apple Configurator. När användarna får sina enheter uppmanas de att köra installationsassistenten för att registrera sin enhet. Den här metoden har stöd för **iOS-övervakat** läge, som i sin tur stöder:
  -    Låst registrering
  -    Helskärmsläge och andra avancerade konfigurationer och begränsningar

Mer information om iOS-registrering finns i:

- [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md)
- [Registrera iOS-enheter med Configurator och Installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
För direkt registrering måste administratören registrera varje enhet manuellt genom att skapa en registreringsprincip och exportera den till Apple Configurator. USB-anslutna, företagsägda enheter registreras direkt och kräver ingen fabriksåterställning. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program.

Mer information om iOS-registrering finns i:

- [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md)
- [Registrera iOS-enheter med Configurator och direktregistrering](apple-configurator-direct-enroll-ios.md)

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS) kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller i molnet. Mer information kommer snart.

## <a name="supported-device-platforms-and-browsers"></a>Enhetsplattformar och webbläsare som stöds

Se [Enheter och webbläsare som stöds för Intune](https://docs.microsoft.com/intune-classic/get-started/supported-mobile-devices-and-computers)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.

