---
title: "Hur du konfigurerar VPN-inställningar i Intune"
titleSuffix: Azure portal
description: "Läs om hur använder Intune för att konfigurera VPN-anslutningar på enheter som du hanterar.”"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 699fa64bc0f720b18c1376e39b85eccd9018bbaf
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>Så här konfigurerar du VPN-inställningar i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Virtuella privata nätverk (VPN, Virtual Private Networks) ger användarna säker fjärråtkomst till företagets nätverk. Enheterna använder en profil för VPN-anslutning för att initiera en anslutning till VPN-servern. Använd **VPN-profiler** i Microsoft Intune för att tilldela VPN-inställningar till användare och enheter i din organisation så att de enkelt och säkert kan ansluta till nätverket.

Exempel: Anta att du vill förse alla enheter som kör iOS med de inställningar som krävs för att ansluta till en filresurs i företagsnätverket. Då kan du skapa en VPN-profil som innehåller de inställningar som behövs för att ansluta till företagsnätverket och sedan tilldela profilen till alla användare som har enheter som kör iOS. Användarna ser VPN-anslutningen i listan över tillgängliga nätverk och kan enkelt ansluta.

## <a name="vpn-connection-types"></a>VPN-anslutningstyper

Du kan skapa VPN-profiler med följande anslutningstyper:

|Anslutningstyp|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8,1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco (IPSec)|Nej|Ja|Nej|Nej|Nej|Nej|
|Citrix|Ja|Ja|Nej|Nej|Nej|Ja|
|F5 Edge Client|Ja|Ja|Ja|Ja|Ja|Ja|
|Dell SonicWALL Mobile Connect|Ja|Ja|Ja|Ja|Ja|Ja|
|Check Point Capsule VPN|Ja|Ja|Ja|Ja|Ja|Ja|
|Cisco AnyConnect|Ja|Ja|Ja|Nej|Nej|Nej|
|Automatiskt|Nej|Nej|Nej|Nej|Nej|Ja|
|IKEv2|Nej|Nej|Nej|Nej|Nej|Ja|
|L2TP|Nej|Nej|Nej|Nej|Nej|Ja|
|PPTP|Nej|Nej|Nej|Nej|Nej|Ja|
|Anpassad|Nej|Ja|Ja|Nej|Nej|Nej|


> [!IMPORTANT]
> Innan du kan använda de VPN-profiler som har tilldelats till en enhet måste du installera lämplig VPN-app för profilen. Använd informationen i avsnittet [Vad är apphantering i Microsoft Intune?](app-management.md) när du ska tilldela appar med hjälp av Intune.  

Läs om hur du skapar anpassade VPN-profiler med hjälp av URI-inställningarna i [Skapa anpassade VPN-profiler](custom-vpn-profiles-create.md).     

## <a name="create-a-device-profile-containing-vpn-settings"></a>Skapa en enhetsprofil som innehåller VPN-inställningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. Ange **Namn** och **Beskrivning** för VPN-profilen på bladet **Skapa profil**.
5. Välj den enhetsplattform på vilken du vill tillämpa VPN-inställningarna från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för VPN-enhetsinställningar:
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 och senare**
    - **Windows 10 och senare**
6. Välj **VPN** i listrutan **Profiltyp**.
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android och Android for Work](vpn-settings-android.md)
    - [Inställningar för iOS](vpn-settings-ios.md)
    - [Inställningar för macOS](vpn-settings-macos.md)
    - [Inställningar för Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 8.1](vpn-settings-windows-8-1.md)
    - [Inställningar för Windows 10](vpn-settings-windows-10.md)
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](device-profile-assign.md).


## <a name="methods-of-securing-vpn-profiles"></a>Metoder för att skydda VPN-profiler

VPN-profiler kan använda ett antal olika anslutningstyper och protokoll från olika tillverkare. Dessa anslutningar skyddas vanligtvis med en av följande metoder.

### <a name="certificates"></a>Certifikat

När du skapar VPN-profilen väljer du en SCEP- eller PKCS-certifikatprofil som du tidigare har skapat i Intune. Detta kallas identitetscertifikat. Det används för att autentisera mot en betrodd certifikatprofil (eller *rotcertifikat*) som du har skapat för att fastställa att användarens enhet får ansluta. Det betrodda certifikatet tilldelas datorn som autentiserar VPN-anslutningen, vanligtvis VPN-servern.

Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Microsoft Intune](certificates-configure.md).

### <a name="user-name-and-password"></a>Användarnamn och lösenord

Användaren autentiseras mot VPN-servern genom att ange användarnamn och lösenord.
