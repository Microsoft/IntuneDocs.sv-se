---
title: Konfigurera en sida för registreringsstatus
titleSuffix: Microsoft Intune
description: Konfigurera en hälsningssida för användare som registrerar Windows 10-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b87e0d24c000e3083eaebeac1a4cf6026d495ccf
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032103"
---
# <a name="set-up-an-enrollment-status-page"></a>Konfigurera en sida för registreringsstatus
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Under enhetskonfigurationen med Intune visas installationsinformation om enheten på sidan för registreringsstatus. Vissa program, profiler och certifikat kanske inte har installerats när en användare som slutför den fördefinierade registreringen loggar in på enheten. En statussida för registreringen kan hjälpa användaren att förstå statusen för sina enheter under enhetskonfigurationen. Du kan skapa flera profiler för sidan för registreringsstatus och tillämpa dem på olika grupper. Profiler kan ställas in att:
- Visa installationsförloppet.
- Blockera användningen tills installationen är klar.
- Ange vad en användare kan göra om enhetskonfigurationen misslyckas.

Du kan också ange prioritetsordningen för varje profil om det skulle uppstå konflikter mellan profiltilldelningar för samma användare eller enhet.

 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivera standardsidan för registreringsstatus för alla användare

Följ stegen nedan om du vill aktivera sidan för registreringsstatus.
 
1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2. På bladet **Statussidan för registrering**  väljer du **Standard** > **Inställningar**.
3. Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4. Välj övriga inställningar som du vill aktivera och välj sedan **Spara**.

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>Skapa en profil för registreringsstatussidan och tilldela den till en grupp

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)** > **Skapa profil**.
2. Ange ett **namn** och en **beskrivning**.
3. Välj **Skapa**.
4. Välj den nya profilen i listan **Statussidan för registrering**.
5. Välj **Tilldelningar** > **Välj grupper** > välj de grupper som ska använda den här profilen > **Välj** > **Spara**.
6. Välj **Inställningar** > välj de inställningar som du vill använda för den här profilen > **Spara**.

## <a name="set-the-enrollment-status-page-priority"></a>Ange prioritet för registreringsstatussidan

En enhet eller användare kan tillhöra flera grupper och ha flera profiler för registreringsstatussidan. För att lösa dessa konflikter kan du ange prioriteten för varje profil. Om någon har mer än en profil för registreringsstatussidan, tillämpas endast profilen med högst prioritet.

1. I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2. Hovra över profilen i listan.
3. Använd de tre lodräta punkterna och dra profilen till önskad plats i listan.

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>Blockera åtkomst till en enhet tills ett visst program har installerats

Du kan ange vilka appar som måste installeras innan användaren kan komma åt skrivbordet.

1. I Intune väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2. Välj en profil > **Inställningar**.
3. Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4. Välj **Ja** för **Block device use until all apps and profiles are installed** (Blockera enhetsanvändning tills alla appar och profiler är installerade).
5. Välj **Valda** för **Block device use until these required apps are installed if they are assigned to the user/device** (Blockera enhetsanvändning tills följande obligatoriska appar har installerats, om de är tilldelade till användaren/enheten).
 6. Välj **Välj appar** > välj apparna > **Välj** > **Spara**.

## <a name="enrollment-status-page-tracking-information"></a>Spårningsinformation på statussidan för registrering

Statussidan spårar information för enhetsförberedelse, enhetskonfiguration och kontokonfiguration.

### <a name="device-preparation"></a>Förberedelse av enheten

För enhetsförberedelser spårar statussidan för registrering TPM-nyckelattestering (Trusted Platform Module) (i förekommande fall), Azure Active Directory-anslutningsförloppet och registreringen i Intune.

### <a name="device-setup"></a>Enhetskonfiguration

För enhetskonfiguration spårar statussidan för registrering följande objekt om de har tilldelats till alla enheter:
- Säkerhetsprinciper
    - En konfigurationstjänstprovider (CSP) för alla registreringar.
    - De faktiska konfigurationstjänstprovidrar som har konfigurerats av Intune spåras inte här.
- Program
    - Verksamhetskritiska (LoB) MSI-appar per dator.
    - LoB-lagringsappar med installationskontext = Enhet.
    - Offlinelagrings- och LoB-lagringsappar med installationskontext = Enhet.
- Anslutningsprofiler
    - VPN- eller Wi-Fi-profiler som har tilldelats **Alla enheter** eller en enhetsgrupp som enheten som registreras är medlem i, men endast för Autopilot-enheter
- Certifikatprofiler som har tilldelats **Alla enheter** eller en enhetsgrupp som enheten som registreras är medlem i, men endast för Autopilot-enheter

### <a name="account-setup"></a>Kontokonfiguration
För kontokonfiguration spårar statussidan för registrering följande objekt:
- Säkerhetsprinciper
    - En konfigurationstjänstprovider (CSP) för alla registreringar.
    - De faktiska konfigurationstjänstprovidrar som har konfigurerats av Intune spåras inte här.
- Program
    - Verksamhetsspecifika MSI-appar per användare som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
    - Verksamhetsspecifika MSI-appar per dator som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
    - Verksamhetsspecifika butiksappar, appar i onlinebutiken och appar i offlinebutiken som tilldelas något av följande:
        - Alla enheter
        - Alla användare
        - en användargrupp där användaren som registrerar enheten är en medlem med installationskontexten Användare.
- Anslutningsprofiler
    - VPN- eller Wi-Fi-profiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
- Certifikat
    - Certifikatprofiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.

## <a name="next-steps"></a>Nästa steg
När du har konfigurerat Windows-registreringssidor kan du gå vidare och lära dig hur du hanterar Windows-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](https://docs.microsoft.com/intune/device-management)
