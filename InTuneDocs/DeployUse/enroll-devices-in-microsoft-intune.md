---
title: Registrera enheter | Microsoft Intune
description: "Hantering av mobila enheter (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c329bd08aaf72ae2acaa03dcb12c911d84b46b4e
ms.openlocfilehash: 9d624da7931c56476b476b7a9fd5711f398052c4


---

# Registrera enheter för hantering i Intune
Hantering av mobila enheter i Microsoft Intune (MDM) använder registrering för att skapa hantering för enheterna och tillåta åtkomst till resurser. Metoden för att registrera enheter beror på enhetstyp, ägande och den hanteringsnivå som krävs. Scenarier med "bring your own device" (BYOD) och företagsägda enheter (COD) kräver en registreringsprocess. Organisationer som använder ActiveSync, antingen lokalt eller med värd i molnet, kan aktivera lättare hantering utan registreringskrav. Windows-datorer kan också hanteras med Intune-klientprogrammet.

Se [Välj hur du vill registrera enheter](/intune/get-started/choose-how-to-enroll-devices1) om du behöver hjälp.

###  Enhetsplattformar som stöds

Intune kan hantera följande enhetsplattformar:

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

## Ange auktoritet för hantering av mobila enheter
Utfärdaren för hantering av mobila enheter definierar den hanteringstjänst som har behörighet att hantera en uppsättning enheter. Alternativen för MDM-utfärdare innefattar själva Intune och Configuration Manager med Intune. Om Configuration Manager anges som utfärdare för hanteringen kan inga andra tjänster användas för hantering av mobila enheter.

>[!IMPORTANT]
> Överväg noggrant om du vill hantera mobila enheter endast med hjälp av Intune (onlinetjänst) eller System Center Configuration Manager med Intune (lokal programvarulösning i samband med onlinetjänsten). När du har angett utfärdare för hantering av mobila enheter går det inte att ändra detta.

1.  Gå till [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) och välj **Admin** &gt; **Hantering av mobila enheter**.

2.  Klicka på **Ange auktoritet för hantering av mobila enheter** i **Uppgiftslistan**. Dialogrutan **Ange MDM-auktoritet** öppnas.

    ![Dialogrutan Ange MDM-auktoritet](../media/intune-mdm-authority.png)

3.  Intune begär bekräftelse på att du vill ha Intune som MDM-utfärdare. Markera kryssrutan och välj sedan **Ja** om du vill hantera mobila enheter med Microsoft Intune.

## Konfigurera Intune-företagsportalen

Intune-företagsportalen är den plats där användare kan komma åt företagets data och utföra vanliga aktiviteter som att registrera enheter, installera appar och hitta information för att få hjälp från IT-avdelningen.

> [!TIP]
> När du anpassar företagsportalen gäller konfigurationerna både företagsportalens webbplats och företagsportalens appar.

Genom att anpassa företagsportalen kan du skapa en välbekant miljö för dina slutanvändare. Om du vill göra det loggar du bara in på [Microsoft Intune-administratörskonsolen](https://manage.microsoft.com) som klient eller tjänstadministratör, väljer **Admin** &gt; **Företagsportal** och konfigurerar inställningarna för företagsportalen.

![admin-console-admin-workspace-comp-portal-settings](../media/cp_sa_cpsetup.PNG)

## Översikt över registreringsmetoder för enheter

I följande tabell visas registreringsmetoder för företagsägda enheter, och vilka fördelar de innebär.

**Metoder för iOS-registrering**

| **Metod** |  **[Rensning](#Wipe)** | **[Tillhörighet](#Affinity)**   |   **[Låst](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |
|**[DEP](#DEP)**|   Ja |   Välj |   Välj|
|**[USB-SA](#USB-SA)**| Ja |   Välj |   Nej|
|**[USB-Direct](#USB-Direct)**| Nej |    Nej  | Nej|

**Windows- och Android-registreringsmetoder**

| **Metod** |  **[Rensning](#Wipe)** | **[Tillhörighet](#Affinity)**   |   **[Låst](#Lock)** |
|:---:|:---:|:---:|:---:|
|**[BYOD](#BYOD)** | Nej|    Ja |   Nej |
|**[DEM](#DEM)**|   Nej |Nej |Nej  |

**Registreringsmetoder för företagsägda enheter**

### BYOD
”Bring Your Own Device”. Användarna installerar företagsportalsappen och registrerar sina enheter. Om en enhet registreras på företagsportalen kommer arbetsplatsen att koppla enheten. Registrering av iOS-enheter i företagsportalen kräver ett Apple-ID. BYOD kräver inte ytterligare konfiguration för företagsägda enheter. Se stegen för att [konfigurera enhetshantering](get-ready-to-enroll-devices-in-microsoft-intune.md#set-up-device-management). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### DEM
Enhetsregistreringshanterare (Device Enrollment Manager). Administratören skapar DEM-konton för hantering av företagsägda enheter. Cheferna kan sedan installera företagsportalen och registrera flera användarlösa enheter. Läs mer om [DEM](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md). ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### DEP
Apples program för enhetsregistrering (Device Enrollment Program). Administratören skapar och distribuerar principen ”via luften” till företagsägda iOS-enheter som har köpts och hanteras med DEP. Enheten registreras när användaren kör iOS-installationsassistenten. Den här metoden har stöd för **iOS Övervakad**-läget vilket i sin tur aktiverar:
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

**Beteende för företagsägda mobila enheter**

### Rensning
Anger om en registrering av enheten kräver att alla data tas bort från enheten och att den återställs till fabriksinställningarna och det ursprungliga tillståndet.
[Dra tillbaka enheter](retire-devices-from-microsoft-intune-management.md) ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### Tillhörighet
Anger om en registreringsmetod har stöd för funktionen ”Användartillhörighet” som används för att koppla en enhet till en viss användare. Deltagande enheter kan registreras med eller utan användartillhörighet. Användartillhörighet krävs för att ge stöd åt följande:
  - Hantering av mobilprogramsappar (MAM, Mobile Application Management)
  - Villkorlig åtkomst till e-post och företagsdata
  - Företagsportalappen

[Användartillhörighet](enroll-corporate-owned-ios-devices-in-microsoft-intune.md#using-company-portal-on-dep-or-apple-configurator-enrolled-devices) ([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

### Lås
Anger om enheten kan låsas för att förhindra att användaren tar bort Intune-principen, vilket tar bort enheten från hanteringen. För iOS-enheter måste enheten vara i övervakat läge för att den ska gå att låsa.
([Tillbaka till tabellen](#overview-of-device-enrollment-methods))

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



<!--HONumber=Aug16_HO3-->


