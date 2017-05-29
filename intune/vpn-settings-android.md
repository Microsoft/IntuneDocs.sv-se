---
title: "VPN-inställningar i Intune för Android-enheter"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig mer om Intune-inställningar som du kan använda för att konfigurera VPN-anslutningar på Android-enheter."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8c8690b191c7358c8fd60c241177aca1372a8f54
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>VPN-inställningar för Android-enheter i Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Beroende på vilka inställningar du väljer, är inte alla värden i listan nedan konfigurerbara.

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

