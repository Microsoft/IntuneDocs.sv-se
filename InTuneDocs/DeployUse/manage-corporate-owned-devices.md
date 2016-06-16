---
# required metadata

title: Registrera företagsägda enheter | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b60bbff-25e6-489b-9621-c71b4275fa06

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Registrera företagsägda enheter med Microsoft Intune
Organisations- eller företagsägda enheter kan anslutas till hantering av Intune på en mängd olika sätt beroende på enheten, hur den har köpts och organisationens behov.

## Företagsägda iOS-enheter
Dessa registreringsmetoder är bra för "Välj din egna enhet"(CYOD)-scenarier där organisationen köper in enheter för användare, men behåller hanteringsbefogenheter av enheten. Om din organisation har köpt iOS-enheter kan du konfigurera registreringen så att enheten är hanterad redan första gången dess användare aktiverar den. Intune stöder registrering via [Apples Enhetsregistreringsprogram (DEP)](ios-device-enrollment-program-in-microsoft-intune.md) eller verktyget Apple Configurator på en Mac-dator för registrering [direkt](ios-direct-enrollment-in-microsoft-intune.md) eller med [installationsassistenten](ios-setup-assistant-enrollment-in-microsoft-intune.md).

[Registrera företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)

## Hanterare av enhetsregistrering
Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto som kallas konto för enhetsregistreringshantering. När du har skapat ett konto för enhetsregistreringshantering kan kontot användas av en chef för att registrera mer än de fem enheter som tillåts som standard för normal användare. Att registrera enheter med en enhetsregistreringshanterare fungerar endast för enheter som inte används av en viss användare. Dessa enheter är bra för till exempel återförsäljning- eller verktygsappar men inte bra för användare som behöver åtkomst till e-post eller företagsresurser.

[Registrera företagsägda enheter med enhetsregistreringshanteraren](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)

## IMEI (International Mobile Equipment Identity)
Unika IMEI-siffror är enhetsegenskap som är gemensam för många tillverkare av mobila enheter. Intune-administratörer kan importera IMEI-nummer för enheter som företaget äger. När enheten hanteras av Intune kan den markeras som en företagsägd enhet och lämpliga principer kan appliceras på den.

[Ange enheter som ägs av företaget med IMEI-nummer (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

## Översikt över registreringsmetoder för företagsägda enheter

I följande tabell visas registreringsmetoder för företagsägda enheter, och vilka fördelar de innebär.

**Metoder för iOS-registrering**

| **Metod** |  **[Återställ](#Reset)** |   **[Tillhörighet](#Affinity)**   |   **[Låst](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |
|**[DEP](#DEP)**|   Ja |   Välj |   Välj|
|**[USB-SA](#USB-SA)**| Ja |   Välj |   Nej|
|**[USB-Direct](#USB-Direct)**| Nej |    Nej  | Nej|

**Windows- och Android-registreringsmetoder**

| **Metod** |  **[Rensning](#Wipe)** | **[Användare](#User)**   |   **[Låst](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |

**Registreringsmetoder för företagsägda enheter**

### BYOD
”Bring Your Own Device”. Användarna installerar företagsportalsappen och registrerar sina enheter. Om en enhet registreras på företagsportalen kommer arbetsplatsen att koppla enheten. Registrering av iOS-enheter i företagsportalen kräver ett Apple-ID. BYOD kräver inte ytterligare konfiguration för företagsägda enheter. Se stegen för att [konfigurera enhetshantering](get-ready-to-enroll-devices-in-microsoft-intune#set-up-device-management.md). ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### DEM
Enhetsregistreringshanterare (Device Enrollment Manager). Administratören skapar DEM-konton. Cheferna kan sedan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### DEP
Apples program för enhetsregistrering (Device Enrollment Program). Administratören skapar och distribuerar principen ”via luften” till iOS-enheter som har köpts och hanteras med DEP. Enheten registreras när användaren kör iOS-installationsassistenten. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Låst registrering
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### USB-SA
Installationsassistent för USB-ansluten registrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna enheter förbereds med Intune-principen. Administratören måste registrera varje enhet manuellt. Användarna får sina enheter och kör Installationsassistenten, där de registrerar sina enheter. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Låst registrering
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [Registrering av installationsassistenten med Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### USB-Direct
Direktregistrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna enheter registreras direkt utan att fabriksåterställning krävs. Administratören måste registrera varje enhet manuellt. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program. Läs mer om [direktregistrering med Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

**Beteende för företagsägda mobila enheter**

### Återställ
Anger om en registrering av enheten kräver att alla data tas bort från enheten och att den återställs till fabriksinställningarna och det ursprungliga tillståndet.
([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### Tillhörighet
Anger om en registreringsmetod har stöd för funktionen ”Användartillhörighet” som används för att koppla en enhet till en viss användare. Deltagande enheter kan registreras med eller utan användartillhörighet. Användartillhörighet krävs för att ge stöd åt följande:
  - Hantering av mobilprogramsappar (MAM, Mobile Application Management)
  - Villkorlig åtkomst till e-post och företagsdata
  - Företagsportalappen

([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))

### Lås
Anger om enheten kan låsas för att förhindra att användaren tar bort Intune-principen, vilket tar bort enheten från hanteringen. För iOS-enheter måste enheten vara i övervakat läge för att den ska gå att låsa.
([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods)) ([Tillbaka till tabellen](#overview-of corporate-owned-device-enrollment-methods))


<!--HONumber=Jun16_HO1-->


