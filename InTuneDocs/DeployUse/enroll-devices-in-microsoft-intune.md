---
title: Registrera enheter | Microsoft Intune
description: "Hantering av mobila enheter (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser."
keywords: 
author: NathBarn
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
ms.sourcegitcommit: e6b182ebab1691c62e69cabaf4689ac7395ab31a
ms.openlocfilehash: 0995d3ced978f5213fdb0e9905f508b64a1e5c09


---

# Registrera enheter för hantering i Intune
Du kan registrera enheter, inklusive Windows-datorer, för att aktivera hantering av mobila enheter (MDM) med Microsoft Intune. Det här avsnittet beskriver olika sätt att registrera mobila enheter i Intune-hanteringen. Hur enheter registrerar enheter beror på enhetstyp, ägande och den hanteringsnivå som krävs. BYOD (Bring Your Own Device)-registrering låter användare att registrera sina personliga telefoner, surfplattor eller datorer. Registrering av företagsägda enheter (COD) gör hanteringsscenarier som fjärrensning, delade enheter och användartillhörighet för en enhet möjliga.

Om du använder [Exchange ActiveSync](#mobile-device-management-with-exchange-activesync-and-intune), antingen lokalt eller med värd i molnet, kan du aktivera enkel Intune-hantering utan registrering. Windows-datorer kan också hanteras med [Intune-klientprogrammet](#manage-windows-pcs-with-intune).

## Översikt över registreringsmetoder för enheter

I följande tabell visas Intunes registreringsmetoder med de funktioner som de stöder. Dessa funktioner är:
- **Rensa** – Fabriksåterställer enheten och ta bort alla data. [Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md)
- **Tillhörighet** – Kopplar enheter till användare. Krävs för hantering av mobila program (MAM) och villkorlig åtkomst till företagsdata. [Användartillhörighet](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices)
- **Lås** – Förhindrar att användare tar bort enheten från hanteringen. iOS-enheter kräver Övervakat läge för Lås. [Fjärrlåsning](retire-devices-from-microsoft-intune-management.md#block-access-a-device)

**Metoder för iOS-registrering**

| **Metod** |  **Rensning** |  **Tillhörighet**    |   **Lås** | **Information** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [mer](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   Nej |Nej |Nej  | [mer](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|
|**[DEP](#dep)**|   Ja |   Valfri |  Valfri|[mer](ios-device-enrollment-program-in-microsoft-intune.md)|
|**[USB-SA](#usb-sa)**| Ja |   Valfri |  Nej| [mer](ios-setup-assistant-enrollment-in-microsoft-intune.md)|
|**[USB-Direct](#usb-direct)**| Nej |    Nej  | Nej|[mer](ios-direct-enrollment-in-microsoft-intune.md)|

**Windows- och Android-registreringsmetoder**

| **Metod** |  **Rensning** |  **Tillhörighet**    |   **Lås** | **Information**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | Nej|    Ja |   Nej | [mer](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management)|
|**[DEM](#dem)**|   Nej |Nej |Nej  |[mer](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)|

För en serie frågor som hjälper dig att hitta rätt metod, se [Choose how to enroll devices](/intune/get-started/choose-how-to-enroll-devices1) (Välj hur du registrerar enheter).

## BYOD
"Bring your own device"-användare installerar företagsportalsappen och registrerar sina enheter. Detta låter användarna att ansluta till företagets nätverk och ansluta till domänen eller Azure Active Directory. Du måste aktivera BYOD-registrering för många COD-scenarier för de flesta plattformarna. Se [Prerequisites for device enrollment](prerequisites-for-enrollment.md) (Krav för enhetsregistrering). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

## Företagsägda enheter
Företagsägda enheter (COD) kan hanteras med Intune-konsolen. iOS-enheter kan registreras direkt via verktyg från Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

[Registrera enheter som ägs av företaget](manage-corporate-owned-devices.md)

### DEM
Enhetsregistreringshanteraren är ett särskilt Intune-konto som används för att registrera och hantera ett flertal företagsägda enheter. Cheferna kan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### DEP
Apples program för enhetsregistrering låter dig skapa och distribuera principen “via luften” till iOS-enheter som har köpts och hanteras med DEP. Enheten registreras när användaren aktiverar enheten för första gången och kör iOS-installationsassistenten. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Låst registrering
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### USB-SA
Installationsassistent för USB-ansluten registrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna företagsägda enheter förbereds med Intune-principen. Administratören måste registrera varje enhet manuellt. Användarna får sina enheter och kör Installationsassistenten, där de registrerar sina enheter. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [Registrering av installationsassistenten med Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### USB-Direct
Direktregistrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna företagsägda enheter registreras direkt utan att fabriksåterställning krävs. Administratören måste registrera varje enhet manuellt. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program. Läs mer om [direktregistrering med Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

## Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS) kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller med värd i molnet .

[Hantering av mobila enheter med Exchange ActiveSync och Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Hantera Windows-datorer med Intune  
Du kan också använda Microsoft Intune för att hantera Windows-datorer med klientprogramvaran för Intune för Windows. Datorer som hanteras med Intune-klienten kan:

 - Rapportera program- och maskinvaruinventering
 - Installera skrivbordsprogram (till exempel .exe och .msi-filer)
 - Brandväggsinställningar

Datorer som hanteras med Intune-klientprogrammet kan inte rensas eller dra nytta av många av Intune-hanteringsfunktionerna, t.ex. villkorlig åtkomst, VPN- och Wi-Fi-inställningar eller distribution av certifikat och e-postkonfigurationer.

[Hantera Windows-datorer med Intune](manage-windows-pcs-with-microsoft-intune.md)

##  Enhetsplattformar som stöds

Intune kan hantera följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Nästa steg
- [Krav för enhetsregistrering](prerequisites-for-enrollment.md)
- [Hantera företagsägda enheter](manage-corporate-owned-devices.md)
- [Mobila enheter och datorer som stöds](../get-started/supported-mobile-devices-and-computers.md)



<!--HONumber=Sep16_HO3-->


