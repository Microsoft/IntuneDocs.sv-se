---
title: Registrera enheter | Microsoft Intune
description: "Hantering av mobila enheter (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: a6e5148996b1010f0248f5b122246e38c3aa0464


---

# <a name="enroll-devices-for-management-in-intune"></a>Registrera enheter för hantering i Intune
Du kan registrera enheter, inklusive Windows-datorer, för att aktivera hantering av mobila enheter (MDM) med Microsoft Intune. Det här avsnittet beskriver olika sätt att registrera mobila enheter i Intune-hanteringen. Hur du registrera dina enheter beror på typen av enhet, ägarskapet och vilken hanteringsnivå som krävs. BYOD (Bring Your Own Device)-registrering låter användare att registrera sina personliga telefoner, surfplattor eller datorer. Registrering av företagsägda enheter (COD) gör hanteringsscenarier som fjärrensning, delade enheter och användartillhörighet för en enhet möjliga.

Om du använder [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), antingen lokalt eller med värd i molnet, kan du aktivera enkel Intune-hantering utan registrering. Windows-datorer kan också hanteras med [Intune-klientprogrammet](#manage-windows-pcs-with-intune).

## <a name="overview-of-device-enrollment-methods"></a>Översikt över registreringsmetoder för enheter

Följande tabell visar Intune-registreringsmetoder och de funktioner som stöds och kraven för varje metod. Funktionerna och kraven beskrivs nedan.

- **Rensa** – Anger om enheten måste rensas innan användarna kan registrera enheten. Termen ”rensa” innebär en fabriksåterställning av enheten, vilket tar bort alla data. Mer information finns i [Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md).
- **Tillhörighet** – Kopplar enheter till användare. Krävs för hantering av mobila program (MAM) och villkorlig åtkomst till företagsdata. Mer information finns i [Användartillhörighet](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#use-the-company-portal-on-dep-enrolled-or-apple-configurator-enrolled-devices).
- **Lås** – Förhindrar att användare kan ta bort enheten från hanteringen. iOS-enheter kräver Övervakat läge för Lås. Mer information finns i [Fjärrlåsning](retire-devices-from-microsoft-intune-management.md#block-access-a-device).

**Metoder för iOS-registrering**

| **Metod** |  **Krävs rensning?** |    **Tillhörighet**    |   **Lås** | **Information** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [Mer information](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  | [Mer information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Ja |   Valfri |  Valfri|[Mer information](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Ja |   Valfri |  Nej| [Mer information](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Nej |    Nej  | Nej|[Mer information](ios-direct-enrollment-in-microsoft-intune.md)|

**Metoder för Windows-registrering**

| **Metod** |  **Krävs rensning?** |    **Tillhörighet**    |   **Lås** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Ja|   Ja |   Nej | [Mer information](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  |[Mer information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

**Metoder för Android-registrering**

| **Metod** |  **Krävs rensning?** |    **Tillhörighet**    |   **Lås** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [Mer information](prerequisites-for-enrollment.md)|
|**[DEM](#dem)**|   Nej |Nej |Nej  |[Mer information](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

Ett antal frågor som hjälper dig att hitta rätt metod finns i [Välj hur du vill registrera enheter](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD
"Bring your own device"-användare installerar företagsportalsappen och registrerar sina enheter. Detta gör det möjligt för användare att ansluta till företagets nätverk och till domänen eller Azure Active Directory. För de flesta plattformar måste du aktivera BYOD-registrering för många COD-scenarier. Mer information finns i [Krav för enhetsregistrering](prerequisites-for-enrollment.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Företagsägda enheter
Företagsägda enheter (COD) kan hanteras med Intune-konsolen. iOS-enheter kan registreras direkt via de verktyg som tillhandahålls av Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

Mer information finns i [Registrera enheter som ägs av företaget](manage-corporate-owned-devices.md).

### <a name="dem"></a>DEM
Enhetsregistreringshanteraren är ett särskilt Intune-konto som används för att registrera och hantera flera företagsägda enheter. Cheferna kan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Med Apples program för enhetsregistrering kan du skapa och distribuera principen “trådlöst” till iOS-enheter som har köpts och hanteras med DEP. Enheten registreras första gången användaren sätter på enheten och kör iOS-installationsassistenten. Den här metoden har stöd för **iOS-övervakat** läge, som i sin tur stöder:
  - Låst registrering
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
USB-anslutna företagsägda enheter förbereds med Intune-principen. Vid registrering med Installationsagenten skapar administratören den här Intune-principen och exporterar den till Apple Configurator. Administratören måste registrera varje enhet manuellt. Användarna får sina enheter och kör Installationsassistenten, där de registrerar sina enheter. Den här metoden har stöd för **iOS-övervakat** läge, som i sin tur stöder:
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [Registrering av installationsassistenten med Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### <a name="usb-direct"></a>USB-Direct
Vid direkt registrering skapar administratören en Intune-princip och exporterar den till Apple Configurator. USB-anslutna, företagsägda enheter registreras direkt och kräver ingen fabriksåterställning. Administratören måste registrera varje enhet manuellt. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program. Läs mer om [direktregistrering med Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-intune"></a>Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS) kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller i molnet.

Mer information finns i [Hantering av mobila enheter med Exchange ActiveSync och Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).


## <a name="windows-pc-management-with-intune"></a>Hantera Windows-datorer med Intune  
Du kan också använda Microsoft Intune för att hantera Windows-datorer med klientprogramvaran för Intune för Windows. Datorer som hanteras med Intune-klienten kan:

 - Rapportera program- och maskinvaruinventering
 - Installera skrivbordsprogram (till exempel .exe och .msi-filer)
 - Hantera Brandväggsinställningar

Datorer som hanteras med Intune-klientprogrammet kan inte rensas helt, men selektiv rensning är tillgängligt. Datorer som hanteras med Intune-klientprogrammet kan inte dra nytta av många av Intunes hanteringsfunktioner, t.ex. villkorlig åtkomst, VPN- och Wi-Fi-inställningar eller distribution av certifikat och e-postkonfigurationer.

Mer information finns i [Hantera Windows-datorer med Intune](manage-windows-pcs-with-microsoft-intune.md).

## <a name="supported-device-platforms"></a>Enhetsplattformar som stöds

Intune kan hantera följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## <a name="next-steps"></a>Nästa steg
- [Krav för enhetsregistrering](prerequisites-for-enrollment.md)
- [Hantera företagsägda enheter](manage-corporate-owned-devices.md)
- [Mobila enheter och datorer som stöds](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Dec16_HO2-->


