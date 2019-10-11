---
title: Vad är enhetsregistrering i Microsoft Intune
titleSuffix: Microsoft Intune
description: Läs om registrering av iOS-, Android- och Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 4/24/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e3fb9af260b8fddc78b644b8ede056c90bac24d0
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999351"
---
# <a name="what-is-device-enrollment"></a>Vad är enhetsregistrering?
[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Med Intune kan du hantera personalens enheter och appar, samt hur de kommer åt företagsdata. Enheterna måste först registreras i Intune-tjänsten innan du kan använda MDM-hanteringen. När en enhet registreras utfärdas ett MDM-certifikat till den. Certifikatet används för att kommunicera med Intune-tjänsten.

Det finns flera metoder för att registrera personalens enheter, vilket visas i följande tabeller. Varje metod påverkas av ägarskapet för enheten (personlig eller företagsägd), enhetstypen (iOS, Windows, Android) och hanteringskraven (återställning, tillhörighet, låsning).

Som standard tillåts enheter för alla plattformar registreras i Intune. Men du kan [begränsa enheter efter plattform](enrollment-restrictions-set.md#create-a-device-type-restriction).

## <a name="ios-enrollment-methods"></a>Metoder för iOS-registrering

| **Metod** | **Återställning krävs** | [**Användartillhörighet**](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) | **Låst** | **Information** |
|:---:|:---:|:---:|:---:|:---:|
| | Enheter rensas under registreringen. | Kopplar varje enhet till en användare.| Det innebär att användarna inte kan avregistrera enheter. | |
|**[BYOD](#bring-your-own-device)** | Nej| Ja | Nej | [Mer information](apple-mdm-push-certificate-get.md)|
|**[DEM](#device-enrollment-manager)**| Nej |Nej |Nej | [Mer information](device-enrollment-program-enroll-ios.md)|
|**[DEP](#apple-device-enrollment-program)**| Ja | Valfri | Valfri|[Mer information](device-enrollment-program-enroll-ios.md)|
|**[USB-SA](#usb-sa)**| Ja | Valfri | Nej| [Mer information](apple-configurator-enroll-ios.md)|
|**[USB-Direct](#usb-direct)**| Nej | Nej | Nej|[Mer information](apple-configurator-enroll-ios.md)|

## <a name="macos-enrollment-methods"></a>Registreringsmetoder för macOS
| **Metod** |  **Återställning krävs** |  **Användartillhörighet** | **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nej| Ja | Nej | [Mer information](macos-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nej |Nej |Nej  | [Mer information](device-enrollment-manager-enroll.md)|
|**[DEP](#apple-device-enrollment-program)**| Ja | Valfri | Valfri|[Mer information](device-enrollment-program-enroll-macos.md)|

## <a name="windows-enrollment-methods"></a>Metoder för Windows-registrering

| **Metod** | **Återställning krävs** | **Användartillhörighet** | **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#bring-your-own-device)** | Nej | Ja | Nej | [Mer information](windows-enroll.md)|
|**[DEM](#device-enrollment-manager)**| Nej |Nej |Nej |[Mer information](device-enrollment-manager-enroll.md)|
|**Registrera automatiskt** | Nej |Ja |Nej | [Mer information](windows-enroll.md#enable-windows-10-automatic-enrollment)|
|**Autopilot** |Ja |Ja |Nej | [Mer information](enrollment-autopilot.md)
|**Massregistrering** |Nej |Nej |Nej | [Mer information](windows-bulk-enroll.md) |
|**Samhantering** |Nej |Ja |Nej | [Mer information](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview)
|**GPO** |Nej |Ja |Nej | [Mer information](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)

## <a name="android-enrollment-methods"></a>Metoder för Android-registrering

| **Personligt** | **Registreringsmetoder** | **Återställning krävs** | **Användartillhörighet** | **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administratör för Android-enhet**|**Användarinitierat via företagsportalen** | Nej | Ja | Nej | [Mer information](https://docs.microsoft.com/intune-user-help/enroll-device-android-company-portal)|
|**Android Enterprise-arbetsprofil**|**Användarinitierat via företagsportalen**| Nej | Ja | Nej | [Mer information](android-work-profile-enroll.md)|


| **Företag** | **Registreringsmetoder** | **Återställning krävs** | **Användartillhörighet** | **Låst** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**Administratör för Android-enhet**|**[DEM](#device-enrollment-manager) initierat via företagsportalen**| Nej | Nej | Nej |[Mer information](device-enrollment-manager-enroll.md)|
|**Administratör för Android-enhet**|**(Förhandsdeklarerad IMEI eller SN) Användarinitierat via företagsportalen**| Nej | Ja | Nej | [Mer information](./../corporate-identifiers-add.md)|
|**Administratör för Android-enhet med Zebra Mobility Extensions**|**Användare eller [DEM](#device-enrollment-manager) initierat via företagsportalen**| Nej | Ja vid användarinitierad, nej vid [DEM](#device-enrollment-manager)-initierad | Nej | [Mer information](../configuration/android-zebra-mx-overview.md)|
|**Android Enterprise-dedikerad**|**NFC, QR-kod, Zero Touch-token**| Ja | Nej | Kan konfigureras via princip | [Mer information](android-kiosk-enroll.md)|
|**Fullständigt hanterad Android Enterprise**|**NFC, QR-kod, Zero Touch-token**| Ja | Ja | Kan konfigureras via princip | [Mer information](android-dedicated-devices-fully-managed-enroll.md)|


## <a name="bring-your-own-device"></a>Bring Your Own Device
Bring Your Own Device (BYOD) omfattar personliga telefoner, surfplattor och datorer. Användarna installerar och kör appen Företagsportal för att registrera sina BYOD-enheter. Det här programmet låter användare komma åt företagsresurser som e-post.

## <a name="corporate-owned-device"></a>Företagsägd enhet
[Företagsägda enheter (COD)](corporate-identifiers-add.md) omfattar telefoner, surfplattor och datorer som ägs av organisationen och distribueras till personalen. COD-registrering har stöd för hanteringsscenarier som automatisk registrering, delade enheter och förauktoriserade registreringskrav. Ett vanligt sätt att registrera COD-enheter är att en administratör eller chef använder enhetsregistreringshanteraren (DEM). iOS-enheter kan registreras direkt via verktygen för programmet för enhetsregistrering (DEP) som tillhandahålls av Apple. Enheter med ett IMEI-nummer kan också identifieras och taggas som företagsägda.

### <a name="device-enrollment-manager"></a>Hanterare av enhetsregistrering
Enhetsregistreringshanteraren (DEM) är ett särskilt användarkonto som används för att registrera och hantera flera företagsägda enheter. Cheferna kan installera företagsportalen och registrera flera användarlösa enheter. Dessa typer av enheter är till exempel bra för verktygs- eller kassaappar (Point-of-Sale), men inte för användare som behöver åtkomst till e-post eller företagsresurser. Läs mer om [DEM](device-enrollment-manager-enroll.md).

### <a name="apple-device-enrollment-program"></a>Apples DEP (Device Enrollment Program)
Med Apples program för enhetsregistrering kan du skapa och distribuera principen ”trådlöst” till iOS- och macOS-enheter som har köpts och hanteras med DEP. Enheten registreras första gången användaren sätter på enheten och kör installationsassistenten. Den här metoden har stöd för övervakat läge för iOS som gör det möjligt att konfigurera en enhet med specifika funktioner.

Läs mer om iOS DEP-registrering:

- [Välj hur du vill registrera iOS-enheter](ios-enroll.md)
- [Registrera iOS-enheter med enhetsregistreringsprogrammet](device-enrollment-program-enroll-ios.md)

### <a name="usb-sa"></a>USB-SA
IT-administratörer använder Apple Configurator, via USB, för att förbereda varje företagsägd enhet manuellt för registrering med installationsassistenten. IT-administratören skapar en registreringsprofil och exporterar den till Apple Configurator. När användarna får sina enheter uppmanas de att köra installationsassistenten för att registrera sin enhet. Den här metoden har stöd för **iOS-övervakat** läge, vilket i sin tur aktiverar följande funktioner:
- Låst registrering
- Helskärmsläge och andra avancerade konfigurationer och begränsningar

Läs mer om iOS Apple Configurator-registrering med installationsassistenten:

- [Välj hur du vill registrera iOS-enheter](ios-enroll.md)
- [Registrera iOS-enheter med Configurator och Installationsassistenten](apple-configurator-enroll-ios.md)

### <a name="usb-direct"></a>USB-Direct
För direkt registrering måste administratören registrera varje enhet manuellt genom att skapa en registreringsprincip och exportera den till Apple Configurator. USB-anslutna, företagsägda enheter registreras direkt och kräver ingen rensning. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program.

Mer information om iOS-registrering finns i:

- [Välj hur du vill registrera iOS-enheter](ios-enroll.md)
- [Registrera iOS-enheter med Configurator och direktregistrering](apple-configurator-enroll-ios.md)

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.
