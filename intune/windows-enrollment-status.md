---
title: Konfigurera en sida för registreringsstatus
titleSuffix: Microsoft Intune
description: Visa en hälsning för användare som registrerar Windows 10-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/17/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c6604c35cebdad4341f27a51db1a4c735f9a9818
ms.sourcegitcommit: 6bd5867c41fb5288fde114dbfcc127dd206f7148
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="set-up-an-enrollment-status-page"></a>Konfigurera en sida för registreringsstatus
 
[!INCLUDE [azure_portal](./includes/azure_portal.md)]
 
Under enhetskonfigurationen visar sidan med registreringsstatus information om installationsstatusen på slutanvändarens enhet. Vissa program, profiler och certifikat kanske inte är helt installerade när en användare registreras. På statussidan kan användaren se statusen för sina enheter under och efter registreringen. Du kan aktivera statussidan för alla användare, samt hindra användare från att använda enheten innan alla tilldelade program och profiler har installerats.
 
Följ stegen nedan om du vill aktivera statussidan för registrering för alla slutanvändare.
 
1.  I [Intune](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **Statussidan för registrering (förhandsversion)**.
2.  På bladet **Statussidan för registrering**  väljer du **Standard** > **Inställningar**.
3.  Välj **Ja** för **Show app and profile installation progress** (Visa installationsförlopp för appar och profiler).
4.  Välj övriga inställningar som du vill aktivera och välj sedan **Spara**.
 
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
- Anslutningsprofiler (VPN och Wi-Fi) spåras inte än, och visas därför alltid som ”0 av 0”.
- Certifikat spåras inte än, och visas därför alltid som ”0 av 0”.

### <a name="account-setup"></a>Kontokonfiguration
För kontokonfiguration spårar statussidan för registrering följande objekt:
- Säkerhetsprinciper
    - En konfigurationstjänstprovider (CSP) för alla registreringar.
    - De faktiska konfigurationstjänstprovidrar som har konfigurerats av Intune spåras inte här.
- Program
    - Verksamhetsspecifika MSI-appar per användare som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
    - Verksamhetsspecifika MSI-appar per dator som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
    - LoB-lagringsappar som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i med installationskontexten = Användare.
    - Onlinelagringsappar som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i med installationskontexten = Användare.
    - Offlinelagringsappar som har tilldelats till alla enheter, till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i med installationskontexten = Användare.
- Anslutningsprofiler
    - VPN- eller Wi-Fi-profiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.
- Certifikat
    - Certifikatprofiler som har tilldelats till alla användare eller till en användargrupp som användaren som registrerar enheten är medlem i.

## <a name="next-steps"></a>Nästa steg
När du har konfigurerat Windows-registreringssidor kan du gå vidare och lära dig hur du hanterar Windows-enheter. Mer information finns i [Vad är Microsoft Intune-enhetshantering?](https://docs.microsoft.com/intune/device-management)