---
title: Konfigurera en sida för registreringsstatus
titleSuffix: Microsoft Intune
description: Visa en hälsning för användare som registrerar Windows 10-enheter.
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
ms.custom: intune-azure
ms.openlocfilehash: f5460db2d646d8bd417baa50d8188acbf69a251d
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48827997"
---
# <a name="set-up-an-enrollment-status-page"></a>Konfigurera en sida för registreringsstatus
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Under enhetskonfigurationen visas installationsinformation om enheten på sidan för registreringsstatus. Vissa program, profiler och certifikat kanske inte är helt installerade när en användare registreras. På statussidan kan användaren se statusen för sina enheter under och efter registreringen. Du kan aktivera statussidan för alla användare eller skapa profiler riktade till specifika användargrupper.  Du kan ange profiler för att visa installationsförloppet, blockera användningen tills installationen är klar, tillåta återställning och så vidare.
 
## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>Aktivera standardsidan för registreringsstatus för alla användare

Följ stegen nedan om du vill aktivera statussidan för registrering för alla slutanvändare.
 
1.  I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2.  På bladet **Statussidan för registrering**  väljer du **Standard** > **Inställningar**.
3.  Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4.  Välj övriga inställningar som du vill aktivera och välj sedan **Spara**.

## <a name="create-enrollment-status-page-profile-to-target-specific-users"></a>Skapa en profil för registreringsstatussidan för specifika användare

1.  I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)** > **Skapa profil**.
2. Ange ett **namn** och en **beskrivning**.
3. Välj **Skapa**.
4. Välj den nya profilen i listan **Statussidan för registrering**.
5. Välj **Tilldelningar** > **Välj grupper** > välj de grupper som ska använda den här profilen > **Välj** > **Spara**.
6. Välj **Inställningar** > välj de inställningar som du vill använda för den här profilen > **Spara**.


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
- Anslutningsprofiler (VPN och Wi-Fi) spåras inte än, och visar därför alltid ”0 av 0”.
- Certifikat spåras inte än, och visar därför alltid ”0 av 0”.

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