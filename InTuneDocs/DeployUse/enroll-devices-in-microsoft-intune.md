---
title: Registrera enheter | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 69cf07aa0747448e0ef3384b5b5132e0e76aed45
ms.openlocfilehash: 930cbc806d8fd1185cf33fd64d866b88ec9a6a04


---

# Registrera enheter för hantering i Intune
Hantering av mobila enheter i Microsoft Intune (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser. Metoden för att registrera enheter beror på enhetstyp, ägande och den hanteringsnivå som krävs. Scenarier med "bring your own device" (BYOD) och företagsägda enheter (COD) kräver en registreringsprocess. Organisationer som använder ActiveSync, antingen lokalt eller med värd i molnet, kan aktivera lättare hantering utan registreringskrav. Windows-datorer kan också hanteras med Intune-klientprogrammet.

###  Enhetsplattformar som stöds

Intune kan hantera följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Översikt över registreringsmetoder för enheter

I följande tabell visas registreringsmetoder för företagsägda enheter, och vilka fördelar de innebär.

**Metoder för iOS-registrering**

| **Metod** |  **[Rensning](#Wipe)** | **[Tillhörighet](#Affinity)**   |   **[Låst](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |
|**[DEP](#DEP)**|   Ja |   Välj |   Välj|
|**[USB-SA](#USB-SA)**| Ja |   Välj |   Nej|
|**[USB-Direct](#USB-Direct)**| Nej |    Nej  | Nej|

**Windows- och Android-registreringsmetoder**

| **Metod** |  **[Rensning](#Wipe)** | **[Tillhörighet](#Affinity)**   |   **[Låst](#Locked)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |

**Registreringsmetoder för företagsägda enheter**

### BYOD
”Bring Your Own Device”. Användarna installerar företagsportalsappen och registrerar sina enheter. Om en enhet registreras på företagsportalen kommer arbetsplatsen att koppla enheten. Registrering av iOS-enheter i företagsportalen kräver ett Apple-ID. BYOD kräver inte ytterligare konfiguration för företagsägda enheter. Se stegen för att [konfigurera enhetshantering](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management). ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### DEM
Enhetsregistreringshanterare (Device Enrollment Manager). Administratören skapar DEM-konton för hantering av företagsägda enheter. Cheferna kan sedan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### DEP
Apples program för enhetsregistrering (Device Enrollment Program). Administratören skapar och distribuerar principen ”via luften” till företagsägda iOS-enheter som har köpts och hanteras med DEP. Enheten registreras när användaren kör iOS-installationsassistenten. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Låst registrering
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [DEP](ios-device-enrollment-program-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### USB-SA
Installationsassistent för USB-ansluten registrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna företagsägda enheter förbereds med Intune-principen. Administratören måste registrera varje enhet manuellt. Användarna får sina enheter och kör Installationsassistenten, där de registrerar sina enheter. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
  - Villkorlig åtkomst
  - Upplåsningsidentifiering
  - Hantering av mobila program

Läs mer om [Registrering av installationsassistenten med Apple Configurator](ios-setup-assistant-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### USB-Direct
Direktregistrering. Administratören skapar en Intune-princip och exporterar den till Apple Configurator. USB-anslutna företagsägda enheter registreras direkt utan att fabriksåterställning krävs. Administratören måste registrera varje enhet manuellt. Enheter hanteras som användarlösa enheter. De är inte låsta eller övervakade och har inte stöd för villkorlig åtkomst, upplåsningsidentifiering eller hantering av mobila program. Läs mer om [direktregistrering med Apple Configurator](ios-direct-enrollment-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

**Beteende för företagsägda mobila enheter**

### Rensning
Anger om en registrering av enheten kräver att alla data tas bort från enheten och att den återställs till fabriksinställningarna och det ursprungliga tillståndet.
([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### Tillhörighet
Anger om en registreringsmetod har stöd för funktionen ”Användartillhörighet” som används för att koppla en enhet till en viss användare. Deltagande enheter kan registreras med eller utan användartillhörighet. Användartillhörighet krävs för att ge stöd åt följande:
  - Hantering av mobilprogramsappar (MAM, Mobile Application Management)
  - Villkorlig åtkomst till e-post och företagsdata
  - Företagsportalappen

([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

### Lås
Anger om enheten kan låsas för att förhindra att användaren tar bort Intune-principen, vilket tar bort enheten från hanteringen. För iOS-enheter måste enheten vara i övervakat läge för att den ska gå att låsa.
([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods)) ([Tillbaka till tabellen](#overview-of-corporate-owned-device-enrollment-methods))

## Aktivera registrering av enheter  
 Med registrering kan användarna få åtkomst till företagsresurser på sina personliga enheter och det gör det möjligt för administratören att se till att dessa enheter följer principer som skyddar företagets resurser. Det här är det bästa sättet att möjliggöra scenarier med "bring your own device" med Intune. Administratören måste aktivera registrering i Intune-konsolen, vilket kan kräva att man skapar en förtroenderelation med enheten och tilldelar licenser till användare. Enheten registreras sedan, normalt av användare som anger sina arbets- eller skolautentiseringsuppgifter. Enheten tar sedan emot principer från Intune och får åtkomst till resurser.

[Dags att registrera enheter i Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)

## Registrera enheter som ägs av företaget
Företagsägda enheter (COD) kan hanteras med Intune-konsolen. iOS-enheter kan registreras direkt via verktyg från Apple. Alla enhetstyper kan registreras av en administratör eller chef med hjälp av hanteraren för enhetsregistrering. Enheter med ett IMEI kan också identifieras och taggas som företagsägda för att möjliggöra COD-scenarier.

[Registrera enheter som ägs av företaget](manage-corporate-owned-devices.md)

## Hantering av mobila enheter med Exchange ActiveSync och Intune
Mobila enheter som inte är registrerade men som ansluter till Exchange ActiveSync (EAS) kan hanteras av Intune med EAS MDM-principen. Intune använder en Exchange-anslutning för att kommunicera med EAS, antingen lokalt eller med värd i molnet .



[Hantering av mobila enheter med Exchange ActiveSync och Intune](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## Hantera Windows-datorer med Intune  
Du kan också använda Microsoft Intune för att hantera Windows-datorer med datorklientprogramvaran Intune för Windows. Datorer som hanteras med Intune-klienten kan:

 - Rapportera program- och maskinvaruinventering
 - Installera skrivbordsprogram (till exempel .exe och .msi-filer)
 - Brandväggsinställningar

Datorer som hanteras med Intune-klientprogrammet kan inte rensas selektivt eller dras tillbaka, och de kan inte dra nytta av många av Intune-hanteringsfunktionerna, t.ex. villkorlig åtkomst, VPN- och Wi-Fi-inställningar eller distribution av certifikat och e-postkonfigurationer.

[Hantera Windows-datorer med Intune](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jun16_HO5-->


