---
title: Skapa VPN-enhetsprofiler i Microsoft Intune – Azure | Microsoft Docs
description: För iOS-enheter kan du se anslutningstyper för det virtuella privata nätverket, skapa en VPN-profil för enheter i Azure Portal och se dina alternativ för att skydda VPN-profilen med certifikat eller användarnamn och lösenord i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97bddc1a183e3a546e76b346f53f80aba6a81c50
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312881"
---
# <a name="create-vpn-profiles-in-intune"></a>Skapa VPN-profiler i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheterna använder en profil för VPN-anslutning för att initiera en anslutning till VPN-servern. Använd **VPN-profiler** i Microsoft Intune för att tilldela VPN-inställningar till användare och enheter i din organisation så att de enkelt och säkert kan ansluta till nätverket.

Exempel: Anta att du vill förse alla enheter som kör iOS med de inställningar som krävs för att ansluta till en filresurs i företagsnätverket. Du kan skapa en VPN-profil som innehåller inställningar för att ansluta till företagets nätverk. Sedan tilldelar du den här profilen till alla användare som har iOS-enheter. Användarna ser VPN-anslutningen i listan med tillgängliga nätverk och kan enkelt ansluta.

Du kan använda anpassade konfigurationsprinciper i Intune för att skapa VPN-profiler för följande plattformar:

* Android 4 och senare
* Registrerade enheter som kör Windows 8.1 och senare
* Windows Phone 8.1 och senare
* Registrerade enheter som kör Windows 10 desktop och senare
* Windows 10 Mobil
* Windows 10 Holographic for Business

## <a name="vpn-connection-types"></a>VPN-anslutningstyper

Du kan skapa VPN-profiler med följande anslutningstyper:

|Anslutningstyp|Android<br>Android-arbetsprofiler|iOS|macOS|Windows Phone 8.1|Windows 8,1|Windows 10|
|-|-|-|-|-|-|-|
|Automatiskt|Nej|Nej|Nej|Nej|Nej|Ja|
|Check Point Capsule VPN|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco AnyConnect|Ja|Ja|Ja|Nej|Nej|Nej|
|SonicWall Mobile Connect|Ja|Ja|Ja|Ja|Ja|Ja|
|F5 Edge Client|Ja|Ja|Ja|Ja|Ja|Ja|
|Palo Alto Networks GlobalProtect|Nej|Ja|Nej|Nej|Nej|Ja|
|Pulse Secure|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco (IPSec)|Nej|Ja|Nej|Nej|Nej|Nej|
|Citrix|Ja (endast Android)|Ja|Nej|Nej|Nej|Ja|
|IKEv2|Nej|Nej|Nej|Nej|Nej|Ja|
|L2TP|Nej|Nej|Nej|Nej|Nej|Ja|
|PPTP|Nej|Nej|Nej|Nej|Nej|Ja|
|Zscaler|Nej|Ja|Nej|Nej|Nej|Nej|
|Anpassat VPN|Nej|Ja|Ja|Nej|Nej|Nej|

> [!IMPORTANT]
> Innan du kan använda de VPN-profiler som har tilldelats till en enhet måste du installera lämplig VPN-app för profilen. Använd informationen i artikeln [Vad är apphantering i Microsoft Intune?](app-management.md) när du ska tilldela appar med hjälp av Intune.  

Läs om hur du skapar anpassade VPN-profiler med hjälp av URI-inställningarna i [Skapa en profil med anpassade inställningar](custom-settings-configure.md).

## <a name="create-a-device-profile-containing-vpn-settings"></a>Skapa en enhetsprofil som innehåller VPN-inställningar

1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
4. Ange ett **Namn** och en **Beskrivning** för VPN-profilen.
5. Välj den enhetsplattform på vilken du vill tillämpa VPN-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för VPN-enhetsinställningar:
   - **Android**
   - **Android enterprise**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 och senare**
   - **Windows 10 och senare**
6. Välj **VPN** i listrutan **Profiltyp**.
7. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
   - [Inställningar för Android och Android-arbetsprofiler](vpn-settings-android.md)
   - [Inställningar för iOS](vpn-settings-ios.md)
   - [Inställningar för macOS](vpn-settings-macos.md)
   - [Inställningar för Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
   - [Inställningar för Windows 8.1](vpn-settings-windows-8-1.md)
   - [Windows 10 settings](vpn-settings-windows-10.md) (Inställningar för Windows 10) (inklusive Windows Holographic for Business)
8. När du är klar väljer du att **Skapa** din profil

Profilen skapas och visas i profillistan. Om du vill tilldela profilen till grupper kan du läsa [Tilldela enhetsprofiler](device-profile-assign.md).

## <a name="methods-of-securing-vpn-profiles"></a>Metoder för att skydda VPN-profiler

VPN-profiler kan använda ett antal olika anslutningstyper och protokoll från olika tillverkare. Dessa anslutningar skyddas vanligtvis med en av följande metoder.

### <a name="certificates"></a>Certifikat

När du skapar VPN-profilen väljer du en SCEP- eller PKCS-certifikatprofil som du tidigare har skapat i Intune. Profilen kallas för identitetscertifikat. Det används för att autentisera mot en betrodd certifikatprofil (eller ett *rotcertifikat*) som du har skapat för att användarens enhet ska få ansluta. Det betrodda certifikatet tilldelas datorn som autentiserar VPN-anslutningen, vanligtvis VPN-servern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Användarnamn och lösenord

Användaren autentiseras mot VPN-servern genom att ange användarnamn och lösenord.
