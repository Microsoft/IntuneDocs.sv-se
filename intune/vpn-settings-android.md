---
title: "VPN-inställningar i Intune för Android-enheter"
titlesuffix: Azure portal
description: "Lär dig mer om de Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Android-enheter"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 23d898df90313a1a342c5a8898afea55e50dd705
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>VPN-inställningar för Android-enheter i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Som Intune-administratör kan du konfigurera VPN-inställningar för följande plattformar:

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

Beroende på vilka inställningar du väljer, så är inte alla värden i listan nedan konfigurerbara.

## <a name="android-vpn-settings"></a>VPN-inställningar för Android
**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Välj den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **Fingeravtryck** (endast Check Point Capsule VPN) – Ange en sträng, till exempel ”Contoso fingeravtryckskod”, som ska användas för att verifiera att VPN-servern är betrodd. Ett fingeravtryck kan skickas till klienten så att den vet att den ska lita på alla servrar som visar upp samma fingeravtryck vid anslutningen. Om enheten inte redan har fingeravtrycket uppmanas användaren att lita på den VPN-server som anslutningsförsöket görs till medan fingeravtrycket visas (användaren verifierar fingeravtrycket manuellt och väljer att lita på för att ansluta).
- **Ange nyckel-värdepar för Citrix VPN-attributen** (endast Citrix) – Ange nyckel- och värdepar som tillhandahålls av Citrix för att konfigurera egenskaperna för VPN-anslutningen.

## <a name="android-for-work-vpn-settings"></a>VPN-inställningar för Android for Work

**Anslutningsnamn** – Ange ett namn på anslutningen. Slutanvändarna ser det här namnet när de bläddrar på enheten i listan över tillgängliga VPN-anslutningar.
- **IP-adress eller FQDN** – Ange IP-adress eller fullständigt domännamn för den VPN-server som enheterna ska ansluta till. Exempel: **192.168.1.1**, **vpn.contoso.com**.
- **Autentiseringsmetod** – Välj hur enheter ska autentiseras mot VPN-servern från:
    - **Certifikat** – Välj den SCEP- eller PKCS-certifikatprofil som du skapade tidigare för att autentisera anslutningen. Mer information om certifikatprofiler finns i [Så här konfigurerar du certifikat](certificates-configure.md).
    - **Användarnamn och lösenord** – Slutanvändare måste ange ett användarnamn och lösenord för att logga in på VPN-servern.
- **Anslutningstyp** – Välj VPN-anslutningstyp från leverantörslistan nedan:
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

- **Delade tunnlar** – Om du aktiverar detta kan viss webbtrafik använda VPN-anslutningen när annan trafik använder Internet. Inaktivera inställningen om du vill att all trafik till ska använda VPN-anslutningen när den är aktiv.
