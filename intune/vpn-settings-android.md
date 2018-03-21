---
title: "VPN-inställningar i Microsoft Intune för enheter som kör Windows 10"
titlesuffix: 
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på enheter som kör Android"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 909c014e1d68c26c1440c2b924e05dbaabbde5e5
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Konfigurera VPN-inställningar i Microsoft Intune för enheter som kör Android 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I den här artikeln beskrivs de Intune-inställningar som du kan använda till att konfigurera VPN-anslutningar på enheter som kör Android.


Du kan konfigurera VPN-inställningar för följande plattformar:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Beroende på vilka inställningar du väljer kan bara vissa av följande värden konfigureras.

## <a name="android-vpn-settings"></a>VPN-inställningar för Android
**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Välj den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Fingeravtryck** (endast Check Point Capsule VPN) – Ange en sträng, till exempel ”Contoso fingeravtryckskod”, som ska användas för att verifiera att VPN-servern är betrodd. Ett fingeravtryck kan skickas till klienten så att den vet att den ska lita på alla servrar som visar upp samma fingeravtryck vid anslutningen. Om enheten inte redan har fingeravtrycket uppmanas användaren att lita på den VPN-server som anslutningsförsöket görs till medan fingeravtrycket visas (användaren verifierar fingeravtrycket manuellt och väljer att lita på för att ansluta).
- **Ange nyckel-värdepar för Citrix VPN-attributen** (endast Citrix) – Ange nyckel- och värdepar som tillhandahålls av Citrix för att konfigurera egenskaperna för VPN-anslutningen.

## <a name="android-for-work-vpn-settings"></a>VPN-inställningar för Android for Work

**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller fullständigt domännamn** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Välj den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

